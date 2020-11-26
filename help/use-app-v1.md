---
title: Use o aplicativo [!DNL Experience Manager] para desktop versão 1.x.
description: Saiba como usar o aplicativo Adobe Experience Manager para desktop versão 1.x e otimizar seu trabalho com ativos no desktop.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 2893fc1f8aad02e1436a1a281a320e6837487220
workflow-type: tm+mt
source-wordcount: '2379'
ht-degree: 0%

---


# Usar aplicativo [!DNL Experience Manager] para desktop v1.x {#use-aem-desktop-app-v1x}

Using the App, the assets within [!DNL Experience Manager] are easily accessible on your local desktop and can be used in any desktop applications. Os ativos podem ser facilmente revelados no Mac Finder ou no Windows Explorer, abertos em aplicativos de desktop e alterados localmente - as alterações são salvas de volta [!DNL Experience Manager] com uma nova versão criada no repositório.

Essa integração permite que várias funções na organização gerenciem os ativos centralmente no Assets e os acessem no Creative Cloud e em outros aplicativos, além de facilitar o cumprimento dos vários padrões, inclusive a marca.

As principais tarefas que você usa o aplicativo de [!DNL Experience Manager] desktop v1 incluem:

1. [Conectar-se com [!DNL Experience Manager] um servidor](#installandconnect)
1. [Abrir ativos diretamente no desktop](#openondesktop)
1. [Editar e fazer check-out de ativos do desktop](#workonassets)
1. [Carregar ativos e pastas em massa](#bulkupload)

Para as várias ações recomendadas e não ativas, consulte as práticas [recomendadas para o uso do aplicativo](best-practices-for-v1.md). Se você enfrentar problemas ao usar o aplicativo, veja como [ [!DNL Experience Manager] solucionar problemas da área de trabalho](troubleshoot-app-v1.md).

>[!NOTE]
>
>[!DNL Experience Manager] o aplicativo desktop foi introduzido na versão [!DNL Experience Manager] 6.1 e foi chamado [!DNL Experience Manager Assets Companion App].

## [!DNL Experience Manager] pontos de contato do aplicativo desktop no fluxo de trabalho criativo {#aem-desktop-app-touch-points-in-the-creative-workflow}

[!DNL Experience Manager] o aplicativo desktop, juntamente com [!DNL Assets]o, integra o fluxo de trabalho criativo e oferta os seguintes pontos de contato.

![[!DNL Experience Manager] o aplicativo desktop aponta o fluxo de trabalho criativo](assets/aem_desktopapp_workflow.png)

[!DNL Experience Manager] o aplicativo desktop aponta o fluxo de trabalho criativo

## Instalar e conectar o aplicativo ao [!DNL Experience Manager] servidor {#installandconnect}

Antes de começar a criar ou editar os ativos criativos, conecte o aplicativo de desktop ao [!DNL Assets] servidor para baixar e fazer upload dos ativos no repositório. Execute as seguintes tarefas:

1. [Instale o aplicativo](#installapp).
1. [Defina suas preferências](#inapppref) e detalhes da conexão.
1. [Conecte-se a [!DNL Experience Manager] um repositório de ativos do servidor](#connect) e monte-o como uma unidade local.
1. [Habilitar ações](#desktopactions) da área de trabalho no [!DNL Experience Manager] servidor.

[!DNL Experience Manager] o aplicativo desktop usa uma conexão HTTPS para se conectar ao [!DNL Experience Manager] servidor para transferir seus ativos de forma robusta e segura.

>[!NOTE]
>
>Para parte ou todas as etapas de instalação e configuração, talvez você precise de ajuda do administrador [!DNL Experience Manager] ou do administrador do sistema.

### Instale o aplicativo {#installapp}

Para usar o aplicativo [!DNL Experience Manager] desktop, verifique se a versão do seu [!DNL Experience Manager] servidor é suportada pelo aplicativo. Baixe o arquivo de instalação apropriado (binário) para seu sistema operacional (Mac ou Windows) e instale o aplicativo.

A configuração detalhada pode ser necessária, dependendo das preferências da rede e do sistema. Consulte [Instalar e [!DNL Experience Manager] configurar o aplicativo](install-configure-app-v1.md) desktop para obter mais detalhes.

1. Vá para a página [[!DNL Experience Manager] de download do aplicativo de](https://helpx.adobe.com/experience-manager/kb/download-companion-app.html) desktop e baixe o binário apropriado para seu sistema operacional.
1. Inicie o arquivo de instalação baixado e siga as instruções na tela para instalar o aplicativo.

   >[!NOTE]
   >
   >Somente uma instância do aplicativo de [!DNL Experience Manager] desktop pode ser instalada e estar ativa de cada vez.

### Entenda as opções e preferências no aplicativo {#inapppref}

O aplicativo permite que as configurações se conectem e se desconectem dos [!DNL Experience Manager] servidores, status de visualização dos uploads, gerenciamento do cache local e assim por diante. As configurações padrão funcionam para um usuário típico do aplicativo. Você pode ajustar as configurações para aproveitar ao máximo o aplicativo e sair da integração com o [!DNL Experience Manager] servidor. As várias configurações são descritas abaixo em detalhes.

**Explorar ativos** Abra a unidade local na qual o [!DNL Assets] repositório está montado. Em outras palavras, explore os ativos que agora estão disponíveis em sua máquina local.

**Status** do ativo de visualização Quando os ativos alterados são carregados ou novos ativos são adicionados ao [!DNL Assets] repositório, o aplicativo carrega os ativos em segundo plano. O upload em segundo plano permite operações suaves, sem a necessidade de aguardar a conclusão do upload, especialmente para ativos de grande porte. Você pode salvar suas alterações localmente e esquecê-las. O aplicativo leva algum tempo para enviar esses ativos para o servidor, dependendo da largura de banda disponível. Você pode verificar o status do upload, juntamente com algumas informações mais básicas.

**Opções** Clique nas opções na bandeja do aplicativo para desktop para acessar as configurações para iniciar o aplicativo quando o sistema for start; conectar-se ao [!DNL Experience Manager] servidor quando o aplicativo for iniciado; e para alterar a letra da unidade local onde [!DNL Assets] está disponível após a montagem.

**Avançado > Gerenciar cache** Você pode controlar a quantidade de espaço em disco disponível para fins de armazenamento em cache local. Os artefatos do [!DNL Assets] servidor são armazenados em cache localmente para proporcionar uma experiência mais suave. Você pode alterar os padrões para atender às suas necessidades. Além disso, você pode limpar o cache para obter todos os ativos novamente. Quando você limpa o cache, ele preserva suas alterações não salvas. Todos os ativos não verificados no [!DNL Experience Manager] servidor são retidos e não excluídos.

### Conectar-se a um [!DNL Experience Manager] servidor {#connect}

O aplicativo oferece suporte à configuração proxy no Mac e no Windows. A configuração é lida quando o aplicativo é start. Se você modificar as configurações de proxy, reinicie o aplicativo para que as alterações entrem em vigor.

>[!NOTE]
>
>Se você modificar as configurações de proxy, reinicie o aplicativo para que as alterações entrem em vigor. Caso contrário, o aplicativo continuará usando o servidor proxy configurado anteriormente.

1. Inicie o aplicativo de [!DNL Experience Manager] desktop. Para mapear sua [!DNL Experience Manager] instância com o aplicativo, especifique seu [!DNL Experience Manager] servidor no formato `https://[aem-server-url]:[port]`.

   ![Autentique no Mac e forneça o URL [!DNL Experience Manager] do servidor](assets/aem_desktop_app_server_url.png)

1. Na tela de logon, especifique o nome de usuário e a senha para sua instância. Para especificar uma [!DNL Experience Manager] instância alternativa, selecione a **[!UICONTROL Alternate Login URL]** opção.

   ![Forneça as credenciais [!DNL Experience Manager] do servidor na tela de logon no aplicativo de [!DNL Experience Manager] desktop](assets/login_screen_v1.png)

### Ativar ações da área de trabalho na interface [!DNL Experience Manager] da Web {#desktopactions}

Na interface do usuário do Assets, você pode explorar os locais dos ativos ou fazer check-out e abrir o ativo para edição no aplicativo de desktop. Essas opções são chamadas de ações da área de trabalho e não são ativadas por padrão. Siga estas etapas para ativá-la.

1. Na interface Ativos, clique/toque no ícone Usuário no canto superior direito da barra de ferramentas.
1. Clique em **[!UICONTROL My Preferences]** para exibir a **[!UICONTROL Preferences]** caixa de diálogo.

   ![[!DNL Experience Manager] interface com preferências do usuário](assets/aem_ui_user_preferences.png)

1. Na caixa de diálogo Preferências do usuário, selecione **[!UICONTROL Show Desktop Actions For Assets]**. Clique em **[!UICONTROL Accept]**.

   ![Marque [!UICONTROL Show Desktop Actions For Assets] para ativar ações da área de trabalho](assets/enable_desktop_actions.png)

   *Figura: Marque Mostrar ações da área de trabalho para ativos para ativar as ações da área de trabalho.*

## Acessar e abrir ativos em seu desktop {#openondesktop}

Quando você clica em **Abrir** para abrir um ativo no computador local, o aplicativo baixa o ativo em seu cache interno. O aplicativo inicia o aplicativo desktop nativo associado ao tipo de arquivo do ativo baixado.

No Mac, selecione **Abrir** no menu de contexto para abrir um ativo pelo aplicativo de [!DNL Experience Manager] desktop. No Windows, selecione Abrir na Web no menu de contexto para abrir o ativo. Na janela Status do ativo, clique/toque em ![Abrir no ícone](assets/do-not-localize/aemassets_icon_openondesktop.png) da área de trabalho para abrir o ativo.

Para arquivos Adobe InDesign (INDD), selecione **[!UICONTROL Open]** no menu de contexto. Quando você clica nessa opção, o aplicativo baixa os ativos vinculados no seu sistema de arquivos local e abre o arquivo INDD no Adobe InDesign. Esse método garante que os ativos necessários estejam disponíveis localmente ao editar o arquivo INDD.

![Opções do menu de contexto para acessar e abrir ativos usando o aplicativo de [!DNL Experience Manager] desktop](assets/aem_desktopapp_mac_context_menu.png)

*Figura: Opções do menu de contexto para acessar e abrir ativos usando o aplicativo de [!DNL Experience Manager] desktop.*

>[!NOTE]
>
>No Windows, a configuração [](https://support.microsoft.com/en-us/kb/2668751) padrão do Windows 7 impede que o aplicativo [!DNL Experience Manager] desktop manipule ativos com mais de 50 MB.

>[!NOTE]
>
>O Adobe recomenda que você vá para Opções de Visualização do Finder no Mac e desative as opções **Mostrar informações** do item, **Mostrar pré-visualização** do item e **Mostrar coluna** de pré-visualização para a [!DNL Assets] pasta montada. Ele melhora o desempenho.

### Opções adicionais na [!DNL Experience Manager] interface {#additional-options-in-aem-assets}

Depois de mapear o [!DNL Assets] repositório para a unidade local, é possível ativar ícones adicionais e o recurso de Upload de pasta será exibido para os ativos e pastas mapeados.

1. Abra a [!DNL Assets] interface e passe o ponteiro do mouse sobre uma pasta ou um ativo para exibir as ações da área de trabalho como ações rápidas na visualização do cartão.

   ![Na interface do usuário do Assets, abra o menu de ações rápidas para ver as ações da área de trabalho](assets/desktop_actions_in_card_view.png)

   *Figura: Na interface do usuário do Assets, abra o menu de ações rápidas para ver as ações da área de trabalho.*

   Essas ações da área de trabalho também estão disponíveis quando você clica na opção Ações **da** área de trabalho na barra de ferramentas depois de selecionar o ativo ou na barra de ferramentas na página do ativo.

1. Para abrir o ativo no aplicativo de área de trabalho associado à extensão de arquivo específica, clique no ícone **Abrir na ação rápida da área de trabalho** ![](assets/do-not-localize/aemassets_icon_openondesktop.png)Abrir na área de trabalho.

   Como alternativa, escolha **Abrir** no menu Ações **da** área de trabalho na barra de ferramentas.

Para localizar o ativo específico no sistema de arquivos local, clique em **Revelar** ação rápida ![ícone](assets/do-not-localize/aemassets_reveal_icon.png)Revelar. Como alternativa, escolha **Revelar** no menu Ações **da** área de trabalho na barra de ferramentas.

## Compreender os status dos ativos {#understand-the-asset-statuses}

| ![Ícone de aplicativo padrão do Windows](assets/do-not-localize/win_default.png) | O aplicativo está conectado ao servidor e todos os ativos são sincronizados. |
--- |--- |
| ![Ícone desativado do Windows](assets/do-not-localize/win_disabled.png) | O aplicativo é iniciado, mas não está conectado ao servidor. Alguns ativos podem estar com sincronização pendente. |
| ![Ícone de sincronização de arquivos do Windows](assets/do-not-localize/win_sync.png) | Os ativos estão sincronizando. Os arquivos estão sendo carregados ou baixados. Você pode ver os status exatos e pausar as transferências na janela Status do Ativo. |
| ![Ícone de reconexão do Windows](assets/do-not-localize/win_refresh.png) | O aplicativo está tentando se reconectar. Os possíveis problemas de rede estão fazendo com que ela se desconecte. |

## Trabalhe com seus ativos {#workonassets}

### Verificar ativos na interface da [!DNL Experience Manager] Web {#check-out-assets-from-the-aem-web-interface}

[!DNL Assets] permite que você faça check-out dos ativos para edição e faça check-in deles novamente depois de concluir a realização das alterações. Depois de fazer check-out de um ativo, somente você pode editar, anotar, publicar, mover ou excluir o ativo. Fazer check-out de um ativo bloqueia o ativo e impede que outros usuários executem qualquer uma dessas operações. Para poder fazer check-out/check-in de ativos, você precisa ter acesso de gravação neles.

Há duas maneiras de fazer check-out de ativos na interface da [!DNL Experience Manager] Web. Para obter informações detalhadas sobre o primeiro método, consulte arquivos de [check-in e check-out da interface do usuário](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/check-out-and-submit-assets.html)do Assets. Siga estas etapas para obter os segundo métodos de dar baixa e abrir o ativo quando o aplicativo [!DNL Experience Manager] desktop estiver instalado.

1. Abra a [!DNL Assets] interface e passe o ponteiro do mouse sobre uma pasta ou um ativo para exibir as ações da área de trabalho como ações rápidas na visualização do cartão.

   ![Opção Propriedades na Visualização de cartão](assets/desktop_actions_in_card_view.png)

   Essas ações da área de trabalho também estão disponíveis quando você clica/toca no ícone Ações da área de trabalho na barra de ferramentas depois de selecionar o ativo ou na barra de ferramentas na página do ativo.

1. Para abrir o ativo, clique/toque na ação rápida Abrir na área de trabalho ![Abrir no ícone](assets/do-not-localize/aemassets_icon_openondesktop.png)da área de trabalho.

   Como alternativa, escolha Abrir no menu Ações da área de trabalho na barra de ferramentas.

   >[!NOTE]
   >
   >Quando você edita um arquivo que acabou de ser aberto e não teve check-out, outros usuários não sabem que um ativo está sendo atualizado por você.

1. Para abrir um ativo para edição em um aplicativo Adobe Creative Cloud, clique/toque no ícone ![Editar desktop da ação rápida](assets/do-not-localize/aemassets_icon_editdesktop.png)Editar área de trabalho. Isso também verifica o ativo para edição. Após terminar a edição, faça o check-in do ativo para atualizar as alterações no [!DNL Assets].

   Como alternativa, escolha Editar no menu Ações da área de trabalho na barra de ferramentas.

1. Selecione a opção de menu Abrir. Os ativos selecionados são abertos no modo de pré-visualização.
1. Para editar os ativos, selecione a opção Editar. Os ativos são abertos no modo de edição.

### Verificar ativos do Finder no Mac OS {#check-out-assets-on-mac}

O aplicativo permite que você faça check-out dos arquivos de ativos para impedir que outros usuários modifiquem os arquivos nos quais você está trabalhando.

1. No menu de contexto do Mac, selecione a opção Abrir pasta do AEM Assets para abrir o Finder.

   ![Opções do menu de contexto para acessar e abrir ativos usando o aplicativo de [!DNL Experience Manager] desktop](assets/aem_desktopapp_mac_context_menu.png)

   *Figura: Opções do menu de contexto para acessar e abrir ativos usando o aplicativo de [!DNL Experience Manager] desktop.*

1. Navegue até o ativo que deseja fazer check-out.
1. Clique com o botão direito do mouse no ativo e selecione Mais informações de ativos no menu de contexto.
1. Na caixa de diálogo Informações do ativo, clique/toque no ícone de Check-out para fazer check-out do ativo. O ícone Check-out alterna para o ícone de check-in depois que você clica/toca nele.

   ![Navegue até o ativo para fazer check-out](assets/browse_assets_to_checkout.png)

1. Para fazer check-in do ativo de modo que ele esteja disponível para outros usuários, clique/toque no ícone de check-in na caixa de diálogo Informações do ativo.

### Verificar ativos no Windows {#check-out-assets-on-windows}

O aplicativo permite que você faça check-out dos arquivos de ativos para impedir que outros usuários modifiquem os arquivos nos quais você está trabalhando.

1. No menu Contexto, selecione Explorar ativos para abrir o Explorer.
1. No Explorer, navegue até o local do ativo que deseja fazer check-out.
1. Clique com o botão direito do mouse no ativo e selecione Abrir na Web no menu de contexto.
1. Na caixa de diálogo Informações do ativo, clique/toque no ícone Check-out. O ícone Check-out alterna para o ícone de check-in.

   ![O ícone de finalização alterna](assets/checkout_icon_toggles.png)

1. Revise o ativo no Explorer. O ícone de cadeado no ícone ![de cadeado](assets/do-not-localize/aemassets_icon_lockcheckout.png) de ativo indica que você fez check-out do ativo.

   >[!NOTE]
   >
   >O ícone de cadeado pode aparecer após algum atraso. [!DNL Experience Manager] o aplicativo desktop armazena os ativos em cache para acesso rápido, portanto, pode levar alguns minutos para atualizar o status bloqueado.

1. Para fazer check-in do ativo de modo que ele esteja disponível para outros usuários, clique/toque no ícone de check-in na caixa de diálogo Informações **do** ativo.

### Fazer check-in de um ativo usando o Finder ou o Explorer e a interface da Web {#check-in-an-asset-using-finder-or-explorer-and-using-web-interface}

Quando terminar de editar os ativos, salve os ativos no aplicativo de desktop. No menu de contexto, selecione **Mais informações** de ativos e clique em check-in.

Os ativos são carregados no [!DNL Experience Manager] servidor. Como opção, você pode verificar o status do upload selecionando **Visualização Asset Status** (Status do ativo de ) no ícone da bandeja do sistema. Como alternativa, você pode fazer check-in de um ativo na interface da [!DNL Experience Manager] Web. Clique nos ativos com check-out ou selecione-os. Na barra de ferramentas, clique no ícone de check-in no ícone de ![check-in](assets/do-not-localize/aemassets_icon_checkin.png).

Um ativo é carregado para [!DNL Experience Manager] automaticamente depois que qualquer alteração é salva localmente. O check-in disponibiliza o ativo para outros [!DNL Experience Manager] usuários para edição.

### Fazer upload em massa de ativos e pastas para o [!DNL Experience Manager] servidor {#bulkupload}

Usando o aplicativo [!DNL Experience Manager] desktop, você pode carregar uma pasta inteira contendo ativos do diretório de arquivos local para [!DNL Assets]. Dessa forma, todos os ativos dentro da pasta são carregados em massa, em vez de serem carregados um de cada vez.

1. Na interface do usuário do Assets, clique/toque em **Criar** na barra de ferramentas e escolha **Carregar pasta** no menu.
1. Navegue até a pasta que deseja carregar e selecione-a.
1. Clique/toque em OK. A caixa de diálogo Status dos ativos exibe o status do upload.

   ![Consulte o status do upload na janela Status do ativo](assets/aem_desktopapp_bulkupload_status.png)

   Consulte o status do upload na janela Status do ativo

   >[!NOTE]
   >
   >Você pode pausar ou cancelar manualmente o upload clicando/tocando no ícone apropriado.

1. Depois que a pasta for carregada, feche a caixa de diálogo e navegue até a interface do usuário dos ativos. A pasta carregada é exibida na interface da Web.

O Adobe não recomenda copiar e colar ou arrastar um número maior de arquivos ou pastas aninhadas, do sistema de arquivos local, para a área de compartilhamento de rede. O aplicativo não pode controlar o processo de upload devido a limitações técnicas e o desempenho é ruim.

Como alternativa, selecione os arquivos/pastas para os quais deseja carregar [!DNL Experience Manager] no Finder ou no Explorer, copie-os para a área de transferência do sistema, navegue até a pasta do público alvo na área de compartilhamento de rede e, no menu de contexto do aplicativo de [!DNL Experience Manager] desktop, selecione **Colar ativos**. Dessa forma, os start de aplicativos de desktop que carregam os ativos colados são semelhantes à opção [!DNL Experience Manager] Carregar pasta **disponível na interface** [!DNL Experience Manager] da Web.

>[!MORELIKETHIS]
>
>* [Solução de [!DNL Experience Manager] problemas do aplicativo de desktop](troubleshoot-app-v1.md)

