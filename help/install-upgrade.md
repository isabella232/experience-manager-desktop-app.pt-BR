---
title: Instalar e configurar o aplicativo Adobe Experience Manager desktop
description: Instale e configure o aplicativo Adobe Experience Manager desktop para trabalhar com os servidores Adobe Experience Manager Assets e baixe os ativos no sistema de arquivos local.
uuid: 79bc9de9-5708-41f9-ac43-68c1fd2a2129
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f6365302-1690-4719-9b8c-035719422740
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a6f33efdd5702cc2f411d0deed8f54e7335c09ed
workflow-type: tm+mt
source-wordcount: '1238'
ht-degree: 1%

---


# Install Adobe Experience Manager desktop app {#install-app-v2}

Usando o aplicativo Adobe Experience Manager para desktop, os recursos no Experience Manager são facilmente disponíveis em seu desktop local e podem ser usados em qualquer aplicativo nativo de desktop. Os ativos podem ser visualizados, abertos em aplicativos nativos da área de trabalho, revelados no Mac Finder ou no Windows Explorer para serem colocados em outros documentos e alterados localmente - as alterações são salvas no Experience Manager quando você carrega e uma nova versão é criada no repositório.

Tal integração permite que várias funções na organização

* Gerencie os ativos centralmente nos ativos Experience Manager.

* Acesse os ativos em qualquer aplicativo de desktop nativo, incluindo aplicativos de terceiros e no Adobe Creative Cloud. Ao fazê-lo, os usuários podem facilmente aderir aos vários padrões, incluindo marcas.

Para usar o aplicativo de desktop Experience Manager,

* Certifique-se de que sua versão do Experience Manager seja suportada pelo aplicativo de desktop Experience Manager. Consulte os requisitos [do](release-notes.md#system-requirements-and-prerequisites-v2) sistema abaixo.

* Baixe e instale o aplicativo. Consulte [instalar o aplicativo](#install-v2) de desktop abaixo.

* Teste a conexão usando alguns ativos. Consulte [como procurar ativos](using.md#browse-search-preview-assets).

## Requisitos do sistema, pré-requisitos e links de download {#tech-specs-v2}

Para obter informações detalhadas, consulte as notas [de versão do aplicativo para desktop](release-notes.md)Experience Manager.

## Upgrade from a previous version {#upgrade-from-previous-version}

Se você for um usuário da versão 1.x do aplicativo para desktop, entenda as diferenças e as semelhanças entre a versão anterior e a versão mais recente do aplicativo. Veja [as novidades no aplicativo](introduction.md#whats-new-v2) para desktop e [como o aplicativo funciona](release-notes.md#how-app-works)

>[!NOTE]
>
>Duas versões do aplicativo desktop não podem coexistir em uma máquina. Antes de instalar uma versão, desinstale a outra versão.

Para atualizar de uma versão anterior do aplicativo, siga estas instruções:

1. Antes de atualizar, sincronize todos os ativos e carregue as alterações no Experience Manager. Isso evita perder edições ao desinstalar o aplicativo.

1. Desinstale a versão anterior do aplicativo. Ao desinstalar, selecione a opção para limpar o cache.

1. Reinicie a máquina.

1. [Baixe](release-notes.md) e [instale](#install-v2) o aplicativo mais recente. Siga as instruções abaixo.

## Instalar {#install-v2}

Para instalar o aplicativo de desktop, siga estas etapas. Desinstale qualquer aplicativo de desktop Adobe Experience Manager v1.x existente antes de instalar o aplicativo mais recente. Para obter mais informações, consulte acima.

1. Baixe o instalador mais recente da página de notas [de](release-notes.md) versão.

1. Mantenha o URL e as credenciais da sua implementação de Experience Manager.

1. Se você estiver atualizando de outra versão do aplicativo, consulte [atualizar o aplicativo](#upgrade-from-previous-version)para desktop.

1. Ignore esta etapa se estiver usando Experience Manager como Cloud Service, Experience Manager 6.4.4 ou posterior ou Experience Manager 6.5.0 ou posterior. Certifique-se de que a configuração do Experience Manager atende aos requisitos de compatibilidade mencionados nas notas [de](release-notes.md)versão. Se necessário, baixe o pacote [de](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) compatibilidade aplicável e instale-o usando o Gerenciador de pacotes de Experience Manager como administrador de Experience Manager. Para instalar um pacote, consulte [Como trabalhar com pacotes](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html).

1. Execute o binário do instalador e siga as instruções na tela para instalar.

1. No Windows, o instalador pode solicitar a instalação `Visual Studio C++ Redistributable 2015`. Siga as instruções na tela para instalá-la. Se a instalação falhar, instale-a manualmente. Baixe o instalador [daqui](https://www.microsoft.com/en-us/download/details.aspx?id=52685) e instale os arquivos `vc_redist.x64.exe` e `vc_redist.x86.exe` arquivos. Execute novamente o instalador do aplicativo AEM desktop.

1. Reinicie a máquina, conforme solicitado. Inicie e configure o aplicativo de desktop.

1. Para conectar o aplicativo a um repositório AEM, clique no ícone do aplicativo na bandeja para iniciar o aplicativo. Forneça o endereço da instância AEM. Clique em **[!UICONTROL Connect]** e forneça as credenciais.

   ![Tela de conexão do aplicativo desktop ao endereço do servidor de entrada](assets/connect_da2.png)

   *Figura: Tela de conexão com o endereço do servidor de entrada*

   >[!CAUTION]
   >
   >Verifique se não há espaços à esquerda ou à direita antes ou depois do endereço do servidor AEM. Caso contrário, o aplicativo não poderá se conectar ao servidor AEM.

1. Após uma conexão bem-sucedida, você pode visualização a lista de pastas e ativos disponíveis na pasta raiz do DAM AEM. Você pode navegar pelas pastas dentro do aplicativo.

   ![Após o logon, o aplicativo exibe o conteúdo do DAM](assets/firstview_da2.png)

   *Figura: O aplicativo exibe o conteúdo do DAM após o logon*

1. (Experience Manager 6.5.1 ou posterior) Se você estiver usando um aplicativo desktop com o Experience Manager 6.5.1 ou posterior, atualize o conector S3 ou Azure para a versão 1.10.4 ou posterior. Consulte Conector [do](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/data-store-config.html#AzureDataStore) Azure ou conector [](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/data-store-config.html#AmazonS3DataStore)S3.

   Se você for um cliente do Adobe Managed Services (AMS), entre em contato com o Atendimento ao cliente da Adobe.

## Definir preferências {#set-preferences}

Para alterar as preferências, clique no ícone ![](assets/do-not-localize/more_options_da2.png) Mais opções e no ícone **[!UICONTROL Preference]** ![Preferências](assets/do-not-localize/preferences_icon_da2.png). Na **[!UICONTROL Preferences]** janela, ajuste os valores do seguinte:

* [!UICONTROL Launch application on login].

* [!UICONTROL Show window when application starts].

* **[!UICONTROL Cache Directory]**: Local do cache local do aplicativo (ele contém os ativos baixados localmente).

* **[!UICONTROL Network Drive Letter]**: A letra da unidade usada para mapear para o DAM AEM. Não altere isso se não tiver certeza. O aplicativo pode mapear para qualquer letra de unidade no Windows. Se dois usuários inserirem ativos de letras de unidade diferentes, eles não poderão ver os ativos colocados uns pelos outros. O caminho dos ativos é alterado. Os ativos permanecem colocados no arquivo binário (digamos, INDD) e não são removidos. O aplicativo lista todas as letras de unidade disponíveis e, por padrão, usa a última letra disponível que normalmente é `Z`.

* **[!UICONTROL Maximum Cache Size]**: Cache permitido no disco rígido em GB que é usado para armazenar ativos baixados localmente.

* **[!UICONTROL Current cache size]**: Tamanho do armazenamento dos ativos baixados localmente. As informações são exibidas somente depois que os ativos são baixados usando o aplicativo.

* **[!UICONTROL Automatically download linked assets]**: Os ativos colocados nos aplicativos de Creative Cloud nativos suportados são buscados automaticamente se você baixar o arquivo original.

* **[!UICONTROL Maximum number of downloads]**: Ao baixar ativos pela primeira vez (por meio da opção Revelar, Abrir, Editar, Download ou similar), os ativos são baixados somente se o lote contiver menos do que esse número. O valor padrão é 50. Não mude se tiver dúvidas. Aumentar o valor pode levar a tempos de espera mais longos e diminuir o valor pode não permitir que você baixe os ativos ou pastas necessários de uma só vez.

* **[!UICONTROL Upload Acceleration]**: Ao fazer upload de ativos, o aplicativo pode usar uploads simultâneos para melhorar a velocidade de upload. Você pode aumentar a simultaneidade do upload movendo o controle deslizante para a direita. O controle deslizante na extremidade esquerda significa ausência de simultaneidade (carregamento de um único segmento), a posição central corresponde a 10 threads simultâneos e o limite máximo na extremidade direita corresponde a 20 threads simultâneos. Um limite de simultaneidade mais alto requer mais consumo de recursos do processador da máquina local.

Para atualizar as preferências indisponíveis, faça logout do servidor AEM. Depois de atualizar as preferências, clique em ![Salvar preferências](assets/do-not-localize/save_preferences_da2.png) para salvar as alterações.

![Preferências e configurações do aplicativo para desktop](assets/preferences_da2.png)

*Figura: Preferências do aplicativo para desktop*

## Desinstalar o aplicativo {#uninstall-the-app}

Para desinstalar o aplicativo no Windows, siga estas etapas:

1. Faça upload de todas as alterações para AEM para evitar a perda de edições. Consulte [Editar ativos e fazer upload de ativos atualizados para AEM](using.md#edit-assets-upload-updated-assets). Faça logoff e [!UICONTROL Exit] o aplicativo.

1. Remova o aplicativo conforme você removeria qualquer outro aplicativo do SO. Desinstale-o de Adicionar e remova programas no Windows.

1. Para remover o cache e os registros, marque a caixa de seleção necessária.

   ![Caixa de diálogo de desinstalação para remover registros e cache](assets/uninstall_da2.png)

1. Siga as instruções na tela. Quando concluído, reinicie a máquina.

Para desinstalar o aplicativo no Mac, siga estas etapas:

1. Faça upload de todas as alterações para AEM para evitar a perda de edições. Consulte [Editar ativos e fazer upload de ativos atualizados para AEM](using.md#edit-assets-upload-updated-assets). Faça logoff e [!UICONTROL Exit] o aplicativo.

1. Remova o `Adobe Experience Manager Desktop.app` de `/Applications`.

Como alternativa, para limpar caches de aplicativos internos no Mac e desinstalar o aplicativo, você pode executar o seguinte comando no terminal:

```shell
/Applications/Adobe Experience Manager Desktop/Contents/Resources/uninstall-osx/uninstall.sh
```
