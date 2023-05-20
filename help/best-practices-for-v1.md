---
title: Práticas recomendadas do aplicativo de desktop v1.10
description: Principais recursos e uso recomendado do [!DNL Adobe Experience Manager] aplicativo de desktop versão 1.10.
exl-id: 5de06b33-c05c-47eb-b884-408b6f9afc94
source-git-commit: 7a7236c36f615e97e9d040e6139368a931eb579e
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 0%

---

# Práticas recomendadas do aplicativo para desktop AEM v1.10 {#aem-desktop-app-best-practices}

## Visão geral {#overview}

[!DNL Adobe Experience Manager] O aplicativo de desktop vincula sua solução de Gerenciamento de ativos digitais (DAM) ao desktop para que você possa abrir os arquivos disponíveis na interface da Web do AEM diretamente no desktop. Se você salvar um ativo do desktop, ele será carregado para AEM no local apropriado.

O aplicativo para desktop AEM elimina a probabilidade de você atualizar cópias locais incorretas ou atualizar um ativo errado no AEM. o fluxo de trabalho fácil de usar do aplicativo de desktop é ativado usando a tecnologia de compartilhamento de rede fornecida pelos sistemas operacionais de desktop.

O aplicativo de desktop monta o repositório do AEM Assets como um compartilhamento de rede no desktop. Portanto, as pastas e os arquivos aparecem como se fossem locais. No entanto, não é recomendável realizar operações de gerenciamento de ativos digitais diretamente do desktop no compartilhamento de rede montado no Finder ou no Explorer. Em vez disso, a Adobe recomenda usar a interface do usuário da Web do AEM Assets para executar operações, como copiar ou mover um grande número de ativos.

>[!NOTE]
>
>Antes de ler este documento, você pode revisar o [Práticas recomendadas de integração de AEM e Creative Cloud](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/aem-cc-integration-best-practices.html) para obter uma visão geral de mais alto nível do tópico.

## Arquitetura de aplicativo para desktop AEM {#aem-desktop-app-architecture}

O aplicativo de desktop AEM usa compartilhamentos de rede WebDAV (Windows) ou SMB (Mac) para montar compartilhamentos de rede. O compartilhamento de rede montado é somente local. O aplicativo de desktop AEM intercepta as chamadas (abrir, ler, gravar) e fornece armazenamento em cache local adicional. Ele traduz chamadas remotas para o servidor do AEM Assets para solicitações HTTP AEM otimizadas. O diagrama a seguir representa a arquitetura de aplicativo de desktop do AEM.

![Arquitetura de aplicativo para desktop AEM](assets/arch_v1.png)

*Figura: arquitetura do aplicativo de desktop*

O armazenamento em cache adicional na gravação quando um arquivo é salvo faz com que o arquivo seja salvo localmente primeiro (para que o usuário não espere a transferência da rede). Em seguida, após um atraso predefinido (30 s), o arquivo é carregado no AEM em segundo plano e, em seguida, o ativo é carregado no AEM. O aplicativo de desktop AEM fornece uma interface para monitorar o status dos uploads de arquivos em segundo plano.

## Uso recomendado do aplicativo de desktop AEM {#recommended-use-of-aem-desktop-app}

Os principais recursos do aplicativo de desktop AEM incluem:

* **Erro ao abrir arquivos da interface do usuário da Web do AEM Assets no desktop**. Na interface da Web, você pode revelar ativos no desktop (no Finder, no Explorer) ou abrir um ativo usando um aplicativo de desktop.

* **Check-out e check-in**. É possível fazer check-out dos ativos para edição; eles são marcados como bloqueados para o usuário no AEM Assets. Após a edição, é possível fazer check-in do ativo para desbloqueá-lo.

* **Salvar alterações em arquivos**. Qualquer alteração que você salvar no arquivo no compartilhamento de rede é carregada automaticamente no AEM e uma nova versão é criada.

* **Colocar ativos vinculados em outros documentos**. Em aplicativos como o Creative Cloud ([!DNL Adobe Photoshop], [!DNL Adobe InDesign], e [!DNL Adobe Illustrator]), você pode colocar um arquivo externo como um link. Por exemplo, você pode inserir uma imagem em um documento do InDesign. Nesse caso, a montagem do compartilhamento de rede permite procurar e selecionar ativos do AEM para posicionamento. Colocar arquivos vinculados também funciona em alguns aplicativos que não sejam do Adobe, como o MS Office.

* **Resolução de referência em AEM**. Se ambos, os arquivos colocados e os arquivos principais com link, estiverem armazenados no AEM, ele poderá fornecer automaticamente informações do lado do servidor sobre as referências de ativos.

* **Acessar o ativo do desktop**. No compartilhamento de rede montado, um menu contextual fornece um [!UICONTROL More Info] (visualização maior, metadados principais) e a capacidade de abrir um ativo na interface do usuário do AEM.

* **Fazer upload de pastas grandes e hierárquicas em massa**. Se você usar a opção Criar > Upload de pasta na interface do AEM para fazer upload de ativos, o aplicativo de desktop AEM fará upload da hierarquia de pastas selecionada para o AEM em segundo plano. O progresso do upload pode ser monitorado com uma interface dedicada no aplicativo de desktop.

## Uso inapropriado do aplicativo de desktop AEM {#inappropriate-use-of-aem-desktop-app}

* Não use o aplicativo de desktop AEM para gerenciar ativos no desktop. O aplicativo de desktop AEM não foi criado para substituir unidades de rede. Em vez disso, use os seguintes recursos:

   * Interface da Web do AEM Assets para gerenciamento de ativos digitais (localização ou compartilhamento de ativos, metadados e cópia ou movimentação).

   * aplicativo de desktop AEM [!UICONTROL Folder Upload] para carregar pastas grandes e hierárquicas.

* Não trate o aplicativo de desktop AEM como um cliente de &quot;sincronização de desktop&quot; para o AEM Assets. O principal benefício do aplicativo de desktop AEM aqui é que ele fornece acesso &quot;virtual&quot; a todo o repositório, e os aplicativos de sincronização de desktop normalmente sincronizam apenas os ativos pertencentes a um usuário. O aplicativo de desktop AEM fornece algum nível de armazenamento em cache e carregamento em segundo plano; ainda assim, ele funciona de forma muito diferente dos aplicativos &quot;Sync&quot; típicos, como o aplicativo de desktop Adobe Creative Cloud ou o Microsoft OneDrive.

* Não use unidades de rede de aplicativos para desktop AEM para salvar ativos com frequência. Todas as operações de salvamento são transmitidas para o AEM Assets. Portanto, é impraticável executar operações de edição intensivas diretamente no repositório do AEM Assets montado. A edição de um ativo diretamente no repositório montado rastreia a linha do tempo do ativo com versões irrelevantes e impõe despesas gerais adicionais no servidor.

* Não use o aplicativo de desktop AEM para migração de grandes quantidades de dados de uma instância de AEM para outra. Consulte a [Guia de migração](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html) para planejar e executar migrações de ativos. Por outro lado, o aplicativo de desktop [suporta upload em massa](use-app-v1.md#bulkupload) um grande número de ativos pela primeira vez no [!DNL Adobe Experience Manager].

## Recommendations para casos de uso selecionados {#recommendations-for-selected-use-cases}

### Acesso a ativos para usuários de criação {#access-to-assets-for-creative-users}

O aplicativo de desktop AEM fornece acesso virtual a todo o repositório DAM, e pode ser complicado para os usuários criativos no desktop encontrar e acessar os ativos certos no desktop. Use essas práticas recomendadas para simplificar isso para eles.

* Use os recursos de colaboração na interface da Web do AEM Assets para fornecer acesso mais direto aos ativos certos para o usuário criativo. O compartilhamento de pastas ou coleções, o fornecimento de Coleções inteligentes (pesquisas salvas) ou o envio de notificações com ponteiros para os ativos certos são alguns deles. O usuário criativo pode então usar ações de desktop na interface da Web para obter acesso rápido a esses ativos no desktop.

* Considere as permissões certas para os ativos (controle de acesso) para simplificar a exibição no repositório DAM para os usuários criativos, limitando basicamente o acesso aos ativos necessários ou em que estão interessados:

   * Certas áreas não relevantes para os usuários criativos podem ser negadas para seus grupos de usuários, para removê-los de sua visualização, também no desktop.

   * A maioria dos ativos no DAM é final e não se destina a alterações. Eles devem ser somente leitura para os usuários criativos.

   * Somente os ativos que exigem alterações ou retoque devem ser habilitados para gravação pelos usuários de criação. Algumas organizações usam Projetos AEM e as pastas que criam para hospedar ativos que ainda estão sujeitos a alterações.

### Pesquisar ativos {#searching-assets}

Para procurar um arquivo que deseja abrir na área de trabalho:

* Use a interface da Web do AEM Assets para localizar o ativo. A pesquisa no AEM Assets não é apenas poderosa (aspectos de pesquisa, pesquisas salvas), ela também fornece recursos adicionais para encontrar o ativo correto. Isso inclui filtros adicionais, como a capacidade de pesquisar ativos com base no status (aprovação, expiração), coleções, tarefas, notificações e compartilhamento de pastas/coleções com outros usuários/grupos.

* Depois de localizar o ativo, use Ações do desktop na interface do AEM para acessar o ativo no desktop .

### Atualização de ativos abertos usando o aplicativo de desktop AEM {#updating-assets-opened-using-aem-desktop-app}

Se você editar um ativo diretamente no local mapeado do AEM Assets para um compartilhamento de rede local, o ativo será carregado para AEM sempre que for salvo no desktop. Além disso, o AEM cria uma versão e gera representações.

Se um ativo armazenado no AEM precisar de uma atualização:

* Para **pequenas atualizações**, como solicitações menores de retoque no processo de aprovação:

   * Faça check-out do arquivo e abra-o no desktop.

   * Atualize o arquivo.

   * Salve a versão atualizada. O ativo é atualizado e a linha do tempo exibe a versão original para comparação.

* Para **principais atualizações**, como uma solicitação de alteração que requer um pequeno ciclo criativo WIP:

   * Use a opção Revelar para abrir a pasta apropriada no desktop.

   * Copie o arquivo para uma pasta WIP fora do compartilhamento do AEM Assets mapeado (por exemplo, copie o arquivo em uma pasta sincronizada com o aplicativo de desktop do Adobe Creative Cloud).

   * Trabalhe no arquivo e salve-o intermitentemente. As alterações não são salvas no AEM Assets.

   * Após a conclusão das edições, mova, copie ou salve o arquivo mapeado do AEM para carregá-lo como uma nova versão.

## Desempenho da rede {#network-performance}

A boa experiência dos usuários que usam o aplicativo de desktop AEM depende muito da conectividade de rede boa e estável entre seus desktops e o servidor AEM, bem como do servidor ajustado para bom desempenho, especialmente no que diz respeito ao upload e à atualização de ativos. Essas recomendações são para as equipes de rede/TI nas organizações.

### Considerações de rede {#network-considerations}

Para entender as práticas recomendadas de configuração de rede do AEM Assets, consulte [Como migrar ativos em massa](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html) documento. Alguns dos aspectos importantes que ajudam a otimizar a experiência do aplicativo de desktop AEM para os usuários incluem:

* **Usar o Dispatcher configurado corretamente**. Use o AEM Dispatcher para obter segurança adicional e verifique se ele está configurado para [Conexão de aplicativo de desktop do AEM com o AEM por trás de um dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)

* **Economize largura de banda**. Considere desativar a visualização de ícones no Finder no Mac - ao navegar pelo repositório montado usando o Finder. O localizador solicita que cada arquivo gere uma visualização e faz com que o aplicativo de desktop baixe e armazene o ativo em cache localmente. Observe que ao economizar largura de banda, também diminuiria a experiência do usuário para os usuários no desktop, portanto, isso deve ser feito ao trabalhar com repositórios com ativos grandes e/ou largura de banda limitada.

>[!NOTE]
>
>Para desativar as visualizações de ícones, no Finder, acesse [!UICONTROL View], selecione [!UICONTROL View Options]e desmarque a opção [!UICONTROL Show icon preview] opção. Isso só funciona para a pasta atual - para torná-la padrão, clique no link [!UICONTROL Use as default] na mesma caixa de diálogo.

### Otimizando o desempenho do servidor {#optimizing-server-performance}

Para entender como o servidor AEM Assets deve ser otimizado para desempenho, consulte [Guia de ajuste de desempenho do AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html). Alguns dos aspectos importantes do desempenho do servidor para o aplicativo de desktop AEM são a otimização da configuração do fluxo de trabalho para que ele tenha bom desempenho para uploads de ativos:

* **Upload de ativos mais eficiente**. Configure o [Modelo de fluxo de trabalho de Atualização de ativos AEM para ser transitório](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html).

* **Limitar CPU do servidor para uploads**. Verifique se o parâmetro máximo de trabalhos de workflow paralelo está definido corretamente, para que os uploads não esgotem toda a CPU.
