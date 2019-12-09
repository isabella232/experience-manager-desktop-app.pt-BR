---
title: Práticas recomendadas para o aplicativo de desktop AEM e solução de problemas
description: Siga as práticas recomendadas e solucione problemas para resolver problemas ocasionais relacionados à instalação, atualização, configuração e assim por diante.
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ad5337c8e1697d0a37d3020d25802dc1d732f320

---


# Troubleshoot AEM desktop app {#troubleshoot-v2}

O aplicativo de desktop Adobe Experience Manager (AEM) se conecta a um repositório DAM (Digital Asset Management, Gerenciamento de ativos digitais) remoto da implantação do AEM. O aplicativo obtém informações do repositório e resultados da pesquisa em seu computador, baixa e carrega arquivos e pastas e inclui recursos para gerenciar conflitos com a interface do usuário do AEM Assets.

Leia para solucionar problemas do aplicativo, aprender as práticas recomendadas e descobrir as limitações.

## Best practices {#best-practices-to-prevent-troubles}

Siga as seguintes práticas recomendadas para evitar alguns problemas comuns e a solução de problemas.

* **Entenda como o aplicativo de desktop funciona**: Antes de começar a usar o aplicativo, aguarde alguns minutos sabendo como ele funciona. Saiba mais sobre a vinculação entre a interface do usuário da Web e a área de trabalho, o mapeamento do repositório, o armazenamento em cache de ativos, a gravação local e o upload em segundo plano. Veja [como funciona](release-notes.md#how-app-works).

* **Evite caracteres não suportados em nomes** de pastas: Não use espaços em branco e caracteres inválidos ao criar ou carregar pastas. Consulte uma lista de caracteres em [Criar pastas nos ativos](https://helpx.adobe.com/experience-manager/6-5/assets/using/managing-assets-touch-ui.html#Creatingfolders)AEM. Alguns casos de uso do AEM podem ser afetados por caracteres não suportados no nome da pasta.

* **Práticas recomendadas para evitar conflitos**: Para evitar conflitos em potencial ao colaborar em vários ativos, consulte [evitar conflitos](using.md#adv-workflow-collaborate-avoid-conflicts)de edição.

* **Use o upload de pasta para pastas** grandes e hierárquicas: Em vez de usar a interface da Web do Assets ou outros métodos, use o aplicativo de desktop do AEM para carregar pastas grandes. O aplicativo carrega os ativos em segundo plano com o registro e o monitoramento. Consulte ativos [de upload em](using.md#bulk-upload-assets)massa.

* **Use a versão** mais recente: Use a versão mais recente do aplicativo e sempre verifique a compatibilidade antes de instalar uma nova versão do aplicativo ou antes de atualizar para uma versão mais recente do AEM. Consulte as notas [de versão](release-notes.md).

* **Use a mesma letra** de unidade: Use a mesma letra de unidade em uma organização para mapear para o AEM DAM. Para ver os ativos colocados por outros usuários, os caminhos devem ser os mesmos. Usar a mesma letra de unidade garante um caminho constante para ativos DAM. Os ativos permanecem posicionados e não são removidos mesmo se letras de unidade diferentes forem usadas por usuários diferentes.

* **Lembre-se da rede**: O desempenho da rede é essencial para o desempenho do aplicativo de desktop AEM. Se você enfrentar uma resposta lenta a transferências de arquivos ou operações em massa, desative os recursos ou aplicativos que podem causar muito tráfego de rede.

* **Casos de uso não suportados para aplicativos** de desktop: Não use o aplicativo para a migração do Assets (ele precisa de planejamento e outras ferramentas); para operações DAM de uso intenso (como mover pastas grandes, uploads grandes, localizar arquivos usando pesquisas avançadas de metadados); e como um cliente de sincronização (os princípios de design e os padrões de uso são diferentes dos clientes sincronizados, como o Microsoft OneDrive ou a sincronização de desktop da Adobe Creative Cloud).

## Como solucionar problemas {#troubleshooting-prep}

Para solucionar problemas com o aplicativo de desktop, tenha em mente as seguintes informações. Além disso, ele o prepara para transmitir melhor os problemas ao Atendimento ao cliente da Adobe se você optar por buscar suporte.

### Ativar modo de depuração {#enable-debug-mode}

Para solucionar problemas, você pode ativar o modo de depuração e obter mais informações nos registros. Para executar o aplicativo no modo de depuração, use as seguintes opções de linha de comando em um terminal ou no prompt de comando.

* No Windows: `SET AEM_DESKTOP_LOG_LEVEL=DEBUG & "C:\Program Files\Adobe\Adobe Experience Manager Desktop\Adobe Experience Manager Desktop.exe"`

* No Mac: `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`

### Localização dos ficheiros de registro {#check-log-files-v2}

Você pode encontrar os arquivos de registro para o aplicativo de desktop AEM nos seguintes locais. Ao carregar muitos ativos, se alguns arquivos não forem carregados, consulte o arquivo no local acima para identificar os uploads que falharam. `backend.log`

* No Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

* No Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

>[!NOTE]
>
>Ao trabalhar com o Atendimento ao cliente da Adobe em uma solicitação/ticket de suporte, você pode ser solicitado a compartilhar os arquivos de registro para ajudar a equipe de suporte a entender o problema. Arquive a `Logs` pasta inteira e compartilhe-a com o Atendimento ao cliente.

### Limpar cache {#clear-cache-v2}

Limpar o cache do aplicativo de desktop do AEM é uma tarefa preliminar de solução de problemas que pode resolver vários problemas. Limpe o cache das preferências do aplicativo. Consulte [Definir preferências](install-upgrade.md#set-preferences). O local padrão da pasta de cache é:

* No Windows: `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

* No Mac: `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

No entanto, o local pode mudar dependendo do ponto de extremidade AEM configurado para desktop do AEM. O valor é uma versão codificada do URL direcionado. Por exemplo, se o aplicativo estiver direcionando `http://localhost:4502`, o nome do diretório será `http%3A%2F%2Flocalhost%3A4502%2F`. Para limpar o cache, exclua a pasta apropriada. Outro motivo para limpar o cache é liberar espaço em disco quando você está com pouco espaço em disco.

>[!CAUTION]
>
>Se você limpar o cache da área de trabalho do AEM, as modificações de ativos locais que não são sincronizadas com o servidor do AEM serão irrevogavelmente perdidas.

### Conheça a versão do aplicativo para desktop do AEM {#know-app-version-v2}

Clique no menu ![](assets/do-not-localize/more_options_da2.png) Aplicativo para abrir o menu do aplicativo e clique em **[!UICONTROL Help]** &gt; **[!UICONTROL About]**.

## Não é possível ver ativos colocados {#placed-assets-missing}

Se você não conseguir ver os ativos que você ou outros profissionais criativos colocaram nos arquivos de suporte (por exemplo, arquivos INDD), verifique o seguinte:

* Conexão com o servidor. A conectividade de rede flexível pode paralisar os downloads de ativos.
* Tamanho de arquivo. Ativos grandes demoram mais para serem baixados e exibidos.
* Aumente a consistência da letra. Se você ou outro colaborador tiver colocado os ativos ao mapear o AEM DAM para uma letra de unidade diferente, os ativos colocados não serão exibidos.
* Permissões. Para verificar se você tem permissões para buscar os ativos inseridos, entre em contato com o administrador do AEM.

## Problemas ao atualizar no macOS {#issues-when-upgrading-on-macos}

Ocasionalmente, podem ocorrer problemas ao atualizar o aplicativo de desktop AEM no MacOS. Isso é causado pelo fato de a pasta de sistema herdada para o aplicativo de desktop AEM impedir que novas versões do aplicativo de desktop AEM sejam carregadas corretamente. Para resolver esse problema, as pastas e os arquivos a seguir podem ser removidos manualmente.

Antes de executar as etapas a seguir, arraste o `Adobe Experience Manager Desktop` aplicativo da pasta Aplicativos MacOS para a lixeira. Em seguida, abra terminal, execute o seguinte comando e forneça sua senha quando solicitado.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## Não é possível carregar arquivos {#upload-fails}

Se você estiver usando um aplicativo de desktop com AEM 6.5.1 ou posterior, atualize o conector S3 ou Azure para a versão 1.10.4 ou posterior. Ele resolve o problema de falha de carregamento de arquivo relacionado ao [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). Consulte as instruções [de instalação](install-upgrade.md#install-v2).

## Problema de configuração SSL {#ssl-config-v2}

As bibliotecas que o aplicativo de desktop AEM usa para comunicação HTTP utilizam imposição rigorosa de SSL. Às vezes, uma conexão pode ser bem-sucedida usando um navegador, mas falha ao usar o aplicativo de desktop AEM. Para configurar o SSL adequadamente, instale o certificado intermediário ausente no Apache. Consulte [Como instalar um certificado CA intermediário no Apache](https://access.redhat.com/solutions/43575).

## O aplicativo não responde {#unresponsive}

Raramente, o aplicativo pode ficar sem resposta, exibir apenas uma tela branca ou exibir um erro na parte inferior da interface sem nenhuma opção na interface. Tente o seguinte na ordem:

1. Clique com o botão direito do mouse na interface do aplicativo e clique em **[!UICONTROL Refresh]**.
1. Saia do aplicativo e reinicie-o.

Em ambos os métodos, o aplicativo é iniciado na pasta DAM raiz.

>[!MORELIKETHIS]
>
>* [Problemas conhecidos](release-notes.md#known-issues-v2)
>* [Evitar conflitos de edição](using.md#adv-workflow-collaborate-avoid-conflicts)