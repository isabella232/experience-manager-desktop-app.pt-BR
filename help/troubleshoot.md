---
title: Práticas recomendadas e solução de problemas para aplicativos de desktop Adobe Experience Manager
description: Siga as práticas recomendadas e solucione problemas para resolver problemas ocasionais relacionados à instalação, atualização, configuração e assim por diante.
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4e2926adfe46265c78f85b63696c98859f895134
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 1%

---


# Troubleshoot Adobe Experience Manager desktop app {#troubleshoot-v2}

O aplicativo de desktop Adobe Experience Manager (AEM) se conecta a um repositório DAM (Digital Asset Management, gerenciamento de ativos digitais) de implantação remota do Experience Manager. O aplicativo obtém informações do repositório e resultados da pesquisa em seu computador, baixa e carrega arquivos e pastas e inclui recursos para gerenciar conflitos com a interface do usuário do AEM Assets.

Leia para solucionar problemas do aplicativo, aprender as práticas recomendadas e descobrir as limitações.

## Best practices {#best-practices-to-prevent-troubles}

Siga as práticas recomendadas a seguir para evitar alguns problemas comuns e a solução de problemas.

* **Entenda como o aplicativo de desktop funciona**: Antes de começar a usar o aplicativo, passe alguns momentos sabendo como ele funciona. Saiba mais sobre a vinculação entre a interface da Web do Experience Manager e o desktop, o mapeamento do repositório, o armazenamento em cache de ativos, a gravação local e o upload em segundo plano. Veja [como funciona](release-notes.md#how-app-works).

* **Evite caracteres não suportados em nomes** de pastas: Não use espaços em branco e caracteres inválidos ao criar ou carregar pastas. Consulte uma lista de caracteres em [Criar pastas em Ativos](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/managing-assets-touch-ui.html#Creatingfolders)Experience Manager. Alguns casos de uso de Adobe Experience Manager podem ser afetados por caracteres não suportados no nome da pasta.

* **Práticas recomendadas para evitar conflitos**: Para evitar conflitos em potencial ao colaborar em vários ativos, consulte [evitar conflitos](using.md#adv-workflow-collaborate-avoid-conflicts)de edição.

* **Use o upload de pasta para pastas** grandes e hierárquicas: Em vez de usar a interface da Web do Assets ou outros métodos, use o aplicativo de desktop Experience Manager para fazer upload de pastas grandes. O aplicativo carrega os ativos em segundo plano com o registro e o monitoramento. Consulte [fazer upload de ativos](using.md#bulk-upload-assets)em massa.

* **Use a versão** mais recente: Use a versão mais recente do aplicativo e sempre verifique a compatibilidade antes de instalar uma nova versão do aplicativo ou antes de atualizar para uma versão mais nova do Adobe Experience Manager. See [release notes](release-notes.md).

* **Use a mesma letra** de unidade: Use a mesma letra de unidade em uma organização para mapear para o Adobe Experience Manager DAM. Para ver os ativos colocados por outros usuários, os caminhos devem ser os mesmos. Usar a mesma letra de unidade garante um caminho constante para ativos DAM. Os ativos permanecem posicionados e não são removidos mesmo se letras de unidade diferentes forem usadas por usuários diferentes.

* **Lembre-se da rede**: O desempenho da rede é essencial para o desempenho do aplicativo de desktop Experience Manager. Se você enfrentar uma resposta lenta a transferências de arquivos ou operações em massa, desative os recursos ou aplicativos que podem causar muito tráfego de rede.

* **Casos de uso não suportados para aplicativos** de desktop: Não use o aplicativo para a migração do Assets (ele precisa de planejamento e outras ferramentas); para operações DAM de uso intenso (como mover pastas grandes, uploads grandes, localizar arquivos usando pesquisas avançadas de metadados); e como um cliente de sincronização (os princípios de design e os padrões de uso são diferentes dos clientes sincronizados, como o Microsoft OneDrive ou a sincronização de desktop da Adobe Creative Cloud).

* **Tempo limite**: Atualmente, o aplicativo de desktop não tem um valor de tempo limite configurável que desconecta a conexão entre o servidor de Experience Manager e o aplicativo de desktop após um intervalo de tempo fixo. Ao fazer upload de ativos grandes, se a conexão expirar depois de algum tempo, o aplicativo tentativas fazer upload do ativo algumas vezes aumentando o tempo limite de upload. Não há uma maneira recomendada de alterar as configurações de tempo limite padrão.

## Como solucionar problemas {#troubleshooting-prep}

Para solucionar problemas com o aplicativo de desktop, tenha em mente as seguintes informações. Além disso, ele o prepara para transmitir melhor os problemas ao Atendimento ao cliente da Adobe se você optar por buscar suporte.

### Ativar o modo de depuração {#enable-debug-mode}

Para solucionar problemas, você pode ativar o modo de depuração e obter mais informações nos registros. Para usar o aplicativo no modo de depuração no Mac, use as seguintes opções de linha de comando em um terminal ou no prompt de comando: `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`.

Para ativar o modo de depuração no Windows, siga estas etapas:

1. Localize `Adobe Experience Manager Desktop.exe.config` o arquivo na pasta de instalação do aplicativo de desktop. By default, the folder is `C:\Program Files\Adobe\Adobe Experience Manager Desktop`.

1. Localize `<level value="INFO"/>` perto do final do arquivo. Altere o valor de `INFO` para `DEBUG`, que é `<level value="DEBUG"/>`. Salve e feche o arquivo.

1. Localize `logging.json` o arquivo na pasta de instalação do aplicativo de desktop. By default, the folder is `C:\Program Files\Adobe\Adobe Experience Manager Desktop\javascript\`.

1. No `logging.json` arquivo, localize todas as instâncias de `"level": "info"`. Altere os valores de `info` para `debug`. Salve e feche o arquivo.

1. Limpe os diretórios em cache que estão no local definido nas [Preferências](/help/install-upgrade.md#set-preferences)do aplicativo.

1. Reinicie o aplicativo de desktop.

<!-- The Windows command doesn't work for now.
* On Windows: `SET AEM_DESKTOP_LOG_LEVEL=DEBUG & "C:\Program Files\Adobe\Adobe Experience Manager Desktop\Adobe Experience Manager Desktop.exe"`
-->

### Localização dos ficheiros de registro {#check-log-files-v2}

Você pode encontrar os arquivos de registro para o aplicativo de desktop AEM nos seguintes locais. Ao fazer upload de muitos ativos, se alguns arquivos não forem carregados, consulte o `backend.log` arquivo para identificar os uploads que falharam.

* Caminho no Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

* Caminho no Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

>[!NOTE]
>
>Ao trabalhar com o Atendimento ao cliente da Adobe em uma solicitação/ticket de suporte, você pode ser solicitado a compartilhar os arquivos de registro para ajudar a equipe do Atendimento ao cliente a entender o problema. Arquive a `Logs` pasta inteira e compartilhe-a com seu contato com o Atendimento ao cliente.

### Limpar cache {#clear-cache-v2}

Limpar o cache do aplicativo de desktop do AEM é uma tarefa preliminar de solução de problemas que pode resolver vários problemas. Limpe o cache das preferências do aplicativo. Consulte [Definir preferências](install-upgrade.md#set-preferences). O local padrão da pasta de cache é:

* No Windows: `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

* No Mac: `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

No entanto, o local pode mudar dependendo do ponto de extremidade AEM configurado para desktop do AEM. O valor é uma versão codificada do URL direcionado. Por exemplo, se o aplicativo estiver direcionando `http://localhost:4502`, o nome do diretório será `http%3A%2F%2Flocalhost%3A4502%2F`. Para limpar o cache, exclua a pasta apropriada. Outro motivo para limpar o cache é liberar espaço em disco quando você está com pouco espaço em disco.

>[!CAUTION]
>
>Se você limpar o cache da área de trabalho do AEM, as modificações de ativos locais que não são sincronizadas com o servidor do AEM serão irrevogavelmente perdidas.

### Conheça a versão do aplicativo para desktop do AEM {#know-app-version-v2}

Clique no menu ![](assets/do-not-localize/more_options_da2.png) Aplicativo para abrir o menu do aplicativo e clique em **[!UICONTROL Help]** > **[!UICONTROL About]**.

## Não é possível ver ativos colocados {#placed-assets-missing}

Se você não conseguir ver os ativos que você ou outros profissionais criativos colocaram nos arquivos de suporte (por exemplo, arquivos INDD), verifique o seguinte:

* Conexão com o servidor. A conectividade de rede flexível pode paralisar os downloads de ativos.
* Tamanho de arquivo. Ativos grandes demoram mais para serem baixados e exibidos.
* Aumente a consistência da letra. Se você ou outro colaborador tiver colocado os ativos ao mapear o AEM DAM para uma letra de unidade diferente, os ativos colocados não serão exibidos.
* Permissões. Para verificar se você tem permissões para buscar os ativos inseridos, entre em contato com o administrador do AEM.

## Problemas ao atualizar no macOS {#issues-when-upgrading-on-macos}

Ocasionalmente, podem ocorrer problemas ao atualizar o aplicativo de desktop AEM no MacOS. Isso é causado pelo fato de a pasta de sistema herdada para o aplicativo de desktop AEM impedir que novas versões do aplicativo de desktop AEM sejam carregadas corretamente. Para resolver esse problema, as pastas e os arquivos a seguir podem ser removidos manualmente.

Antes de executar as etapas a seguir, arraste o `Adobe Experience Manager Desktop` aplicativo da pasta Aplicativos MacOS para a lixeira. Em seguida, abra o terminal, execute o seguinte comando e forneça sua senha quando solicitado.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## Não é possível carregar arquivos {#upload-fails}

Se você estiver usando um aplicativo de desktop com AEM 6.5.1 ou posterior, atualize o conector S3 ou Azure para a versão 1.10.4 ou posterior. Ele resolve o problema de falha de carregamento de arquivo relacionado ao [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). Consulte as instruções [de](install-upgrade.md#install-v2)instalação.

## Problema de configuração de SSL {#ssl-config-v2}

As bibliotecas que o aplicativo de desktop AEM usa para comunicação HTTP utilizam imposição rigorosa de SSL. Às vezes, uma conexão pode ser bem-sucedida usando um navegador, mas falha ao usar o aplicativo de desktop do AEM. Para configurar o SSL adequadamente, instale o certificado intermediário ausente no Apache. Consulte [Como instalar um certificado CA intermediário no Apache](https://access.redhat.com/solutions/43575).

## O aplicativo não está respondendo {#unresponsive}

Raramente, o aplicativo pode ficar sem resposta, exibir apenas uma tela branca ou exibir um erro na parte inferior da interface, sem nenhuma opção na interface. Tente o seguinte na ordem:

* Clique com o botão direito do mouse na interface do aplicativo e clique em **[!UICONTROL Refresh]**.
* Saia do aplicativo e abra-o novamente.

Em ambos os métodos, os start do aplicativo na pasta DAM raiz.

>[!MORELIKETHIS]
>
>* [Problemas conhecidos](release-notes.md#known-issues-v2)
>* [Evitar conflitos de edição](using.md#adv-workflow-collaborate-avoid-conflicts)