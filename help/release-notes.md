---
title: Notas de versão do aplicativo Adobe Experience Manager para desktop
description: Detalhes da versão, melhorias, novos recursos, compatibilidade e links de download para o aplicativo de desktop Adobe Experience Manager.
uuid: b783c3f8-aa1e-4c05-b687-5894909769f5
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 3052549b-fe75-44fb-a55e-5cc612868f54
index: y
internal: n
snippet: y
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 63cb82b6bdafeb87d296a895d68cb3912045839a

---


# Notas de versão do aplicativo Adobe Experience Manager para desktop {#release-notes-v2}

| Produtos | Aplicativo de desktop do Adobe Experience Manager |
|----|----|
| Versão do aplicativo (revisão) | 2.0 (2.0.2.0) |
| Versões compatíveis do AEM | AEM como serviço em nuvem; AEM 6.5; AEM 6.4; AEM 6.3 (com pacote de compatibilidade) |
| Tipo | Versão secundária |
| Data de lançamento | 15 de abr de 2020 (Mac e Win) |
| URLs para download | [macOS de 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-osx-2.0.2.0.dmg); [Windows de 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win64-2.0.2.0.exe); [Windows de 32 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win32-2.0.2.0.exe) |

## Requisitos e pré-requisitos do sistema {#system-requirements-and-prerequisites-v2}

O aplicativo de desktop Adobe Experience Manager é compatível com os seguintes sistemas operacionais:

* Mac OS X 10.10 ou posterior, com as correções de erros mais recentes.
* Windows 7 e Windows 10 com os service packs e correções de erros mais recentes.

O aplicativo funciona com as seguintes versões do Experience Manager, seja implantado como um serviço em nuvem, no Adobe Managed Services (AMS) ou no local:

* [Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/home.html)
* [Experience Manager 6.5.0+](https://docs.adobe.com/content/help/en/experience-manager-65/release-notes/release-notes.html) ou posterior
* [Experience Manager 6.4.4+](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/release-notes.html) ou posterior
* Experience Manager 6.4.0 - 6.4.3 com pacote de [compatibilidade](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)

>[!NOTE]
>
>O suporte do aplicativo para desktop para o Experience Manager 6.3 foi descontinuado. A Adobe recomenda atualizar para uma versão mais recente e compatível do Adobe Experience Manager.
>O Experience Manager 6.3.3.1 ou posterior funciona com o aplicativo desktop após a instalação do pacote [de](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)compatibilidade. Esse pacote não está disponível para o Experience Manager 6.3, pois nenhum pacote [de serviços está planejado](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html).

A versão do aplicativo que você pretende instalar no computador local requer uma versão específica do servidor do Adobe Experience Manager/componentes adicionais do servidor (service packs, hot fixes ou pacotes de recursos). Entre em contato com o administrador do Adobe Experience Manager para obter ajuda.

### Support for different assets and file types {#support-for-file-types}

O aplicativo oferece suporte a ativos armazenados no Adobe Experience Manager que representam arquivos binários para suas operações básicas. A abertura de arquivos no aplicativo de desktop nativo depende da associação do sistema operacional dos tipos de arquivos específicos, como PNG ou JPG, para aplicativos específicos, como Mac Preview ou Adobe Photoshop.

Alguns tipos de arquivo oferecem suporte para a inserção de ativos vinculados no binário. O aplicativo pré-baixa os ativos vinculados se o ativo estiver presente no repositório do Experience Manager quando esses arquivos binários forem abertos usando o aplicativo de desktop. Os tipos de arquivos compatíveis no momento incluem o seguinte:

* Arquivos do Adobe InDesign (formato INDD)
* Arquivos do Adobe Illustrator (formato AI)
* Arquivos do Adobe Photoshop (formato PS)

O recurso é compatível com as versões da Adobe Creative Cloud 2018 e da Adobe Creative Cloud 2019 do aplicativo acima. O aplicativo usa uma abordagem heurística e de melhor correspondência para mapear os caminhos de desktop locais de ativos vinculados a URLs no servidor do Experience Manager. Baseia-se em algumas suposições:

* Paths to placed files in the native application use a global desktop path (placed from the local network share shown with [!UICONTROL Reveal] option).
* Os caminhos são armazenados no registro XMP do arquivo pelo aplicativo nativo.
* O Experience Manager extraiu o registro XMP com os caminhos para o registro de metadados do ativo.
* Os caminhos podem corresponder aos ativos no Experience Manager, ou seja, os arquivos inseridos também estão no Experience Manager em um caminho correspondente.

## Novos recursos e melhorias {#whats-new-added}

To know the details, see [What&#39;s new in v2.0](introduction.md#whats-new-v2).

**Atualizações no app v2.0.2**

As correções e atualizações de erros são:

* Para melhorar o desempenho do upload, aumente a aceleração do upload em [!UICONTROL Preferences]. Quando essa configuração é ativada, o aplicativo usa mais processos de CPU locais e consome mais recursos.
* Corrigido o problema com uploads de ativos quando nomes de arquivos ou caminhos contêm determinados caracteres GB18030. <!-- CQ-4283494 -->
* A opção Classificar por relevância está disponível depois de alternar para outro tipo de classificação nos resultados da pesquisa. <!-- CQ-4286874 -->
* O aplicativo para desktop agora lista subpastas sem a necessidade de atualizar explicitamente. <!-- CQ-4285711 -->
* (Windows) Corrigido um problema raro de interface de aplicativo inutilizável em algumas máquinas do Windows. Os usuários não podem clicar na interface do aplicativo, pois ela aparece distorcida com a área de clique dos elementos de interface deslocados. <!-- CQ-4280785 -->

**Atualizações no app v2.0.1**

As correções e atualizações de erros são:

* Permitir que a opção configure o diretório para corresponder ao `%Temp%` `%APPDATA%` caminho. <!-- CQ-4282665 -->
* Permita que os usuários façam logon no AEM Author por meio da autenticação Okta SAML. <!-- CQ-4278134 -->

## Instruções de instalação {#installation-instructions-v2}

To know how to install and configure the app, see [Install Experience Manager desktop app](install-upgrade.md).

If you are upgrading from a previous Experience Manager desktop app, you must follow these best practices for transitioning that are listed at [upgrade from previous version](install-upgrade.md#upgrade-from-previous-version).

## Observações importantes sobre como funciona o aplicativo {#how-app-works}

É importante entender o seguinte sobre o aplicativo e como ele funciona.

* O aplicativo fornece controle total sobre operações que exigem transferência total de binários de ativos de e para o AEM (abrir, editar, fazer upload de alterações e fazer upload de ativos).
   * Se quiser trabalhar com o ativo no desktop, você precisa abrir, editar ou baixar explicitamente no desktop, individualmente, em uma pasta ou por meio de várias seleções.
   * Se você deseja obter alterações locais em ativos carregados no AEM, é necessário selecionar [!UICONTROL Upload Changes], individualmente ou por meio de várias seleções.
   * O aplicativo não é um “cliente de sincronização” que sincroniza ativos no desktop e no AEM.
   * O aplicativo não fornece um compartilhamento de rede que mapeia o repositório do AEM como uma estrutura de pasta virtual.
* A lista de ativos mostrada pelo aplicativo se baseia no status do repositório dos Ativos AEM. Os arquivos baixados localmente e depois renomeados nos arquivos locais ou na pasta de cache não são exibidos ou gerenciados pelo aplicativo.
* Se o aplicativo não exibir os resultados esperados, clique no ícone atualizar na barra superior.
* O compartilhamento de rede local, mostrado quando você usa a ação [!UICONTROL Reveal File], mostra somente os arquivos (e pastas) que estão disponíveis localmente. O [!UICONTROL Reveal File] e o [!UICONTROL Reveal Folder] baixam previamente os ativos para ajudar a obter os ativos certos exibidos no compartilhamento de rede local.
* O compartilhamento de rede local SMB (Mac) /WebDAV (Win) é usado quando um aplicativo da Adobe Creative Cloud lê os arquivos de ativos vinculados/colocados em um arquivo nativo do aplicativo da Creative Cloud.

O diagrama a seguir ilustra o fluxo de ativos e arquivos da nuvem para o sistema de arquivos local e vice-versa, conforme iniciado pelas ações do usuário.

![Fluxo de ativos do servidor AEM para aplicativos de desktop nativos por meio de aplicativos de desktop](assets/da20_flow_diagram.png)

## Problemas conhecidos {#known-issues-v2}

**Problemas da interface do usuário:**

* Às vezes, a interface do aplicativo de desktop pode ficar em branco. Right-click and click [!UICONTROL Refresh] to re-load the application. Após essa atualização, você start na raiz do repositório DAM. As atualizações ou os status de seus ativos são retidos. <!-- CQ-4270267 -->
* Difícil navegar pelas pastas/resultados de pesquisa sem um teclado de rastreamento ou ponteiro do mouse. The scroll-bar might not appear with mouse devices without mouse wheel. <!-- CQ-4269947 -->
* Raramente, a barra de andamento não é exibida corretamente quando o ativo de upload é alterado.
* Depois de aplicar e remover o filtro para localizar todos os ativos editados localmente, o aplicativo não leva os usuários até os resultados da pesquisa ou a visualização de pasta com os quais os usuários começaram a trabalhar. O aplicativo exibe a pasta raiz do repositório DAM.
* Às vezes, quando você é conectado a um URL que não tem um servidor AEM em execução, a tela de conexão fica sem resposta. Saia do aplicativo e reinicie.

**Problemas de CRUD (Create, Read, Update, and Delete, Criar, ler, atualizar e excluir):**

* O aplicativo tenta carregar arquivos mesmo com caracteres inválidos, isso pode causar falha de carregamento no servidor. <!-- CQ-4273652 -->
* Ao carregar alterações em um ativo com comentários, os comentários são armazenados com o ativo no AEM, mas não são visíveis como comentários de controle de versão. Esse problema foi resolvido no AEM 6.4.5 e no AEM 6.5.1. A Adobe recomenda enfaticamente a instalação dos service packs mais recentes. <!-- CQ-4268990 -->
* As transferências de ativos não podem ser canceladas pelo usuário. Se você acionou uma transferência volumosa não intencional, saia do aplicativo e reinicie. <!-- CQ-4278940 -->

**Problemas de plataforma:**

* Às vezes, no Windows, o status de um ativo pode mudar imediatamente para [!UICONTROL Edited Locally] depois de abri-lo, mesmo que você não o tenha editado. Clique em [!UICONTROL Refresh] para atualizar.

>[!MORELIKETHIS]
>
>* [Documentação do AEM como um serviço em nuvem](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/landing/home.html)
>* [Documentação do AEM como ativos de serviço em nuvem](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/home.html)
>* [Como usar o aplicativo de desktop Experience Manager](using.md)
>* [Instalar e atualizar o aplicativo de desktop](install-upgrade.md)
>* [Práticas recomendadas e dicas para solução de problemas](troubleshoot.md)

