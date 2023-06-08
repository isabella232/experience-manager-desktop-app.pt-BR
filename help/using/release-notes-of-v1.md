---
title: Notas de versão do aplicativo de desktop v1.10
description: Detalhes da versão, melhorias, novos recursos, compatibilidade e links de download para o aplicativo para desktop AEM versão 1.10.
exl-id: 886864e0-016a-4a17-b3ba-4b18a514214a
source-git-commit: df5283f6bef6adbb007bf93c6dabb3b12e430f58
workflow-type: tm+mt
source-wordcount: '3898'
ht-degree: 1%

---

# [!DNL Adobe Experience Manager] notas de versão do aplicativo de desktop v1.10 {#aem-desktop-app-release-notes}

Para a versão v1.x do aplicativo de desktop, veja a seguir os links de download e as informações de compatibilidade do AEM.

| Produtos | Aplicativo de desktop do [!DNL Adobe Experience Manager] |
|--- |--- |
| Versão | 1.10 (1.10.0.6 no Mac e 1.10.0.3 no Windows) |
| Tipo | Versão secundária |
| Data | 1.10.0.6 (Mac): 15 de abril de 2020; 1.10.0.3 (Win): 31 de agosto de 2018 |
| URLs para download | [Mac OS X 64 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-1.10.0.6.dmg); [Windows de 32 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-1.10.0.3.exe); [Windows de 64 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-1.10.0.3.exe) |
| Compatibilidade | AEM 6.5.x; AEM 6.4.x; AEM 6.3 SP2; AEM AEM 6.2 SP1 CFP2+; 6.1 SP2 CFP7+ |

>[!NOTE]
>
>O limite de tamanho do cache não é aplicado. Quando o aplicativo de desktop é iniciado, o tamanho do cache é calculado uma vez e uma notificação é exibida se o tamanho estiver próximo do limite predefinido.

## Requisitos e pré-requisitos do sistema {#system-requirements-and-prerequisites}

[!DNL Adobe Experience Manager]O aplicativo de desktop do é compatível com os seguintes sistemas operacionais:

* Mac OS X 10.10 ou mais recente, com as correções de erros mais recentes.

* Windows 10 com os service packs e correções de erros mais recentes.

>[!NOTE]
>
>Não há mais suporte para o Windows 7. Consulte [o artigo sobre EOL do Windows 7](https://support.microsoft.com/en-us/help/4057281/windows-7-support-ended-on-january-14-2020).

A Adobe recomenda o uso da versão mais recente do aplicativo de desktop AEM para aproveitar os recursos e as correções de erros mais recentes e o melhor desempenho possível.

A versão do aplicativo para desktop AEM que você pretende instalar no computador local requer uma versão específica do servidor AEM/componentes adicionais do servidor (service packs, hot fixes ou pacotes de recursos). Verifique se o servidor AEM está configurado corretamente antes de se conectar a ele pela primeira vez. Se precisar de ajuda, entre em contato com o administrador do AEM.

Consulte a [matriz de compatibilidade detalhada](#compatibilitymatrix) no final deste documento para avaliar os pré-requisitos da sua configuração.

## Novidades no aplicativo de desktop v1.10 {#what-s-new-in-aem-desktop-app}

O aplicativo para desktop AEM 1.10 tem como objetivo melhorar a experiência do usuário com uploads grandes, informações sobre as operações em segundo plano e experiência otimizada ao abrir ativos com arquivos vinculados (como o InDesign).

>[!NOTE]
>
>Se você estiver usando o macOS 10.15.4 ou mais recente, use a versão 1.10.0.6 do aplicativo. Esta versão de patch está em conformidade com [Requisitos de autenticação do Apple](https://developer.apple.com/news/?id=04102019a).

**Edição local / Check-out**: os uploads automáticos de alterações salvas em ativos podem ser desativados na janela de status. Dessa forma, o usuário pode continuar trabalhando nos arquivos e salvando as alterações e, quando estiverem prontos, decidir fazer upload de todas as alterações.

**Janela Status do ativo simplificado**. A janela de status foi simplificada. A variável [!UICONTROL Uploads] A guia agora mostra ativos individuais, bem como carregamentos em pasta ou em massa. A guia anterior Uploads em massa foi removida.

**Ícone de aplicativo para indicar uploads em massa**. O ícone do aplicativo indica que um upload em massa está em andamento ao mostrar uma sobreposição de &quot;transferência&quot;.

**Notificações para Conflitos de Atualização**. Quando o aplicativo detectar um conflito ao tentar atualizar um ativo, uma notificação será exibida, para que o usuário possa revisá-la sem a necessidade de monitorar a janela de status. Quando o aplicativo for iniciado, ele verificará todos os conflitos para que o usuário possa resolvê-los.

**Melhor tratamento das perdas de conexão**. Os uploads em massa serão pausados se houver perda de conexão e o usuário poderá retomar a operação posteriormente. A [!UICONTROL Retry] A opção está disponível para tentar novamente um upload com falha de um arquivo individual.

## Instruções de instalação {#installation-instructions}

Para obter instruções detalhadas, consulte [Instalar e configurar o aplicativo de desktop AEM](install-configure-app-v1.md).

## Melhorias nas versões anteriores {#enhancements-in-the-previous-versions}

Esta versão estende e substitui as versões anteriores da [!DNL Experience Manager] aplicativo de desktop da, que forneceu as seguintes melhorias principais:

* **Versão 1.9/1.9.1**: uploads retomáveis, janela de status aprimorada, ícones de aplicativo que indicam o status do aplicativo/conexão, pré-busca de ativos vinculados para arquivos do InDesign.

* **Versão 1.8**: melhor controle do tamanho do cache para o usuário, experiência de logon aprimorada para SAML/SSO no Windows, suporte ao proxy de rede .pac no Mac e problemas relatados pelo cliente.

* **Versão 1.7**: melhorias na estabilidade e na lógica de cache, melhor suporte para proxy de rede e capacidade de limpar arquivos internos após a desinstalação.

* **Versão 1.6**: melhorias no processo de logon para várias configurações de segurança AEM e estabilidade e desempenho do aplicativo.

* **Versão 1.5**: estabilidade e resiliência de aplicativos contra vários problemas de rede, melhor capacidade de suporte.

* **Versão 1.4**: a capacidade de fazer upload de pastas hierárquicas em segundo plano com o monitoramento do progresso.

* **Versão 1.3**: aprimoramentos de desempenho e estabilidade de acesso a arquivos e salvamento de alterações no AEM, especialmente em aplicativos de desktop Creative Cloud, como InDesign, Illustrator ou Photoshop. O objetivo era proporcionar aos usuários uma experiência mais semelhante à de um desktop local ao trabalhar com arquivos, enquanto manipulava simultaneamente operações de transferência de dados em rede em segundo plano.

### Melhorias disponíveis desde o aplicativo de desktop AEM 1.9 {#Enhancements-Available-Since-AEM-Desktop-App-19x}

[!DNL Adobe Experience Manager] o aplicativo de desktop 1.9.1 era uma versão de patch para resolver alguns problemas principais do cliente sobre check-out de ativos e cópia de arquivos do compartilhamento de rede para um diretório local.

* Os ativos verificados por um usuário não devem estar disponíveis para modificação para outros usuários (CQ-4246009)

* Suporte à cópia da pasta mapeada para uma pasta local quando a pasta do usuário está em uma partição de disco separada (CQ-4243978)

O aplicativo para desktop AEM 1.9 tem como objetivo melhorar a experiência do usuário com uploads grandes, informações sobre as operações em segundo plano e experiência otimizada ao abrir ativos com arquivos vinculados (como o InDesign).

**Uploads retomáveis**
Para uploads, especialmente em arquivos grandes, há uma opção para pausá-los/retomá-los na nova janela Status do ativo.

**Janela Status do ativo aprimorada**
Uma janela de status de ativo aprimorada fornece as seguintes informações sobre os ativos.

[!UICONTROL Changes]

* Exibe as alterações atualmente na fila.

* Mostra uploads em andamento, incluindo uma barra de progresso, taxa de transferência, tamanho total do arquivo e tamanho transferido até o momento.

* Uploads concluídos mostrados com o total transferido e a taxa final.

* Os uploads com falha são exibidos junto com uma mensagem de erro e informações de transferência, se disponíveis.

* Os uploads que falharam 3 vezes mostrarão uma mensagem de erro.

* Arquivos conflitantes mostrados com um ícone no qual o usuário pode clicar. Clicar no ícone mostra uma caixa de diálogo com uma explicação e duas opções:

   * [!UICONTROL Keep Mine] faz o upload do arquivo imediatamente no servidor.

   * [!UICONTROL Overwrite Mine] O exclui imediatamente o arquivo local e baixa uma nova cópia do servidor.

[!UICONTROL Downloads]

* Exibe downloads em andamento, incluindo uma taxa de transferência e o tamanho transferido até o momento.

* Downloads concluídos mostrados com o total transferido, taxa final e um ícone que abrirá o arquivo quando clicado (disponível apenas para arquivos únicos).

* Downloads malsucedidos exibidos com uma mensagem de erro e informações de transferência, se disponíveis.

* O rodapé mostra o número total de arquivos baixados e a taxa média de transferência.

* Se um usuário optar por abrir ou editar vários arquivos no [!DNL Experience Manager Assets] Web, elas serão agrupadas. Por exemplo, myasset.jpeg e mais 4 arquivos.

* Ao baixar Documentos do InDesign, incluindo ativos vinculados armazenados no AEM Assets, o aplicativo de desktop baixará todos os Ativos vinculados primeiro, antes de abrir o [!UICONTROL Adobe InDesign] documento e indicar o download de ativos vinculados. Por exemplo, 5 de 24.

[!UICONTROL Bulk Uploads]

Fazer upload de grandes hierarquias de pastas por meio de [!UICONTROL Create] > [!UICONTROL Upload Folder] na interface da Web do AEM, copiar e selecionar &quot;Colar ativos&quot; no Finder ou no Explorer, no menu de contexto do aplicativo de desktop, acionará o uso dessa caixa de diálogo.

* Exibe uploads em andamento, incluindo uma barra de progresso e o nome do arquivo que está sendo transferido.

* Os uploads em andamento incluem um ícone que cancelará o upload quando clicado. A transferência será interrompida após a conclusão da transferência do arquivo atual.

* Os processos de transferência com falha são exibidos com uma mensagem de erro (somente se toda a transferência falhar).

* Se um arquivo individual não for transferido, ele aparecerá na guia como um erro. Caso contrário, os arquivos individuais não aparecerão na guia * apenas uma única entrada para todo o upload.

**Ícones para Indicar o Status das Operações em Segundo Plano**

O ícone do aplicativo indicará o estado das operações em segundo plano para fornecer uma sugestão visual melhor aos usuários. Por exemplo, quando o aplicativo não está conectado ao AEM, o ícone fica esmaecido, quando há um upload ativo, ele mostra uma sobreposição de &quot;sincronização&quot; etc.

**Pré-busca de ativos vinculados**

Para melhorar a experiência do usuário ao trabalhar com documentos do InDesign, que incluem ativos vinculados armazenados no AEM, o aplicativo de desktop tentará buscar previamente esses arquivos vinculados no cache local antes de baixar e abrir o documento do InDesign. Dessa forma, o usuário terá os arquivos vinculados disponíveis localmente e não precisará aguardar mais ao acessá-los no InDesign (no painel Links ).
Observe que a busca prévia só funciona se o AEM reconhecer os links no lado do servidor. Um ativo com links reconhecidos terá uma lista de &quot;Referências&quot; listadas na visualização Propriedades do ativo do InDesign.

### Melhorias disponíveis desde o aplicativo de desktop AEM 1.8.x {#enhancements-available-since-aem-desktop-app-18x}

A versão de acompanhamento rápido do aplicativo de desktop AEM 1.8.1 adicionou melhorias ao abrir vários arquivos de uma só vez da interface AEM para a versão 1.8 (CQ-4237747, CQ-4238780). As melhorias no aplicativo para desktop AEM 1.8 são:

* Armazenamento em cache: nova interface para gerenciar o cache do aplicativo de desktop AEM (CQ-4208690), incluindo,

   * exibir tamanho atual do cache

   * definir o tamanho máximo do cache antes do envio de uma notificação

   * O tamanho do cache é verificado somente na inicialização do aplicativo de desktop, e uma notificação é exibida se estiver atingindo o limite configurado

   * o botão limpar cache agora está disponível na nova interface do usuário

* Logon: (Win) correção do logon na instância do AEM configurada para usar SAML e SSL (CQ-4216353)

* Rede:

   * quando uma sessão de AEM expira, o usuário agora é notificado e pode clicar na notificação para fazer logon novamente (CQ-4202028).

   * (Mac) Adicionar suporte para conexão com AEM usando configuração de proxy .pac (CQ-4233430).

   * (Win) corrija problemas com a caixa de diálogo Avançado - URL de logon (CQ-4236061).

* Correções de erros:

   * Caixa de diálogo Mais informações do ativo: às vezes, a barra de ação não estava visível (CQ-4208540).

   * (Win) O arquivo agora pode ser sincronizado após reverter para uma versão anterior da interface do usuário do AEM Assets (CQ-4216411).

### Melhorias disponíveis desde o aplicativo de desktop AEM 1.7 {#Enhancements-Available-Since-AEM-Desktop-App-17}

* Estabilidade:

   * Estabilidade aprimorada quando o aplicativo de desktop AEM se conecta a um servidor AEM sobrecarregado (CQ-4224803).

   * Estabilidade aprimorada quando muitos arquivos são solicitados (CQ-4224212).

   * Atualização de ativos aprimorada com verificação adicional (CQ-4228291).

* Armazenamento em cache:

   * Correção de erros de disco e problemas de abertura ao abrir arquivos no Photoshop, InDesign, Finder (CQ-4223993, CQ-4217603, CQ-4223717).

   * Armazenamento em cache aprimorado para evitar binários de tamanho zero (CQ-4216599).

* Logon: permitir a conexão com strictSSL desabilitado para configurações especiais (como certificados emitidos localmente) (CQ-4223949).

* Rede: suporte aprimorado para conexão via proxy de rede (CQ-4223477, CQ-4221280, CQ-4206854).

* Instalação e desinstalação:

   * (Win) Desinstalação do limpador (CQ-4220906).

   * [Windows de 32 bits] Falha do instalador ao tentar instalar o Microsoft .NET Framework v. 4.5 (CQ-4218084).

   * (Mac) Script manual para remover completamente os arquivos de aplicativo de desktop (CQ-4216489).

>[!NOTE]
>
>Problemas encontrados nas cargas beta do aplicativo de desktop AEM 1.7 (que não estavam presentes na versão 1.6 não são relatados nas notas de versão).

### Melhorias disponíveis desde o aplicativo de desktop AEM 1.6 {#Enhancements-Available-Since-AEM-Desktop-App-16}

* Documentação: nova [Práticas recomendadas para o aplicativo v1.x](/help/using/best-practices-for-v1.md) documentação.

* Processo de logon aprimorado para AEM:

   * Melhorar o manuseio de SAML * regras de atenuação (CQ-4202781).

   * Adicione a capacidade de configurar um URL de logon separado em Preferências (CQ-4214052, CQ-4214051).

* Usabilidade: notifique o usuário quando o ativo ainda estiver sendo baixado para ativos maiores (CQ-4216284).

* Rede:

   * Armazenamento em cache DNS (CQ-4210176).

   * Conexão de suporte via proxy no Windows (CQ-4206854).

* Armazenamento em cache e acesso ao compartilhamento de rede no Finder/Explorer:

   * O ícone de bloqueio agora está visível para ativos verificados no Windows 10 (CQ-90957).

   * O conteúdo da pasta pode desaparecer/reaparecer no compartilhamento de rede (CQ-4209160, CQ-4210180).

   * Erro no upload do arquivo devido a um conflito relatado no Status da fila de upload (CQ-4215727).

   * Ao abrir vários arquivos da pasta de aplicativos de desktop no PS, mensagens truncadas ou incompletas de arquivos podem ser exibidas (CQ-4216276).

* Correções na estabilidade e no desempenho:

   * Desempenho aprimorado ao navegar pelas pastas com muitos ativos (CQ-4214933).

   * O aplicativo de desktop 1.5 pode desacelerar a máquina de desktop ao longo do tempo (CQ-4209159).

   * O recurso Mostrar status da fila funciona somente para o usuário que instalou o aplicativo (CQ-4212199).

   * (Windows) Verifique se o instalador de 32 bits não contém o código de 64 bits (CQ-4217406).

* Problemas selecionados encontrados e corrigidos em 1.6 Beta:

   * Alto uso da CPU (CQ-4218070).

   * Arraste e solte arquivos que geram erros ao fazer upload para o AEM (CQ-4217006).

### Melhorias disponíveis desde o aplicativo de desktop AEM 1.5 {#Enhancements-Available-Since-AEM-Desktop-App-15}

**Versão 1.5.1.5 para Mac OS X:** A versão 1.5.1.5 oferece os seguintes benefícios:

* Novos recursos e melhorias: adicione a funcionalidade Copiar/Colar à integração do Finder para permitir a transferência direta do desktop para o AEM (CQ-4208158).

* Correções de erros:

   * Correção do problema 43 que ocorria às vezes durante a renomeação de ativos (CQ-4207900).

   * Reverter para uma versão mais antiga da linha do tempo no AEM não atualiza o ativo no Localizador (CQ-4205194).

   * O aplicativo de desktop trava ao navegar em diretórios aninhados grandes (CQ-4208539).

   * O ponto de montagem do aplicativo de desktop agora é /Volumes/DAM, portanto, é consistente para todos os usuários (CQ-4208159).

   * Colocar o arquivo no InDesign pela primeira vez inicia um aviso de atualização (CQ-4207454).

Observação sobre avisos de link: os aplicativos Creative Cloud (como o InDesign) fazem um &quot;instantâneo&quot; da hora da última modificação do item no momento em que ele é colocado. Se essa data for alterada posteriormente, o aplicativo Adobe Creative Cloud relatará que os links estão desatualizados. Isso é relatado de duas maneiras:

* Quando o aplicativo Adobe Creative Cloud for iniciado, ele exibirá uma caixa de diálogo informando ao usuário que os ativos vinculados estão desatualizados e solicitará que o usuário tome uma ação.

* Se o aplicativo Adobe Creative Cloud já estiver em execução, ele mostrará um ícone de aviso de triângulo amarelo no ativo vinculado.

Esse comportamento é o mesmo para ativos no disco local e ativos em um diretório montado no AEM Desktop, com as seguintes exceções:

* Se um ativo inserido for modificado por um usuário diferente, o ícone de aviso será exibido na primeira vez que outros usuários abrirem um documento contendo o ativo inserido. Isso só acontecerá se o ativo inserido já tiver sido armazenado em cache localmente.

* Se um usuário modificar um ativo inserido por meio do diretório montado do desktop AEM e, em seguida, limpar o cache local, o ativo inserido será relatado como desatualizado.

Ambos os casos são esperados e são efeitos colaterais da arquitetura de &quot;sincronização atrasada&quot; do AEM Desktop.

**Versão 1.5.0.x para Mac OS X e Windows:** Essa versão do aplicativo para desktop AEM oferece os seguintes benefícios:

* Maior estabilidade e resiliência contra problemas de rede.

   * Mapeamento mais estável de pastas do AEM Assets (CQ-103276, CQ-4204669, CQ-4203957).

   * Melhor tratamento dos arquivos em cache (CQ-4204336, CQ-4206263).

   * Manuseio aprimorado de download/upload de arquivos grandes com mais de 2 GB (CQ-4206438).

   * Correção do &quot;Erro 36&quot; ao mover ou renomear um número maior de arquivos no Finder (CQ-4204640).

* Otimizações na comunicação de rede com o Servidor AEM (CQ-4204974, CQ-100903).

* Aprimoramento da confiabilidade de abrir, colocar e salvar ativos AEM em aplicativos Creative Cloud (CQ-4203968, CQ-4205511, CQ-103543, CQ-4207141, CQ-90980).

* Melhor capacidade de suporte: opção para limpar o cache (CQ-4202541), acesso fácil a registros (CQ-4202340, CQ-4204673).

* Outras correções:
   * Melhor suporte para ativos e pastas que têm caracteres japoneses nas configurações de nome/idioma diferentes do inglês (CQ-4195433, CQ-4205793, CQ-4199446).

   * Melhor manipulação do logon com SSL (CQ-4200217).

   * Montagem de compartilhamento mais confiável (CQ-4200793).

   * Várias melhorias na estabilidade (CQ-4207539, CQ-4200378).

   * Melhor manipulação do URL do AEM Assets em Preferências (CQ-97388).

### Melhorias disponíveis desde o aplicativo de desktop AEM 1.4 {#Enhancements-Available-Since-AEM-Desktop-App-14}

* Upload simplificado de pastas hierárquicas por meio da nova ação Criar > Fazer upload da pasta na interface para toque.
   * A ação inicia uma operação de carregamento de pasta realizada pelo aplicativo de desktop
   * O aplicativo de desktop percorre a hierarquia de pastas fornecida no desktop em segundo plano e faz upload dos arquivos para o AEM Assets
   * O usuário pode monitorar o progresso na nova janela Fazer upload do status da fila com a barra de progresso para operações em andamento
   * O Status da fila de uploads também fornece melhores informações de solução de problemas (por exemplo, sem conexão com o servidor)
* Nova ação Editar na interface para toque, que combina operações de Check-out e Abrir em uma
* Agrupamento otimizado de ações relacionadas ao desktop na interface para toque (AEM 6.3)
* Maior compatibilidade com as versões mais recentes do sistema operacional
* Correções relatadas pelo cliente

### Melhorias disponíveis desde o aplicativo de desktop AEM 1.3 {#Enhancements-Available-Since-AEM-Desktop-App-13}

* Maior eficiência. Os usuários gastam menos tempo aguardando a conclusão das operações de rede.
* Aprimoramento da integração do Localizador, que fornece mais estabilidade e acesso a recursos, como miniaturas.
* Armazenamento em cache e melhorias de desempenho.
* Melhor suporte para salvar diretamente de aplicativos de desktop (PS, ID, AI e assim por diante).
* Melhor integração com o Mac OS (protocolo de unidade de rede local alterado de WebDAV para SMB1 mais estável).
* O aplicativo de desktop se conecta com o servidor AEM usando o protocolo RESTful HTTP nativo AEM.
* Primeiro, os arquivos são salvos localmente e depois carregados de volta no AEM em segundo plano após um tempo predefinido (30 segundos). Isso reduz o tempo para salvar arquivos.
* Melhor manuseio de aplicativos de desktop que usam operações de arquivo intermediárias para salvar um arquivo (salvamentos parciais e arquivos temporários), o que permite que a linha do tempo do ativo AEM exiba as informações corretas de versão e upload de ativos.
* Caixa de diálogo fornecida para rastrear o status de tarefas de upload em segundo plano.

## Lista de alterações {#list-of-changes}

### Ponto de montagem no Mac {#mount-point-on-mac}

Desde o MacOS 10.12 (Sierra), a Apple alterou as permissões na pasta /Volumes usada para montar unidades de rede e dispositivos para serem mais restritas. A criação de um novo ponto de montagem exigia direitos administrativos. Este problema foi corrigido no MacOS 10.12.5.

Como o aplicativo de desktop AEM deve ser executado para usuários que não têm direitos de administrador no computador local, o ponto de montagem do repositório do AEM Assets foi alterado nas versões 1.4 e 1.5 para uma subpasta DAM na pasta local do usuário no MacOS (CQ-104183).

Como a pasta /Volumes não requer mais direitos administrativos, essa alteração foi revertida na versão 1.5.1. Isso também permite compartilhar documentos do InDesign que colocaram ativos AEM entre os usuários do MacOS.

### Alteração de protocolo (desde a v1.3) {#protocol-change-since}

* Mac OS X:
   * O protocolo de unidade de rede local para integração de desktop do OS X foi alterado para SMB1 a partir do WebDAV.
   * O repositório AEM montado com o aplicativo de desktop estará visível como uma unidade de rede &quot;smb&quot; no Finder, em vez de uma unidade WebDAV.
* Windows:
   * O protocolo de unidade de rede local para integrações de desktop do Windows permanece; o AEM será montado como um compartilhamento WebDAV.
* Para ambas as plataformas (Windows e Mac):
   * O protocolo para acessar/baixar ativos e fazer upload de alterações no AEM foi alterado para o protocolo AEM nativo, que é um protocolo RESTful baseado em HTTP. Ele oferece maior controle sobre as operações de rede e é mais compatível com a infraestrutura de rede.

>[!NOTE]
>
>No Mac OS X, a alteração do protocolo de unidade de rede local de WebDAV para SMB1 resulta em um caminho local diferente para o mesmo ativo no repositório. Isso pode afetar os links para arquivos colocados em aplicativos do Adobe Creative Cloud por meio do comando &quot;Inserir&quot;. Consulte a [Usar o aplicativo AEM Desktop](use-app-v1.md) para obter mais informações.

### Manuseio de arquivos (desde 1.3) {#file-handling-since}

* As pastas são atualizadas automaticamente após um atraso predefinido (atualmente 30s).
* Os arquivos submetidos a check-out por outros usuários são marcados como somente leitura.
* Os arquivos são salvos em um local de unidade de rede montado por meio de um aplicativo de desktop em duas fases.
* Na primeira fase, um arquivo é salvo localmente. Dessa forma, o usuário que salva o arquivo não precisa esperar até que ele seja totalmente transferido para o AEM e pode retomar o trabalho assim que o arquivo for salvo.
* Na segunda fase, o aplicativo de desktop carrega um arquivo atualizado no servidor AEM após um atraso predefinido (por exemplo, 30s ). Esta operação ocorre em segundo plano. Use o **Mostrar Status de Sincronização de Arquivos em Segundo Plano** opção para visualizar o status da operação de upload.

## Avisos importantes {#important-notices}

**Carregamento de pasta.** É recomendável usar o novo recurso Carregamento de pasta para fazer upload de pastas maiores e hierárquicas no AEM, em vez de usar uma cópia/arrastar e soltar em um repositório AEM montado no nível do Finder/Explorer. Ao usar o recurso de carregamento de pasta, o aplicativo de desktop se comunica diretamente com o AEM e, portanto, tem muito melhor controle sobre o processo geral.

**Mantenha a sessão do AEM disponível.** O aplicativo de desktop AEM depende de uma sessão aberta no servidor do AEM Assets para garantir a operação adequada. Para usuários que trabalham com aplicativos de desktop todos os dias, é recomendável desmontar o AEM Assets no final do dia para forçar o logout e, em seguida, &quot;montar o AEM Assets&quot; pela manhã para garantir que eles estejam conectados e o compartilhamento de rede esteja operacional.

**Desative &quot;Visualização de ícone&quot; no Finder.** Para a navegação eficiente de pastas grandes com o Finder, especialmente com baixa conectividade de rede, verifique se o &quot;Ícone&quot; e a &quot;Visualização de ícone&quot; estão desativados. Caso contrário, o Finder iniciará o download de cada ativo em uma pasta para gerar uma pequena visualização, o que pode resultar em baixo desempenho e alta utilização de largura de banda (CQ-4219779)

* No localizador, vá para a pasta de rede compartilhada da AEM Assets
* Clique com o botão direito do mouse no ponto de montagem do DAM
* Selecione Mostrar opções de exibição
* Desmarque &quot;Mostrar visualização do ícone&quot;
* Clique em &quot;Usar como padrão&quot;

**Limpar o cache ao conectar-se a um novo servidor AEM.** Se o aplicativo de desktop se conectar a outro servidor AEM com o mesmo URL, o cache não será limpo automaticamente. Limpe o cache manualmente para garantir as operações adequadas. Observe que isso normalmente ocorreria em testes, quando instalações de AEM podem ser substituídas enquanto são executadas no mesmo URL (CQ-4216982)

**Usar certificados SSL assinados pela CA.** Observe que o aplicativo de desktop AEM não é compatível com certificados SSL autoassinados ao se conectar ao AEM por meio de uma conexão segura HTTPS. É necessário um certificado assinado pela CA no servidor para essas conexões. (CQ-87941)

## Problemas conhecidos {#known-issues}

* Geral:
   * Os URLs do servidor são necessários para apontar para o servidor sem um caminho (por exemplo, `http://server`, `https://server`, `http://server:port`ou `https://server:port`). Não há suporte para caminhos e subpastas de contexto diferentes de /content/dam (CQ-89343, CQ-87272)
* Nomes/localização de arquivos:
   * Nomes de arquivos e pastas com caracteres reservados não são manipulados corretamente. Use os nomes de arquivos e pastas compatíveis com os requisitos de AEM (CQ-93361, CQ-93308, CQ-89276, CQ-4217183)
   * Alguns aplicativos, como o Adobe Illustrator, podem criar arquivos com nomes não compatíveis com AEM. Por exemplo, adicionar `Converted` após converter um arquivo, o que impede que ele seja carregado (CQ-4216985)
   * Ativos com nomes internacionais podem aparecer e desaparecer a cada poucos segundos
* Check-in e Check-out:
   * Um ativo retirado por um usuário não pode ser aberto por outro usuário, seja pela ação Abrir da interface do usuário de toque, ou diretamente no desktop. Alguns aplicativos podem relatá-lo como bloqueado, mas também corrompido ou até mesmo travar ao tentar abrir o. (CQ-4199234)
   * A alteração de arquivos simultaneamente por vários usuários pode causar a perda de algumas modificações. A solução alternativa é usar a funcionalidade de check-in e check-out para impedir que vários usuários alterem o mesmo arquivo (CQ-97035)
   * Certos aplicativos não oferecem suporte adequado ao sinalizador somente leitura, o que permite que um usuário salve um arquivo que foi submetido a check-out por outro usuário. O arquivo modificado não é transferido até que o outro usuário faça check-in do arquivo. Ambas as modificações estão disponíveis no AEM como versões diferentes do ativo (CQ-89551, CQ-87572, CQ-89615)
   * Os status de check-out e somente leitura são relatados de forma independente no Localizador. Isso resulta em dois ícones de bloqueio quando um usuário faz o check-out de um ativo (CQ-89507)
* Integração do localizador:
   * Ao arrastar/soltar arquivos grandes, o Finder pode atingir o tempo limite enquanto os arquivos estão sendo transferidos em segundo plano. Isso resulta em uma `Error - 36`. A solução alternativa é arrastar/soltar ou abrir o ativo novamente (CQ-4219628)
   * O recarregamento manual da pasta nem sempre funciona. Solução alternativa: aguarde 30s para que a pasta seja atualizada automaticamente. (CQ-97389)
   * Mais informações do ativo... estão limitadas a seleções de arquivos únicos (CQ-89542, CQ-87656)
   * Abrir no AEM Assets... é limitado a seleções de arquivos e pastas únicos (CQ-83382)
   * Erro ao renomear ativos que não têm extensão (CQ-4218971)
* Funcionalidade Copiar/Colar: a opção Colar está disponível quando nenhum ativo foi copiado para a área de transferência
* Windows:
   * Arquivos com Fluxos de Dados Alternativos (ADS) só são totalmente compatíveis com o NTFS. Copiar esses arquivos para o compartilhamento WebDAV fornecido pelo aplicativo de desktop resultará em uma caixa de diálogo de aviso de cuidado, avisando o usuário de que o arquivo tem propriedades que não podem ser copiadas para o novo local. Isso geralmente é bom, pois as propriedades são relevantes apenas para um aplicativo específico no desktop do usuário e não têm nada a ver com o conteúdo real do arquivo (CQ-103770) (Win)
   * o aplicativo de desktop no Windows precisa ser instalado pelo usuário que o usará (CQ-4216389) (win)
   * O aplicativo pode falhar ao selecionar o [!UICONTROL Retry] opção em um upload com falha em determinadas circunstâncias após ter retomado o upload em lote quando desconectado (CQ-4251884) (Win)

## Recursos úteis {#helpful-resources}

* [Documentação do AEM](https://experienceleague.adobe.com/docs/)
* [Usar o aplicativo para desktop AEM v1.x](use-app-v1.md)
* [Práticas recomendadas do aplicativo para desktop AEM v1.x](best-practices-for-v1.md)

## Matriz de compatibilidade e pré-requisitos {#compatibilitymatrix}

O aplicativo de desktop AEM funciona com várias versões do AEM. Consulte a matriz de compatibilidade para obter as versões compatíveis.

| Versão | Revisão | Data de lançamento | Compatibilidade |
|--- |--- |--- |--- |
| 1.10 | 1.10.0.3 (Mac e Win) | 31 de agosto de 2018 | AEM 6.5; AEM 6.4 SP1; AEM 6.3 SP2; AEM AEM 6.2 SP1 CFP2+; 6.1 SP2 CFP7+ |
| 1.9 | 1.9.1.1 (Mac e Win) | 21 de junho de 2018 | AEM 6.4; AEM 6.3 SP1; AEM AEM 6.2 SP1 CFP2+; 6.1 SP2 CFP7+ |
| 1.8 | 1.8.1.0 (Mac e Win) | 28 de março de 2018 | AEM 6.4; AEM 6.3 SP1; AEM AEM 6.2 SP1 CFP2+; 6.1 SP2 CFP7+ |
| 1.7 | 1.7.0.3 (Mac e Win) | 10 de janeiro de 2018 | AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
