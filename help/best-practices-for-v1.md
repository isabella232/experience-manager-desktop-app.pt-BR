---
title: Práticas recomendadas para aplicativos de desktop AEM versão 1.x
description: Principais recursos e uso recomendado do aplicativo Adobe Experience Manager para desktop versão 1.x.
uuid: ba8fbc74-e1ad-4085-a031-ffd317628ba6
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 57d5cd78-abce-4ede-a50e-7c161ddb43ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ad5337c8e1697d0a37d3020d25802dc1d732f320

---


# Práticas recomendadas do aplicativo de desktop AEM v1.x {#aem-desktop-app-best-practices}

## Visão geral {#overview}

O aplicativo de desktop Adobe Experience Manager (AEM) vincula sua solução de Gerenciamento de ativos digitais (DAM) ao seu desktop para que você possa abrir os arquivos disponíveis na interface do usuário da Web do AEM diretamente no desktop. Se você salvar um ativo do desktop, ele será carregado no AEM no local apropriado.

O aplicativo de desktop AEM elimina as chances de você atualizar cópias locais incorretas ou atualizar um ativo errado no AEM. o fluxo de trabalho fácil de usar do aplicativo desktop é ativado usando a tecnologia de compartilhamento de rede fornecida pelos sistemas operacionais de desktop.

O aplicativo de desktop monta o repositório AEM Assets como um compartilhamento de rede no desktop. Portanto, as pastas e os arquivos aparecem como se fossem locais. No entanto, não é recomendado realizar operações de gerenciamento de ativos digitais diretamente do desktop no compartilhamento de rede montado no Finder ou no Explorer. Em vez disso, a Adobe recomenda usar a interface do usuário do AEM Assets para executar operações, como copiar ou mover um grande número de ativos.

>[!NOTE]
>
>Antes de ler este documento, você pode consultar as práticas [recomendadas gerais de integração do](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-integration-best-practices.html) AEM e da Creative Cloud para obter uma visão geral de nível superior do tópico.

## AEM desktop app architecture {#aem-desktop-app-architecture}

O aplicativo de desktop AEM usa compartilhamentos de rede WebDAV (Windows) ou SMB (Mac) para montar compartilhamentos de rede. O compartilhamento de rede montado é somente local. O aplicativo de desktop AEM intercepta as chamadas (abrir, ler, gravar) e fornece armazenamento em cache local adicional. Ele traduz chamadas remotas para o servidor de ativos AEM para solicitações HTTP de AEM otimizadas. O diagrama a seguir descreve a arquitetura do aplicativo para desktop do AEM.

![Arquitetura de aplicativo para desktop do AEM](assets/chlimage_1.png)

O cache adicional de gravação quando um arquivo é salvo faz com que o arquivo seja salvo localmente primeiro (para que o usuário não aguarde a transferência da rede). Depois de um atraso predefinido (30 s), o arquivo é carregado no AEM em segundo plano e o ativo é carregado no AEM. O aplicativo de desktop AEM fornece uma interface para monitorar o status de uploads de arquivos em segundo plano.

## Uso recomendado do aplicativo de desktop AEM {#recommended-use-of-aem-desktop-app}

Os principais recursos do aplicativo de desktop AEM incluem:

* Abrindo arquivos da interface do usuário da Web do AEM Assets no desktop: Na interface do usuário da Web, você pode revelar ativos na área de trabalho (no Finder, no Explorer) ou abrir um ativo usando um aplicativo de área de trabalho.
* Check-out e check-in: É possível fazer check-out dos ativos para edição, eles são marcados como bloqueados para o usuário nos ativos AEM. Após a edição, é possível fazer check-in do ativo para desbloqueá-lo.
* Salve as alterações nos arquivos: Qualquer alteração que você salvar no arquivo no compartilhamento de rede será carregada automaticamente no AEM e uma nova versão será criada.
* Coloque ativos vinculados em outros documentos: Em aplicativos como a Creative Cloud (PS, ID, AI etc), você pode colocar um arquivo externo como um link (por exemplo, você pode inserir uma imagem em um documento do InDesign). Nesse caso, a montagem de compartilhamento de rede permite que você navegue e selecione ativos do AEM para colocação. A inserção de arquivos vinculados também funciona em alguns aplicativos que não são da Adobe, como o MS Office.
* Resolução de referência no AEM: Se os arquivos inseridos e o arquivo principal com links estiverem armazenados no AEM, ele poderá fornecer automaticamente informações do lado do servidor sobre as referências dos ativos.
* Acesse o ativo da área de trabalho: No compartilhamento de rede montado, um menu contextual fornece uma caixa de diálogo Mais informações (visualização maior, metadados principais) e a capacidade de abrir um ativo na interface do usuário do AEM.
* Carregando pastas grandes e hierárquicas em massa: Se você usar a opção Criar &gt; Carregamento de pasta na interface do usuário do AEM para fazer upload de ativos, o aplicativo da área de trabalho do AEM fará upload da hierarquia de pastas selecionada para o AEM em segundo plano. O progresso do upload pode ser monitorado com uma interface dedicada no aplicativo de desktop.

## Uso inadequado do aplicativo de desktop AEM {#inappropriate-use-of-aem-desktop-app}

* Não use o aplicativo de desktop AEM para gerenciar ativos da área de trabalho. O aplicativo de desktop AEM não foi criado como uma substituição para unidades de rede. Em vez disso, use os seguintes recursos:
   * Interface do usuário da Web do AEM Assets para gerenciamento de ativos digitais (localizar/compartilhar ativos, metadados, copiar/mover etc.)
   * Carregamento de pasta do aplicativo para desktop AEM para carregar pastas grandes e hierárquicas

* Não trate o aplicativo de desktop do AEM como um cliente de "sincronização de desktop" para os ativos AEM. O principal benefício do aplicativo de desktop AEM aqui é que ele fornece acesso "virtual" ao repositório inteiro e os aplicativos de sincronização de desktop normalmente sincronizam apenas os ativos pertencentes a um usuário. O aplicativo de desktop AEM fornece algum nível de cache e upload em segundo plano; ainda assim, funciona de forma muito diferente dos aplicativos "Sincronizar" típicos, como o aplicativo de desktop da Adobe Creative Cloud ou o Microsoft OneDrive.
* Não use unidades de rede de aplicativos de desktop do AEM para salvar ativos com frequência. Todas as operações de salvamento são transmitidas para os ativos AEM. Portanto, não é prático executar operações de edição intensiva diretamente no repositório montado do AEM Assets. A edição de um ativo diretamente no repositório montado encaixa a linha do tempo do ativo com versões irrelevantes e impõe sobrecargas adicionais no servidor.
* Não use o aplicativo de desktop do AEM para migrar grandes quantidades de dados de uma instância do AEM para outra. Consulte o Guia [de](https://helpx.adobe.com/experience-manager/6-4/assets/using/assets-migration-guide.html) Migração para planejar e executar migrações de ativos. Por outro lado, o aplicativo de desktop [oferece suporte ao carregamento](use-app-v1.md#bulkupload) em massa de um grande número de ativos pela primeira vez no AEM.

## Recomendações para casos de utilização selecionados {#recommendations-for-selected-use-cases}

### Acesso a ativos para usuários criativos {#access-to-assets-for-creative-users}

O aplicativo de desktop AEM fornece acesso virtual a todo o repositório DAM - e pode ser complicado para os usuários criativos de desktop encontrar e acessar os ativos certos em seu desktop. Use essas práticas recomendadas para simplificar isso para eles.

* Use os recursos de colaboração na interface do usuário do AEM Assets para fornecer acesso mais direto aos ativos certos para o usuário criativo. Compartilhar pastas ou coleções, fornecer coleções inteligentes (pesquisas salvas) ou enviar notificações com ponteiros para os ativos certos são algumas delas. O usuário criativo pode usar as ações da área de trabalho na interface do usuário da Web para obter acesso rápido a esses ativos em seu desktop.
* Considere as permissões certas para ativos (controle de acesso) para simplificar a visualização no repositório DAM para os usuários criativos, basicamente limitando seu acesso somente aos ativos de que eles precisam / que estão interessados:

   * Algumas áreas não relevantes para os usuários criativos podem ser negadas para seus grupos de usuários, para removê-los de sua visão, também no desktop
   * A maioria dos ativos no DAM são finais e não se destinam à alteração - devem ser somente leitura para os usuários criativos
   * Somente os ativos que exigem alterações / retoque devem ser habilitados para gravação para os usuários criativos. Algumas organizações usam os projetos AEM e as pastas que criam para hospedar ativos que ainda estão sujeitos a alterações.

### Pesquisar ativos {#searching-assets}

Para procurar um arquivo que deseja abrir na área de trabalho:

* Use a interface do usuário do AEM Assets para localizar o ativo. A pesquisa nos ativos AEM é poderosa (aspectos de pesquisa, pesquisas salvas), além de fornecer recursos adicionais para encontrar o ativo certo. Eles incluem filtros adicionais, como a capacidade de pesquisar ativos com base no status (aprovação, expiração), coleções, tarefas, notificações e compartilhar pastas/coleções com outros usuários/grupos.
* Depois de localizar o ativo, use as Ações da área de trabalho na interface do usuário do AEM para acessar o ativo na área de trabalho.

### Atualizar ativos abertos usando o aplicativo de desktop do AEM {#updating-assets-opened-using-aem-desktop-app}

Se você editar um ativo diretamente no local mapeado dos ativos AEM para um compartilhamento de rede local, o ativo será carregado no AEM sempre que você salvá-lo no desktop. Além disso, o AEM cria uma versão e gera execuções.

Se um ativo armazenado no AEM precisar de uma atualização:

* Para atualizações **** menores, como solicitações de retoque secundárias no processo de aprovação:

   * Verifique o arquivo e abra-o na área de trabalho
   * Atualizar o arquivo
   * Salve a versão atualizada. O ativo é atualizado e a linha do tempo exibe a versão original para comparação

* Para **grandes atualizações**, como uma solicitação de alteração que requer um pequeno ciclo criativo de WIP:

   * Use a opção Revelar para abrir a pasta apropriada na área de trabalho
   * Copie o arquivo para uma pasta WIP fora do compartilhamento dos ativos AEM mapeados (por exemplo, copie o arquivo para uma pasta sincronizada com o aplicativo de desktop da Adobe Creative Cloud)
   * Trabalhe no arquivo e salve-o intermitentemente. As alterações não são salvas nos ativos AEM
   * Após a conclusão das edições, mova, copie ou salve o arquivo mapeado do AEM para carregá-lo como uma nova versão

## Desempenho da rede {#network-performance}

Uma boa experiência para os usuários que usam o aplicativo de desktop AEM depende muito de uma conectividade de rede boa e estável entre seus desktops e o servidor AEM, bem como do servidor ajustado para proporcionar um bom desempenho, especialmente ao fazer upload e atualizar ativos. Essas recomendações são para as equipes de rede/TI em organizações.

### Considerações de rede {#network-considerations}

Para entender as práticas recomendadas sobre a configuração de rede do AEM Assets, consulte o documento Considerações [de rede do](https://helpx.adobe.com/experience-manager/6-4/assets/using/assets-network-considerations.html) AEM Assets. Alguns dos aspectos importantes que ajudam a otimizar a experiência do aplicativo de desktop do AEM para os usuários incluem:

* **** Usar o Dispatcher corretamente configurado: Use o AEM Dispatcher para obter segurança adicional e verifique se ele está configurado para conexão de aplicativo de desktop do [AEM com o AEM atrás de um dispatcher](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#ConnectingtoAEMBehindaDispatcher)

* **** Salvar largura de banda: Considere desativar a visualização do ícone no Finder no Mac - ao navegar pelo repositório montado usando o Finder. O Finder solicita que cada arquivo gere uma visualização e faz com que o aplicativo desktop baixe e armazene o ativo em cache localmente. Observe que, ao economizar largura de banda, isso também diminuiria a experiência do usuário para os usuários no desktop, portanto, isso deve ser feito ao trabalhar com repositórios com ativos grandes e/ou largura de banda limitada.

>[!NOTE]
>
>Para desativar visualizações de ícones, no Finder vá para Exibir, selecione Opções de visualização e desmarque a opção "Mostrar visualização de ícones". Isso só funciona para a pasta atual - para torná-la padrão, clique no botão "Usar como padrão" na mesma janela.

### Otimizando o desempenho do servidor {#optimizing-server-performance}

Para entender como o servidor do AEM Assets deve ser otimizado para desempenho, consulte o Guia [de ajuste de desempenho do](https://helpx.adobe.com/in/experience-manager/6-4/assets/using/performance-tuning-guidelines.html)AEM Assets. Alguns dos aspectos importantes do desempenho do servidor para aplicativos de desktop do AEM são a otimização da configuração do fluxo de trabalho para que ele tenha bom desempenho para uploads de ativos:

* **** Carregamento de ativos mais eficiente: Configure o modelo de fluxo de trabalho de Atualização de ativos [AEM para ser temporário](https://helpx.adobe.com/experience-manager/6-4/assets/using/performance-tuning-guidelines.html#Workflows).

* **** Limitar CPU do servidor para uploads: Certifique-se de que o parâmetro de trabalho de fluxo de trabalho paralelo máximo esteja definido corretamente, para que os uploads não esgotem toda a CPU.