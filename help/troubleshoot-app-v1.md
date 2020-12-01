---
title: Solução de problemas AEM aplicativo para desktop versão 1.x
description: Solucione problemas AEM aplicativo de desktop versão 1.x para resolver problemas ocasionais relacionados à instalação, atualização, configuração e assim por diante.
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.5/ASSETS, SG_EXPERIENCEMANAGER/6.4/ASSETS, SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1702ef74ad0497b25c2fc349a2950e4e2b19a90b
workflow-type: tm+mt
source-wordcount: '3379'
ht-degree: 1%

---


# Solução de problemas AEM aplicativo de desktop v1.x {#troubleshoot-aem-desktop-app}

Solucione problemas AEM aplicativo de desktop para resolver problemas ocasionais relacionados à instalação, atualização, configuração e assim por diante.

O aplicativo para desktop Adobe Experience Manager (AEM) inclui utilitários que ajudam a mapear o repositório AEM Assets como um compartilhamento de rede no desktop (compartilhamento SMB no Mac OS). O compartilhamento de rede é uma tecnologia de sistema operacional que permite que fontes remotas sejam tratadas como se fossem parte de um sistema de arquivos local do computador. No caso de aplicativos de desktop, a estrutura de repositório DAM (digital asset management, gerenciamento de ativos digitais) de uma instância remota AEM é direcionada como a fonte de arquivos remotos. O diagrama a seguir descreve a topologia do aplicativo de desktop:

![diagrama do aplicativo desktop](assets/aem-desktopapp-architecture.png)

Com essa arquitetura, o aplicativo desktop intercepta chamadas do sistema de arquivos (abrir, fechar, ler, gravar e assim por diante) para o compartilhamento de rede montado e as converte em chamadas HTTP nativas AEM para o servidor AEM. Os arquivos são armazenados em cache localmente. Para obter mais detalhes, consulte [Usar AEM aplicativo de desktop v1.x](use-app-v1.md).

## Visão geral do componente do aplicativo para desktop AEM {#desktop-app-component-overview}

o aplicativo desktop inclui os seguintes componentes:

* **O aplicativo** de desktop: O aplicativo monta ou desmonta o DAM como um sistema de arquivos remoto e traduz as chamadas do sistema de arquivos entre o compartilhamento de rede montado localmente e a instância remota AEM à qual ele se conecta.
* **Cliente** WebDAV/SMB do sistema operacional: Trata da comunicação entre o Windows Explorer/Finder e o aplicativo de desktop. Se um arquivo for recuperado, criado, modificado, excluído, movido ou copiado, o cliente WebDAV/SMB do sistema operacional (OS) comunicará esta operação para o aplicativo de desktop. Depois de receber a comunicação, o aplicativo de desktop a converte em chamadas de API remotas nativas AEM. Por exemplo, se um usuário cria um arquivo no diretório montado, o cliente WebDAV/SMB inicia uma solicitação, que o aplicativo desktop converte em uma solicitação HTTP que cria o arquivo no DAM. O cliente WebDAV/SMB é um componente incorporado do SO. Ele não é afiliado a aplicativos de desktop, AEM ou Adobe de forma alguma.
* **Instância** do Adobe Experience Manager: Fornece acesso aos ativos armazenados no repositório do AEM Assets DAM. Além disso, ele executa ações solicitadas pelo aplicativo desktop em nome dos aplicativos de desktop locais que interagem com o compartilhamento de rede montado. A instância do AEM do público alvo deve ser executada AEM versão 6.1 ou superior. AEM instâncias executando versões AEM anteriores podem exigir pacotes de recursos adicionais e hot fixes instalados para se tornarem totalmente funcionais.

## Casos de uso pretendido para AEM aplicativo de desktop {#intended-use-cases-for-aem-desktop-app}

AEM aplicativo desktop usa a tecnologia de compartilhamento de rede para mapear um repositório AEM remoto para um desktop local. No entanto, não se destina a substituir um compartilhamento de rede que contém ativos, onde os usuários executam operações de gerenciamento de ativos digitais diretamente de seu desktop local. Isso inclui mover ou copiar vários arquivos, ou arrastar estruturas de pastas grandes para o compartilhamento de rede da AEM Assets diretamente no Finder/Explorer.

AEM aplicativo para desktop fornece uma maneira conveniente de acessar (abrir) e editar (salvar) ativos DAM entre a interface do usuário AEM Assets Touch e a área de trabalho local. Ele vincula ativos no servidor AEM Assets aos workflows baseados em desktop.

O exemplo de uso a seguir ilustra como AEM Desktop deve ser usada:

* Um usuário faz logon no AEM e usa a interface do usuário da Web para localizar um ativo.
* Usando os recursos de ação da área de trabalho da interface do usuário da Web AEM, o usuário abre, exibe ou edita o ativo na área de trabalho, conforme necessário.
* AEM Desktop abre o ativo no editor padrão para o tipo de arquivo do ativo.
* O usuário faz as alterações desejadas no ativo.
* Depois que um arquivo é modificado, o usuário pode visualização o status de sincronização do arquivo usando AEM janela de status de sincronização em segundo plano da área de trabalho.
* Usando o menu de contexto AEM Área de trabalho, o usuário faz check-in/check-out do ativo ou retorna à interface do usuário do DAM.
* Após concluir as alterações no arquivo, o usuário retorna à interface do usuário da Web AEM

Este não é o único caso de uso. No entanto, ele ilustra como AEM Desktop é um mecanismo conveniente para acessar/editar ativos localmente. É recomendável usar a interface do usuário da Web do DAM o máximo possível, pois ela fornece uma experiência melhor. Ele oferece Adobe maior flexibilidade para atender às necessidades do cliente.

## Limitações           {#limitations}

O compartilhamento de rede WebDAV/SMB1 oferece a conveniência de trabalhar com arquivos em uma janela do Explorer/Finder. No entanto, o Explorer/Finder e AEM se comunicam por uma conexão de rede que tem certas limitações. Por exemplo, o tempo gasto para copiar um arquivo de 1 GB para o diretório WebDAV/SMB montado é aproximadamente o mesmo que o tempo necessário para carregar um arquivo de 1 GB para um site usando um navegador da Web. Na verdade, no primeiro caso, a duração pode ser mais longa devido às ineficiências do protocolo WebDAV/SMB e dos clientes WebDAV/SMB do SO (especialmente Mac OS X).

Há limitações para os tipos de tarefas que podem ser executadas a partir de um diretório montado. Em geral, trabalhar com arquivos grandes, especialmente em uma conexão de rede de baixa/alta latência/largura de banda baixa, pode ser um desafio, especialmente ao editar arquivos grandes.

O Adobe recomenda que você execute alguns testes de caso de uso antes de confirmar para um cliente que certos tipos de arquivos podem ser editados no local com eficiência a partir do diretório montado.

AEM desktop não é adequado para a manipulação intensiva do sistema de arquivos, incluindo, mas não se limitando a:

* Mover ou copiar arquivos e diretórios
* Adicionar muitos ativos ao AEM
* Procurando e abrindo arquivos pelo sistema de arquivos, exceto por pastas de navegação
* Compactação ou descompactação de arquivos

Devido a limitações no sistema operacional, o Windows tem uma limitação de tamanho de arquivo de 4.294.967.295 bytes (aproximadamente 4,29 GB). É devido a uma configuração de registro que define o tamanho de um arquivo em um compartilhamento de rede. O valor da configuração do Registro é um DWORD com um tamanho máximo igual ao número referenciado.

O aplicativo de desktop Experience Manager não tem um valor de tempo limite configurável que desconecta a conexão entre o servidor Experience Manager e o aplicativo de desktop após um intervalo de tempo fixo. Ao fazer upload de ativos grandes, se a conexão expirar depois de algum tempo, o aplicativo tentativas fazer upload do ativo algumas vezes aumentando o tempo limite de upload. Não há uma maneira recomendada de alterar as configurações de tempo limite padrão.

## Cache e comunicação com AEM {#caching-and-communication-with-aem}

AEM aplicativo desktop fornece recursos internos de cache e upload em segundo plano para melhorar a experiência do usuário final. Quando você salva um arquivo grande, ele é salvo localmente pela primeira vez para permitir que você continue trabalhando. Depois de algum tempo (atualmente 30 segundos), o arquivo é enviado para o servidor AEM em segundo plano.

Diferentemente das soluções de sincronização de arquivos ou Creative Cloud Desktop, como Microsoft One Drive, AEM aplicativo de desktop não é um cliente de sincronização de desktop completo. Isso acontece porque ele fornece acesso a todo o repositório AEM Assets, que pode ser extremamente grande (centenas de gigabytes ou terabytes) para uma sincronização completa.

O armazenamento em cache oferece a capacidade de limitar a sobrecarga da rede/armazenamento somente a um subconjunto de ativos relevantes para o usuário.

>[!CAUTION]
>
>O Adobe recomenda desativar a geração de miniaturas para agilizar a navegação. Se você ativar pré-visualizações de ícones, o aplicativo armazenará em cache os ativos digitais quando você navegar pela pasta montada. O aplicativo também baixa ativos com os quais o usuário pode não se importar, o que adiciona carga ao servidor, consome a largura de banda do usuário e usa mais espaço em disco do usuário.

Veja como AEM aplicativo desktop executa o cache:

* Quando você abre uma pasta no Finder e as miniaturas/pré-visualizações de arquivos são exibidas, ou quando você abre um arquivo em um aplicativo, o aplicativo desktop armazena o arquivo em cache binário.
* Quando você armazena arquivos via Finder ou outros aplicativos de desktop, o arquivo é armazenado localmente primeiro (em cache) e o sistema operacional é notificado. O arquivo é então colocado na fila para upload no servidor em segundo plano e eventualmente carregado pela rede. Em caso de erro de rede, o aplicativo de desktop tentativas o carregamento do arquivo inteiro por no máximo três vezes. Se o upload não for feito após três tentativas, o arquivo será marcado como um arquivo em conflito e o status será exibido por meio da janela Status da fila de upload em segundo plano. o aplicativo de desktop não tenta mais atualizar o arquivo. O usuário deve atualizar o arquivo e carregá-lo novamente depois que a conectividade for restaurada

Todas as operações não são armazenadas em cache localmente. Os itens a seguir são transmitidos ao servidor AEM imediatamente sem o cache local:

* Quaisquer operações em pastas, por exemplo, criar, excluir e assim por diante
* O recurso Carregamento de pasta introduzido na versão 1.4 carrega uma hierarquia de pasta local, sem armazenar os arquivos em cache localmente

## Operações individuais {#individual-operations}

Ao solucionar problemas de desempenho sub-otimizado para usuários individuais, consulte primeiro [Limitações](https://helpx.adobe.com/experience-manager/desktop-app/troubleshooting-desktop-app.html#limitations). As seções subsequentes incluem sugestões para melhorar o desempenho de usuários individuais.

## Recomendações de largura de banda {#bandwidth-recommendations}

A largura de banda disponível para um usuário individual desempenha um papel fundamental no desempenho do cliente WebDAV/SMB.

A Adobe recomenda que a velocidade de upload de um usuário individual esteja próxima a 10 Mbps. Para conexões sem fio, a largura de banda é frequentemente compartilhada entre vários usuários. Se vários usuários executarem simultaneamente tarefas que consomem largura de banda da rede, o desempenho pode diminuir ainda mais. Para evitar esses problemas, use uma conexão com fio.

## Configurações específicas do Windows {#windows-specific-configurations}

Se você executar AEM no Windows, poderá configurar o Windows para melhorar o desempenho do cliente WebDAV. Para obter mais informações, acesse [https://support.microsoft.com/en-us/kb/2445570](https://support.microsoft.com/en-us/kb/2445570).

No Windows 7, a modificação das configurações do IE pode melhorar o desempenho do WebDAV. Para obter detalhes, consulte como [corrigir o desempenho lento do WebDAV no Windows 7](https://oddballupdate.com/2009/12/fix-slow-webdav-performance-in-windows-7/).

## Operações simultâneas {#concurrent-operations}

Quando você interage com um arquivo localmente, AEM Desktop verifica se uma versão mais recente do arquivo está disponível no AEM. Se uma nova versão estiver disponível, o aplicativo baixa uma cópia atualizada do arquivo no cache local. No entanto, AEM desktop não substitui um arquivo em cache local se ele tiver sido modificado. Este recurso impede que seu trabalho seja substituído inadvertidamente.

Quando o mesmo arquivo é modificado localmente e no AEM, a versão modificada localmente substitui a versão no AEM. Nesse caso, a versão anterior está disponível na linha do tempo do ativo. Você pode verificar ambas as versões e resolver conflitos.

Se um arquivo local for inconsistente com a versão disponível no servidor, a caixa de diálogo de status do upload em segundo plano notificará você sobre o conflito. Para resolver o problema, abra o arquivo em conflito e salve-o. Salvar o arquivo força a área de trabalho AEM sincronizar as alterações locais mais recentes em AEM. Você pode visualização versões anteriores do ativo na linha do tempo e resolver conflitos.

Você deve levar em conta fatores adicionais quando vários usuários tentarem trabalhar em diretórios montados separados direcionando a mesma instância AEM. Em particular, são importantes os seguintes fatores:

* A quantidade de largura de banda disponível na rede de origem dos usuários
* Configuração de rede, como firewalls ou proxies, da rede de origem
* Quantidade de largura de banda disponível na rede da instância do público alvo AEM
* Se um dispatcher está presente antes da instância AEM do público alvo
* Carga atual na instância AEM público alvo

## Configurações adicionais de AEM {#additional-aem-configurations}

Se o desempenho do WebDAV/SMB diminuir drasticamente quando vários usuários trabalham simultaneamente, você pode configurar algumas coisas no AEM, o que pode ajudar a melhorar o desempenho.

## Atualizar workflows transientes de ativos {#update-asset-transient-workflows}

Você pode melhorar o desempenho no lado da AEM, habilitando workflows transitórios para o fluxo de trabalho do Ativo de atualização do DAM. Habilitar workflows transitórios reduz o poder de processamento necessário para atualizar ativos quando eles são criados ou modificados em AEM.

1. Navegue até `/miscadmin` na instância AEM a ser configurada (por exemplo, `http://[Server]:[Port]/miscadmin`).
1. Na árvore de navegação, expanda **Ferramentas** > **Fluxo de trabalho** > **Modelos** > **dam**.
1. Clique no duplo **Ativo de atualização do DAM**.
1. No painel de ferramentas flutuantes, alterne para a guia **Página** e clique em **Propriedades da página**.
1. Marque a caixa de seleção **Fluxo de trabalho temporário** e clique em **OK**.

### Ajustar fila de Fluxo de trabalho transitório do Granite {#adjust-granite-transient-workflow-queue}

Outro método para melhorar o desempenho AEM é configurar o valor máximo de trabalhos paralelos para o trabalho da Fila de Fluxo de Trabalho Transitório Granite. O valor recomendado é aproximadamente a metade do número da CPU disponível com o servidor. Para ajustar o valor, execute estas etapas:

1. Navegue até */system/console/configMgr* na instância de AEM a ser configurada (por exemplo, `http://[aem_server]:[port]/system/console/configMgr`).
1. Procure **QueueConfiguration** e clique para abrir cada tarefa até localizar a tarefa **Granite Transient Workflow Queue**. Clique em Editar ao lado.
1. Altere o valor **Máximo de Trabalhos Paralelos** e clique em **Salvar**.

## Configuração AWS {#aws-configuration}

Devido às limitações de largura de banda da rede, o desempenho do WebDAV/SMB pode diminuir quando vários usuários trabalham simultaneamente. O Adobe recomenda aumentar o tamanho da instância AWS para uma instância de AEM de público alvo executada no AWS para melhorar o desempenho do WebDAV/SMB.

Essa medida aumenta especificamente a quantidade de largura de banda de rede disponível para o servidor. Estes são alguns detalhes:

* A quantidade de largura de banda de rede dedicada a uma instância AWS aumenta à medida que o tamanho da instância aumenta. Para obter informações sobre a largura de banda disponível para cada tamanho de instância, consulte [documentação AWS](https://aws.amazon.com/ec2/instance-types/).
* Ao solucionar problemas para um cliente grande, o Adobe configurou o tamanho de sua instância AEM para c4.8xlarge, principalmente para os 4000 Mbps de largura de banda dedicada que ele fornece.
* Se houver um expedidor à frente da instância AEM, verifique se ele tem o tamanho apropriado. Se a instância AEM fornecer 4000 Mbps, mas o dispatcher fornecer apenas 500 Mbps, a largura de banda efetiva será de apenas 500 Mbps. É porque o dispatcher cria um gargalo de rede.

## Limitações de arquivo com check-out {#checked-out-file-limitations}

Há algumas limitações conhecidas na maneira como você pode interagir com arquivos com check-out por meio do Explorer/Finder. Se for dada saída de um arquivo, ele deverá ser somente leitura para qualquer pessoa, exceto o usuário que tiver feito check-out do arquivo. A implementação do protocolo WebDAV/SMB1 no AEM aplica esta regra. No entanto, os clientes WebDAV/SMB do SO geralmente não interagem normalmente com arquivos com check-out. Algumas esquisitices estão descritas abaixo.

### Geral {#general}

Ao gravar em um arquivo com check-out, o bloqueio é aplicado somente AEM implementação WebDAV. Consequentemente, o bloqueio só é imposto por clientes que usam o WebDAV, como o aplicativo de desktop. O bloqueio não é imposto por meio AEM interface da Web. A interface AEM apenas exibe um ícone de cadeado na visualização do cartão para os ativos com check-out. O ícone é cosmético e não tem efeito no comportamento da AEM.

Em geral, os clientes WebDAV nem sempre se comportam como esperado. Pode haver outros problemas. No entanto, atualizar ou verificar o ativo em AEM é uma maneira sólida de verificar se um ativo não está sendo modificado. Esse comportamento é típico do OS WebDAV, que não está sob controle do Adobe.

### Windows {#windows}

A exclusão de um arquivo parece ter êxito porque ele desaparece do explorador de arquivos no Windows. No entanto, atualizar o diretório e fazer check-in AEM ativos mostra que o arquivo ainda está presente. Além disso, a edição de arquivos parece ter êxito (nenhuma caixa de diálogo de aviso ou mensagem de erro é exibida). No entanto, reabrir o arquivo ou fazer check-in AEM ativos revela que o arquivo permanece inalterado.

#### Mac OS X {#mac-os-x}

A substituição de um arquivo não exibe um aviso ou erro, mas a verificação do ativo no AEM revela que ele permanece inalterado. Atualize ou verifique o ativo no AEM para verificar se ele não está sendo modificado.

## Solução de problemas de ícone do aplicativo de desktop (Mac OS X) {#troubleshooting-desktop-app-icon-issues-mac-os-x}

Depois de instalar o aplicativo de desktop, o ícone de menu do aplicativo de desktop aparece na barra de menus. Se o ícone não for exibido, execute estas etapas para resolver o problema:

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

AEM desktop tenta sincronizar qualquer arquivo três vezes. Se o arquivo falhar na sincronização após a terceira tentativa, AEM Desktop considerará o arquivo em conflito e o notificará por meio da janela de status do upload em segundo plano. Um estado de conflito indica que suas alterações mais recentes ainda estão disponíveis localmente, mas não são sincronizadas de volta para AEM. AEM aplicativo de desktop não tenta mais sincronizar.

A maneira mais simples de corrigir essa situação é abrir o arquivo em conflito e salvá-lo novamente. Ela força AEM desktop a tentar a sincronização por mais três ocasiões. Se o arquivo ainda falhar na sincronização, consulte as seções abaixo para obter mais ajuda.

## Limpando AEM cache da área de trabalho {#clearing-aem-desktop-cache}

Limpar AEM cache da área de trabalho é uma tarefa preliminar de solução de problemas que pode resolver vários problemas AEM da área de trabalho.

Você pode limpar o cache excluindo o diretório de cache do aplicativo nos seguintes locais.
No Windows, `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

No Mac, `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

No entanto, o local pode mudar dependendo do ponto final AEM da área de trabalho configurado AEM. O valor é uma versão codificada do URL direcionado. Por exemplo, se o aplicativo estiver direcionando `http://localhost:4502`, o nome do diretório será `http%3A%2F%2Flocalhost%3A4502%2F`.

Para limpar o cache, exclua o diretório &lt;Encoded AEM Endpoint>.

>[!NOTE]
>
>Se você limpar AEM cache da área de trabalho, as alterações de arquivo local que não são sincronizadas com AEM serão perdidas.

>[!NOTE]
>
>A partir AEM aplicativo de desktop versão 1.5, há uma opção na interface do usuário do aplicativo de desktop para limpar o cache.

## Localizando a versão da área de trabalho AEM {#finding-the-aem-desktop-version}

O procedimento para determinar a versão da área de trabalho AEM é o mesmo para Windows e Mac OS.

Clique no ícone AEM área de trabalho e escolha **Sobre**. O número da versão é exibido na tela.

## Atualização AEM aplicativo de desktop no macOS {#upgrading-aem-desktop-app-on-macos}

Ocasionalmente, podem ocorrer problemas ao atualizar AEM aplicativo desktop no macOS. Isso é causado pela pasta herdada do sistema para AEM aplicativo de desktop que impede que novas versões AEM desktop sejam carregadas corretamente. Para resolver esse problema, as pastas e os arquivos a seguir podem ser removidos manualmente.

Antes de executar as etapas abaixo, arraste o aplicativo &quot;Adobe Experience Manager Desktop&quot; da pasta Aplicativos macOS para a lixeira. Em seguida, abra o terminal e execute o seguinte comando, fornecendo sua senha quando solicitado.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## Salvar um arquivo com check-out feito por outras pessoas {#saving-a-file-checked-out-by-others}

As limitações técnicas do sistema operacional impedem que os usuários tenham uma experiência consistente ao tentar substituir um arquivo cujo check-out foi feito por outras pessoas. A experiência varia dependendo do aplicativo usado para editar o arquivo com check-out. Às vezes, o aplicativo exibe uma mensagem de erro indicando uma falha de gravação de disco ou um erro aparentemente não relacionado ou genérico. Em outras ocasiões, nenhuma mensagem de erro é exibida e a operação parece ter êxito.

Nesse caso, fechar e reabrir o arquivo pode revelar que o conteúdo não é alterado. No entanto, alguns aplicativos podem armazenar um backup do arquivo para que suas alterações possam ser aplicadas.

Independentemente do comportamento, o arquivo permanece inalterado quando você faz o check-in. Mesmo se uma versão diferente do arquivo for exibida, as alterações não serão sincronizadas para AEM.

## Solução de problemas ao mover arquivos {#troubleshooting-problems-around-moving-files}

A API do servidor requer cabeçalhos adicionais, Destino X, Profundidade X e Substituição X para que as operações de movimentação e cópia funcionem. O dispatcher não passa esses cabeçalhos por padrão, o que resulta em falha dessas operações. Para obter mais informações, consulte [Conexão com AEM atrás de um Dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Solução de problemas AEM conexão da área de trabalho {#troubleshooting-aem-desktop-connection-issues}

### Problema de redirecionamento SAML {#saml-redirect-issue}

O motivo mais comum para problemas com a área de trabalho AEM se conectando à sua instância de AEM ativada por SSO (SAML) é que o processo SAML não redireciona para o caminho solicitado originalmente. Como alternativa, a conexão pode ser redirecionada para um host que não está configurado AEM área de trabalho. Execute estas etapas para verificar o processo de logon:

1. Abra um navegador da Web.
1. Na barra de endereços, especifique o URL `/content/dam.json`.
1. Substitua o URL pela instância AEM público alvo, por exemplo `http://localhost:4502/content/dam.json`.
1. Faça logon no AEM.
1. Depois de fazer logon, verifique o endereço atual do navegador na barra de endereços. Deve corresponder ao URL inserido inicialmente.
1. Verifique se tudo antes de `/content/dam.json` corresponde ao valor AEM do público alvo configurado na área de trabalho AEM.

### Problema de configuração SSL {#ssl-configuration-issue}

As bibliotecas que AEM aplicativo de desktop usa para comunicação HTTP utilizam imposição rigorosa de SSL. Às vezes, uma conexão pode ser bem-sucedida usando um navegador, mas falha ao usar AEM aplicativo de desktop. Para configurar o SSL adequadamente, instale o certificado intermediário ausente no Apache. Consulte [Como instalar um certificado CA intermediário no Apache](https://access.redhat.com/solutions/43575).

## Uso da área de trabalho AEM com o dispatcher {#using-aem-desktop-with-dispatcher}

AEM desktop trabalha com implantações AEM atrás de um dispatcher, que é uma configuração padrão e recomendada para AEM servidores. AEM despachantes na frente dos ambientes de criação AEM geralmente são configurados para ignorar o armazenamento em cache de ativos DAM. Portanto, os despachantes não fornecem armazenamento em cache adicional do ponto de vista da área de trabalho AEM. Verifique se a configuração do dispatcher está ajustada para funcionar AEM desktop. Para obter mais detalhes, consulte [Ligar a AEM atrás de um dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Verificando arquivos de registro {#checking-for-log-files}

Dependendo do sistema operacional, você pode encontrar os arquivos de registro para AEM desktop nos seguintes locais:

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`
* Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`
