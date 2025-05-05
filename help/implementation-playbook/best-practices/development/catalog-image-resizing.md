---
title: Práticas recomendadas de redimensionamento de imagem de catálogo
description: Saiba como evitar a degradação do desempenho antes de uma inicialização de produção do site do Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 591b1a62-bdba-4301-858a-77620ee657a9
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '464'
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
- O processo é multiservidor (se você tiver vários nós da Web, um balanceador de carga e espaço em disco compartilhado para o diretório `media/`)
- O processo ignora imagens que já foram redimensionadas

Essa abordagem redimensiona 100.000 imagens em menos de 8 horas, enquanto o comando da CLI leva 6 dias para ser concluído.

1. Faça logon no servidor.
1. Navegue até `pub/media/catalog/product` e anote um dos hashes (por exemplo, 0047d83143a5a3a4683afdf1116df680).
1. Nos exemplos a seguir, substitua `www.example.com` pelo domínio de seu armazenamento e substitua o hash pelo que você anotou.

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB cerco]

A desvantagem de `siege` é que ele visita todas as URLs em 10 vezes se a simultaneidade estiver definida como 10.

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

O argumento `-P` determina o número de threads.

>[!TAB bash one-liner]

A linha única para o exemplo de `find/curl`, caso você possa executar `curl` a partir da mesma máquina em que as imagens estão:

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

Novamente, substitua `www.example.com` pelo domínio do seu site e defina `-P` como o número de threads que seu servidor pode manipular sem falhas.

>[!ENDTABS]

A saída retorna uma lista de todas as imagens de produtos na loja. Você pode rastrear as imagens (com `siege` ou qualquer outro rastreador) usando todos os servidores e núcleos de processador disponíveis para você e gerar o cache de redimensionamento em velocidade significativamente maior do que outras abordagens.

Visitar um URL de cache de imagem gera todos os tamanhos de imagem em segundo plano se eles ainda não existirem. Além disso, ignora os arquivos que já foram redimensionados.

>[!NOTE]
>
>- O Adobe Commerce em projetos de infraestrutura em nuvem pode descarregar o redimensionamento de imagem do produto para o serviço Fastly. Consulte [Otimização de imagem profunda](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=pt-BR#deep-image-optimization) no _Guia da Nuvem_.
>- Se você usar o módulo de armazenamento remoto, também poderá tentar descarregar o redimensionamento da imagem para nginx. Consulte [Configurar redimensionamento de imagem para armazenamento remoto](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html?lang=pt-BR) no _Guia de Configuração_.
