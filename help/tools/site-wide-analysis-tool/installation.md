---
title: Guia de instalação
description: Use este guia para instalar [!DNL Site-Wide Analysis Tool] para o seu site
source-git-commit: de2fb829def2cf94c452a06a219d7f29885c8f9f
workflow-type: tm+mt
source-wordcount: '1050'
ht-degree: 0%

---

# Guia de instalação

O [!DNL Site-Wide Analysis Tool] O oferece monitoramento, relatórios e recomendações em tempo real, 24 horas por dia, 7 dias por semana, para garantir a segurança e a operabilidade do Adobe Commerce nas instalações da infraestrutura em nuvem. Ele também fornece informações detalhadas sobre patches disponíveis e instalados, extensões de terceiros e sua instalação do Adobe Commerce.

>[!INFO]
>
>Saiba mais [como ativar](../site-wide-analysis-tool/access.md) o [!DNL Site-Wide Analysis Tool] e gerar relatórios.

Se você tiver uma instalação local do Adobe Commerce, deverá instalar um agente em sua infraestrutura para usar a ferramenta. Não é necessário instalar o agente no Adobe Commerce em projetos de infraestrutura em nuvem.

## Agente

O [!DNL Site-Wide Analysis Tool] O Agente permite usar o [!DNL Site-Wide Analysis Tool] para instalações no local da Adobe Commerce.

O [!DNL Site-Wide Analysis Tool] O agente coleta dados de aplicativos e negócios, analisa e fornece informações adicionais sobre a integridade de sua instalação para que você possa melhorar a experiência do cliente. Ele monitora seu aplicativo e ajuda a identificar problemas de desempenho, segurança, disponibilidade e aplicativo.

A instalação do agente requer as seguintes etapas:

1. Verifique os requisitos do sistema.

1. Configure as chaves da API no [!UICONTROL Commerce Services Connector] extensão.

1. Instale o agente.

1. Execute o agente.

>[!INFO]
>
>O agente oferece suporte a instalações de vários nós do Adobe Commerce. Você deve instalar e configurar o agente em cada nó.

## Requisitos do sistema

Sua infraestrutura local deve atender aos seguintes requisitos antes de instalar o agente:

- Sistemas operacionais

   - [!DNL Linux x86-64] distribuições, como [!DNL RedHat Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian]e semelhantes
   >[!IMPORTANT]
   >
   >O Adobe Commerce não é compatível com [!DNL Microsoft Windows] ou [!DNL macOS].

- Adobe Commerce 2.4.1 ou posterior

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Utilitários Bash/shell

   - `grep`

   - `awk`

   - `nice`

   - `grep`

## [!DNL Commerce Services Connector]

O agente exige que o [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) para ser instalada em seu sistema e [configurado](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) com chaves de API. Para verificar se a extensão está instalada, execute o seguinte comando:

```bash
bin/magento module:status Magento_ServicesConnector
```

Se tiver instalado e configurado a extensão usando uma chave de API existente para um serviço diferente, **DEVE gerar novamente a chave de API** e atualize-o no Administrador do Adobe Commerce para o agente.

1. Coloque seu site em [modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. Faça logon [accounts.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

1. Clique em **[!UICONTROL API Portal]**.

1. Clique em **[!UICONTROL Delete]** ao lado da Chave da API existente.

1. [Configurar](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) uma nova chave de API.

>[!IMPORTANT]
>
> Se você gerar novas chaves no Portal da API, atualize imediatamente as chaves da API no [!DNL Admin configuration]. Se você gerar novas chaves e não as atualizar na [!DNL Admin], suas extensões SaaS não funcionarão mais e você perderá dados valiosos.

Se a extensão não estiver instalada, use as seguintes instruções para instalá-la:

1. Adicionar a extensão ao `composer.json` e instale-o.

   ```bash
   composer require magento/services-connector:1.*
   ```

1. Habilite a extensão do .

   ```bash
   bin/magento module:enable Magento_ServicesConnector
   ```

1. Atualize o schema do banco de dados.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configurar chaves de API](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) para conectar a extensão ao seu sistema.

## Instalar o agente

Criamos um [script de shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) para simplificar a instalação. Recomendamos o uso do script de shell, mas você pode seguir o [instalação manual](#manual) se necessário.

>[!INFO]
>
>Após o agente ser instalado, ele será atualizado automaticamente quando uma nova versão estiver disponível.

### Script

1. Baixe e execute o script de shell.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >Recomendamos instalar o agente fora do diretório de projeto raiz do Adobe Commerce.

1. Verifique a instalação.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Após baixar e instalar o agente, é necessário [configure-a para ser executada](#run-the-agent) utilizando um dos seguintes métodos:

   - [Serviço](#service) (preferencial se você tiver acesso raiz)

   - [Cron](#cron)

### Manual {#manual}

Se você não quiser usar nosso [script de shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) para instalar o agente, você deve instalá-lo manualmente seguindo estas etapas:

1. Crie um diretório onde deseja baixar o agente.

   >[!TIP]
   >
   >Recomendamos instalar o agente fora do diretório de projeto raiz do Adobe Commerce.

1. Baixe o arquivo binário e descompacte-o.

   >[!INFO]
   >
   >Para usar o [!DNL Site-Wide Analysis Tool], primeiro leia e aceite os Termos de uso que são apresentados quando você acessa o painel pelo Administrador do Adobe Commerce.

   Para o **AMD64** arquitetura:

   1. Baixe o arquivo do iniciador.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Descompacte o arquivo do iniciador.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```
   Para o **ARM64** arquitetura:

   1. Baixe o arquivo do iniciador.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Embale o arquivo do iniciador.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```


1. *(Opcional)* Verifique a assinatura do arquivo de soma de verificação.

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

1. Após baixar e instalar o agente, é necessário [configure-a para ser executada](#run-the-agent) utilizando um dos seguintes métodos:

   - [Serviço](#service) (preferencial se você tiver acesso raiz)

   - [Cron](#cron)

## Executar o agente {#run-the-agent}

Recomendamos configurar o agente para ser executado como um serviço. Se você tiver acesso limitado à sua infraestrutura e não tiver permissões raiz, deverá usar [cron](#cron) em vez disso.

### Serviço {#service}

1. Criar um arquivo de unidade do sistema `(/etc/systemd/system/scheduler.service)` com a seguinte configuração (substitua `<filesystemowner>` com o usuário do Unix que possui o diretório onde o agente está instalado).

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

1. Iniciar o serviço.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. Valide se o serviço está em execução.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Se você não tiver permissões de raiz ou não tiver permissões para configurar um serviço como raiz, poderá usar o cron em vez disso.

Atualize seu cronograma do cron:

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Desinstalar

Execute os seguintes comandos para desinstalar o serviço do sistema e remover todos os arquivos gerados:

1. Pare o programador.

   ```bash
   systemctl stop scheduler
   ```

1. Desative o programador.

   ```bash
   systemctl disable scheduler
   ```

1. Remova o `systemd` arquivo da unidade.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Recarregue o `systemd` configuração do gerenciador.

   ```bash
   systemctl daemon-reload
   ```

1. Reinicie qualquer `systemd` unidades de um estado com falha.

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

Se você configurou o agente para executar com o cron, use as seguintes instruções:

1. Remova o agente da lista crontab.

   ```bash
   crontab -e
   ```

1. Pare o trabalho em execução.

   ```bash
   ps aux | grep scheduler
   ```

1. Remova o diretório onde você instalou o agente.

   ```bash
   rm -rf swat-agent
   ```

## Substituir o arquivo de configuração

Você pode substituir os valores especificados no arquivo de configuração durante a instalação usando variáveis de ambiente. Isso preserva a compatibilidade com versões anteriores do agente. Consulte a tabela a seguir para obter os valores recomendados:

| PROPRIEDADE | DESCRIÇÃO |
| --- | --- |
| `SWAT_AGENT_APP_NAME` | Nome da empresa ou do site fornecido ao instalar o agente |
| `SWAT_AGENT_APPLICATION_PHP_PATH` | Caminho para o seu interpretador da CLI PHP (geralmente `/usr/bin/php`) |
| `SWAT_AGENT_APPLICATION_MAGENTO_PATH` | Diretório raiz onde o aplicativo Adobe Commerce está instalado (normalmente `/var/www/html`) |
| `SWAT_AGENT_APPLICATION_DB_USER` | Usuário do banco de dados para sua instalação do Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_PASSWORD` | Senha do banco de dados para o usuário especificado para sua instalação do Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_HOST` | Host de banco de dados para sua instalação do Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_NAME` | Nome do banco de dados para sua instalação do Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_PORT` | Porta do banco de dados para sua instalação do Adobe Commerce (normalmente `3306`) |
| `SWAT_AGENT_APPLICATION_DB_TABLE_PREFIX` | Prefixo da tabela para sua instalação do Adobe Commerce (valor padrão: `empty`) |
| `SWAT_AGENT_APPLICATION_DB_REPLICATED` | Se a instalação do Adobe Commerce tem uma instância de banco de dados secundária (normalmente `false`) |
| `SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH` | Diretório temporário do agente (geralmente `/usr/local/swat-agent/tmp`) |
| `SWAT_AGENT_RUN_CHECKS_ON_START` | Coletar dados na primeira execução (normalmente `1`) |
| `SWAT_AGENT_LOG_LEVEL` | Determina quais eventos são registrados com base na gravidade (normalmente `error`) |
| `SWAT_AGENT_ENABLE_AUTO_UPGRADE` | Ativa a atualização automática (reinicialização necessária após uma atualização; O agente não verifica as atualizações se a opção estiver desativada; `true` ou `false`) |
| `SWAT_AGENT_IS_SANDBOX=false` | Ativar o modo sandbox para usar o agente no ambiente de preparo |

>[!INFO]
>
>Consulte [Como acessar [!DNL Site-Wide Analysis Tool] e gerar relatórios](../site-wide-analysis-tool/access.md).
