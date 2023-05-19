---
title: Arquivos de configuração para implantação
description: Entenda como os arquivos de configuração funcionam para instalar o aplicativo Commerce.
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: dd990800551dd2ba35ebc7d2bc04edeb1b183d6f
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# Arquivos de configuração para implantação

O Adobe Commerce fornece arquivos de configuração que permitem personalizar facilmente um componente e criar tipos de configuração para estender a funcionalidade padrão. O processo de configuração de implantação consiste na configuração compartilhada e específica do sistema para sua instalação. A configuração de implantação do Commerce é dividida entre [`app/etc/config.php`](../reference/config-reference-configphp.md) e [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` é o _compartilhado_ arquivo de configuração.
Esse arquivo contém a lista de módulos, temas e pacotes de idioma instalados e as configurações compartilhadas.

   Inclua esse arquivo no controle de origem e use-o em seus sistemas de desenvolvimento, preparo e produção.

- `app/etc/env.php` contém configurações específicas para o ambiente de instalação.

Juntos, `config.php` e `env.php` são designados por comércio _configuração de implantação_ porque os arquivos são criados durante a instalação e são necessários para iniciar o aplicativo Commerce.

>[!INFO]
>
>A variável [!DNL Commerce 2] a configuração de implantação substitui `local.xml` in [!DNL Magento 1.x].

Ao contrário de outras [arquivos de configuração do módulo](../reference/module-files.md), a configuração de implantação do Commerce é carregada na memória quando, durante a inicialização, não é mesclada com outros arquivos e não pode ser estendida. (`config.php` e `env.php` são mesclados, no entanto.)

## Detalhes sobre a configuração de implantação

`config.php` e `env.php` são arquivos PHP que retornam um [matriz associativa multidimensional](https://www.w3schools.com:443/php/php_arrays.asp), que é basicamente uma disposição hierárquica de parâmetros e valores de configuração.

No nível superior dessa matriz estão _segmentos de configuração_. Um segmento tem conteúdo arbitrário (um valor escalar ou uma matriz aninhada) diferenciado por uma chave arbitrária, em que o par de chaves e valores é definido pela estrutura do Commerce.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) O apenas fornece acesso a essas seções, mas não permite que você as estenda.

No próximo nível de hierarquia, os itens em cada segmento são ordenados de acordo com a definição de sequência do módulo, que é obtida ao mesclar todos os arquivos de configuração dos módulos, exceto os módulos desativados.

As seções a seguir discutem a estrutura e o conteúdo da configuração de implantação:

- Gerenciar módulos instalados
- Configuração específica do sistema

## Gerenciar módulos instalados

A variável `config.php` O arquivo contém uma lista de módulos instalados. O Adobe Commerce fornece utilitários de linha de comando e baseados na Web para gerenciar módulos (instalar, desinstalar, habilitar, desabilitar ou atualizar).

Exemplos:

- Desinstalar componentes: [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- Verificar status dos componentes: [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- Ativar ou desativar componentes: [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

O valor `1` ou `0` indica se um módulo está ativado ou desativado.

Os módulos desativados não são reconhecidos pelo aplicativo Commerce; em outras palavras, eles não participam da configuração de mesclagem, da injeção de dependência, de eventos, plug-ins e assim por diante. Os módulos desativados não modificam a vitrine nem o Administrador e não afetam o roteamento.

A única diferença prática entre um módulo desativado e um módulo ausente na base de código é que um módulo desativado é encontrado pelo carregador automático, e suas classes e constantes estão disponíveis para reutilização em outro código.
