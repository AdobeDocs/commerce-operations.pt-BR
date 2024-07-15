---
title: Ambiente de desenvolvimento Recommendations
description: Saiba mais sobre as recomendações de desempenho para configurar o ambiente de desenvolvimento local do Adobe Commerce.
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Recomendações para o ambiente de desenvolvimento

Esta página fornece recomendações para ambientes de desenvolvimento do Commerce.

## Limpar os caches em vez de desabilitar

Muitos desenvolvedores tendem a desativar todos os caches em suas instâncias de desenvolvedor. Recomendamos apenas limpar caches, sem desativar todos os caches. O [!DNL Commerce] é executado com mais eficiência quando você [limpa os caches](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) em vez de desabilitá-los completamente. A maioria dos tipos de caches raramente é invalidada durante o desenvolvimento.

Se você [desabilitar os caches](../configuration/cli/manage-cache.md#enable-or-disable-cache-types), recomendamos desabilitar apenas caches de Página e Bloqueio em instâncias de desenvolvimento. Lembre-se de ativar todos os caches durante os testes.

## Comandos a serem evitados no modo de desenvolvimento

No modo de desenvolvimento, não execute comandos para compilação, geração de código e implantação de conteúdo estático. Esses comandos foram criados para uso somente no modo de produção.

**Não executar** comandos de produção no modo de desenvolvimento:

* `setup:di:compile` gera classes geradas automaticamente e caches de configuração otimizados.

  ```bash
  bin/magento setup:di:compile
  ```

  No modo de desenvolvimento, o Magento executa a geração sob demanda; não é necessário executá-la. Se você modificou uma assinatura de uma classe e precisa gerar novamente a `factories/proxies/interceptors` gerada automaticamente, remova essas classes ou a pasta _gerada_.

* `setup:static-content:deploy` implanta conteúdo estático para um armazenamento.

  ```bash
  bin/magento setup:static-content:deploy
  ```

  No modo de desenvolvimento, o Magento o executa sob demanda; não é necessário executá-lo.

## Tempo normal de carregamento de página em uma máquina virtual

Se você desenvolver em uma VM e levar mais de 2 segundos para carregar uma página de Magento, revise as configurações do ambiente.
