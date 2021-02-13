---
title: '[!DNL Adobe Experience Manager] práticas recomendadas do aplicativo para desktop versão 1.x'
description: Recursos principais e uso recomendado do  [!DNL Adobe Experience Manager] aplicativo desktop versão 1.x.
translation-type: tm+mt
source-git-commit: 95e252504a4fbb3b60a2c6bc9b57a8a0d8ecb51c
workflow-type: tm+mt
source-wordcount: '1677'
ht-degree: 0%

---


# Práticas recomendadas do aplicativo de desktop AEM v1.x {#aem-desktop-app-best-practices}

## Visão geral {#overview}

[!DNL Adobe Experience Manager] o aplicativo desktop vincula sua solução DAM (Digital Asset Management, gerenciamento de ativos digitais) ao seu desktop para que você possa abrir os arquivos disponíveis na interface do usuário da Web AEM diretamente no desktop. Se você salvar um ativo da área de trabalho, ele será carregado para AEM no local apropriado.

AEM aplicativo de desktop elimina as chances de você atualizar cópias locais incorretas ou atualizar um ativo incorreto no AEM. o fluxo de trabalho fácil de usar do aplicativo desktop é ativado usando a tecnologia de compartilhamento de rede fornecida pelos sistemas operacionais de desktop.

O aplicativo desktop monta o repositório AEM Assets como um compartilhamento de rede no desktop. Portanto, as pastas e os arquivos aparecem como se fossem locais. No entanto, não é recomendável realizar operações de gerenciamento de ativos digitais diretamente do desktop no compartilhamento de rede montado no Finder ou no Explorer. Em vez disso, o Adobe recomenda usar a interface do usuário da AEM Assets Web para executar operações, como copiar ou mover um grande número de ativos.

>[!NOTE]
>
>Antes de ler este documento, você pode revisar as [AEM e as práticas recomendadas de integração de Creative Cloud](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/aem-cc-integration-best-practices.html) para obter uma visão geral de nível superior do tópico.

## AEM arquitetura de aplicativos de desktop {#aem-desktop-app-architecture}

AEM aplicativo desktop usa compartilhamentos de rede WebDAV (Windows) ou SMB (Mac) para montar compartilhamentos de rede. O compartilhamento de rede montado é somente local. AEM aplicativo de desktop intercepta as chamadas (abrir, ler, gravar) e fornece cache local adicional. Ele traduz chamadas remotas para o servidor AEM Assets para solicitações HTTP AEM otimizadas. O diagrama a seguir descreve a arquitetura do aplicativo AEM desktop.

![AEM arquitetura de aplicativos para desktop](assets/arch_v1.png)

*Figura: arquitetura de aplicativos para desktop*

O cache adicional de gravação quando um arquivo é salvo faz com que o arquivo seja salvo localmente primeiro (para que o usuário não aguarde a transferência da rede). Depois de um atraso predefinido (30 s), o arquivo é carregado para AEM em segundo plano e o ativo é carregado para AEM. AEM aplicativo desktop fornece uma interface para monitorar o status dos uploads de arquivos em segundo plano.

## Uso recomendado de AEM aplicativo de desktop {#recommended-use-of-aem-desktop-app}

Os principais recursos AEM aplicativo de desktop incluem:

* **Abrindo arquivos da interface do usuário da AEM Assets Web na área de trabalho**. Na interface do usuário da Web, você pode revelar ativos na área de trabalho (no Finder, no Explorer) ou abrir um ativo usando um aplicativo de área de trabalho.

* **Check-out e check-in**. É possível fazer check-out dos ativos para edição, eles são marcados como bloqueados para o usuário no AEM Assets. Após a edição, é possível fazer check-in do ativo para desbloqueá-lo.

* **Salve as alterações nos arquivos**. Qualquer alteração que você salvar no arquivo no compartilhamento de rede será carregada para AEM automaticamente e uma nova versão será criada.

* **Coloque ativos vinculados em outros documentos**. Em aplicativos, como Creative Cloud ([!DNL Adobe Photoshop], [!DNL Adobe InDesign] e [!DNL Adobe Illustrator]), você pode colocar um arquivo externo como um link. Por exemplo, é possível colocar uma imagem em um documento de InDesign. Nesse caso, a montagem de compartilhamento de rede permite que você navegue e selecione ativos de AEM para posicionamento. A inserção de arquivos vinculados também funciona em alguns aplicativos que não são de Adobe, como o MS Office.

* **Resolução de referência em AEM**. Se os arquivos inseridos e os arquivos principais com link forem armazenados no AEM, ele poderá fornecer automaticamente informações do lado do servidor sobre as referências do ativo.

* **Acesse o ativo da área de trabalho**. No compartilhamento de rede montado, um menu contextual fornece uma caixa de diálogo [!UICONTROL More Info] (pré-visualização maior, metadados principais) e a capacidade de abrir um ativo na interface do usuário AEM.

* **Carregando pastas grandes e hierárquicas em massa**. Se você usar a opção Criar > Carregamento de pasta AEM interface do usuário para fazer upload de ativos, AEM aplicativo de desktop fará upload da hierarquia de pastas selecionada para AEM em segundo plano. O progresso do upload pode ser monitorado com uma interface de usuário dedicada no aplicativo de desktop.

## Uso inapropriado AEM aplicativo de desktop {#inappropriate-use-of-aem-desktop-app}

* Não use AEM aplicativo de desktop para gerenciar ativos da área de trabalho. AEM aplicativo de desktop não foi criado como uma substituição para unidades de rede. Em vez disso, use os seguintes recursos:

   * Interface do usuário da Web da AEM Assets para gerenciamento de ativos digitais (localizar ou compartilhar ativos, metadados e copiar ou mover).

   * AEM aplicativo de desktop [!UICONTROL Folder Upload] para carregar pastas grandes e hierárquicas.

* Não trate AEM aplicativo desktop como um cliente de &quot;sincronização de desktop&quot; para AEM Assets. O principal benefício AEM aplicativo de desktop aqui é fornecer acesso &quot;virtual&quot; a todo o repositório, e os aplicativos de sincronização de desktop normalmente sincronizam apenas os ativos pertencentes a um usuário. AEM aplicativo para desktop fornece um certo nível de armazenamento em cache e upload em segundo plano; mesmo assim, funciona de forma muito diferente dos aplicativos &quot;Sincronizar&quot; típicos, como o aplicativo de desktop Adobe Creative Cloud ou o Microsoft OneDrive.

* Não use unidades de rede AEM aplicativo desktop para salvar ativos com frequência. Todas as operações de salvamento são transmitidas para a AEM Assets. Portanto, não é prático executar operações de edição intensiva diretamente no repositório AEM Assets montado. A edição de um ativo diretamente no repositório montado encaixa a linha do tempo do ativo com versões irrelevantes e impõe sobrecargas adicionais no servidor.

* Não use AEM aplicativo de desktop para a migração de grandes quantidades de dados de uma instância AEM para outra. Consulte o [Guia de Migração](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html) para planejar e executar migrações de ativos. Por outro lado, o aplicativo de desktop [suporta o carregamento em massa](use-app-v1.md#bulkupload) de um grande número de ativos pela primeira vez em [!DNL Adobe Experience Manager].

## Recommendations para casos de uso selecionados {#recommendations-for-selected-use-cases}

### Acesso a ativos para usuários criativos {#access-to-assets-for-creative-users}

AEM aplicativo de desktop fornece acesso virtual a todo o repositório DAM - e pode ser complicado para os usuários criativos de desktop encontrar e acessar os ativos certos em seu desktop. Use essas práticas recomendadas para simplificar isso para eles.

* Use os recursos de colaboração na interface do usuário da Web do AEM Assets para fornecer acesso mais direto aos ativos certos para o usuário criativo. Compartilhar pastas ou coleções, fornecer coleções inteligentes (pesquisas salvas) ou enviar notificações com ponteiros para os ativos certos são algumas delas. O usuário criativo pode usar as ações da área de trabalho na interface do usuário da Web para obter acesso rápido a esses ativos em seu desktop.

* Considere as permissões certas para os ativos (controle de acesso) para simplificar a visualização no repositório DAM para os usuários criativos, basicamente limitando seu acesso somente aos ativos de que eles precisam ou estão interessados:

   * Algumas áreas não relevantes para os usuários criativos podem ser negadas para seus grupos de usuários, para removê-los da visualização, também no desktop.

   * A maioria dos ativos no DAM são finais e não devem ser alterados - devem ser somente leitura para os usuários criativos.

   * Somente os ativos que exigem alterações ou retoque devem ser habilitados para gravação para os usuários criativos. Algumas organizações usam AEM Projetos e as pastas que criam para hospedar ativos que ainda estão sujeitos a alterações.

### Pesquisando ativos {#searching-assets}

Para procurar um arquivo que você deseja abrir na área de trabalho:

* Use a interface do usuário da Web da AEM Assets para localizar o ativo. A pesquisa não só é poderosa no AEM Assets (aspectos de pesquisa, pesquisas salvas), como também oferece recursos adicionais para encontrar o ativo certo. Isso inclui filtros adicionais, como a capacidade de pesquisar ativos com base no status (aprovação, expiração), coleções, tarefas, notificações e compartilhar pastas/coleções com outros usuários/grupos.

* Depois de localizar o ativo, use as Ações da área de trabalho na interface AEM para acessar o ativo na área de trabalho.

### Atualização de ativos abertos usando AEM aplicativo de desktop {#updating-assets-opened-using-aem-desktop-app}

Se você editar um ativo diretamente no local mapeado da AEM Assets para um compartilhamento de rede local, o ativo será carregado para AEM sempre que você salvá-lo no desktop. Além disso, AEM cria uma versão e gera execuções.

Se um ativo armazenado em AEM precisar de uma atualização:

* Para **atualizações secundárias**, como solicitações de retoque secundárias no processo de aprovação:

   * Faça check-out do arquivo e abra-o na área de trabalho.

   * Atualize o arquivo.

   * Salve a versão atualizada. O ativo é atualizado e a linha do tempo exibe a versão original para comparação.

* Para **principais atualizações**, como uma solicitação de alteração que requer um pequeno ciclo criativo de WIP:

   * Use a opção Revelar para abrir a pasta apropriada na área de trabalho.

   * Copie o arquivo para uma pasta WIP fora do compartilhamento mapeado da AEM Assets (por exemplo, copie o arquivo para uma pasta sincronizada com o aplicativo de desktop da Adobe Creative Cloud).

   * Trabalhe no arquivo e salve-o intermitentemente. As alterações não são salvas no AEM Assets.

   * Após a conclusão das edições, mova, copie ou salve o arquivo mapeado do AEM para carregá-lo como uma nova versão.

## Desempenho da rede {#network-performance}

Uma boa experiência para os usuários que usam o aplicativo de desktop AEM depende muito de uma conectividade de rede boa e estável entre seus desktops e o servidor AEM, bem como do servidor ajustado para um bom desempenho, especialmente em relação ao upload e atualização de ativos. Essas recomendações são para as equipes de rede/TI em organizações.

### Considerações de rede {#network-considerations}

Para entender as práticas recomendadas sobre a configuração de rede AEM Assets, consulte o documento [AEM Assets Network Considerations](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/assets-migration-guide.html). Alguns dos aspectos importantes que ajudam a otimizar AEM experiência do aplicativo de desktop para os usuários são:

* **Use o Dispatcher** corretamente configurado. Use AEM Dispatcher para obter segurança adicional e verifique se ele está configurado para [AEM conexão do aplicativo desktop para AEM atrás de um dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)

* **Economize largura de banda**. Considere desativar a pré-visualização de ícone no Finder no Mac - ao navegar pelo repositório montado usando o Finder. O Finder solicita que cada arquivo gere uma pré-visualização e faz com que o aplicativo de desktop baixe e armazene o ativo em cache localmente. Observe que, ao economizar largura de banda, isso também diminuiria a experiência do usuário para os usuários no desktop, portanto, isso deve ser feito ao trabalhar com repositórios com ativos grandes e/ou largura de banda limitada.

>[!NOTE]
>
>Para desativar pré-visualizações de ícones, no Finder vá para [!UICONTROL View], selecione [!UICONTROL View Options] e desmarque a opção [!UICONTROL Show icon preview]. Isso só funciona para a pasta atual - para torná-la padrão, clique na opção [!UICONTROL Use as default] na mesma caixa de diálogo.

### Otimizando o desempenho do servidor {#optimizing-server-performance}

Para entender como o servidor AEM Assets deve ser otimizado para desempenho, consulte [AEM Assets Performance Tuning Guide](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html). Alguns dos aspectos importantes do desempenho do servidor para aplicativos de desktop AEM estão relacionados à otimização da configuração do fluxo de trabalho para que ele tenha bom desempenho para uploads de ativos:

* **Carregamento** de ativos mais eficiente. Configure o [AEM modelo de fluxo de trabalho de Atualização de ativos para ser temporário](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html).

* **Limitar CPU do servidor para uploads**. Certifique-se de que o parâmetro de trabalho de fluxo de trabalho paralelo máximo esteja definido corretamente, de modo que os uploads não esgotem toda a CPU.
