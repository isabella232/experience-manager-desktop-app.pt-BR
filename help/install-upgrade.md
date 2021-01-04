---
title: Instalar e configurar [!DNL Adobe Experience Manager] aplicativo desktop
description: Instale e configure [!DNL Adobe Experience Manager] desktop app to work with [!DNL Adobe Experience Manager Assets] servidores e baixe os ativos no seu sistema de arquivos local.
translation-type: tm+mt
source-git-commit: a25c1fa13895ae9eb7268e3e01c83a5f0b9d7d1d
workflow-type: tm+mt
source-wordcount: '1162'
ht-degree: 1%

---


# Instalar [!DNL Adobe Experience Manager] aplicativo desktop {#install-app-v2}

Usando o [!DNL Adobe Experience Manager] aplicativo de desktop, os ativos em [!DNL Experience Manager] são facilmente disponíveis em seu desktop local e podem ser usados em qualquer aplicativo de desktop nativo. Os ativos podem ser visualizados, abertos em aplicativos nativos de desktop, revelados no Mac Finder ou no Windows Explorer para serem colocados em outros documentos e alterados localmente - as alterações são salvas em [!DNL Experience Manager] quando você carrega e uma nova versão é criada no repositório.

Tal integração permite que várias funções na organização

* Gerencie os ativos centralmente em [!DNL Experience Manager Assets].

* Acesse os ativos em qualquer aplicativo de desktop nativo, incluindo aplicativos de terceiros e no Adobe Creative Cloud. Ao fazê-lo, os usuários podem facilmente aderir aos vários padrões, incluindo marcas.

Para usar [!DNL Experience Manager] aplicativo de desktop,

* Certifique-se de que sua versão [!DNL Experience Manager] seja suportada pelo [!DNL Experience Manager] aplicativo de desktop. Consulte os [requisitos do sistema](release-notes.md#system-requirements-and-prerequisites-v2) abaixo.

* Baixe e instale o aplicativo. Consulte [instalar aplicativo de desktop](#install-v2) abaixo.

* Teste a conexão usando alguns ativos. Consulte [como navegar e procurar ativos](using.md#browse-search-preview-assets).

## Requisitos do sistema, pré-requisitos e links de download {#tech-specs-v2}

Para obter informações detalhadas, consulte as [[!DNL Experience Manager] notas de versão do aplicativo para desktop](release-notes.md).

## Atualizar de uma versão anterior {#upgrade-from-previous-version}

Se você for um usuário da versão 1.x do aplicativo para desktop, entenda as diferenças e as semelhanças entre a versão anterior e a versão mais recente do aplicativo. Veja [o que há de novo no aplicativo de desktop](introduction.md#whats-new-v2) e [como o aplicativo funciona](release-notes.md#how-app-works)

>[!NOTE]
>
>Duas versões do aplicativo desktop não podem coexistir em uma máquina. Antes de instalar uma versão, desinstale a outra versão.

Para atualizar de uma versão anterior do aplicativo, siga estas instruções:

1. Antes de atualizar, sincronize todos os ativos e carregue as alterações para [!DNL Experience Manager]. Isso evita perder edições ao desinstalar o aplicativo.

1. Desinstale a versão anterior do aplicativo. Ao desinstalar, selecione a opção para limpar o cache.

1. Reinicie a máquina.

1. [](release-notes.md) Baixe e  [](#install-v2) instale o aplicativo mais recente. Siga as instruções abaixo.

## Instalar {#install-v2}

Para instalar o aplicativo de desktop, siga estas etapas. Desinstale qualquer aplicativo de desktop Adobe [!DNL Experience Manager] v1.x existente antes de instalar o aplicativo mais recente. Para obter mais informações, consulte acima.

1. Baixe o instalador mais recente da página [notas de versão](release-notes.md).

1. Mantenha o URL e as credenciais da sua implementação [!DNL Experience Manager] acessíveis.

1. Se você estiver atualizando de outra versão do aplicativo, consulte [atualizar aplicativo desktop](#upgrade-from-previous-version).

1. Ignore esta etapa se estiver usando [!DNL Experience Manager] como [!DNL Cloud Service], [!DNL Experience Manager] 6.4.4 ou posterior, ou [!DNL Experience Manager] 6.5.0 ou posterior. Certifique-se de que sua configuração [!DNL Experience Manager] atenda aos requisitos de compatibilidade mencionados nas [notas de versão](release-notes.md). Se necessário, baixe o [pacote de compatibilidade](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) aplicável e instale-o usando o [!DNL Experience Manager] Gerenciador de pacotes como um administrador [!DNL Experience Manager]. Para instalar um pacote, consulte [Como trabalhar com Pacotes](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html).

1. Execute o binário do instalador e siga as instruções na tela para instalar.

1. No Windows, o instalador pode solicitar a instalação de `Visual Studio C++ Redistributable 2015`. Siga as instruções na tela para instalá-la. Se a instalação falhar, instale-a manualmente. Baixe o instalador de [here](https://www.microsoft.com/en-us/download/details.aspx?id=52685) e instale os arquivos `vc_redist.x64.exe` e `vc_redist.x86.exe`. Execute novamente o instalador do aplicativo para desktop [!DNL Experience Manager].

1. Reinicie a máquina, conforme solicitado. Inicie e configure o aplicativo de desktop.

1. Para conectar o aplicativo a um repositório [!DNL Experience Manager], clique no ícone do aplicativo na bandeja e inicie o aplicativo. Forneça o endereço do servidor [!DNL Experience Manager] no formato `https://[aem_server]:[port]/`.

   Clique em **[!UICONTROL Connect]** e forneça as credenciais.

   ![Tela de conexão do aplicativo desktop ao endereço do servidor de entrada](assets/connect_da2.png)

   *Figura: Tela de conexão com o endereço do servidor de entrada.*

   >[!CAUTION]
   >
   >Verifique se não há espaços à esquerda ou à direita antes ou depois do endereço do servidor [!DNL Experience Manager]. Caso contrário, o aplicativo não poderá se conectar ao servidor [!DNL Experience Manager].

1. Após uma conexão bem-sucedida, você pode visualização a lista de pastas e ativos disponíveis na pasta raiz do [!DNL Experience Manager] DAM. Você pode navegar pelas pastas dentro do aplicativo.

   ![Após o logon, o aplicativo exibe o conteúdo do DAM](assets/firstview_da2.png)

   *Figura: O aplicativo exibe o conteúdo do DAM após o logon*

1. ([!DNL Experience Manager] 6.5.1 ou posterior) Se você estiver usando um aplicativo desktop com [!DNL Experience Manager] 6.5.1 ou posterior, atualize o conector S3 ou Azure para a versão 1.10.4 ou posterior. Consulte [Conector do Azure](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#azure-data-store) ou [Conector S3](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#amazon-s-data-store).

   Se você for um cliente do Adobe Managed Services (AMS), entre em contato com o Atendimento ao cliente da Adobe.

## Definir preferências {#set-preferences}

Para alterar as preferências, clique no ícone ![Mais opções](assets/do-not-localize/more_options_da2.png) e **[!UICONTROL Preference]** ![Ícone de preferências](assets/do-not-localize/preferences_icon_da2.png). Na janela **[!UICONTROL Preferences]**, ajuste os valores do seguinte:

* [!UICONTROL Launch application on login].

* [!UICONTROL Show window when application starts].

* **[!UICONTROL Cache Directory]**: Local do cache local do aplicativo (ele contém os ativos baixados localmente).

* **[!UICONTROL Network Drive Letter]**: A letra da unidade usada para mapear para o  [!DNL Experience Manager] DAM. Não altere isso se não tiver certeza. O aplicativo pode mapear para qualquer letra de unidade no Windows. Se dois usuários inserirem ativos de letras de unidade diferentes, eles não poderão ver os ativos colocados uns pelos outros. O caminho dos ativos é alterado. Os ativos permanecem colocados no arquivo binário (digamos, INDD) e não são removidos. O aplicativo lista todas as letras de unidade disponíveis e, por padrão, usa a última letra disponível que normalmente é `Z`.

* **[!UICONTROL Maximum Cache Size]**: Cache permitido no disco rígido em GB que é usado para armazenar ativos baixados localmente.

* **[!UICONTROL Current cache size]**: Tamanho do armazenamento dos ativos baixados localmente. As informações são exibidas somente depois que os ativos são baixados usando o aplicativo.

* **[!UICONTROL Automatically download linked assets]**: Os ativos colocados nos aplicativos de Creative Cloud nativos suportados são buscados automaticamente se você baixar o arquivo original.

* **[!UICONTROL Maximum number of downloads]**: Ao baixar ativos pela primeira vez (por meio da opção Revelar, Abrir, Editar, Download ou similar), os ativos são baixados somente se o lote contiver menos do que esse número. O valor padrão é 50. Não mude se tiver dúvidas. Aumentar o valor pode levar a tempos de espera mais longos e diminuir o valor pode não permitir que você baixe os ativos ou pastas necessários de uma só vez.

* **[!UICONTROL Upload Acceleration]**: Ao fazer upload de ativos, o aplicativo pode usar uploads simultâneos para melhorar a velocidade de upload. Você pode aumentar a simultaneidade do upload movendo o controle deslizante para a direita. O controle deslizante na extremidade esquerda significa ausência de simultaneidade (carregamento de um único segmento), a posição central corresponde a 10 threads simultâneos e o limite máximo na extremidade direita corresponde a 20 threads simultâneos. Um limite de simultaneidade mais alto requer mais consumo de recursos do processador da máquina local.

Para atualizar as preferências indisponíveis, faça logout do servidor [!DNL Experience Manager]. Depois de atualizar as preferências, clique em ![Salvar preferências](assets/do-not-localize/save_preferences_da2.png) para salvar as alterações.

![Preferências e configurações do aplicativo para desktop](assets/preferences_da2.png)

*Figura: Preferências do aplicativo para desktop.*

## Desinstalar o aplicativo {#uninstall-the-app}

Para desinstalar o aplicativo no Windows, siga estas etapas:

1. Carregue todas as alterações em [!DNL Experience Manager] para evitar a perda de edições. Consulte [Editar ativos e carregar ativos atualizados para [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets). Faça logoff e [!UICONTROL Exit] o aplicativo.

1. Remova o aplicativo conforme você removeria qualquer outro aplicativo do SO. Desinstale-o de Adicionar e remova programas no Windows.

1. Para remover o cache e os registros, marque a caixa de seleção necessária.

   ![Desinstalar caixa de diálogo para remover registros e cache](assets/uninstall_da2.png)

1. Siga as instruções na tela. Quando concluído, reinicie a máquina.

Para desinstalar o aplicativo no Mac, siga estas etapas:

1. Carregue todas as alterações em [!DNL Experience Manager] para evitar a perda de edições. Consulte [Editar ativos e carregar ativos atualizados para [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets). Faça logoff e [!UICONTROL Exit] o aplicativo.

1. Remova `Adobe Experience Manager Desktop.app` de `/Applications`.

Como alternativa, para limpar caches de aplicativos internos no Mac e desinstalar o aplicativo, você pode executar o seguinte comando no terminal:

```shell
/Applications/Adobe Experience Manager Desktop/Contents/Resources/uninstall-osx/uninstall.sh
```
