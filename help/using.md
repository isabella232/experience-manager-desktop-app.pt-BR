---
title: Uso [!DNL Experience Manager] aplicativo de desktop
description: Uso [!DNL Adobe Experience Manager] aplicativo de desktop, para trabalhar com [!DNL Adobe Experience Manager] Ativos DAM diretamente do desktop Win ou Mac e uso em outros aplicativos.
mini-toc-levels: 1
feature: Desktop App,Asset Management
exl-id: fa19d819-231a-4a01-bfd2-6bba6fec2f18
source-git-commit: ca04b64e1ebfee4b677fcc5ef84b0e8fd9950d17
workflow-type: tm+mt
source-wordcount: '4054'
ht-degree: 0%

---

# Uso [!DNL Adobe Experience Manager] aplicativo de desktop {#use-aem-desktop-app-v2}

Use o [!DNL Adobe Experience Manager] aplicativo de desktop da para acessar facilmente os ativos digitais armazenados no [!DNL Adobe Experience Manager] Repositório DAM no desktop local e usar esses ativos em qualquer aplicativo de desktop. É possível abrir os ativos em aplicativos de desktop e editá-los localmente; carregue as alterações de volta para [!DNL Experience Manager] com o controle de versão, para compartilhar as atualizações com outros usuários. Também é possível fazer upload de novos arquivos e hierarquias de pastas para [!DNL Experience Manager], criar pastas e excluir ativos ou pastas de [!DNL Experience Manager] DAM.

A integração permite que várias funções na organização gerenciem os ativos de forma central no [!DNL Experience Manager Assets] e para acessar os ativos no desktop local nos aplicativos nativos no sistema operacional Windows ou Mac.

Ao abrir o aplicativo depois de fazer logoff ou pela primeira vez, forneça o URL do [!DNL Experience Manager] servidor no formato `https://[aem-server-url]:[port]/`. Em seguida, selecione o [!UICONTROL Connect] opção. Forneça credenciais para conectar o aplicativo ao servidor.

As principais tarefas que você realizar usando o [!DNL Adobe Experience Manager] aplicativos de desktop são:

![Workflows e tarefas que você pode realizar usando [!DNL Experience Manager] aplicativo de desktop](assets/aem_desktop_app_usecases_v2.png "Workflows e tarefas que você pode realizar usando [!DNL Adobe Experience Manager] aplicativo de desktop")
Baixar [este](assets/aem_desktop_app_usecases_print.pdf) arquivo PDF pronto para impressão.

## Como o aplicativo de desktop funciona {#how-app-works2}

Antes de começar a usar o aplicativo, compreenda [Como o aplicativo funciona](release-notes.md#how-app-works). Além disso, familiarize-se com os seguintes termos:

* **[!UICONTROL Desktop Actions]**: na interface da Web do Assets, em um navegador, você pode explorar os locais dos ativos ou fazer check-out e abrir o ativo para edição no aplicativo de desktop nativo. Essas ações estão disponíveis na interface da Web e usam a funcionalidade do aplicativo de desktop. Consulte [como ativar ações da área de trabalho](using.md#desktopactions-v2).

* O status do arquivo é **[!UICONTROL Cloud Only]**: esses ativos não são baixados no computador local e estão disponíveis em [!DNL Experience Manager] somente servidor.

* O status do arquivo é **[!UICONTROL Available locally]**: os ativos são baixados e disponibilizados no computador local como estão. Os ativos não são alterados.

* O status do arquivo é **[!UICONTROL Edited locally]**: esses ativos são modificados localmente e as alterações permanecem no carregado para [!DNL Experience Manager] servidor. Após o upload, o status muda para [!UICONTROL Available locally]. Consulte [editar ativos](using.md#edit-assets-upload-updated-assets).

* O status do arquivo é **[!UICONTROL Editing conflict]**: se você e outros usuários modificarem um ativo simultaneamente, o aplicativo indicará que um conflito de edição ocorreu. O aplicativo também fornece opções para reter ou descartar suas alterações. Consulte [como evitar conflitos de edição](using.md#adv-workflow-collaborate-avoid-conflicts).

* O status do arquivo é **[!UICONTROL Modified remotely]**: o aplicativo indica se um ativo baixado foi alterado no [!DNL Experience Manager] servidor. O aplicativo também oferece a opção de baixar a versão mais recente e atualizar a cópia local. Consulte [como evitar conflitos de edição](using.md#adv-workflow-collaborate-avoid-conflicts).

* **[!UICONTROL Check-out]**: Se você estiver editando um arquivo ou pretende editar um arquivo, alterne o status para check-out. Ele adiciona um ícone de bloqueio no ativo no aplicativo e [!DNL Experience Manager] Web. O ícone de bloqueio indica a outros usuários que eles devem evitar a edição simultânea do mesmo ativo, pois isso resulta em um conflito de edição.

* **[!UICONTROL Check-in]**: marque o ativo como seguro para que outros usuários editem sem causar um conflito de edição. Ao fazer upload das alterações, o ícone de bloqueio é removido automaticamente. Alternar o status de check-in também remove o ícone de bloqueio, embora seja recomendável não fazer check-in manualmente sem carregar as alterações. Se você descartar as alterações, alterne o check-in manualmente.

* **[!UICONTROL Open]** ação: basta abrir o ativo para visualizá-lo no aplicativo nativo. Não é recomendável editar o ativo usando esta ação, pois ele não faz check-out do ativo e outros usuários podem fazer edições que geram conflitos de edição.

* **[!UICONTROL Edit]** action: use a ação para modificar a imagem. Clicando [!UICONTROL Edit] A ação verifica automaticamente o ativo e adiciona um ícone de bloqueio no ativo. Depois de clicar em Editar, se não quiser editar o ativo, clique em [!UICONTROL Toggle check-in]. Para excluir, renomear ou mover ativos no [!DNL Experience Manager] Hierarquia da pasta DAM, use o [!DNL Experience Manager] ações da interface da web e não a ação de edição.

* **[!UICONTROL Download]** ação: baixe o ativo no computador local. É possível baixar os ativos agora e editar depois; trabalhar offline e fazer upload das alterações posteriormente. Os ativos são baixados em uma pasta de cache no sistema de arquivos.

* **[!UICONTROL Reveal File]** ou **[!UICONTROL Reveal Folder]** ação: enquanto os ativos são baixados para uma pasta de cache local, o aplicativo imita uma unidade de rede local e fornece um caminho local para cada ativo. Para conhecer esse caminho, use a opção de revelação apropriada no aplicativo. É necessária uma ação de revelar para colocar ativos no aplicativo Creative Cloud. Consulte [colocar ativos](using.md#place-assets-in-native-documents).

* **[!UICONTROL Open In Web]** ação: exibir o ativo em [!DNL Experience Manager] interface da Web, abra-a na Web. Você pode iniciar mais workflows em [!DNL Experience Manager] como atualização de metadados ou descoberta de ativos.

* **[!UICONTROL Delete]** ação: exclua o ativo da variável [!DNL Experience Manager] Repositório DAM. A ação exclui a cópia original do ativo no servidor Experience Manager. Se quiser descartar apenas as modificações no ativo local, consulte [descartar alterações](using.md#edit-assets-upload-updated-assets).

* **[!UICONTROL Upload Changes]**: o aplicativo de desktop faz upload do ativo atualizado somente quando você faz upload explicitamente para o [!DNL Experience Manager] servidor. Ao salvar suas edições, as alterações são salvas somente em seu computador local. Ao fazer upload, o ativo é automaticamente enviado para check-in e o ícone de bloqueio é removido. Consulte [editar ativos](using.md#edit-assets-upload-updated-assets).

## Ativar ações do desktop no [!DNL Experience Manager] interface da web {#desktopactions-v2}

De dentro do [!DNL Assets] em um navegador, você pode explorar os locais dos ativos ou fazer check-out e abrir o ativo para edição no aplicativo de desktop. Essas opções são chamadas de [!UICONTROL Desktop Actions] e não estão ativadas por padrão. Para ativá-lo, siga estas etapas.

1. No [!DNL Assets] clique no link **[!UICONTROL User]** ícone na barra de ferramentas.
1. Clique em **[!UICONTROL My Preferences]** para exibir o **[!UICONTROL Preferences]** diálogo.

1. No [!UICONTROL User Preferences] , selecione **[!UICONTROL Show Desktop Actions For Assets]** e, em seguida, clique em **[!UICONTROL Accept]**.


   ![Selecione Mostrar ações da área de trabalho para ativos para habilitar ações da área de trabalho](assets/enable_desktop_actions.png)

   *Figura: Selecionar [!UICONTROL Show Desktop Actions For Assets] para ativar ações no desktop.*

## Procurar, pesquisar e visualizar ativos {#browse-search-preview-assets}

Você pode navegar até os ativos disponíveis na guia, pesquisar por eles e visualizá-los [!DNL Experience Manager] repositório, tudo a partir do aplicativo de desktop. Tente o seguinte no aplicativo:

1. Navegue até uma pasta e veja algumas informações básicas sobre os ativos disponíveis na pasta, juntamente com pequenas miniaturas de todos os ativos.

   ![Procurar arquivos e pastas DAM](assets/browse_folder_da2.png "Procurar arquivos e pastas DAM")

1. Para exibir mais informações e uma miniatura maior de um ativo individual, clique no nome do arquivo.

   ![Ver uma visualização maior de um ativo e ações](assets/large_preview_actions_da2.png "Ver uma visualização maior de um ativo e ações")

1. Clique em **[!UICONTROL Open]** ou **[!UICONTROL Edit]** para baixar o arquivo localmente e apenas exibi-lo ou editá-lo no aplicativo nativo, respectivamente.
1. Pesquisar usando palavras-chave para localizar um ativo relacionado na [!DNL Experience Manager] repositório. Uso `?` e `*` como curingas. Esses curingas substituem um único caractere por vários caracteres, respectivamente. Filtre e classifique os resultados conforme necessário.

   ![Exemplo de pesquisa usando o curinga asterisco](assets/search_wildcard_da2.png "Exemplo de pesquisa usando o curinga asterisco")

   ![Outra pesquisa de amostra usando o curinga asterisco](assets/search_wildcard2_da2.png "Outra pesquisa de amostra com posicionamento diferente do curinga asterisco")

>[!NOTE]
>
>O aplicativo exibe os ativos correspondendo aos critérios de pesquisa em vários campos de metadados e não apenas o título do ativo ou o nome do arquivo.

## Baixar ativos {#download-assets}

Você pode baixar os ativos no sistema de arquivos local. O aplicativo busca os ativos de [!DNL Experience Manager] e salva a mesma cópia no sistema de arquivos local.

Clique em ![Ícone Mais opções](assets/do-not-localize/more2_da2.png) para opções e clique em ![Ícone de download](assets/do-not-localize/download_cloud_da2.png) para baixar.

![Opção de download de um ativo](assets/download_option_da2.png "Opção de download de um ativo")

>[!NOTE]
>
>Ao baixar ou carregar um arquivo grande ou muitos arquivos, o aplicativo desativa as ações nos ativos e pastas. As ações estão disponíveis quando o download ou upload for concluído.

O download de vários ativos pode levar a baixo desempenho se o tamanho da fila for grande ou se você enfrentar algum problema de rede. Além disso, você pode colocar muitos ativos na fila para download sem saber ao baixar uma pasta. Para evitar longos tempos de espera, o aplicativo restringe o número de ativos baixados de uma só vez. Para saber como configurá-lo, consulte [Definir preferências](install-upgrade.md#set-preferences). Mesmo abaixo desse limite, o aplicativo pode às vezes buscar uma confirmação antes de baixar uma pasta aparentemente grande.

![O aplicativo confirma o download de um número relativamente grande de ativos](assets/download_confirmation_da2.png "O aplicativo confirma o download de um número relativamente grande de ativos")

Se as pastas forem selecionadas e baixadas, o aplicativo baixará somente os ativos armazenados diretamente nas pastas no [!DNL Experience Manager]. Ele não baixa ativos de subpastas automaticamente.

## Abrir ativos no desktop {#openondesktop-v2}

É possível abrir os ativos remotos para visualização no aplicativo nativo. Os ativos são baixados para uma pasta local e iniciados no aplicativo nativo associado ao formato de arquivo. Você pode alterar o aplicativo nativo para abrir tipos de arquivos específicos (extensões) no Mac ou no Windows.

Clique em **[!UICONTROL Open]** no menu de ativos. O ativo é baixado localmente e aberto no aplicativo nativo. Verifique o progresso do download e a velocidade de transferência de ativos grandes na barra de status.

<!-- ![Download progress bar for large-sized assets](assets/download_status_bar_da2.png "Download progress bar for large-sized assets")
-->

>[!NOTE]
>
>Se as alterações esperadas não forem refletidas no aplicativo, clique no ícone de atualização ![Ícone Atualizar](assets/do-not-localize/refresh.png) ou clique com o botão direito na interface do aplicativo e clique em **[!UICONTROL Refresh]**. As ações não estão disponíveis enquanto downloads ou uploads maiores estão em andamento.

Para abrir a pasta de download local de um ativo, clique em ![Ícone Mais ações](assets/do-not-localize/more2_da2.png) e clique em ![Ícone Revelar](assets/do-not-localize/reveal_action2_da2.png) **[!UICONTROL Reveal File]** ação.

## Usar ou colocar ativos em documentos nativos {#place-assets-in-native-documents}

Em alguns casos, ao colocar um ativo em um documento nativo, você acessa um arquivo no Windows Explorer ou no Mac Finder. Para chegar ao local do sistema de arquivos do arquivo baixado localmente, use o ![Ícone Revelar](assets/do-not-localize/reveal_action2_da2.png) **[!UICONTROL Reveal File]** opção.

![Revelar ação de arquivo para um ativo](assets/revealfile_action_da2.png "Revelar ação de arquivo para um ativo")

Clique em **[!UICONTROL Reveal File]** ou **[!UICONTROL Reveal Folder]** em uma pasta, para abrir o Windows Explorer ou o Mac Finder com o arquivo ou pasta pré-selecionado no computador local. A opção é útil para, digamos, colocar o [!DNL Experience Manager] arquivos nos aplicativos nativos que oferecem suporte à inserção ou vinculação de arquivos locais. Para ver como colocar arquivos no Adobe InDesign, consulte [Inserção de gráficos](https://helpx.adobe.com/indesign/using/placing-graphics.html).

A variável **[!UICONTROL Reveal File]** a ação abre um compartilhamento de rede local, que exibe somente os ativos que estão disponíveis localmente, ou seja, exibe ativos que foram revelados, baixados ou abertos/editados usando o aplicativo. O compartilhamento de rede local não carrega nenhuma alteração no [!DNL Experience Manager]. Para fazer upload das alterações, use **[!UICONTROL Upload Changes]** ou **[!UICONTROL Upload]** ações no aplicativo.

>[!NOTE]
>
>Para compatibilidade com versões anteriores do [!DNL Experience Manager] aplicativo de desktop v1.x, os arquivos revelados são veiculados a partir de um compartilhamento de rede local, expondo apenas arquivos disponíveis localmente. Os caminhos da área de trabalho dos arquivos revelados são os mesmos caminhos criados pelo aplicativo v1.x.

>[!CAUTION]
>
>Não usar **[!UICONTROL Reveal File]** opção para editar ativos em aplicativos nativos. Use o botão **[!UICONTROL Edit]** ações. Para saber mais, consulte [Fluxo de trabalho avançado: colabore nos mesmos arquivos e evite conflitos de edição](#adv-workflow-collaborate-avoid-conflicts).

## Editar ativos e carregar ativos atualizados para [!DNL Experience Manager] {#edit-assets-upload-updated-assets}

Abra ativos para edição quando quiser fazer alterações e faça upload dos ativos atualizados para o servidor do Experience ManagerEM. Para evitar conflitos com as edições de outros usuários, use o aplicativo para iniciar uma sessão de edição. Antes de começar a editar, verifique se o ativo não tem um ícone de bloqueio, ou seja, se outro usuário não está editando o ativo.

Para editar um ativo, pesquise pelo ativo ou navegue até o local do ativo. Clique em ![Ícone Mais](assets/do-not-localize/more2_da2.png) e clique em **[!UICONTROL Edit]**.

Uso **[!UICONTROL Toggle Check-out]** bloquear o ativo para evitar conflitos com edições de outros usuários nas seguintes situações:

* Você começou a editar um ativo sem fazer o check-out dele primeiro (digamos apenas abrindo-o).
* Você pretende começar a editar um ativo em breve e não deseja que outros editem.

Quando terminar de fazer as edições, o aplicativo exibirá a **[!UICONTROL Edited Locally]** status dos ativos alterados. Todas as alterações salvas nos ativos são somente locais até que você faça upload das alterações no [!DNL Experience Manager]. Para fazer upload de um indivíduo ou de alguns ativos individualmente, clique em **[!UICONTROL Upload Changes]** nas opções de um ativo. Ele cria uma versão do ativo no [!DNL Experience Manager]. Usar a interface da Web do [!DNL Assets], é possível ver o histórico do ativo no [Exibição da linha do tempo](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/activity-stream.html).

![Opção Fazer upload de alterações no aplicativo](assets/upload_changes_single1_da2.png "Opção Fazer upload de alterações no aplicativo")

![Opção Fazer upload de alterações ao visualizar uma grande visualização de um ativo](assets/upload_changes_single2_da2.png "Opção Fazer upload de alterações ao visualizar uma grande visualização de um ativo")

Para obter as práticas recomendadas sobre edição colaborativa, consulte [Fluxo de trabalho avançado: colabore nos mesmos arquivos e evite conflitos de edição](#adv-workflow-collaborate-avoid-conflicts).

Nos casos a seguir, talvez você queira descartar as alterações e edições no ativo local. Clique em **[!UICONTROL Discard Changes]**.

* Se não quiser salvar suas alterações locais no [!DNL Experience Manager].
* Comece a fazer alterações no ativo original depois de salvar algumas alterações.
* Pare de editar o ativo, pois ele não é mais necessário.

Se necessário, alterne o check-out. O ativo atualizado é removido da pasta de cache local e é baixado novamente quando você o edita ou abre.

## Fazer upload e adicionar novos ativos a [!DNL Experience Manager] {#upload-and-add-new-assets-to-aem}

Os usuários podem adicionar novos ativos ao repositório DAM. Por exemplo, você pode ser um fotógrafo ou um empreiteiro de uma agência que deseja adicionar um grande número de fotos de uma sessão de fotos à [!DNL Experience Manager] repositório. Para adicionar novo conteúdo a [!DNL Experience Manager], selecione ![opção carregar na nuvem](assets/do-not-localize/upload_to_cloud_da2.png) na barra superior do aplicativo. Navegue até os arquivos de ativos no sistema de arquivos local e clique em **[!UICONTROL Select]**. Como alternativa, para fazer upload de ativos, arraste os arquivos ou as pastas para a interface do aplicativo. No Windows, se você arrastar ativos em uma pasta dentro do aplicativo, os ativos serão carregados na pasta. Se demorar mais para carregar, o aplicativo exibe uma barra de progresso.

<!-- ![Download progress bar for large-sized assets](assets/upload_status_da2.png "Download progress bar for large-sized assets")
-->

Você pode fazer upload de pastas ou arquivos individuais do seu sistema de arquivos local. A hierarquia de uma pasta é preservada ao ser carregada. Antes de fazer upload de ativos em massa, consulte [Uploads em massa](#bulk-upload-assets).

Para exibir a lista de ativos transferidos em uma determinada sessão, clique em **[!UICONTROL View]** > **[!UICONTROL Assets transfers]**. A lista permite visualizar e verificar rapidamente as transferências de arquivos da sessão atual.

![Lista de ativos transferidos em uma sessão específica](assets/assets_transfered_da2.png "Lista de ativos transferidos em uma sessão específica")

Você pode controlar a simultaneidade de upload (aceleração) no **[!UICONTROL Preferences]** > **[!UICONTROL Upload acceleration]** configuração. Em geral, mais simultaneidade resulta em uploads mais rápidos, mas pode consumir muitos recursos, consumindo mais potência de processamento da máquina local. Se o sistema for lento, tente fazer upload novamente usando um valor de simultaneidade menor.

>[!NOTE]
>
>A lista de transferência não é persistente e não estará disponível se você sair do aplicativo e reabri-la.

### Gerenciar caracteres especiais nos nomes de ativos {#special-characters-in-filename}

No aplicativo herdado, os nomes de nó criados no repositório mantiveram os espaços e os caracteres maiúsculos e minúsculos dos nomes de pasta fornecidos pelo usuário. Para que o aplicativo atual emule as regras de nomenclatura de nó do aplicativo v1.10, habilite [!UICONTROL Use legacy conventions when creating nodes for assets and folders] no [!UICONTROL Preferences]. Consulte [preferências do aplicativo](/help/install-upgrade.md#set-preferences). Esta preferência de legado está desativada por padrão.

>[!NOTE]
>
>O aplicativo altera apenas os nomes dos nós no repositório usando as seguintes convenções de nomenclatura. O aplicativo retém o `Title` do ativo como está.

<!-- TBD: Do NOT use this table.

| Where do characters occur | Characters | Legacy preference | Renaming convention | Example |
|---|---|---|---|---|
| In file name extension | `.` | Enabled or disabled | Retained as is | NA |
| File or folder name | `. / : [ ] | *` | Enabled or disabled | Replaced with a `-` (hyphen) | `myimage.jpg` remains as is and `my.image.jpg` changes to `my-image.jpg`. |
| Folder name | `% ; # , + ? ^ { } "` | Disabled | Replaced with a `-` (hyphen) | tbd |
| File name | `% # ? { } &` | Disabled | Replaced with a `-` (hyphen) | tbd |
| File name | Whitespaces | Enabled or disabled | Retained as is | NA |
| Folder name | Whitespaces | Disabled | Replaced with a `-` (hyphen) | tbd |
| File name | Uppercase characters | Disabled | Retained as is | tbd |
| Folder name | Uppercase characters | Disabled | Replaced with a `-` (hyphen) | tbd |
-->

| Caracteres ‡ | Preferência Herdada no aplicativo | Quando ocorrer em nomes de arquivo | Quando ocorrer em nomes de pasta | Exemplo |
|---|---|---|---|---|
| `. / : [ ] | *` | Ativado ou desativado | Substituído por `-` (hífen). A `.` (ponto) na extensão de nome de arquivo é retido como está. | Substituído por `-` (hífen). | `myimage.jpg` permanece como está e `my.image.jpg` alterações em `my-image.jpg`. |
| `% ; # , + ? ^ { } "` e espaços em branco | ![ícone de desmarcar](assets/do-not-localize/deselect-icon.png) Desabilitado | Os espaços em branco são retidos | Substituído por `-` (hífen). | `My Folder.` alterações em `my-folder-`. |
| `# % { } ? & .` | ![ícone de desmarcar](assets/do-not-localize/deselect-icon.png) Desabilitado | Substituído por `-` (hífen). | ND. | `#My New File.` alterações em `-My New File-`. |
| Caracteres em maiúsculas | ![ícone de desmarcar](assets/do-not-localize/deselect-icon.png) Desabilitado | A caixa é retida como está. | Alterado para caracteres em minúsculas. | `My New Folder` alterações em `my-new-folder`. |
| Caracteres em maiúsculas | ![ícone seleção verificada](assets/do-not-localize/selection-checked-icon.png) Ativado | A caixa é retida como está. | A caixa é retida como está. | ND. |

‡ A lista de caracteres é uma lista separada por espaços em branco.

<!-- TBD: Check if the following is to be included in the footnote.

Do not use &#92;&#92; in the names of files and &#92;&#116; &#38; in the names of folders. 
-->


<!-- TBD: Securing the below presentation of the same content in a comment.

**File names**

| Characters | Replaced by |
|---|---|
| &#35; &#37; &#123; &#63; &#125; &#38; &#46; &#47; &#58; &#91; &#124; &#93; &#42; | hyphen (-) |
| whitespaces | whitespaces are retained |
| capital case | casing is retained |

>[!CAUTION]
>
>Avoid using &#92;&#92; in file names.

**Folder names**

| Characters | Replaced by |
|---|---|
| Characters | Replaced by |
| &#37; &#59; &#35; &#44; &#43; &#63; &#94; &#123; &#123; &#34; &#46; &#47; &#59; &#91; &#93; &#124; &#42; | hyphen (-) |
| whitespaces | hyphen (-) |
| capital case | lower case |

>[!CAUTION]
>
>Avoid using &#92;&#92; &#92;&#116; &#38; in folder names.

>[!NOTE]
>
>If you enable [!UICONTROL Use legacy conventions when creating nodes for assets and folders] in app [!UICONTROL Preferences], then the app emulates v1.10 app behavior when uploading folders. In v1.10, the node names created in the repository respect spaces and casing of the folder names provided by the user. For more information, see [app Preferences](/help/install-upgrade.md#set-preferences).

-->

## Trabalhar com vários ativos {#work-with-multiple-assets}

Os usuários podem trabalhar com facilidade e gerenciar vários ativos usando ações como fazer upload de todas as edições de uma só vez ou fazer upload de pastas aninhadas com apenas alguns cliques.

### Procurar pastas grandes {#browse-large-folders}

Ao trabalhar com pastas que contêm muitos ativos, role a tela para exibir mais ativos. Para rolar usando o teclado, pressione a tecla de tabulação algumas vezes para selecionar o ativo na parte superior. Observe o ativo destacado para saber quando está selecionado. Agora use a tecla de seta para baixo para percorrer a lista de ativos.

### Ações rápidas para ativos selecionados {#quick-actions-for-selected-assets}

Clique na miniatura de alguns ativos para selecioná-los. Para selecionar todos os ativos, clique na caixa de seleção na barra superior do aplicativo. O conjunto de ações aplicáveis a todos os ativos selecionados coletivamente é exibido em uma barra de ferramentas na parte inferior do aplicativo.

![A barra de ferramentas na parte inferior mostra as ações relevantes para os ativos selecionados](assets/actions_bottom_toolbar1_da2.png "A barra de ferramentas na parte inferior mostra ações comuns para os ativos selecionados")

![Nenhuma ação na barra de ferramentas quando não há ações comuns para a seleção](assets/actions_bottom_toolbar2_da2.png "Nenhuma ação na barra de ferramentas quando não há ações comuns para a seleção")

As ações disponíveis na barra de ferramentas na parte inferior dependem do status dos arquivos selecionados. Por exemplo, se você selecionar apenas **[!UICONTROL Edited Locally]** arquivos, você verá **[!UICONTROL Upload Changes]** ícone. Se você selecionar uma combinação de **[!UICONTROL Edited locally]** e **[!UICONTROL Cloud only]**, o **[!UICONTROL Upload Changes]** ação não disponível.

### Localizar todas as imagens editadas {#find-all-edited-images}

O aplicativo fornece uma visualização, chamada **[!UICONTROL Edited locally]**, para fornecer acesso rápido a todos os arquivos baixados localmente (via [!UICONTROL Open] ou [!UICONTROL Edit] ações) e depois modificado. O aplicativo permite selecionar todos os ativos editados localmente e fazer upload das alterações com apenas alguns cliques. Essa exibição também mostra os ativos editados localmente que têm um conflito de edição.

![Filtrar para ver todos os ativos editados localmente](assets/edited_locally_filter_da2.png "Filtrar para ver todos os ativos editados localmente, por exemplo, para o upload em massa de edições")

### Fazer upload de ativos em massa {#bulk-upload-assets}

Os usuários ou a organização, como fotógrafos ou agências de criação, podem criar vários ativos locais em cenários, como sessões de fotos, retoque ou seleção de um conjunto maior feito externamente [!DNL Experience Manager]. Eles podem fazer upload dessas pastas locais grandes para [!DNL Assets] diretamente do aplicativo de desktop. As hierarquias de pastas são preservadas e todas as subpastas aninhadas e os ativos incluídos são carregados. Os ativos carregados também ficam disponíveis imediatamente para outros usuários do mesmo servidor para consumo. Os ativos são carregados em segundo plano, portanto, a operação não é vinculada a uma sessão do navegador da Web.

![Fazer upload em massa de várias pastas locais do desktop para o [!DNL Experience Manager]](assets/upload_local_folders_da2.png "Fazer upload em massa de várias pastas locais do seu desktop para o Experience Manager")

Após o upload, se as alterações esperadas não forem refletidas no aplicativo, clique no ícone de atualização ![Ícone Atualizar](assets/do-not-localize/refresh.png).

>[!NOTE]
>
>Não use a funcionalidade de upload para migrar ativos entre dois [!DNL Experience Manager] implantações. Em vez disso, consulte a [guia de migração](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html).

### Lista de ativos transferidos {#list-of-transferred-assets}

Para exibir a lista de ativos transferidos em uma determinada sessão, consulte [Fazer upload de ativos para [!DNL Experience Manager]](#upload-and-add-new-assets-to-aem).

## Fluxo de trabalho avançado: comece no [!DNL Assets] interface da web {#adv-workflow-start-from-aem-ui}

Se necessário, inicie o fluxo de trabalho na interface da Web do Assets. O aplicativo de desktop integra-se com o [!DNL Experience Manager] quando solicitado usando as ações da área de trabalho.

Um caso especial de iniciar o fluxo de trabalho a partir da interface da Web é a descoberta de ativos. A barra Omnisearch na interface do Assets oferece uma experiência de pesquisa avançada. Talvez você queira localizar um ativo desejado na Web e iniciar o fluxo de trabalho no aplicativo, usando [!UICONTROL Desktop Actions]. Alguns casos de amostra incluem filtrar resultados de pesquisa usando facetas, localizar um ativo específico licenciado da Adobe Stock ou uma personalização implementada pela organização que permite uma melhor descoberta na interface da Web.

A funcionalidade do aplicativo de desktop é usada quando você tenta as seguintes ações na interface da Web do Assets:

* A variável [!UICONTROL Desktop Actions] que permite [!UICONTROL Open], [!UICONTROL Edit], e [!UICONTROL Reveal]
* [!UICONTROL Upload folder]
* [!UICONTROL Check-out] ou [!UICONTROL check-in]

Por exemplo, as ações na interface da Web disponíveis para um ativo que está com check-out no aplicativo são [!UICONTROL Open], [!UICONTROL Reveal], e [!UICONTROL Check-in].

![Ações da área de trabalho no [!DNL Experience Manager] interface da web](assets/assets_web_actions_da2.png "Ações do desktop na interface da Web do Experience Manager")

>[!NOTE]
>
>O navegador pode solicitar que você autorize a inicialização de [!DNL Adobe Experience Manager] Área de trabalho. Para desfrutar de transferência ininterrupta do navegador para o aplicativo, marque a caixa de seleção apropriada para sempre permitir que o aplicativo assuma o controle.

Não é possível localizar as informações ou o fluxo de trabalho a seguir usando a interface da Web. Use o aplicativo de desktop, pois a interface da Web não rastreia alterações locais e não tem conhecimento do seguinte:

* Arquivos editados localmente.
* Arquivos que têm um conflito de edição e uma maneira de resolvê-lo.
* Fazer upload de alterações locais em [!DNL Experience Manager].
* Vários status dos arquivos disponíveis localmente.

Ao contrário, é possível abrir o ativo na interface da Web a partir do aplicativo de desktop usando o **[!UICONTROL Open In Web]** ação.

## Fluxo de trabalho avançado: colabore nos mesmos arquivos e evite conflitos de edição {#adv-workflow-collaborate-avoid-conflicts}

Em ambientes colaborativos, vários usuários podem trabalhar no mesmo conjunto de ativos que podem levar a conflitos de versão. Para evitar conflitos, siga estas práticas recomendadas:

* Não edite nenhum ativo clicando em [!UICONTROL Open]. Não edite os ativos baixados localmente abrindo na pasta do sistema de arquivos. Outros usuários não sabem que o ativo está sendo editado.
* Para editar um ativo, sempre clique em [!UICONTROL Edit]. Ele abre o ativo no aplicativo nativo e adiciona um ícone de bloqueio no ativo para que os outros usuários saibam que o ativo está sendo editado.
* Clique em [!UICONTROL Toggle Check-in] se você começar a editar acidentalmente sem clicar [!UICONTROL Edit]. Isso adiciona um ícone de bloqueio ao ativo. Mesmo que planeje editar um ativo posteriormente, mas não queira que outras pessoas o editem, clique em [!UICONTROL Toggle Check-in] para bloquear o ativo.
* Antes de editar um ativo, verifique se outros usuários não o estão editando. Procure o ícone de bloqueio no ativo.
* Após concluir as edições, faça upload de todas as alterações e faça check-in do ativo.

![Status de conflitos de edição](assets/edits_conflicts_status_da2.png "Status de conflitos de edição")

Se um ativo baixado localmente for atualizado no [!DNL Experience Manager] servidor, o aplicativo exibe uma **[!UICONTROL Modified remotely]** status. Você pode remover a cópia local ou renová-la clicando em [!UICONTROL Remove] ou [!UICONTROL Update] respectivamente. Os links na caixa de diálogo permitem exibir ambas as versões do ativo.

![Opções para resolver o conflito quando o ativo for modificado remotamente](assets/modified_remotely_dialog_da2.png "Opções para resolver o conflito quando o ativo for modificado remotamente")

Se um ativo que você está editando localmente também for atualizado no servidor sem seu conhecimento, o aplicativo exibirá um **[!UICONTROL Editing Conflict]** status. Você pode reter um conjunto de alterações: mantenha suas atualizações (clique em **[!UICONTROL Keep Mine]**) e excluir a do outro usuário ou editar ou respeitar as atualizações do outro usuário e excluir a sua (**[!UICONTROL Overwrite Mine]**).

![Opções para resolver um conflito de edição](assets/editing_conflict_dialog_da2.png "Opções para resolver um conflito de edição")

## Fluxo de trabalho avançado: colocar e vincular ativos no arquivo do InDesign {#adv-workflow-place-assets-indesign}

Quando você usa [!DNL Experience Manager] aplicativo de desktop para abrir arquivos com ativos vinculados, os ativos são pré-baixados e aparecem colocados nos aplicativos nativos. Para que esse fluxo de trabalho funcione, seu aplicativo nativo deve oferecer suporte à inserção de links para ativos locais e [!DNL Experience Manager] O deve aceitar a resolução desses links nos arquivos binários para referências do lado do servidor.

[!DNL Experience Manager] o aplicativo de desktop é compatível com esse fluxo de trabalho com alguns aplicativos de desktop e formatos de arquivo selecionados do Adobe Creative Cloud - Adobe InDesign, Adobe Illustrator e Adobe Photoshop. O fluxo de trabalho permite trabalhar com eficiência com os arquivos de Creative Cloud compatíveis. Portanto, se o usuário A colocar alguns ativos em um arquivo do InDesign e fizer o check-in dele [!DNL Experience Manager]No entanto, o usuário B vê os ativos no arquivo do InDesign mesmo que os ativos não façam parte do arquivo. Os ativos são baixados localmente no computador do usuário B.

>[!NOTE]
>
>O aplicativo de desktop pode ser mapeado para qualquer unidade no Windows. No entanto, para operações suaves, não altere a letra da unidade padrão. Se os usuários da mesma organização usarem letras de unidade diferentes, eles não poderão ver os ativos colocados por outros. Os ativos colocados não são buscados conforme o caminho muda. Os ativos colocados continuam a ser colocados no arquivo binário (digamos, INDD) e não são removidos.

Para conhecer as limitações desse workflow, consulte a [requisitos de sistema e versões compatíveis](release-notes.md).

Para experimentar esse fluxo de trabalho com um ativo de imagem e um InDesign, siga estas etapas:

1. Mantenha disponível um arquivo INDD com ativos colocados em [!DNL Experience Manager]. Para saber como criar esse arquivo INDD, consulte [Inserção de gráficos](https://helpx.adobe.com/indesign/using/placing-graphics.html).
1. No aplicativo de desktop, **[!UICONTROL Edit]** o arquivo INDD com ativos colocados em [!DNL Experience Manager].
1. O aplicativo baixa o arquivo InDesign e os ativos vinculados. Quando o InDesign abre o documento, os links são resolvidos, os ativos são baixados e os ativos são exibidos no documento do InDesign.
1. Para inserir um novo gráfico no arquivo de InDesign, use **[!UICONTROL Reveal File]** ação no ativo. A ação baixa o ativo localmente e abre o local de compartilhamento de rede local no Windows Explorer ou no Mac Finder.
1. Inserir o ativo revelado no documento do InDesign. Isso cria um link no documento.
1. Depois de concluir suas edições no documento do InDesign, salve-o e faça upload para [!DNL Experience Manager] usando o aplicativo de desktop.

## Fluxo de trabalho avançado: baixar os ativos localmente {#adv-workflow-download-assets-locally}

O aplicativo baixa os ativos de [!DNL Experience Manager] localmente em seu sistema de arquivos em vários cenários. Os downloads consomem largura de banda e espaço em disco. Conhecer os cenários ajuda a otimizar o tempo de espera até que os downloads sejam concluídos.

Baixe os ativos no aplicativo sob demanda. Consulte [Baixar ativos](#download-assets).

Quando você usa o [!UICONTROL Open] ação para abrir um ativo em um aplicativo de desktop nativo, o ativo é baixado localmente se ainda não estiver disponível localmente. Consulte [Abrir ativos](#openondesktop-v2).

Quando você revela o local de um ativo ou de uma pasta no aplicativo, primeiro o ativo ou a pasta é baixada localmente e depois aberta no computador no compartilhamento de rede local. Consulte [Abrir ativos](#openondesktop-v2).

Quando você usa o [!UICONTROL Edit] ação para editar um ativo em um aplicativo de desktop nativo, o ativo é baixado localmente se ainda não estiver disponível localmente. Consulte [Editar ativos e carregar ativos atualizados para [!DNL Experience Manager]](#edit-assets-upload-updated-assets).

Se o aplicativo estiver instalado e tiver permissão para, ele concluirá as ações quando você usar [!UICONTROL Desktop Actions] de [!DNL Experience Manager] Web. O aplicativo baixa o ativo primeiro e depois conclui a ação.
