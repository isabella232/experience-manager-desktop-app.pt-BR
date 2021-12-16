---
title: '[!DNL Adobe Experience Manager] notas de versão do aplicativo de desktop'
description: Detalhes da versão, melhorias, novos recursos, compatibilidade e links de download para [!DNL Adobe Experience Manager] aplicativo de desktop.
mini-toc-levels: 1
feature: Desktop App,Release Information
exl-id: e058e7a2-fcc8-4ad1-899e-20695db6bc72
source-git-commit: 88d74bb9bff7ec5d454600d383f27dcd5dbbe775
workflow-type: tm+mt
source-wordcount: '1711'
ht-degree: 23%

---

# [!DNL Adobe Experience Manager] notas de versão do aplicativo de desktop {#release-notes-v2}

As informações de versão do aplicativo de desktop mais recente versão 2.1 (2.1.4.0) estão abaixo. A data de lançamento é 16 de dezembro de 2021.

O **compatível [!DNL Experience Manager] versões** são:

* [!DNL Experience Manager] as a [!DNL Cloud Service]. Consulte [notas de versão](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/home.html?lang=pt-BR).
* [!DNL Experience Manager] 6.5.0 ou mais recente, no Adobe Managed Services (AMS) ou no local. Consulte [notas de versão do service pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=pt-BR).
* [!DNL Experience Manager] 6.4.4 ou mais recente, no Adobe Managed Services (AMS) ou no local. Consulte [notas de versão do service pack](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/sp-release-notes.html?lang=pt-BR).
* [!DNL Experience Manager] 6.4.0 - 6.4.3 com o [pacote de compatibilidade](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) instalado, no Adobe Managed Services (AMS) ou no local.
* [!DNL Experience Manager] 6.3 (com pacote de compatibilidade)
* [!DNL Experience Manager] 6.3.3.1 ou mais recente com o [pacote de compatibilidade](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) instalado. O aplicativo de desktop não é compatível com [!DNL Experience Manager] 6.3.3.0 ou versões anteriores.

[!DNL Adobe Experience Manager] o aplicativo de desktop está disponível para o seguinte **sistemas operacionais**:

* macOS X 10.14 ou mais recente, com as correções de erros mais recentes. [Computadores Mac com silício Apple](https://support.apple.com/en-us/HT211814) ainda não são compatíveis.
* Windows 10 com os service packs e correções de erros mais recentes.

O **baixar URLs** para os SO compatíveis são:

| Sistema operacional | [!DNL Experience Manager] as a [!DNL Cloud Service] | [!DNL Experience Manager] 6.x |
|---|---|---|
| macOS (v2.1.3.4) | [Link de download](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-osx-2.1.3.4.dmg) | [Link de download](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-2.1.3.4.dmg) |
| Windows de 64 bits (v2.1.3.4) | [Link de download](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win64-2.1.3.4.exe) | [Link de download](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-2.1.3.4.exe) |
| Windows de 32 bits (v2.1.3.1) | [Link de download](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win32-2.1.3.1.exe) | [Link de download](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-2.1.3.1.exe) |

>[!NOTE]
>
>O Windows 7 não é mais suportado. Consulte [o artigo sobre EOL do Windows 7](https://support.microsoft.com/en-us/help/4057281/windows-7-support-ended-on-january-14-2020).

## Suporte para diferentes ativos e tipos de arquivo {#support-for-file-types}

O aplicativo é compatível com ativos armazenados em [!DNL Experience Manager] que representam arquivos binários para suas operações básicas. A abertura de arquivos no aplicativo de desktop nativo depende da associação do sistema operacional dos tipos de arquivos específicos, como PNG ou JPG, para aplicativos específicos, como Mac Preview ou Adobe Photoshop.

Alguns tipos de arquivo oferecem suporte para a inserção de ativos vinculados no binário. O aplicativo baixa previamente os ativos vinculados se o ativo estiver presente na variável [!DNL Experience Manager] repositório quando esses arquivos binários forem abertos usando o aplicativo de desktop. Os tipos de arquivos compatíveis no momento incluem o seguinte:

* [!DNL Adobe InDesign] arquivos (formato INDD)
* [!DNL Adobe Illustrator] arquivos (formato AI)
* [!DNL Adobe Photoshop] arquivos (formato PS)

O recurso é compatível com [!DNL Adobe Creative Cloud] 2018 e [!DNL Adobe Creative Cloud] Versões de 2019 do aplicativo acima. O aplicativo usa uma abordagem heurística e de melhor correspondência para mapear os caminhos de desktop locais dos ativos vinculados para URLs na [!DNL Experience Manager] servidor. Baseia-se em algumas suposições:

* Os caminhos para os arquivos colocados no aplicativo nativo usam um caminho de desktop global (posicionado a partir do compartilhamento de rede local mostrado com [!UICONTROL Reveal] ).

* Os caminhos são armazenados no registro XMP do arquivo pelo aplicativo nativo.

* [!DNL Experience Manager] extraiu o registro de XMP com os caminhos para o registro de metadados do ativo.

* Os caminhos podem corresponder aos ativos em [!DNL Experience Manager], ou seja, os arquivos inseridos também estão em [!DNL Experience Manager] em um caminho correspondente.

## Novos recursos, melhorias e correções de erros {#what-is-new}

Para saber os detalhes, consulte [Novidades da versão 2.0](introduction.md#whats-new-v2).

**Atualizações no aplicativo v2.1.4.0**

A nova versão do aplicativo oferece uma correção de erro.

**Atualizações no aplicativo v2.1.3.4**

A nova versão do aplicativo oferece uma correção de erro.

**Atualizações no aplicativo v2.1.3.3**

A nova versão do aplicativo oferece uma correção de erro.

**Atualizações no aplicativo v2.1.3.2**

Esta versão do aplicativo oferece uma correção de erro.

**Atualizações no aplicativo v2.1.3.1**

O erro corrigido nesta versão é:

* As velocidades de upload e download de ativos melhoraram, mesmo com ativos grandes. Esta versão corrigiu um problema em que o upload de ativos com [!DNL desktop app] às vezes, falhava quando arquivos muito grandes eram carregados.

**Atualização no aplicativo v2.1.2.0**

* Uma nova opção para [!UICONTROL Clear Cookies] é adicionado ao menu principal do aplicativo. Ajuda com possíveis problemas de logon, por exemplo, ao alterar a conexão de um servidor para outro. Consulte [limpar cookies antes de conectar](/help/troubleshoot.md#cannot-login-cookies-issue).

* Uma opção é adicionada permitindo que o aplicativo carregue pastas e arquivos, de modo que seus nomes de nó tenham sido criados no [!DNL Adobe Experience Manager] são iguais aos nomes de arquivo e pasta locais.

   Esse comportamento é semelhante ao comportamento padrão na versão 1 do aplicativo de desktop. Enquanto na versão atual, se a opção não estiver ativada, os espaços em branco e os caracteres `% ; # , + ? ^ { } "` em nomes de pastas são substituídos por traço nos caminhos de pastas. Além disso, os caracteres em maiúsculas são convertidos em minúsculas nos caminhos da pasta. No entanto, em nomes de arquivos, os caracteres `# % { } ? &` são substituídas por traço; mas os espaços em branco e o invólucro são retidos. Para obter mais informações, consulte [Preferências do aplicativo](/help/install-upgrade.md#set-preferences) e [Fazer upload e adicionar novos ativos](/help/using.md#upload-and-add-new-assets-to-aem).

**Atualização no aplicativo v2.1.1.0**

* Uma configuração avançada permite que o aplicativo emule o comportamento do aplicativo v1.10 ao carregar pastas. Na v1.10, os nomes de nó criados no repositório respeitam os espaços e a identificação dos nomes de pasta fornecidos pelo usuário. O comportamento padrão da v2.1 continua o mesmo, ou seja, substitua vários espaços em nomes de pastas por um hífen no nome do nó do repositório e converta em nomes de nó em minúsculas. Consulte [as preferências do aplicativo](/help/install-upgrade.md#set-preferences).

**Atualização no aplicativo v2.1.0.0**

* Para fazer upload de ativos, os usuários agora podem arrastar os arquivos ou pastas na interface do aplicativo, diretamente do Windows Explorer ou do Mac Finder. Isso funciona além da opção de upload disponível no aplicativo. Consulte [fazer upload de ativos](/help/using.md#upload-and-add-new-assets-to-aem) <!-- CQ-4309527 -->

**Atualização no aplicativo v2.0.3**

O erro corrigido nesta versão é:

* Correção do problema de logon para usuários de aplicativos no Windows que tentam acessar o repositório DAM no [!DNL Adobe Experience Manager] 6.5.5.0

**Atualizações no aplicativo v2.0.2**

As correções de erros e atualizações são:

* A configuração de aceleração de upload agora está disponível para melhorar o desempenho do upload. Quando esta configuração é ativada, o aplicativo faz upload mais rápido usando mais threads locais da CPU e consome mais recursos.

* O ativo é carregado quando nomes de arquivo ou caminhos que contêm determinados caracteres GB18030 são fixos. <!-- CQ-4283494 -->

* A opção Classificar por relevância está disponível após alternar para outro tipo de classificação nos resultados da pesquisa. <!-- CQ-4286874 -->

* O aplicativo de desktop agora lista subpastas sem a necessidade de atualizar explicitamente. <!-- CQ-4285711 -->

* (Windows) Correção de um problema raro de interface de aplicativo inutilizável em algumas máquinas do Windows. Os usuários não podem clicar na interface do aplicativo, pois ela aparece distorcida com a área de clique dos elementos de interface &quot;deslocados&quot;. <!-- CQ-4280785 -->

**Atualizações no aplicativo v2.0.1**

As correções de erros e atualizações são:

* Permitir opção para configurar `%Temp%` diretório para corresponder `%APPDATA%` caminho. <!-- CQ-4282665 -->

* Permitir que os usuários façam logon [!DNL Experience Manager] Autor via autenticação Okta SAML. <!-- CQ-4278134 -->

## Instruções de instalação {#installation-instructions-v2}

Para saber como instalar e configurar o aplicativo, consulte [Instalar [!DNL Experience Manager] aplicativo de desktop](install-upgrade.md).

Se você estiver atualizando de um [!DNL Experience Manager] aplicativo de desktop, você deve seguir essas práticas recomendadas para transição listadas em [atualizar da versão anterior](install-upgrade.md#upgrade-from-previous-version).

## Observações importantes sobre como funciona o aplicativo {#how-app-works}

É importante entender o seguinte sobre o aplicativo e como ele funciona.

* O aplicativo fornece controle total sobre operações que exigem transferência total de binários de ativos de e para [!DNL Experience Manager] (abrir, editar, fazer upload de alterações e fazer upload de ativos).

   * Se quiser trabalhar com o ativo no desktop, você deve abrir, editar ou baixar explicitamente no desktop, individualmente, em uma pasta ou por meio de várias seleções.

   * Se desejar obter alterações locais em ativos carregados para o [!DNL Experience Manager], é necessário selecionar [!UICONTROL Upload Changes], individualmente ou por meio de várias seleções.

   * O aplicativo não é um “cliente de sincronização” que sincroniza ativos no desktop e no [!DNL Experience Manager].

   * O aplicativo não fornece um compartilhamento de rede que mapeia a variável [!DNL Experience Manager] repositório como uma estrutura de pasta virtual.

* A lista de ativos mostrada pelo aplicativo se baseia no status do repositório dos Ativos Os arquivos baixados localmente e depois renomeados nos arquivos locais ou na pasta de cache não são exibidos ou gerenciados pelo aplicativo.

* Se o aplicativo não exibir os resultados esperados, clique no ícone atualizar na barra superior.

* O compartilhamento de rede local, mostrado quando você usa a ação [!UICONTROL Reveal File], mostra somente os arquivos (e pastas) que estão disponíveis localmente. O [!UICONTROL Reveal File] e o [!UICONTROL Reveal Folder] baixam previamente os ativos para ajudar a obter os ativos certos exibidos no compartilhamento de rede local.

* O compartilhamento de rede local SMB (Mac) /WebDAV (Win) é usado quando um aplicativo da Adobe Creative Cloud lê os arquivos de ativos vinculados/colocados em um arquivo nativo do aplicativo da Creative Cloud.

O diagrama a seguir ilustra o fluxo de ativos e arquivos da nuvem para o sistema de arquivos local e o oposto, conforme iniciado pelas ações do usuário.

![[!DNL Experience Manager]Fluxo de ativos do servidor para aplicativos de desktop nativos por meio de aplicativos de desktop](assets/da20_flow_diagram.png)

## Problemas conhecidos {#known-issues-v2}

**Problemas da interface do usuário:**

* Às vezes, a interface do aplicativo de desktop pode ficar em branco. Clique com o botão direito do mouse e clique em [!UICONTROL Refresh] para recarregar o aplicativo. Após essa atualização, você inicia na raiz do repositório DAM. As atualizações ou os status de seus ativos são retidos. <!-- CQ-4270267 -->

* Difícil de navegar pelas pastas/resultados de pesquisa sem um trackpad ou ponteiro do mouse. A barra de rolagem pode não aparecer com dispositivos de mouse sem o botão de rolagem. <!-- CQ-4269947 -->

* Raramente, a barra de andamento não é exibida corretamente quando o ativo de upload é alterado.

* Depois de aplicar e remover o filtro para localizar todos os ativos editados localmente, o aplicativo não leva os usuários até os resultados da pesquisa ou a visualização de pasta com os quais os usuários começaram a trabalhar. O aplicativo exibe a pasta raiz do repositório DAM.

* Às vezes, ao se conectar a um URL que não tem [!DNL Experience Manager] servidor em execução, a tela de conexão fica sem resposta. Saia do aplicativo e reinicie.

**Problemas de CRUD (Create, Read, Update, and Delete, Criar, ler, atualizar e excluir):**

* Ao fazer upload de alterações em um ativo com comentários, os comentários são armazenados com o ativo em [!DNL Experience Manager] mas não são visíveis como comentários de versão. Esse problema é resolvido em [!DNL Experience Manager] 6.4.5 e [!DNL Experience Manager] 6.5.1. A Adobe recomenda a instalação dos service packs mais recentes. <!-- CQ-4268990 -->

* As transferências de ativos não podem ser canceladas pelo usuário. Se você acionou uma transferência volumosa não intencional, saia do aplicativo e reinicie. <!-- CQ-4278940 -->

**Problemas de plataforma:**

* Às vezes, no Windows, o status de um ativo pode mudar imediatamente para [!UICONTROL Edited Locally] depois de abri-lo, mesmo que você não o tenha editado. Clique em [!UICONTROL Refresh] para atualizar.

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] documentação](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/landing/home.html?lang=pt-BR)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] [!DNL Assets] documentação](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/home.html)
>* [Como utilizar [!DNL Experience Manager] aplicativo de desktop](using.md)
>* [Instalar e atualizar o aplicativo de desktop](install-upgrade.md)
>* [Práticas recomendadas e dicas para solução de problemas](troubleshoot.md)

