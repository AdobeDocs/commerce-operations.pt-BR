---
title: Pré-requisitos do mecanismo de pesquisa
description: Siga estas etapas para instalar e configurar o software de mecanismo de pesquisa compatível para instalações locais do Adobe Commerce e do Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---


# Pré-requisitos do mecanismo de pesquisa

A partir do Adobe Commerce e do Magento Open Source 2.4, todas as instalações devem ser configuradas para usar [Elasticsearch](https://www.elastic.co) ou [OpenSearch](https://opensearch.org/) como solução de pesquisa de catálogo.

>[!NOTE]
>
>O suporte ao OpenSearch foi adicionado em 2.4.4. O OpenSearch é uma bifurcação compatível do Elasticsearch. Todas as instruções para configurar o Elasticsearch 7 se aplicam ao OpenSearch. [Migrar do Elasticsearch para o OpenSearch](../../../upgrade/prepare/opensearch-migration.md) fornece orientação sobre como alternar para o OpenSearch.

## Versões compatíveis

Você deve instalar e configurar o Elasticsearch ou o OpenSearch antes de instalar o Adobe Commerce 2.4.4 e posterior.

Consulte a [Requisitos do sistema](../../system-requirements.md) para obter informações de versão específicas.

## Configuração recomendada

Recomendamos o seguinte:

* [Configurar o nó do mecanismo de pesquisa](configure-nginx.md)
* [Configurar o Apache para seu mecanismo de pesquisa](configure-apache.md)

## Local de instalação

As seguintes tarefas presumem que você configurou o sistema de acordo com o diagrama a seguir:

![Diagrama do mecanismo de pesquisa](../../../assets/installation/search-engine-config.svg)

O diagrama anterior mostra:

* O aplicativo Commerce e o mecanismo de pesquisa são instalados em hosts diferentes.

   A execução em hosts separados requer proxy para funcionar. (O clustering do mecanismo de pesquisa está além do escopo deste guia, mas você pode encontrar mais informações na [Documentação de clustering do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* Cada host tem seu próprio servidor da Web; os servidores da web não precisam ser os mesmos.

   Por exemplo, o aplicativo Commerce pode executar o Apache e o mecanismo de pesquisa pode executar o nginx.

* Ambos os servidores da Web usam a Segurança da camada de transporte (TLS).

   A configuração do TLS está além do escopo de nossa documentação.

As solicitações de pesquisa são processadas da seguinte maneira:

1. Uma solicitação de pesquisa de um usuário é recebida pelo servidor Web do Commerce, que a encaminha para o servidor do mecanismo de pesquisa.

   Você configura o mecanismo de pesquisa para se conectar ao host e à porta do proxy. Recomendamos a porta SSL do servidor Web (por padrão, 443).

1. O servidor Web do mecanismo de pesquisa (acompanhando na porta 443) envia a solicitação ao servidor do mecanismo de pesquisa (por padrão, escuta na porta 9200).

1. O acesso ao mecanismo de pesquisa é protegido ainda mais pela autenticação HTTP Basic. Para uma solicitação alcançar o mecanismo de pesquisa, ele deve viajar pelo SSL *e* forneça um nome de usuário e senha válidos.

1. O mecanismo de pesquisa processa a solicitação.

1. A comunicação retorna ao longo da mesma rota, com o servidor da Web Elasticsearch agindo como um proxy reverso seguro.

## Pré-requisitos

As tarefas discutidas nesta seção exigem o seguinte:

* [Firewall e SELinux](#firewall-and-selinux)
* [Instale o Java Software Development Kit (JDK)](#install-the-java-software-development-kit)
* [Instalar o mecanismo de pesquisa](#install-the-search-engine)
* [Atualização do Elasticsearch](#upgrading-elasticsearch)

### Firewall e SELinux

Por padrão, os softwares relacionados à segurança (iptables, SELinux, AppArmor) podem ser configurados para bloquear a comunicação entre subsistemas. Pode ser uma boa ideia verificá-los se houver problemas.

#### Configurar regras para iptables e SELinux

Para configurar regras para permitir a comunicação com o firewall ou o SELinux habilitado, consulte os seguintes recursos:

* [instruções dos iptables](https://help.ubuntu.com/community/IptablesHowTo)
* [Como editar regras iptables (projeto fedora)](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [Introdução ao SELinux (CentOS.org)](https://www.centos.org)
* [Wiki de procedimentos do SELinux (CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Instale o Kit de desenvolvimento de software Java

Para determinar se o Java já está instalado, insira o seguinte comando:

```bash
java -version
```

Se a mensagem `java: command not found` for exibido, você deve instalar o SDK do Java, conforme discutido na próxima seção.

Veja uma das seguintes seções:

* [Instalar o JDK mais recente no CentOS](#install-the-jdk-on-centos)
* [Instale o JDK mais recente no Ubuntu](#install-the-jdk-on-ubuntu)

#### Instalar o JDK no CentOS

Veja isso [Tutorial para Oceano digital](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

Certifique-se de instalar o JDK e *not* o JRE.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>O Java versão 8 pode não estar disponível para todos os sistemas operacionais. Por exemplo, você pode [pesquise a lista de pacotes disponíveis para Ubuntu](https://packages.ubuntu.com/).

#### Instalar o JDK no Ubuntu

Para instalar o JDK 1.8 no Ubuntu, insira os seguintes comandos como um usuário com `root` privilégios:

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

Para outras opções, consulte [Documentação do oracle](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### Instalar o mecanismo de pesquisa

Seguir [Instalação do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) ou [Instalar e configurar o OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) para suas etapas específicas da plataforma.

Para verificar se o Elasticsearch está funcionando, digite o seguinte comando no servidor em que está sendo executado:

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

Uma mensagem semelhante à seguinte é exibida:

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

Para verificar se o OpenSearch está funcionando, insira os seguintes comandos:

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## Atualização do Elasticsearch

Consulte [Atualização do Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obter instruções completas sobre como fazer backup de seus dados, detectar possíveis problemas de migração e testar atualizações antes de implantar na produção. Dependendo da versão atual do Elasticsearch, pode ser ou não necessário reiniciar o cluster completo.

O Elasticsearch requer o JDK 1.8 ou superior. Consulte [Instale o Kit de desenvolvimento de software Java](#install-the-java-software-development-kit) para verificar qual versão do JDK está instalada.

## Recursos adicionais

Consulte a [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) ou [OpenSearch](https://opensearch.org/docs/latest/) documentação.
