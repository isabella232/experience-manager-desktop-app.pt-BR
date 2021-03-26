---
title: Práticas recomendadas para o aplicativo de desktop e solução de problemas [!DNL Adobe Experience Manager] i
description: Siga as práticas recomendadas e solucione problemas para resolver os problemas ocasionais relacionados à instalação, atualização, configuração e assim por diante.
translation-type: tm+mt
source-git-commit: 9d90bdcab79604e03d1ad3f30ed2aca2eb03e1c5
workflow-type: tm+mt
source-wordcount: '2110'
ht-degree: 0%

---


# Solucionar problemas do [!DNL Adobe Experience Manager] aplicativo de desktop {#troubleshoot-v2}

[!DNL Adobe Experience Manager] o aplicativo de desktop se conecta a um repositório DAM (Digital Asset Management, gerenciamento de ativos digitais) de  [!DNL Experience Manager] implantação. O aplicativo busca informações do repositório e resultados de pesquisa em sua máquina, baixa e carrega arquivos e pastas e inclui recursos para gerenciar conflitos com a interface do usuário do Assets.

Leia para solucionar problemas do aplicativo, aprenda as práticas recomendadas e descubra as limitações.

## Práticas recomendadas {#best-practices-to-prevent-troubles}

Siga as práticas recomendadas a seguir para evitar alguns problemas comuns e a solução de problemas.

* **Entenda como o aplicativo de desktop funciona**: Antes de começar a usar o aplicativo, passe alguns minutos sabendo como ele funciona. Saiba mais sobre a vinculação entre [!DNL Experience Manager] a interface da Web e o desktop, o mapeamento do repositório, o armazenamento em cache de ativos, a gravação local e o upload em segundo plano. Consulte [como funciona](release-notes.md#how-app-works).

* **Evite caracteres não suportados em nomes** de pastas: Não use espaços em branco e caracteres inválidos ao criar ou carregar pastas. Consulte uma lista de caracteres em [Criar pastas em [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders). Alguns casos de uso [!DNL Experience Manager] podem ser afetados por caracteres não suportados no nome da pasta.

* **Práticas recomendadas para evitar conflitos**: Para evitar possíveis conflitos ao colaborar em vários ativos, consulte  [evitar conflitos](using.md#adv-workflow-collaborate-avoid-conflicts) de edição.

* **Use o upload de pastas para pastas** grandes e hierárquicas: Em vez de usar a interface da Web do Assets ou outros métodos, use o aplicativo de  [!DNL Experience Manager] desktop para fazer upload de pastas grandes. O aplicativo faz upload dos ativos em segundo plano com logon e monitoramento. Consulte [ativos de upload em massa](using.md#bulk-upload-assets).

* **Use a versão** mais recente: Use a versão mais recente do aplicativo e sempre verifique a compatibilidade antes de instalar uma nova versão do aplicativo ou antes de atualizar para uma  [!DNL Experience Manager] versão mais recente. Consulte as [notas de versão](release-notes.md).

* **Use a mesma letra** de unidade: Use a mesma letra de unidade em uma organização para mapear para o  [!DNL Experience Manager] DAM. Para ver os ativos colocados por outros usuários, os caminhos devem ser os mesmos. Usar a mesma letra de unidade garante um caminho constante para ativos DAM. Os ativos permanecem posicionados e não são removidos mesmo se letras de unidade diferentes forem usadas por usuários diferentes.

* **Considere a rede**: O desempenho da rede é fundamental para o desempenho do aplicativo de  [!DNL Experience Manager] desktop. Se você enfrentar uma resposta lenta a transferências de arquivos ou operações em massa, desative os recursos ou aplicativos que podem causar muito tráfego de rede.

* **Casos de uso não suportados para o aplicativo** de desktop: Não use o aplicativo para migração de Ativos (ele precisa de planejamento e outras ferramentas); para operações DAM pesadas (como mover pastas grandes, uploads grandes, encontrar arquivos usando pesquisas avançadas de metadados); e como cliente de sincronização (os princípios de design e os padrões de uso são diferentes dos clientes em sincronia, como o Microsoft OneDrive ou o Adobe Creative Cloud Desktop Sync).

* **Tempo limite**: Atualmente, o aplicativo de desktop não tem um valor de tempo limite configurável que desconecta a conexão entre o  [!DNL Experience Manager] servidor e o aplicativo de desktop após um intervalo de tempo fixo. Ao fazer upload de ativos grandes, se a conexão expirar depois de um tempo, o aplicativo tenta fazer upload do ativo algumas vezes, aumentando o tempo limite de upload. Não há uma maneira recomendada de alterar as configurações de tempo limite padrão.

## Como solucionar problemas {#troubleshooting-prep}

Para solucionar problemas do aplicativo de desktop, esteja ciente das seguintes informações. Além disso, ele o prepara para transmitir melhor os problemas ao Atendimento ao cliente do Adobe se você optar por solicitar suporte.

### Localização dos arquivos de log {#check-log-files-v2}

[!DNL Experience Manager] o aplicativo de desktop armazena seus arquivos de log nos seguintes locais, dependendo do sistema operacional:

No Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

No Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

Ao carregar muitos ativos, se alguns arquivos não forem carregados, consulte o arquivo `backend.log` para identificar os uploads com falha.

>[!NOTE]
>
>Ao trabalhar com o Atendimento ao cliente do Adobe em uma solicitação de suporte ou tíquete, você pode ser solicitado a compartilhar os arquivos de log para ajudar a equipe de Atendimento ao cliente a entender o problema. Arquive toda a pasta `Logs` e compartilhe-a com o contato do Atendimento ao cliente.

### Alterar o nível de detalhes em arquivos de log {#level-of-details-in-log}

Para alterar o nível de detalhes nos arquivos de log:

1. Verifique se o aplicativo não está em execução.

1. No sistema Windows:

   1. Abra uma janela de comando.

   1. Inicie o [!DNL Adobe Experience Manager] aplicativo de desktop executando o comando:

   ```shell
   set AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe
   ```

   No sistema Mac:

   1. Abra uma janela de terminal.

   1. Inicie o [!DNL Adobe Experience Manager] aplicativo de desktop executando o comando:

   ```shell
   AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app
   ```

Os níveis de log válidos são DEBUG, INFO, WARN ou ERROR. A verbosidade dos logs é mais alta em DEBUG e mais baixa em ERROR.

### Ativar o modo de depuração {#enable-debug-mode}

Para solucionar problemas, você pode habilitar o modo de depuração e obter mais informações nos logs.

>[!NOTE]
>
>Níveis de log válidos são DEBUG, INFO, WARN ou ERROR. A verbosidade dos logs é mais alta em DEBUG e mais baixa em ERROR.

Para usar o aplicativo no modo de depuração no Mac:

1. Abra uma janela de terminal ou um prompt de comando.

1. Inicie o aplicativo de desktop [!DNL Experience Manager] executando o seguinte comando:

   `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`.

Para ativar o modo de depuração no Windows:

1. Abra uma janela de comando.

1. Inicie o [!DNL Experience Manager] aplicativo de desktop executando o seguinte comando:

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`.

### Limpar cache {#clear-cache-v2}

Execute as seguintes etapas:

1. Inicie o aplicativo e conecte uma instância [!DNL Experience Manager].

1. Abra as preferências do aplicativo clicando nas reticências no canto superior direito e selecionando [!UICONTROL Preferences].

1. Localize a entrada que exibe [!UICONTROL Current Cache Size]. Clique no ícone da lixeira ao lado desse elemento.

Para limpar manualmente o cache, continue com as etapas abaixo.

>[!CAUTION]
>
>Esta é uma operação potencialmente destrutiva. Se houver alterações de arquivo local que não sejam carregadas em [!DNL Adobe Experience Manager], essas alterações serão perdidas ao prosseguir.

O cache é limpo excluindo o diretório de cache do aplicativo, que é encontrado nas preferências do aplicativo.

1. Inicie o aplicativo.

1. Abra as preferências do aplicativo selecionando as reticências no canto superior direito e selecionando [!UICONTROL Preferences].

1. Observe o valor [!UICONTROL Cache Directory].

   Nesse diretório, há subdiretórios nomeados após os Endpoints [!DNL Adobe Experience Manager] codificados. Os nomes são uma versão codificada do URL [!DNL Adobe Experience Manager] direcionado. Por exemplo, se o aplicativo estiver direcionando `localhost:4502`, o nome do diretório será `localhost_4502`.

Para limpar o cache, exclua o diretório Endpoint [!DNL Adobe Experience Manager] codificado desejado. Como alternativa, excluir o diretório inteiro especificado nas preferências limpará o cache para todas as instâncias que foram usadas pelo aplicativo.

Limpar o cache do [!DNL Adobe Experience Manager] aplicativo de desktop é uma tarefa preliminar de solução de problemas que pode resolver vários problemas. Limpe o cache das preferências do aplicativo. Consulte [definir preferências](install-upgrade.md#set-preferences). O local padrão da pasta de cache é:

### Saiba mais sobre a versão [!DNL Adobe Experience Manager] do aplicativo de desktop {#know-app-version-v2}

Para ver o número da versão:

1. Inicie o aplicativo.

1. Clique nas reticências no canto superior direito, passe o mouse sobre [!UICONTROL Help] e clique em [!UICONTROL About].

   O número da versão é listado nesta tela.

### Não é possível ver os ativos colocados {#placed-assets-missing}

Se não conseguir ver os ativos que você ou outros profissionais criativos colocaram nos arquivos de suporte (por exemplo, arquivos INDD), verifique o seguinte:

* Conexão com o servidor. A conectividade de rede flexível pode paralisar downloads de ativos.

* Tamanho de arquivo. Os ativos grandes demoram mais para serem baixados e exibidos.

* Consistência da letra da unidade. Se você ou outro colaborador colocou os ativos ao mapear o [!DNL Experience Manager] DAM para uma letra de unidade diferente, os ativos colocados não são exibidos.

* Permissões. Para verificar se você tem permissões para buscar os ativos inseridos, entre em contato com o administrador [!DNL Experience Manager].

### As edições em arquivos na interface do usuário do aplicativo de desktop não refletem em [!DNL Adobe Experience Manager] imediatamente {#changes-on-da-not-visible-on-aem}

[!DNL Adobe Experience Manager] o aplicativo de desktop deixa ao usuário a decisão de quando todas as edições em um arquivo são concluídas. Dependendo do tamanho e da complexidade de um arquivo, leva um tempo significativo para transferir a nova versão de um arquivo de volta para [!DNL Adobe Experience Manager]. O design do aplicativo exige a minimização do número de vezes que um arquivo é transferido de um lado para o outro, em vez de adivinhar quando as edições do arquivo são concluídas e carregadas automaticamente. É recomendável que o usuário inicie a transferência do arquivo de volta para [!DNL Adobe Experience Manager] optando por fazer upload das alterações de um arquivo.

### Problemas ao atualizar no macOS {#issues-when-upgrading-on-macos}

Ocasionalmente, podem ocorrer problemas ao atualizar o [!DNL Experience Manager] aplicativo de desktop no macOS. Isso é causado pela pasta herdada do sistema para o aplicativo de desktop [!DNL Experience Manager], impedindo que novas versões do aplicativo de desktop [!DNL Experience Manager] sejam carregadas corretamente. Para solucionar esse problema, as pastas e os arquivos a seguir podem ser removidos manualmente.

Antes de executar as etapas a seguir, arraste o aplicativo `Adobe Experience Manager Desktop` da pasta Aplicativos macOS para a Lixeira. Em seguida, abra o terminal, execute o seguinte comando e forneça sua senha quando solicitado.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

### Não é possível carregar arquivos {#upload-fails}

Se você estiver usando o aplicativo de desktop com [!DNL Experience Manager] 6.5.1 ou posterior, atualize o conector S3 ou Azure para a versão 1.10.4 ou posterior. Ele resolve o problema de falha de carregamento de arquivo relacionado a [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). Consulte [instruções de instalação](install-upgrade.md#install-v2).

### [!DNL Experience Manager] problemas de conexão do aplicativo de desktop  {#connection-issues}

Se você estiver tendo problemas gerais de conectividade, veja algumas maneiras de obter mais informações sobre o que o [!DNL Experience Manager] aplicativo de desktop está fazendo.

**Verificar o log de solicitações**

[!DNL Experience Manager] o aplicativo de desktop registra todas as solicitações que envia, juntamente com o código de resposta de cada solicitação, em um arquivo de log dedicado.

1. Abra `request.log` no diretório de log do aplicativo para ver essas solicitações.

1. Cada linha no log representa uma solicitação ou uma resposta. As solicitações terão um caractere `>` seguido pelo URL que foi solicitado. As respostas terão um caractere `<` seguido pelo código de resposta e pelo URL que foi solicitado. As Solicitações e a Resposta podem ser correspondidas usando o GUID de cada linha.

**Verificar solicitações carregadas pelo navegador incorporado do aplicativo**

A maioria das solicitações do aplicativo é encontrada no log de solicitações. No entanto, se não houver informações úteis, pode ser útil examinar as solicitações enviadas pelo navegador incorporado do aplicativo.
Consulte a seção [SAML](#da-connection-issue-with-saml-aem) para obter instruções sobre como visualizar essas solicitações.

#### Autenticação de logon SAML não funciona {#da-connection-issue-with-saml-aem}

[!DNL Experience Manager] o aplicativo de desktop pode não se conectar à  [!DNL Adobe Experience Manager] implantação habilitada para SSO (SAML). O design do aplicativo tenta acomodar as variações e complexidades de conexões e processos SSO. No entanto, uma configuração pode exigir solução de problemas adicional.

Às vezes, o processo SAML não redireciona para o caminho solicitado originalmente ou o redirecionamento final é para um host diferente do que é configurado no aplicativo de desktop [!DNL Adobe Experience Manager]. Para verificar se não é o caso:

1. Abra um navegador da Web. Acesse o URL `https://[aem_server]:[port]/content/dam.json`.

1. Faça logon na implantação [!DNL Adobe Experience Manager].

1. Quando o logon for concluído, verifique o endereço atual do navegador na barra de endereços. Deve corresponder exatamente ao URL que foi inserido inicialmente.

1. Verifique também se tudo antes de `/content/dam.json` corresponde ao valor [!DNL Adobe Experience Manager] de destino configurado nas configurações do [!DNL Adobe Experience Manager] aplicativo de desktop.

**O processo de logon SAML funciona corretamente de acordo com as etapas acima, mas os usuários ainda não conseguem fazer logon**

A janela no aplicativo de desktop [!DNL Adobe Experience Manager] que exibe o processo de logon é simplesmente um navegador da Web que exibe a interface do usuário da Web da instância de destino [!DNL Adobe Experience Manager]:

* A versão do Mac usa um [WebView](https://developer.apple.com/documentation/webkit/webview).

* A versão do Windows usa CefSharp ](https://cefsharp.github.io/) baseado em Chromium.[

Certifique-se de que o processo SAML seja compatível com esses navegadores.

Para solucionar mais problemas, é possível exibir os URLs exatos que o navegador está tentando carregar. Para ver essas informações:

1. Siga as instruções para iniciar o aplicativo no [modo de depuração](#enable-debug-mode).

1. Reproduza a tentativa de logon.

1. Navegue até [diretório de log](#check-log-files-v2) do aplicativo

1. Para Windows:

   1. Abra &quot;aemcompanionlog.txt&quot;.

   1. Pesquise por mensagens que começam com &quot;Endereço do navegador de login alterado para&quot;. Essas entradas também contêm o URL que o aplicativo carregou.

   Para Mac:

   1. `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`, em que o  **** número é substituído pelo número que estiver no nome de arquivo mais recente.

   1. Procure mensagens que comecem com &quot;quadro carregado&quot;. Essas entradas também contêm o URL que o aplicativo carregou.


Olhar a sequência de URL que está sendo carregada pode ajudar a solucionar problemas no final do SAML para determinar o que está errado.

#### Problema de configuração SSL {#ssl-config-v2}

As bibliotecas que o [!DNL Experience Manager] aplicativo de desktop usa para comunicação HTTP usam a imposição estrita de SSL. Às vezes, uma conexão pode ser bem-sucedida usando um navegador, mas falha ao usar [!DNL Experience Manager] aplicativo de desktop. Para configurar o SSL adequadamente, instale o certificado intermediário ausente no Apache. Consulte [Como instalar um certificado CA intermediário no Apache](https://access.redhat.com/solutions/43575).

As bibliotecas que o [!DNL Experience Manager] aplicativo de desktop usa para comunicação HTTP utilizam a imposição rigorosa do SSL. Portanto, pode haver instâncias em que as conexões SSL que têm sucesso por meio de um navegador falham com o [!DNL Adobe Experience Manager] aplicativo de desktop. Isso é bom porque incentiva a configuração correta do SSL e aumenta a segurança, mas pode ser frustrante quando o aplicativo não consegue se conectar.

A abordagem recomendada nesse caso é usar uma ferramenta para analisar o certificado SSL de um servidor e identificar problemas para que eles possam ser corrigidos. Há sites que inspecionam o certificado de um servidor ao fornecer o URL.

Como medida temporária, é possível desabilitar a imposição SSL estrita no [!DNL Adobe Experience Manager] aplicativo de desktop. Essa não é uma solução de longo prazo recomendada, pois reduz a segurança ao ocultar a causa raiz do SSL configurado incorretamente. Para desativar a imposição estrita:

1. Use o editor de sua escolha para editar o arquivo de configuração JavaScript do aplicativo, que é encontrado (por padrão) nos seguintes locais (dependendo do sistema operacional):

   No Mac: `/Applications/Adobe Experience Manager Desktop.app/Contents/Resources/javascript/lib-smb/config.json`

   No Windows: `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop\javascript\config.json`

1. Localize a seguinte seção no arquivo :

   ```shell
   ...
   "assetRepository": {
       "options": {
   ...
   ```

1. Modifique a seção adicionando `"strictSSL": false` da seguinte maneira:

   ```shell
   ...
   "assetRepository": {
       "options": {
           "strictSSL": false,
   ...
   ```

1. Salve o arquivo e reinicie o [!DNL Adobe Experience Manager] aplicativo de desktop.

### O aplicativo não responde {#unresponsive}

Raramente, o aplicativo pode ficar sem resposta, exibir apenas uma tela branca ou exibir um erro na parte inferior da interface, sem opções na interface. Tente o seguinte na ordem:

* Clique com o botão direito na interface do aplicativo e clique em **[!UICONTROL Refresh]**.
* Saia do aplicativo e abra-o novamente.

Em ambos os métodos, o aplicativo é iniciado na pasta DAM raiz.

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
>* [Evite conflitos de edição](using.md#adv-workflow-collaborate-avoid-conflicts)

