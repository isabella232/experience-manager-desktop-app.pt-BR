---
title: Usar o aplicativo AEM para desktop versão 1.x.
description: Saiba como usar o aplicativo Adobe Experience Manager para desktop versão 1.x e otimizar seu trabalho com ativos no desktop.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 68cc5ee80aa12c08b48098ad666ca694b843405a

---


# Usar o aplicativo de desktop AEM v1.x {#use-aem-desktop-app-v1x}

Usando o aplicativo, os ativos no AEM são facilmente acessíveis em seu desktop local e podem ser usados em qualquer aplicativo de desktop. Os ativos podem ser facilmente revelados no Mac Finder ou no Windows Explorer, abertos em aplicativos de desktop e alterados localmente - as alterações são salvas no AEM com uma nova versão criada no repositório.

Essa integração permite que várias funções na organização gerenciem os ativos centralmente nos ativos AEM e os acessem na Creative Cloud e em outros aplicativos, além de facilitar a adesão aos vários padrões, inclusive a marca.

As principais tarefas que você faz usando o aplicativo de desktop AEM v1 incluem:

1. [Conectar-se a um servidor AEM](#installandconnect)
1. [Abrir ativos diretamente no desktop](#openondesktop)
1. [Editar e fazer check-out de ativos do desktop](#workonassets)
1. [Carregar ativos e pastas em massa](#bulkupload)

Para as várias ações recomendadas e não ativas, consulte as práticas [recomendadas para o uso do aplicativo](best-practices-for-v1.md). Se você enfrentar problemas ao usar o aplicativo, veja como [solucionar problemas na área de trabalho](troubleshoot-app-v1.md)do AEM.

>[!NOTE]
>
>O aplicativo de desktop AEM foi introduzido na versão 6.1 do AEM e foi chamado de Aplicativo associado do AEM Assets.

## Pontos de contato do aplicativo para desktop AEM no fluxo de trabalho criativo {#aem-desktop-app-touch-points-in-the-creative-workflow}

O aplicativo AEM Desktop, juntamente com os ativos AEM, integra seu fluxo de trabalho criativo e oferta os seguintes pontos de contato.

![O aplicativo AEM Desktop aponta o fluxo de trabalho criativo para o toque do aplicativo](assets/aem_desktopapp_workflow.png)

O aplicativo AEM Desktop aponta o fluxo de trabalho criativo para o toque do aplicativo

## Instalar e conectar o aplicativo de desktop AEM ao servidor AEM {#installandconnect}

Antes de começar a criar ou editar os ativos criativos, conecte o aplicativo de desktop ao servidor dos ativos AEM para baixar e fazer upload dos ativos no repositório. Execute as seguintes tarefas:

1. [Instale o aplicativo](#installapp).
1. [Defina suas preferências](#inapppref) e detalhes da conexão.
1. [Conecte-se a um servidor](#connect) AEM e monte o repositório de ativos como unidade local.
1. [Habilitar ações](#desktopactions) da área de trabalho no servidor AEM.

O aplicativo de desktop AEM usa uma conexão HTTPS para se conectar ao servidor AEM para transferir seus ativos de forma robusta e segura.

>[!NOTE]
>Para parte ou todas as etapas de instalação e configuração, talvez você precise de ajuda do administrador do AEM ou do administrador do sistema.

### Instale o aplicativo {#installapp}

Para usar o aplicativo de desktop AEM, verifique se a versão do servidor AEM é compatível com o aplicativo de desktop AEM. Baixe o arquivo de instalação apropriado (binário) para seu sistema operacional (Mac ou Windows) e instale o aplicativo.

A configuração detalhada pode ser necessária, dependendo das preferências da rede e do sistema. Consulte [Instalar e configurar o aplicativo](install-configure-app-v1.md) AEM Desktop para obter mais detalhes.

1. Acesse a página [de download do aplicativo para desktop](https://helpx.adobe.com/experience-manager/kb/download-companion-app.html) AEM e baixe o binário apropriado para seu sistema operacional.
1. Inicie o arquivo de instalação baixado e siga as instruções na tela para instalar o aplicativo.

   >[!NOTE]
   >Somente uma instância do aplicativo de desktop do AEM pode ser instalada e estar ativa de cada vez.

### Entenda as opções e preferências no aplicativo {#inapppref}

O aplicativo permite que as configurações se conectem e se desconectem dos servidores AEM, status de visualização de uploads, gerenciamento do cache local e assim por diante. As configurações padrão funcionam para um usuário típico do aplicativo. Você pode ajustar as configurações para aproveitar ao máximo o aplicativo e sair da integração com o servidor AEM. As várias configurações são descritas abaixo em detalhes.

**Explorar ativos** Abra a unidade local na qual o repositório do AEM Assets está montado. Em outras palavras, explore os ativos que agora estão disponíveis em sua máquina local.

**Status** do ativo de Visualização Quando os ativos alterados são carregados ou novos ativos são adicionados ao repositório do AEM Assets, o aplicativo carrega os ativos em segundo plano. O upload em segundo plano permite operações suaves, sem a necessidade de aguardar a conclusão do upload, especialmente para ativos de grande porte. Você pode salvar suas alterações localmente e esquecê-las. O aplicativo leva algum tempo para enviar esses ativos para o servidor, dependendo da largura de banda disponível. Você pode verificar o status do upload, juntamente com algumas informações mais básicas.

**Opções** Clique/toque em Opções na bandeja do aplicativo para desktop do AEM para acessar as configurações para iniciar o aplicativo quando o sistema for start; para conectar-se ao servidor AEM quando o aplicativo for iniciado; e para alterar a letra da unidade local onde os ativos AEM estão disponíveis após a montagem.

**Avançado > Gerenciar cache** Você pode controlar a quantidade de espaço em disco disponível para fins de armazenamento em cache local. Os artefatos do servidor do AEM Assets são armazenados em cache localmente para proporcionar uma experiência mais suave. Você pode alterar os padrões para atender às suas necessidades. Além disso, você pode limpar o cache para obter todos os ativos novamente. Quando você limpa o cache, ele preserva suas alterações não salvas. Todos os ativos não verificados no servidor AEM são retidos e não excluídos.

### Conectar-se a um servidor AEM {#connect}

O aplicativo oferece suporte à configuração proxy no Mac e no Windows. A configuração é lida quando o aplicativo é start. Se você modificar as configurações de proxy, reinicie o aplicativo para que as alterações entrem em vigor.

>[!NOTE]
>
>Se você modificar as configurações de proxy, reinicie o aplicativo para que as alterações entrem em vigor. Caso contrário, o aplicativo continuará usando o servidor proxy configurado anteriormente.

1. Inicie o aplicativo AEM Desktop. Para mapear a instância do AEM com o aplicativo, especifique o servidor AEM no formato `https://[aem-server-url]:[port]`.

   ![Autentique no Mac e forneça o URL do servidor AEM](assets/aem_desktop_app_server_url.png)

1. Na tela de logon, especifique o nome de usuário e a senha para sua instância. Para especificar uma instância alternativa do AEM, selecione a **[!UICONTROL Alternate Login URL]** opção.

   ![Forneça credenciais do servidor AEM na tela de logon na área de trabalho do AEM](assets/chlimage_1-2.png)

### Ativar ações da área de trabalho na interface da Web do AEM {#desktopactions}

Na interface do usuário do Assets, você pode explorar os locais dos ativos ou fazer check-out e abrir o ativo para edição no aplicativo de desktop. Essas opções são chamadas de ações da área de trabalho e não são ativadas por padrão. Siga estas etapas para ativá-la.

1. Na interface Ativos, clique/toque no ícone Usuário no canto superior direito da barra de ferramentas.
1. Clique em **[!UICONTROL My Preferences]** para exibir a **[!UICONTROL Preferences]** caixa de diálogo.

   ![Interface do AEM com preferências do usuário](assets/aem_ui_user_preferences.png)

1. Na caixa de diálogo Preferências do usuário, selecione **[!UICONTROL Show Desktop Actions For Assets]**. Clique em **[!UICONTROL Accept]**.

   ![Marque Mostrar ações da área de trabalho para ativos para ativar ações da área de trabalho](assets/chlimage_1-3.png)

   *Figura: Marque Mostrar ações da área de trabalho para ativos para ativar as ações da área de trabalho.*

## Acessar e abrir ativos em seu desktop {#openondesktop}

Quando você clica em **Abrir** para abrir um ativo no computador local, o aplicativo baixa o ativo em seu cache interno. O aplicativo inicia o aplicativo desktop nativo associado ao tipo de arquivo do ativo baixado.

No Mac, selecione **Abrir** no menu de contexto para abrir um ativo por meio do aplicativo de desktop AEM. No Windows, selecione Abrir na Web no menu de contexto para abrir o ativo. Na janela Status do ativo, clique/toque em ![Abrir no ícone](assets/aemassets_icon_openondesktop.png) da área de trabalho para abrir o ativo.

Para arquivos do Adobe InDesign (INDD), selecione **[!UICONTROL Open]** no menu de contexto. Quando você clica nessa opção, o aplicativo baixa os ativos vinculados para seu sistema de arquivos local e abre o arquivo INDD no Adobe InDesign. Esse método garante que os ativos necessários estejam disponíveis localmente ao editar o arquivo INDD.

![Opções do menu de contexto para acessar e abrir ativos usando o aplicativo da área de trabalho do AEM](assets/aem_desktopapp_mac_context_menu.png)

*Figura: Opções do menu de contexto para acessar e abrir ativos usando o aplicativo de desktop do AEM.*

>[!NOTE]
>No Windows, a configuração [](https://support.microsoft.com/en-us/kb/2668751) padrão do Windows 7 impede que o aplicativo de desktop do AEM manipule ativos com mais de 50 MB.

>[!NOTE]
>
>A Adobe recomenda que você vá para Opções de Visualização do Finder no Mac e desative as opções **Mostrar informações** do item, **Mostrar pré-visualização** do item e **Mostrar coluna** pré-visualização para a pasta AEM Assets montada. Ele melhora o desempenho.

### Opções adicionais na interface do AEM {#additional-options-in-aem-assets}

Depois de mapear o repositório dos ativos AEM para a unidade local, é possível ativar ícones adicionais e o recurso de Upload de pasta para os ativos e pastas mapeados.

1. Abra a interface dos ativos AEM e passe o ponteiro sobre uma pasta ou um ativo para exibir as ações da área de trabalho como ações rápidas na visualização de cartão.

   ![Na interface do usuário do Assets, abra o menu de ações rápidas para ver as ações da área de trabalho](assets/chlimage_1-4.png)

   *Figura: Na interface do usuário do Assets, abra o menu de ações rápidas para ver as ações da área de trabalho.*

   Essas ações da área de trabalho também estão disponíveis quando você clica no ícone Ações **da** área de trabalho na barra de ferramentas depois de selecionar o ativo ou na barra de ferramentas na página do ativo.

1. Para abrir o ativo no aplicativo de desktop associado à extensão de arquivo específica, clique/toque na ação rápida **Abrir no desktop** ![Abrir no ícone](assets/aemassets_icon_openondesktop.png)da área de trabalho.

   Como alternativa, escolha **Abrir** no menu Ações **da** área de trabalho na barra de ferramentas.

Para localizar o ativo específico no sistema de arquivos local, clique em **Revelar** ação rápida ![ícone](assets/aemassets_reveal_icon.png)Revelar. Como alternativa, escolha **Revelar** no menu Ações **da** área de trabalho na barra de ferramentas.

## Compreender os status dos ativos {#understand-the-asset-statuses}

| ![Ícone de aplicativo padrão do Windows](assets/win_default.png) | O aplicativo está conectado ao servidor e todos os ativos são sincronizados. |
|------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Ícone desativado do Windows](assets/win_disabled.png) | O aplicativo é iniciado, mas não está conectado ao servidor. Alguns ativos podem estar com sincronização pendente. |
| ![Ícone de sincronização de arquivos do Windows](assets/win_sync.png) | Os ativos estão sincronizando. Os arquivos estão sendo carregados ou baixados. Você pode ver os status exatos e pausar as transferências na janela Status do Ativo. |
| ![Ícone de reconexão do Windows](assets/win_refresh.png) | O aplicativo está tentando se reconectar. Os possíveis problemas de rede estão fazendo com que ela se desconecte. |

## Trabalhe com seus ativos {#workonassets}

### Verificar ativos na interface da Web do AEM {#check-out-assets-from-the-aem-web-interface}

Os ativos AEM permitem que você faça check-out dos ativos para edição e faça check-in deles novamente depois de concluir as alterações. Depois de fazer check-out de um ativo, somente você pode editar, anotar, publicar, mover ou excluir o ativo. Fazer check-out de um ativo bloqueia o ativo e impede que outros usuários executem qualquer uma dessas operações. Para poder fazer check-out/check-in de ativos, você precisa ter acesso de gravação neles.

Há duas maneiras de fazer check-out dos ativos na interface da Web do AEM. Para obter informações detalhadas sobre o primeiro método, consulte arquivos de [check-in e check-out da interface do usuário](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/check-out-and-submit-assets.html)do Assets. Siga estas etapas para obter os segundo métodos de dar baixa e abrir o ativo quando o aplicativo da área de trabalho AEM estiver instalado.

1. Abra a interface dos ativos AEM e passe o ponteiro sobre uma pasta ou um ativo para exibir as ações da área de trabalho como ações rápidas na visualização de cartão.

   ![Opção Propriedades na Visualização de cartão](assets/chlimage_1-4.png)

   Essas ações da área de trabalho também estão disponíveis quando você clica/toca no ícone Ações da área de trabalho na barra de ferramentas depois de selecionar o ativo ou na barra de ferramentas na página do ativo.

1. Para abrir o ativo, clique/toque na ação rápida Abrir na área de trabalho ![Abrir no ícone](assets/aemassets_icon_openondesktop.png)da área de trabalho.

   Como alternativa, escolha Abrir no menu Ações da área de trabalho na barra de ferramentas.

   >[!NOTE]
   >Quando você edita um arquivo que acabou de ser aberto e não teve check-out, outros usuários não sabem que um ativo está sendo atualizado por você.

1. Para abrir um ativo para edição em um aplicativo da Adobe Creative Cloud, clique/toque no ícone ![Editar desktop da ação rápida](assets/aemassets_icon_editdesktop.png)Editar área de trabalho. Isso também verifica o ativo para edição. Após terminar a edição, faça o check-in do ativo para atualizar as alterações nos ativos AEM.

   Como alternativa, escolha Editar no menu Ações da área de trabalho na barra de ferramentas.

1. Selecione a opção de menu Abrir. Os ativos selecionados são abertos no modo de pré-visualização.
1. Para editar os ativos, selecione a opção Editar. Os ativos são abertos no modo de edição.

### Verificar ativos do Finder no Mac OS {#check-out-assets-on-mac}

O aplicativo permite que você faça check-out dos arquivos de ativos para impedir que outros usuários modifiquem os arquivos nos quais você está trabalhando.

1. No menu de contexto do Mac, selecione a pasta Abrir ativos AEM para abrir o Finder.

   ![Opções do menu de contexto para acessar e abrir ativos usando o aplicativo da área de trabalho do AEM](assets/aem_desktopapp_mac_context_menu.png)

   Opções do menu de contexto para acessar e abrir ativos usando o aplicativo da área de trabalho do AEM

1. Navegue até o ativo que deseja fazer check-out.

   ![Abrir no menu de contexto AEM Assets no Mac](assets/chlimage_1-5.png)

1. Clique com o botão direito do mouse no ativo e selecione Mais informações de ativos no menu de contexto.
1. Na caixa de diálogo Informações do ativo, clique/toque no ícone de Check-out para fazer check-out do ativo. O ícone Check-out alterna para o ícone de check-in depois que você clica/toca nele.

   ![Navegue até o ativo para fazer check-out](assets/chlimage_1-6.png)

1. Para fazer check-in do ativo de modo que ele esteja disponível para outros usuários, clique/toque no ícone de check-in na caixa de diálogo Informações do ativo.

### Verificar ativos no Windows {#check-out-assets-on-windows}

O aplicativo permite que você faça check-out dos arquivos de ativos para impedir que outros usuários modifiquem os arquivos nos quais você está trabalhando.

1. No menu Contexto, selecione Explorar ativos para abrir o Explorer.
1. No Explorer, navegue até o local do ativo que deseja fazer check-out.

   ![O ícone de finalização alterna](assets/chlimage_1-7.png)

1. Clique com o botão direito do mouse no ativo e selecione Abrir na Web no menu de contexto.
1. Na caixa de diálogo Informações do ativo, clique/toque no ícone Check-out. O ícone Check-out alterna para o ícone de check-in.

   ![O ícone de finalização alterna](assets/chlimage_1-8.png)

1. Revise o ativo no Explorer. O ícone de cadeado no ícone ![de cadeado](assets/aemassets_icon_lockcheckout.png) de ativo indica que você fez check-out do ativo.

   >[!NOTE]
   >O ícone de cadeado pode aparecer após algum atraso. O aplicativo de desktop AEM armazena os ativos em cache para acesso rápido, portanto, pode levar alguns minutos para atualizar o status bloqueado.

1. Para fazer check-in do ativo de modo que ele esteja disponível para outros usuários, clique/toque no ícone de check-in na caixa de diálogo Informações **do** ativo.

### Fazer check-in de um ativo usando o Finder ou o Explorer e a interface da Web {#check-in-an-asset-using-finder-or-explorer-and-using-web-interface}

Quando terminar de editar os ativos, salve os ativos no aplicativo de desktop. No menu de contexto, selecione **Mais informações** de ativos e clique em check-in.

Os ativos são carregados no servidor AEM. Como opção, você pode verificar o status do upload selecionando **Visualização Asset Status** (Status do ativo de ) no ícone da bandeja do sistema. Como alternativa, você pode fazer check-in de um ativo na interface da Web do AEM. Clique nos ativos com check-out ou selecione-os. Na barra de ferramentas, clique no ícone de check-in no ícone de ![check-in](assets/aemassets_icon_checkin.png).

Um ativo é carregado automaticamente no AEM depois que qualquer alteração é salva localmente. O check-in disponibiliza o ativo para outros usuários do AEM para edição.

### Fazer upload em massa de ativos e pastas para o servidor AEM {#bulkupload}

Usando o AEM Desktop, você pode carregar uma pasta inteira contendo ativos do diretório de arquivos local para os ativos AEM. Dessa forma, todos os ativos dentro da pasta são carregados em massa, em vez de serem carregados um de cada vez.

1. Na interface do usuário do Assets, clique/toque em **Criar** na barra de ferramentas e escolha **Carregar pasta** no menu.
1. Navegue até a pasta que deseja carregar e selecione-a.
1. Clique/toque em OK. A caixa de diálogo Status dos ativos exibe o status do upload.

   ![Consulte o status do upload na janela Status do ativo](assets/aem_desktopapp_bulkupload_status.png)

   Consulte o status do upload na janela Status do ativo

   >[!NOTE]
   >Você pode pausar ou cancelar manualmente o upload clicando/tocando no ícone apropriado.

1. Depois que a pasta for carregada, feche a caixa de diálogo e navegue até a interface do usuário dos ativos. A pasta carregada é exibida na interface da Web.

A Adobe não recomenda copiar e colar ou arrastar um número maior de arquivos ou pastas aninhadas, do sistema de arquivos local, para a área de compartilhamento de rede. O aplicativo não pode controlar o processo de upload devido a limitações técnicas e o desempenho é ruim.

Como alternativa, selecione os arquivos/pastas que deseja carregar no AEM no Finder ou no Explorer, copie-os para a área de transferência do sistema, navegue até a pasta do público alvo na área de compartilhamento de rede e, no menu de contexto do aplicativo para desktop do AEM, selecione **Colar ativos**. Dessa forma, os start de aplicativos de desktop do AEM carregam os ativos colados de maneira semelhante à opção **Carregar pasta** disponível na interface da Web do AEM.

>[!MORELIKETHIS]
>
>* [Introdução ao aplicativo de desktop do AEM](https://helpx.adobe.com/customer-care-office-hours/aem/desktop-app.html)
>* [Entenda o check-in/check-out com o aplicativo de desktop do AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/collaboration/checkin-checkout-technical-video-understand.html)
>* [Solução de problemas do aplicativo de desktop AEM](troubleshoot-app-v1.md)

