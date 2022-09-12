---
title: Pré-requisitos de instalação no local
description: Saiba mais sobre as dependências de software necessárias para instalações locais do Adobe Commerce e Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Pré-requisitos de instalação no local

Antes de instalar o Adobe Commerce ou o Magento Open Source, faça o seguinte:

* Configure um ou mais hosts que atendam ao [requisitos do sistema](../system-requirements.md).
* Se você estiver configurando mais de um nó da Web com balanceamento de carga, configure e teste essa parte do sistema _before_ instale o aplicativo.
* Certifique-se de fazer o backup de todo o sistema em vários pontos durante a instalação para que você possa revertê-lo em caso de problemas.

>[!NOTE]
>
>Suponhamos que você esteja instalando o Adobe Commerce ou o Magento Open Source em um **ambiente de desenvolvimento**, que você tem acesso de usuário raiz à máquina, **e** que a máquina não precisa ser altamente segura. Se você estiver configurando uma máquina mais segura, recomendamos que consulte um administrador de rede para obter assistência adicional.

Recomendamos que você atualize e atualize seu software do sistema operacional. Essas atualizações podem fornecer correções de segurança e software que podem evitar problemas futuros. Não sabe o que isso significa? Veja nossa [página visão geral da instalação](../overview.md).

Digite os seguintes comandos como um usuário com `root` privilégios:

* Ubuntu

   ```bash
   apt-get update
   ```

   ```bash
   apt-get upgrade
   ```

* CentOS

   ```bash
   yum -y update
   ```

   ```bash
   yum -y upgrade
   ```

## Verificação de pré-requisito

Para verificar os pré-requisitos do sistema, insira os seguintes comandos:

### Apache

CentOS: `httpd -v`

Ubuntu: `apache2 -v`

O Adobe Commerce e o Magento Open Source oferecem suporte ao Apache versão 2.4, pois o resultado a seguir indica:

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Para instalar ou atualizar o Apache, consulte [Apache](web-server/apache.md).

### PHP

Consulte [requisitos do sistema](../system-requirements.md) para versões compatíveis do PHP e [PHP] para requisitos PHP.

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

Por exemplo:

```bash
mysql -u magento -p
```

Verifique se você tem a versão correta do MySQL para a versão do Adobe Commerce ou do Magento Open Source que está instalando ([confira aqui as versões compatíveis](../system-requirements.md). O resultado a seguir indica a versão em execução.)

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Tipo `help` ou `\h` para obter ajuda. Tipo `\c` para limpar a instrução de entrada atual.

Enter `exit` no `mysql>` para sair.

Para instalar ou atualizar o MySQL, consulte [MySQL](database/mysql.md).

### Elasticsearch ou OpenSearch

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

Por exemplo:

```bash
curl -XGET 'localhost:9200'
```

```terminal
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```
