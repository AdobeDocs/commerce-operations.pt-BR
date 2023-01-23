---
title: Otimizar arquivos de recursos CSS e JS
description: Saiba como mesclar e minificar arquivos CSS e JavaScript (JS) para projetos do Adobe Commerce pelo Administrador ou pela linha de comando.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: e6e8a2d7ef059265dbcbfcd6be117828a639f6d6
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Otimizar arquivos de recursos

Para um site de Comércio mais responsivo, otimize os arquivos de recursos de CSS e JavaScript (JS) e elimine os recursos de bloqueio de renderização.

- **Otimizar arquivos CSS e JS**—Reduza o tempo necessário para carregar arquivos CSS e JavaScript (JS) configurando o Adobe Commerce para mesclar, diminuir e agrupar arquivos separados em um único arquivo.
- **Eliminar recursos de bloqueio de renderização**—Considere fornecer recursos críticos de JS e CSS em linha e adiar todos os estilos não críticos de JS/CSS. Para obter orientação, consulte [Eliminar recursos de bloqueio de renderização](https://web.dev/render-blocking-resources/).

## Produtos e versões afetados

[Todas as versões compatíveis, 2.3 e posteriores](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local
- Magento Open Source

## Mesclar ou minificar arquivos CSS

O tempo necessário para carregar arquivos CSS e JavaScript (JS) pode ser reduzido ao mesclar, minificar e agrupar arquivos separados em um único arquivo.

>[!IMPORTANT]
>
>O Adobe Commerce na infraestrutura em nuvem sempre é executado no modo Produção e não é possível configurá-lo de outra forma, portanto, você deve usar o método de linha de comando para habilitar a mesclagem, a minificação e o agrupamento.

### Uso de Admin

Para ativar a mesclagem ou minificação de CSS, acesse a [!UICONTROL **Administrador** > **Lojas** > **Configuração** > **Configuração** > **Avançado** > **Desenvolvedor** > **Configurações de CSS**].

### Uso da linha de comando

Para habilitar a mesclagem de CSS no Adobe Commerce na infraestrutura de nuvem:

1. Execute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Confirmar alterações no `app/etc/config.php` e reimplante.

Para habilitar a minificação de CSS no Adobe Commerce na infraestrutura de nuvem:

1. Execute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Confirmar alterações no `app/etc/config.php` e reimplante.

## Minimizar arquivos JS

### Uso de Admin

No *Administrador* barra lateral, vá para **Lojas** > **Configurações** > **Configuração** > **Avançado** > **Desenvolvedor** > **Configurações do JavaScript**.

### Uso da linha de comando

Para ativar a minificação de JS no Adobe Commerce na infraestrutura de nuvem:

1. Execute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Confirmar alterações no `app/etc/config.php` e reimplante.

## Mesclar e agrupar arquivos JS

Você pode ativar a mesclagem ou o empacotamento no Administrador de comércio (a mesclagem e o empacotamento não podem ser habilitados ao mesmo tempo): [!UICONTROL **Lojas** > **Configurações** > **Configuração** > **Avançado** > **Desenvolvedor** > **Configurações do JavaScript**].

Você também pode habilitar o pacote integrado do Adobe Commerce (pacote básico) na linha de comando:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Informações adicionais

- [Configurações de otimização do lado do cliente](../../../performance/configuration.md#client-side-optimization-settings)
- [Guia do usuário: Otimização de arquivos de recursos](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Guia do desenvolvedor do Front-end: Mesclagem de CSS, minificação e desempenho do site](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Pacote avançado de JavaScript](../../../performance/advanced-js-bundling.md)

