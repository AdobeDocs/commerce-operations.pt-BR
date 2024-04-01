---
title: Guia de instalação
description: Use este guia para instalar [!DNL Site-Wide Analysis Tool] para o seu site
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: 2501630bdbeb9a80c247fd39dcbe57c327b3244d
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# Guia de instalação

>[!IMPORTANT]
>
>A partir de 23 de abril de 2024, a [!DNL Site-Wide Analysis Tool] será descontinuado para todos os clientes do Adobe Commerce no local.

A variável [!DNL Site-Wide Analysis Tool] O fornece monitoramento, relatórios e recomendações de desempenho em tempo real 24 horas por dia, 7 dias por semana, para garantir a segurança e a operabilidade do Adobe Commerce nas instalações da infraestrutura em nuvem. Ela também fornece informações detalhadas sobre patches disponíveis e instalados, extensões de terceiros e a instalação do Adobe Commerce.

>[!INFO]
>
>Saiba mais [como ativar](../site-wide-analysis-tool/access.md) o [!DNL Site-Wide Analysis Tool] e gerar relatórios.

Se você tiver uma instalação local do Adobe Commerce, instale um agente em sua infraestrutura para usar a ferramenta. Não é necessário instalar o agente no Adobe Commerce em projetos de infraestrutura em nuvem.

## Agente

A variável [!DNL Site-Wide Analysis Tool] O agente permite usar o [!DNL Site-Wide Analysis Tool] para instalações locais do Adobe Commerce.

A variável [!DNL Site-Wide Analysis Tool] O agente coleta dados de aplicativos e de negócios, analisa e fornece insights adicionais sobre a integridade de sua instalação para que você possa melhorar a experiência do cliente. Ele monitora os aplicativos e ajuda a identificar problemas de desempenho, segurança, disponibilidade e aplicativos.

A instalação do agente requer as seguintes etapas:

1. Verifique os requisitos do sistema.

1. Configure as chaves de API no [!UICONTROL Commerce Services Connector] extensão.

1. Instale o agente.

1. Execute o agente.

>[!INFO]
>
>O agente é compatível com instalações de vários nós do Adobe Commerce. Instale e configure o agente em cada nó.

## Requisitos do sistema

Sua infraestrutura local deve atender aos seguintes requisitos antes de instalar o agente:

- Sistemas operacionais

   - [!DNL Linux x86-64] distribuições, como [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian], e similares

  >[!IMPORTANT]
  >
  >O Adobe Commerce não é compatível com o [!DNL Microsoft Windows] ou [!DNL macOS].

- Adobe Commerce 2.4.5-p1 ou posterior (devido à dependência do Service Connector)

- [!DNL Commerce Services Connector extension]

- CLI do PHP

- Utilitários Bash/Shell

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

O agente exige o [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) a ser instalada no sistema e [configurado](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) com chaves de API. Para verificar se a extensão está instalada, execute o seguinte comando:

```bash
bin/magento module:status Magento_ServicesId
```

Se tiver instalado a extensão e a configurado usando uma chave de API existente para um serviço diferente, você **É NECESSÁRIO gerar novamente a chave de API** e atualizá-lo no Adobe Commerce Admin para o agente.

1. Coloque seu site em [modo de manutenção](../../installation/tutorials/maintenance-mode.md).

1. Efetue logon no [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > Se tiver problemas para acessar sua conta, consulte [Não é possível fazer logon no suporte da Adobe Commerce ou na conta da nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) para obter ajuda com a solução de problemas.

1. Clique em **[!UICONTROL API Portal]**.

1. Clique em **[!UICONTROL Delete]** ao lado da chave de API existente.

1. [Configurar](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) uma nova chave de API.

>[!IMPORTANT]
>
> Se você gerar novas chaves no Portal de API, atualize imediatamente as chaves de API no [!DNL Admin configuration]. Se você gerar novas chaves e não atualizar as chaves na variável [!DNL Admin], suas extensões SaaS não funcionarão mais e você perderá dados valiosos.

Se a extensão não estiver instalada, use as seguintes instruções para instalá-la:

1. Adicione a extensão ao `composer.json` arquivo e instale-o.

   ```bash
   composer require magento/services-id
   ```

1. Ative a extensão.

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. Atualize o esquema do banco de dados.

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:clean
   ```

1. [Configurar chaves de API](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) para conectar a extensão ao sistema.

## Instalar o agente

Criamos um [script de shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) para simplificar a instalação. Recomendamos o uso do script de shell, mas você pode seguir o [instalação manual](#manual) se necessário.

>[!INFO]
>
>Após a instalação do agente, ele se autoatualizará quando uma nova versão estiver disponível.

### Com script

1. Baixe e execute o script de shell.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >Recomendamos instalar o agente fora do diretório raiz do projeto Adobe Commerce.

1. Verifique a instalação.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Após fazer o download e instalar o agente, [configurá-lo para executar](#run-the-agent) usando um dos seguintes métodos:

   - [Serviço](#service) (preferencial se você tiver acesso de raiz)

   - [Cron](#cron)

### Manual {#manual}

Se você não quiser usar nosso [script de shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) para instalar o agente, você deve instalá-lo manualmente seguindo estas etapas:

1. Crie um diretório no qual deseja fazer download do agente.

   >[!TIP]
   >
   >Recomendamos instalar o agente fora do diretório raiz do projeto Adobe Commerce.

1. Baixe o arquivo binário e descompacte-o.

   >[!INFO]
   >
   >Para usar o [!DNL Site-Wide Analysis Tool], você deve primeiro ler e aceitar os Termos de uso que são apresentados quando você acessa o painel pelo Administrador do Adobe Commerce.

   Para o **AMD64** Arquitetura:

   1. Baixe o arquivo iniciador.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Descompacte o arquivo iniciador.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   Para o **ARM64** Arquitetura:

   1. Baixe o arquivo iniciador.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Descompacte o arquivo iniciador.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *(Opcional)* Verifique a assinatura do arquivo de checksum.

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *(Opcional)* Verifique a soma de verificação.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. Crie o `config.yaml` com o seguinte conteúdo.

   ```yaml
   project:
     appname: "Acme Inc" # Company or site name that you provided when installing the agent
   application:
     phppath: php # Path to your PHP CLI interpreter (usually /usr/bin/php)
     magentopath: /var/www/html/example.com # Root directory where your Adobe Commerce application is installed (usually /var/www/html)
     checkregistrypath: /path/to/swat-agent/tmp # Temporary directory for the agent (usually /usr/local/swat-agent/tmp)
     issandbox: false # Enabling sandbox mode to use the agent on staging environment (true or false)
     database:
       user: your-adobe-commerce-db-username # Database user for your Adobe Commerce installation
       password: your-password # Database password for the specified user for your Adobe Commerce installation
       host: 127.0.0.1 # Database host for your Adobe Commerce installation
       dbname: your-adobe-commerce-db-name # Database name for your Adobe Commerce installation
       port: 3306 # Database port for your Adobe Commerce installation (usually 3306)
       tableprefix: # Table Prefix for your Adobe Commerce installation (default value: empty)
    enableautoupgrade: true # Enables automatic upgrade (restart required after an upgrade; agent does not check for upgrades if the option is disabled; true or false)
    runchecksonstart: true # Collect data on the first run (Usually 1)
    loglevel: error # Determines what events are logged based on severity (usually error)
   ```

1. Verifique a instalação.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Depois de fazer download e instalar o agente, você deve [configurá-lo para executar](#run-the-agent) usando um dos seguintes métodos:

   - [Serviço](#service) (preferencial se você tiver acesso de raiz)

   - [Cron](#cron)

## Executar o agente {#run-the-agent}

Recomendamos configurar o agente para ser executado como um serviço. Se você tiver acesso limitado à sua infraestrutura e não tiver permissões raiz, deverá usar [cron](#cron) em vez disso.

### Serviço {#service}

1. Criar um arquivo de unidade do sistema `(/etc/systemd/system/scheduler.service)` com a seguinte configuração (substituir `<filesystemowner>` com o usuário UNIX® que possui o diretório onde o agente e o software Adobe Commerce estão instalados). Se você baixou o agente como um usuário raiz, altere o diretório e o proprietário dos arquivos aninhados.

   ```config
   [Unit]
   Wants=network.target
   After=network.target
   
   [Service]
   Type=simple
   User=<filesystemowner>
   ExecStart=/path/to/agent/scheduler
   Restart=always
   RestartSec=3
   
   [Install]
   WantedBy=multi-user.target
   ```

1. Inicie o serviço.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. Valide se o serviço está ativo e em execução.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Se você não tiver permissões raiz ou não tiver permissões para configurar um serviço como raiz, poderá usar o cron.

Atualize seu cronograma cron:

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Desinstalar

Execute os seguintes comandos para desinstalar o serviço do sistema e remover todos os arquivos gerados:

1. Interrompa o programador.

   ```bash
   systemctl stop scheduler
   ```

1. Desative o programador.

   ```bash
   systemctl disable scheduler
   ```

1. Remover o do serviço de scheduler `systemd` arquivo de unidade.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Recarregue o `systemd` configuração do gerenciador.

   ```bash
   systemctl daemon-reload
   ```

1. Redefinir qualquer `systemd` unidades de um estado de falha.

   ```bash
   systemctl reset-failed
   ```

1. Remova o diretório de serviço do scheduler.

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. Remova o arquivo binário do scheduler.

   ```bash
   rm /usr/local/bin/scheduler
   ```

Se, em vez disso, você configurou o agente para ser executado com cron, use as seguintes instruções:

1. Remova o agente da lista crontab.

   ```bash
   crontab -e
   ```

1. Interrompa o job em execução.

   ```bash
   ps aux | grep scheduler
   ```

1. Remova o diretório onde você instalou o agente.

   ```bash
   rm -rf swat-agent
   ```

## Solução de problemas

### Chaves de acesso não analisadas corretamente

Você pode observar o seguinte erro se as chaves de acesso não forem analisadas corretamente:

```terminal
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

Para resolver esse erro, tente as seguintes etapas:

1. Fazer um [instalação com script](#scripted), salve a saída e verifique se há erros na saída.
1. Revise o gerado `config.yaml` e verifique se o caminho para a sua instância do Commerce e para o PHP está correto.
1. Verifique se o usuário que está executando o scheduler está na [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md) grupo Unix ou é o mesmo usuário que o proprietário do sistema de arquivos.
1. Certifique-se de que a variável [Conector dos Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) As chaves do estão instaladas corretamente e tente atualizá-las para conectar a extensão ao sistema.
1. [Desinstalar](#uninstall) o agente depois de atualizar as chaves e reinstalar usando o [script de instalação](#scripted).
1. Execute o scheduler e veja se você ainda recebe o mesmo erro.
1. Se você ainda receber o mesmo erro, aumente o nível de log no `config.yaml` para depurar e abrir um tíquete de suporte.

### *SIGFAULT* Erro

Se você vir um *SIGFAULT* erro ao executar o binário, você provavelmente não o executa como proprietário dos arquivos do Adobe Commerce e do Agente.
Para resolver, verifique se todos os arquivos dentro do diretório do agente que têm o mesmo usuário que o proprietário do arquivo que os arquivos Adobe Commerce têm, e se o binário também deve ser executado nesse usuário.
Você pode usar o `chown` comando para alterar o proprietário dos arquivos e alternar para o usuário apropriado.
Certifique-se de que seu mecanismo de daemonização (Cron ou System.d) execute o processo no usuário apropriado.

>[!INFO]
>
>Consulte [Como acessar [!DNL Site-Wide Analysis Tool] e gerar relatórios](../site-wide-analysis-tool/access.md).
