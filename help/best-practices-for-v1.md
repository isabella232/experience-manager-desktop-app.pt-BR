---
title: Práticas recomendadas do aplicativo de desktop v1.10
description: Principais recursos e uso recomendado de [!DNL Adobe Experience Manager] aplicativo de desktop versão 1.10.
exl-id: 5de06b33-c05c-47eb-b884-408b6f9afc94
source-git-commit: 7a7236c36f615e97e9d040e6139368a931eb579e
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 0%

---

# Práticas recomendadas do aplicativo de desktop AEM v1.10 {#aem-desktop-app-best-practices}

## Visão geral {#overview}

[!DNL Adobe Experience Manager] o aplicativo de desktop vincula sua solução de Gerenciamento de ativos digitais (DAM) ao desktop para que você possa abrir os arquivos que estão disponíveis na interface do usuário da Web AEM diretamente no desktop. Se você salvar um ativo do desktop, ele será carregado para o AEM no local apropriado.

AEM aplicativo de desktop elimina as chances de você atualizar cópias locais incorretas ou atualizar um ativo errado no AEM. o fluxo de trabalho fácil de usar do aplicativo de desktop é ativado com a tecnologia de compartilhamento de rede fornecida pelos sistemas operacionais de desktop.

O aplicativo para desktop monta o repositório AEM Assets como um compartilhamento de rede no desktop. Portanto, as pastas e os arquivos aparecem como se fossem locais. No entanto, não é recomendável realizar operações de gerenciamento de ativos digitais diretamente do desktop no compartilhamento de rede montado no Finder ou Explorer. Em vez disso, o Adobe recomenda usar a interface do usuário da Web do AEM Assets para executar operações, como copiar ou mover um grande número de ativos.

>[!NOTE]
>
>Antes de ler este documento, você pode revisar o [Práticas recomendadas de integração de AEM e Creative Cloud](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/aem-cc-integration-best-practices.html) para obter uma visão geral de nível superior do tópico.

## Arquitetura de aplicativo de desktop AEM {#aem-desktop-app-architecture}

AEM aplicativo de desktop usa compartilhamentos de rede WebDAV (Windows) ou SMB (Mac) para montar compartilhamentos de rede. O compartilhamento de rede montado é somente local. AEM aplicativo de desktop intercepta as chamadas (abrir, ler, gravar) e fornece armazenamento em cache local adicional. Ele traduz chamadas remotas para o servidor do AEM Assets para solicitações HTTP AEM otimizadas. O diagrama a seguir descreve a arquitetura do aplicativo de desktop AEM.

![Arquitetura de aplicativo de desktop AEM](assets/arch_v1.png)

*Figura: arquitetura de aplicativos de desktop*

O armazenamento em cache adicional na gravação quando um arquivo é salvo faz com que o arquivo seja salvo localmente primeiro (para que o usuário não espere a transferência da rede). Em seguida, após um atraso predefinido (30s), o arquivo é carregado para AEM em segundo plano e, em seguida, o ativo é carregado para AEM. AEM aplicativo de desktop fornece uma interface do usuário para monitorar o status dos uploads de arquivo em segundo plano.

## Uso recomendado de AEM aplicativo de desktop {#recommended-use-of-aem-desktop-app}

Os principais recursos AEM aplicativo de desktop incluem:

* **Abrir arquivos da interface do usuário da Web do AEM Assets no desktop**. Na interface do usuário da Web, você pode revelar ativos no desktop (no Finder, no Explorer) ou abrir um ativo usando um aplicativo de desktop.

* **Check-out e check-in**. É possível fazer check-out dos ativos para edição, eles são marcados como bloqueados para o usuário no AEM Assets. Após a edição, é possível fazer check-in do ativo para desbloqueá-lo.

* **Salvar alterações em arquivos**. Qualquer alteração salva no arquivo no compartilhamento de rede é carregada para AEM automaticamente e uma nova versão é criada.

* **Colocar ativos vinculados em outros documentos**. Em aplicativos como o Creative Cloud ([!DNL Adobe Photoshop], [!DNL Adobe InDesign]e [!DNL Adobe Illustrator]), é possível colocar um arquivo externo como um link. Por exemplo, você pode colocar uma imagem em um documento do InDesign. Nesse caso, a montagem do compartilhamento de rede permite procurar e selecionar ativos do AEM para posicionamento. A colocação de arquivos vinculados também funciona em alguns aplicativos que não são Adobe, como o MS Office.

* **Resolução de referência em AEM**. Se os arquivos inseridos e os arquivos principais com o link , forem armazenados no AEM, ele poderá fornecer automaticamente informações do lado do servidor sobre as referências do ativo.

* **Acessar o ativo do desktop**. No compartilhamento de rede montado, um menu contextual fornece um [!UICONTROL More Info] (visualização maior, metadados principais) e a capacidade de abrir um ativo na interface do usuário do AEM.

* **Upload de pastas grandes e hierárquicas em massa**. Se você usar a opção Criar > Upload de pasta AEM interface do usuário para fazer upload de ativos, AEM aplicativo de desktop fará upload da hierarquia de pastas selecionada para AEM em segundo plano. O progresso do upload pode ser monitorado com uma interface dedicada no aplicativo de desktop.

## Uso inadequado AEM aplicativo de desktop {#inappropriate-use-of-aem-desktop-app}

* Não use AEM aplicativo de desktop para gerenciar ativos da área de trabalho. AEM aplicativo de desktop não foi criado como substituição para unidades de rede. Em vez disso, use os seguintes recursos:

   * Interface do usuário da Web do AEM Assets para gerenciamento de ativos digitais (localização ou compartilhamento de ativos, metadados e cópia ou movimentação).

   * AEM aplicativo de desktop [!UICONTROL Folder Upload] para carregar pastas grandes e hierárquicas.

* Não trate AEM aplicativo de desktop como um cliente de &quot;sincronização de desktop&quot; para AEM Assets. O principal benefício de AEM aplicativo de desktop aqui é que ele fornece acesso &quot;virtual&quot; a todo o repositório e os aplicativos de sincronização de desktop normalmente sincronizam apenas os ativos pertencentes a um usuário. AEM aplicativo de desktop fornece algum nível de armazenamento em cache e upload em segundo plano; ainda assim, ele funciona de forma muito diferente dos aplicativos típicos de &quot;sincronização&quot;, como o aplicativo de desktop do Adobe Creative Cloud ou o Microsoft OneDrive.

* Não use AEM unidades de rede de aplicativos de desktop para salvar ativos com frequência. Todas as operações de salvamento são transmitidas para a AEM Assets. Portanto, não é prático executar operações de edição intensiva diretamente no repositório AEM Assets montado. Editar um ativo diretamente no repositório montado encaixa a linha do tempo do ativo com versões irrelevantes e impõe custos adicionais no servidor.

* Não use AEM aplicativo de desktop para migração de grandes quantidades de dados de uma instância de AEM para outra. Consulte a [Guia de migração](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html) para planejar e executar migrações de ativos. Por outro lado, o aplicativo de desktop [suporta upload em massa](use-app-v1.md#bulkupload) grande número de ativos pela primeira vez em [!DNL Adobe Experience Manager].

## Recommendations para casos de uso selecionados {#recommendations-for-selected-use-cases}

### Acesso a ativos para usuários criativos {#access-to-assets-for-creative-users}

AEM aplicativo de desktop fornece acesso virtual a todo o repositório DAM - e pode ser complicado para os usuários criativos de desktop encontrar e acessar os ativos certos em seu desktop. Use essas práticas recomendadas para simplificar isso para eles.

* Use os recursos de colaboração na interface do usuário da Web do AEM Assets para fornecer acesso mais direto aos ativos certos para o usuário criativo. Compartilhar pastas ou coleções, fornecer Coleções inteligentes (pesquisas salvas) ou enviar notificações com ponteiros para os ativos corretos são alguns deles. O usuário criativo pode então usar as ações da área de trabalho na interface do usuário da Web para obter acesso rápido a esses ativos na área de trabalho.

* Considere as permissões certas para ativos (controle de acesso) para simplificar a visualização no repositório DAM para os usuários criativos, limitando basicamente seu acesso a apenas ativos que eles precisam ou que estão interessados em:

   * Certas áreas não relevantes para os usuários criativos podem ser negadas para seus grupos de usuários, para removê-las de sua visualização, também no desktop.

   * A maioria dos ativos no DAM é final e não se destina a alterações; eles devem ser somente leitura para os usuários criativos.

   * Somente os ativos que exigem alterações ou retoque devem ser habilitados para gravação para os usuários criativos. Algumas organizações usam AEM Projetos e as pastas que criam para hospedar ativos que ainda estão sujeitos a alterações.

### Pesquisar ativos {#searching-assets}

Para procurar um arquivo que deseja abrir na área de trabalho :

* Use a interface do usuário da Web do AEM Assets para localizar o ativo. A pesquisa não só é poderosa no AEM Assets (aspectos de pesquisa, pesquisas salvas), como também fornece recursos adicionais para encontrar o ativo correto. Isso inclui filtros adicionais, como a capacidade de pesquisar ativos com base no status (aprovação, expiração), coleções, tarefas, notificações e compartilhar pastas/coleções com outros usuários/grupos.

* Depois de localizar o ativo, use as Ações da área de trabalho na interface AEM para acessar o ativo na área de trabalho .

### Atualização de ativos abertos usando AEM aplicativo de desktop {#updating-assets-opened-using-aem-desktop-app}

Se você editar um ativo diretamente no local mapeado do AEM Assets para um compartilhamento de rede local, o ativo será carregado para AEM sempre que você salvá-lo no desktop. Além disso, o AEM cria uma versão e gera representações.

Se um ativo armazenado em AEM precisar de uma atualização:

* Para **atualizações secundárias**, como solicitações menores de retoque no processo de aprovação:

   * Dê uma olhada no arquivo e abra-o na área de trabalho.

   * Atualize o arquivo.

   * Salve a versão atualizada. O ativo é atualizado e a linha do tempo exibe a versão original para comparação.

* Para **principais atualizações**, como uma solicitação de alteração que requer um ciclo de WIP criativo pequeno:

   * Use a opção Revelar para abrir a pasta apropriada na área de trabalho.

   * Copie o arquivo para uma pasta WIP fora do compartilhamento AEM Assets mapeado (por exemplo, copie o arquivo em uma pasta sincronizada com o aplicativo de desktop do Adobe Creative Cloud).

   * Trabalhe o arquivo e salve-o intermitentemente. As alterações não são salvas no AEM Assets.

   * Após a conclusão das edições, mova, copie ou salve o arquivo mapeado do AEM para carregá-lo como uma nova versão.

## Desempenho da rede {#network-performance}

Uma boa experiência para os usuários que usam o aplicativo de desktop AEM depende muito da conectividade de rede estável e boa entre seus desktops e o servidor AEM, bem como do servidor ajustado para um bom desempenho, especialmente em relação ao upload e atualização de ativos. Essas recomendações são para as equipes de rede/TI em organizações.

### Considerações de rede {#network-considerations}

Para entender as práticas recomendadas relacionadas à configuração de rede do AEM Assets, consulte [Como migrar ativos em massa](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html) documento. Alguns dos aspectos importantes que ajudam a otimizar a experiência AEM aplicativo de desktop para os usuários incluem:

* **Usar o Dispatcher corretamente configurado**. Use AEM Dispatcher para segurança adicional e verifique se ele está configurado para [AEM conexão do aplicativo de desktop para AEM atrás de um dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)

* **Salvar largura de banda**. Considere desativar a visualização do ícone no Finder no Mac - ao navegar pelo repositório montado usando o Finder. O Finder solicita que cada arquivo gere uma pré-visualização e que o aplicativo de desktop baixe e armazene o ativo em cache localmente. Observe que, ao economizar largura de banda, também diminuiria a experiência do usuário para os usuários no desktop, portanto, isso deve ser feito ao trabalhar com repositórios com ativos grandes e/ou largura de banda limitada.

>[!NOTE]
>
>Para desativar as visualizações de ícones, no Finder, acesse [!UICONTROL View], selecione [!UICONTROL View Options]e, em seguida, desmarque a opção [!UICONTROL Show icon preview] opção. Isso só funciona para a pasta atual - para torná-la padrão, clique no botão [!UICONTROL Use as default] na mesma caixa de diálogo.

### Otimização do desempenho do servidor {#optimizing-server-performance}

Para entender como o servidor AEM Assets deve ser otimizado para desempenho, consulte [Guia de ajuste de desempenho do AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html). Alguns dos aspectos importantes do desempenho do servidor para AEM aplicativo de desktop são a otimização da configuração do fluxo de trabalho para que ele tenha bom desempenho para uploads de ativos:

* **Upload de ativos com mais desempenho**. Configure o [AEM modelo de fluxo de trabalho do Asset Update como temporário](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html).

* **Limitar CPU do servidor para uploads**. Verifique se o parâmetro máximo de trabalhos paralelos do fluxo de trabalho está definido corretamente, de modo que os uploads não esgotem toda a CPU.
