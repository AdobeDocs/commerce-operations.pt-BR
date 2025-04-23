---
title: Pré-requisitos de instalação local
description: Saiba mais sobre as dependências de software necessárias para instalações locais do Adobe Commerce.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: db2256f5327897a4376a0d038ce697e8f93235af
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 1%

---

# Pré-requisitos de instalação local

Antes de instalar o Adobe Commerce, é necessário fazer o seguinte:

* Configure um ou mais hosts que atendam aos [requisitos de sistema](../system-requirements.md) listados na guia *Commerce local*.
* Se você estiver configurando mais de um nó da Web com balanceamento de carga, configure e teste essa parte do sistema _antes_ de instalar o aplicativo.
* Certifique-se de poder fazer backup de todo o sistema em vários pontos durante a instalação para que você possa revertê-lo em caso de problemas.

>[!NOTE]
>
>Presumimos que você esteja instalando o Adobe Commerce em um **ambiente de desenvolvimento**, que você tenha acesso de usuário raiz ao computador, **e** que o computador não precisa ser altamente seguro. Se você estiver configurando uma máquina mais segura, recomendamos consultar um administrador de rede para obter assistência adicional.

É altamente recomendável atualizar e atualizar o software do sistema operacional. Essas atualizações podem fornecer correções de segurança e software que podem evitar problemas futuros. Não sabe o que isso significa? Confira nossa [página de visão geral da instalação](../overview.md).

Digite os seguintes comandos como um usuário com privilégios de `root`:

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

## Verificação de pré-requisitos

Para verificar se há pré-requisitos no sistema, digite os seguintes comandos:

### Apache

CentOS: `httpd -v`

Ubuntu: `apache2 -v`

O Adobe Commerce é compatível com a versão 2.4 do Apache, como indica o resultado a seguir:

```
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Para instalar ou atualizar o Apache, consulte [Apache](web-server/apache.md).

### PHP

Consulte a guia *Commerce no local* em [requisitos do sistema](../system-requirements.md) para obter as versões do PHP compatíveis e [PHP](../system-requirements.md#php-settings) para os requisitos do PHP.

### MySQL

Verifique se você tem uma versão compatível do MySQL com a versão do Adobe Commerce que está instalando. Consulte a guia *Commerce no local* em [Requisitos do sistema](../system-requirements.md) para obter as versões com suporte.

```bash
mysql -u <database root user or database owner name> -p
```

Por exemplo:

```bash
mysql -u magento -p
```

O resultado a seguir indica a versão que você está executando.

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Digite `help` ou `\h` para obter ajuda. Digite `\c` para limpar a instrução de entrada atual.

Digite `exit` no prompt `mysql>` para sair.

Para instalar ou atualizar o MySQL, consulte [MySQL](database/mysql.md).

### Mecanismo de pesquisa

Para verificar a instalação do OpenSearch:

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Para verificar a instalação do Elasticsearch:

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

Por exemplo:

```bash
curl -XGET 'localhost:9200'
```

```
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
