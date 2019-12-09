---
title: Solução de problemas do aplicativo AEM para desktop versão 1.x
description: Solucione problemas do aplicativo AEM para desktop versão 1.x para resolver problemas ocasionais relacionados à instalação, atualização, configuração e assim por diante.
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ad5337c8e1697d0a37d3020d25802dc1d732f320

---


# Solução de problemas do aplicativo de desktop AEM v1.x {#troubleshoot-aem-desktop-app}

Solucione problemas do aplicativo de desktop AEM para resolver problemas ocasionais relacionados à instalação, atualização, configuração e assim por diante.

O aplicativo de desktop Adobe Experience Manager (AEM) inclui utilitários que ajudam a mapear o repositório dos ativos AEM como um compartilhamento de rede no desktop (compartilhamento SMB no Mac OS). O compartilhamento de rede é uma tecnologia de sistema operacional que permite que fontes remotas sejam tratadas como se fossem parte de um sistema de arquivos local do computador. No caso de um aplicativo de desktop, a estrutura de repositório DAM (digital asset management, gerenciamento de ativos digitais) de uma instância remota do AEM é direcionada como a fonte de arquivos remotos. O diagrama a seguir descreve a topologia do aplicativo de desktop:

![diagrama do aplicativo desktop](assets/aem-desktopapp-architecture.png)

Com essa arquitetura, o aplicativo desktop intercepta chamadas do sistema de arquivos (abrir, fechar, ler, gravar e assim por diante) no compartilhamento de rede montado e as converte em chamadas HTTP nativas do AEM para o servidor AEM. Os arquivos são armazenados em cache localmente. Para obter mais detalhes, consulte [Usar o aplicativo de desktop AEM v1.x](use-app-v1.md).

## AEM desktop app component overview {#desktop-app-component-overview}

o aplicativo desktop inclui os seguintes componentes:

* **O aplicativo** desktop: O aplicativo monta ou desmonta o DAM como um sistema de arquivos remoto e traduz as chamadas do sistema de arquivos entre o compartilhamento de rede montado localmente e a instância remota do AEM à qual ele se conecta.
* **Cliente** WebDAV/SMB do sistema operacional: Trata da comunicação entre o Windows Explorer/Finder e o aplicativo de desktop. Se um arquivo for recuperado, criado, modificado, excluído, movido ou copiado, o cliente WebDAV/SMB do sistema operacional (OS) comunicará esta operação para o aplicativo de desktop. Depois de receber a comunicação, o aplicativo de desktop a converte em chamadas de API remota nativas do AEM. Por exemplo, se um usuário cria um arquivo no diretório montado, o cliente WebDAV/SMB inicia uma solicitação, que o aplicativo desktop converte em uma solicitação HTTP que cria o arquivo no DAM. O cliente WebDAV/SMB é um componente incorporado do SO. Ele não é afiliado a aplicativos de desktop, AEM ou Adobe de nenhuma forma.
* **Instância** do Adobe Experience Manager: Fornece acesso aos ativos armazenados no repositório DAM do AEM Assets. Além disso, ele executa ações solicitadas pelo aplicativo desktop em nome dos aplicativos de desktop locais que interagem com o compartilhamento de rede montado. A instância de AEM de destino deve executar o AEM versão 6.1 ou superior. Instâncias do AEM que executam versões anteriores do AEM podem exigir pacotes de recursos adicionais e hot fixes instalados para se tornarem totalmente funcionais.

## Casos de uso pretendido para o aplicativo de desktop AEM {#intended-use-cases-for-aem-desktop-app}

O aplicativo de desktop AEM usa a tecnologia de compartilhamento de rede para mapear um repositório AEM remoto para um desktop local. No entanto, não se destina a substituir um compartilhamento de rede que contém ativos, onde os usuários executam operações de gerenciamento de ativos digitais diretamente de seu desktop local. Isso inclui mover ou copiar vários arquivos, ou arrastar estruturas de pastas grandes para o compartilhamento de rede do AEM Assets diretamente no Finder/Explorer.

O aplicativo de desktop AEM fornece uma maneira conveniente de acessar (abrir) e editar (salvar) ativos DAM entre a interface de usuário de toque do AEM Assets e a área de trabalho local. Ela vincula ativos no servidor do AEM Assets aos fluxos de trabalho baseados em desktop.

O exemplo de uso a seguir ilustra como o AEM Desktop deve ser usado:

* Um usuário faz logon no AEM e usa a interface do usuário da Web para localizar um ativo.
* Usando os recursos de ação da área de trabalho da interface do usuário da Web do AEM, o usuário abre, exibe ou edita o ativo na área de trabalho, conforme necessário.
* O AEM Desktop abre o ativo no editor padrão para o tipo de arquivo do ativo.
* O usuário faz as alterações desejadas no ativo.
* Depois que um arquivo é modificado, o usuário pode exibir o status de sincronização do arquivo usando a janela de status de sincronização em segundo plano da área de trabalho do AEM.
* Usando o menu de contexto do AEM Desktop, o usuário faz check-in/check-out do ativo ou retorna à interface do usuário do DAM.
* Após concluir as alterações no arquivo, o usuário retorna à interface do usuário da Web do AEM

Este não é o único caso de uso. No entanto, isso ilustra como o AEM Desktop é um mecanismo conveniente para acessar/editar ativos localmente. É recomendável usar a interface do usuário da Web do DAM o máximo possível, pois ela fornece uma experiência melhor. Ele oferece à Adobe mais flexibilidade para atender às necessidades do cliente.

## Limitações {#limitations}

O compartilhamento de rede WebDAV/SMB1 oferece a conveniência de trabalhar com arquivos em uma janela do Explorer/Finder. No entanto, o Explorer/Finder e o AEM se comunicam por uma conexão de rede que tem certas limitações. Por exemplo, o tempo gasto para copiar um arquivo de 1 GB para o diretório WebDAV/SMB montado é aproximadamente o mesmo que o tempo necessário para carregar um arquivo de 1 GB para um site usando um navegador da Web. Na verdade, no primeiro caso, a duração pode ser mais longa devido às ineficiências do protocolo WebDAV/SMB e dos clientes WebDAV/SMB do SO (especialmente Mac OS X).

Há limitações para os tipos de tarefas que podem ser executadas a partir de um diretório montado. Em geral, trabalhar com arquivos grandes, especialmente em uma conexão de rede de baixa/alta latência/largura de banda baixa, pode ser um desafio, especialmente ao editar arquivos grandes.

A Adobe recomenda que você execute alguns testes de caso de uso antes de confirmar para um cliente que certos tipos de arquivos podem ser editados no local com eficiência a partir do diretório montado.

O AEM Desktop não é adequado para a manipulação intensiva do sistema de arquivos, incluindo, mas não se limitando a:

* Mover ou copiar arquivos e diretórios
* Adicionar muitos ativos ao AEM
* Procurando e abrindo arquivos pelo sistema de arquivos, exceto por pastas de navegação
* Compactação ou descompactação de arquivos

Devido a limitações no sistema operacional, o Windows tem uma limitação de tamanho de arquivo de 4.294.967.295 bytes (aproximadamente 4,29 GB). É devido a uma configuração de registro que define o tamanho de um arquivo em um compartilhamento de rede. O valor da configuração do Registro é um DWORD com um tamanho máximo igual ao número referenciado.

## Cache e comunicação com o AEM {#caching-and-communication-with-aem}

O aplicativo de desktop AEM fornece recursos internos de cache e upload em segundo plano para melhorar a experiência do usuário final. Quando você salva um arquivo grande, ele é salvo localmente pela primeira vez para permitir que você continue trabalhando. Depois de algum tempo (atualmente 30 segundos), o arquivo é enviado para o servidor AEM em segundo plano.

Ao contrário da Creative Cloud Desktop ou de outras soluções de sincronização de arquivos, como Microsoft One Drive, o aplicativo de desktop AEM não é um cliente completo de Sincronização de desktop. Isso ocorre porque fornece acesso a todo o repositório dos ativos AEM, que pode ser extremamente grande (centenas de gigabytes ou terabytes) para uma sincronização completa.

O cache oferece a capacidade de limitar a sobrecarga de rede/armazenamento somente a um subconjunto de ativos relevantes para o usuário.

Veja como o aplicativo de desktop AEM executa o cache:

* Quando você abre uma pasta no Finder e as miniaturas/visualizações de arquivos são exibidas ou quando você abre um arquivo em um aplicativo, o aplicativo desktop armazena o arquivo em cache binário.
* Quando você armazena arquivos via Finder ou outros aplicativos de desktop, o arquivo é armazenado localmente primeiro (em cache) e o sistema operacional é notificado. O arquivo é então colocado na fila para upload no servidor em segundo plano e eventualmente carregado pela rede. Em caso de erro de rede, o aplicativo desktop tenta carregar o arquivo inteiro novamente por um máximo de três vezes. Se o upload não for feito após três tentativas, o arquivo será marcado como um arquivo em conflito e o status será exibido por meio da janela Status da fila de upload em segundo plano. o aplicativo de desktop não tenta mais atualizar o arquivo. O usuário deve atualizar o arquivo e carregá-lo novamente depois que a conectividade for restaurada

Todas as operações não são armazenadas em cache localmente. Os itens a seguir são transmitidos ao servidor AEM imediatamente sem o cache local:

* Quaisquer operações em pastas, por exemplo, criar, excluir e assim por diante
* O recurso Carregamento de pasta introduzido na versão 1.4 carrega uma hierarquia de pasta local, sem armazenar os arquivos em cache localmente

## Operações individuais {#individual-operations}

Ao solucionar problemas de desempenho sub-otimizado para usuários individuais, consulte primeiro [Limitações](https://helpx.adobe.com/experience-manager/desktop-app/troubleshooting-desktop-app.html#limitations). As seções subsequentes incluem sugestões para melhorar o desempenho de usuários individuais.

## Recomendações de largura de banda {#bandwidth-recommendations}

A largura de banda disponível para um usuário individual desempenha um papel fundamental no desempenho do cliente WebDAV/SMB.

A Adobe recomenda que a velocidade de upload de um usuário individual esteja próxima a 10 Mbps. Para conexões sem fio, a largura de banda é frequentemente compartilhada entre vários usuários. Se vários usuários executarem simultaneamente tarefas que consomem largura de banda da rede, o desempenho pode diminuir ainda mais. Para evitar esses problemas, use uma conexão com fio.

## Configurações específicas do Windows {#windows-specific-configurations}

Se você executar o AEM no Windows, poderá configurar o Windows para melhorar o desempenho do cliente WebDAV. Para obter mais informações, acesse [https://support.microsoft.com/en-us/kb/2445570](https://support.microsoft.com/en-us/kb/2445570).

No Windows 7, a modificação das configurações do IE pode melhorar o desempenho do WebDAV. Para obter detalhes, visite [http://oddballupdate.com/2009/12/fix-slow-webdav-performance-in-windows-7/](http://oddballupdate.com/2009/12/fix-slow-webdav-performance-in-windows-7/).

## Operações simultâneas {#concurrent-operations}

Quando você interage com um arquivo localmente, o AEM Desktop verifica se uma versão mais recente do arquivo está disponível no AEM. Se uma nova versão estiver disponível, o aplicativo baixa uma cópia atualizada do arquivo no cache local. No entanto, o AEM Desktop não substitui um arquivo em cache local se ele tiver sido modificado. Este recurso impede que seu trabalho seja substituído inadvertidamente.

Quando o mesmo arquivo é modificado localmente e no AEM, a versão modificada localmente substitui a versão no AEM. Nesse caso, a versão anterior está disponível na linha do tempo do ativo. Você pode verificar ambas as versões e resolver conflitos.

Se um arquivo local for inconsistente com a versão disponível no servidor, a caixa de diálogo de status do upload em segundo plano notificará você sobre o conflito. Para resolver o problema, abra o arquivo em conflito e salve-o. Salvar o arquivo força o AEM Desktop a sincronizar as alterações locais mais recentes no AEM. É possível exibir versões anteriores do ativo na linha do tempo e resolver conflitos.

Você deve levar em conta fatores adicionais quando vários usuários tentarem trabalhar em diretórios montados separados direcionados à mesma instância do AEM. Em particular, são importantes os seguintes fatores:

* A quantidade de largura de banda disponível na rede de origem dos usuários
* Configuração de rede, como firewalls ou proxies, da rede de origem
* Quantidade de largura de banda disponível na rede da instância de AEM de destino
* Se um dispatcher está presente antes da instância de AEM de destino
* Carga atual na instância de AEM de destino

## Configurações AEM adicionais {#additional-aem-configurations}

Se o desempenho do WebDAV/SMB diminuir drasticamente quando vários usuários trabalham simultaneamente, você pode configurar algumas coisas no AEM, o que pode ajudar a melhorar o desempenho.

## Atualizar fluxos de trabalho temporários de ativos {#update-asset-transient-workflows}

Você pode melhorar o desempenho no lado do AEM, ativando fluxos de trabalho transitórios para o fluxo de trabalho do Ativo de atualização do DAM. Habilitar fluxos de trabalho transitórios reduz o poder de processamento necessário para atualizar ativos quando eles são criados ou modificados no AEM.

1. Navegue até `/miscadmin` a instância do AEM a ser configurada (por exemplo, `http://[Server]:[Port]/miscadmin`).
1. Na árvore de navegação, expanda **Ferramentas** &gt; **Fluxo de trabalho** &gt; **Modelos** &gt; **dam**.
1. Clique duas vezes em Ativo **de atualização** DAM.
1. No painel de ferramentas flutuantes, alterne para a guia **Página** e clique em Propriedades **** da página.
1. Marque a caixa de seleção Fluxo de trabalho **temporário e clique em** OK ****.

### Ajustar fila de Fluxo de trabalho transitório do Granite {#adjust-granite-transient-workflow-queue}

Outro método para melhorar o desempenho do AEM é configurar o valor máximo de trabalhos paralelos para o trabalho da Fila de Fluxo de Trabalho Transitório Granite. O valor recomendado é aproximadamente a metade do número da CPU disponível no servidor. Para ajustar o valor, execute estas etapas:

1. Navegue até */system/console/configMgr* na instância do AEM a ser configurada (por exemplo, <http://&lt;Server&gt;:&lt;Port&gt;/system/console/configMgr>).
1. Procure **QueueConfiguration** e clique para abrir cada tarefa até localizar o trabalho **Granite Transient Workflow Queue** . Clique no ícone Editar ao lado dele.
1. Altere o valor **Máximo de Trabalhos** Paralelos e clique em **Salvar**.

## Configuração AWS {#aws-configuration}

Devido às limitações de largura de banda da rede, o desempenho do WebDAV/SMB pode diminuir quando vários usuários trabalham simultaneamente. A Adobe recomenda aumentar o tamanho da instância AWS para uma instância de AEM de destino que é executada no AWS para melhorar o desempenho do WebDAV/SMB.

Essa medida aumenta especificamente a quantidade de largura de banda de rede disponível para o servidor. Veja alguns detalhes:

* A quantidade de largura de banda de rede dedicada a uma instância AWS aumenta à medida que o tamanho da instância aumenta. Para obter informações sobre a largura de banda disponível para cada tamanho de instância, consulte a documentação [](https://aws.amazon.com/ec2/instance-types/)AWS.
* Ao solucionar problemas para um cliente grande, a Adobe configurou o tamanho de sua instância do AEM para c4.8xlarge, principalmente para os 4000 Mbps de largura de banda dedicada que ela fornece.
* Se houver um despachante antes da instância do AEM, verifique se ele tem o tamanho apropriado. Se a instância do AEM fornecer 4000 Mbps, mas o dispatcher fornecer apenas 500 Mbps, a largura de banda efetiva será de apenas 500 Mbps. É porque o dispatcher cria um gargalo de rede.

## Limitações de arquivo com check-out {#checked-out-file-limitations}

Há algumas limitações conhecidas na maneira como você pode interagir com arquivos com check-out por meio do Explorer/Finder. Se for dada saída de um arquivo, ele deverá ser somente leitura para qualquer pessoa, exceto o usuário que tiver feito check-out do arquivo. A implementação do protocolo WebDAV/SMB1 no AEM aplica esta regra. No entanto, os clientes WebDAV/SMB do SO geralmente não interagem normalmente com arquivos com check-out. Algumas esquisitices estão descritas abaixo.

### Geral {#general}

Ao gravar em um arquivo com check-out, o bloqueio é aplicado somente na implementação do AEM WebDAV. Consequentemente, o bloqueio só é imposto por clientes que usam o WebDAV, como o aplicativo de desktop. O bloqueio não é imposto pela interface da Web do AEM. A interface do AEM apenas exibe um ícone de cadeado na exibição de cartão para os ativos com check-out. O ícone é superficial e não tem efeito sobre o comportamento do AEM.

Em geral, os clientes WebDAV nem sempre se comportam como esperado. Pode haver outros problemas. No entanto, atualizar ou verificar o ativo no AEM é uma forma sólida de verificar se um ativo não está sendo modificado. Esse comportamento é típico dos clientes do OS WebDAV, que não estão sob o controle da Adobe.

### Windows {#windows}

A exclusão de um arquivo parece ter êxito porque ele desaparece do explorador de arquivos no Windows. Entretanto, atualizar o diretório e fazer check-in dos ativos AEM mostra que o arquivo ainda está presente. Além disso, a edição de arquivos parece ter êxito (nenhuma caixa de diálogo de aviso ou mensagem de erro é exibida). Entretanto, reabrir o arquivo ou fazer check-in dos ativos AEM revela que o arquivo não foi alterado.

#### Mac OS X {#mac-os-x}

Substituir um arquivo não exibe um aviso ou erro, mas verificar o ativo no AEM revela que ele permanece inalterado. Atualize ou verifique o ativo no AEM para verificar se ele não está sendo modificado.

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

O AEM Desktop tenta sincronizar qualquer arquivo três vezes. Se o arquivo não for sincronizado após a terceira tentativa, a área de trabalho do AEM considerará o arquivo em conflito e o notificará por meio da janela de status do upload em segundo plano. Um estado de conflito indica que suas alterações mais recentes ainda estão disponíveis localmente para você, mas não são sincronizadas de volta para o AEM. O aplicativo de desktop AEM não tenta mais sincronizar.

A maneira mais simples de corrigir essa situação é abrir o arquivo em conflito e salvá-lo novamente. Ela força o AEM Desktop a tentar sincronizar por mais três ocasiões. Se o arquivo ainda falhar na sincronização, consulte as seções abaixo para obter mais ajuda.

## Limpar o cache da área de trabalho do AEM {#clearing-aem-desktop-cache}

Limpar o cache do AEM Desktop é uma tarefa preliminar de solução de problemas que pode resolver vários problemas do AEM Desktop.

Você pode limpar o cache excluindo o diretório de cache do aplicativo nos seguintes locais:Windows: %LocalAppData%\Adobe\AssetsCompanion\Cache\

Mac: ~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/

No entanto, o local pode ser alterado dependendo do ponto de extremidade AEM configurado para desktop. O valor é uma versão codificada do URL direcionado. Por exemplo, se o aplicativo estiver direcionando `http://localhost:4502`, o nome do diretório será `http%3A%2F%2Flocalhost%3A4502%2F`.

Para limpar o cache, exclua o diretório &lt;Endpoint AEM codificado&gt;.

>[!NOTE]
>
>Se você limpar o cache da área de trabalho do AEM, as alterações de arquivo local que não são sincronizadas com o AEM serão perdidas.

>[!NOTE]
>
>A partir do aplicativo de desktop AEM versão 1.5, há uma opção na interface do usuário do aplicativo de desktop para limpar o cache.

## Como encontrar a versão da área de trabalho do AEM {#finding-the-aem-desktop-version}

O procedimento para determinar a versão do AEM Desktop é o mesmo para Windows e Mac OS.

Clique no ícone da área de trabalho do AEM e escolha **Sobre**. O número da versão é exibido na tela.

## Atualização do aplicativo de desktop AEM no macOS {#upgrading-aem-desktop-app-on-macos}

Ocasionalmente, podem ocorrer problemas ao atualizar o aplicativo de desktop AEM no MacOS. Isso é causado pelo fato de a pasta de sistema herdada para o aplicativo de desktop AEM impedir que novas versões do desktop AEM sejam carregadas corretamente. Para resolver esse problema, as pastas e os arquivos a seguir podem ser removidos manualmente.

Antes de executar as etapas abaixo, arraste o aplicativo "Adobe Experience Manager Desktop" da pasta Aplicativos MacOS para a lixeira. Em seguida, abra o terminal e execute o seguinte comando, fornecendo sua senha quando solicitado.

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

Independentemente do comportamento, o arquivo permanece inalterado quando você faz o check-in. Mesmo se uma versão diferente do arquivo for exibida, as alterações não serão sincronizadas com o AEM.

## Solução de problemas ao mover arquivos {#troubleshooting-problems-around-moving-files}

A API do servidor requer cabeçalhos adicionais, Destino X, Profundidade X e Substituição X para que as operações de movimentação e cópia funcionem. O dispatcher não passa esses cabeçalhos por padrão, o que resulta em falha dessas operações. Para obter mais informações, consulte [Conexão com o AEM atrás de um Dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Solução de problemas de conexão de desktop do AEM {#troubleshooting-aem-desktop-connection-issues}

### Problema de redirecionamento SAML {#saml-redirect-issue}

O motivo mais comum para problemas com a área de trabalho do AEM se conectando à sua instância do AEM habilitada por SSO (SAML) é que o processo SAML não redireciona de volta para o caminho solicitado originalmente. Como alternativa, a conexão pode ser redirecionada para um host que não está configurado na área de trabalho do AEM. Execute estas etapas para verificar o processo de logon:

1. Abra um navegador da Web.
1. Na barra de endereços, especifique o URL `/content/dam.json`.
1. Substitua o URL pela instância de AEM de destino, por exemplo `http://localhost:4502/content/dam.json`.
1. Faça logon no AEM.
1. Depois de fazer logon, verifique o endereço atual do navegador na barra de endereços. Deve corresponder ao URL inserido inicialmente.
1. Verifique se tudo antes corresponde `/content/dam.json` ao valor AEM de destino configurado na área de trabalho do AEM.

### Problema de configuração SSL {#ssl-configuration-issue}

As bibliotecas que o aplicativo de desktop AEM usa para comunicação HTTP utilizam imposição rigorosa de SSL. Às vezes, uma conexão pode ser bem-sucedida usando um navegador, mas falha ao usar o aplicativo de desktop AEM. Para configurar o SSL adequadamente, instale o certificado intermediário ausente no Apache. Consulte [Como instalar um certificado CA intermediário no Apache](https://access.redhat.com/solutions/43575).

## Usar o AEM Desktop com o dispatcher {#using-aem-desktop-with-dispatcher}

A área de trabalho do AEM trabalha com implantações do AEM atrás de um despachante, que é uma configuração padrão e recomendada para servidores AEM. Os despachantes do AEM na frente dos ambientes de criação do AEM geralmente são configurados para ignorar o armazenamento em cache de ativos do DAM. Portanto, os despachantes não fornecem armazenamento em cache adicional do ponto de vista de desktop do AEM. Verifique se a configuração do dispatcher está ajustada para funcionar no AEM Desktop. Para obter mais detalhes, consulte [Conexão com o AEM atrás de um despachante](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Verificando arquivos de registro {#checking-for-log-files}

Dependendo do sistema operacional, você pode encontrar os arquivos de registro para o AEM Desktop nos seguintes locais:

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`
* Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`