---
title: Execute os utilitários de suporte
description: Solucione problemas em seu projeto do Commerce usando o utilitário de suporte integrado.
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Execute os utilitários de suporte

{{ee-only}}

{{file-system-owner}}

Os utilitários de suporte da Adobe Commerce, também conhecidos como [Coletor de dados](https://docs.magento.com/user-guide/system/support-data-collector.html)— permite que os usuários coletem informações de solução de problemas do seu sistema que podem ser usadas pela nossa equipe de suporte.

O Adobe Commerce usa esses backups, também chamados de _despejos_, para analisar problemas que exigem acesso ao seu código. Um cenário típico é o seguinte:

1. Você está tendo um problema com sua loja de Commerce e entra em contato com o Suporte da Adobe Commerce.
1. O suporte determina que eles precisam ver seu código ou banco de dados para reproduzir o problema.
1. Você faz backup do código em um `.tar.gz` arquivo.

   Este backup _exclui seus arquivos de mídia para acelerar o processo e resultar em um arquivo muito menor.

1. Você faz backup do banco de dados em um `.tar.gz` arquivo.

   Por padrão, os dados confidenciais recebem hash ao fazer o backup.

1. Você faz upload de backups para um serviço de compartilhamento de arquivos.
1. O suporte analisa seus problemas sem afetar o ambiente de desenvolvimento ou produção.

Os utilitários podem levar vários minutos para serem concluídos.

## Criar um backup de código

Esse comando faz backup do código e o compacta em `tar.gz` formato.

{{tip-backup-command}}

Opções de comando:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Onde:

- **`--name`** especifica o nome do arquivo de dump (opcional). Se você omitir esse parâmetro, o arquivo de despejo terá carimbo de data e hora.
- **`-o|--output=<path>`** é o caminho absoluto do sistema de arquivos para armazenar o backup (necessário).
- **`-l|--logs`** inclui arquivos de registro (opcional).

Por exemplo, para criar um backup de código chamado `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Depois que o comando for concluído, forneça o backup do código para o Suporte da Adobe Commerce.

## Criar um backup de banco de dados

Esse comando faz backup do banco de dados do Commerce e o compacta em `tar.gz` formato.

{{tip-backup-command}}

Opções de comando:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Onde:

- **`--name`** especifica o nome do arquivo de dump (opcional). Se você omitir esse parâmetro, o arquivo de despejo terá carimbo de data e hora.
- **`-o|--output=<path>` é o caminho absoluto do sistema de arquivos para armazenar o backup (necessário).
- **`-l|--logs`** inclui arquivos de registro (opcional).
- **`-i|--ignore-sanitize`** significa que os dados são preservados; omita o sinalizador para aplicar hash a dados confidenciais armazenados no banco de dados ao criar o backup (opcional).

Os dados confidenciais incluem informações de clientes das seguintes tabelas de banco de dados:

```terminal
'customer_entity',
'customer_entity_varchar',
'customer_address_entity',
'customer_address_entity_varchar',
'customer_grid_flat',
'quote',
'quote_address',
'sales_order',
'sales_order_address',
'sales_order_grid'
```

Após a conclusão do comando, forneça o backup do banco de dados para o Suporte da Adobe Commerce.

## Solução de problemas: utilitários de exibição e caminhos

Fornecemos comandos que exibem caminhos para utilitários exigidos pelo Coletor de dados e pela linha de comando. Você pode usar esses comandos, por exemplo, se erros como o seguinte forem exibidos no Admin ou na linha de comando:

```terminal
Utility lsof not found
```

Execute os seguintes comandos na ordem mostrada para exibir os caminhos para os aplicativos usados pelos utilitários de suporte e pelo Coletor de dados:

1. Altere para o diretório de instalação do Commerce.

   Por exemplo, `cd /var/www/magento2`

   >[!INFO]
   >
   >Os comandos são executados corretamente _somente_ do diretório de instalação.

1. `bin/magento support:utility:paths` cria `<magento_root>/var/support/Paths.php`, que lista os caminhos para todos os aplicativos usados pelo utilitário.
1. `bin/magento support:utility:check` exibe os caminhos do sistema de arquivos.

A seguir, há uma amostra:

```terminal
   gzip => /bin/gzip
   lsof => /usr/sbin/lsof
   mysqldump => /usr/bin/mysqldump
   nice => /bin/nice
   php => /usr/bin/php
   tar => /bin/tar
   sed => /bin/sed
   bash => /bin/bash
   mysql => /usr/bin/mysql
```

Para resolver problemas com a execução das ferramentas, verifique se esses aplicativos estão instalados e no repositório do usuário do servidor Web `$PATH` variável de ambiente.
