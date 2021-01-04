---
title: '[!DNL Adobe Experience Manager] notas de versão do aplicativo de desktop'
description: Detalhes da versão, melhorias, novos recursos, compatibilidade e links de download para  [!DNL Adobe Experience Manager] aplicativo desktop.
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: a25c1fa13895ae9eb7268e3e01c83a5f0b9d7d1d
workflow-type: tm+mt
source-wordcount: '1346'
ht-degree: 35%

---


# [!DNL Adobe Experience Manager] notas de versão do aplicativo de desktop  {#release-notes-v2}

| Produtos | [!DNL Adobe Experience Manager] aplicativo para desktop |
|--- |--- |
| Versão do aplicativo (revisão) | 2.1 (2.1.0.0) |
| Versões [!DNL Adobe Experience Manager] suportadas | [!DNL Experience Manager] como um  [!DNL Cloud Service];  [!DNL Experience Manager] 6.5;  [!DNL Experience Manager] 6.4;  [!DNL Experience Manager] 6.3 (com pacote de compatibilidade) |
| Tipo | Versão secundária |
| Data de lançamento | 17 de dez de 2020 (Mac e Win) |
| URLs para download | [macOS de 64 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-2.1.0.0.dmg);  [Windows de 64 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-2.1.0.0.exe);  [Windows de 32 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-2.1.0.0.exe) |

## Requisitos e pré-requisitos do sistema {#system-requirements-and-prerequisites-v2}

[!DNL Adobe Experience Manager]O aplicativo de desktop do é compatível com os seguintes sistemas operacionais:

* Mac OS X 10.14 ou mais recente, com as últimas correções de erros.

* Windows 10 com os service packs e correções de erros mais recentes.

>[!NOTE]
>
>O fornecedor não oferece mais suporte ao Windows 7 (https://support.microsoft.com/en-us/help/4057281/windows-7-support-ended-on-january-14-2020).

O aplicativo funciona com as seguintes versões [!DNL Experience Manager], seja implantadas como [!DNL Cloud Service], no Adobe Managed Services (AMS) ou no local:

* [[!DNL Experience Manager] como um [!DNL Cloud Service]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/home.html).

* [[!DNL Experience Manager] 6.5.0 ](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html) ou mais recente.

* [[!DNL Experience Manager] 6.4.4](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/sp-release-notes.html) ou mais recente.

* [!DNL Experience Manager] 6.4.0 - 6.4.3 com pacote [ de ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)compatibilidade.

>[!NOTE]
>
>O suporte do aplicativo para desktop para [!DNL Experience Manager] 6.3 foi substituído. O Adobe recomenda atualizar para uma versão [!DNL Adobe Experience Manager] mais recente e suportada.
>[!DNL Experience Manager] 6.3.3.1 ou posterior funciona com o aplicativo de desktop após a instalação do pacote de compatibilidade [a1/>. ](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) Esse pacote não está disponível para [!DNL Experience Manager] 6.3, pois nenhum [service packs estão planejados](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html).

A versão do aplicativo que você planeja instalar no computador local requer uma versão específica do servidor [!DNL Adobe Experience Manager]/componentes adicionais do servidor (service packs, hot fixes ou pacotes de recursos). Entre em contato com o administrador [!DNL Experience Manager] para obter ajuda.

### Suporte para diferentes ativos e tipos de arquivos {#support-for-file-types}

O aplicativo oferece suporte a ativos armazenados em [!DNL Experience Manager] que representam arquivos binários para suas operações básicas. A abertura de arquivos no aplicativo de desktop nativo depende da associação do sistema operacional dos tipos de arquivos específicos, como PNG ou JPG, para aplicativos específicos, como Mac Preview ou Adobe Photoshop.

Alguns tipos de arquivo oferecem suporte para a inserção de ativos vinculados no binário. O aplicativo pré-baixa os ativos vinculados se o ativo estiver presente no repositório [!DNL Experience Manager] quando esses arquivos binários forem abertos usando o aplicativo de desktop. Os tipos de arquivos compatíveis no momento incluem o seguinte:

* [!DNL Adobe InDesign] arquivos (formato INDD)
* [!DNL Adobe Illustrator] arquivos (formato AI)
* [!DNL Adobe Photoshop] arquivos (formato PS)

O recurso é compatível com as versões [!DNL Adobe Creative Cloud] 2018 e [!DNL Adobe Creative Cloud] 2019 do aplicativo acima. O aplicativo usa uma abordagem heurística e de melhor correspondência para mapear os caminhos de desktop locais de ativos vinculados para URLs no servidor [!DNL Experience Manager]. Baseia-se em algumas suposições:

* Os caminhos para os arquivos colocados no aplicativo nativo usam um caminho de área de trabalho global (posicionado a partir do compartilhamento de rede local mostrado com a opção [!UICONTROL Reveal]).

* Os caminhos são armazenados no registro XMP do arquivo pelo aplicativo nativo.

* [!DNL Experience Manager] extraiu o registro XMP com os caminhos para o registro de metadados do ativo.

* Os caminhos podem ser correspondidos a ativos em [!DNL Experience Manager], ou seja, os arquivos inseridos também estão em [!DNL Experience Manager] em um caminho correspondente.

## Novos recursos e melhorias {#whats-new-added}

Para saber mais detalhes, consulte [Novidades da v2.0](introduction.md#whats-new-v2).

**Atualizações no app v2.1.0.0**

* Para carregar ativos, os usuários agora podem arrastar os arquivos ou pastas na interface do aplicativo, diretamente do Windows Explorer ou do Mac Finder. Isso funciona além da opção de carregamento anteriormente disponível no aplicativo.

**Atualizações no app v2.0.3**

O erro corrigido na versão atual é:

* Correção do problema de logon enfrentado pelos usuários do Windows que tentavam acessar o repositório DAM na instância [!DNL Adobe Experience Manager] 6.5.5.0 usando o aplicativo.

**Atualizações no app v2.0.2**

As correções e atualizações de erros são:

* Para melhorar o desempenho do upload, aumente a aceleração do upload em [!UICONTROL Preferences]. Quando essa configuração é ativada, o aplicativo usa mais processos de CPU locais e consome mais recursos.

* Corrigido o problema com uploads de ativos quando nomes de arquivos ou caminhos contêm determinados caracteres GB18030. <!-- CQ-4283494 -->

* A opção Classificar por relevância está disponível depois de alternar para outro tipo de classificação nos resultados da pesquisa. <!-- CQ-4286874 -->

* O aplicativo para desktop agora lista subpastas sem a necessidade de atualizar explicitamente. <!-- CQ-4285711 -->

* (Windows) Corrigido um problema raro de interface de aplicativo inutilizável em algumas máquinas do Windows. Os usuários não podem clicar na interface do aplicativo, pois ela aparece distorcida com a área de clique dos elementos de interface deslocados. <!-- CQ-4280785 -->

**Atualizações no app v2.0.1**

As correções e atualizações de erros são:

* Permita que a opção configure o diretório `%Temp%` para corresponder ao caminho `%APPDATA%`. <!-- CQ-4282665 -->

* Permita que os usuários façam logon no [!DNL Experience Manager] Autor por meio da autenticação Okta SAML. <!-- CQ-4278134 -->

## Instruções de instalação {#installation-instructions-v2}

Para saber como instalar e configurar o aplicativo, consulte [Instalar [!DNL Experience Manager] aplicativo desktop](install-upgrade.md).

Se estiver atualizando de um aplicativo de desktop [!DNL Experience Manager] anterior, você deve seguir essas práticas recomendadas para a transição que estão listadas em [atualização da versão anterior](install-upgrade.md#upgrade-from-previous-version).

## Observações importantes sobre como funciona o aplicativo {#how-app-works}

É importante entender o seguinte sobre o aplicativo e como ele funciona.

* O aplicativo fornece controle total sobre operações que exigem transferência total de binários de ativos de e para [!DNL Experience Manager] (abrir, editar, fazer upload de alterações e fazer upload de ativos).

   * Se quiser trabalhar com o ativo no desktop, você precisa abrir, editar ou baixar explicitamente no desktop, individualmente, em uma pasta ou por meio de várias seleções.

   * Se você quiser obter alterações locais em ativos carregados para [!DNL Experience Manager], é necessário selecionar [!UICONTROL Upload Changes] individualmente ou por meio de várias seleções.

   * O aplicativo não é um “cliente de sincronização” que sincroniza ativos no desktop e no [!DNL Experience Manager].

   * O aplicativo não fornece um compartilhamento de rede que mapeia o repositório [!DNL Experience Manager] como uma estrutura de pasta virtual.

* A lista de ativos mostrada pelo aplicativo se baseia no status do repositório dos Ativos Os arquivos baixados localmente e depois renomeados nos arquivos locais ou na pasta de cache não são exibidos ou gerenciados pelo aplicativo.

* Se o aplicativo não exibir os resultados esperados, clique no ícone atualizar na barra superior.

* O compartilhamento de rede local, mostrado quando você usa a ação [!UICONTROL Reveal File], mostra somente os arquivos (e pastas) que estão disponíveis localmente. O [!UICONTROL Reveal File] e o [!UICONTROL Reveal Folder] baixam previamente os ativos para ajudar a obter os ativos certos exibidos no compartilhamento de rede local.

* O compartilhamento de rede local SMB (Mac) /WebDAV (Win) é usado quando um aplicativo da Adobe Creative Cloud lê os arquivos de ativos vinculados/colocados em um arquivo nativo do aplicativo da Creative Cloud.

O diagrama a seguir ilustra o fluxo de ativos e arquivos da nuvem para o sistema de arquivos local e vice-versa, conforme iniciado pelas ações do usuário.

![[!DNL Experience Manager]Fluxo de ativos do servidor para aplicativos de desktop nativos por meio de aplicativos de desktop](assets/da20_flow_diagram.png)

## Problemas conhecidos {#known-issues-v2}

**Problemas da interface do usuário:**

* Às vezes, a interface do aplicativo de desktop pode ficar em branco. Clique com o botão direito do mouse e em [!UICONTROL Refresh] para recarregar o aplicativo. Após essa atualização, você start na raiz do repositório DAM. As atualizações ou os status de seus ativos são retidos. <!-- CQ-4270267 -->

* Difícil navegar pelas pastas/resultados de pesquisa sem um teclado de rastreamento ou ponteiro do mouse. A barra de rolagem pode não aparecer com dispositivos do mouse sem a roda do mouse. <!-- CQ-4269947 -->

* Raramente, a barra de andamento não é exibida corretamente quando o ativo de upload é alterado.

* Depois de aplicar e remover o filtro para localizar todos os ativos editados localmente, o aplicativo não leva os usuários até os resultados da pesquisa ou a visualização de pasta com os quais os usuários começaram a trabalhar. O aplicativo exibe a pasta raiz do repositório DAM.

* Às vezes, quando você se conecta a um URL que não tem [!DNL Experience Manager] servidor em execução, a tela de conexão fica sem resposta. Saia do aplicativo e reinicie.

**Problemas de CRUD (Create, Read, Update, and Delete, Criar, ler, atualizar e excluir):**

* O aplicativo tenta carregar arquivos mesmo com caracteres inválidos, isso pode causar falha de carregamento no servidor. <!-- CQ-4273652 -->

* Ao carregar alterações em um ativo com comentários, os comentários são armazenados com o ativo em [!DNL Experience Manager], mas não são visíveis como comentários de controle de versão. Esse problema foi resolvido em [!DNL Experience Manager] 6.4.5 e [!DNL Experience Manager] 6.5.1. O Adobe recomenda instalar os service packs mais recentes. <!-- CQ-4268990 -->

* As transferências de ativos não podem ser canceladas pelo usuário. Se você acionou uma transferência volumosa não intencional, saia do aplicativo e reinicie. <!-- CQ-4278940 -->

**Problemas de plataforma:**

* Às vezes, no Windows, o status de um ativo pode mudar imediatamente para [!UICONTROL Edited Locally] depois de abri-lo, mesmo que você não o tenha editado. Clique em [!UICONTROL Refresh] para atualizar.

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] documentação](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/landing/home.html)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] [!DNL Assets] documentação](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/home.html)
>* [Como  [!DNL Experience Manager] usar o aplicativo de desktop](using.md)
>* [Instalar e atualizar o aplicativo de desktop](install-upgrade.md)
>* [Práticas recomendadas e dicas para solução de problemas](troubleshoot.md)

