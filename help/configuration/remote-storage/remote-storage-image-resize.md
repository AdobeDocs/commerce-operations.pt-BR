---
title: Configurar redimensionamento de imagem para armazenamento remoto
description: Otimize os recursos de disco configurando o redimensionamento de imagens do lado do servidor.
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%
---
# Configurar redimensionamento de imagem para armazenamento remoto

Por padrão, o Adobe Commerce oferece suporte ao redimensionamento de imagens no lado do aplicativo. No entanto, ao ativar o módulo de Armazenamento remoto, você pode usar o Nginx para descarregar o redimensionamento de imagens no lado do servidor, onde é possível salvar recursos de disco e otimizar o uso do disco.

O diagrama a seguir mostra como o Nginx recupera, redimensiona e armazena imagens no cache. O redimensionamento é determinado pelos parâmetros incluídos no URL, como altura e largura.

![Configuração de nginx para redimensionamento de imagem de armazenamento remoto mostrando as configurações de bloco do servidor](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>Para projetos do Adobe Commerce na infraestrutura em nuvem, consulte [Configurar armazenamento remoto para a infraestrutura do Commerce na nuvem](cloud-support.md)

## Configurar formato de URL no Adobe Commerce

Para redimensionar imagens no lado do servidor, você deve configurar o Adobe Commerce para fornecer argumentos para a altura, a largura e o local (URL) da imagem.

**Para configurar o Commerce para redimensionamento de imagem do lado do servidor**:

1. No painel _Admin_, clique em **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. No painel direito, expanda **[!UICONTROL Url options]**.

1. Na seção _Formato da URL de mídia de catálogo_, desmarque **[!UICONTROL Use system value]**.

1. Selecione a URL `Image optimization based on query parameters` no campo **_Formato da URL de mídia de catálogo_**.

1. Clique em **[!UICONTROL Save Config]**.

1. Prossiga para a [Configuração do Nginx](#configure-nginx).

## Configurar Nginx

Para continuar configurando o redimensionamento de imagem do lado do servidor, você deve preparar o arquivo `nginx.conf` e fornecer um valor de `proxy_pass` para o adaptador escolhido.

**Para permitir que o Nginx redimensione imagens**:

1. Instale o [módulo do filtro de imagem Nginx](https://nginx.org/en/docs/http/ngx_http_image_filter_module.html).

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Crie um arquivo `nginx.conf` com base no arquivo de modelo `nginx.conf.sample` incluído. Por exemplo:

   ```conf
   location ~* \.(jpg|jpeg|png|gif|webp)$ {
       set $width "-";
       set $height "-";
       if ($arg_width != '') {
           set $width $arg_width;
       }
       if ($arg_height != '') {
           set $height $arg_height;
       }
       image_filter resize $width $height;
       image_filter_jpeg_quality 90;
   }
   ```

1. [_Opcional_] Configure um valor de `proxy_pass` para o adaptador específico.

   - [Serviço de armazenamento simples da Amazon (Amazon S3)](remote-storage-aws-s3.md)

