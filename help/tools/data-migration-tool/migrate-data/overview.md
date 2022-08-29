---
title: Visão geral da migração
description: Saiba como começar a migrar dados do Magento 1 para o Magento 2 com o [!DNL Data Migration Tool].
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# Visão geral da migração

Antes de iniciar a migração, pare todos os trabalhos de cron do Magento 1.

Durante o processo de migração, siga estas regras gerais para uma migração bem-sucedida:

1. **Não** faça alterações no Administrador do Magento 1, exceto para o gerenciamento de pedidos (remessa, criação de fatura e avisos de crédito)
1. **Não** alterar qualquer código
1. **Não** faça alterações no Administrador do Magento 2 e [vitrine](https://glossary.magento.com/storefront)

>[!TIP]
>
>Todas as operações na loja do Magento 1 são permitidas.

## Execute o [!DNL Data Migration Tool]

Esta seção mostra como executar o [!DNL Data Migration Tool] para migrar configurações, dados ou alterações incrementais.

### Primeiros passos

1. Faça logon no servidor de aplicativos como, ou alterne para, um usuário com permissões para gravar no sistema de arquivos. Consulte [mudar para o proprietário do sistema de ficheiros](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

   Se você usar o shell bash, poderá usar a seguinte sintaxe para alternar para o proprietário do sistema de arquivos e inserir o comando ao mesmo tempo:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Se o proprietário do sistema de arquivos não permitir logons, você poderá fazer o seguinte:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Para executar comandos Magento de qualquer diretório, adicione `<magento_root>/bin` ao seu sistema `PATH`.

   Como os shells têm sintaxe diferente, consulte uma referência como [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Exemplo de shell bash para CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Como opção, você pode executar os comandos das seguintes maneiras:

   - `cd <magento_root>/bin` e execute-os como `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` é um subdiretório do docroot do servidor da Web.

Além dos argumentos de comando mencionados aqui, consulte [Argumentos comuns](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands.html#instgde-cli-subcommands-common)

### Sintaxe de comando

Abaixo está um exemplo típico de comando:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Em que:

- `<mode>` pode ser: [`settings`](settings.md), [`data`](data.md)ou [`delta`](delta.md)
- `[-r|--reset]` é um argumento opcional que inicia a migração desde o início. Você pode usar esse argumento para testar a migração.
- `[-a|--auto]` é um argumento opcional que impede a interrupção da migração quando encontra erros de verificação de integridade.
- `{<path to config.xml>}` é o caminho absoluto do sistema de arquivos para `config.xml`; esse argumento é obrigatório.

>[!NOTE]
>
>Os logs são gravados no `<magento_root>/var/` diretório.


## Ordem de migração

Quando criamos o [!DNL Data Migration Tool], assumimos a seguinte sequência de transferência de dados:

1. [Configurações](settings.md)
1. [Dados](data.md)
1. [Alterações](delta.md)

É altamente recomendável migrar dados na mesma ordem.
