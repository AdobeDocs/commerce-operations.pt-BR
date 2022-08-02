---
title: Execute os utilitários de suporte
description: Solucione problemas do seu projeto do Commerce usando o utilitário de suporte integrado.
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# Execute os utilitários de suporte

{{ee-only}}

{{file-system-owner}}

Os utilitários de suporte Adobe Commerce, também conhecidos como [Coletor de dados](https://docs.magento.com/user-guide/system/support-data-collector.html)—permitir que os usuários coletem informações de solução de problemas do seu sistema que podem ser usadas pela nossa equipe de suporte.

A Adobe Commerce usa esses backups, também conhecidos como _despejos_, para analisar problemas que exigem acesso ao código. Um cenário típico é o seguinte:

1. Você está tendo um problema com a loja do Commerce e entra em contato com o Suporte da Adobe Commerce.
1. O suporte determina que eles precisam ver seu código ou banco de dados para reproduzir o problema.
1. Faça o backup do código em um `.tar.gz` arquivo.

   Este backup _exclui seus arquivos de mídia para acelerar o processo e resultar em um arquivo muito menor.

1. Faça o backup do banco de dados em um `.tar.gz` arquivo.

   Por padrão, os dados confidenciais passam por hash ao fazer o backup.

1. Você carrega seus backups em um serviço de compartilhamento de arquivos.
1. O suporte analisa seus problemas sem afetar seu ambiente de desenvolvimento ou produção.

Os utilitários podem levar vários minutos para serem concluídos.

## Criar um backup de código

Esse comando faz o backup do código e o compacta em `tar.gz` formato.

{{tip-backup-command}}

Opções de comando:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Em que:

- **`--name`** especifica o nome do arquivo de despejo (opcional). Se esse parâmetro for omitido, o arquivo de despejo terá data e hora.
- **`-o|--output=<path>`** é o caminho absoluto do sistema de arquivos para armazenar o backup (obrigatório).
- **`-l|--logs`** inclui arquivos de log (opcional).

Por exemplo, para criar um backup de código chamado `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Depois que o comando for concluído, forneça o backup do código para o Suporte da Adobe Commerce.

## Criar um backup de banco de dados

Esse comando faz o backup do banco de dados do Commerce e o compacta em `tar.gz` formato.

{{tip-backup-command}}

Opções de comando:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Em que:

- **`--name`** especifica o nome do arquivo de despejo (opcional). Se esse parâmetro for omitido, o arquivo de despejo terá data e hora.
- **`-o|--output=<path>` é o caminho absoluto do sistema de arquivos para armazenar o backup (obrigatório).
- **`-l|--logs`** inclui arquivos de log (opcional).
- **`-i|--ignore-sanitize`** significa que os dados são conservados; omita o sinalizador para dados sensíveis a hash armazenados no banco de dados ao criar o backup (opcional).

Os dados confidenciais incluem informações do cliente nas seguintes tabelas do banco de dados:

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

Depois que o comando for concluído, forneça o backup do banco de dados ao Suporte da Adobe Commerce.

## Solução de problemas: utilitários e caminhos de exibição

Fornecemos comandos que exibem caminhos para utilitários exigidos pelo Coletor de dados e pela linha de comando. Você pode usar esses comandos, por exemplo, se erros como o seguinte forem exibidos no Admin ou na linha de comando:

```terminal
Utility lsof not found
```

Execute os seguintes comandos na ordem mostrada para exibir os caminhos para os aplicativos usados pelos utilitários de suporte e pelo Coletor de dados:

1. Altere para o diretório de instalação do Commerce.

   Por exemplo, `cd /var/www/magento2`

   >[!INFO]
   >
   >Os comandos são executados corretamente _only_ do diretório de instalação.

1. `bin/magento support:utility:paths` cria `<magento_root>/var/support/Paths.php`, que lista os caminhos para todos os aplicativos usados pelo utilitário.
1. `bin/magento support:utility:check` exibe os caminhos do sistema de arquivos.

Uma amostra:

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

Para resolver problemas com a execução das ferramentas, verifique se esses aplicativos estão instalados e estão no `$PATH` variável de ambiente.
