---
title: Configurar o bucket do AWS S3 para armazenamento remoto
description: Configure seu projeto do Commerce para usar o serviço de armazenamento AWS S3 para armazenamento remoto.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Configurar o bucket do AWS S3 para armazenamento remoto

O [Serviço de Armazenamento Simples da Amazon (Amazon S3)][AWS S3] é um serviço de armazenamento de objetos que oferece escalabilidade, disponibilidade, segurança e desempenho líderes do setor. O serviço AWS S3 usa buckets, ou containers, para o armazenamento de dados. Essa configuração exige que você crie uma _private_ balde.

>[!WARNING]
>
>A Adobe desencoraja fortemente a utilização de baldes públicos, uma vez que representa um sério risco para a segurança.

**Para habilitar o armazenamento remoto com o adaptador AWS S3**:

1. Faça logon no painel do Amazon S3 e crie uma _private_ balde.

1. Configurar [AWS IAM] funções. Como alternativa, gere acesso e chaves secretas.

1. Desative o armazenamento padrão do banco de dados.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Configure o Commerce para usar o bucket privado. Consulte [Opções de armazenamento remoto](remote-storage.md#remote-storage-options) para obter uma lista completa de parâmetros.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

## Configurar Nginx

O Nginx requer uma configuração adicional para executar a Autenticação com o `proxy_pass` diretiva. Adicione as seguintes informações de proxy à `nginx.conf` arquivo:

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

Se você usar chaves de acesso e secretas em vez de [AWS IAM] , você deve incluir a variável [`ngx_aws_auth` Módulo próximo][ngx repo].

### Permissões

A integração S3 depende da capacidade de gerar e armazenar imagens em cache no sistema de arquivos local; portanto, permissões de pasta para `pub/media` e diretórios semelhantes são iguais para S3 como ao usar armazenamento local.

### Operações de arquivo

É altamente recomendável usar [!DNL Commerce] métodos de adaptador de arquivo em sua codificação ou desenvolvimento de extensão, independentemente do tipo de armazenamento de arquivo. Ao usar S3 para armazenamento, não use operações de I/O de arquivo PHP nativo, como `copy`, `rename` ou `file_put_contents`, pois os arquivos S3 não estão localizados no sistema de arquivos. Consulte [DriverInterface.php] para exemplos de código.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
[DriverInterface.php]: https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18
