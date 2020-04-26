---
title: Notas de versão do aplicativo para desktop AEM para a versão 1.x
description: Detalhes da versão, melhorias, novos recursos, compatibilidade e links de download para o aplicativo de desktop AEM versão 1.x.
uuid: b783c3f8-aa1e-4c05-b687-5894909769f5
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 3052549b-fe75-44fb-a55e-5cc612868f54
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b92e47456f9e16c24eac43d1c5fef9a582f143b5

---


# Notas de versão do aplicativo de desktop AEM v1.x {#aem-desktop-app-release-notes}

Para o aplicativo de desktop versão v1.x, veja a seguir os links de download e as informações de compatibilidade do AEM.

| Produtos | Aplicativo de desktop do Adobe Experience Manager (AEM) |
|---------------|--------------------------------------------------------------------|
| Versão | 1.10 (1.10.0.6 no Mac e 1.10.0.3 no Windows) |
| Tipo | Versão secundária |
| Data | 1.10.0.6 (Mac): 15 de abril de 2020; 1.10.0.3 (Win): 31 de agosto de 2018 |
| URLs para download | [Mac OS X 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-osx-1.10.0.6.dmg); 32 [bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win32-1.10.0.3.exe)do Windows; [Windows 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win64-1.10.0.3.exe) |
| Compatibilidade | AEM 6.5.x; AEM 6.4.x; AEM 6.3 SP2; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |

>[!NOTE]
>
>O limite de tamanho de cache não é aplicado. Quando o aplicativo de desktop é start, o tamanho do cache é calculado uma vez e uma notificação é exibida se o tamanho estiver próximo ao limite predefinido.

## Requisitos e pré-requisitos do sistema {#system-requirements-and-prerequisites}

O AEM Desktop é compatível com os seguintes sistemas operacionais:

* Mac OS X 10.10 ou posterior, com as correções de erros mais recentes.
* Windows 7 e Windows 10 com os service packs e correções de erros mais recentes.

A Adobe recomenda usar a versão mais recente do aplicativo AEM para desktop para aproveitar a funcionalidade mais recente, as correções de erros mais recentes e o melhor desempenho possível.

A versão do aplicativo de desktop AEM que você está planejando instalar em sua máquina local requer uma versão específica do servidor AEM/componentes adicionais do servidor (service packs, hot fixes ou pacotes de recursos). Verifique se o servidor AEM está configurado corretamente antes de se conectar a ele pela primeira vez. Se precisar de ajuda, entre em contato com o administrador do AEM.

Consulte a matriz [de compatibilidade](#compatibilitymatrix) detalhada no final deste documento para avaliar os pré-requisitos para sua configuração.

## What&#39;s New in AEM desktop app 1.10 {#what-s-new-in-aem-desktop-app}

O aplicativo de desktop AEM 1.10 foca na melhoria da experiência do usuário em uploads grandes, informações sobre as operações em segundo plano e experiência otimizada ao abrir ativos com arquivos vinculados (como o InDesign).

>[!NOTE]
>
>Se você estiver usando o macOS 10.15.4 ou mais recente, use pelo menos a versão 1.10.0.6 do aplicativo. Esta versão de patch está em conformidade com os requisitos [de autenticação da](https://developer.apple.com/news/?id=04102019a)Apple.

**Edição local / Check-out**: Os uploads automáticos de alterações salvas em ativos podem ser desativados na janela de status. Dessa forma, o usuário pode continuar trabalhando em arquivos e salvando as alterações e, quando estiver pronto, decidir carregar todas as alterações.

**Janela** Status do ativo simplificado: A janela de status foi simplificada * A guia Uploads agora mostra ativos individuais, bem como uploads de pasta / itens em massa. A guia Carregamentos em massa anterior foi removida.

**Ícone de aplicativo para indicar uploads** em massa: O ícone do aplicativo indicará que um upload em massa está em andamento, mostrando uma sobreposição de &quot;transferência&quot;.

**Notificações para conflito** de atualização: Quando o aplicativo detectar um conflito ao tentar atualizar um ativo, ele mostrará uma notificação, para que o usuário possa revisá-lo sem a necessidade de monitorar a janela de status. Quando o aplicativo for start, ele verificará todos os conflitos para que o usuário possa resolvê-los.

**Melhor tratamento das perdas** de conexão: Os uploads em massa serão pausados se houver perda de conexão e o usuário poderá retomar mais tarde. Um botão Tentar novamente está disponível para tentar fazer novamente um upload com falha de um arquivo individual.

## Instruções de instalação {#installation-instructions}

Para obter instruções detalhadas, consulte [Instalar e configurar o aplicativo](install-configure-app-v1.md)de desktop do AEM.

## Melhorias nas versões anteriores {#enhancements-in-the-previous-versions}

Esta versão estende e substitui as versões anteriores do aplicativo Experience Manager para desktop, que proporcionou os seguintes aprimoramentos principais:

* **Versão 1.9/1.9.1**: uploads retomáveis, janela de status aprimorada, ícones de aplicativos que indicam o status do aplicativo/conexão, busca prévia de ativos vinculados para arquivos do InDesign
* **Versão 1.8**: melhor controle do tamanho do cache para o usuário, experiência de logon aprimorada para SAML/SSO no Windows, suporte ao proxy de rede .pac no Mac e problemas relatados pelo cliente.
* **Versão 1.7**: melhorias na estabilidade e na lógica de cache, melhor suporte para proxy de rede e capacidade de limpar arquivos internos após a desinstalação.
* **Versão 1.6**: melhorias no processo de logon para várias configurações de segurança do AEM e estabilidade e desempenho do aplicativo.
* **Versão 1.5**: estabilidade e resiliência de aplicativos contra vários problemas de rede, melhor suporte.
* **Versão 1.4**: a capacidade de carregar pastas hierárquicas em segundo plano com o monitoramento de progresso.
* **Versão 1.3**: melhorias de desempenho e estabilidade de acesso a arquivos e salvamento de alterações no AEM, especialmente de aplicativos de desktop da Creative Cloud, como InDesign, Illustrator ou Photoshop. O objetivo era fornecer aos usuários uma experiência mais semelhante à de um desktop local ao trabalhar com arquivos, enquanto manipulava simultaneamente as operações de transferência de dados de rede em segundo plano.

### Melhorias disponíveis desde o aplicativo de desktop AEM 1.9 {#Enhancements-Available-Since-AEM-Desktop-App-19x}

O aplicativo de desktop Adobe Experience Manager (AEM) 1.9.1 foi uma versão de correção para solucionar alguns problemas principais do cliente com a verificação de ativos e a cópia de arquivos do compartilhamento de rede para um diretório local.

* Os ativos com check-out feito por um usuário não devem estar disponíveis para modificação para outros usuários (CQ-4246009)
* Suporte para cópia da pasta mapeada para uma pasta local quando a pasta do usuário estiver em uma partição de disco separada (CQ-4243978)

O aplicativo de desktop AEM 1.9 focou-se em melhorar a experiência do usuário em uploads grandes, informações sobre operações em segundo plano e experiência otimizada ao abrir ativos com arquivos vinculados (como o InDesign).

**Uploads**reiniciáveis Para uploads, especialmente em arquivos grandes, há uma opção para pausá-los/retomá-los na nova janela Status do ativo.
**Janela**Status do ativo aprimorado Uma janela de status do ativo aprimorado fornece informações sobre os ativos que são:
Alterações

* Exibe as alterações na fila no momento
* Mostra os uploads em andamento, incluindo uma barra de progresso, taxa de transferência, tamanho total do arquivo e tamanho transferido até agora
* Carregamentos concluídos mostrados com o total transferido e a taxa final
* Falha na exibição de uploads juntamente com uma mensagem de erro e informações de transferência, se disponíveis
* Carregamentos que falharam 3 vezes mostrarão uma mensagem de erro
* Arquivos conflitantes exibidos com um ícone no qual o usuário pode clicar. Clicar no ícone mostra uma caixa de diálogo com uma explicação e duas opções:
   * &quot;Mantenha o meu&quot;: carrega imediatamente o arquivo no servidor
   * &quot;Substituir o meu&quot;: exclui imediatamente o arquivo local e baixa uma nova cópia do servidor

Downloads

* Exibe os downloads em andamento, incluindo a taxa de transferência e o tamanho transferidos até agora
* Downloads concluídos mostrados com total transferido, taxa final e um ícone que abrirá o arquivo quando clicado (disponível somente para arquivos únicos)
* Falha nos downloads exibidos com uma mensagem de erro e informações de transferência, se disponíveis
* O rodapé mostra o número total de arquivos baixados e a taxa média de transferência.
* Se um usuário optar por abrir ou editar vários arquivos da interface do usuário do AEM Assets, eles serão agrupados, mostrando como, por exemplo, &quot;myasset.jpeg e mais 4 arquivos&quot;
* Ao baixar Documentos do InDesign incluindo ativos vinculados armazenados nos ativos AEM, o aplicativo de desktop baixará todos os ativos vinculados primeiro, antes de abrir o Documento do InDesign e indicará o download de ativos vinculados como, por exemplo, (5 de 24)

Uploads em massa: Carregar hierarquias de pastas grandes via Criar > Carregar pasta na interface do usuário da Web do AEM ou copiar e selecionar &quot;Colar ativos&quot; no Finder/Explorer no menu de contexto do aplicativo de desktop acionará o uso desta caixa de diálogo:

* Exibe os uploads em andamento, incluindo uma barra de progresso e o nome do arquivo que está sendo transferido no momento
* Os uploads em andamento incluem um ícone que cancelará o upload quando clicado. A transferência será interrompida após a conclusão do arquivo que está sendo transferido
* Os processos de transferência com falha são exibidos com uma mensagem de erro (somente se toda a transferência falhar)
* Se um arquivo individual falhar na transferência, ele aparecerá na guia como um erro. Caso contrário, os arquivos individuais não serão exibidos na guia * apenas uma única entrada para todo o upload.

**Ícones para indicar o status das operações** em segundo plano O ícone do aplicativo indicará o estado das operações em segundo plano para fornecer uma melhor indicação visual aos usuários. Por exemplo, quando o aplicativo não estiver conectado ao AEM, o ícone ficará acinzentado, quando houver um upload ativo, ele mostrará uma sobreposição &quot;sincronizada&quot; etc.

**Pré-busca dos ativos**vinculados Para melhorar a experiência do usuário ao trabalhar com documentos do InDesign que incluem ativos vinculados armazenados no AEM, o aplicativo de desktop tentará e pré-busca desses arquivos vinculados para o cache local antes de baixar e abrir o documento do InDesign. Dessa forma, o usuário terá os arquivos vinculados disponíveis localmente e não precisará aguardar mais ao acessá-los no InDesign (no painel Links).
Observe que a busca prévia só funciona se o AEM reconhecer os links no lado do servidor. Um ativo com links reconhecidos terá uma lista de &quot;Referências&quot; listada na visualização Propriedades do ativo do InDesign.

### Aprimoramentos disponíveis desde o aplicativo de desktop AEM 1.8.x {#enhancements-available-since-aem-desktop-app-18x}

O aplicativo de desktop AEM versão 1.8.1 de acompanhamento rápido adicionou melhorias ao abrir vários arquivos simultaneamente da interface do usuário do AEM à versão 1.8 (CQ-4237747, CQ-4238780). As melhorias no aplicativo 1.8 para desktop do AEM são:

* Armazenamento em cache: nova interface do usuário para gerenciar o cache do aplicativo para desktop AEM (CQ-4208690), incluindo,
   * visualização do tamanho do cache atual
   * definir o tamanho máximo do cache antes de uma notificação ser enviada
   * O tamanho do cache é verificado apenas no start do aplicativo de desktop, e uma notificação é mostrada se estiver atingindo o limite configurado
   * limpar o botão de cache agora está disponível na nova interface do usuário
* Logon: (Win) Corrigido o logon na instância do AEM configurada para usar SAML e SSL (CQ-4216353)
* Rede:
   * quando uma sessão do AEM expira, o usuário é notificado e pode clicar na notificação para fazer logon novamente (CQ-4202028)
   * (Mac) Adicione suporte para conexão com o AEM por meio da configuração de proxy .pac (CQ-4233430)
   * (Win) corrigir problemas com a caixa de diálogo Avançado - URL de logon (CQ-4236061)
* Correções de erros:
   * Caixa de diálogo Mais informações do ativo: às vezes, a barra de ação não estava visível (CQ-4208540)
   * (Win) O arquivo agora pode ser sincronizado após reverter para uma versão anterior da interface do usuário do AEM Assets (CQ-4216411)

### Aprimoramentos disponíveis desde o aplicativo de desktop AEM 1.7 {#Enhancements-Available-Since-AEM-Desktop-App-17}

* Estabilidade:
   * Estabilidade aprimorada quando o aplicativo de desktop AEM se conecta a um servidor AEM sobrecarregado (CQ-4224803)
   * Estabilidade aprimorada quando vários arquivos são solicitados (CQ-4224212)
   * Atualização de ativos aprimorada com verificação adicional (CQ-4228291)
* Armazenamento em cache:
   * Corrigir erros de disco e problemas de abertura ao abrir arquivos no Photoshop, InDesign, Finder (CQ-4223993, CQ-4217603, CQ-4223717)
   * Aprimoramento do cache para evitar binários de tamanho zero (CQ-4216599)
* Logon: Permitir a conexão com SSL restrito desabilitado para configurações especiais (como certificados emitidos localmente) (CQ-4223949)
* Rede: Suporte aprimorado para conexão por proxy de rede (CQ-4223477, CQ-4221280, CQ-4206854)
* Instalação e desinstalação:
   * (Win) Desinstalação do Cleaner (CQ-4220906)
   * [O Windows 32 bit] Installer falha ao tentar instalar o Microsoft .NET Framework v. 4.5 (CQ-4218084)
   * (Mac) Script manual para remover completamente os arquivos do aplicativo de desktop (CQ-4216489)

>[!NOTE]
>
>Problemas encontrados nas cargas beta 1.7 do aplicativo de desktop AEM (que não estavam presentes na versão 1.6 não são reportados nas notas de versão).

### Aprimoramentos disponíveis desde o aplicativo de desktop AEM 1.6 {#Enhancements-Available-Since-AEM-Desktop-App-16}

* Documentação: Novas práticas [recomendadas para a documentação do aplicativo](https://helpx.adobe.com/experience-manager/6-3/assets/using/aem-desktop-app-best-practices.html) v1.x.
* Processo de logon aprimorado no AEM:
   * Melhore a manipulação do SAML * regras de relaxamento (CQ-4202781).
   * Adicione a capacidade de configurar um URL de logon separado em Preferências (CQ-4214052, CQ-4214051).
* Usabilidade: Notificar o usuário quando o ativo ainda estiver baixando para ativos maiores (CQ-4216284).
* Rede:
   * Cache de DNS (CQ-4210176).
   * Conexão de suporte via proxy no Windows (CQ-4206854).
* Cache e acesso ao compartilhamento de rede no Finder / Explorer:
   * O ícone de bloqueio agora está visível para ativos com check-out no Windows 10 (CQ-90957).
   * O conteúdo da pasta pode desaparecer/reaparecer no compartilhamento de rede (CQ-4209160, CQ-4210180).
   * Erro no carregamento do arquivo devido a um conflito relatado no status de fila de upload (CQ-4215727).
   * Ao abrir vários arquivos da pasta do aplicativo de desktop no PS, mensagens de arquivo truncadas ou incompletas podem ser exibidas (CQ-4216276).
* Correções na estabilidade e desempenho:
   * Desempenho aprimorado ao navegar pelas pastas com muitos ativos (CQ-4214933).
   * o aplicativo desktop 1.5 pode retardar a máquina de desktop com o tempo (CQ-4209159).
   * Mostrar o recurso de status da fila funciona somente para o usuário que instalou o aplicativo (CQ-4212199).
   * (Windows) Verifique se o instalador de 32 bits não contém código de 64 bits (CQ-4217406).
* Problemas selecionados encontrados e corrigidos em 1.6 Beta:
   * Alta utilização da CPU (CQ-4218070).
   * Erro ao arrastar e soltar arquivos ao fazer upload para o AEM (CQ-4217006).

### Melhorias disponíveis desde o aplicativo de desktop AEM 1.5 {#Enhancements-Available-Since-AEM-Desktop-App-15}

**Versão 1.5.1.5 para Mac OS X:** A versão 1.5.1.5 oferece os seguintes benefícios:

* Novos recursos e melhorias: Adicione a funcionalidade Copiar/Colar à integração do Finder para permitir a transferência direta da área de trabalho para o AEM (CQ-4208158)
* Correções de erros:
   * Corrigido o erro 43 que ocorria às vezes durante a renomeação de ativos (CQ-4207900)
   * Reverter para uma versão anterior da linha do tempo no AEM não atualiza o ativo no Finder (CQ-4205194)
   * o aplicativo de desktop falha ao navegar em grandes diretórios aninhados (CQ-4208539)
   * o ponto de montagem do aplicativo desktop agora é /Volumes/DAM, portanto, é consistente para todos os usuários (CQ-4208159)
   * Colocar arquivo no InDesign pela primeira vez inicia um aviso de atualização (CQ-4207454)

Observação sobre Avisos de link: Os aplicativos da Creative Cloud (como o InDesign) tiram um &quot;instantâneo&quot; da última modificação do item no momento em que ele é colocado. Se essa data for alterada posteriormente, o aplicativo da Adobe Creative Cloud reportará que os links estão desatualizados. Isso é reportado de várias maneiras:

* Quando o aplicativo da Adobe Creative Cloud for iniciado, ele exibirá uma caixa de diálogo informando ao usuário que os ativos vinculados estão desatualizados e solicitará que ele execute uma ação.
* Se o aplicativo da Adobe Creative Cloud já estiver em execução, ele mostrará um ícone de aviso de triângulo amarelo no ativo vinculado.

Esse comportamento é o mesmo para ativos em disco local e ativos em um diretório montado na área de trabalho do AEM, com as seguintes exceções:

* Se um ativo inserido for modificado por um usuário diferente, o ícone de aviso será exibido na primeira vez que outros usuários abrirem um documento contendo o ativo colocado. Isso só acontecerá se o ativo colocado já tiver sido armazenado em cache localmente.
* Se um usuário modificar um ativo colocado por meio do diretório montado da área de trabalho do AEM e, em seguida, limpar seu cache local, o ativo colocado será reportado como desatualizado.

Ambos os casos são esperados e são efeitos colaterais da arquitetura de &quot;sincronização atrasada&quot; do AEM Desktop.

**Versão 1.5.0.x para Mac OS X e Windows:** Esta versão do aplicativo de desktop AEM oferece os seguintes benefícios:

* Melhor estabilidade e resiliência contra problemas de rede
   * Mapeamento mais estável das pastas do AEM Assets (CQ-103276, CQ-4204669, CQ-4203957)
   * Melhor manipulação de arquivos em cache (CQ-4204336, CQ-4206263)
   * Funcionamento aprimorado do download/carregamento de arquivos grandes com mais de 2 GB (CQ-4206438)
   * Corrigido o &quot;Erro 36&quot; ao mover ou renomear um número maior de arquivos no Finder (CQ-4204640)
* Otimizações na comunicação de rede com o AEM Server (CQ-4204974, CQ-100903)
* Melhoria da confiabilidade de abrir, posicionar e salvar ativos AEM em aplicativos da Creative Cloud (CQ-4203968, CQ-4205511, CQ-103543, CQ-4207141, CQ-90980)
* Suporte aprimorado: opção para limpar o cache (CQ-4202541), acesso fácil aos registros (CQ-4202340, CQ-4204673)
* Outras correções:
   * Melhor suporte para ativos e pastas com caracteres japoneses nas configurações de nome/idioma diferente do inglês (CQ-4195433, CQ-4205793, CQ-4199446)
   * Melhor manipulação do logon com SSL (CQ-4200217)
   * Montagem de compartilhamento mais confiável (CQ-4200793)
   * Várias melhorias na estabilidade (CQ-4207539, CQ-4200378)
   * Melhor manipulação do URL do AEM Assets em Preferências (CQ-97388)

### Aprimoramentos disponíveis desde o aplicativo de desktop AEM 1.4 {#Enhancements-Available-Since-AEM-Desktop-App-14}

* Carregamento simplificado de pastas hierárquicas por meio da nova ação Criar > Carregar pasta na interface de usuário de toque
   * Ação inicia uma operação de carregamento de pasta executada pelo aplicativo de desktop
   * O aplicativo de desktop atravessa a hierarquia de pastas específica na área de trabalho em segundo plano e carrega os arquivos nos ativos AEM
   * O usuário pode monitorar o progresso na nova janela Upload Queue Status (Status da fila de upload) com a barra de progresso para operações em andamento
   * O status da fila de upload também fornece informações melhores sobre solução de problemas (por exemplo, sem conexão com o servidor)
* Nova ação de edição na interface do usuário de toque, que combina as operações de retirada e abertura em uma única
* Agrupamento otimizado de ações relacionadas ao desktop na interface do usuário para toque (AEM 6.3)
* Compatibilidade aprimorada com as versões mais recentes do SO
* Correções relatadas pelo cliente

### Aprimoramentos disponíveis desde o aplicativo de desktop AEM 1.3 {#Enhancements-Available-Since-AEM-Desktop-App-13}

* Maior eficiência. Os usuários gastam menos tempo esperando a conclusão das operações de rede.
* Integração aprimorada do Finder, que oferece mais estabilidade e acesso a recursos, como miniaturas.
* Melhorias no cache e no desempenho.
* Melhor suporte para salvar diretamente de aplicativos de desktop (PS, ID, AI e assim por diante).
* Integração aprimorada com o Mac OS (protocolo de unidade de rede local alterado de WebDAV para SMB1 mais estável).
* O aplicativo de desktop se conecta com o servidor AEM usando o protocolo HTTP RESTful nativo do AEM.
* Os arquivos são salvos localmente primeiro e carregados de volta ao AEM em segundo plano após um tempo predefinido (30 segundos). Isso reduz o tempo para salvar arquivos.
* Melhor manipulação de aplicativos de desktop que usam operações intermediárias de arquivos para salvar um arquivo (salvamentos parciais e arquivos temporários), o que permite que a linha do tempo do AEM Asset exiba informações corretas de versão e upload de ativos.
* Caixa de diálogo fornecida para rastrear o status das tarefas de upload em segundo plano.

## Lista de alterações {#list-of-changes}

### Ponto de montagem no Mac {#mount-point-on-mac}

Desde o MacOS 10.12 (Sierra), a Apple alterou as permissões na pasta /Volumes usada para montar unidades de rede e dispositivos para torná-los mais restritivos. A criação de um novo ponto de montagem exigia direitos administrativos. Esse problema foi corrigido no MacOS 10.12.5.

Como o aplicativo de desktop AEM deve ser executado para usuários que não têm direitos de administrador na máquina local, o ponto de montagem do repositório do AEM Assets foi alterado em 1.4 e 1.5 para uma subpasta DAM na pasta local do usuário no MacOS (CQ-104183).

Como a pasta /Volumes não requer mais direitos administrativos, essa alteração foi revertida em 1.5.1. Isso também possibilita o compartilhamento de documentos do InDesign que colocaram ativos AEM entre usuários do MacOS.

### Alteração de protocolo (desde v1.3) {#protocol-change-since}

* Mac OS X:
   * O protocolo de unidade de rede local para integração de desktop OS X foi alterado para SMB1 do WebDAV.
   * O repositório AEM montado com aplicativo de desktop estará visível como uma unidade de rede &quot;smb&quot; no Finder, em vez de uma unidade WebDAV.
* Windows:
   * O protocolo de unidade de rede local para integrações de computadores Windows permanece; O AEM será montado como um compartilhamento WebDAV.
* Para ambas as plataformas (Windows e Mac):
   * O protocolo para acessar/baixar ativos e fazer upload de alterações no AEM foi alterado para o protocolo AEM nativo, que é um protocolo RESTful baseado em HTTP. Fornece maior controle sobre as operações da rede e é mais compatível com a infraestrutura da rede.

>[!NOTE]
>
>No Mac OS X, a alteração do protocolo de unidade de rede local de WebDAV para SMB1 resulta em um caminho local diferente para o mesmo ativo no repositório. Isso pode afetar os links para arquivos colocados nos aplicativos da Adobe Creative Cloud por meio do comando &quot;Inserir&quot;. Consulte [Usar o aplicativo](use-app-v1.md) para desktop AEM para obter mais informações.

### Manuseio de arquivos (desde 1.3) {#file-handling-since}

* As pastas são atualizadas automaticamente após um atraso predefinido (atualmente 30 s).
* Os arquivos com check-out feito por outros usuários são marcados como somente leitura.
* Os arquivos são salvos em um local de unidade de rede montado por meio de um aplicativo de desktop em duas fases.
* Na primeira fase, um arquivo é salvo localmente. Dessa forma, o usuário que estiver salvando o arquivo não precisará aguardar até que o arquivo seja totalmente transferido para o AEM e poderá retomar o trabalho assim que o arquivo for salvo.
* Na segunda fase, o aplicativo desktop carrega um arquivo atualizado no servidor AEM após um atraso predefinido (por exemplo, 30s ). Esta operação ocorre em segundo plano. Use a opção **Mostrar status** de sincronização de arquivo em segundo plano para visualização do status da operação de upload.

## Avisos importantes {#important-notices}

**Upload de pasta.** É recomendável usar o novo recurso de Carregamento de pasta para carregar pastas maiores e hierárquicas no AEM, em vez de usar uma cópia / arrastar e soltar em um repositório AEM montado no nível do Finder / Explorer. Ao usar o recurso de upload de pasta, o aplicativo desktop se comunica diretamente com o AEM e, portanto, tem um controle muito melhor sobre o processo geral.

**Mantenha a sessão do AEM disponível.** O aplicativo de desktop AEM depende de uma sessão aberta no servidor do AEM Assets para garantir a operação correta. Para usuários que trabalham com aplicativos de desktop todos os dias, é recomendável desmontar os ativos AEM no final do dia para forçar o logout e, em seguida, &quot;Montar ativos AEM&quot; pela manhã para garantir que eles estejam conectados e que o compartilhamento de rede esteja operacional.

**Desative &quot;Pré-visualização de ícones&quot; no Finder.** Para navegar em pastas grandes com o Finder, especialmente com conectividade de rede ruim, verifique se &quot;Ícone&quot; e &quot;Pré-visualização de ícones&quot; estão desativados. Caso contrário, o Finder fará o download de cada ativo em uma pasta para gerar uma pequena pré-visualização, o que pode resultar em desempenho insatisfatório e na utilização de alta largura de banda (CQ-4219779)

* No Finder, vá para a pasta de rede compartilhada do AEM Assets
* Clique com o botão direito do mouse no ponto de montagem DAM
* Selecionar Mostrar opções de Visualização
* Desmarque &quot;Mostrar pré-visualização do ícone&quot;
* Clique em &quot;Usar como padrões&quot;

**Limpe o cache ao conectar-se a um novo servidor AEM.** Se o aplicativo de desktop se conectar a outro servidor AEM com o mesmo URL, o cache não será apagado automaticamente. Limpe o cache manualmente para garantir as operações adequadas. Observe que isso normalmente aconteceria em testes, quando as instalações do AEM podem ser substituídas durante a execução no mesmo URL (CQ-4216982)

**Usar certificados SSL assinados pela CA.** Observe que o aplicativo de desktop AEM não oferece suporte a certificados SSL autoassinados ao se conectar ao AEM por uma conexão segura HTTPS. Um certificado assinado pela CA é necessário no servidor para essas conexões. (CQ-87941)

## Problemas conhecidos {#known-issues}

* Geral:
   * Os URLs do servidor são necessários para apontar para o servidor sem um caminho (por exemplo, `http://server`, `https://server`, `http://server:port`ou `https://server:port`). Caminhos de contexto e subpastas diferentes de /content/dam não são suportados (CQ-89343, CQ-87272)
* Nomes de arquivo / localização:
   * Os nomes de arquivos e pastas com caracteres reservados não são tratados corretamente. Certifique-se de usar os nomes de arquivos e pastas que atendem aos requisitos do AEM (CQ-93361, CQ-93308, CQ-89276, CQ-4217183)
   * Alguns aplicativos, como o Adobe Illustrator, podem criar arquivos com nomes sem suporte no AEM. Por exemplo, adicionar `Converted` após a conversão de um arquivo, o que impede que ele seja carregado (CQ-4216985)
   * Ativos com nomes internacionais podem aparecer e desaparecer a cada poucos segundos
* Check-in e Check-out:
   * Um ativo com check-out feito por um usuário não é possível abrir para outro usuário, seja pela ação Abrir da interface de usuário ou diretamente na área de trabalho. Alguns aplicativos podem relatá-lo como bloqueado, mas também corrompido ou até mesmo suspenso ao tentar abrir. (CQ-4199234)
   * Alterar arquivos simultaneamente por vários usuários pode causar a perda de algumas modificações. A solução alternativa é usar a funcionalidade de check-in e check-out para impedir que vários usuários alterem o mesmo arquivo (CQ-97035)
   * Determinados aplicativos não suportam o sinalizador somente leitura corretamente, o que permite que um usuário salve um arquivo cujo check-out foi feito por outro usuário. O arquivo modificado não é transferido até que o outro usuário faça check-in no arquivo. Ambas as modificações estão disponíveis no AEM como diferentes versões do ativo (CQ-89551, CQ-87572, CQ-89615)
   * O status de check-out e somente leitura é relatado independentemente no Finder. Isso resulta em 2 ícones de bloqueio quando um usuário faz check-out de um ativo (CQ-89507)
* Integração do Finder:
   * Ao arrastar/soltar arquivos grandes, o Finder pode expirar enquanto os arquivos são transferidos em segundo plano. Isso resulta em um `Error - 36`. A solução alternativa é arrastar/soltar ou abrir o ativo novamente (CQ-4219628)
   * O recarregamento manual da pasta nem sempre funciona. Solução:  aguarde 30s para que a pasta seja atualizada automaticamente. (CQ-97389)
   * Mais Informações sobre Ativos... está limitado a seleções de arquivo único (CQ-89542, CQ-87656)
   * Abrir nos ativos AEM... está limitado a seleções de arquivo único e pasta (CQ-83382)
   * Erro ao renomear ativos que não têm extensão (CQ-4218971)
* Funcionalidade Copiar/Colar: Colar está disponível quando nenhum ativo foi copiado para a área de transferência
* Windows:
   * Os arquivos com fluxos de dados alternativos (ADS) só são totalmente suportados no NTFS. A cópia desses arquivos para o compartilhamento WebDAV fornecido pelo aplicativo de desktop resultará em uma caixa de diálogo de precaução avisando o usuário de que o arquivo tem propriedades que não podem ser copiadas para o novo local. Normalmente, isso é correto, pois as propriedades são relevantes somente para um aplicativo específico na área de trabalho do usuário e não têm nada a ver com o conteúdo do arquivo real (CQ-103770) (Win)
   * o aplicativo desktop no Windows precisa ser instalado pelo usuário que o usará (CQ-4216389) (win)
   * O aplicativo pode travar ao clicar no botão Tentar novamente em um upload com falha em determinadas circunstâncias depois de retomar o upload em lote quando desconectado (CQ-4251884) (Win)

## Recursos úteis {#helpful-resources}

* [Documentação do AEM](https://helpx.adobe.com/support/experience-manager/6-4.html)
* [Usar o aplicativo de desktop AEM v1.x](use-app-v1.md)
* [Práticas recomendadas do aplicativo de desktop AEM v1.x](best-practices-for-v1.md)

## Matriz de compatibilidade e pré-requisitos {#compatibilitymatrix}

O aplicativo de desktop AEM funciona com várias versões do AEM. Consulte a matriz de compatibilidade das versões suportadas.

| Versão | Revisão | Data de lançamento | Compatibilidade |
|---------|------------------------|--------------|-------------------------------------------------------------|
| 1.10 | 1.10.0.3 (Mac e Win) | 31 de ago de 2018 | AEM 6.5; AEM 6.4 SP1; AEM 6.3 SP2; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1.9 | 1.9.1.1 (Mac e Win) | 21 de jun de 2018 | AEM 6.4; AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1.8 | 1.8.1.0 (Mac e Win) | 28 de mar de 2018 | AEM 6.4; AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1.7 | 1.7.0.3 (Mac e Win) | 10 de janeiro de 2018 | AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
