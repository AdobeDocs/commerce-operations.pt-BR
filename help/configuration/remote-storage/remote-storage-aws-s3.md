---
title: Configurar bucket do AWS S3 para armazenamento remoto
description: Configure seu projeto do Commerce para usar o serviço de armazenamento AWS S3 para armazenamento remoto.
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Configurar bucket do AWS S3 para armazenamento remoto

O [Amazon Simple Storage Service (Amazon S3)][AWS S3] é um serviço de armazenamento de objetos que oferece escalabilidade, disponibilidade de dados, segurança e desempenho líderes do setor. O serviço AWS S3 usa buckets ou containers para armazenamento de dados. Esta configuração requer que você crie um bucket _privado_. Para o Adobe Commerce na infraestrutura em nuvem, consulte [Configurar armazenamento remoto para a infraestrutura do Commerce na nuvem](cloud-support.md).

>[!WARNING]
>
>A Adobe desencoraja muito o uso de baldes públicos porque representa um sério risco à segurança.

**Para habilitar o armazenamento remoto com o adaptador AWS S3**:

1. Faça logon no painel do Amazon S3 e crie um bucket _privado_.

1. Configurar funções do [AWS IAM]. Como alternativa, gere as chaves de acesso e secreta.

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

O Nginx requer configuração adicional para executar a Autenticação com a diretiva `proxy_pass`. Adicionar as seguintes informações de proxy ao arquivo `nginx.conf`:

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

Se você usar chaves de acesso e secretas em vez das funções do [AWS IAM], deverá incluir o módulo [`ngx_aws_auth` Nginx][ngx repo].

### Permissões

A integração S3 depende da capacidade de gerar e armazenar imagens em cache no sistema de arquivos local. Portanto, as permissões de pasta para `pub/media` e diretórios semelhantes são as mesmas para S3 como são ao usar o armazenamento local.

### Operações de arquivo

É altamente recomendável usar os métodos de adaptador de arquivo do [!DNL Commerce] na codificação ou no desenvolvimento de extensão, independentemente do tipo de armazenamento de arquivo. Ao usar S3 para armazenamento, não use operações de E/S de arquivo PHP nativo, como `copy`, `rename` ou `file_put_contents`, porque os arquivos S3 não estão localizados no sistema de arquivos. Consulte [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) para ver exemplos de código.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
