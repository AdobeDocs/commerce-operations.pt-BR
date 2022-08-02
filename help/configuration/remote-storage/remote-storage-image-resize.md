---
title: Configurar o redimensionamento de imagem para armazenamento remoto
description: Otimize os recursos de disco configurando o redimensionamento de imagem do lado do servidor.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---

# Configurar o redimensionamento de imagem para armazenamento remoto

Por padrão, [!DNL Commerce] O suporta redimensionamento de imagem no lado do aplicativo. No entanto, ao ativar o módulo de Armazenamento Remoto, você pode usar o Nginx para descarregar o redimensionamento de imagem no lado do servidor, onde você pode salvar recursos de disco e otimizar o uso do disco.

O diagrama a seguir mostra como o Nginx recupera, redimensiona e armazena imagens no cache. O redimensionamento é determinado pelos parâmetros incluídos no URL, como altura e largura.

![redimensionamento de imagem](../../assets/configuration/remote-storage-nginx-image-resize.png)

## Configurar o formato do URL em [!DNL Commerce]

Para redimensionar imagens no lado do servidor, você deve configurar o Commerce para fornecer argumentos para a altura, a largura e o local (URL) da imagem.

**Para configurar o Commerce para redimensionamento de imagens no lado do servidor**:

1. No _Administrador_ painel, clique em **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. No painel direito, expanda **[!UICONTROL Url options]**.

1. No _Formato de URL de mídia de catálogo_ seção, limpar **[!UICONTROL Use system value]**.

1. Selecione o `Image optimization based on query parameters` O URL na **_Formato de URL de mídia de catálogo_** campo.

1. Clique em **[!UICONTROL Save Config]**.

1. Continue para a [Configuração do próximo nó](#configure-nginx).

## Configurar Nginx

Para continuar configurando o redimensionamento de imagem do lado do servidor, você deve preparar o `nginx.conf` e forneça um `proxy_pass` para o adaptador escolhido.

**Para permitir que o Nginx redimensione imagens**:

1. Instale o [Módulo de filtro de imagem próximo][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Crie um `nginx.conf` arquivo com base no modelo incluído `nginx.conf.sample` arquivo. Por exemplo:

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

1. [_Opcional_] Configure um `proxy_pass` para o adaptador específico.

   - [Serviço de Armazenamento Simples da Amazon (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
