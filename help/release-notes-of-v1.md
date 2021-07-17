---
title: Notas de versão do aplicativo de desktop v1.10
description: Detalhes da versão, melhorias, novos recursos, compatibilidade e links de download para AEM aplicativo de desktop versão 1.10.
exl-id: 886864e0-016a-4a17-b3ba-4b18a514214a
source-git-commit: 32aff5d66f2cb67ab4bb440d7ace747a5cf1dd26
workflow-type: tm+mt
source-wordcount: '3898'
ht-degree: 1%

---

# [!DNL Adobe Experience Manager] notas de versão do aplicativo de desktop v1.10 {#aem-desktop-app-release-notes}

Para o aplicativo de desktop versão v1.x, veja a seguir os links de download e AEM informações de compatibilidade.

| Produtos | Aplicativo de desktop do [!DNL Adobe Experience Manager]  |
|--- |--- |
| Versão | 1.10 (1.10.0.6 no Mac e 1.10.0.3 no Windows) |
| Tipo | Versão secundária |
| Data | 1.10.0.6 (Mac): 15 de abril de 2020; 1.10.0.3 (Win): 31 de agosto de 2018 |
| URLs para download | [Mac OS X 64 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-1.10.0.6.dmg);  [Windows 32 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-1.10.0.3.exe);  [Windows de 64 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-1.10.0.3.exe) |
| Compatibilidade | AEM 6.5.x; AEM 6.4.x; AEM 6.3 SP2; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |

>[!NOTE]
>
>O limite de tamanho de cache não é aplicado. Quando o aplicativo de desktop é iniciado, o tamanho do cache é calculado uma vez e uma notificação é exibida se o tamanho estiver próximo ao limite predefinido.

## Requisitos e pré-requisitos do sistema {#system-requirements-and-prerequisites}

[!DNL Adobe Experience Manager]O aplicativo de desktop do é compatível com os seguintes sistemas operacionais:

* Mac OS X 10.10 ou mais recente, com as correções de erros mais recentes.

* Windows 10 com os service packs e correções de erros mais recentes.

>[!NOTE]
>
>O Windows 7 não é mais suportado. Consulte [o artigo sobre EOL do Windows 7](https://support.microsoft.com/en-us/help/4057281/windows-7-support-ended-on-january-14-2020).

A Adobe recomenda utilizar a versão mais recente do aplicativo de desktop AEM para aproveitar os recursos mais recentes, as correções de erros mais recentes e o melhor desempenho possível.

A versão do AEM aplicativo de desktop que você pretende instalar no computador local requer uma versão específica AEM servidor/componentes adicionais do lado do servidor (service packs, hot fixes ou pacotes de recursos). Certifique-se de que o servidor de AEM esteja configurado corretamente antes de se conectar a ele pela primeira vez. Se precisar de ajuda, entre em contato com o administrador do AEM.

Consulte a [matriz de compatibilidade detalhada](#compatibilitymatrix) no final deste documento para avaliar os pré-requisitos para sua configuração.

## Novidades no aplicativo de desktop v1.10 {#what-s-new-in-aem-desktop-app}

AEM aplicativo de desktop 1.10 tem como foco melhorar a experiência do usuário em grandes uploads, informações sobre as operações em segundo plano e experiência otimizada ao abrir ativos com arquivos vinculados (como o InDesign).

>[!NOTE]
>
>Se você estiver usando o macOS 10.15.4 ou posterior, use pelo menos a versão 1.10.0.6 do aplicativo. Esta versão de patch está em conformidade com [Requisitos de notarização da Apple](https://developer.apple.com/news/?id=04102019a).

**Edição/Check-out** Local: Os uploads automáticos de alterações salvas em ativos podem ser desativados na janela de status. Dessa forma, o usuário pode continuar trabalhando nos arquivos e salvando as alterações e, quando estiver pronto, decidir fazer upload de todas as alterações.

**Janela** Status do ativo simplificado. A janela de status foi simplificada. A guia [!UICONTROL Uploads] agora mostra ambos os ativos individuais, bem como uploads de pasta ou em massa. A guia Uploads em massa anterior foi removida.

**Ícone de aplicativo para indicar uploads em massa**. O ícone do aplicativo indica que um upload em massa está em andamento ao mostrar uma sobreposição de &quot;transferência&quot;.

**Notificações para conflito de atualização**. Quando o aplicativo detecta um conflito ao tentar atualizar um ativo, ele mostra uma notificação para que o usuário possa revisar isso sem a necessidade de monitorar a janela de status. Quando o aplicativo for iniciado, ele verificará todos os conflitos, para que o usuário possa resolvê-los.

**Melhor tratamento das perdas de conexão**. Os uploads em massa serão pausados se houver perda de conexão e o usuário poderá retomar mais tarde. Uma opção [!UICONTROL Retry] está disponível para tentar novamente um upload com falha de um arquivo individual.

## Instruções de instalação {#installation-instructions}

Para obter instruções detalhadas, consulte [Instalar e configurar AEM aplicativo de desktop](install-configure-app-v1.md).

## Melhorias nas versões anteriores {#enhancements-in-the-previous-versions}

Esta versão estende e substitui as versões anteriores do [!DNL Experience Manager] aplicativo de desktop, que forneceu os seguintes aprimoramentos principais:

* **Versão 1.9/1.9.1**: uploads retomáveis, janela de status aprimorada, ícones de aplicativo que indicam o status do aplicativo / conexão, pré-busca de ativos vinculados para arquivos de InDesign.

* **Versão 1.8**: melhor controle do tamanho do cache para o usuário, melhor experiência de logon para SAML/SSO no Windows, suporte ao proxy de rede .pac no Mac e problemas relatados pelo cliente.

* **Versão 1.7**: melhorias na estabilidade e na lógica de armazenamento em cache, melhor suporte para proxy de rede e capacidade de limpar arquivos internos após a desinstalação.

* **Versão 1.6**: melhorias no processo de logon para várias configurações de segurança AEM e estabilidade e desempenho do aplicativo.

* **Versão 1.5**: estabilidade de aplicativos e resiliência contra vários problemas de rede, melhor suporte.

* **Versão 1.4**: a capacidade de fazer upload de pastas hierárquicas em segundo plano com o monitoramento do progresso.

* **Versão 1.3**: aprimoramentos de desempenho e estabilidade de acesso a arquivos e salvamento de alterações em AEM, especialmente em aplicativos de desktop Creative Cloud, como InDesign, Illustrator ou Photoshop. O objetivo era fornecer aos usuários uma experiência mais semelhante à de um desktop local ao trabalhar com arquivos, ao mesmo tempo em que lidava com operações de transferência de dados de rede em segundo plano.

### Melhorias disponíveis desde AEM aplicativo de desktop 1.9 {#Enhancements-Available-Since-AEM-Desktop-App-19x}

[!DNL Adobe Experience Manager] o aplicativo de desktop 1.9.1 era uma versão de patch para solucionar alguns problemas principais do cliente com relação à finalização de ativos e à cópia de arquivos do compartilhamento de rede para um diretório local.

* Os ativos com check-out feito por um usuário não devem estar disponíveis para modificação para outros usuários (CQ-4246009)

* Cópia de suporte da pasta mapeada para uma pasta local quando a pasta do usuário está em uma partição de disco separada (CQ-4243978)

AEM aplicativo de desktop 1.9 focado na melhoria da experiência do usuário em grandes uploads, informações sobre as operações em segundo plano e experiência otimizada ao abrir ativos com arquivos vinculados (como o InDesign).

**Uploads**
retomáveisPara uploads, especialmente em torno de arquivos grandes, há uma opção para pausá-los/retomá-los na nova janela Status do ativo.

****
Janela Status do Ativo MelhoradoUma janela de status de ativo aprimorada fornece as seguintes informações sobre ativos.

[!UICONTROL Changes]

* Exibe as alterações na fila no momento.

* Mostra os uploads em andamento, incluindo uma barra de progresso, taxa de transferência, tamanho total do arquivo e tamanho transferido até o momento.

* Uploads concluídos mostrados com o total transferido e a taxa final.

* Os uploads com falha são exibidos junto com uma mensagem de erro e informações de transferência, se disponíveis.

* Uploads que falharam 3 vezes mostrarão uma mensagem de erro.

* Arquivos em conflito exibidos com um ícone em que o usuário pode clicar. Clicar no ícone mostra uma caixa de diálogo com uma explicação e duas opções:

   * [!UICONTROL Keep Mine] O carrega imediatamente o arquivo no servidor.

   * [!UICONTROL Overwrite Mine] O exclui imediatamente o arquivo local e baixa uma nova cópia do servidor.

[!UICONTROL Downloads]

* Exibe downloads em andamento, incluindo taxa de transferência e tamanho transferido até o momento.

* Downloads concluídos mostrados com o total transferido, taxa final e um ícone que abrirá o arquivo quando clicado (disponível somente para arquivos únicos).

* Falhas nos downloads exibidos com uma mensagem de erro e informações de transferência, se disponíveis.

* O rodapé mostra o número total de arquivos baixados e a taxa média de transferência.

* Se um usuário optar por abrir ou editar vários arquivos na interface da Web [!DNL Experience Manager Assets], eles serão agrupados. Por exemplo, myasset.jpeg e mais 4 arquivos.

* Ao baixar os Documentos do InDesign, incluindo ativos vinculados armazenados no AEM Assets, o aplicativo de desktop baixará todos os Ativos vinculados primeiro, antes de abrir o documento [!UICONTROL Adobe InDesign] e indicará o download dos ativos vinculados. Por exemplo, 5 de 24.

[!UICONTROL Bulk Uploads]

Fazer upload de hierarquias de pastas grandes via [!UICONTROL Create] > [!UICONTROL Upload Folder] AEM interface do usuário da Web ou copiar e selecionar &quot;Colar ativos&quot; no Finder ou no Explorer no menu de contexto do aplicativo de desktop acionará o uso dessa caixa de diálogo.

* Exibe os uploads em andamento, incluindo uma barra de progresso e o nome do arquivo que está sendo transferido no momento.

* Os uploads em andamento incluem um ícone que cancelará o upload quando clicado. A transferência será interrompida após a conclusão do arquivo de transferência no momento.

* Os processos de transferência com falha são exibidos com uma mensagem de erro (somente se a transferência inteira falhar).

* Se um arquivo individual não for transferido, ele será exibido na guia como um erro. Caso contrário, os arquivos individuais não serão exibidos na guia * somente em uma única entrada para todo o upload.

**Ícones para indicar o status das operações em segundo plano**

O ícone de aplicativo indicará o estado das operações em segundo plano para fornecer uma melhor dica visual aos usuários. Por exemplo, quando o aplicativo não está conectado ao AEM, o ícone fica esmaecido, quando há um upload ativo, ele mostra uma sobreposição &quot;síncrona&quot; etc.

**Pré-busca de ativos vinculados**

Para melhorar a experiência do usuário ao trabalhar com documentos do InDesign que incluem ativos vinculados armazenados em AEM, o aplicativo de desktop tentará realizar uma busca prévia desses arquivos vinculados no cache local antes de baixar e abrir o documento do InDesign. Dessa forma, o usuário terá os arquivos vinculados disponíveis localmente e não precisará aguardar mais ao acessá-los no InDesign (no painel Links ).
Observe que a busca prévia só funciona se o AEM reconhecer os links no lado do servidor. Um ativo com links reconhecidos terá uma lista de &quot;Referências&quot; listada na exibição Propriedades do ativo do InDesign.

### Aprimoramentos disponíveis desde AEM aplicativo de desktop 1.8.x {#enhancements-available-since-aem-desktop-app-18x}

AEM aplicativo de desktop versão 1.8.1 de sequência rápida adicionou melhorias ao abrir vários arquivos de uma só vez da interface do usuário AEM à versão 1.8 (CQ-4237747, CQ-4238780). As melhorias no aplicativo de desktop AEM 1.8 são:

* Armazenamento em cache: nova interface do usuário para gerenciar AEM cache de aplicativos de desktop (CQ-4208690), incluindo,

   * exibir o tamanho atual do cache

   * definir o tamanho máximo do cache antes do envio de uma notificação

   * O tamanho do cache é verificado apenas na inicialização do aplicativo de desktop, e uma notificação é exibida se ele estiver atingindo o limite configurado

   * o botão limpar cache agora está disponível na nova interface do usuário

* Logon: (Win) Corrigido o logon em AEM instância configurada para usar SAML e SSL (CQ-4216353)

* Rede:

   * quando uma sessão de AEM expira, o usuário é notificado e pode clicar na notificação para fazer logon novamente (CQ-4202028).

   * (Mac) Adicione suporte para conexão com o AEM usando a configuração de proxy .pac (CQ-4233430).

   * (Win) corrija problemas com a caixa de diálogo Avançado - URL de logon (CQ-4236061).

* Correções de bugs:

   * Caixa de diálogo Mais informações do ativo: às vezes, a barra de ação não estava visível (CQ-4208540).

   * (Win) O arquivo agora pode ser sincronizado após reverter para uma versão anterior da interface do usuário do AEM Assets (CQ-4216411).

### Melhorias disponíveis desde AEM aplicativo de desktop 1.7 {#Enhancements-Available-Since-AEM-Desktop-App-17}

* Estabilidade:

   * Melhora da estabilidade quando AEM aplicativo de desktop se conecta a um servidor de AEM sobrecarregado (CQ-4224803).

   * Melhora da estabilidade quando vários arquivos são solicitados (CQ-4224212).

   * Atualização de ativos aprimorada com verificação adicional (CQ-4228291).

* Armazenamento em cache:

   * Correção de erros de disco e problemas de abertura ao abrir arquivos no Photoshop, InDesign, Finder (CQ-4223993, CQ-4217603, CQ-4223717).

   * Melhoria no cache para evitar binários de tamanho zero (CQ-4216599).

* Logon: Permitir conexão com o stricto sensu desativado para configurações especiais (como certificados emitidos localmente) (CQ-4223949).

* Rede: Suporte aprimorado para conexão por proxy de rede (CQ-4223477, CQ-4221280, CQ-4206854).

* Instalação e desinstalação:

   * (Win) Desinstalação do Cleaner (CQ-4220906).

   * [O Windows 32] bitInstaller falha ao tentar instalar o Microsoft .NET Framework v. 4.5 (CQ-4218084).

   * (Mac) Script manual para remover arquivos de aplicativo de desktop completamente (CQ-4216489).

>[!NOTE]
>
>Problemas encontrados AEM cargas beta 1.7 do aplicativo de desktop (que não estavam presentes na versão 1.6 não são relatados nas notas de versão).

### Aprimoramentos disponíveis desde AEM aplicativo de desktop 1.6 {#Enhancements-Available-Since-AEM-Desktop-App-16}

* Documentação: Nova documentação [Práticas recomendadas para o aplicativo v1.x](/help/best-practices-for-v1.md) .

* Melhoria no processo de logon para AEM:

   * Melhore o manuseio de SAML * regras de relaxamento (CQ-4202781).

   * Adicione a capacidade de configurar um URL de logon separado em Preferências (CQ-4214052, CQ-4214051).

* Usabilidade: Notifique o usuário quando o ativo ainda estiver baixando para ativos maiores (CQ-4216284).

* Rede:

   * Armazenamento em cache DNS (CQ-4210176).

   * Conexão de suporte via proxy no Windows (CQ-4206854).

* Armazenamento em cache e acesso ao compartilhamento de rede no Finder / Explorer:

   * O ícone Bloquear agora está visível para ativos com check-out no Windows 10 (CQ-90957).

   * O conteúdo da pasta pode desaparecer/reaparecer no compartilhamento de rede (CQ-4209160, CQ-4210180).

   * Erro no upload do arquivo devido a um conflito relatado no Status da fila de upload (CQ-4215727).

   * Ao abrir vários arquivos da pasta de aplicativo de desktop no PS, mensagens de arquivo truncadas ou incompletas podem ser exibidas (CQ-4216276).

* Correções na estabilidade e desempenho:

   * Desempenho aprimorado ao navegar pelas pastas com muitos ativos (CQ-4214933).

   * o aplicativo de desktop 1.5 pode desacelerar a máquina de desktop ao longo do tempo (CQ-4209159).

   * Mostrar recurso de status da fila funciona somente para o usuário que instalou o aplicativo (CQ-4212199).

   * (Windows) Certifique-se de que o instalador de 32 bits não contenha o código de 64 bits (CQ-4217406).

* Problemas selecionados encontrados e corrigidos em 1.6 Beta:

   * Alto uso de CPU (CQ-4218070).

   * Arraste e solte arquivos gerando um erro ao fazer upload para o AEM (CQ-4217006).

### Melhorias disponíveis desde AEM aplicativo de desktop 1.5 {#Enhancements-Available-Since-AEM-Desktop-App-15}

**Versão 1.5.1.5 para Mac OS X:** a versão 1.5.1.5 fornece os seguintes benefícios:

* Novos recursos e melhorias: Adicione a funcionalidade Copiar/Colar à integração do Finder para permitir a transferência direta do Desktop para o AEM (CQ-4208158).

* Correções de erros:

   * Correção do problema 43 que ocorria algumas vezes durante a renomeação de ativos (CQ-4207900).

   * Reverter para uma versão mais antiga a partir da linha do tempo no AEM não atualiza o ativo no Finder (CQ-4205194).

   * o aplicativo de desktop falha ao navegar por diretórios aninhados grandes (CQ-4208539).

   * o ponto de montagem do aplicativo de desktop agora é /Volumes/DAM, portanto, é consistente para todos os usuários (CQ-4208159).

   * Colocar arquivo no InDesign pela primeira vez inicia um aviso de atualização (CQ-4207454).

Observação sobre avisos de link: Os aplicativos Creative Cloud (como o InDesign) tiram um &quot;instantâneo&quot; da hora da última modificação do item no momento em que ele é colocado. Se essa data for alterada posteriormente, o aplicativo Adobe Creative Cloud reportará que os links estão desatualizados. Isso é relatado de algumas maneiras:

* Quando o aplicativo Adobe Creative Cloud for iniciado, uma caixa de diálogo será exibida informando ao usuário que os ativos vinculados estão desatualizados e solicitará que ele execute uma ação.

* Se o aplicativo Adobe Creative Cloud já estiver em execução, ele mostrará um ícone de aviso de triângulo amarelo no ativo vinculado.

Esse comportamento é o mesmo para ativos em disco local e ativos em um diretório montado na área de trabalho AEM, com as seguintes exceções:

* Se um ativo colocado for modificado por um usuário diferente, o ícone de aviso será exibido na primeira vez que outros usuários abrirem um documento contendo o ativo colocado. Isso só acontecerá se o ativo colocado já tiver sido armazenado em cache localmente.

* Se um usuário modificar um ativo colocado por meio do diretório montado AEM desktop e, em seguida, limpar o cache local, o ativo colocado será relatado como desatualizado.

Ambos os casos são esperados e são efeitos colaterais da arquitetura de &quot;sincronização tardia&quot; do AEM Desktop.

**Versão 1.5.0.x para Mac OS X e Windows:** essa versão do aplicativo de desktop AEM fornece os seguintes benefícios:

* Melhor estabilidade e resiliência contra problemas de rede.

   * Mapeamento mais estável de pastas do AEM Assets (CQ-103276, CQ-4204669, CQ-4203957).

   * Melhor tratamento de arquivos em cache (CQ-4204336, CQ-4206263).

   * Melhoria na manipulação do download/upload de arquivos grandes com mais de 2 GB de tamanho (CQ-4206438).

   * Correção do &quot;Erro 36&quot; ao mover ou renomear um número maior de arquivos no Finder (CQ-4204640).

* Otimizações na comunicação de rede com o AEM Server (CQ-4204974, CQ-100903).

* Melhoria na confiabilidade de abrir, colocar e salvar ativos AEM em aplicativos Creative Cloud (CQ-4203968, CQ-4205511, CQ-103543, CQ-4207141, CQ-90980).

* Suporte aprimorado: opção para limpar o cache (CQ-4202541), acesso fácil a logs (CQ-4202340, CQ-4204673).

* Outras correções:
   * Melhor suporte para ativos e pastas com caracteres japoneses nas configurações de nome/idioma diferente do inglês (CQ-4195433, CQ-4205793, CQ-4199446).

   * Melhor tratamento do logon com SSL (CQ-4200217).

   * Montagem de compartilhamento mais confiável (CQ-4200793).

   * Várias melhorias na estabilidade (CQ-4207539, CQ-4200378).

   * Melhor tratamento do URL do AEM Assets em Preferências (CQ-97388).

### Melhorias disponíveis desde AEM aplicativo de desktop 1.4 {#Enhancements-Available-Since-AEM-Desktop-App-14}

* O upload de pastas hierárquicas foi simplificado por meio da nova ação Criar > Fazer upload da pasta na interface do usuário de toque.
   * A ação inicia uma operação de upload de pasta realizada pelo aplicativo de desktop
   * O aplicativo de desktop atravessa a hierarquia de pastas específica no desktop em segundo plano e faz o upload dos arquivos para o AEM Assets
   * O usuário pode monitorar o progresso na nova janela Upload Queue Status com a barra de progresso para operações em andamento
   * O Status da fila de upload também fornece informações de solução de problemas melhores (por exemplo, sem conexão com o servidor)
* Nova ação Editar na interface do usuário de toque, que combina as operações Verificar e Abrir em uma única
* Agrupamento otimizado de ações relacionadas ao desktop na interface do usuário de toque (AEM 6.3)
* Compatibilidade aprimorada com as versões mais recentes do sistema operacional
* Correções relatadas pelo cliente

### Melhorias disponíveis desde AEM aplicativo de desktop 1.3 {#Enhancements-Available-Since-AEM-Desktop-App-13}

* Maior eficiência. Os usuários gastam menos tempo aguardando a conclusão das operações de rede.
* Integração do Finder aprimorada, que oferece mais estabilidade e acesso a recursos, como miniaturas.
* Melhorias no armazenamento em cache e no desempenho.
* Melhor suporte para salvar diretamente de aplicativos de desktop (PS, ID, AI e assim por diante).
* Integração aprimorada com o Mac OS (protocolo de unidade de rede local alterado de WebDAV para SMB1 mais estável).
* O aplicativo de desktop se conecta com o servidor de AEM usando AEM protocolo HTTP RESTful nativo.
* Os arquivos são salvos localmente primeiro e, em seguida, carregados de volta para o AEM em segundo plano após um tempo predefinido (30 segundos). Isso reduz o tempo para salvar arquivos.
* Melhor manipulação de aplicativos de desktop que usam operações intermediárias de arquivos para salvar um arquivo (salvamentos parciais e arquivos temporários), o que permite que a linha do tempo do AEM Asset exiba informações corretas de versão e upload de ativos.
* Caixa de diálogo fornecida para rastrear o status das tarefas de upload em segundo plano.

## Lista de alterações {#list-of-changes}

### Ponto de montagem no Mac {#mount-point-on-mac}

Desde o MacOS 10.12 (Sierra), a Apple alterou as permissões na pasta /Volumes usada para montar unidades de rede e dispositivos para torná-los mais restritivos. A criação de um novo ponto de montagem exigia direitos administrativos. Esse problema foi corrigido no MacOS 10.12.5.

Como AEM aplicativo de desktop deve ser executado para usuários que não têm direitos de administrador na máquina local, o ponto de montagem do repositório AEM Assets foi alterado em 1.4 e 1.5 para uma subpasta DAM na pasta local do usuário no MacOS (CQ-104183).

Como a pasta /Volumes não requer mais direitos administrativos, essa alteração foi revertida na versão 1.5.1. Isso também possibilita o compartilhamento de documentos do InDesign que colocaram AEM ativos entre usuários do MacOS.

### Alteração de protocolo (desde v1.3) {#protocol-change-since}

* Mac OS X:
   * O protocolo de unidade de rede local para integração de desktop OS X foi alterado para SMB1 de WebDAV.
   * O repositório AEM montado com o aplicativo de desktop será visível como uma unidade de rede &quot;smb&quot; no Finder, em vez de uma unidade WebDAV.
* Windows:
   * O protocolo de unidade de rede local para integrações de desktop do Windows permanece; AEM será montado como um compartilhamento WebDAV.
* Para ambas as plataformas (Windows e Mac):
   * O protocolo para acessar/baixar ativos e fazer upload de alterações no AEM foi alterado para o protocolo AEM nativo, que é um protocolo RESTful baseado em HTTP. Ele oferece maior controle sobre as operações de rede e é mais compatível com a infraestrutura de rede.

>[!NOTE]
>
>No Mac OS X, a alteração do protocolo da unidade de rede local de WebDAV para SMB1 resulta em um caminho local diferente para o mesmo ativo no repositório. Isso pode afetar links para arquivos colocados em aplicativos Adobe Creative Cloud por meio do comando &quot;Inserir&quot;. Consulte o [Use AEM Desktop app](use-app-v1.md) para obter mais informações.

### Manuseio de arquivo (desde 1.3) {#file-handling-since}

* As pastas são atualizadas automaticamente após um atraso predefinido (atualmente, 30s).
* Os arquivos com check-out feito por outros usuários são marcados como somente leitura.
* Os arquivos são salvos em um local da unidade de rede montado pelo aplicativo de desktop em duas fases.
* Na primeira fase, um arquivo é salvo localmente. Dessa forma, o usuário que salva o arquivo não precisa aguardar até que ele seja totalmente transferido para o AEM e pode retomar o trabalho assim que o arquivo for salvo.
* Na segunda fase, o aplicativo de desktop faz upload de um arquivo atualizado para AEM servidor após um atraso predefinido (por exemplo, 30s ). Essa operação ocorre em segundo plano. Use a opção **Mostrar Status de Sincronização do Arquivo de Plano de Fundo** para visualizar o status da operação de upload.

## Avisos importantes {#important-notices}

**Upload de pasta.** É recomendável usar o novo recurso de Upload de pasta para fazer upload de pastas maiores e hierárquicas em AEM em vez de usar copiar/arrastar e soltar em um repositório AEM montado no nível do Localizador / Explorer. Ao usar o recurso de upload de pasta, o aplicativo de desktop se comunica diretamente com o AEM e, portanto, tem muito melhor controle sobre o processo geral.

**Mantenha AEM sessão disponível.** AEM aplicativo de desktop depende de uma sessão aberta ao servidor AEM Assets para garantir a operação correta. Para usuários que trabalham com aplicativos de desktop todos os dias, é recomendável desmontar o AEM Assets no fim do dia para forçar o logoff e, em seguida, &quot;Montar AEM Assets&quot; pela manhã, para garantir que eles estejam conectados e que o compartilhamento de rede esteja operacional.

**Desative &quot;Visualização de ícone&quot; no Localizador.** Para uma navegação de alto desempenho de pastas grandes com o Finder, especialmente com baixa conectividade de rede, certifique-se de que tanto &quot;Ícone&quot; quanto &quot;Visualização de ícone&quot; estejam desligados. Caso contrário, o Finder iniciará o download de cada ativo em uma pasta para gerar uma visualização pequena, o que pode levar a um desempenho insatisfatório e à utilização de alta largura de banda (CQ-4219779)

* No Localizador, vá para a pasta de rede compartilhada da AEM Assets
* Clique com o botão direito no ponto de montagem do DAM
* Selecionar Mostrar opções de exibição
* Desmarque &quot;Mostrar visualização do ícone&quot;
* Clique em &quot;Usar como padrão&quot;

**Limpe o cache ao se conectar a um novo servidor de AEM.** Se o aplicativo de desktop se conecta a outro servidor de AEM com o mesmo URL, o cache não é limpo automaticamente. Limpe o cache manualmente para garantir as operações adequadas. Observe que isso normalmente acontece em testes, quando AEM instalações podem ser substituídas durante a execução no mesmo URL (CQ-4216982)

**Use certificados SSL assinados por CA.** Observe que AEM aplicativo de desktop não suporta certificados SSL autoassinados ao se conectar ao AEM por uma conexão segura HTTPS. Um certificado assinado por CA é necessário no servidor para essas conexões. (CQ-87941)

## Problemas conhecidos {#known-issues}

* Geral:
   * Os URLs do servidor são necessários para apontar para o servidor sem um caminho (por exemplo, `http://server`, `https://server`, `http://server:port` ou `https://server:port`). Caminhos e subpastas de contexto diferentes de /content/dam não são compatíveis (CQ-89343, CQ-87272)
* Nomes de arquivo/localização:
   * Os nomes de arquivo e pasta com caracteres reservados não são manipulados adequadamente. Certifique-se de usar os nomes de arquivo e pasta que se encaixam AEM requisitos (CQ-93361, CQ-93308, CQ-89276, CQ-4217183)
   * Alguns aplicativos como o Adobe Illustrator podem criar arquivos com nomes não suportados no AEM. Por exemplo, adicionar `Converted` após a conversão de um arquivo, o que impede que ele seja carregado (CQ-4216985)
   * Ativos com nomes internacionais podem aparecer e desaparecer a cada poucos segundos
* Check-in e Check-out:
   * Um ativo com check-out feito por um usuário não é possível abrir para outro usuário, por meio da ação Abrir da interface do usuário de toque ou diretamente na área de trabalho. Alguns aplicativos podem informá-lo como bloqueado, mas também corrompido ou suspenso ao tentar abrir. (CQ-4199234)
   * Alterar arquivos simultaneamente por vários usuários pode fazer com que algumas modificações sejam perdidas. A solução é usar a funcionalidade de check-in e check-out para impedir que vários usuários alterem o mesmo arquivo (CQ-97035)
   * Determinados aplicativos não oferecem suporte ao sinalizador somente leitura corretamente, o que permite que um usuário salve um arquivo que foi tirado do check-out por outro usuário. O arquivo modificado não é transferido até que o outro usuário faça o check-in do arquivo. Ambas as modificações estão disponíveis no AEM como diferentes versões do ativo (CQ-89551, CQ-87572, CQ-89615)
   * O status de check-out e somente leitura é relatado de maneira independente no Finder. Isso resulta em 2 ícones de bloqueio quando um usuário faz o check-out de um ativo (CQ-89507)
* Integração do localizador:
   * Ao arrastar/soltar arquivos grandes, o Finder pode expirar enquanto os arquivos são transferidos em segundo plano. Isso resulta em um `Error - 36`. A solução alternativa é arrastar/soltar ou abrir o ativo novamente (CQ-4219628)
   * O recarregamento manual de pasta nem sempre funciona. Solução alternativa:  wait   30s para a pasta ser atualizada automaticamente. (CQ-97389)
   * Mais informações do ativo... está limitado a seleções de arquivo único (CQ-89542, CQ-87656)
   * Abrir no AEM Assets... é limitado a seleções de arquivo único e de pasta (CQ-83382)
   * Erro ao renomear ativos que não têm extensão (CQ-4218971)
* Funcionalidade Copiar/Colar: Colar está disponível quando nenhum ativo foi copiado para a área de transferência
* Windows:
   * Arquivos com fluxos de dados alternativos (ADS) só são totalmente compatíveis com o NTFS. Copiar esses arquivos para o compartilhamento WebDAV fornecido pelo aplicativo de desktop resultará em uma caixa de diálogo de cuidado avisando o usuário que o arquivo tem propriedades que não podem ser copiadas para o novo local. Isso geralmente é bom, pois as propriedades são relevantes apenas para um aplicativo específico na área de trabalho do usuário e não têm nada a ver com o conteúdo real do arquivo (CQ-103770) (Win)
   * o aplicativo de desktop no Windows precisa ser instalado pelo usuário que o usará (CQ-4216389) (win)
   * O aplicativo pode falhar ao selecionar a opção [!UICONTROL Retry] em um upload com falha em determinadas circunstâncias após ter retomado o upload em lote quando desconectado (CQ-4251884) (Win)

## Recursos úteis {#helpful-resources}

* [Documentação AEM](https://experienceleague.adobe.com/docs/)
* [Usar AEM aplicativo de desktop v1.x](use-app-v1.md)
* [Práticas recomendadas do aplicativo de desktop do AEM v1.x](best-practices-for-v1.md)

## Matriz de compatibilidade e pré-requisitos {#compatibilitymatrix}

AEM aplicativo de desktop funciona com várias versões do AEM. Consulte a matriz de compatibilidade para as versões compatíveis.

| Versão | Revisão | Data de lançamento | Compatibilidade |
|--- |--- |--- |--- |
| 1,10 | 1.10.0.3 (Mac e Win) | 31 de agosto de 2018 | AEM 6.5; AEM 6.4 SP1; AEM 6.3 SP2; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1,9 | 1.9.1.1 (Mac e Win) | 21 de junho de 2018 | AEM 6.4; AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1,8 | 1.8.1.0 (Mac e Win) | 28 de março de 2018 | AEM 6.4; AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1,7 | 1.7.0.3 (Mac e Win) | 10 de janeiro de 2018 | AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
