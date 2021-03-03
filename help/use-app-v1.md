---
title: Use [!DNL Experience Manager] aplicativo de desktop versão 1.10.
description: Saiba como usar o aplicativo de desktop do Adobe Experience Manager versão 1.10 e otimizar seu trabalho com ativos no desktop.
translation-type: tm+mt
source-git-commit: 4870615ed40226964d077d6666b83b85b73da180
workflow-type: tm+mt
source-wordcount: '2373'
ht-degree: 0%

---


# Usar [!DNL Experience Manager] aplicativo de desktop v1.10 {#use-aem-desktop-app-v1x}

Usando o aplicativo, os ativos em [!DNL Experience Manager] são facilmente acessíveis no desktop local e podem ser usados em qualquer aplicativo de desktop. Os ativos podem ser facilmente revelados no Mac Finder ou no Windows Explorer, abertos em aplicativos de desktop e alterados localmente - as alterações são salvas em [!DNL Experience Manager] com uma nova versão criada no repositório.

Essa integração permite que várias funções na organização gerenciem os ativos de forma central no Assets e os acessem na Creative Cloud e em outros aplicativos, além de facilitar a adesão aos vários padrões, incluindo identidade visual.

As principais tarefas que você faz usando o [!DNL Experience Manager] aplicativo de desktop v1 incluem:

1. [Conectar com  [!DNL Experience Manager] um servidor](#installandconnect)
1. [Abrir ativos diretamente no desktop](#openondesktop)
1. [Editar e fazer check-out de ativos no desktop](#workonassets)
1. [Fazer upload de ativos e pastas em massa](#bulkupload)

Para as várias ações recomendadas e não ativas, consulte as [práticas recomendadas para usar o aplicativo](best-practices-for-v1.md). Se tiver problemas com o uso do aplicativo, consulte como [solucionar problemas [!DNL Experience Manager] desktop](troubleshoot-app-v1.md).

>[!NOTE]
>
>O aplicativo de desktop foi introduzido na versão [!DNL Experience Manager] 6.1 e foi chamado de [!DNL Experience Manager Assets Companion App].

## [!DNL Experience Manager] pontos de contato do aplicativo de desktop no fluxo de trabalho criativo  {#aem-desktop-app-touch-points-in-the-creative-workflow}

[!DNL Experience Manager] o aplicativo de desktop, juntamente com o  [!DNL Assets], integra-se ao fluxo de trabalho criativo e oferece os seguintes pontos de contato.

![[!DNL Experience Manager] o aplicativo de desktop aponta o fluxo de trabalho criativo](assets/aem_desktopapp_workflow.png)

[!DNL Experience Manager] o aplicativo de desktop aponta o fluxo de trabalho criativo

## Instalar e conectar o aplicativo ao servidor [!DNL Experience Manager] {#installandconnect}

Antes de começar a criar ou editar os ativos criativos, conecte o aplicativo de desktop ao servidor [!DNL Assets] para baixar e fazer upload de ativos no repositório. Execute as seguintes tarefas:

1. [Instale o aplicativo](#installapp).
1. [Defina suas ](#inapppref) preferências e detalhes da conexão.
1. [Conecte-se a  [!DNL Experience Manager] ](#connect) um repositório de ativos e monte como uma unidade local.
1. [Ative as ações ](#desktopactions) de desktop no  [!DNL Experience Manager] servidor.

[!DNL Experience Manager] o aplicativo de desktop usa uma conexão HTTPS para se conectar ao  [!DNL Experience Manager] servidor para transferir seus ativos de forma robusta e segura.

>[!NOTE]
>
>Para parte ou todas as etapas de instalação e configuração, talvez seja necessário obter ajuda do administrador [!DNL Experience Manager] ou do administrador do sistema.

### Instalar o aplicativo {#installapp}

Para usar [!DNL Experience Manager] aplicativo de desktop, verifique se a versão do servidor [!DNL Experience Manager] é compatível com o aplicativo. Baixe o arquivo de instalação apropriado (binário) para seu sistema operacional (Mac ou Windows) e instale o aplicativo.

A configuração detalhada pode ser necessária, dependendo das preferências da rede e do sistema. Consulte [Instalar e configurar [!DNL Experience Manager] aplicativo de desktop](install-configure-app-v1.md) para obter mais detalhes.

1. Vá para a [[!DNL Experience Manager] página de download do aplicativo de desktop v1.10](/help/release-notes-of-v1.md) e baixe o binário apropriado para seu sistema operacional.
1. Inicie o arquivo de instalação baixado e siga as instruções na tela para instalar o aplicativo.

   >[!NOTE]
   >
   >Somente uma instância do aplicativo de desktop [!DNL Experience Manager] pode ser instalada e estar ativa de cada vez.

### Entenda as opções e preferências no aplicativo {#inapppref}

O aplicativo permite que as configurações se conectem e se desconectem dos servidores [!DNL Experience Manager], visualizem o status de uploads, gerenciem o cache local e assim por diante. As configurações padrão funcionam para um usuário típico do aplicativo. Você pode ajustar as configurações para tirar mais proveito do aplicativo e da integração com o servidor [!DNL Experience Manager]. As várias configurações são descritas abaixo em detalhes.

**Explorar** ativosAbra a unidade local na qual o  [!DNL Assets] repositório está montado. Em outras palavras, explore os ativos que agora estão disponíveis no computador local.

**Exibir** status do ativoQuando os ativos alterados são carregados ou novos ativos são adicionados ao  [!DNL Assets] repositório, o aplicativo faz upload dos ativos em segundo plano. O upload em segundo plano permite operações sem problemas, sem precisar aguardar a conclusão do upload, especialmente para ativos de grande porte. Você pode salvar as alterações localmente e esquecê-las. O aplicativo leva algum tempo para enviar esses ativos para o servidor, dependendo da largura de banda disponível. Você pode verificar o status do upload, juntamente com algumas informações mais básicas.

**** OpçõesClique nas opções na bandeja do aplicativo de desktop para acessar as configurações para iniciar o aplicativo quando o sistema for iniciado; para se conectar ao  [!DNL Experience Manager] servidor quando o aplicativo for iniciado; e para alterar a letra da unidade local, onde  [!DNL Assets] está disponível após a montagem.

**Avançado > Gerenciar** cacheVocê pode controlar a quantidade de espaço em disco disponível para fins de armazenamento em cache local. Os artefatos do servidor [!DNL Assets] são armazenados em cache localmente para uma experiência mais suave. Você pode alterar os padrões para atender aos seus requisitos. Além disso, é possível limpar o cache para buscar todos os ativos novamente. Ao limpar o cache, ele preserva as alterações não salvas. Quaisquer ativos não verificados no servidor [!DNL Experience Manager] são retidos e não excluídos.

### Conecte-se a um servidor [!DNL Experience Manager] {#connect}

O aplicativo oferece suporte à configuração de proxy no Mac e no Windows. A configuração é lida quando o aplicativo é iniciado. Se modificar configurações de proxy, reinicie o aplicativo para que as alterações tenham efeito.

>[!NOTE]
>
>Se modificar as configurações de proxy, reinicie o aplicativo para que as alterações tenham efeito. Caso contrário, o aplicativo continuará a usar o servidor proxy configurado anteriormente.

1. Inicie o [!DNL Experience Manager] aplicativo de desktop. Para mapear a instância [!DNL Experience Manager] com o aplicativo, especifique o servidor [!DNL Experience Manager] no formato `https://[aem-server-url]:[port]`.

   ![Autentique no Mac e forneça o URL  [!DNL Experience Manager] do servidor](assets/aem_desktop_app_server_url.png)

1. Na tela de logon, especifique o nome de usuário e a senha da sua instância. Para especificar uma instância [!DNL Experience Manager] alternativa, selecione a opção **[!UICONTROL Alternate Login URL]**.

   ![Forneça credenciais  [!DNL Experience Manager] do servidor na tela de logon no aplicativo  [!DNL Experience Manager] de desktop](assets/login_screen_v1.png)

### Ativar ações da área de trabalho na [!DNL Experience Manager] interface da Web {#desktopactions}

Na interface do usuário do Assets, é possível explorar os locais dos ativos ou fazer check-out e abrir o ativo para edição no aplicativo de desktop. Essas opções são chamadas de ações da área de trabalho e não são ativadas por padrão. Siga estas etapas para habilitá-lo.

1. Na interface do Assets, clique/toque no ícone Usuário no canto superior direito da barra de ferramentas.
1. Clique em **[!UICONTROL My Preferences]** para exibir a caixa de diálogo **[!UICONTROL Preferences]**.

   ![[!DNL Experience Manager] interface com preferências do usuário](assets/aem_ui_user_preferences.png)

1. Na caixa de diálogo Preferências do usuário, selecione **[!UICONTROL Show Desktop Actions For Assets]**. Clique em **[!UICONTROL Accept]**.

   ![Marque  [!UICONTROL Show Desktop Actions For Assets] para ativar ações da área de trabalho](assets/enable_desktop_actions.png)

   *Figura: Marque Mostrar ações da área de trabalho para ativos para ativar as ações da área de trabalho.*

## Acessar e abrir ativos na área de trabalho {#openondesktop}

Quando você clica em **Abrir** para abrir um ativo no computador local, o aplicativo baixa o ativo no cache interno. O aplicativo inicia o aplicativo de desktop nativo associado ao tipo de arquivo do ativo baixado.

No Mac, selecione **Abrir** no menu de contexto para abrir um ativo por meio de [!DNL Experience Manager] aplicativo de desktop. No Windows, selecione Abrir na Web no menu de contexto para abrir o ativo. Na janela Status do ativo, clique/toque em ![Abrir no desktop ícone](assets/do-not-localize/aemassets_icon_openondesktop.png) para abrir o ativo.

Para arquivos do Adobe InDesign (INDD), selecione **[!UICONTROL Open]** no menu de contexto. Ao clicar nessa opção, o aplicativo baixa os ativos vinculados no seu sistema de arquivos local e abre o arquivo INDD no Adobe InDesign. Esse método garante que os ativos necessários estejam disponíveis localmente ao editar o arquivo INDD.

![Opções do menu de contexto para acessar e abrir ativos usando o aplicativo  [!DNL Experience Manager] de desktop](assets/aem_desktopapp_mac_context_menu.png)

*Figura: Opções do menu de contexto para acessar e abrir ativos usando o aplicativo  [!DNL Experience Manager] de desktop.*

>[!NOTE]
>
>No Windows, a [configuração padrão do Windows 7](https://support.microsoft.com/pt-BR/kb/2668751) impede que o [!DNL Experience Manager] aplicativo de desktop manipule ativos com mais de 50 MB.

<!-- TBD: The above note is for Windows 7 which is not supported by the app anymore. Remove it later.
-->

>[!NOTE]
>
>A Adobe recomenda acessar as Opções de visualização do localizador no Mac e desativar as opções **Mostrar informações do item**, **Mostrar visualização do item** e **Mostrar coluna de visualização** para a pasta montada [!DNL Assets]. Melhora o desempenho.

### Opções adicionais na interface [!DNL Experience Manager] {#additional-options-in-aem-assets}

Depois de mapear o repositório [!DNL Assets] para a unidade local, é possível ativar ícones adicionais e o recurso de Upload de pasta será exibido para os ativos e pastas mapeados.

1. Abra a interface [!DNL Assets] e passe o ponteiro do mouse sobre uma pasta ou ativo para exibir as ações da área de trabalho como ações rápidas na exibição Cartão.

   ![Na interface do usuário do Assets, abra o menu de ações rápidas para ver as ações da área de trabalho](assets/desktop_actions_in_card_view.png)

   *Figura: Na interface do usuário do Assets, abra o menu de ações rápidas para ver as ações da área de trabalho.*

   Essas ações da área de trabalho também estão disponíveis ao clicar na opção **Ações da área de trabalho** na barra de ferramentas depois de selecionar o ativo ou na barra de ferramentas na página de ativos.

1. Para abrir o ativo no aplicativo de desktop associado à extensão de arquivo específica, clique na ação rápida **Abrir no desktop** ![Abrir no desktop ícone](assets/do-not-localize/aemassets_icon_openondesktop.png).

   Como alternativa, escolha **Abrir** no menu **Ações da Área de Trabalho** na barra de ferramentas.

Para localizar o ativo específico em seu sistema de arquivos local, clique em **Revelar** ação rápida ![Ícone de revelação](assets/do-not-localize/aemassets_reveal_icon.png). Como alternativa, escolha **Revelar** no menu **Ações da Área de Trabalho** na barra de ferramentas.

## Entenda os status do ativo {#understand-the-asset-statuses}

| ![Ícone de aplicativo padrão do Windows](assets/do-not-localize/win_default.png) | O aplicativo está conectado ao servidor e todos os ativos são sincronizados. |
--- |--- |
| ![Ícone do Windows desativado](assets/do-not-localize/win_disabled.png) | O aplicativo é iniciado, mas não está conectado ao servidor. Alguns ativos podem estar pendentes na sincronização. |
| ![Ícone de sincronização de arquivos do Windows](assets/do-not-localize/win_sync.png) | Os ativos estão sincronizando. Os arquivos estão sendo carregados ou baixados. Você pode ver status exatos e pausar as transferências da janela Status do Ativo . |
| ![Ícone de reconexão do Windows](assets/do-not-localize/win_refresh.png) | O aplicativo está tentando se reconectar. Possivelmente, os problemas de rede estão fazendo com que ela se desconecte. |

## Trabalhe seus ativos {#workonassets}

### Confira os ativos da [!DNL Experience Manager] interface da Web {#check-out-assets-from-the-aem-web-interface}

[!DNL Assets] permite fazer check-out dos ativos para edição e check-in deles novamente depois de concluir a realização das alterações. Após fazer check-out de um ativo, somente você pode editar, anotar, publicar, mover ou excluir o ativo. Fazer check-out de um ativo bloqueia o ativo e impede que outros usuários executem qualquer uma dessas operações. Para fazer check-out/in de ativos, você precisa ter acesso de gravação.

Há duas maneiras de fazer check-out de ativos na interface da Web [!DNL Experience Manager]. Para obter informações detalhadas sobre o primeiro método, consulte [check-in e check-out de arquivos da interface do usuário do Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/check-out-and-submit-assets.html). Siga estas etapas, para os segundos métodos para fazer check-out e abrir o ativo quando [!DNL Experience Manager] o aplicativo de desktop estiver instalado.

1. Abra a interface [!DNL Assets] e passe o ponteiro do mouse sobre uma pasta ou ativo para exibir as ações da área de trabalho como ações rápidas na exibição Cartão.

   ![Opção Propriedades na exibição de cartão](assets/desktop_actions_in_card_view.png)

   Essas ações da área de trabalho também estão disponíveis ao clicar/tocar no ícone Ações da área de trabalho na barra de ferramentas depois de selecionar o ativo ou na barra de ferramentas na página do ativo.

1. Para abrir o ativo, clique/toque na ação rápida Abrir na área de trabalho ![Abrir no ícone da área de trabalho](assets/do-not-localize/aemassets_icon_openondesktop.png).

   Como alternativa, escolha Abrir no menu Ações da área de trabalho, na barra de ferramentas.

   >[!NOTE]
   >
   >Ao editar um arquivo que acabou de ser aberto e sem check-out, outros usuários não sabem que um ativo está sendo atualizado por você.

1. Para abrir um ativo para edição em um aplicativo da Adobe Creative Cloud, clique/toque na ação rápida Editar desktop ![Editar ícone da área de trabalho](assets/do-not-localize/aemassets_icon_editdesktop.png). Isso também verifica o ativo para edição. Após terminar a edição, marque no ativo para atualizar as alterações em [!DNL Assets].

   Como alternativa, escolha Editar no menu Ações da área de trabalho na barra de ferramentas.

1. Selecione a opção Open menu . Os ativos selecionados são abertos no modo de visualização.
1. Para editar os ativos, selecione a opção Editar . Os ativos são abertos no modo de edição.

### Confira os ativos do Finder no Mac OS {#check-out-assets-on-mac}

O aplicativo permite que você faça check-out dos arquivos de ativos para impedir que outros usuários modifiquem os arquivos nos quais você está trabalhando.

1. No menu de contexto Mac, selecione a opção Abrir pasta do AEM Assets para abrir o Finder.

   ![Opções do menu de contexto para acessar e abrir ativos usando o aplicativo  [!DNL Experience Manager] de desktop](assets/aem_desktopapp_mac_context_menu.png)

   *Figura: Opções do menu de contexto para acessar e abrir ativos usando o aplicativo  [!DNL Experience Manager] de desktop.*

1. Navegue até o ativo que deseja fazer check-out.
1. Clique com o botão direito do mouse no ativo e selecione Mais informações de ativos no menu de contexto.
1. Na caixa de diálogo Informações do ativo, clique/toque no ícone Check-out para verificar o ativo. O ícone Check-out é alternado para o ícone de check-in depois que você clica/toca nele.

   ![Navegue até o ativo para finalizar a compra](assets/browse_assets_to_checkout.png)

1. Para fazer check-in do ativo para que ele fique disponível para outros usuários, clique/toque no ícone de check-in na caixa de diálogo Informações do ativo .

### Confira os ativos no Windows {#check-out-assets-on-windows}

O aplicativo permite que você faça check-out dos arquivos de ativos para impedir que outros usuários modifiquem os arquivos nos quais você está trabalhando.

1. No menu Contexto, selecione Explorar ativos para abrir o Explorer.
1. No Explorer, navegue até o local do ativo que deseja fazer check-out.
1. Clique com o botão direito do mouse no ativo e selecione Abrir na Web no menu de contexto.
1. Na caixa de diálogo Informações do ativo, clique/toque no ícone Check-out . O ícone Check-out é alternado para o ícone de check-in.

   ![O ícone de finalização é alternado](assets/checkout_icon_toggles.png)

1. Revise o ativo no Explorer. O ícone de cadeado no ativo ![Ícone de cadeado de ativo](assets/do-not-localize/aemassets_icon_lockcheckout.png) indica que você fez o check-out do ativo.

   >[!NOTE]
   >
   >O ícone de cadeado pode aparecer após algum atraso. [!DNL Experience Manager] o aplicativo de desktop armazena os ativos em cache para acesso rápido, portanto, pode levar alguns minutos para atualizar o status bloqueado.

1. Para fazer o check-in do ativo para que ele esteja disponível para outros usuários, clique/toque no ícone de check-in na caixa de diálogo **Informações do ativo**.

### Fazer check-in de um ativo usando o Finder ou o Explorer e usando a interface da Web {#check-in-an-asset-using-finder-or-explorer-and-using-web-interface}

Quando terminar de editar os ativos, salve-os no aplicativo de desktop. No menu de contexto, selecione **Mais informações de ativos** e clique em check-in.

Os ativos são carregados no servidor [!DNL Experience Manager]. Como opção, você pode verificar o status do upload selecionando **Exibir status do ativo** no ícone da bandeja do sistema. Como alternativa, você pode fazer check-in de um ativo na interface da Web [!DNL Experience Manager]. Clique nos ativos com check-out ou selecione-os. Na barra de ferramentas, clique no ícone de check-in ![ícone de check-in](assets/do-not-localize/aemassets_icon_checkin.png).

Um ativo é carregado para [!DNL Experience Manager] automaticamente depois que qualquer alteração é salva localmente. O check-in disponibiliza o ativo para outros [!DNL Experience Manager] usuários para edição.

### Fazer upload em massa de ativos e pastas para o servidor [!DNL Experience Manager] {#bulkupload}

Usando o [!DNL Experience Manager] aplicativo de desktop, você pode fazer upload de uma pasta inteira contendo ativos do diretório de arquivos local para [!DNL Assets]. Dessa forma, todos os ativos na pasta são carregados em massa em vez de precisar carregá-los um de cada vez.

1. Na interface do usuário do Assets, clique/toque em **Criar** na barra de ferramentas e escolha **Fazer upload da pasta** no menu.
1. Navegue até a pasta que deseja fazer upload e selecione-a.
1. Clique/toque em OK. A caixa de diálogo Status dos ativos exibe o status do upload.

   ![Consulte o status do upload na janela Status do ativo](assets/aem_desktopapp_bulkupload_status.png)

   Consulte o status do upload na janela Status do ativo

   >[!NOTE]
   >
   >Você pode pausar ou cancelar manualmente o upload clicando/tocando no ícone apropriado.

1. Depois que a pasta for carregada, feche a caixa de diálogo e navegue até a interface do usuário do Assets. A pasta carregada é exibida na interface da Web.

A Adobe não recomenda copiar-colar ou arrastar um número maior de arquivos ou pastas aninhadas, do sistema de arquivos local, para a área de compartilhamento de rede. O aplicativo não pode controlar o processo de upload devido a limitações técnicas e o desempenho é ruim.

Como alternativa, selecione os arquivos/pastas que deseja fazer upload para [!DNL Experience Manager] no Finder ou Explorer, copie-os para a área de transferência do sistema, navegue até a pasta de destino na área de compartilhamento de rede e, no menu de contexto do aplicativo de desktop [!DNL Experience Manager] selecione **Colar ativos**. Dessa forma, [!DNL Experience Manager] o aplicativo de desktop inicia o upload dos ativos colados semelhantes à opção **Fazer upload da pasta** disponível na interface da Web [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [ [!DNL Experience Manager] Solução de problemas do aplicativo de desktop](troubleshoot-app-v1.md)

