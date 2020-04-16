---
title: Instalar e configurar o aplicativo Adobe Experience Manager para desktop
description: Instale e configure o aplicativo de desktop Adobe Experience Manager para trabalhar com os servidores de ativos Adobe Experience Manager e baixe os ativos em seu sistema de arquivos local.
uuid: 79bc9de9-5708-41f9-ac43-68c1fd2a2129
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f6365302-1690-4719-9b8c-035719422740
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 49532b1c5eec497df5b29084675c08f25a15819a

---


# Install Adobe Experience Manager desktop app {#install-app-v2}

Usando o aplicativo Adobe Experience Manager para desktop, os ativos no Experience Manager ficam facilmente disponíveis na área de trabalho local e podem ser usados em quaisquer aplicativos nativos. Os ativos podem ser visualizados, abertos em aplicativos nativos de desktop, revelados no Mac Finder ou no Windows Explorer para serem colocados em outros documentos e alterados localmente - as alterações são salvas no Experience Manager quando você carrega e uma nova versão é criada no repositório.

Tal integração permite que várias funções na organização

* Gerencie os ativos centralmente nos ativos do Experience Manager.
* Acesse os ativos em qualquer aplicativo de desktop nativo, incluindo aplicativos de terceiros e na Adobe Creative Cloud. Ao fazê-lo, os usuários podem facilmente aderir aos vários padrões, incluindo marcas.

Para usar o aplicativo de desktop Experience Manager,

* Certifique-se de que a versão do Experience Manager seja compatível com o aplicativo de desktop Experience Manager. Consulte os requisitos [do](release-notes.md#system-requirements-and-prerequisites-v2) sistema abaixo.
* Baixe e instale o aplicativo. Consulte [instalar o aplicativo](#install-v2) de desktop abaixo.
* Teste a conexão usando alguns ativos. Consulte [como procurar ativos](using.md#browse-search-preview-assets).

## Requisitos do sistema, pré-requisitos e links de download {#tech-specs-v2}

Para obter informações detalhadas, consulte as notas [de versão do aplicativo para desktop do](release-notes.md)Experience Manager.

## Atualizar do app v1.x para o app v2 {#upgrade-from-previous-version}

Se você já for um usuário do aplicativo, entenda as diferenças e as semelhanças entre a versão anterior e a mais recente do aplicativo. Além disso, siga estas diretrizes para transição de v1.x para a versão mais recente.

>[!NOTE]
>
>O aplicativo de desktop v1.x e v2 não podem coexistir em uma máquina. Antes de instalar uma versão, desinstale a outra versão.

Para atualizar da v1.x para a versão mais recente do aplicativo, siga estas instruções:

1. Antes de atualizar, sincronize todos os seus ativos. Carregue todas as alterações usando app v1.x. Isso evita perder quaisquer alterações ao desinstalar o aplicativo v1.x.
1. Desinstale o aplicativo v1.x. Ao desinstalar a v1.x, limpe o cache.
1. Reinicie a máquina.
1. Baixe e instale o aplicativo mais recente. Siga as instruções abaixo.

## Instalar {#install-v2}

Para instalar o aplicativo de desktop, siga estas etapas. Desinstale qualquer aplicativo de desktop Adobe Experience Manager v1.x existente antes de instalar o aplicativo mais recente. Para obter mais informações, consulte acima.

1. Mantenha o URL e as credenciais de sua implantação do Experience Manager acessíveis.
1. Ignore esta etapa se você estiver usando o Experience Manager como um serviço da Cloud, o Experience Manager 6.4.4 ou posterior ou o Experience Manager 6.5.0 ou posterior. Certifique-se de que a configuração do Experience Manager atenda aos requisitos de compatibilidade mencionados nas notas [de](release-notes.md)versão. Se necessário, baixe o pacote [de](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) compatibilidade aplicável e instale-o usando o Experience Manager Package Manager como administrador do Experience Manager. Para instalar um pacote, consulte [Como trabalhar com pacotes](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/package-manager.html).
1. Execute o binário do instalador e siga as instruções na tela para instalar.
1. No Windows, o instalador pode solicitar a instalação `Visual Studio C++ Redistributable 2015`. Siga as instruções na tela para instalá-la. Se a instalação falhar, instale-a manualmente. Baixe o instalador [daqui](https://www.microsoft.com/en-us/download/details.aspx?id=52685) e instale os arquivos `vc_redist.x64.exe` e `vc_redist.x86.exe` arquivos. Execute novamente o instalador do aplicativo para desktop do AEM.
1. Reinicie a máquina, conforme solicitado. Inicie e configure o aplicativo de desktop.
1. Para conectar o aplicativo a um repositório do AEM, clique no ícone do aplicativo na bandeja para iniciar o aplicativo. Forneça o endereço da instância do AEM. Clique em **[!UICONTROL Connect]** e forneça as credenciais.

   ![Tela de conexão do aplicativo desktop ao](assets/connect_da2.png "endereço do servidor de entradaTela de conexão ao endereço do servidor de entrada")

   >[!Cautorização]
   >
   >Verifique se não há espaços à esquerda ou à direita antes ou depois do endereço do servidor AEM. Caso contrário, o aplicativo não poderá se conectar ao servidor AEM.

1. Após uma conexão bem-sucedida, você pode visualização a lista de pastas e ativos disponíveis na pasta raiz do AEM DAM. Você pode navegar pelas pastas dentro do aplicativo.

   ![Após o logon, o aplicativo exibe o](assets/firstview_da2.png "conteúdo do DAM. Após o logon, o aplicativo exibe o conteúdo do DAM")

1. (Experience Manager 6.5.1 ou posterior) Se você estiver usando um aplicativo de desktop com o Experience Manager 6.5.1 ou posterior, atualize o conector S3 ou Azure para a versão 1.10.4 ou posterior. Consulte Conector [do](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/data-store-config.html#AzureDataStore) Azure ou conector [](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/data-store-config.html#AmazonS3DataStore)S3.

   Se você for um cliente do Adobe Managed Services (AMS), entre em contato com o Atendimento ao cliente da Adobe.

## Definir preferências {#set-preferences}

Para alterar as preferências, clique no ícone ![](assets/do-not-localize/more_options_da2.png) Mais opções e no ícone **[!UICONTROL Preference]** ![Preferências](assets/do-not-localize/preferences_icon_da2.png). Na **[!UICONTROL Preferences]** janela, ajuste os valores do seguinte:

* [!UICONTROL Launch application on login].
* [!UICONTROL Show window when application starts].
* **[!UICONTROL Cache Directory]**: Local do cache local do aplicativo (ele contém os ativos baixados localmente).
* **[!UICONTROL Network Drive Letter]**: A letra da unidade usada para mapear para o AEM DAM. Não altere isso se não tiver certeza. O aplicativo pode mapear para qualquer letra de unidade no Windows. Se dois usuários inserirem ativos de letras de unidade diferentes, eles não poderão ver os ativos colocados uns pelos outros. O caminho dos ativos é alterado. Os ativos permanecem colocados no arquivo binário (digamos, INDD) e não são removidos. O aplicativo lista todas as letras de unidade disponíveis e, por padrão, usa a última letra disponível que normalmente é `Z`.
* **[!UICONTROL Maximum Cache Size]**: Cache permitido no disco rígido em GB que é usado para armazenar os ativos baixados localmente.
* **[!UICONTROL Current cache size]**: Tamanho do Armazenamento dos ativos baixados localmente. As informações são exibidas somente depois que os ativos são baixados usando o aplicativo.
* **[!UICONTROL Automatically download linked assets]**: Os ativos colocados nos aplicativos nativos da Creative Cloud suportados são buscados automaticamente se você baixar o arquivo original.
* **[!UICONTROL Maximum number of downloads]**: Ao baixar ativos pela primeira vez (por meio da opção Revelar, Abrir, Editar, Download ou similar), os ativos são baixados somente se o lote contiver menos do que esse número. O valor padrão é 50. Não mude se tiver dúvidas. Aumentar o valor pode levar a tempos de espera mais longos e diminuir o valor pode não permitir que você baixe os ativos ou pastas necessários de uma só vez.
* **[!UICONTROL Upload Acceleration]**: Ao fazer upload de ativos, o aplicativo pode usar uploads simultâneos para melhorar a velocidade de upload. Você pode aumentar a simultaneidade do upload movendo o controle deslizante para a direita. O controle deslizante na extremidade esquerda significa ausência de simultaneidade (carregamento de um único segmento), a posição central corresponde a 10 threads simultâneos e o limite máximo na extremidade direita corresponde a 20 threads simultâneos. Um limite de simultaneidade mais alto requer mais consumo de recursos do processador da máquina local.

Para atualizar as preferências indisponíveis, faça logout do servidor AEM. Depois de atualizar as preferências, clique em ![Salvar preferências](assets/do-not-localize/save_preferences_da2.png) para salvar as alterações.

![Preferências e](assets/preferences_da2.png "configurações do aplicativo para desktop AEM Preferências do aplicativo para desktop")

## Desinstalar o aplicativo {#uninstall-the-app}

Para desinstalar o aplicativo no Windows, siga estas etapas:

1. Carregue todas as alterações no AEM para evitar a perda de edições. Consulte [Editar ativos e fazer upload de ativos atualizados para o AEM](using.md#edit-assets-upload-updated-assets). Faça logoff e [!UICONTROL Exit] o aplicativo.
1. Remova o aplicativo conforme você removeria qualquer outro aplicativo do SO. Desinstale-o de Adicionar e remova programas no Windows.
1. Para remover o cache e os registros, marque a caixa de seleção necessária.
   ![Caixa de diálogo de desinstalação para remover registros e](assets/uninstall_da2.png "cacheCaixa de diálogo de desinstalação para remover registros e cache")
1. Siga as instruções na tela. Quando concluído, reinicie a máquina.

Para desinstalar o aplicativo no Mac, siga estas etapas:

1. Carregue todas as alterações no AEM para evitar a perda de edições. Consulte [Editar ativos e fazer upload de ativos atualizados para o AEM](using.md#edit-assets-upload-updated-assets). Faça logoff e [!UICONTROL Exit] o aplicativo.
1. Remova o `Adobe Experience Manager Desktop.app` de `/Applications`.

Como alternativa, para limpar caches de aplicativos internos no Mac e desinstalar o aplicativo, você pode executar o seguinte comando no terminal:
`/Applications/Adobe Experience Manager Desktop/Contents/Resources/uninstall-osx/uninstall.sh`
