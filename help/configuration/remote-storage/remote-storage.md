---
title: Configurar armazenamento remoto
description: Saiba como configurar o módulo de Armazenamento remoto para o aplicativo comercial local.
source-git-commit: 9a5993c9a65ad210f1a9682734730f235bbc3d44
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# Configurar armazenamento remoto

O módulo de Armazenamento Remoto fornece a opção de armazenar arquivos de mídia e agendar importações e exportações em um contêiner de armazenamento persistente e remoto usando um serviço de armazenamento, como o AWS S3. Por padrão, o aplicativo Adobe Commerce armazena arquivos de mídia no mesmo sistema de arquivos que contém o aplicativo. Isso é ineficiente para configurações complexas de vários servidores e pode resultar em desempenho degradado ao compartilhar recursos. Com o módulo de Armazenamento Remoto, você pode armazenar arquivos de mídia no `pub/media` e importar/exportar arquivos no `var` diretório do armazenamento remoto de objetos para aproveitar o redimensionamento de imagens do lado do servidor.

>[!INFO]
>
>O armazenamento remoto está disponível somente para a versão 2.4.2 e posterior do Commerce. Consulte a [Notas de versão 2.4.2](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>O módulo de armazenamento remoto tem _limitado_ suporte no Adobe Commerce na infraestrutura em nuvem. O Adobe não pode solucionar totalmente os problemas do serviço do adaptador de armazenamento de terceiros. Consulte [Configurar o armazenamento remoto para o Commerce on Cloud Infrastructure](cloud-support.md) para obter orientação sobre a implementação de armazenamento remoto para projetos em nuvem.

![imagem do esquema](../../assets/configuration/remote-storage-schema.png)

## Opções de armazenamento remoto

Você pode configurar o armazenamento remoto usando o `remote-storage` com a opção [`setup` comando CLI](../../installation/tutorials/deployment.md). O `remote-storage` A opção usa a seguinte sintaxe:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

O `parameter-name` refere-se ao nome do parâmetro de armazenamento remoto específico. A tabela a seguir lista os parâmetros disponíveis para a configuração do armazenamento remoto:

| Parâmetro de linha de comando | Nome do parâmetro | Descrição | Valor padrão |
|--- |--- |--- |--- |
| `remote-storage-driver` | driver | Nome do adaptador<br>Valores possíveis:<br>**arquivo**: Desativa o armazenamento remoto e usa o sistema de arquivos local <br>**aws-s3**: Use o [Serviço de Armazenamento Simples da Amazon (Amazon S3)](remote-storage-aws-s3.md) | nenhum |
| `remote-storage-bucket` | bucket | Armazenamento de objetos ou nome do contêiner | nenhum |
| `remote-storage-prefix` | prefixo | Prefixo opcional (local dentro do armazenamento de objetos) | empty |
| `remote-storage-region` | região | Nome da região | nenhum |
| `remote-storage-key` | chave de acesso | Chave de acesso opcional | empty |
| `remote-storage-secret` | chave secreta | Chave secreta opcional | empty |

### Adaptadores de armazenamento

O local de armazenamento padrão está no sistema de arquivos local. A _adaptador de armazenamento_ permite que você se conecte a um serviço de armazenamento e armazene seus arquivos em qualquer lugar. [!DNL Commerce] O suporta a configuração dos seguintes serviços de armazenamento:

- [Serviço de Armazenamento Simples da Amazon (Amazon S3)](remote-storage-aws-s3.md)

## Habilitar armazenamento remoto

Você pode instalar o armazenamento remoto durante uma instalação do Adobe Commerce ou adicionar o armazenamento remoto a uma instância do Commerce existente. Os exemplos a seguir demonstram cada método usando um conjunto de `remote-storage` parâmetros com Commerce `setup` Comandos CLI. No mínimo, você deve fornecer o armazenamento `driver`, `bucket`e `region`.

- Exemplo: Instalar o Commerce com armazenamento remoto

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- Exemplo: Habilitar armazenamento remoto no Commerce existente

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

>[!TIP]
>
>Para obter informações sobre a infraestrutura em nuvem do Adobe Commerce, consulte [Configurar o armazenamento remoto para o Commerce on Cloud Infrastructure](cloud-support.md).

## Limitações

Não é possível ativar simultaneamente o armazenamento remoto e o armazenamento de banco de dados. Desative o armazenamento do banco de dados se estiver usando armazenamento remoto.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Habilitar o armazenamento remoto pode afetar sua experiência de desenvolvimento estabelecida. Por exemplo, certas funções de arquivo PHP podem não funcionar conforme esperado. O uso da Estrutura de comércio para operações de arquivo deve ser aplicado.

A lista de funções nativas PHP proibidas está disponível em [repositório magento-coding-standard][code-standard].

## Migrar conteúdo

Depois de habilitar o armazenamento remoto para um adaptador específico, você pode usar a CLI para migrar o _mídia_ arquivos para o armazenamento remoto.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>O comando de sincronização só migra arquivos no `pub/media` diretory, _not_ os arquivos de importação/exportação na `var` diretório. Consulte [Importação/exportação programada][import-export] no _Guia do usuário do Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[code-standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
