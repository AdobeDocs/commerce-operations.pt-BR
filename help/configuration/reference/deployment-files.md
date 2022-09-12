---
title: Arquivos de configuração para implantação
description: Entenda como os arquivos de configuração funcionam para instalar o aplicativo Commerce.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Arquivos de configuração para implantação

O Adobe Commerce fornece arquivos de configuração que permitem personalizar facilmente um componente e criar tipos de configuração para estender a funcionalidade padrão. O processo de configuração de implantação consiste na configuração compartilhada e específica do sistema para sua instalação. A configuração de implantação do Commerce é dividida entre [`app/etc/config.php`](../reference/config-reference-configphp.md) e [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` é _compartilhado_ arquivo de configuração.
Este arquivo contém a lista de módulos, temas e pacotes de idioma instalados; e configurações compartilhadas.

   Verifique este arquivo para obter o controle e usá-lo em seus sistemas de desenvolvimento, armazenamento temporário e produção.

   A partir da versão 2.2, a variável `app/etc/config.php` O arquivo não é mais uma entrada no `.gitignore` arquivo.
Isso foi feito para facilitar [implantação de pipeline](../deployment/technical-details.md).

- `app/etc/env.php` contém configurações específicas do ambiente de instalação.

Juntos, `config.php` e `env.php` são designadas como comércio _configuração de implantação_ porque os arquivos são criados durante a instalação e precisam iniciar o aplicativo Commerce.

>[!INFO]
>
>O [!DNL Commerce 2] a configuração de implantação substitui `local.xml` em [!DNL Magento 1.x].

Diferente de outros [arquivos de configuração do módulo](../reference/module-files.md), a configuração de implantação do Commerce é carregada na memória quando, durante a inicialização, não é mesclada com nenhum outro arquivo e não pode ser estendida. (`config.php` e `env.php` no entanto, são mescladas entre si.)

## Detalhes sobre a configuração de implantação

`config.php` e `env.php` são arquivos PHP que retornam um [matriz associativa multidimensional](https://www.w3schools.com:443/php/php_arrays.asp), que é basicamente uma disposição hierárquica de parâmetros e valores de configuração.

No nível superior desse storage estão _segmentos de configuração_. Um segmento tem conteúdo arbitrário (um valor escalar ou uma matriz aninhada) distinto por uma chave arbitrária, onde o par de chave e valor é definido pela estrutura do Commerce.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) fornece apenas acesso a essas seções, mas não permite estendê-las.

No próximo nível de hierarquia, os itens em cada segmento são ordenados de acordo com a variável [módulo](https://glossary.magento.com/module) definição de sequência, que é obtida pela união de todos os arquivos de configuração de módulos, exceto para módulos desativados.

As seções a seguir discutem a estrutura e o conteúdo da configuração de implantação:

- Gerenciar módulos instalados
- Configuração específica do sistema

## Gerenciar módulos instalados

O `config.php` O arquivo contém uma lista de módulos instalados. O Adobe Commerce fornece utilitários baseados em linha de comando e na Web para gerenciar módulos (instalar, desinstalar, ativar, desativar ou atualizar).

Exemplos:

- Desinstalar componentes: [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- Verificar o status dos componentes: [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
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

Os módulos desativados não são reconhecidos pelo aplicativo Commerce; em outras palavras, eles não participam da mesclagem de configuração, injeção de dependência, eventos, plug-ins e assim por diante. Os módulos desativados não modificam a variável [vitrine](https://glossary.magento.com/storefront) ou [Administrador](https://glossary.magento.com/admin) e não afetam o roteamento.

A única diferença prática de um módulo desativado e ausente na base de código é que um módulo desativado é encontrado pelo carregador automático, e suas classes e constantes estão disponíveis para reutilização em outro código.
