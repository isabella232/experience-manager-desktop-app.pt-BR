---
title: Práticas recomendadas para e solução de problemas [!DNL Adobe Experience Manager] aplicativo de desktop
description: Siga as práticas recomendadas e solucione problemas para resolver problemas ocasionais relacionados à instalação, atualização, configuração, etc.
exl-id: f388e4ac-907d-4093-ba6f-86ecdafeb015
source-git-commit: 2c846fb9cd82691f6439e93429dffcca8127ba68
workflow-type: tm+mt
source-wordcount: '2260'
ht-degree: 0%

---

# Solução de problemas [!DNL Adobe Experience Manager] aplicativo de desktop {#troubleshoot-v2}

[!DNL Adobe Experience Manager] o aplicativo de desktop se conecta a um [!DNL Experience Manager] Digital Asset Management (DAM) da implantação. O aplicativo busca informações do repositório e resultados de pesquisa em seu computador, baixa e carrega arquivos e pastas, além de recursos para gerenciar conflitos com a interface do Assets.

Leia para solucionar problemas do aplicativo, conhecer as práticas recomendadas e descobrir as limitações.

## Práticas recomendadas {#best-practices-to-prevent-troubles}

Siga as práticas recomendadas a seguir para evitar alguns problemas comuns e solução de problemas.

* **Entender como o aplicativo de desktop funciona**: Antes de começar a usar o aplicativo, passe algum tempo sabendo como ele funciona. Saber mais sobre a vinculação entre [!DNL Experience Manager] interface da web e desktop, mapeamento de repositório, armazenamento em cache de ativos, salvamento local e upload em segundo plano. Consulte [como funciona](release-notes.md#how-app-works).

* **Evite caracteres não aceitos em nomes de pastas**: não use espaços em branco e caracteres inválidos ao criar ou carregar pastas. Veja uma lista de caracteres em [Criar pastas em [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders). Alguns [!DNL Experience Manager] os casos de uso podem ser afetados por caracteres não compatíveis no nome da pasta.

* **Práticas recomendadas para evitar conflitos**: para evitar possíveis conflitos ao colaborar em vários ativos, consulte [evitar conflitos de edição](using.md#adv-workflow-collaborate-avoid-conflicts).

* **Usar o upload de pastas para pastas grandes e hierárquicas**: em vez de usar a interface da Web do Assets ou outros métodos, use [!DNL Experience Manager] aplicativo de desktop para carregar pastas grandes. O aplicativo carrega os ativos em segundo plano com registro e monitoramento. Consulte [fazer upload de ativos em massa](using.md#bulk-upload-assets).

* **Usar a versão mais recente**: use a versão mais recente do aplicativo e sempre verifique a compatibilidade antes de instalar uma nova versão do aplicativo ou antes de atualizar para uma versão mais recente [!DNL Experience Manager] versão. Consulte [notas de versão](release-notes.md).

* **Usar a mesma letra de unidade**: use a mesma letra de unidade em uma organização para mapear para a variável [!DNL Experience Manager] DAM. Para ver os ativos colocados por outros usuários, os caminhos devem ser os mesmos. Usar a mesma letra de unidade garante um caminho constante para os ativos do DAM. Os ativos permanecem inseridos e não são removidos mesmo se letras de unidade diferentes forem usadas por usuários diferentes.

* **Cuidado com a rede**: o desempenho da rede é essencial para [!DNL Experience Manager] desempenho do aplicativo de desktop. Se você enfrentar respostas lentas para transferências de arquivos ou operações em massa, desative os recursos ou aplicativos que podem causar muito tráfego de rede.

* **Casos de uso não aceitos para o aplicativo de desktop**: não use o aplicativo para a migração do Assets (ele precisa de planejamento e outras ferramentas); para operações DAM pesadas (como mover pastas grandes, uploads grandes, encontrar arquivos usando pesquisas avançadas de metadados); e como um cliente de sincronização (os princípios de design e padrões de uso são diferentes dos clientes em sincronia, como o Microsoft OneDrive ou a sincronização de desktop do Adobe Creative Cloud).

* **Tempo limite**: Atualmente, o aplicativo de desktop não tem um valor de tempo limite configurável que desconecta a conexão entre [!DNL Experience Manager] aplicativo de servidor e desktop após um intervalo de tempo fixo. Ao fazer upload de ativos grandes, se a conexão atingir o tempo limite após um tempo, o aplicativo tentará fazer upload do ativo algumas vezes, aumentando o tempo limite do upload. Não há uma maneira recomendada de alterar as configurações padrão de tempo limite.

## Como solucionar problemas {#troubleshooting-prep}

Para solucionar problemas do aplicativo de desktop, esteja ciente das seguintes informações. Além disso, ele o prepara para melhor encaminhar os problemas ao Suporte ao cliente do Adobe se você optar por buscar suporte.

### Local dos arquivos de log {#check-log-files-v2}

[!DNL Experience Manager] o aplicativo de desktop armazena seus arquivos de log nos seguintes locais, dependendo do sistema operacional:

No Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

No Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

Ao fazer upload de muitos ativos, se houver falha no upload de alguns arquivos, consulte `backend.log` para identificar os uploads com falha.

>[!NOTE]
>
>Ao trabalhar com o Suporte ao cliente do Adobe em uma solicitação de suporte ou tíquete, você pode ser solicitado a compartilhar os arquivos de log para ajudar a equipe de Suporte ao cliente a entender o problema. Arquivar todo o `Logs` e compartilhe-a com seu contato de Suporte ao cliente.

### Alterar nível de detalhes nos arquivos de log {#level-of-details-in-log}

Para alterar o nível de detalhes nos arquivos de log:

1. Certifique-se de que o aplicativo não esteja em execução.

1. No sistema Windows:

   1. Abra uma janela de comando.

   1. Launch [!DNL Adobe Experience Manager] aplicativo de desktop executando o comando:

   ```shell
   set AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe
   ```

   No sistema Mac:

   1. Abra uma janela de terminal.

   1. Launch [!DNL Adobe Experience Manager] aplicativo de desktop executando o comando:

   ```shell
   AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app
   ```

Os níveis de log válidos são DEBUG, INFO, WARN ou ERROR. O detalhamento dos logs é mais alto em DEBUG e mais baixo em ERROR.

### Ativar modo de depuração {#enable-debug-mode}

Para solucionar problemas, você pode ativar o modo de depuração e obter mais informações nos logs.

>[!NOTE]
>
>Os níveis de log válidos são DEBUG, INFO, WARN ou ERROR. O detalhamento dos logs é mais alto em DEBUG e mais baixo em ERROR.

Para usar o aplicativo no modo de depuração no Mac:

1. Abra uma janela de terminal ou um prompt de comando.

1. Inicie o [!DNL Experience Manager] aplicativo de desktop do executando o seguinte comando:

   `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`.

Para ativar o modo de depuração no Windows:

1. Abra uma janela de comando.

1. Launch [!DNL Experience Manager] aplicativo de desktop do executando o seguinte comando:

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`.

### Conhecer o [!DNL Adobe Experience Manager] versão do aplicativo de desktop {#know-app-version-v2}

Para ver o número da versão:

1. Inicie o aplicativo.

1. Clique nas reticências no canto superior direito e passe o mouse sobre [!UICONTROL Help]e, em seguida, clique em [!UICONTROL About].

   O número da versão está listado nesta tela.

### Limpar cache {#clear-cache-v2}

Execute as seguintes etapas:

1. Inicie o aplicativo e conecte-se à [!DNL Experience Manager] instância.

1. Abra as preferências do aplicativo clicando nas reticências no canto superior direito e selecionando [!UICONTROL Preferences].

1. Localize a entrada que exibe o [!UICONTROL Current Cache Size]. Clique no ícone de lixeira ao lado desse elemento.

Para limpar manualmente o cache, continue com as etapas abaixo.

>[!CAUTION]
>
>Esta é uma operação potencialmente destrutiva. Se houver alterações em arquivos locais que não foram carregadas no [!DNL Adobe Experience Manager], essas alterações serão perdidas ao continuar.

O cache é limpo excluindo o diretório de cache do aplicativo, que se encontra nas preferências do aplicativo.

1. Inicie o aplicativo.

1. Abra as preferências do aplicativo selecionando as reticências no canto superior direito e [!UICONTROL Preferences].

1. Observe que [!UICONTROL Cache Directory] valor.

   Nesse diretório há subdiretórios nomeados de acordo com a variável [!DNL Adobe Experience Manager] Endpoints. Os nomes são uma versão codificada do arquivo de destino [!DNL Adobe Experience Manager] URL. Por exemplo, se o aplicativo for direcionado `localhost:4502` então, o nome do diretório será `localhost_4502`.

Para limpar o cache, exclua o código [!DNL Adobe Experience Manager] Diretório do ponto de extremidade. Como alternativa, excluir todo o diretório especificado nas preferências limpará o cache de todas as instâncias que foram usadas pelo aplicativo.

Limpando [!DNL Adobe Experience Manager] o cache do aplicativo de desktop é uma tarefa preliminar de solução de problemas que pode resolver vários problemas. Limpe o cache nas preferências do aplicativo. Consulte [definir preferências](install-upgrade.md#set-preferences). O local padrão da pasta de cache é:

## Não é possível ver os ativos colocados {#placed-assets-missing}

Se você não conseguir ver os ativos que você ou outros profissionais de criação colocaram nos arquivos de suporte (ou seja, arquivos INDD), verifique o seguinte:

* Conexão com o servidor. A conectividade instável da rede pode paralisar os downloads de ativos.

* Tamanho do arquivo. Os ativos grandes demoram mais para serem baixados e exibidos.

* Consistência da letra de unidade. Se você ou outro colaborador tiver colocado os ativos ao mapear o [!DNL Experience Manager] do DAM para uma letra de unidade diferente, os ativos inseridos não serão exibidos.

* Permissões. Para verificar se você tem permissões para buscar os ativos colocados, entre em contato com o [!DNL Experience Manager] administrador.

### Edições em arquivos na interface do usuário do aplicativo de desktop não refletem no [!DNL Adobe Experience Manager] imediatamente {#changes-on-da-not-visible-on-aem}

[!DNL Adobe Experience Manager] O aplicativo de desktop deixa ao usuário a decisão de quando todas as edições em um arquivo são concluídas. Dependendo do tamanho e da complexidade de um arquivo, leva um tempo significativo para transferir a nova versão de um arquivo de volta para o [!DNL Adobe Experience Manager]. O design do aplicativo requer a redução do número de vezes que um arquivo é transferido de um lado para o outro, em vez de adivinhar quando as edições do arquivo são concluídas e carregadas automaticamente. Recomenda-se que o usuário inicie a transferência do arquivo de volta para [!DNL Adobe Experience Manager] escolhendo fazer upload das alterações de um arquivo.

### Problemas ao atualizar no macOS {#issues-when-upgrading-on-macos}

Ocasionalmente, podem ocorrer problemas durante a atualização [!DNL Experience Manager] aplicativo de desktop no macOS. Isso é causado pela pasta herdada do sistema para [!DNL Experience Manager] aplicativo de desktop que impede novas versões do [!DNL Experience Manager] aplicativo de desktop a ser carregado corretamente. Para solucionar esse problema, as seguintes pastas e arquivos podem ser removidos manualmente.

Antes de executar as etapas a seguir, arraste o `Adobe Experience Manager Desktop` aplicativo da pasta Aplicativos macOS para a Lixeira. Em seguida, abra o terminal, execute o comando a seguir e forneça sua senha quando solicitado.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## Não é possível carregar arquivos {#upload-fails}

Se você estiver usando o aplicativo de desktop com [!DNL Experience Manager] 6.5.1 ou posterior, atualize o conector S3 ou Azure para a versão 1.10.4 ou posterior. Ele resolve o problema de falha de upload de arquivo relacionado ao [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). Consulte [instruções de instalação](install-upgrade.md#install-v2).

## [!DNL Experience Manager] problemas de conexão do aplicativo de desktop {#connection-issues}

Se tiver problemas gerais de conectividade, veja a seguir algumas maneiras de obter mais informações sobre o que [!DNL Experience Manager] o aplicativo de desktop está funcionando.

**Verificar o log da solicitação**

[!DNL Experience Manager] o aplicativo de desktop registra todas as solicitações enviadas, juntamente com o código de resposta de cada solicitação, em um arquivo de log dedicado.

1. Abertura `request.log` no diretório de log do aplicativo para ver essas solicitações.

1. Cada linha no log representa uma solicitação ou uma resposta. As solicitações terão um `>` caractere seguido pelo URL que foi solicitado. As respostas terão um `<` caractere seguido pelo código de resposta e pelo URL solicitado. As solicitações e as respostas podem ser correspondidas usando o GUID de cada linha.

**Verificar solicitações carregadas pelo navegador incorporado do aplicativo**

A maioria das solicitações do aplicativo é encontrada no log de solicitações. No entanto, se não houver informações úteis, pode ser útil examinar as solicitações enviadas pelo navegador incorporado do aplicativo.
Consulte a [Seção SAML](#da-connection-issue-with-saml-aem) para obter instruções sobre como visualizar essas solicitações.

### A autenticação de login do SAML não está funcionando {#da-connection-issue-with-saml-aem}

[!DNL Experience Manager] O aplicativo de desktop pode não se conectar ao SSO habilitado (SAML) [!DNL Adobe Experience Manager] implantação. O design do aplicativo tenta acomodar as variações e complexidades das conexões e dos processos de SSO. No entanto, uma configuração pode exigir solução de problemas adicional.

Às vezes, o processo SAML não redireciona de volta para o caminho solicitado originalmente ou o redirecionamento final é para um host diferente do configurado no [!DNL Adobe Experience Manager] aplicativo de desktop. Para verificar se esse não é o caso:

1. Abra um navegador da Web. Access `https://[aem_server]:[port]/content/dam.json` URL.

1. Faça logon no [!DNL Adobe Experience Manager] implantação.

1. Quando o logon for concluído, verifique o endereço atual do navegador na barra de endereços. Ele deve corresponder exatamente ao URL inserido inicialmente.

1. Verifique também se tudo o que antes `/content/dam.json` corresponde ao público alvo [!DNL Adobe Experience Manager] valor configurado em [!DNL Adobe Experience Manager] configurações do aplicativo de desktop.

**O processo de logon SAML funciona corretamente de acordo com as etapas acima, mas os usuários ainda não conseguem fazer logon**

A janela dentro de [!DNL Adobe Experience Manager] aplicativo de desktop que exibe o processo de logon é simplesmente um navegador da web que está exibindo o destino [!DNL Adobe Experience Manager] interface da Web da instância do:

* A versão do Mac usa um [WebView](https://developer.apple.com/documentation/webkit/webview).

* A versão para Windows usa o Chromium [CefSharp](https://cefsharp.github.io/).

Verifique se o processo SAML é compatível com esses navegadores.

Para solucionar mais problemas, é possível visualizar as URLs exatas que o navegador está tentando carregar. Para ver essas informações:

1. Siga as instruções para iniciar o aplicativo em [modo de depuração](#enable-debug-mode).

1. Reproduza a tentativa de logon.

1. Navegue até [diretório de log](#check-log-files-v2) do aplicativo

1. Para Windows:

   1. Abra &quot;aemcompanionlog.txt&quot;.

   1. Procure mensagens que comecem com &quot;Endereço do navegador de logon alterado para&quot;. Essas entradas também contêm o URL que o aplicativo carregou.

   Para o Mac:

   1. `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`, em que o **n** são substituídos pelos números que estiverem no nome de arquivo mais recente.

   1. Procure mensagens que comecem com &quot;quadro carregado&quot;. Essas entradas também contêm o URL que o aplicativo carregou.


Observar a sequência de URL que está sendo carregada pode ajudar a solucionar problemas na extremidade do SAML para determinar o que está errado.

### Problema de configuração do SSL {#ssl-config-v2}

As bibliotecas que [!DNL Experience Manager] O aplicativo de desktop usa para comunicação HTTP e utiliza imposição SSL estrita. Às vezes, uma conexão pode ser bem-sucedida usando um navegador, mas falha usando [!DNL Experience Manager] aplicativo de desktop. Para configurar o SSL adequadamente, instale o certificado intermediário ausente no Apache. Consulte [Como instalar um certificado CA intermediário no Apache](https://access.redhat.com/solutions/43575).

As bibliotecas que [!DNL Experience Manager] O aplicativo de desktop do usa para comunicação HTTP e utiliza imposição rigorosa de SSL. Portanto, pode haver instâncias em que as conexões SSL bem-sucedidas por meio de um navegador falhem com [!DNL Adobe Experience Manager] aplicativo de desktop. Isso é bom porque incentiva a configuração correta do SSL e aumenta a segurança, mas pode ser frustrante quando o aplicativo não consegue se conectar.

A abordagem recomendada neste caso é usar uma ferramenta para analisar o certificado SSL de um servidor e identificar problemas para que eles possam ser corrigidos. Há sites que inspecionam o certificado de um servidor ao fornecer seu URL.

Como medida temporária, é possível desativar a imposição estrita de SSL em [!DNL Adobe Experience Manager] aplicativo de desktop. Essa não é uma solução de longo prazo recomendada, pois reduz a segurança ao ocultar a causa raiz do SSL configurado incorretamente. Para desativar a imposição estrita:

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

1. Modifique a seção adicionando `"strictSSL": false` do seguinte modo:

   ```shell
   ...
   "assetRepository": {
       "options": {
           "strictSSL": false,
   ...
   ```

1. Salve o arquivo e reinicie [!DNL Adobe Experience Manager] aplicativo de desktop.

### Problemas de logon ao alternar para um servidor diferente {#cannot-login-cookies-issue}

Depois de usar um [!DNL Experience Manager] servidor, ao tentar alterar a conexão para um servidor diferente, você pode encontrar problemas de logon. Isso se deve à interferência de cookies antigos na nova autenticação. Uma opção no menu principal para [!UICONTROL Clear Cookies] ajuda. Faça logoff da sessão atual no aplicativo e selecione [!UICONTROL Clear Cookies] antes de continuar a conexão.

![Limpar cookies ao alternar entre servidores](assets/main_menu_logout_da2.png)

## O aplicativo não está respondendo {#unresponsive}

Raramente, o aplicativo pode ficar sem resposta, exibir apenas uma tela branca ou exibir um erro na parte inferior da interface sem nenhuma opção na interface. Tente o seguinte na ordem:

* Clique com o botão direito na interface do aplicativo e clique em **[!UICONTROL Refresh]**.
* Saia do aplicativo e abra-o novamente.

Em ambos os métodos, o aplicativo é iniciado na pasta raiz do DAM.

## Ocultar ativos expirados {#hide-expired-assets}

Ao navegar pelos ativos no [!DNL Experience Manager] os ativos expirados não são exibidos. Para impedir a visualização, pesquisa e busca de ativos expirados ao navegar pelos ativos do aplicativo de desktop e do Asset Link, os administradores podem fazer a seguinte configuração. A configuração funciona para todos os usuários, independentemente do privilégio de administrador.

* [Configuração no Experience Manager 6.5 para ocultar ativos expirados](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#hide-expired-assets-via-acp-api).
* [Configuração no Experience Manager as a Cloud Service para ocultar ativos expirados](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/manage-digital-assets.html#hide-expired-assets-via-acp-api).

<!--
### Need additional help with [!DNL Experience Manager] desktop app {#additional-help}

Create Jira ticket with the following information:

* Use `DAM - Companion App` as the [!UICONTROL Component].

* Detailed steps to reproduce the issue in [!UICONTROL Description].

* DEBUG level logs that were captured while reproducing the issue.

* Target Experience Manager version.

* Operating system version.

* [!DNL Adobe Experience Manager] desktop app version. To know your app version, see [finding the desktop app version](#know-app-version-v2).
-->

>[!MORELIKETHIS]
>
>* [Problemas conhecidos](release-notes.md#known-issues-v2)
>* [Evitar conflitos de edição](using.md#adv-workflow-collaborate-avoid-conflicts)

