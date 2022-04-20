---
title: Ambiente de desenvolvimento Recommendations
description: Saiba mais sobre as recomendações de desempenho para configurar seu ambiente local de desenvolvimento de Adobe Commerce ou Magento Open Source.
source-git-commit: 87b353b408ecd7f55cea5b4775a0c8523952abc0
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Recomendações para o ambiente de desenvolvimento

Esta página fornece recomendações para ambientes de desenvolvimento de Comércio .

## Limpe os caches em vez de desabilitar

Muitos desenvolvedores tendem a desativar todos os caches em suas instâncias de desenvolvedor. Recomendamos apenas limpar caches, sem desativar todos os caches. [!DNL Commerce] executa com mais eficiência quando você [limpe os caches] em vez de desativá-los completamente. A maioria dos tipos de caches raramente são invalidados durante o desenvolvimento.

Se você [desative os caches], recomendamos desativar apenas os caches Page e Block em instâncias de desenvolvimento. Lembre-se de ativar todos os caches durante os testes.

## Comandos para evitar no modo de desenvolvimento

No modo de desenvolvimento, não execute comandos para compilação, geração de código e implantação de conteúdo estático. Esses comandos foram criados para uso somente no modo de produção.

**Não executar** comandos de produção no modo de desenvolvimento:

* `setup:di:compile` gera classes geradas automaticamente e caches de configuração otimizados.

   ```bash
   bin/magento setup:di:compile
   ```

   No modo de desenvolvimento, o Magento executa a geração sob demanda; você não precisa executá-lo. Se você modificou uma assinatura de uma classe e precisa gerar novamente sua `factories/proxies/interceptors`remova essas classes ou a _gerado_ pasta.

* `setup:static-content:deploy` implanta conteúdo estático para uma loja.

   ```bash
   bin/magento setup:static-content:deploy
   ```

   No modo de desenvolvimento, o Magento executa-o sob demanda; você não precisa executá-lo.

## Tempo normal de carregamento de página em uma máquina virtual

Se você se desenvolver em uma VM e levar mais de 2 segundos para carregar uma página do Magento, revise as configurações do ambiente.

<!-- Link definitions -->

[limpe os caches]: https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cache.html#config-cli-subcommands-cache-clean
[desative os caches]: https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cache.html#config-cli-subcommands-cache-en
