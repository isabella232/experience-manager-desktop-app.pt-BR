---
title: Práticas recomendadas e solução de problemas para aplicativos de desktop Adobe Experience Manager
description: Siga as práticas recomendadas e solucione problemas para resolver problemas ocasionais relacionados à instalação, atualização, configuração e assim por diante.
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.5/ASSETS, SG_EXPERIENCEMANAGER/6.4/ASSETS, SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 200135fb96bbfcf9f72e857514bb9b71a88ed817
workflow-type: tm+mt
source-wordcount: '2228'
ht-degree: 0%

---


# Troubleshoot Adobe Experience Manager desktop app {#troubleshoot-v2}

O aplicativo de desktop Adobe Experience Manager (AEM) se conecta a um repositório DAM (Digital Asset Management, gerenciamento de ativos digitais) de implantação remota. O aplicativo obtém informações do repositório e resultados da pesquisa em seu computador, baixa e carrega arquivos e pastas e inclui recursos para gerenciar conflitos com a interface do usuário do AEM Assets.

Leia para solucionar problemas do aplicativo, aprender as práticas recomendadas e descobrir as limitações.

## Best practices {#best-practices-to-prevent-troubles}

Siga as práticas recomendadas a seguir para evitar alguns problemas comuns e a solução de problemas.

* **Entenda como o aplicativo de desktop funciona**: Antes de começar a usar o aplicativo, passe alguns momentos sabendo como ele funciona. Saiba mais sobre a vinculação entre a interface da Web do Experience Manager e o desktop, o mapeamento do repositório, o armazenamento em cache de ativos, a gravação local e o upload em segundo plano. Veja [como funciona](release-notes.md#how-app-works).

* **Evite caracteres não suportados em nomes** de pastas: Não use espaços em branco e caracteres inválidos ao criar ou carregar pastas. Consulte uma lista de caracteres em [Criar pastas em Ativos](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders)Experience Manager. Alguns casos de uso do Adobe Experience Manager podem ser afetados por caracteres não suportados no nome da pasta.

* **Práticas recomendadas para evitar conflitos**: Para evitar conflitos em potencial ao colaborar em vários ativos, consulte [evitar conflitos](using.md#adv-workflow-collaborate-avoid-conflicts)de edição.

* **Use o upload de pasta para pastas** grandes e hierárquicas: Em vez de usar a interface da Web do Assets ou outros métodos, use o aplicativo de desktop Experience Manager para fazer upload de pastas grandes. O aplicativo carrega os ativos em segundo plano com o registro e o monitoramento. Consulte [fazer upload de ativos](using.md#bulk-upload-assets)em massa.

* **Use a versão** mais recente: Use a versão mais recente do aplicativo e sempre verifique a compatibilidade antes de instalar uma nova versão do aplicativo ou antes de atualizar para uma versão mais recente do Adobe Experience Manager. See [release notes](release-notes.md).

* **Use a mesma letra** de unidade: Use a mesma letra de unidade em uma organização para mapear para o Adobe Experience Manager DAM. Para ver os ativos colocados por outros usuários, os caminhos devem ser os mesmos. Usar a mesma letra de unidade garante um caminho constante para ativos DAM. Os ativos permanecem posicionados e não são removidos mesmo se letras de unidade diferentes forem usadas por usuários diferentes.

* **Lembre-se da rede**: O desempenho da rede é essencial para o desempenho do aplicativo de desktop Experience Manager. Se você enfrentar uma resposta lenta a transferências de arquivos ou operações em massa, desative os recursos ou aplicativos que podem causar muito tráfego de rede.

* **Casos de uso não suportados para aplicativos** de desktop: Não use o aplicativo para a migração do Assets (ele precisa de planejamento e outras ferramentas); para operações DAM de uso intenso (como mover pastas grandes, uploads grandes, localizar arquivos usando pesquisas avançadas de metadados); e como um cliente de sincronização (os princípios de design e os padrões de uso são diferentes dos clientes em sincronia, como o Microsoft OneDrive ou o Adobe Creative Cloud Desktop Sync).

* **Tempo limite**: Atualmente, o aplicativo de desktop não tem um valor de tempo limite configurável que desconecta a conexão entre o servidor de Experience Manager e o aplicativo de desktop após um intervalo de tempo fixo. Ao fazer upload de ativos grandes, se a conexão expirar depois de algum tempo, o aplicativo tentativas fazer upload do ativo algumas vezes aumentando o tempo limite de upload. Não há uma maneira recomendada de alterar as configurações de tempo limite padrão.

## Como solucionar problemas {#troubleshooting-prep}

Para solucionar problemas com o aplicativo de desktop, tenha em mente as seguintes informações. Além disso, ele o prepara para transmitir melhor os problemas ao Atendimento ao cliente da Adobe se você optar por buscar suporte.

### Localização dos ficheiros de registro {#check-log-files-v2}

[!DNL Experience Manager] o aplicativo desktop armazena seus arquivos de registro nos seguintes locais, dependendo do sistema operacional:

No Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

No Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

Ao fazer upload de muitos ativos, se alguns arquivos não forem carregados, consulte o `backend.log` arquivo para identificar os uploads que falharam.

>[!NOTE]
>
>Ao trabalhar com o Atendimento ao cliente do Adobe em uma solicitação de suporte ou ticket, você pode ser solicitado a compartilhar os arquivos de registro para ajudar a equipe do Atendimento ao cliente a entender o problema. Arquive a `Logs` pasta inteira e compartilhe-a com seu contato com o Atendimento ao cliente.

### Alterar o nível de detalhes nos arquivos de registro {#level-of-details-in-log}

Para alterar o nível de detalhes nos arquivos de registro:

1. Verifique se o aplicativo não está em execução.

1. No sistema Windows:

   1. Abra uma janela de comando.

   1. Inicie o aplicativo [!DNL Adobe Experience Manager] desktop executando o comando:

   ```shell
   set AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe
   ```

   No sistema Mac:

   1. Abra uma janela de terminal.

   1. Inicie o aplicativo [!DNL Adobe Experience Manager] desktop executando o comando:

   ```shell
   AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app
   ```

Os níveis de log válidos são DEBUG, INFO, WARN ou ERROR. A verbosidade dos registros é mais alta em DEBUG e mais baixa em ERROR.

### Ativar o modo de depuração {#enable-debug-mode}

Para solucionar problemas, você pode ativar o modo de depuração e obter mais informações nos registros.

>[!NOTE]
>
>Os níveis de log válidos são DEBUG, INFO, WARN ou ERROR. A verbosidade dos registros é mais alta em DEBUG e mais baixa em ERROR.

Para usar o aplicativo no modo de depuração no Mac:

1. Abra uma janela de terminal ou um prompt de comando.

1. Inicie o aplicativo para [!DNL Experience Manager] desktop executando o seguinte comando:

   `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`.

Para ativar o modo de depuração no Windows:

1. Abra uma janela de comando.

1. Inicie o aplicativo [!DNL Experience Manager] desktop executando o seguinte comando:

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`.

### Limpar cache {#clear-cache-v2}

Execute as seguintes etapas:

1. Start o aplicativo e conecte uma instância AEM.

1. Abra as preferências do aplicativo clicando nas elipses no canto superior direito e selecionando [!UICONTROL Preferences].

1. Localize a entrada que exibe a [!UICONTROL Current Cache Size]. Clique no ícone de lixeira ao lado desse elemento.

Para limpar manualmente o cache, siga as etapas abaixo.

>[!CAUTION]
>
>Esta é uma operação potencialmente destrutiva. Se houver alterações no arquivo local para as quais não foi feito upload, [!DNL Adobe Experience Manager]essas alterações serão perdidas prosseguindo.

O cache é limpo excluindo o diretório de cache do aplicativo, que é encontrado nas preferências do aplicativo.

1. Start do aplicativo.

1. Abra as preferências do aplicativo selecionando as elipses no canto superior direito e selecionando [!UICONTROL Preferences].

1. Observe o [!UICONTROL Cache Directory] valor.

   Neste diretório, há subdiretórios nomeados após os [!DNL Adobe Experience Manager] Endpoints Codificados. Os nomes são uma versão codificada do [!DNL Adobe Experience Manager] URL direcionado. Por exemplo, se o aplicativo estiver direcionando, `localhost:4502` o nome do diretório será `localhost_4502`.

Para limpar o cache, exclua o diretório Endpoint [!DNL Adobe Experience Manager] codificado desejado. Como alternativa, a exclusão do diretório inteiro especificado nas preferências limpará o cache para todas as instâncias que foram usadas pelo aplicativo.

Limpar o cache [!DNL Adobe Experience Manager] do aplicativo desktop é uma tarefa preliminar de solução de problemas que pode resolver vários problemas. Limpe o cache das preferências do aplicativo. Consulte [Definir preferências](install-upgrade.md#set-preferences). O local padrão da pasta de cache é:

### Conheça a versão do aplicativo para [!DNL Adobe Experience Manager] desktop {#know-app-version-v2}

Para ver o número da versão:

1. Start do aplicativo.

1. Clique nas elipses no canto superior direito, passe o mouse sobre [!UICONTROL Help]e clique em [!UICONTROL About].

   O número da versão é listado nesta tela.

### Não é possível ver ativos colocados {#placed-assets-missing}

Se você não conseguir ver os ativos que você ou outros profissionais criativos colocaram nos arquivos de suporte (por exemplo, arquivos INDD), verifique o seguinte:

* Conexão com o servidor. A conectividade de rede flexível pode paralisar os downloads de ativos.

* Tamanho de arquivo. Ativos grandes demoram mais para serem baixados e exibidos.

* Aumente a consistência da letra. Se você ou outro colaborador colocou os ativos ao mapear o DAM AEM para uma letra de unidade diferente, os ativos colocados não serão exibidos.

* Permissões. Para verificar se você tem permissões para buscar os ativos inseridos, entre em contato com o administrador do AEM.

### As edições em arquivos na interface do usuário do aplicativo de desktop não são refletidas [!DNL Adobe Experience Manager] imediatamente em {#changes-on-da-not-visible-on-aem}

[!DNL Adobe Experience Manager] o aplicativo de desktop deixa ao usuário a decisão de quando todas as edições em um arquivo são concluídas. Dependendo do tamanho e da complexidade de um arquivo, leva um tempo significativo para transferir a nova versão de um arquivo de volta para [!DNL Adobe Experience Manager]. O design do aplicativo solicita a minimização do número de vezes que um arquivo é transferido para frente e para trás, em vez de adivinhar quando as edições do arquivo são concluídas e carregadas automaticamente. Recomenda-se que o usuário inicie a transferência do arquivo de volta para [!DNL Adobe Experience Manager] o, escolhendo fazer upload das alterações do arquivo.

### Problemas ao atualizar no macOS {#issues-when-upgrading-on-macos}

Ocasionalmente, podem ocorrer problemas ao atualizar AEM aplicativo desktop no macOS. Isso é causado pela pasta herdada do sistema para AEM aplicativo desktop que impede que novas versões do aplicativo AEM desktop sejam carregadas corretamente. Para resolver esse problema, as pastas e os arquivos a seguir podem ser removidos manualmente.

Antes de executar as etapas a seguir, arraste o `Adobe Experience Manager Desktop` aplicativo da pasta Aplicativos MacOS para a lixeira. Em seguida, abra o terminal, execute o seguinte comando e forneça sua senha quando solicitado.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

### Não é possível carregar arquivos {#upload-fails}

Se você estiver usando um aplicativo de desktop com AEM 6.5.1 ou posterior, atualize o conector S3 ou Azure para a versão 1.10.4 ou posterior. Ele resolve o problema de falha de carregamento de arquivo relacionado ao [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). Consulte as instruções [de instalação](install-upgrade.md#install-v2).

### [!DNL Experience Manager] problemas de conexão do aplicativo de desktop {#connection-issues}

Se você estiver enfrentando problemas gerais de conectividade, veja algumas maneiras de obter mais informações sobre o que o aplicativo para [!DNL Experience Manager] desktop está fazendo.

**Verificar o registro de solicitações**

[!DNL Experience Manager] o aplicativo desktop registra todas as solicitações que envia, juntamente com o código de resposta de cada solicitação, em um arquivo de log dedicado.

1. Abra `request.log` o diretório de log do aplicativo para ver essas solicitações.

1. Cada linha no registro representa uma solicitação ou uma resposta. As solicitações terão um `>` caractere seguido do URL solicitado. As respostas terão um `<` caractere seguido pelo código de resposta e o URL solicitado. As solicitações e a resposta podem ser correspondidas usando o GUID de cada linha.

**Verificar solicitações carregadas pelo navegador incorporado do aplicativo**

A maioria das solicitações do aplicativo é encontrada no registro de solicitações. No entanto, se não houver informações úteis, então pode ser útil investigar as solicitações enviadas pelo navegador incorporado do aplicativo.
Consulte a seção [](#da-connection-issue-with-saml-aem) SAML para obter instruções sobre como visualização essas solicitações.

#### A autenticação de logon SAML não está funcionando {#da-connection-issue-with-saml-aem}

Se o aplicativo de [!DNL Experience Manager] [!DNL Adobe Experience Manager] desktop não se conectar à sua instância habilitada por SSO (SAML), leia esta seção para solucionar problemas. Os processos SSO são variados, às vezes complexos, e o design do aplicativo faz o melhor para acomodar esses tipos de conexões. No entanto, algumas configurações exigem solução de problemas adicional.

Às vezes, o processo SAML não redireciona para o caminho solicitado originalmente, ou o redirecionamento final é para um host diferente do configurado no aplicativo [!DNL Adobe Experience Manager] desktop. Para verificar se não é esse o caso:

1. Abra um navegador da Web.

1. Insira o URL `<AEM host>/content/dam.json` na barra de endereços.

   Substitua `<AEM host>` pela instância do público alvo [!DNL Adobe Experience Manager] , por exemplo `http://localhost:4502/content/dam.json`.

1. Faça logon na [!DNL Adobe Experience Manager] instância.

1. Quando o logon for concluído, verifique o endereço atual do navegador na barra de endereços. Deve corresponder exatamente ao URL que foi digitado inicialmente.

1. Verifique também se tudo antes corresponde `/content/dam.json` ao valor do público alvo [!DNL Adobe Experience Manager] configurado nas configurações do aplicativo [!DNL Adobe Experience Manager] desktop.

**O processo de logon SAML funciona corretamente de acordo com as etapas acima, mas os usuários ainda não conseguem fazer logon**

A janela dentro do aplicativo de [!DNL Adobe Experience Manager] [!DNL Adobe Experience Manager] desktop que exibe o processo de login é simplesmente um navegador da Web que exibe a interface do usuário da Web da instância do público alvo:

* A versão Mac usa um [WebView](https://developer.apple.com/documentation/webkit/webview).

* A versão do Windows usa o [CefSharp](https://cefsharp.github.io/)baseado em Chromo.

Verifique se o processo SAML suporta esses navegadores.

Para solucionar problemas ainda mais, é possível visualização os URLs exatos que o navegador está tentando carregar. Para ver essas informações:

1. Siga as instruções para iniciar o aplicativo no modo [de](#enable-debug-mode)depuração.

1. Reproduza a tentativa de login.

1. Navegue até o diretório [de](#check-log-files-v2) log do aplicativo

1. Para Windows:

   1. Abra &quot;aemcompanionlog.txt&quot;.

   1. Procure mensagens que comecem com &quot;Endereço do navegador de logon alterado para&quot;. Essas entradas também contêm o URL que o aplicativo carregou.

   Para Mac:

   1. `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`, em que **n** é substituído por qualquer número que esteja no nome de arquivo mais recente.

   1. Procure mensagens que comecem com &quot;quadro carregado&quot;. Essas entradas também contêm o URL que o aplicativo carregou.


Analisar a sequência de URL que está sendo carregada pode ajudar a solucionar problemas no fim do SAML para determinar o que está errado.

#### Problema de configuração de SSL {#ssl-config-v2}

As bibliotecas que AEM aplicativo de desktop usa para comunicação HTTP utilizam imposição rigorosa de SSL. Às vezes, uma conexão pode ser bem-sucedida usando um navegador, mas falha ao usar AEM aplicativo de desktop. Para configurar o SSL adequadamente, instale o certificado intermediário ausente no Apache. Consulte [Como instalar um certificado CA intermediário no Apache](https://access.redhat.com/solutions/43575).


As bibliotecas que AEM desktop usa para a comunicação HTTP utilizam imposição rigorosa de SSL. Portanto, pode haver casos em que as conexões SSL que têm sucesso por meio de um navegador falham com o aplicativo [!DNL Adobe Experience Manager] desktop. Isso é bom porque incentiva a configuração correta do SSL e aumenta a segurança, mas pode ser frustrante quando o aplicativo não consegue se conectar.

A abordagem recomendada neste caso é usar uma ferramenta para analisar o certificado SSL de um servidor e identificar problemas para que eles possam ser corrigidos. Há sites que verificam o certificado de um servidor ao fornecer seu URL.

Como medida temporária, é possível desativar a imposição SSL estrita em aplicativos para [!DNL Adobe Experience Manager] desktop. Esta não é uma solução de longo prazo recomendada, pois reduz a segurança ocultando a causa raiz do SSL configurado incorretamente. Para desativar a imposição estrita:

1. Use o editor de sua escolha para editar o arquivo de configuração JavaScript do aplicativo, que é encontrado (por padrão) nos seguintes locais (dependendo do sistema operacional):

   No Mac: `/Applications/Adobe Experience Manager Desktop.app/Contents/Resources/javascript/lib-smb/config.json`

   No Windows: `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop\javascript\config.json`

1. Localize a seguinte seção no arquivo:

   ```shell
   ...
   "assetRepository": {
       "options": {
   ...
   ```

1. Modifique a seção adicionando `"strictSSL": false` o seguinte:

   ```shell
   ...
   "assetRepository": {
       "options": {
           "strictSSL": false,
   ...
   ```

1. Salve o arquivo e reinicie o aplicativo da [!DNL Adobe Experience Manager] área de trabalho.

### O aplicativo não está respondendo {#unresponsive}

Raramente, o aplicativo pode ficar sem resposta, exibir apenas uma tela branca ou exibir um erro na parte inferior da interface, sem nenhuma opção na interface. Tente o seguinte na ordem:

* Clique com o botão direito do mouse na interface do aplicativo e clique em **[!UICONTROL Refresh]**.
* Saia do aplicativo e abra-o novamente.

Em ambos os métodos, os start do aplicativo na pasta DAM raiz.

### Precisa de ajuda adicional com o aplicativo [!DNL Experience Manager] de desktop {#additional-help}

Crie um ticket Jira com as seguintes informações:

* Use `DAM - Companion App` como o [!UICONTROL Component].

* Etapas detalhadas para reproduzir o problema em [!UICONTROL Description].

* Registros de nível DEBUG capturados durante a reprodução do problema.

* Versão AEM público alvo.

* Versão do sistema operacional.

* [!DNL Adobe Experience Manager] versão do aplicativo para desktop. Para saber a versão do aplicativo, consulte [encontrar a versão](#know-app-version-v2)do aplicativo para desktop.

>[!MORELIKETHIS]
>
>* [Problemas conhecidos](release-notes.md#known-issues-v2)
>* [Evitar conflitos de edição](using.md#adv-workflow-collaborate-avoid-conflicts)

