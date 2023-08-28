---
title: Práticas recomendadas de redimensionamento de imagem de catálogo
description: Saiba como evitar a degradação do desempenho antes de uma inicialização de produção do site do Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---


# Práticas recomendadas de redimensionamento de imagem de catálogo

Todas as imagens do catálogo devem ser redimensionadas antes que um armazenamento entre em produção. A falha no redimensionamento de imagens antes da produção força o redimensionamento da imagem durante o carregamento da página, o que reduz significativamente a velocidade do site e aumenta a carga do servidor nos primeiros dias a semanas após o lançamento.

## O caminho lento

Use o comando padrão da CLI para redimensionar todas as imagens:

```bash
bin/magento catalog:images:resize
```

As desvantagens dessa abordagem incluem:

- O processo é de encadeamento único
- O processo redimensiona imagens que já foram redimensionadas
- O processo não pode ser interrompido, o que pode levar dias

## A maneira mais rápida

O redimensionamento assíncrono de imagens foi introduzido no Adobe Commerce 2.4 e pode redimensionar imagens com mais rapidez.

1. Em cada servidor da Web, inicie temporariamente alguns manipuladores de fila extras (o dobro do número de processadores físicos por servidor):

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. Verifique se os manipuladores de fila estão em execução:

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. Preencher a fila com todas as solicitações de redimensionamento de imagem:

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. Depois que todas as imagens forem redimensionadas, encerre o processo:

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## O caminho rápido

Há outra maneira de redimensionar imagens usando o front-end.

As vantagens dessa abordagem incluem:

- O processo é multithread
- O processo é multiservidor (se você tiver vários nós da Web, um balanceador de carga e o espaço em disco compartilhado para o `media/` diretory)
- O processo ignora imagens que já foram redimensionadas

Essa abordagem redimensiona 100.000 imagens em menos de 8 horas, enquanto o comando da CLI leva 6 dias para ser concluído.

1. Faça logon no servidor.
1. Navegue até `pub/media/catalog/product` e anote uma das hashes (por exemplo, 0047d83143a5a3a4683afdf1116df680).
1. Nos exemplos a seguir, substitua `www.example.com` com o domínio de sua loja e substitua o hash pelo que você anotou.

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB cerco]

A desvantagem da `siege` é que visita todos os URLs no 10 vezes se a simultaneidade estiver definida como 10.

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

A variável `-P` determina o número de threads.

>[!TAB bash one-liner]

O revestimento único para o `find/curl` exemplo, caso você possa executar `curl` na mesma máquina em que estão as imagens:

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

Novamente, substitua `www.example.com` com o domínio do seu site e defina `-P` ao número de threads que o servidor pode manipular sem travar.

>[!ENDTABS]

A saída retorna uma lista de todas as imagens de produtos na loja. Você pode rastrear as imagens (com `siege` ou qualquer outro crawler) usando todos os servidores e núcleos de processador disponíveis para você e gerar o cache de redimensionamento em velocidade significativamente maior do que outras abordagens.

Visitar um URL de cache de imagem gera todos os tamanhos de imagem em segundo plano se eles ainda não existirem. Além disso, ignora os arquivos que já foram redimensionados.

>[!NOTE]
>
>- O Adobe Commerce em projetos de infraestrutura em nuvem pode descarregar o redimensionamento de imagem do produto para o serviço Fastly. Consulte [Otimização profunda de imagem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=en#deep-image-optimization) no _Guia da nuvem_.
>- Se você usar o módulo de armazenamento remoto, também poderá tentar descarregar o redimensionamento da imagem para nginx. Consulte [Configurar redimensionamento de imagem para armazenamento remoto](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html) no _Guia de configuração_.
