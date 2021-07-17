---
title: Solução de problemas do aplicativo de desktop versão 1.10.
description: Solucione os problemas [!DNL Adobe Experience Manager] do aplicativo de desktop versão 1.10 para resolver os problemas ocasionais relacionados à instalação, atualização e configuração.
exl-id: 1e1409c2-bf5e-4e2d-a5aa-3dd74166862c
source-git-commit: 32aff5d66f2cb67ab4bb440d7ace747a5cf1dd26
workflow-type: tm+mt
source-wordcount: '3350'
ht-degree: 1%

---

# Solucionar problemas do [!DNL Adobe Experience Manager] aplicativo de desktop v1.x {#troubleshoot-aem-desktop-app}

Solucione problemas AEM aplicativo de desktop para resolver problemas ocasionais relacionados à instalação, atualização, configuração e assim por diante.

[!DNL Adobe Experience Manager] o aplicativo de desktop inclui utilitários que ajudam a mapear o repositório do AEM Assets como um compartilhamento de rede no desktop (compartilhamento SMB no Mac OS). O compartilhamento de rede é uma tecnologia de sistema operacional que permite que fontes remotas sejam tratadas como se fizessem parte de um sistema de arquivos local do computador. No caso de um aplicativo de desktop, a estrutura de repositório DAM (Digital Asset Management, gerenciamento de ativos digitais) de uma instância de AEM remota é direcionada como a fonte de arquivos remota. O diagrama a seguir descreve a topologia do aplicativo de desktop:

![diagrama do aplicativo de desktop](assets/aem-desktopapp-architecture.png)

Com essa arquitetura, o aplicativo de desktop intercepta chamadas do sistema de arquivos (abrir, fechar, ler, gravar e assim por diante) para o compartilhamento de rede montado e as transforma em chamadas HTTP nativas AEM para o servidor AEM. Os arquivos são armazenados em cache localmente. Para obter mais detalhes, consulte [Usar AEM aplicativo de desktop v1.x](use-app-v1.md).

## Visão geral do componente de aplicativo de desktop do AEM {#desktop-app-component-overview}

o aplicativo de desktop inclui os seguintes componentes:

* **O aplicativo** de desktop: O aplicativo monta ou desmonta o DAM como um sistema de arquivos remoto e traduz chamadas do sistema de arquivos entre o compartilhamento de rede montado localmente e a instância de AEM remota à qual ele se conecta.
* **Sistema operacional Cliente WebDAV/SMB**: Gerencia a comunicação entre o Windows Explorer/Finder e o aplicativo de desktop. Se um arquivo for recuperado, criado, modificado, excluído, movido ou copiado, o cliente WebDAV/SMB do sistema operacional (OS) comunicará essa operação ao aplicativo de desktop. Depois de receber a comunicação, o aplicativo de desktop a converte em chamadas de API remotas nativas AEM. Por exemplo, se um usuário cria um arquivo no diretório montado, o cliente WebDAV/SMB inicia uma solicitação, que o aplicativo de desktop converte em uma solicitação HTTP que cria o arquivo no DAM. O cliente WebDAV/SMB é um componente incorporado do SO. Ele não é afiliado a aplicativos de desktop, AEM ou Adobe de forma alguma.
* **Instância** do Adobe Experience Manager: Fornece acesso aos ativos armazenados no repositório do AEM Assets DAM. Além disso, ele executa ações solicitadas pelo aplicativo de desktop em nome dos aplicativos de desktop locais que interagem com o compartilhamento de rede montado. A instância do target AEM deve ser executada AEM versão 6.1 ou superior. AEM instâncias que executam versões AEM anteriores podem exigir pacotes de recursos adicionais e hotfixes instalados para se tornarem totalmente funcionais.

## Casos de uso previstos para AEM aplicativo de desktop {#intended-use-cases-for-aem-desktop-app}

AEM aplicativo de desktop usa a tecnologia de compartilhamento de rede para mapear um repositório AEM remoto para um desktop local. No entanto, não se destina a substituir um compartilhamento de rede que contém ativos, no qual os usuários executam operações de gerenciamento de ativos digitais diretamente do desktop local. Isso inclui mover ou copiar vários arquivos ou arrastar grandes estruturas de pasta para o compartilhamento de rede do AEM Assets diretamente no Finder/Explorer.

AEM aplicativo de desktop fornece uma maneira conveniente de acessar (abrir) e editar (salvar) ativos DAM entre a interface do usuário de toque do AEM Assets e o desktop local. Ele vincula ativos no servidor do AEM Assets aos fluxos de trabalho baseados em desktop.

O exemplo de uso a seguir ilustra como AEM Desktop deve ser usado:

* Um usuário faz logon no AEM e usa a interface do usuário da Web para localizar um ativo.
* Usando os recursos de ação da área de trabalho da interface do usuário da Web AEM, o usuário abre, exibe ou edita o ativo na área de trabalho, conforme necessário.
* AEM Desktop abre o ativo no editor padrão para o tipo de arquivo do ativo.
* O usuário faz as alterações desejadas no ativo.
* Depois que um arquivo é modificado, o usuário pode visualizar o status de sincronização do arquivo usando AEM janela de status de sincronização em segundo plano da Área de trabalho.
* Usando o menu de contexto de AEM desktop, o usuário faz o check-in/out do ativo ou retorna à interface do usuário do DAM.
* Após concluir as alterações no arquivo, o usuário retorna à interface do usuário da Web AEM

Esse não é o único caso de uso. No entanto, isso ilustra como o AEM Desktop é um mecanismo conveniente para acessar/editar ativos localmente. Você é incentivado a usar a interface do usuário da Web do DAM o máximo possível, pois ela fornece uma experiência melhor. Ele oferece Adobe mais flexibilidade para atender às necessidades do cliente.

## Limitações           {#limitations}

O compartilhamento de rede WebDAV/SMB1 oferece a conveniência de trabalhar com arquivos em uma janela Explorer/Finder. No entanto, o Explorer/Finder e o AEM se comunicam por uma conexão de rede que tem determinadas limitações. Por exemplo, o tempo gasto para copiar um arquivo de 1 GB para o diretório WebDAV/SMB montado é aproximadamente o mesmo que o tempo necessário para carregar um arquivo de 1 GB em um site usando um navegador da Web. Na verdade, no primeiro caso, a duração pode ser maior devido às ineficiências do protocolo WebDAV/SMB e dos clientes WebDAV/SMB do sistema operacional (especialmente Mac OS X).

Existem limitações para os tipos de tarefas que podem ser executadas a partir de um diretório montado. Em geral, trabalhar com arquivos grandes, especialmente por uma conexão de rede de baixa/alta latência/largura de banda baixa, pode ser um desafio, especialmente ao editar arquivos grandes.

O Adobe recomenda que você execute algum teste de caso de uso antes de confirmar para um cliente que certos tipos de arquivos podem ser editados no local com eficiência a partir do diretório montado.

AEM Desktop não é adequado para executar a manipulação intensiva do sistema de arquivos, incluindo, mas não se limitando a:

* Mover ou copiar arquivos e diretórios
* Adicionar muitos ativos ao AEM
* Procurando e abrindo arquivos pelo sistema de arquivos, exceto por pastas de navegação
* Compactação ou descompactação de arquivos

Devido a limitações no sistema operacional, o Windows tem uma limitação de tamanho de arquivo de 4.294.967.295 bytes (aproximadamente 4,29 GB). É devido a uma configuração de registro que define o tamanho que um arquivo em um compartilhamento de rede pode ter. O valor da configuração do Registro é um DWORD com um tamanho máximo que é igual ao número referenciado.

[!DNL Experience Manager] o aplicativo de desktop não tem um valor de tempo limite configurável que desconecta a conexão entre o  [!DNL Experience Manager] servidor e o aplicativo de desktop após um intervalo de tempo fixo. Ao fazer upload de ativos grandes, se a conexão expirar depois de um tempo, o aplicativo tenta fazer upload do ativo algumas vezes, aumentando o tempo limite de upload. Não há uma maneira recomendada de alterar as configurações de tempo limite padrão.

## Armazenamento em cache e comunicação com AEM {#caching-and-communication-with-aem}

AEM aplicativo de desktop fornece recursos internos de cache e upload em segundo plano para melhorar a experiência do usuário final. Ao salvar um arquivo grande, ele é salvo localmente pela primeira vez para permitir que você continue trabalhando. Depois de algum tempo (atualmente 30 segundos), o arquivo é enviado ao servidor AEM em segundo plano.

Ao contrário do Creative Cloud Desktop ou de outras soluções de sincronização de arquivos, como o Microsoft One Drive, AEM aplicativo de desktop não é um cliente de Sincronização de desktop completo. O motivo é que ele fornece acesso a todo o repositório AEM Assets, que pode ser extremamente grande (centenas de gigabytes ou terabytes) para uma sincronização completa.

O armazenamento em cache fornece a capacidade de limitar a sobrecarga da rede/armazenamento somente a um subconjunto de ativos relevantes para o usuário.

>[!CAUTION]
>
>O Adobe recomenda desativar a geração de miniaturas para agilizar a navegação. Se você ativar visualizações de ícones, o aplicativo armazenará em cache os ativos digitais ao navegar pela pasta montada. O aplicativo também baixa ativos que o usuário pode não se importar, o que adiciona carga ao servidor, consome a largura de banda do usuário e usa mais espaço em disco do usuário.

Veja como AEM aplicativo de desktop executa o cache:

* Quando você abre uma pasta no Finder e miniaturas/visualizações de arquivos são exibidas, ou quando você abre um arquivo em um aplicativo, o aplicativo de desktop armazena em cache o binário de arquivo.
* Ao armazenar arquivos por meio do Finder ou de outros aplicativos de desktop, o arquivo é armazenado localmente primeiro (em cache) e o sistema operacional é notificado. O arquivo é então colocado na fila para upload no servidor em segundo plano e, eventualmente, carregado pela rede. No caso de um erro de rede, o aplicativo de desktop tenta fazer upload do arquivo inteiro por no máximo três vezes. Se ocorrer uma falha no upload após três tentativas, o arquivo é marcado como um arquivo em conflito e o status é exibido por meio da janela Status da fila de upload em segundo plano . o aplicativo de desktop não tenta mais atualizar o arquivo. O usuário deve atualizar o arquivo e fazer o upload novamente após a restauração da conectividade

Cada operação não é armazenada em cache localmente. Os itens a seguir são transmitidos ao servidor do AEM imediatamente sem armazenamento em cache local:

* Qualquer operação em pastas, por exemplo, criar, excluir e assim por diante
* O recurso Carregamento de pasta introduzido na versão 1.4 carrega uma hierarquia de pasta local, sem armazenar os arquivos em cache localmente

## Operações individuais {#individual-operations}

Ao solucionar problemas de desempenho sub-otimizado para usuários individuais, revise primeiro [as limitações do aplicativo](#limitations). As seções subsequentes incluem sugestões para melhorar o desempenho de cada usuário.

## Recomendações de largura de banda {#bandwidth-recommendations}

A largura de banda disponível para um usuário individual desempenha um papel crítico no desempenho do cliente WebDAV/SMB.

O Adobe recomenda que a velocidade de upload de um usuário individual seja próxima a 10 Mbps. Para conexões sem fio, a largura de banda é frequentemente compartilhada entre vários usuários. Se vários usuários executarem simultaneamente tarefas que consomem largura de banda da rede, o desempenho pode degradar-se ainda mais. Para evitar esses problemas, use uma conexão com fio.

## Configurações específicas do Windows {#windows-specific-configurations}

Se utilizar o Experience Manager no Windows, poderá configurar o Windows para melhorar o desempenho do cliente WebDAV. Para obter mais informações, acesse [https://support.microsoft.com/en-us/kb/2445570](https://support.microsoft.com/pt-BR/kb/2445570).

No Windows 7, a modificação das configurações do IE pode melhorar o desempenho do WebDAV. Para obter detalhes, consulte como [corrigir o desempenho lento do WebDAV no Windows 7](https://oddballupdate.com/2009/12/fix-slow-webdav-performance-in-windows-7/).

<!-- TBD: The above performance tip is for Windows 7 which is not supported by the app anymore. Remove it later.
-->

## Operações simultâneas {#concurrent-operations}

Quando você interage com um arquivo localmente, o AEM Desktop verifica se uma versão mais recente do arquivo está disponível no AEM. Se uma nova versão estiver disponível, o aplicativo baixará uma cópia nova do arquivo para o cache local. No entanto, AEM Desktop não substitui um arquivo armazenado em cache localmente se ele tiver sido modificado. Esse recurso impede que seu trabalho seja substituído inadvertidamente.

Quando o mesmo arquivo é modificado localmente e no AEM, a versão modificada localmente substitui a versão no AEM. Nesse caso, a versão anterior está disponível na linha do tempo do ativo. Você pode verificar ambas as versões e resolver qualquer conflito.

Se um arquivo local estiver inconsistente com a versão disponível no servidor, a caixa de diálogo de status do upload em segundo plano o notificará sobre o conflito. Para resolver o problema, abra o arquivo em conflito e salve-o. Salvar o arquivo força o Desktop a sincronizar as alterações locais mais recentes no AEM. É possível exibir versões anteriores do ativo na linha do tempo e resolver conflitos.

Você deve levar em conta fatores adicionais quando vários usuários tentarem trabalhar em diretórios montados separados direcionando a mesma instância de AEM. Em particular, os seguintes fatores são importantes:

* A quantidade de largura de banda disponível na rede de origem dos usuários
* Configuração de rede, como firewalls ou proxies, da rede de origem
* Quantidade de largura de banda disponível na rede da instância de AEM de destino
* Se um dispatcher está presente antes da instância do AEM de destino
* Carga atual na instância de AEM de destino

## Configurações adicionais de AEM {#additional-aem-configurations}

Se o desempenho do WebDAV/SMB se degrada drasticamente quando vários usuários trabalham simultaneamente, você pode configurar algumas coisas no AEM, o que pode ajudar a melhorar o desempenho.

## Atualizar fluxos de trabalho transitórios de ativos {#update-asset-transient-workflows}

Você pode melhorar o desempenho no lado do AEM ativando fluxos de trabalho transitórios para o fluxo de trabalho do Ativo de atualização DAM . Habilitar workflows transitórios reduz o poder de processamento necessário para atualizar ativos quando eles são criados ou modificados em AEM.

1. Navegue até `/miscadmin` na instância do Experience Manager (`https://[aem_server]:[port]/miscadmin`).
1. Na árvore de navegação, expanda **Ferramentas** > **Fluxo de trabalho** > **Modelos** > **dam**.
1. Clique duas vezes em **Ativo de atualização do DAM**.
1. No painel de ferramentas flutuantes, alterne para a guia **Page** e clique em **Page Properties**.
1. Marque a caixa de seleção **Transient Workflow** e clique em **OK**.

### Ajustar fila de Fluxo de trabalho transitório do Granite {#adjust-granite-transient-workflow-queue}

Outro método para melhorar AEM desempenho é configurar o valor máximo de trabalhos paralelos para o trabalho da fila de fluxo de trabalho transitório do Granite. O valor recomendado é aproximadamente metade do número da CPU disponível com o servidor. Para ajustar o valor, execute estas etapas:

1. Navegue até `/system/console/configMgr` na instância de AEM a ser configurada (por exemplo, `https://[aem_server]:[port]/system/console/configMgr`).
1. Procure por `QueueConfiguration` e clique para abrir cada tarefa até localizar a tarefa **Fila de Fluxo de Trabalho Transitório do Granite** e clique em **Editar**.
1. Altere o valor `Maximum Parallel Jobs` e clique em **Salvar**.

## Configuração AWS {#aws-configuration}

Devido às limitações da largura de banda da rede, o desempenho do WebDAV/SMB pode degradar-se quando vários usuários trabalham simultaneamente. O Adobe recomenda aumentar o tamanho da instância do AWS para uma instância de AEM de destino executada no AWS para aprimorar o desempenho do WebDAV/SMB.

Essa medida aumenta especificamente a quantidade de largura de banda de rede disponível para o servidor. Veja alguns detalhes:

* A quantidade de largura de banda de rede dedicada a uma instância AWS aumenta à medida que o tamanho da instância aumenta. Para obter informações sobre a largura de banda disponível para cada tamanho de instância, consulte a [documentação AWS](https://aws.amazon.com/ec2/instance-types/).
* Ao solucionar problemas para um cliente grande, o Adobe configurou o tamanho de sua instância de AEM para c4.8xlarge, principalmente para os 4000 Mbps de largura de banda dedicada que ele fornece.
* Se houver um dispatcher antes da instância de AEM, verifique se ele tem o tamanho apropriado. Se a instância de AEM fornece 4000 Mbps, mas o dispatcher fornece apenas 500 Mbps, a largura de banda efetiva é de apenas 500 Mbps. Isso ocorre porque o dispatcher cria um gargalo de rede.

## Limitações de arquivo com check-out {#checked-out-file-limitations}

Há algumas limitações conhecidas na maneira de interagir com arquivos com check-out por meio do Explorer/Finder. Se for feito check-out de um arquivo, ele deverá ser somente leitura para qualquer pessoa, exceto o usuário que tiver o arquivo com check-out. A implementação do protocolo WebDAV/SMB1 no AEM aplica esta regra. No entanto, os clientes OS WebDAV/SMB geralmente não interagem normalmente com os arquivos com check-out. Algumas chances estão descritas abaixo.

### Geral {#general}

Ao gravar em um arquivo com check-out, o bloqueio é aplicado somente AEM implementação do WebDAV. Consequentemente, o bloqueio é imposto apenas por clientes que usam o WebDAV, como aplicativos de desktop. O bloqueio não é imposto por meio AEM interface da Web. A interface de AEM apenas exibe um ícone de cadeado na exibição de cartão para ativos com check-out. O ícone é cosmético e não tem efeito no comportamento do AEM.

Em geral, os clientes WebDAV nem sempre se comportam como esperado. Pode haver outros problemas. No entanto, atualizar ou verificar o ativo no AEM é uma maneira sólida de verificar se um ativo não está sendo modificado. Esse comportamento é típico dos clientes WebDAV do OS, que não estão sob o controle Adobe.

### Windows {#windows}

A eliminação de um ficheiro parece ter êxito porque o ficheiro desaparece do explorador de ficheiros no Windows. No entanto, atualizar o diretório e verificar AEM ativos mostra que o arquivo ainda está presente. Além disso, a edição de arquivos parece ter êxito (nenhuma caixa de diálogo de aviso ou mensagem de erro é exibida). No entanto, reabrir o arquivo ou verificar AEM ativos revela que o arquivo permanece inalterado.

#### Mac OS X {#mac-os-x}

Substituir um arquivo não exibe um aviso ou erro, mas verificar o ativo em AEM revela que ele permanece inalterado. Atualize ou verifique o ativo no AEM para verificar se ele não está sendo modificado.

## Solução de problemas do ícone do aplicativo de desktop (Mac OS X) {#troubleshooting-desktop-app-icon-issues-mac-os-x}

Depois de instalar o aplicativo de desktop, o ícone do menu do aplicativo de desktop aparece na barra de menus. Se o ícone não for exibido, execute estas etapas para resolver o problema:

1. Abra a janela do terminal do sistema operacional.
1. Digite o seguinte comando no prompt de comando e pressione Enter:

   ```shell
    cd ../Library/Caches.
   ```

1. Digite o seguinte comando e pressione Enter:

   ```shell
   rm -r com.adobe.aem.assetscompanion
   ```

1. Digite o seguinte comando e pressione Enter:

   ```shell
   cd ~/Library/Preferences
   ```

1. Digite o seguinte comando e pressione Enter:

   ```shell
   rm com.adobe.aem.assetscompanion.plist
   ```

1. Digite o seguinte comando e pressione Enter:

   ```shell
   rm ~/Library/Group\ Containers/group.com.adobe.aem.desktop/*
   ```

1. Reinicie o sistema.

AEM Desktop tenta sincronizar qualquer arquivo específico três vezes. Se o arquivo não for sincronizado após a terceira tentativa, o AEM Desktop considerará o arquivo em conflito e o notificará por meio da janela de status do upload em segundo plano. Um estado de conflito indica que suas alterações mais recentes ainda estão disponíveis localmente, mas não são sincronizadas com o AEM. AEM aplicativo de desktop não tenta mais sincronizar.

A maneira mais simples de corrigir essa situação é abrir o arquivo conflitante e salvá-lo novamente. Isso força AEM Desktop a tentar a sincronização por mais três ocasiões. Se o arquivo ainda não conseguir sincronizar, consulte as seções abaixo para obter mais ajuda.

## Limpar AEM cache do desktop {#clearing-aem-desktop-cache}

Limpar AEM cache da área de trabalho é uma tarefa preliminar de solução de problemas que pode resolver vários problemas AEM da área de trabalho.

Você pode limpar o cache excluindo o diretório de cache do aplicativo nos seguintes locais.
No Windows, `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

No Mac, `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

No entanto, o local pode mudar dependendo do ponto de extremidade AEM da área de trabalho configurada AEM. O valor é uma versão codificada do URL de destino. Por exemplo, se o aplicativo estiver direcionando `http://localhost:4502`, o nome do diretório será `http%3A%2F%2Flocalhost%3A4502%2F`.

Para limpar o cache, exclua o diretório &lt;Endpoint AEM codificado>.

>[!NOTE]
>
>Se você limpar AEM cache do Desktop, as alterações de arquivo local que não estão sincronizadas com AEM serão perdidas.

>[!NOTE]
>
>A partir AEM aplicativo de desktop versão 1.5, há uma opção na interface do usuário do aplicativo de desktop para limpar o cache.

## Encontrar a versão AEM Desktop {#finding-the-aem-desktop-version}

O procedimento para determinar a versão do AEM Desktop é o mesmo para Windows e Mac OS.

Clique no ícone AEM Desktop e escolha **Sobre**. O número da versão é exibido na tela .

## Atualização AEM aplicativo de desktop no macOS {#upgrading-aem-desktop-app-on-macos}

Ocasionalmente, podem ocorrer problemas ao atualizar AEM aplicativo de desktop no macOS. Isso é causado pela pasta herdada do sistema para AEM aplicativo de desktop, impedindo que novas versões do AEM Desktop sejam carregadas corretamente. Para solucionar esse problema, as pastas e os arquivos a seguir podem ser removidos manualmente.

Antes de executar as etapas abaixo, arraste o aplicativo &quot;Adobe Experience Manager Desktop&quot; da pasta Aplicativos macOS para a Lixeira. Em seguida, abra o terminal e execute o seguinte comando, fornecendo sua senha quando solicitado.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## Salvar um arquivo com check-out feito por outras pessoas {#saving-a-file-checked-out-by-others}

As limitações técnicas do sistema operacional impedem que os usuários tenham uma experiência consistente ao tentar substituir um arquivo com check-out feito por outros. A experiência varia dependendo do aplicativo usado para editar o arquivo com check-out. Às vezes, o aplicativo exibe uma mensagem de erro indicando uma falha de gravação de disco ou exibe um erro aparentemente não relacionado ou genérico. Em outras ocasiões, nenhuma mensagem de erro é exibida e a operação parece ter êxito.

Nesse caso, fechar e reabrir o arquivo pode revelar que o conteúdo permanece inalterado. No entanto, alguns aplicativos podem armazenar um backup do arquivo para que suas alterações possam ser aplicadas.

Independentemente do comportamento, o arquivo permanece inalterado ao fazer o check-in. Mesmo que uma versão diferente do arquivo seja exibida, as alterações não serão sincronizadas com o AEM.

## Solução de problemas ao mover arquivos {#troubleshooting-problems-around-moving-files}

A API do servidor requer cabeçalhos adicionais, Destino X, Profundidade X e Substituição X, para que as operações de movimentação e cópia funcionem. O dispatcher não passa esses cabeçalhos por padrão, o que faz com que essas operações falhem. Para obter mais informações, consulte [Conexão com AEM atrás de um Dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Solução de problemas de conexão AEM desktop {#troubleshooting-aem-desktop-connection-issues}

### Problema de redirecionamento SAML {#saml-redirect-issue}

O motivo mais comum para problemas com AEM Desktop se conectando à instância de AEM habilitada por SSO (SAML) é que o processo SAML não redireciona para o caminho solicitado originalmente. Como alternativa, a conexão pode ser redirecionada para um host que não está configurado AEM desktop. Execute as etapas a seguir para verificar o processo de logon:

1. Abra um navegador da Web.
1. Na barra de endereços, especifique o URL `/content/dam.json`.
1. Substitua o URL pela instância do AEM de destino, por exemplo `https://localhost:4502/content/dam.json`.
1. Faça logon no AEM.
1. Depois de fazer logon, verifique o endereço atual do navegador na barra de endereços. Deve corresponder ao URL inserido inicialmente.
1. Verifique se tudo antes de `/content/dam.json` corresponde ao valor do AEM de destino configurado AEM desktop.

### Problema de configuração de SSL {#ssl-configuration-issue}

As bibliotecas que AEM aplicativo de desktop usa para comunicação HTTP usam imposição estrita de SSL. Às vezes, uma conexão pode ser bem-sucedida usando um navegador, mas falha ao usar AEM aplicativo de desktop. Para configurar o SSL adequadamente, instale o certificado intermediário ausente no Apache. Consulte [Como instalar um certificado CA intermediário no Apache](https://access.redhat.com/solutions/43575).

## Uso do AEM Desktop com o dispatcher {#using-aem-desktop-with-dispatcher}

AEM Desktop funciona com implantações AEM atrás de um dispatcher, que é uma configuração padrão e recomendada para AEM servidores. AEM dispatchers na frente AEM ambientes de criação normalmente são configurados para ignorar o armazenamento em cache de ativos do DAM. Portanto, os dispatchers não fornecem armazenamento em cache adicional do ponto de vista do Desktop AEM. Verifique se a configuração do dispatcher está ajustada para funcionar no AEM Desktop. Para obter detalhes adicionais, consulte [Conexão com AEM atrás de um dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Verificando arquivos de log {#checking-for-log-files}

Dependendo do seu sistema operacional, você pode encontrar os arquivos de log para AEM Desktop nos seguintes locais:

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`
* Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`
