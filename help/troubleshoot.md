---
title: Práticas recomendadas para o aplicativo desktop e solução de problemas [!DNL Adobe Experience Manager] app
description: Siga as práticas recomendadas e solucione problemas para resolver problemas ocasionais relacionados à instalação, atualização, configuração e assim por diante.
translation-type: tm+mt
source-git-commit: a25c1fa13895ae9eb7268e3e01c83a5f0b9d7d1d
workflow-type: tm+mt
source-wordcount: '2120'
ht-degree: 0%

---


# Solucionar problemas do [!DNL Adobe Experience Manager] aplicativo de desktop {#troubleshoot-v2}

[!DNL Adobe Experience Manager] o aplicativo desktop se conecta ao repositório DAM (Digital Asset Management, Gerenciamento de ativos digitais) de uma  [!DNL Experience Manager] implantação. O aplicativo obtém informações do repositório e resultados da pesquisa em seu computador, baixa e carrega arquivos e pastas e inclui recursos para gerenciar conflitos com a interface do usuário do Assets.

Leia para solucionar problemas do aplicativo, aprender as práticas recomendadas e descobrir as limitações.

## Práticas recomendadas {#best-practices-to-prevent-troubles}

Siga as práticas recomendadas a seguir para evitar alguns problemas comuns e a solução de problemas.

* **Entenda como o aplicativo de desktop funciona**: Antes de começar a usar o aplicativo, passe alguns momentos sabendo como ele funciona. Saiba mais sobre a vinculação entre [!DNL Experience Manager] interface da Web e área de trabalho, mapeamento do repositório, armazenamento em cache de ativos, salvamento local e upload em segundo plano. Consulte [como funciona](release-notes.md#how-app-works).

* **Evite caracteres não suportados em nomes** de pastas: Não use espaços em branco e caracteres inválidos ao criar ou carregar pastas. Consulte uma lista de caracteres em [Criar pastas em [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders). Alguns casos de uso de [!DNL Experience Manager] podem ser afetados por caracteres não suportados no nome da pasta.

* **Práticas recomendadas para evitar conflitos**: Para evitar conflitos em potencial ao colaborar em vários ativos, consulte  [evitar conflitos](using.md#adv-workflow-collaborate-avoid-conflicts) de edição.

* **Use o upload de pasta para pastas** grandes e hierárquicas: Em vez de usar a interface da Web do Assets ou outros métodos, use o aplicativo de  [!DNL Experience Manager] desktop para fazer upload de pastas grandes. O aplicativo carrega os ativos em segundo plano com o registro e o monitoramento. Consulte [ativos de upload em massa](using.md#bulk-upload-assets).

* **Use a versão** mais recente: Use a versão mais recente do aplicativo e sempre verifique a compatibilidade antes de instalar uma nova versão do aplicativo ou antes de atualizar para uma  [!DNL Experience Manager] versão mais recente. Consulte [notas de versão](release-notes.md).

* **Use a mesma letra** de unidade: Use a mesma letra de unidade em uma organização para mapear para o  [!DNL Experience Manager] DAM. Para ver os ativos colocados por outros usuários, os caminhos devem ser os mesmos. Usar a mesma letra de unidade garante um caminho constante para ativos DAM. Os ativos permanecem posicionados e não são removidos mesmo se letras de unidade diferentes forem usadas por usuários diferentes.

* **Lembre-se da rede**: O desempenho da rede é essencial para o desempenho do aplicativo  [!DNL Experience Manager] desktop. Se você enfrentar uma resposta lenta a transferências de arquivos ou operações em massa, desative os recursos ou aplicativos que podem causar muito tráfego de rede.

* **Casos de uso não suportados para aplicativos** de desktop: Não use o aplicativo para a migração do Assets (ele precisa de planejamento e outras ferramentas); para operações DAM de uso intenso (como mover pastas grandes, uploads grandes, localizar arquivos usando pesquisas avançadas de metadados); e como um cliente de sincronização (os princípios de design e os padrões de uso são diferentes dos clientes em sincronia, como o Microsoft OneDrive ou o Adobe Creative Cloud Desktop Sync).

* **Tempo limite**: Atualmente, o aplicativo de desktop não tem um valor de tempo limite configurável que desconecta a conexão entre o  [!DNL Experience Manager] servidor e o aplicativo de desktop após um intervalo de tempo fixo. Ao fazer upload de ativos grandes, se a conexão expirar depois de algum tempo, o aplicativo tentativas fazer upload do ativo algumas vezes aumentando o tempo limite de upload. Não há uma maneira recomendada de alterar as configurações de tempo limite padrão.

## Como solucionar problemas {#troubleshooting-prep}

Para solucionar problemas com o aplicativo de desktop, tenha em mente as seguintes informações. Além disso, ele o prepara para transmitir melhor os problemas ao Atendimento ao cliente da Adobe se você optar por buscar suporte.

### Localização dos arquivos de registro {#check-log-files-v2}

[!DNL Experience Manager] o aplicativo desktop armazena seus arquivos de registro nos seguintes locais, dependendo do sistema operacional:

No Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

No Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

Ao fazer upload de muitos ativos, se alguns arquivos não forem carregados, consulte `backend.log` o arquivo para identificar os uploads com falha.

>[!NOTE]
>
>Ao trabalhar com o Atendimento ao cliente do Adobe em uma solicitação de suporte ou ticket, você pode ser solicitado a compartilhar os arquivos de registro para ajudar a equipe do Atendimento ao cliente a entender o problema. Arquive a pasta `Logs` inteira e compartilhe-a com seu contato com o Atendimento ao cliente.

### Alterar o nível de detalhes nos arquivos de log {#level-of-details-in-log}

Para alterar o nível de detalhes nos arquivos de registro:

1. Verifique se o aplicativo não está em execução.

1. No sistema Windows:

   1. Abra uma janela de comando.

   1. Inicie o [!DNL Adobe Experience Manager] aplicativo desktop executando o comando:

   ```shell
   set AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe
   ```

   No sistema Mac:

   1. Abra uma janela de terminal.

   1. Inicie o [!DNL Adobe Experience Manager] aplicativo desktop executando o comando:

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

1. Inicie o [!DNL Experience Manager] aplicativo desktop executando o seguinte comando:

   `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`.

Para ativar o modo de depuração no Windows:

1. Abra uma janela de comando.

1. Inicie o [!DNL Experience Manager] aplicativo desktop executando o seguinte comando:

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`.

### Limpar cache {#clear-cache-v2}

Execute as seguintes etapas:

1. Start o aplicativo e conecte uma instância [!DNL Experience Manager].

1. Abra as preferências do aplicativo clicando nas elipses no canto superior direito e selecionando [!UICONTROL Preferences].

1. Localize a entrada que exibe [!UICONTROL Current Cache Size]. Clique no ícone de lixeira ao lado desse elemento.

Para limpar manualmente o cache, siga as etapas abaixo.

>[!CAUTION]
>
>Esta é uma operação potencialmente destrutiva. Se houver alterações no arquivo local que não forem carregadas em [!DNL Adobe Experience Manager], essas alterações serão perdidas ao prosseguir.

O cache é limpo excluindo o diretório de cache do aplicativo, que é encontrado nas preferências do aplicativo.

1. Start do aplicativo.

1. Abra as preferências do aplicativo selecionando as elipses no canto superior direito e selecionando [!UICONTROL Preferences].

1. Observe o valor [!UICONTROL Cache Directory].

   Neste diretório, há subdiretórios nomeados após os Pontos finais [!DNL Adobe Experience Manager] codificados. Os nomes são uma versão codificada do URL [!DNL Adobe Experience Manager] direcionado. Por exemplo, se o aplicativo estiver direcionando `localhost:4502`, o nome do diretório será `localhost_4502`.

Para limpar o cache, exclua o diretório Encoded [!DNL Adobe Experience Manager] Endpoint desejado. Como alternativa, a exclusão do diretório inteiro especificado nas preferências limpará o cache para todas as instâncias que foram usadas pelo aplicativo.

Limpar o cache do [!DNL Adobe Experience Manager] aplicativo desktop é uma tarefa preliminar de solução de problemas que pode resolver vários problemas. Limpe o cache das preferências do aplicativo. Consulte [definir preferências](install-upgrade.md#set-preferences). O local padrão da pasta de cache é:

### Conheça a versão [!DNL Adobe Experience Manager] do aplicativo de desktop {#know-app-version-v2}

Para ver o número da versão:

1. Start do aplicativo.

1. Clique nas elipses no canto superior direito, passe o mouse sobre [!UICONTROL Help] e clique em [!UICONTROL About].

   O número da versão é listado nesta tela.

### Não é possível ver ativos colocados {#placed-assets-missing}

Se você não conseguir ver os ativos que você ou outros profissionais criativos colocaram nos arquivos de suporte (por exemplo, arquivos INDD), verifique o seguinte:

* Conexão com o servidor. A conectividade de rede flexível pode paralisar os downloads de ativos.

* Tamanho de arquivo. Ativos grandes demoram mais para serem baixados e exibidos.

* Aumente a consistência da letra. Se você ou outro colaborador tiver colocado os ativos ao mapear o [!DNL Experience Manager] DAM para uma letra de unidade diferente, os ativos colocados não serão exibidos.

* Permissões. Para verificar se você tem permissões para buscar os ativos inseridos, entre em contato com o administrador do [!DNL Experience Manager].

### As edições em arquivos na interface de usuário do aplicativo de desktop não refletem em [!DNL Adobe Experience Manager] imediatamente {#changes-on-da-not-visible-on-aem}

[!DNL Adobe Experience Manager] o aplicativo de desktop deixa ao usuário a decisão de quando todas as edições em um arquivo são concluídas. Dependendo do tamanho e da complexidade de um arquivo, leva um tempo significativo para transferir a nova versão de um arquivo de volta para [!DNL Adobe Experience Manager]. O design do aplicativo solicita a minimização do número de vezes que um arquivo é transferido para frente e para trás, em vez de adivinhar quando as edições do arquivo são concluídas e carregadas automaticamente. Recomenda-se que o usuário inicie a transferência do arquivo de volta para [!DNL Adobe Experience Manager] escolhendo carregar as alterações de um arquivo.

### Problemas ao atualizar no macOS {#issues-when-upgrading-on-macos}

Ocasionalmente, podem ocorrer problemas ao atualizar [!DNL Experience Manager] o aplicativo desktop no macOS. Isso é causado pela pasta herdada do sistema para [!DNL Experience Manager] aplicativo desktop que impede que novas versões do [!DNL Experience Manager] aplicativo desktop sejam carregadas corretamente. Para resolver esse problema, as pastas e os arquivos a seguir podem ser removidos manualmente.

Antes de executar as etapas a seguir, arraste o aplicativo `Adobe Experience Manager Desktop` da pasta Aplicativos macOS para a Lixeira. Em seguida, abra o terminal, execute o seguinte comando e forneça sua senha quando solicitado.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

### Não é possível carregar arquivos {#upload-fails}

Se você estiver usando um aplicativo de desktop com [!DNL Experience Manager] 6.5.1 ou posterior, atualize o conector S3 ou Azure para a versão 1.10.4 ou posterior. Ele resolve o problema de falha de carregamento de arquivo relacionado a [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). Consulte [instruções de instalação](install-upgrade.md#install-v2).

### [!DNL Experience Manager] problemas de conexão do aplicativo de desktop  {#connection-issues}

Se você estiver enfrentando problemas gerais de conectividade, veja algumas maneiras de obter mais informações sobre o que [!DNL Experience Manager] o aplicativo de desktop está fazendo.

**Verificar o registro de solicitações**

[!DNL Experience Manager] o aplicativo desktop registra todas as solicitações que envia, juntamente com o código de resposta de cada solicitação, em um arquivo de log dedicado.

1. Abra `request.log` no diretório de log do aplicativo para ver essas solicitações.

1. Cada linha no registro representa uma solicitação ou uma resposta. As solicitações terão um caractere `>` seguido do URL solicitado. As respostas terão um caractere `<` seguido pelo código de resposta e pelo URL solicitado. As solicitações e a resposta podem ser correspondidas usando o GUID de cada linha.

**Verificar solicitações carregadas pelo navegador incorporado do aplicativo**

A maioria das solicitações do aplicativo é encontrada no registro de solicitações. No entanto, se não houver informações úteis, então pode ser útil investigar as solicitações enviadas pelo navegador incorporado do aplicativo.
Consulte a seção [SAML](#da-connection-issue-with-saml-aem) para obter instruções sobre como visualização essas solicitações.

#### A autenticação de logon SAML não está funcionando {#da-connection-issue-with-saml-aem}

Se [!DNL Experience Manager] o aplicativo desktop não se conectar à sua instância ativada por SSO (SAML) [!DNL Adobe Experience Manager], leia esta seção para solucionar problemas. Os processos SSO são variados, às vezes complexos, e o design do aplicativo faz o melhor para acomodar esses tipos de conexões. No entanto, algumas configurações exigem solução de problemas adicional.

Às vezes, o processo SAML não redireciona para o caminho originalmente solicitado, ou o redirecionamento final é para um host diferente do configurado no [!DNL Adobe Experience Manager] aplicativo desktop. Para verificar se não é esse o caso:

1. Abra um navegador da Web. Acesse o URL `https://[aem_server]:[port]/content/dam.json`.

1. Faça logon na implantação [!DNL Adobe Experience Manager].

1. Quando o logon for concluído, verifique o endereço atual do navegador na barra de endereços. Deve corresponder exatamente ao URL que foi digitado inicialmente.

1. Verifique também se tudo antes de `/content/dam.json` corresponde ao valor [!DNL Adobe Experience Manager] do público alvo configurado nas configurações do [!DNL Adobe Experience Manager] aplicativo para desktop.

**O processo de logon SAML funciona corretamente de acordo com as etapas acima, mas os usuários ainda não conseguem fazer logon**

A janela no aplicativo de área de trabalho [!DNL Adobe Experience Manager] que exibe o processo de logon é simplesmente um navegador da Web que exibe a interface do usuário da Web da instância do público alvo [!DNL Adobe Experience Manager]:

* A versão Mac usa um [WebView](https://developer.apple.com/documentation/webkit/webview).

* A versão do Windows usa [CefSharp](https://cefsharp.github.io/) baseado em Chromo.

Verifique se o processo SAML suporta esses navegadores.

Para solucionar problemas ainda mais, é possível visualização os URLs exatos que o navegador está tentando carregar. Para ver essas informações:

1. Siga as instruções para iniciar o aplicativo no [modo de depuração](#enable-debug-mode).

1. Reproduza a tentativa de login.

1. Navegue até [diretório de log](#check-log-files-v2) do aplicativo

1. Para Windows:

   1. Abra &quot;aemcompanionlog.txt&quot;.

   1. Procure mensagens que comecem com &quot;Endereço do navegador de logon alterado para&quot;. Essas entradas também contêm o URL que o aplicativo carregou.

   Para Mac:

   1. `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`, onde o  **** nome é substituído pelos números que estiverem no nome de arquivo mais recente.

   1. Procure mensagens que comecem com &quot;quadro carregado&quot;. Essas entradas também contêm o URL que o aplicativo carregou.


Analisar a sequência de URL que está sendo carregada pode ajudar a solucionar problemas no fim do SAML para determinar o que está errado.

#### Problema de configuração SSL {#ssl-config-v2}

As bibliotecas que o [!DNL Experience Manager] aplicativo desktop usa para comunicação HTTP utilizam imposição rigorosa de SSL. Às vezes, uma conexão pode ser bem-sucedida usando um navegador, mas falha ao usar [!DNL Experience Manager] aplicativo desktop. Para configurar o SSL adequadamente, instale o certificado intermediário ausente no Apache. Consulte [Como instalar um certificado CA intermediário no Apache](https://access.redhat.com/solutions/43575).

As bibliotecas que o [!DNL Experience Manager] aplicativo desktop usa para comunicação HTTP utilizam imposição rigorosa de SSL. Portanto, pode haver casos em que as conexões SSL com êxito por meio de um navegador falham com o [!DNL Adobe Experience Manager] aplicativo de desktop. Isso é bom porque incentiva a configuração correta do SSL e aumenta a segurança, mas pode ser frustrante quando o aplicativo não consegue se conectar.

A abordagem recomendada neste caso é usar uma ferramenta para analisar o certificado SSL de um servidor e identificar problemas para que eles possam ser corrigidos. Há sites que verificam o certificado de um servidor ao fornecer seu URL.

Como medida temporária, é possível desativar a imposição SSL estrita no [!DNL Adobe Experience Manager] aplicativo de desktop. Esta não é uma solução de longo prazo recomendada, pois reduz a segurança ocultando a causa raiz do SSL configurado incorretamente. Para desativar a imposição estrita:

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

1. Modifique a seção adicionando `"strictSSL": false` da seguinte forma:

   ```shell
   ...
   "assetRepository": {
       "options": {
           "strictSSL": false,
   ...
   ```

1. Salve o arquivo e reinicie o [!DNL Adobe Experience Manager] aplicativo de desktop.

### O aplicativo não responde {#unresponsive}

Raramente, o aplicativo pode ficar sem resposta, exibir apenas uma tela branca ou exibir um erro na parte inferior da interface, sem nenhuma opção na interface. Tente o seguinte na ordem:

* Clique com o botão direito do mouse na interface do aplicativo e clique em **[!UICONTROL Refresh]**.
* Saia do aplicativo e abra-o novamente.

Em ambos os métodos, os start do aplicativo na pasta DAM raiz.

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

