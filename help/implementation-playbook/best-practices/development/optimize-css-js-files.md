---
title: Otimizar arquivos de recursos CSS e JS
description: Saiba como mesclar e minificar arquivos CSS e JavaScript (JS) para projetos Adobe Commerce do Administrador ou da linha de comando.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Otimizar arquivos de recurso

Para um site do Commerce mais responsivo, otimize os arquivos de recursos CSS e JavaScript (JS) e elimine os recursos de bloqueio de renderização.

- **Otimizar arquivos CSS e JS**—Reduza o tempo necessário para carregar arquivos CSS e JavaScript (JS) configurando o Adobe Commerce para mesclar, minificar e agrupar arquivos separados em um único arquivo.
- **Eliminar recursos de bloqueio de renderização**—Considere fornecer recursos críticos de JS e CSS em linha e adiar todos os estilos de JS/CSS não críticos. Para obter orientação, consulte [Eliminar recursos de bloqueio de renderização](https://web.dev/render-blocking-resources/).

## Produtos e versões afetados

[Todas as versões compatíveis, 2.3 e posteriores](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local
- Magento Open Source

## Mesclar ou minificar arquivos CSS

O tempo necessário para carregar arquivos CSS e JavaScript (JS) pode ser reduzido com a mesclagem, minificação e agrupamento de arquivos separados em um único arquivo.

>[!IMPORTANT]
>
>A infraestrutura do Adobe Commerce na nuvem sempre é executada no modo de Produção e não é possível defini-la de outra forma. Portanto, você deve usar o método de linha de comando para habilitar a mesclagem, a minificação e o agrupamento.

### Uso do Admin

Para habilitar a mesclagem ou minificação de CSS, acesse o [!UICONTROL **Admin** > **Lojas** > **Configuração** > **Configuração** > **Avançado** > **Desenvolvedor** > **Configurações de CSS**].

### Usando a linha de comando

Para habilitar a mesclagem de CSS no Adobe Commerce na infraestrutura em nuvem:

1. Execute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Confirme as alterações no `app/etc/config.php` arquivo e reimplantar.

Para ativar a minificação CSS no Adobe Commerce na infraestrutura em nuvem:

1. Execute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Confirme as alterações no `app/etc/config.php` arquivo e reimplantar.

## Minificar arquivos JS

### Uso do Admin

No *Admin* barra lateral, vá para **Lojas** > **Configurações** > **Configuração** > **Avançado** > **Desenvolvedor** > **Configurações do JavaScript**.

### Usando a linha de comando

Para ativar a minificação de JS no Adobe Commerce na infraestrutura em nuvem:

1. Execute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Confirme as alterações no `app/etc/config.php` arquivo e reimplantar.

## Mesclar e agrupar arquivos JS

Você pode ativar a mesclagem ou o agrupamento no Administrador do Commerce (a mesclagem e o agrupamento não podem ser habilitados ao mesmo tempo): [!UICONTROL **Lojas** > **Configurações** > **Configuração** > **Avançado** > **Desenvolvedor** > **Configurações do JavaScript**].

Você também pode ativar o agrupamento Adobe Commerce incorporado (agrupamento básico) na linha de comando:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Informações adicionais

- [Configurações de otimização do lado do cliente](../../../performance/configuration.md#client-side-optimization-settings)
- [Guia do usuário: otimizar arquivos de recursos](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Guia do desenvolvedor de front-end: mesclagem de CSS, minificação e desempenho do site](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Empacotamento avançado de JavaScript](../../../performance/advanced-js-bundling.md)
