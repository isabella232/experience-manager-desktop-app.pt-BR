---
title: Instalar e configurar o aplicativo de desktop AEM versão 1.x
description: Instale e configure o aplicativo de desktop AEM versão 1.x para trabalhar com os servidores do AEM Assets e mapeie os ativos para montar como uma unidade em seu desktop.
uuid: 79bc9de9-5708-41f9-ac43-68c1fd2a2129
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f6365302-1690-4719-9b8c-035719422740
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ad5337c8e1697d0a37d3020d25802dc1d732f320

---


# Instalar e configurar o aplicativo de desktop AEM v1.x {#install-and-configure-aem-desktop-app}

Instale e configure o aplicativo de desktop do AEM para trabalhar com os servidores do AEM Assets e baixe os ativos no sistema de arquivos local. Para usar o aplicativo de desktop AEM,

* Certifique-se de que a versão do servidor AEM seja compatível com o aplicativo de desktop AEM. Consulte a matriz de [compatibilidade](release-notes-of-v1.md#compatibilitymatrix).
* Baixe e instale o aplicativo.
* Teste a conexão usando alguns ativos. Consulte [Acessar e abrir ativos na área de trabalho](use-app-v1.md#openondesktop).

## Requisitos do sistema, pré-requisitos e links de download {#system-requirements-prerequisites-and-download-links}

Para obter informações detalhadas, consulte as notas [de versão do aplicativo para desktop do](release-notes-of-v1.md)AEM.

## Instalar e conectar o aplicativo de desktop AEM ao servidor AEM {#install-and-connect-aem-desktop-app-to-aem-server}

Para obter detalhes, consulte [Instalar e conectar o aplicativo de desktop AEM ao servidor](use-app-v1.md#installandconnect)AEM.

>[!NOTE]
>
>Somente uma instância do aplicativo de desktop AEM pode ser instalada e estar ativa de cada vez.

## Suporte a proxy {#proxy-support}

O aplicativo de desktop AEM usa o proxy predefinido do sistema para se conectar à Internet por HTTPS. O aplicativo só pode se conectar usando um proxy de rede que não exija autenticação extra.

Se você configurar ou modificar as configurações do servidor proxy para Windows (Opções da Internet &gt; Configurações de LAN), reinicie o aplicativo de desktop do AEM para que as alterações tenham efeito.

Se o proxy exigir autenticação, a equipe de TI poderá adicionar o URL dos ativos AEM às configurações do servidor proxy para permitir a passagem do tráfego do aplicativo.

## Manuseio de arquivos {#file-handling}

Ao alterar um arquivo de um local de compartilhamento de rede montado pelo aplicativo de desktop, os arquivos são salvos nesse local em duas fases. Na primeira fase, um arquivo é salvo localmente. Um usuário pode salvar o arquivo e continuar trabalhando nele, sem esperar a conclusão da transferência.

Na segunda fase, o aplicativo de desktop carrega o arquivo atualizado no servidor AEM após um atraso predefinido (por exemplo, 30s). Esta operação ocorre em segundo plano. Use a opção Exibir status do ativo para exibir o status da operação de upload.

1. Faça upload de um ativo para os ativos AEM.
1. Clique/toque no ícone do aplicativo para desktop do AEM na barra de ferramentas.
1. No menu, selecione a opção Exibir status do ativo.
1. Na caixa de diálogo, reveja o status da operação de upload.

>[!NOTE]
>
>O aplicativo de desktop AEM pode lidar com ativos de até 40 GB.

## Conectar-se a uma instância do AEM atrás de um dispatcher {#connect-to-an-aem-instance-behind-a-dispatcher}

Os métodos de cópia e movimentação na API Ativos exigem que os seguintes cabeçalhos adicionais sejam passados para o AEM:

* Destino X
* Profundidade X
* X-Overwrite

A área de trabalho do AEM se conecta ao AEM usando um URL que inclui a porta padrão. Portanto, a `virtualhosts` configuração na configuração do dispatcher deve incluir o número da porta padrão. Para obter mais informações sobre a `virtualhosts` configuração, consulte [Identificação de hosts](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts)virtuais.

Para obter informações adicionais sobre como configurar o dispatcher para passar por esses cabeçalhos adicionais, consulte [Especificação dos cabeçalhos](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-http-headers-to-pass-through-clientheaders)HTTP.

## Personalizar a caixa de diálogo Informações do ativo {#customize-the-asset-info-dialog}

Você pode personalizar a caixa de diálogo Informações do ativo sobrepondo um ou ambos os componentes:

* A página da interface do usuário do Granite em `/libs/dam/gui/content/assets/moreinfo`
* O componente HTL `/css/javascript` em `/libs/dam/gui/components/admin/moreinfo`

O componente sobreposto depende da natureza da personalização. Para alterar quais componentes são exibidos como parte da caixa de diálogo Informações do ativo, sobreponha a página da interface do usuário do Granite. Para alterar o conteúdo HTML/CSS/Javascript da caixa de diálogo, sobreponha o componente HTL.

## Gerenciar cache {#manage-cache}

No Windows, o cache está em `%LOCALAPPDATA%\Adobe\AssetsCompanion\Cache\`, onde é uma versão codificada do host AEM configurado no aplicativo de desktop. Por exemplo, `http://localhost:4502` é exibido como `http%3A%2F%2Flocalhost%3A4502%2F`.

No Mac OS X, há um diretório semelhante em `~/Library/Group Containers/group.com.adobe.aem.desktop/cache`.

### Opção no aplicativo para gerenciar o cache {#in-app-option-to-manage-cache}

Você pode controlar a quantidade de espaço em disco disponível para fins de armazenamento em cache local. Os artefatos do servidor do AEM Assets são armazenados em cache localmente para proporcionar uma experiência mais suave. Você pode alterar os padrões para atender às suas necessidades. Além disso, você pode limpar o cache para obter todos os ativos novamente. Para definir as opções desejadas, clique no ícone do aplicativo e clique em **[!UICONTROL Advanced]** &gt; **[!UICONTROL Manage Cache]**. ****

>[!NOTE]
>
>Quando você limpa o cache, ele preserva suas alterações não salvas. Todos os ativos não verificados no servidor AEM são retidos e não excluídos.

### Alterar local do cache no Windows {#change-location-of-cache-on-windows}

O local padrão do cache para o aplicativo de desktop AEM é:

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Cache\EncodedAEMEndpoint`
* Mac: `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/EncodedAEMEndpoint`

`EncodedAEMEndpoint` é o URL de ponto de extremidade AEM configurado do aplicativo de desktop do AEM. O valor é uma versão codificada do URL de definição de metas do servidor AEM. Por exemplo, se o aplicativo estiver direcionando `http://localhost:4502`, o nome do diretório será `http%3A%2F%2Flocalhost%3A4502`. O caminho do Windows para o diretório de cache neste exemplo é %LocalAppData%\Adobe\AssetsCompanion\Cache\http%3A%2F%2Flocalhost%3A4502.

Para apontar o aplicativo para uma pasta diferente ou uma unidade diferente, edite o arquivo de configuração do aplicativo.

1. Navegue até o diretório de instalação do aplicativo. O local padrão no Windows é `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop`.
1. Edite o arquivo Adobe Experience Manager Desktop.exe.config com um editor de texto.

   São necessários privilégios de administrador para salvar alterações neste arquivo.

1. Procure a string "ProxyCacheRoot". Você verá que seu valor está definido para o local de cache "%LocalAppData%\Adobe\AssetsCompanion\Cache". Basta alterar esse valor para qualquer caminho válido.

   >[!NOTE]
   >
   >O aplicativo cria automaticamente um subdiretório *&lt;Endpoint&gt;* de AEM codificado; esse comportamento não é configurável.

## Recursos adicionais {#additional-resources}

* [Introdução ao aplicativo de desktop do AEM](https://helpx.adobe.com/experience-manager/kt/eseminars/ccoo-aem-desktop-app.html)
* [Usar o aplicativo de desktop do AEM](use-app-v1.md)

* [Compreender o check-in/check-out com o aplicativo de desktop AEM](https://helpx.adobe.com/experience-manager/kt/assets/using/checkin-checkout-technical-video-understand.html)
* [Usar o aplicativo de desktop com os ativos AEM](https://helpx.adobe.com/experience-manager/kt/assets/using/checkin-checkout-technical-video-understand.html)
* [Solução de problemas do aplicativo de desktop AEM](troubleshoot-app-v1.md)