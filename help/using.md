---
title: Usar  [!DNL Experience Manager] aplicativo de desktop
description: Use [!DNL Adobe Experience Manager] desktop app, to work with [!DNL Adobe Experience Manager] DAM assets diretamente do desktop Win ou Mac e use em outros aplicativos.
mini-toc-levels: 1
feature: Aplicativo para desktop, Gerenciamento de ativos
exl-id: fa19d819-231a-4a01-bfd2-6bba6fec2f18
source-git-commit: bc938588d0d54a6f3b8b85e0d4097104f9df46c9
workflow-type: tm+mt
source-wordcount: '3923'
ht-degree: 0%

---

# Use [!DNL Adobe Experience Manager] aplicativo de desktop {#use-aem-desktop-app-v2}

Use o [!DNL Adobe Experience Manager] aplicativo de desktop para acessar facilmente os ativos digitais armazenados no repositório DAM [!DNL Adobe Experience Manager] em seu desktop local e usar esses ativos em qualquer aplicativo de desktop. Você pode abrir os ativos em aplicativos de desktop e editar os ativos localmente - faça upload das alterações de volta para [!DNL Experience Manager] com controle de versão, para compartilhar as atualizações com outros usuários. Você também pode fazer upload de novos arquivos e hierarquias de pastas para [!DNL Experience Manager], criar pastas e excluir ativos ou pastas do [!DNL Experience Manager] DAM.

A integração permite que várias funções na organização gerenciem os ativos centralmente em [!DNL Experience Manager Assets] e acessem os ativos no desktop local nos aplicativos nativos no Windows ou Mac OS.

Ao abrir o aplicativo após fazer logoff ou pela primeira vez, forneça o URL do seu servidor [!DNL Experience Manager] no formato `https://[aem-server-url]:[port]/`. Em seguida, selecione a opção [!UICONTROL Connect] . Forneça credenciais para conectar o aplicativo ao servidor.

As principais tarefas que você faz usando o aplicativo de desktop [!DNL Experience Manager] são:

![Fluxos de trabalho e tarefas que você pode realizar usando o  [!DNL Experience Manager] aplicativo de ](assets/aem_desktop_app_usecases_v2.png "desktopFluxos de trabalho e tarefas que você pode realizar  [!DNL Adobe Experience Manager] usando o ")
aplicativo de desktopBaixe este arquivo PDF pronto para  [](assets/aem_desktop_app_usecases_print.pdf) impressão.

## Como o aplicativo de desktop funciona {#how-app-works2}

Antes de começar a usar o aplicativo, entenda [Como o aplicativo funciona](release-notes.md#how-app-works). Além disso, familiarize-se com os seguintes termos:

* **[!UICONTROL Desktop Actions]**: Na interface da Web Assets, de dentro de um navegador, é possível explorar os locais dos ativos ou fazer check-out e abrir o ativo para edição no aplicativo de desktop nativo. Essas ações estão disponíveis na interface da Web e usam a funcionalidade de aplicativo de desktop. Consulte [como ativar as Ações da Área de Trabalho](using.md#desktopactions-v2).

* O status do arquivo é **[!UICONTROL Cloud Only]**: Esses ativos não são baixados no computador local e estão disponíveis somente no servidor [!DNL Experience Manager].

* O status do arquivo é **[!UICONTROL Available locally]**: Os ativos são baixados e disponibilizados no computador local como estão. Os ativos não são alterados.

* O status do arquivo é **[!UICONTROL Edited locally]**: Esses ativos são modificados localmente e as alterações permanecem no servidor [!DNL Experience Manager] carregado. Após o upload, o status é alterado para [!UICONTROL Available locally]. Consulte [editar ativos](using.md#edit-assets-upload-updated-assets).

* O status do arquivo é **[!UICONTROL Editing conflict]**: Se você e outros usuários modificarem um ativo simultaneamente, o aplicativo indica que ocorreu um conflito de edição. O aplicativo também fornece opções para manter ou descartar suas alterações. Consulte [como evitar conflitos de edição](using.md#adv-workflow-collaborate-avoid-conflicts).

* O status do arquivo é **[!UICONTROL Modified remotely]**: O aplicativo indica se um ativo que você baixou foi alterado no servidor [!DNL Experience Manager]. O aplicativo também fornece a opção de baixar a versão mais recente e atualizar a cópia local. Consulte [como evitar conflitos de edição](using.md#adv-workflow-collaborate-avoid-conflicts).

* **[!UICONTROL Check-out]**: Se você estiver editando um arquivo ou pretende editar um arquivo, alterne o status para sair. Ele adiciona um ícone de bloqueio no ativo no aplicativo e na interface da Web [!DNL Experience Manager]. O ícone de bloqueio indica para outros usuários para evitar a edição simultânea do mesmo ativo, pois gera um conflito de edição.

* **[!UICONTROL Check-in]**: Marque o ativo como seguro para outros usuários editarem sem causar um conflito de edição. Ao fazer upload das alterações, o ícone de bloqueio é removido automaticamente. Alternar o status de check-in também remove o ícone de bloqueio, embora seja recomendável não fazer o check-in manualmente sem fazer upload das alterações. Se você descartar as alterações, alterne manualmente o check-in.

* **[!UICONTROL Open]** ação: Basta abrir o ativo para pré-visualizá-lo no aplicativo nativo. Não é recomendável editar o ativo usando essa ação, pois ele não faz check-out do ativo e outros usuários podem fazer edições que levam a conflitos de edição.

* **[!UICONTROL Edit]** ação: Use a ação para modificar a imagem. Clicar em [!UICONTROL Edit] faz o check-out automático do ativo e adiciona um ícone de bloqueio no ativo. Depois de clicar em Editar, se você não quiser editar o ativo, clique em [!UICONTROL Toggle check-in]. Para excluir, renomear ou mover ativos na hierarquia de pastas [!DNL Experience Manager] do DAM, use as [!DNL Experience Manager] ações da interface da Web e não a ação de edição.

* **[!UICONTROL Download]** ação: Baixe o ativo no computador local. Você pode baixar os ativos agora e editar posteriormente; trabalhe offline e carregue as alterações posteriormente. Os ativos são baixados em uma pasta de cache no sistema de arquivos.

* **[!UICONTROL Reveal File]** ou  **[!UICONTROL Reveal Folder]** ação: Enquanto os ativos são baixados para uma pasta de cache local, o aplicativo imita uma unidade de rede local e fornece um caminho local para cada ativo. Para conhecer esse caminho, use a opção de revelação apropriada no aplicativo. A ação Revelar é necessária para colocar ativos no aplicativo Creative Cloud. Consulte [colocar ativos](using.md#place-assets-in-native-documents).

* **[!UICONTROL Open In Web]** ação: Para exibir o ativo na interface  [!DNL Experience Manager] da Web, abra-o na Web. Você pode iniciar mais workflows a partir da interface [!DNL Experience Manager] como atualizar metadados ou descoberta de ativos.

* **[!UICONTROL Delete]** ação: Exclua o ativo do repositório  [!DNL Experience Manager] DAM. A ação exclui a cópia original do ativo no servidor do Experience Manager. Se desejar descartar apenas as modificações no ativo local, consulte [descartar alterações](using.md#edit-assets-upload-updated-assets).

* **[!UICONTROL Upload Changes]**: O aplicativo de desktop faz upload do ativo atualizado somente quando você faz upload explícito para o  [!DNL Experience Manager] servidor. Ao salvar suas edições, as alterações são salvas somente no computador local. Ao fazer upload, o ativo é automaticamente marcado e o ícone de bloqueio é removido. Consulte [editar ativos](using.md#edit-assets-upload-updated-assets).

## Ativar ações da área de trabalho na [!DNL Experience Manager] interface da Web {#desktopactions-v2}

Na interface do usuário [!DNL Assets] em um navegador, é possível explorar os locais do ativo ou fazer check-out e abrir o ativo para edição no aplicativo de desktop. Essas opções são chamadas [!UICONTROL Desktop Actions] e não são ativadas por padrão. Para habilitá-lo, siga estas etapas.

1. No console [!DNL Assets], clique no ícone **[!UICONTROL User]** na barra de ferramentas.
1. Clique em **[!UICONTROL My Preferences]** para exibir a caixa de diálogo **[!UICONTROL Preferences]**.

1. Na caixa de diálogo Preferências do usuário, selecione **[!UICONTROL Show Desktop Actions For Assets]**. Clique em **[!UICONTROL Accept]**.


   ![Selecione Mostrar ações da área de trabalho para ativos para ativar ações da área de trabalho](assets/enable_desktop_actions.png)

   *Figura: Selecione  [!UICONTROL Show Desktop Actions For Assets] para ativar as ações da área de trabalho.*

## Procurar, pesquisar e visualizar ativos {#browse-search-preview-assets}

Você pode navegar, procurar e visualizar os ativos disponíveis no repositório [!DNL Experience Manager], tudo isso no aplicativo de desktop. Tente o seguinte no aplicativo:

1. Navegue até uma pasta e veja algumas informações básicas dos ativos disponíveis na pasta, juntamente com pequenas miniaturas de todos os ativos.

   ![Procurar os arquivos e ](assets/browse_folder_da2.png "pastas do DAMNavegue pelos arquivos e pastas do DAM")

1. Para exibir mais informações e uma miniatura maior de um ativo individual, clique no nome do arquivo.

   ![Veja uma visualização maior de um ativo e ](assets/large_preview_actions_da2.png "açõesVeja uma visualização maior de um ativo e de ações")

1. Clique em **[!UICONTROL Open]** ou **[!UICONTROL Edit]** para baixar o arquivo localmente e apenas visualizá-lo ou editá-lo no aplicativo nativo, respectivamente.
1. Pesquise usando palavras-chave para localizar um ativo relacionado no repositório [!DNL Experience Manager]. Use `?` e `*` como curingas. Esses curingas substituem por um único caractere ou por vários caracteres, respectivamente. Filtre e classifique os resultados conforme necessário.

   ![Pesquisa de amostra usando asterisco ](assets/search_wildcard_da2.png "curingaPesquisa de amostra usando asterisco curinga")

   ![Outra pesquisa de amostra usando ](assets/search_wildcard2_da2.png "curinga asteriscoOutra pesquisa de amostra com uma posição diferente do curinga asterisco")

>[!NOTE]
>
>O aplicativo exibe os ativos ao corresponder aos critérios de pesquisa em vários campos de metadados, e não apenas no título do ativo ou no nome do arquivo.

## Baixar ativos {#download-assets}

Você pode baixar os ativos em seu sistema de arquivos local. O aplicativo busca os ativos do servidor [!DNL Experience Manager] e salva a mesma cópia em seu sistema de arquivos local.

Clique em ![Mais opções ícone](assets/do-not-localize/more2_da2.png) para opções e clique em ![Baixar ícone](assets/do-not-localize/download_cloud_da2.png) para baixar.

![Opção de download para uma opção ](assets/download_option_da2.png "assetDownload para um ativo")

>[!NOTE]
>
>Ao baixar ou carregar um arquivo grande ou muitos arquivos, o aplicativo desativa as ações em ativos e pastas. As ações estão disponíveis quando o download ou o upload estiver concluído.

Baixar vários ativos pode resultar em desempenho ruim se o tamanho da fila for grande ou se você enfrentar algum problema de rede. Além disso, você pode colocar na fila, sem saber, muitos ativos para download ao baixar uma pasta. Para evitar longos tempos de espera, o aplicativo restringe o número de ativos baixados de uma só vez. Para saber como configurá-lo, consulte [Definir preferências](install-upgrade.md#set-preferences). Mesmo abaixo desse limite, o aplicativo pode, às vezes, buscar uma confirmação antes de baixar uma pasta aparentemente grande.

![O aplicativo confirma o download de um número relativamente grande de ](assets/download_confirmation_da2.png "ativosO aplicativo confirma o download de um número relativamente grande de ativos")

Se as pastas forem selecionadas e baixadas, o aplicativo baixará apenas os ativos armazenados diretamente nas pastas em [!DNL Experience Manager]. Ele não baixa ativos de subpastas automaticamente.

## Abra ativos no desktop {#openondesktop-v2}

Você pode abrir os ativos remotos para visualização no aplicativo nativo. Os ativos são baixados em uma pasta local e iniciados no aplicativo nativo associado ao formato de arquivo. Você pode alterar o aplicativo nativo para abrir tipos de arquivos específicos (extensões) no Mac ou no Windows.

Clique em **[!UICONTROL Open]** no menu de ativos. O ativo é baixado localmente e aberto no aplicativo nativo. Verifique o progresso do download e a velocidade de transferência de ativos grandes na barra de status.

<!-- ![Download progress bar for large-sized assets](assets/download_status_bar_da2.png "Download progress bar for large-sized assets")
-->

>[!NOTE]
>
>Se as alterações esperadas não forem refletidas no aplicativo, clique no ícone de atualização ![Ícone de atualização](assets/do-not-localize/refresh.png) ou clique com o botão direito do mouse na interface do aplicativo e clique em **[!UICONTROL Refresh]**. As ações não estão disponíveis enquanto downloads ou uploads maiores estiverem em andamento.

Para abrir a pasta de download local de um ativo, clique em ![Mais ações ícone](assets/do-not-localize/more2_da2.png) e clique em ![Revelar ícone](assets/do-not-localize/reveal_action2_da2.png) **[!UICONTROL Reveal File]** ação.

## Usar ou colocar ativos em documentos nativos {#place-assets-in-native-documents}

Em alguns casos, digamos, ao colocar um ativo em um documento nativo, você acessa um arquivo no Windows Explorer ou no Mac Finder. Para chegar ao local do sistema de arquivos do arquivo baixado localmente, use a opção ![Revelar ícone](assets/do-not-localize/reveal_action2_da2.png) **[!UICONTROL Reveal File]** .

![Ação Revelar arquivo para uma ação Arquivo ](assets/revealfile_action_da2.png "assetRevelar para um ativo")

Clique em **[!UICONTROL Reveal File]** ou **[!UICONTROL Reveal Folder]** em uma pasta para abrir o Windows Explorer ou o Mac Finder com o arquivo ou a pasta pré-selecionado no computador local. A opção é útil para, por exemplo, colocar os arquivos [!DNL Experience Manager] nos aplicativos nativos que suportam a inserção ou a vinculação de arquivos locais. Para ver como colocar arquivos no Adobe InDesign, consulte [Colocando gráficos](https://helpx.adobe.com/indesign/using/placing-graphics.html).

A ação **[!UICONTROL Reveal File]** abre um compartilhamento de rede local, que exibe somente os ativos que estão disponíveis localmente, ou seja, exibe ativos que foram revelados, baixados ou abertos/editados usando o aplicativo. O compartilhamento de rede local não carrega nenhuma alteração em [!DNL Experience Manager]. Para fazer upload das alterações, use explicitamente as ações **[!UICONTROL Upload Changes]** ou **[!UICONTROL Upload]** no aplicativo.

>[!NOTE]
>
>Para ter compatibilidade com versões anteriores do [!DNL Experience Manager] aplicativo de desktop v1.x, os arquivos revelados são veiculados a partir de um compartilhamento de rede local, expondo somente os arquivos disponíveis localmente. Os caminhos da área de trabalho dos arquivos revelados são os mesmos caminhos criados pelo aplicativo v1.x.

>[!CAUTION]
>
>Não use a opção **[!UICONTROL Reveal File]** para editar ativos em aplicativos nativos. Em vez disso, use as ações **[!UICONTROL Edit]** . Para saber mais, consulte [Fluxo de trabalho avançado: colabore nos mesmos arquivos e evite conflitos de edição](#adv-workflow-collaborate-avoid-conflicts).

## Edite ativos e faça upload de ativos atualizados para [!DNL Experience Manager] {#edit-assets-upload-updated-assets}

Abra os ativos para editar quando quiser fazer alterações e fazer upload dos ativos atualizados para o servidor AEM Experience Manager. Para evitar conflitos com edições de outros usuários, use o aplicativo para iniciar uma sessão de edição. Antes de começar a editar, verifique se o ativo não tem um ícone de cadeado, ou seja, outro usuário não está editando o ativo.

Para editar um ativo, pesquise pelo ativo ou navegue até o local do ativo. Clique em ![Mais ícone](assets/do-not-localize/more2_da2.png) e clique em **[!UICONTROL Edit]**.

Use **[!UICONTROL Toggle Check-out]** para bloquear o ativo para evitar conflitos com edições de outros usuários em ambas as situações a seguir:

* Você começou a editar um ativo sem verificá-lo primeiro (digamos ao abri-lo).
* Você pretende começar a editar um ativo em breve e não deseja que outros editem.

Quando terminar de fazer as edições, o aplicativo exibe o status **[!UICONTROL Edited Locally]** dos ativos alterados. Todas as alterações salvas nos ativos são somente locais até que você carregue as alterações para [!DNL Experience Manager]. Para fazer upload de um indivíduo ou alguns ativos um por um, clique em **[!UICONTROL Upload Changes]** nas opções de um ativo. Ele cria uma versão do ativo em [!DNL Experience Manager]. Usando a interface da Web de [!DNL Assets], você pode ver o histórico de ativos no [Exibição da linha do tempo](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/activity-stream.html).

![Opção Fazer upload de alterações na opção ](assets/upload_changes_single1_da2.png "appUpload de alterações no aplicativo")

![Fazer upload de alterações , opção ao exibir uma visualização grande de um ](assets/upload_changes_single2_da2.png "ativo. Fazer upload de alterações ao exibir uma visualização grande de um ativo")

Para obter as práticas recomendadas sobre a edição colaborativa, consulte [Fluxo de trabalho avançado: colabore nos mesmos arquivos e evite conflitos de edição](#adv-workflow-collaborate-avoid-conflicts).

Nos casos a seguir, convém descartar as alterações e edições no ativo local. Clique em **[!UICONTROL Discard Changes]**.

* Se não quiser salvar as alterações locais em [!DNL Experience Manager].
* Comece a fazer alterações no ativo original depois de salvar algumas alterações.
* Pare de editar o ativo, pois ele não é mais necessário.

Se necessário, alterne o check-out. O ativo atualizado é removido da pasta de cache local e é baixado novamente ao editá-lo ou abri-lo.

## Faça upload e adicione novos ativos a [!DNL Experience Manager] {#upload-and-add-new-assets-to-aem}

Os usuários podem adicionar novos ativos ao repositório DAM. Por exemplo, você pode ser um fotógrafo ou empreiteiro de agências que deseja adicionar um grande número de fotos de uma sessão fotográfica ao repositório [!DNL Experience Manager]. Para adicionar novo conteúdo a [!DNL Experience Manager], selecione ![opção upload to cloud](assets/do-not-localize/upload_to_cloud_da2.png) na barra superior do aplicativo. Navegue até os arquivos de ativos no sistema de arquivos local e clique em **[!UICONTROL Select]**. Como alternativa, para fazer upload de ativos, arraste os arquivos ou pastas na interface do aplicativo. No Windows, se você arrastar ativos em uma pasta dentro do aplicativo, os ativos serão carregados na pasta.

Se o upload demorar mais para ser carregado, o aplicativo exibirá uma barra de progresso na parte inferior. Não use espaços em branco e caracteres inválidos ao criar ou carregar pastas. Consulte uma lista de caracteres permitidos em [criar pastas em [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders).

<!-- ![Download progress bar for large-sized assets](assets/upload_status_da2.png "Download progress bar for large-sized assets")
-->

Você pode fazer upload de pastas ou arquivos individuais de seu sistema de arquivos local. A hierarquia de uma pasta é preservada quando é carregada. Antes de fazer upload de ativos em massa, consulte [Fazer uploads em massa](#bulk-upload-assets).

Para exibir a lista de ativos transferidos em uma determinada sessão, clique em **[!UICONTROL View]** > **[!UICONTROL Assets transfers]**. A lista permite visualizar e verificar rapidamente as transferências de arquivos da sessão atual.

![Lista de ativos transferidos em uma ](assets/assets_transfered_da2.png "sessão específicaLista de ativos transferidos em uma sessão específica")

Você pode controlar a simultaneidade do upload (aceleração) na configuração **[!UICONTROL Preferences]** > **[!UICONTROL Upload acceleration]** . Geralmente, mais simultaneidade fornece uploads mais rápidos, mas pode consumir recursos e mais poder de processamento da máquina local. Se você tiver um sistema lento, tente fazer uploads novamente usando um valor de simultaneidade menor.

>[!NOTE]
>
>A lista de transferência não é persistente e não está disponível se você sair do aplicativo e reabri-lo.

>[!NOTE]
>
>Se os arquivos não conseguirem fazer upload e se você estiver se conectando a [!DNL Experience Manager] 6.5.1 ou posterior implantação, consulte estas [informações de solução de problemas](troubleshoot.md#upload-fails).

## Trabalhar com vários ativos {#work-with-multiple-assets}

Os usuários podem trabalhar facilmente com vários ativos e gerenciá-los usando ações como carregar todas as edições de uma só vez ou carregar pastas aninhadas em alguns cliques.

### Procurar pastas grandes {#browse-large-folders}

Ao trabalhar com pastas que contêm muitos ativos, role para exibir mais ativos. Para rolar usando o teclado, pressione a tecla tab algumas vezes para selecionar o ativo na parte superior. Observe o ativo destacado para saber quando ele é selecionado. Agora use a tecla de seta para baixo para percorrer a lista de ativos.

### Ações rápidas para ativos selecionados {#quick-actions-for-selected-assets}

Clique na miniatura de alguns ativos para selecionar os ativos. Para selecionar todos os ativos, clique na caixa de seleção na barra superior do aplicativo. O conjunto de ações que são aplicáveis a todos os ativos selecionados coletivamente é exibido em uma barra de ferramentas na parte inferior do aplicativo.

![A barra de ferramentas na parte inferior mostra as ações relevantes para os ](assets/actions_bottom_toolbar1_da2.png "ativos selecionados. A barra de ferramentas na parte inferior mostra as ações comuns para os ativos selecionados")

![Nenhuma ação na barra de ferramentas quando não há ações comuns para a ](assets/actions_bottom_toolbar2_da2.png "seleçãoNenhuma ação na barra de ferramentas quando não há ações comuns para a seleção")

As ações disponíveis na barra de ferramentas na parte inferior dependem do status dos arquivos selecionados. Por exemplo, se selecionar apenas **[!UICONTROL Edited Locally]** arquivos, você verá o ícone **[!UICONTROL Upload Changes]**. Se você selecionar uma combinação de **[!UICONTROL Edited locally]** e **[!UICONTROL Cloud only]**, a ação **[!UICONTROL Upload Changes]** não estará disponível.

### Localizar todas as imagens editadas {#find-all-edited-images}

O aplicativo fornece uma visualização, chamada **[!UICONTROL Edited locally]**, para conceder acesso rápido a todos os arquivos baixados localmente (por meio das ações [!UICONTROL Open] ou [!UICONTROL Edit]) e depois modificados. O aplicativo permite selecionar todos os ativos editados localmente e fazer upload das alterações em alguns cliques. Essa exibição também exibe os ativos editados localmente que têm um conflito de edição.

![Filtre para ver todos os ](assets/edited_locally_filter_da2.png "ativos editados localmenteFiltre para ver todos os ativos editados localmente, digamos para o upload em massa das edições")

### Fazer upload em massa de ativos {#bulk-upload-assets}

Usuários ou organizações, como fotógrafos ou agências criativas, podem criar vários ativos locais em cenários, como fotografias, retoque ou seleção em um conjunto maior feito fora de [!DNL Experience Manager]. Eles podem fazer upload dessas pastas locais grandes para [!DNL Assets] diretamente do aplicativo de desktop. As hierarquias da pasta são preservadas e todas as subpastas aninhadas e os ativos incluídos são carregados. Os ativos carregados também estão imediatamente disponíveis para consumo por outros usuários do mesmo servidor. Os ativos são carregados em segundo plano, de modo que a operação não está vinculada a uma sessão do navegador da Web.

![Faça o upload em massa de várias pastas locais da área de trabalho para o upload em  [!DNL Experience Manager]](assets/upload_local_folders_da2.png "massa de várias pastas locais da área de trabalho no Experience Manager")

Após o upload, se as alterações esperadas não forem refletidas no aplicativo, clique no ícone de atualização ![Atualizar ícone](assets/do-not-localize/refresh.png).

>[!NOTE]
>
>Não use a funcionalidade de upload para migrar ativos entre duas [!DNL Experience Manager] implantações. Em vez disso, consulte o [guia de migração](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html).

### Lista de ativos transferidos {#list-of-transferred-assets}

Para exibir a lista de ativos transferidos em uma determinada sessão, consulte [Fazer upload de ativos para [!DNL Experience Manager]](#upload-and-add-new-assets-to-aem).

## Fluxo de trabalho avançado: inicie a partir da [!DNL Assets] interface da Web {#adv-workflow-start-from-aem-ui}

Se necessário, inicie o fluxo de trabalho pela interface da Web do Assets. O aplicativo de desktop integra-se com o [!DNL Experience Manager] para assumir o controle quando solicitado usando as Ações do desktop.

Um caso especial de início de fluxo de trabalho na interface da Web é a descoberta de ativos. A barra Omnisearch na interface de usuário do Assets oferece uma experiência de pesquisa avançada e avançada. Você pode primeiro localizar um ativo desejado na Web e depois iniciar o fluxo de trabalho no aplicativo, usando [!UICONTROL Desktop Actions]. Alguns casos de exemplo incluem filtrar resultados de pesquisa usando facetas, localizar um ativo específico licenciado pelo Adobe Stock ou uma personalização implementada pela organização que permite uma melhor descoberta na interface da Web.

A funcionalidade do aplicativo de desktop é usada ao tentar as seguintes ações na interface da Web do Assets:

* O [!UICONTROL Desktop Actions] que permite [!UICONTROL Open], [!UICONTROL Edit] e [!UICONTROL Reveal]
* [!UICONTROL Upload folder]
* [!UICONTROL Check-out] ou [!UICONTROL check-in]

Por exemplo, as ações na interface da Web que estão disponíveis para um ativo com check-out no aplicativo são [!UICONTROL Open], [!UICONTROL Reveal] e [!UICONTROL Check-in].

![Ações da área de trabalho na  [!DNL Experience Manager] interface da ](assets/assets_web_actions_da2.png "WebAções da área de trabalho na interface da Web do Experience Manager")

>[!NOTE]
>
>O navegador pode solicitar que você permita a inicialização da área de trabalho [!DNL Adobe Experience Manager]. Para desfrutar de transferência ininterrupta do navegador para o aplicativo, marque a caixa de seleção apropriada para sempre permitir que o aplicativo assuma o controle.

Não é possível encontrar as seguintes informações ou fluxo de trabalho usando a interface da Web. Use o aplicativo de desktop, pois a interface da Web não rastreia as alterações locais e não tem conhecimento do seguinte:

* Arquivos editados localmente.
* Arquivos que têm um conflito de edição e a maneira de resolvê-lo.
* Carregue as alterações locais em [!DNL Experience Manager].
* Vários status dos arquivos disponíveis localmente.

Ao contrário, você pode abrir o ativo na interface da Web, começando pelo aplicativo de desktop usando a ação **[!UICONTROL Open In Web]**.

## Fluxo de trabalho avançado: colabore nos mesmos arquivos e evite conflitos de edição {#adv-workflow-collaborate-avoid-conflicts}

Em ambientes colaborativos, vários usuários podem trabalhar no mesmo conjunto de ativos que pode levar a conflitos de controle de versão. Para evitar conflitos, siga estas práticas recomendadas:

* Não edite ativos ao clicar em [!UICONTROL Open]. Não edite os ativos baixados localmente abrindo da pasta do sistema de arquivos. Outros usuários não sabem que o ativo está sendo editado.
* Para editar um ativo, sempre clique em [!UICONTROL Edit]. Ele abre o ativo no aplicativo nativo e adiciona um ícone de cadeado no ativo, para que os outros usuários saibam que o ativo está sendo editado.
* Clique em [!UICONTROL Toggle Check-in] se você começar a editar acidentalmente sem clicar em [!UICONTROL Edit]. Isso adiciona um ícone de cadeado ao ativo. Mesmo que você planeje editar um ativo posteriormente, mas deseja evitar que outros o editem, clique em [!UICONTROL Toggle Check-in] para bloquear o ativo.
* Antes de editar um ativo, verifique se outros usuários não o estão editando. Procure o ícone de bloqueio no ativo.
* Após concluir as edições, faça upload de todas as alterações e faça check-in do ativo.

![Status de edição de ](assets/edits_conflicts_status_da2.png "conflitosStatus de conflitos de edição")

Se um ativo baixado localmente for atualizado no servidor [!DNL Experience Manager], o aplicativo exibe um status **[!UICONTROL Modified remotely]**. Você pode remover a cópia local ou atualizar a cópia local clicando [!UICONTROL Remove] ou [!UICONTROL Update] respectivamente. Os links na caixa de diálogo permitem exibir ambas as versões do ativo.

![Opções para resolver o conflito quando o ativo for ](assets/modified_remotely_dialog_da2.png "modificado remotamenteOpções para resolver o conflito quando o ativo for modificado remotamente")

Se um ativo que você está editando localmente também for atualizado no servidor sem seu conhecimento, o aplicativo exibirá um status **[!UICONTROL Editing Conflict]**. Você pode reter um conjunto de alterações - ou manter suas atualizações (clique em **[!UICONTROL Keep Mine]**) e excluir a edição do outro usuário ou respeitar as atualizações do outro usuário e excluir o seu (**[!UICONTROL Overwrite Mine]**).

![Opções para resolver um ](assets/editing_conflict_dialog_da2.png "conflito de ediçãoOpções para resolver um conflito de edição")

## Fluxo de trabalho avançado: colocar e vincular ativos no arquivo de InDesign {#adv-workflow-place-assets-indesign}

Quando você usa [!DNL Experience Manager] aplicativo de desktop para abrir arquivos com ativos vinculados, os ativos são baixados previamente e aparecem colocados nos aplicativos nativos. Para que esse fluxo de trabalho funcione, o aplicativo nativo deve oferecer suporte para a inserção de links para ativos locais e [!DNL Experience Manager] deve oferecer suporte para a resolução desses links nos arquivos binários para referências do lado do servidor.

[!DNL Experience Manager] o aplicativo de desktop é compatível com esse fluxo de trabalho com alguns aplicativos de desktop Adobe Creative Cloud e formatos de arquivo selecionados - Adobe InDesign, Adobe Illustrator e Adobe Photoshop. O fluxo de trabalho permite trabalhar com eficiência com os arquivos Creative Cloud suportados. Portanto, se o usuário A colocar alguns ativos em um arquivo de InDesign e fizer o check-in em [!DNL Experience Manager], o usuário B visualizará os ativos no arquivo de InDesign, mesmo que os ativos não façam parte do arquivo. Os ativos são baixados localmente na máquina do usuário B.

>[!NOTE]
>
>O aplicativo de desktop pode mapear para qualquer unidade no Windows. No entanto, para operações suaves, não altere a letra de unidade padrão. Se usuários da mesma organização usarem letras de unidade diferentes, não poderão ver os ativos colocados por outras pessoas. Os ativos inseridos não são buscados conforme o caminho muda. Os ativos colocados continuam sendo colocados no arquivo binário (digamos, INDD) e não são removidos.

Para saber quais são as limitações desse fluxo de trabalho, consulte os [requisitos do sistema e as versões compatíveis](release-notes.md).

Para experimentar este fluxo de trabalho com um ativo e InDesign de imagem, siga estas etapas:

1. Mantenha o controle de um arquivo INDD com ativos colocados em [!DNL Experience Manager]. Para saber como criar um arquivo INDD, consulte [Colocando gráficos](https://helpx.adobe.com/indesign/using/placing-graphics.html).
1. No aplicativo de desktop, **[!UICONTROL Edit]** o arquivo INDD com ativos colocados em [!DNL Experience Manager].
1. O aplicativo baixa ambos, o arquivo InDesign e os ativos vinculados. Quando o InDesign abre o documento, os links são resolvidos, os ativos são baixados e os ativos são exibidos no documento do InDesign.
1. Para colocar um novo gráfico no arquivo de InDesign, use a ação **[!UICONTROL Reveal File]** no ativo. A ação baixa o ativo localmente e abre o local de compartilhamento de rede local no Windows Explorer ou no Mac Finder.
1. Coloque o ativo revelado no documento do InDesign. Isso cria um link no documento.
1. Depois de concluir as edições no documento do InDesign, salve-o e carregue-o em [!DNL Experience Manager] usando o aplicativo de desktop.

## Fluxo de trabalho avançado: baixe os ativos localmente {#adv-workflow-download-assets-locally}

O aplicativo baixa os ativos do [!DNL Experience Manager] servidor localmente em seu sistema de arquivos em vários cenários. Os downloads consomem largura de banda e espaço em disco. Conhecer os cenários ajuda a otimizar o tempo de espera para a conclusão dos downloads.

Baixe os ativos de dentro do aplicativo sob demanda. Consulte [Baixar ativos](#download-assets).

Quando você usa a ação [!UICONTROL Open] para abrir um ativo em um aplicativo de desktop nativo, o ativo é baixado localmente, se ainda não estiver disponível localmente. Consulte [Abrir ativos](#openondesktop-v2).

Ao revelar o local de um ativo ou de uma pasta no aplicativo, o ativo ou a pasta é baixado pela primeira vez localmente e aberto em sua máquina no compartilhamento de rede local. Consulte [Abrir ativos](#openondesktop-v2).

Quando você usa a ação [!UICONTROL Edit] para editar um ativo em um aplicativo de desktop nativo, o ativo é baixado localmente, se ainda não estiver disponível localmente. Consulte [Editar ativos e fazer upload de ativos atualizados para [!DNL Experience Manager]](#edit-assets-upload-updated-assets).

Se o aplicativo estiver instalado e tiver permissão para isso, ele concluirá as ações quando você usar [!UICONTROL Desktop Actions] da interface da Web [!DNL Experience Manager]. O aplicativo baixa o ativo primeiro e, em seguida, conclui a ação.
