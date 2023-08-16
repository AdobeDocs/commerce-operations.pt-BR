---
title: Configurar redimensionamento de imagem para armazenamento remoto
description: Otimize os recursos de disco configurando o redimensionamento de imagens do lado do servidor.
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 1%

---

# Configurar redimensionamento de imagem para armazenamento remoto

Por padrão, o Adobe Commerce oferece suporte ao redimensionamento de imagens no lado do aplicativo. No entanto, ao ativar o módulo de Armazenamento remoto, você pode usar o Nginx para descarregar o redimensionamento de imagens no lado do servidor, onde é possível salvar recursos de disco e otimizar o uso do disco.

O diagrama a seguir mostra como o Nginx recupera, redimensiona e armazena imagens no cache. O redimensionamento é determinado pelos parâmetros incluídos no URL, como altura e largura.

![redimensionamento de imagem](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>Para projetos de infraestrutura em nuvem do Adobe Commerce, consulte [Configurar o armazenamento remoto para a infraestrutura do Commerce na nuvem](cloud-support.md)

## Configurar formato de URL no Adobe Commerce

Para redimensionar imagens no lado do servidor, você deve configurar o Adobe Commerce para fornecer argumentos para a altura, a largura e o local (URL) da imagem.

**Para configurar o Commerce para redimensionamento de imagem do lado do servidor**:

1. No _Admin_ clique em **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. No painel direito, expanda **[!UICONTROL Url options]**.

1. No _Formato de URL da mídia de catálogo_ seção, limpar **[!UICONTROL Use system value]**.

1. Selecione o `Image optimization based on query parameters` URL no **_Formato de URL da mídia de catálogo_** campo.

1. Clique em **[!UICONTROL Save Config]**.

1. Prossiga para a [Configuração do Nginx](#configure-nginx).

## Configurar Nginx

Para continuar configurando o redimensionamento de imagem do lado do servidor, você deve preparar o `nginx.conf` arquivo e forneça um `proxy_pass` para o adaptador escolhido.

**Para permitir que o Nginx redimensione imagens**:

1. Instale o [Módulo de filtro de imagem Nginx][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Criar um `nginx.conf` arquivo com base no modelo incluído `nginx.conf.sample` arquivo. Por exemplo:

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

1. [_Opcional_] Configurar um `proxy_pass` para o seu adaptador específico.

   - [Serviço de armazenamento simples da Amazon (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
