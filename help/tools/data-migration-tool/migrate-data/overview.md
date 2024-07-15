---
title: Visão geral da migração
description: Saiba como iniciar a migração de dados do Magento 1 para o Magento 2 com o  [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Visão geral da migração

Antes de iniciar a migração, pare todos os trabalhos de cron do Magento 1.

Durante o processo de migração, siga estas regras gerais para uma migração bem-sucedida:

1. **Não** fazer alterações no Administrador do Magento 1, exceto para gerenciamento de pedidos (remessa, criação de fatura e avisos de crédito)
1. **Não** altere qualquer código
1. **Não** fazer alterações no administrador e na vitrine do Magento 2

>[!TIP]
>
>Todas as operações na loja de Magento 1 são permitidas.

## Executar o [!DNL Data Migration Tool]

Esta seção mostra como executar o [!DNL Data Migration Tool] para migrar configurações, dados ou alterações incrementais.

### Primeiros passos

1. Efetue login no servidor de aplicativos como, ou alterne para, um usuário com permissões para gravar no sistema de arquivos. Consulte [alternar para o proprietário do sistema de arquivos](../../../installation/prerequisites/file-system/overview.md).

   Se você usar o shell bash, poderá usar a seguinte sintaxe para alternar para o proprietário do sistema de arquivos e inserir o comando ao mesmo tempo:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Se o proprietário do sistema de arquivos não permitir logons, você poderá fazer o seguinte:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Para executar comandos Magento de qualquer diretório, adicione `<magento_root>/bin` ao sistema `PATH`.

   Como os shells têm sintaxe diferente, consulte uma referência como [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Exemplo de shell bash para CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Como opção, você pode executar os comandos das seguintes maneiras:

   - `cd <magento_root>/bin` e executá-los como `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` é um subdiretório do docroot do seu servidor Web.

### Sintaxe de comando

Abaixo está um exemplo típico de comando:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Onde:

- `<mode>` pode ser: [`settings`](settings.md), [`data`](data.md), ou [`delta`](delta.md)
- `[-r|--reset]` é um argumento opcional que inicia a migração desde o início. Você pode usar esse argumento para testar a migração.
- `[-a|--auto]` é um argumento opcional que impede que a migração pare quando encontrar erros de verificação de integridade.
- `{<path to config.xml>}` é o caminho absoluto do sistema de arquivos para `config.xml`; este argumento é obrigatório.

>[!NOTE]
>
>Os logs são gravados no diretório `<magento_root>/var/`.


## Ordem de migração

Quando criamos o [!DNL Data Migration Tool], assumimos a seguinte sequência de transferência de dados:

1. [Configurações](settings.md)
1. [Dados](data.md)
1. [Alterações](delta.md)

É altamente recomendável migrar os dados na mesma ordem.
