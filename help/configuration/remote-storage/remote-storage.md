---
title: Configurar o armazenamento remoto
description: Saiba como configurar o módulo de Armazenamento remoto para o aplicativo de comércio local.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Configurar o armazenamento remoto

O módulo de Armazenamento remoto oferece a opção de armazenar arquivos de mídia e agendar importações e exportações em um contêiner de armazenamento remoto persistente usando um serviço de armazenamento, como o AWS S3. Por padrão, o aplicativo do Adobe Commerce armazena arquivos de mídia no mesmo sistema de arquivos que contém o aplicativo. Isso é ineficiente para configurações complexas de vários servidores e pode resultar em redução do desempenho ao compartilhar recursos. Com o módulo de Armazenamento remoto, você pode armazenar arquivos de mídia no `pub/media` diretório e arquivos de importação/exportação na `var` diretório do armazenamento remoto de objetos para aproveitar o redimensionamento de imagens do lado do servidor.

>[!INFO]
>
>O armazenamento remoto está disponível somente para a versão 2.4.2 e posterior do Commerce. Consulte a [Notas de versão do 2.4.2](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>O módulo de armazenamento remoto possui _limitado_ no Adobe Commerce na infraestrutura em nuvem. O Adobe não pode solucionar problemas completamente com o serviço de adaptador de armazenamento de terceiros. Consulte [Configurar o armazenamento remoto para a infraestrutura do Commerce na nuvem](cloud-support.md) para obter orientação sobre como implementar o armazenamento remoto para projetos na nuvem.

![imagem do esquema](../../assets/configuration/remote-storage-schema.png)

## Opções de armazenamento remoto

É possível configurar o armazenamento remoto usando o `remote-storage` com a opção [`setup` comando CLI](../../installation/tutorials/deployment.md). A variável `remote-storage` A opção usa a seguinte sintaxe:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

A variável `parameter-name` refere-se ao nome do parâmetro de armazenamento remoto específico. A tabela a seguir lista os parâmetros disponíveis para configurar o armazenamento remoto:

| Parâmetro de linha de comando | Nome do parâmetro | Descrição | Valor padrão |
|--- |--- |--- |--- |
| `remote-storage-driver` | driver | Nome do adaptador<br>Valores possíveis:<br>**arquivo**: desativa o armazenamento remoto e usa o sistema de arquivos local <br>**aws-s3**: Use o [Serviço de armazenamento simples da Amazon (Amazon S3)](remote-storage-aws-s3.md) | nenhum |
| `remote-storage-bucket` | balde | Armazenamento de objetos ou nome do container | nenhum |
| `remote-storage-prefix` | prefixo | Prefixo opcional (local dentro do armazenamento de objetos) | vazio |
| `remote-storage-region` | região | Nome da região | nenhum |
| `remote-storage-key` | chave de acesso | Chave de acesso opcional | vazio |
| `remote-storage-secret` | chave secreta | Chave secreta opcional | vazio |

### Adaptadores de armazenamento

O local de armazenamento padrão está no sistema de arquivos local. A _adaptador de armazenamento_ O permite que você se conecte a um serviço de armazenamento e armazene seus arquivos em qualquer lugar. [!DNL Commerce] O é compatível com a configuração dos seguintes serviços de armazenamento:

- [Serviço de armazenamento simples da Amazon (Amazon S3)](remote-storage-aws-s3.md)

## Habilitar armazenamento remoto

Você pode instalar o armazenamento remoto durante uma instalação do Adobe Commerce ou adicionar armazenamento remoto a uma instância existente do Commerce. Os exemplos a seguir demonstram cada método usando um conjunto de `remote-storage` parâmetros com o Commerce `setup` Comandos da CLI. No mínimo, você deve fornecer o armazenamento `driver`, `bucket`, e `region`.

- Exemplo: instalar o Commerce com armazenamento remoto

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- Exemplo: habilitar o armazenamento remoto no Commerce existente

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>Para o Adobe Commerce na infraestrutura em nuvem, consulte [Configurar o armazenamento remoto para a infraestrutura do Commerce na nuvem](cloud-support.md).

## Limitação

Não é possível habilitar o armazenamento remoto e o armazenamento de banco de dados ao mesmo tempo. Desabilite o armazenamento do banco de dados se estiver usando o armazenamento remoto.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

A habilitação do armazenamento remoto pode afetar sua experiência de desenvolvimento estabelecida. Por exemplo, certas funções de arquivo PHP podem não funcionar como esperado. O uso do Commerce Framework para operações de arquivo deve ser empregado.

A lista de funções nativas proibidas do PHP está disponível em [repositório magento-coding-standard][code-standard].

## Migrar conteúdo

Depois de habilitar o armazenamento remoto para um adaptador específico, você pode usar a CLI para migrar o existente _mídia_ para o armazenamento remoto.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>O comando sync migra somente arquivos no estado `pub/media` diretório, _não_ os arquivos de importação/exportação no `var` diretório. Consulte [Importação/exportação programada](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html) no _Guia do usuário do Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[code-standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
