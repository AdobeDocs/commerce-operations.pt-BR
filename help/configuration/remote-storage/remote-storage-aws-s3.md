---
title: Configurar bucket do AWS S3 para armazenamento remoto
description: Configure seu projeto do Commerce para usar o serviço de armazenamento AWS S3 para armazenamento remoto.
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Configurar bucket do AWS S3 para armazenamento remoto

A variável [Serviço de armazenamento simples da Amazon (Amazon S3)][AWS S3] O é um serviço de armazenamento de objetos que oferece escalabilidade, disponibilidade de dados, segurança e desempenho líderes do setor. O serviço AWS S3 usa buckets ou containers para armazenamento de dados. Essa configuração exige que você crie um _privado_ balde. Para o Adobe Commerce na infraestrutura em nuvem, consulte [Configurar o armazenamento remoto para a infraestrutura do Commerce na nuvem](cloud-support.md).

>[!WARNING]
>
>A Adobe desencoraja muito o uso de baldes públicos porque representa um sério risco à segurança.

**Para habilitar o armazenamento remoto com o adaptador AWS S3**:

1. Faça logon no painel do Amazon S3 e crie um _privado_ balde.

1. Configurar [AWS IAM] funções. Como alternativa, gere as chaves de acesso e secreta.

1. Desabilitar o armazenamento de banco de dados padrão.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Configure o Commerce para usar o bucket privado. Consulte [Opções de armazenamento remoto](remote-storage.md#remote-storage-options) para obter uma lista completa de parâmetros.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. Sincronizar arquivos de mídia com o armazenamento remoto.

   ```bash
   bin/magento remote-storage:sync
   ```

## Configurar Nginx

O Nginx requer configuração adicional para executar a autenticação com o `proxy_pass` diretiva. Adicione as seguintes informações de proxy à `nginx.conf` arquivo:

>nginx.conf

```conf
location ~* \.(ico|jpg|jpeg|png|gif|svg|js|css|swf|eot|ttf|otf|woff|woff2)$ {
    # Proxying to AWS S3 storage.
    resolver 8.8.8.8;
    set $bucket "<s3-bucket-name>";
    proxy_pass https://s3.amazonaws.com/$bucket$uri;
    proxy_pass_request_body off;
    proxy_pass_request_headers off;
    proxy_intercept_errors on;
    proxy_hide_header "x-amz-id-2";
    proxy_hide_header "x-amz-request-id";
    proxy_hide_header "x-amz-storage-class";
    proxy_hide_header "Set-Cookie";
    proxy_ignore_headers "Set-Cookie";
}
```

### Autenticação

Se você usar chaves de acesso e secretas em vez de [AWS IAM] funções, você deve incluir o [`ngx_aws_auth` Módulo Nginx][ngx repo].

### Permissões

A integração S3 depende da capacidade de gerar e armazenar imagens em cache no sistema de arquivos local. Portanto, as permissões de pasta para `pub/media` e diretórios semelhantes são os mesmos para S3 como são ao usar o armazenamento local.

### Operações de arquivo

É altamente recomendável usar [!DNL Commerce] métodos de adaptador de arquivo no desenvolvimento de codificação ou extensão, independentemente do tipo de armazenamento de arquivo. Ao usar S3 para armazenamento, não use operações de E/S de arquivo PHP nativo, como `copy`, `rename`ou `file_put_contents`, pois os arquivos S3 não estão localizados no sistema de arquivos. Consulte [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) para obter exemplos de código.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
