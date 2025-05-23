---
title: Instalação de início rápido local
description: Siga estas etapas para instalar o Adobe Commerce na sua infraestrutura.
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 60db3da9154e76032c88d687b6b6e22d7b81f9ae
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 0%

---

# Instalação start rápida no local

As instruções nesta página descrevem como instalar Adobe Systems Comércio na infraestrutura auto-hospedada. Para obter orientações sobre como atualizar uma instalação existente, consulte o [_Guia_](../upgrade/overview.md) de atualização.

Adobe Systems usa [o Composer](https://getcomposer.org/) para gerenciar Adobe Systems Comércio componentes e suas dependências. Usar o Composer para obter a Adobe Systems Comércio metapackage oferece as seguintes vantagens:

- Reutilize bibliotecas de terceiros sem agrupar com o código-fonte
- Reduza conflitos de extensão e problemas de compatibilidade usando uma arquitetura baseada em componentes com um gerenciamento de dependência robusto
- Adere aos [padrões PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/)
- Reembalar Magento Open Source com outros componentes
- Use o software Adobe Systems Comércio em um ambiente de produção

>[!NOTE]
>
>Os desenvolvedores que contribuem para o Magento Open Source devem usar o [método de instalação baseado em](https://developer.adobe.com/commerce/contributor/guides/install/) Git.

## Pré-requisitos

Antes de continuar, faça o seguinte:

- Conclua todas as [tarefas de pré-requisito](system-requirements.md).
- [Instalar Compositor](https://getcomposer.org/download/).
- Obtenha [chaves de autenticação](prerequisites/authentication-keys.md) para o repositório do Adobe Commerce Composer.

## Efetuar login como proprietário do sistema de arquivos

Saiba mais sobre propriedade, permissões e o proprietário do sistema de arquivos no [tópico Visão geral de propriedade e permissões](prerequisites/file-system/overview.md).

Para alternar para o proprietário do sistema de arquivos:

1. Efetue login no servidor de aplicativos como, ou alterne para, um usuário com permissões para gravar no sistema de arquivos.

   Se você usar o shell bash, poderá usar a seguinte sintaxe para alternar para o proprietário do sistema de arquivos e inserir o comando ao mesmo tempo:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Se o proprietário do sistema de arquivos não permitir logons, você poderá fazer o seguinte:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Para executar comandos CLI de qualquer diretório, adicione o `<app_root>/bin` ao sistema `PATH`.

   Como os shells têm sintaxes diferentes, consulte uma referência como [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Exemplo de shell bash para CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Como opção, você pode executar os comandos das seguintes maneiras:

   - `cd <app_root>/bin` e executá-los como `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` é um subdiretório do docroot do seu servidor Web

## Obter o metapackage

Para obter o metappackage do Adobe Commerce:

1. Faça logon no servidor de aplicativos como ou alterne para o [proprietário do sistema de arquivos](prerequisites/file-system/overview.md).
1. Altere para o diretório docroot do servidor Web ou um diretório que você configurou como docroot do host virtual.
1. Crie um projeto do Composer usando um metapackage do Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando solicitado, insira suas chaves de autenticação. Chaves públicas e privadas são criadas e configuradas de [Commerce Marketplace - Chaves de Acesso](https://commercemarketplace.adobe.com/customer/account/login/). Para o `[!UICONTROL username]`, copie e cole o valor da chave pública. Para o valor da `[!UICONTROL password]`chave privada, copie e cole o valor da chave privada.

   >[!NOTE]
   >
   > Se você usar um `[auth.json](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/authentication-keys)` arquivo composer ou ambiente variável configurado com suas chaves de autenticação Comércio, você não será solicitado a inserir chaves de autenticação.

   Se você encontrar erros como `Could not find package...` ou `...no matching package found`, certifique-se de que não haja erros de digitação no seu comando. Se ainda encontrar erros, talvez não esteja autorizado a baixar Adobe Systems Comércio. Contate o [Suporte da Adobe Commerce](https://support.magento.com/hc/en-us) para obter ajuda.

   Consulte [Solução de problemas](https://support.magento.com/hc/en-us/articles/360033818091) para obter ajuda com mais erros.

### Exemplo - Versão secundária

As versões secundárias contêm novos recursos, correções de qualidade e correções de segurança. Use o Composer para especificar uma versão secundária. Por exemplo, para especificar o metappackage do Adobe Commerce 2.4.6:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Exemplo - Correção de qualidade

Os patches de qualidade contêm principalmente correções de segurança _e_ funcionais. No entanto, às vezes elas também podem conter recursos novos e compatíveis com versões anteriores. Use o Composer para baixar um patch de qualidade. Por exemplo, para especificar o metappackage do Adobe Commerce 2.4.6:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Exemplo - Correção de segurança

Os patches de segurança contêm apenas correções de segurança. Elas foram projetadas para tornar o processo de atualização mais rápido e fácil.

Os patches de segurança usam a convenção de nomenclatura do Composer `2.4.6-px`. Use o Composer para especificar um patch. Por exemplo, para baixar o metappackage 2.4.6-p1 do Adobe Commerce:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## Definir permissões de arquivo

Você deve definir permissões de leitura e gravação para o grupo de servidores Web antes de instalar o Adobe Commerce. Isso é necessário para que a linha de comando possa gravar arquivos no sistema de arquivos.

```bash
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## Instale o aplicativo

Você deve usar a linha de comando para instalar o Adobe Commerce.

Este exemplo supõe que o diretório de instalação seja nomeado como `magento2ee`, o `db-host` esteja na mesma máquina (`localhost`) e que o `db-name`, `db-user` e `db-password` sejam todos `magento`:

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>Você pode personalizar o URI do Administrador com a opção `--backend-frontname`. No entanto, o Adobe recomenda omitir essa opção e permitir que o comando de instalação gere automaticamente um URI aleatório. Um URI aleatório é mais difícil de ser explorado por hackers ou softwares mal-intencionados. O URI é exibido no console quando a instalação é concluída.

>[!TIP]
>
>Para obter uma descrição completa das opções de instalação da CLI, consulte [Instalar o aplicativo da linha de comando](advanced.md).

## Resumo do Comando

Para exibir uma lista completa de comandos, insira:

```bash
bin/magento list
```

Para obter ajuda para um comando específico, insira:

```bash
bin/magento help <command>
```

Por exemplo:

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

A tabela a seguir resume os comandos disponíveis. Os comandos são mostrados somente no formulário de resumo. Para obter mais informações sobre um comando, clique na link na coluna Comando.

| Comando | Descrição | Pré-requisitos |
|--- |--- |--- |
| `magento setup:install` | Instala o aplicativo | Nenhum |
| `magento setup:uninstall` | Remove o aplicativo. | Aplicativo instalado |
| `magento setup:upgrade` | Atualiza o aplicativo. | Configuração de implantação |
| `magento maintenance:{enable/disable}` | Habilita ou desabilita o modo de manutenção (no modo de manutenção, somente endereços IP isentos podem acessar o Administrador ou a loja). | Aplicativo instalado |
| `magento setup:config:set` | Cria ou atualiza a configuração de implantação. | Nenhum |
| `magento module:{enable/disable}` | Ative ou desative módulos. | Nenhum |
| `magento setup:store-config:set` | Define opções relacionadas à loja, como URL base, idioma, fuso horário. | Configuração de implantação |
| `magento setup:db-schema:upgrade` | Atualiza o esquema do banco de dados. | Configuração de implantação |
| `magento setup:db-data:upgrade` | Atualiza os dados do banco de dados. | Configuração de implantação |
| `magento setup:db:status` | Verifica se o banco de dados está atualizado com o código. | Configuração de implantação |
| `magento admin:user:create` | Cria um usuário administrador. | Você pode criar usuários para o seguinte:<br><br>Configuração de implantação<br><br>Habilitar no mínimo o `Magento_User` e o `Magento_Authorization` módulos<br><br>Banco de dados (a maneira mais simples é usar o `bin/magento setup:upgrade`) |
| `magento list` | Lista todos os comandos disponíveis. | Nenhum |
| `magento help` | Fornece ajuda para o comando especificado. | Nenhum |

### Argumentos comuns

Os argumentos a seguir são comuns a todos os comandos. Esses comandos podem ser executados antes ou depois que o aplicativo for instalado:

| Versão longa | Versão curta | Significado |
|--- |--- |--- |
| `--help` | `-h` | Obtenha ajuda para qualquer comando. Por exemplo, `./magento help setup:install` ou `./magento help setup:config:set`. |
| `--quiet` | `-q` | Modo silencioso; sem saída. |
| `--no-interaction` | `-n` | Sem perguntas interativas. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Nível de detalhamento. Por exemplo, `--verbose=3` ou `-vvv` exibe o detalhamento de depuração, que é a saída mais detalhada. O padrão é `--verbose=1` ou `-v`. |
| `--version` | `-V` | Exibir esta versão do aplicativo |
| `--ansi` | n/d | Forçar saída ANSI |
| `--no-ansi` | n/d | Desabilitar saída ANSI |

>[!NOTE]
>
>Parabéns! Você concluiu a instalação rápida. Precisa de ajuda mais avançada? Confira o guia [Instalação avançada](advanced.md).
