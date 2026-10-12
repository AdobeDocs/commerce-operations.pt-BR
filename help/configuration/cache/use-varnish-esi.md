---
title: Configurar bloco ESI de verniz
description: Saiba mais sobre as ESI (Varnish Edge Side Includes) e como incorporar páginas da Web para o Adobe Commerce. Descubra a implementação e otimização de blocos ESI.
badge: label="Contribuição de Constantino G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G"
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
autotag-review: '2026-06-22T22:02:08.706Z'
TQID: 'https://experienceleague.adobe.com/hzsfaZyHuUhzfb86anO43PfP-62WRPOoMbYOh-H1vqo'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%
---
# Configurar bloco ESI de verniz {#varnish-esi-block}

{{varnish-config-cloud}}

As ESI (Edge Side Includes) são diretivas especiais que podem ser usadas para incluir páginas da Web em outras páginas da Web.

Um exemplo:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

O verniz busca conteúdo de `http://domain.com/index.php/page_cache/block/esi/blocks` e substitui a marca `<esi>` por ela.

## ESI do Commerce e do verniz

A estrutura do Commerce cria uma tag ESI quando as seguintes condições são atendidas:

- O aplicativo de cache está definido como `Varnish Cache`
- Um elemento `block` do layout XML é adicionado com um atributo `ttl`

### Exemplo

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

No exemplo acima, o elemento `block` adiciona conteúdo do modelo `esi.phtml` a uma página inicial e o Verniz o atualiza automaticamente a cada 30 segundos.

## Limitação

Atualmente, o Verniz não é compatível com ESI em HTTPS, portanto, ele muda automaticamente para HTTP.

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```
