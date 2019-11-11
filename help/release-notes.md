---
title: Notas de versão do aplicativo de desktop do AEM
seo-title: Notas de versão do aplicativo de desktop do AEM
description: Detalhes da versão, melhorias, novos recursos, compatibilidade e links de download para o aplicativo de desktop AEM v1.x.
seo-description: Detalhes da versão, melhorias, novos recursos, compatibilidade e links de download para o aplicativo de desktop AEM v1.x.
uuid: b783c3f8-aa1e-4c05-b687-5894909769f5
contentOwner: asgupta
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 3052549b-fe75-44fb-a55e-5cc612868f54
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b74a3ff5c9a25ee1433dd661a1bce677271a5ebe

---


# Notas de versão do aplicativo de desktop do AEM {#release-notes-v2}

| Produtos | Aplicativo de desktop Adobe Experience Manager (AEM) |
|---------------|--------------------------------------------------------------------|
| Versão do aplicativo (Revisão) | 2.0 (2.0.0.4) |
| Versões de AEM suportadas | AEM 6.5, AEM 6.4, AEM 6.3 (com pacote de compatibilidade) |
| Tipo | Versão principal |
| Data de lançamento | 30 de agosto de 2019 (Mac), 9 de setembro de 2019 (Win) |
| Download de URLs | [MacOS de 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-osx-2.0.0.4.dmg); [Windows de 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win64-2.0.0.4.exe); [Windows de 32 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win32-2.0.0.4.exe) |

## Requisitos e pré-requisitos do sistema {#system-requirements-and-prerequisites-v2}

O aplicativo de desktop AEM é compatível com os seguintes sistemas operacionais:

* Mac OS X 10.10 ou posterior, com as últimas correções de erros.
* Windows 7 e Windows 10 com os service packs e correções de erros mais recentes.

O aplicativo funciona com as seguintes versões do AEM, sejam elas implantadas no local ou nos Adobe Managed Services (AMS):

* [AEM 6.5.0](https://helpx.adobe.com/experience-manager/6-5/release-notes.html) ou posterior
* [AEM 6.4.4](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html) ou posterior
* AEM 6.4.0 - 6.4.3 com pacote de [compatibilidade](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)
* AEM 6.3.3.1 e posterior com pacote de [compatibilidade](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)
* Para o AEM 6.3, nenhum pacote de [serviços está planejado](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html). A Adobe recomenda atualizar para uma versão posterior do AEM.

A versão do aplicativo que você pretende instalar no computador local requer uma versão específica do servidor do Adobe Experience Manager/componentes adicionais do servidor (service packs, hot fixes ou pacotes de recursos). Entre em contato com o administrador do AEM para obter ajuda.

### Suporte para diferentes tipos de ativos e arquivos {#support-for-file-types}

O aplicativo suporta ativos armazenados no AEM que representam arquivos binários para suas operações básicas. A abertura de arquivos no aplicativo desktop nativo depende da associação do sistema operacional dos tipos de arquivos específicos, como PNG ou JPG, para aplicativos específicos, como Mac Preview ou Adobe Photoshop.

Alguns tipos de arquivo oferecem suporte para a inserção de ativos vinculados no binário. O aplicativo pré-baixa os ativos vinculados se o ativo estiver presente no repositório do AEM quando esses arquivos binários forem abertos usando o aplicativo de desktop. Os tipos de arquivos suportados atualmente são:

* Arquivos do Adobe InDesign (formato INDD)
* Arquivos do Adobe Illustrator (formato AI)
* Arquivos do Adobe Photoshop (formato PS)

O recurso é compatível com as versões da Adobe Creative Cloud 2018 e da Creative Cloud 2019 do aplicativo acima. O aplicativo usa uma abordagem heurística e de melhor correspondência para mapear os caminhos de desktop locais de ativos vinculados para URLs no servidor AEM. Baseia-se em alguns pressupostos:

* Os caminhos para os arquivos colocados no aplicativo nativo usam um caminho de desktop global (posicionado a partir do compartilhamento de rede local mostrado com a opção "Revelar")
* Os caminhos são armazenados no registro XMP do arquivo pelo aplicativo nativo
* O AEM extraiu o registro XMP com os caminhos para o registro de metadados do ativo
* Os caminhos podem corresponder aos ativos no AEM (ou seja, os arquivos inseridos também estão no AEM em um caminho correspondente)

## Novos recursos e melhorias {#whats-new-added}

Para saber os detalhes, consulte [Novidades no aplicativo](introduction.md#whats-new-v2).

## Instruções de instalação {#installation-instructions-v2}

Para saber como instalar e configurar o aplicativo, consulte [Instalar o aplicativo](install-upgrade.md)de desktop do AEM.

Se você estiver atualizando de um aplicativo de desktop AEM anterior, é necessário seguir essas práticas recomendadas para a transição que estão listadas na [atualização da versão](install-upgrade.md#upgrade-from-previous-version)anterior.

## Observações importantes sobre como o aplicativo funciona {#how-app-works}

É importante entender o seguinte sobre o aplicativo e como ele funciona.

* O aplicativo fornece controle total sobre operações que exigem transferência total de binários de ativos de e para o AEM (abrir, editar, fazer upload de alterações e fazer upload de ativos).
   * Se quiser trabalhar com o ativo no desktop, você precisa abrir, editar ou baixar explicitamente no desktop, individualmente, em uma pasta ou por meio de várias seleções.
   * Se você deseja obter alterações locais em ativos carregados no AEM, é necessário selecionar [!UICONTROL Upload Changes], individualmente ou por meio de várias seleções.
   * O aplicativo não é um "cliente de sincronização" que sincroniza ativos no desktop e no AEM.
   * O aplicativo não fornece um compartilhamento de rede que mapeia o repositório do AEM como uma estrutura de pasta virtual.
* A lista de ativos mostrada pelo aplicativo se baseia no status do repositório do AEM Assets. Os arquivos baixados localmente e depois renomeados nos arquivos locais ou na pasta de cache não são exibidos ou gerenciados pelo aplicativo.
* Se o aplicativo não exibir os resultados esperados, clique no ícone atualizar na barra superior.
* O compartilhamento de rede local, mostrado quando você usa [!UICONTROL Reveal File] ação, mostra somente os arquivos (e pastas) que estão disponíveis localmente. [!UICONTROL Reveal File] e [!UICONTROL Reveal Folder] pré-baixa ativos para ajudar a obter os ativos certos exibidos no compartilhamento de rede local.
* O compartilhamento de rede local SMB (Mac) /WebDAV (Win) é usado quando um aplicativo da Adobe Creative Cloud lê os arquivos de ativos vinculados/colocados em um arquivo nativo do aplicativo da Creative Cloud.

O diagrama a seguir ilustra o fluxo de ativos e arquivos da nuvem para o sistema de arquivos local e vice-versa, conforme iniciado pelas ações do usuário.

![Fluxo de ativos do servidor AEM para aplicativos de desktop nativos por meio de aplicativos de desktop](assets/do-not-localize/da20_flow_diagram.png)

## Known issues {#known-issues-v2}

**Problemas de interface do usuário:**
* Às vezes, a interface do aplicativo de desktop pode ficar em branco. Clique com o botão direito do mouse e clique [!UICONTROL Refresh] para carregar o aplicativo novamente. Essa atualização redefine o estado do aplicativo e você inicia na tela de boas-vindas na raiz do repositório DAM. <!-- CQ-4270267 -->
* Difícil navegar pelas pastas/resultados de pesquisa sem um trackpad ou roda do mouse. A barra de rolagem pode não aparecer com dispositivos do mouse sem a roda do mouse. <!-- CQ-4269947 -->
* Frequentemente, a barra de progresso não é exibida corretamente quando o ativo de upload é alterado.
* Depois de aplicar e remover o filtro para localizar todos os ativos editados localmente, o aplicativo não leva os usuários para os resultados da pesquisa ou para a visualização de pasta com os quais os usuários começaram a trabalhar. O aplicativo exibe a pasta raiz do repositório DAM.
* Às vezes, quando você se conecta a um URL que não tem um servidor AEM em execução, a tela de conexão fica sem resposta. Saia do aplicativo e inicie-o novamente.

**Problemas de CRUD (Criar, Ler, Atualizar e Excluir):**
* O aplicativo tenta carregar arquivos mesmo com caracteres inválidos, pode causar falha de carregamento no servidor. <!-- CQ-4273652 -->
* Ao fazer upload de alterações em um ativo com comentários, os comentários são armazenados com o ativo no AEM, mas não são visíveis como comentários de versão (resolvidos no AEM 6.4.5, 6.5.1). <!-- CQ-4268990 -->
* As transferências de ativos não podem ser canceladas pelo usuário. Se você disparou uma transferência grande não intencional, saia do aplicativo e inicie-o novamente. <!-- CQ-4278940 -->

**Problemas de plataforma:**
* Às vezes, no Windows, o status de um ativo pode mudar imediatamente para [!UICONTROL Edited Locally] depois de abri-lo, mesmo que você não o tenha editado. Clique [!UICONTROL Refresh] para atualizar.

>[!MORELIKETHIS]
>
>* [Documentação do AEM 6.5](https://helpx.adobe.com/support/experience-manager/6-5.html)
>* [Documentação do AEM Assets 6.5](https://docs.adobe.com/content/help/en/experience-manager-64/assets/home.html)
>* [Usar o aplicativo de desktop do AEM](using.md)
>* [Instalar e atualizar o aplicativo de desktop](install-upgrade.md)
>* [Práticas recomendadas e dicas para solução de problemas](troubleshoot.md)

