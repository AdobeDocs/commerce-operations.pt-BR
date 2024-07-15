---
title: Práticas recomendadas para modificar o código PHP principal e de terceiros
description: Saiba como e quando modificar o Adobe Commerce principal e o código PHP de terceiros.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
exl-id: 32b3137d-fc00-4be8-ba02-5d8d48a51fe1
source-git-commit: d47567a8d69ccdae3db01e964f1db12e8ae26717
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# Práticas recomendadas para modificar ou substituir o código PHP principal e de terceiros

Este documento descreve as práticas recomendadas quando surge a necessidade de modificar a funcionalidade, o resultado ou a entrada de qualquer código que você não criou ou não controla diretamente. Em outras palavras, código principal e código de terceiros. Este documento se concentra principalmente no código PHP de back-end.

## Métodos de modificação do código

Ao modificar o código, é importante considerar o escopo de suas alterações. O &quot;âmbito&quot; das alterações refere-se ao alcance dos efeitos das alterações do código. Como prática recomendada, baseie a decisão de como a implementação final é concluída com base na opção que tem o menor espaço e o menor uso de recursos. Quanto mais abrangentes forem as substituições de código, mais uma equipe de desenvolvimento se desvia da funcionalidade principal do Adobe Commerce, aumentando a probabilidade de bugs e maior esforço para manter a base de código no futuro.

### Correção

Um patch é um arquivo que contém instruções para alterar diretamente o código em um arquivo que não está sob o controle direto da equipe de desenvolvimento. Essa é uma opção que geralmente deve ser considerada como um último recurso quando não existem outras opções. Os patches devem ser uma solução temporária. Se você precisar criar um patch, como prática recomendada, remova o patch em favor de uma solução mais permanente nas próximas 2 a 4 semanas. 

Os patches se quebram facilmente. Se os arquivos dos alvos de patch forem atualizados, isso frequentemente faz com que o patch pare de funcionar. Isso ocorre porque um arquivo de patch contém números de linha e de coluna que indicam especificamente o que deve ser alterado pelo patch. Se algo não corresponder ao que o patch esperava, ele deixará de ser aplicado e quebrará o código.

```bash
diff --git a/vendor/magento/module-quote/Model/QuoteManagement.php b/vendor/magento/module-quote/Model/QuoteManagement.php
index 51b68411d40..ac4a3468322 100644
--- a/vendor/magento/module-quote/Model/QuoteManagement.php
+++ b/vendor/magento/module-quote/Model/QuoteManagement.php
@@ -424,8 +424,9 @@ class QuoteManagement implements CartManagementInterface
                 }
             }
             $quote->setCustomerIsGuest(true);
-            $groupId = $customer ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID;
-            $quote->setCustomerGroupId($groupId);
+            $quote->setCustomerGroupId(
+                $quote->getCustomerId() ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID
+            );
         }
  
         $remoteAddress = $this->remoteAddress->getRemoteAddress();
```

#### O que pode ser alterado com um patch

Qualquer coisa. Literalmente, qualquer caractere em qualquer arquivo direcionado pode ser alterado. Os patches não estão limitados a nenhum tipo de arquivo ou linguagem de código em particular. Normalmente, você usaria um patch para direcionar arquivos dentro do diretório `vendor`. 

#### Quando usar um patch

Se você perceber que nenhuma outra opção existe. Por exemplo, quando o fornecedor ainda não tiver publicado uma correção para o código, você poderá usar uma correção para resolver temporariamente o problema enquanto aguarda uma solução permanente.

#### Desvantagens

Os patches se quebram facilmente. No momento em que o código-alvo é alterado, o patch deixa de funcionar. Elas devem ser uma solução apenas de curto prazo.

### Preferência

Uma preferência é um conceito projetado na plataforma do Adobe Commerce. É essencialmente uma &quot;substituição de classe PHP&quot;.

A plataforma Adobe Commerce usa um &quot;gerenciador de objeto&quot; para instanciar classes PHP porque ela não instancia classes PHP com a nova palavra-chave como é feito nos aplicativos PHP tradicionais. Em vez disso, o gerenciador de objetos faz referência cruzada ao nome da classe PHP a ser instanciada contra uma configuração compilada para determinar se qualquer módulo declarou uma preferência para a classe original. Se uma preferência para a classe PHP for encontrada, o gerenciador de objetos instancia a classe especificada.

Deve-se notar que (geralmente) a nova classe PHP substituindo a classe PHP original estende/herda da classe PHP original. Isso é feito por alguns motivos:

- Para garantir que a injeção/indicação de tipo de dependência seja cumprida. Caso contrário, ocorrerá um erro fatal e o aplicativo será interrompido.
- Para permitir uma gravação mínima de código. Se a classe PHP original contém dez métodos, mas você só precisa substituir um método, você pode geralmente alterar um método sozinho e deixar os outros nove métodos intactos. Isso é importante para garantir que você não esteja bloqueando as atualizações para a funcionalidade principal, pois a plataforma é atualizada para novas versões.

#### Declarar uma preferência

É um processo bastante simples declarar uma preferência. Uma única linha de código precisaria ser adicionada a um arquivo `di.xml` em um módulo. Isso pode ser feito globalmente ou em qualquer &quot;área&quot; do Adobe Commerce, como `frontend`, `adminhtml`, `graphql`, `webapi_rest` e `crontab`.

```xml
<preference for="Magento\Elasticsearch7\SearchAdapter\Adapter" type="Vendor\Namespace\Adapter\AlgoliaElasticSearch7Adapter"/>
```

```php
<?php

declare(strict_types=1);

namespace Vendor\Namespace\Adapter;

class AlgoliaElasticSearchAdapter extends \Magento\Elasticsearch7\SearchAdapter\Adapter
{
}
```

#### O que pode ser alterado com uma preferência

Somente as classes PHP podem ser substituídas com uma preferência. Dentro da classe PHP, você pode modificar propriedades e métodos públicos e protegidos. Para métodos públicos e protegidos, é possível substituir totalmente o método ou modificar os argumentos que entram (ou o resultado que sai) do método pai original.

Tecnicamente, os métodos privados não podem ser substituídos. No entanto, você pode criar sua própria substituição para o método privado original. Você pode até dar a ele um nome arbitrário, você também pode usar o nome original. Não importa, pois um método privado só existe no arquivo real que o contém. Para substituir um método privado, é necessário substituir ou modificar o método público ou protegido que chama o método privado original e substituir sua própria funcionalidade em seu lugar.

#### Quando usar uma preferência

Mais uma vez, você deve usar as preferências quando nenhuma outra opção existir e quando não puder alcançar seu objetivo com injeção de dependência, um plug-in ou observador. Às vezes, você pode precisar de uma preferência se precisar modificar ou substituir métodos ou propriedades privados ou protegidos. Observe que as preferências devem ser usadas com moderação. Eles são um método bastante &quot;ganancioso&quot; de alterar o aplicativo e você efetivamente tomar posse da classe PHP. Isso pode gerar conflitos com módulos de terceiros, bloquear atualizações na classe principal e causar bugs difíceis de diagnosticar. A plataforma do Adobe Commerce foi projetada para incluir outros caminhos pelos quais as alterações no código subjacente podem ser feitas com um espaço menor.

#### Desvantagens

As preferências são uma maneira ambiciosa de modificar o código e só devem ser usadas quando outras opções não existirem. As preferências podem muitas vezes levar a conflitos dentro da base de código e, pior ainda, podem bloquear as atualizações principais que ocorrem com as atualizações da plataforma. 

### Observador

Um observador é o conceito de um ouvinte de eventos, como encontrado em muitos aplicativos, plataformas, bibliotecas e linguagens de codificação. O conceito não é exclusivo da plataforma Adobe Commerce. Os observadores são enviados para a plataforma desde os dias de Magento 1 e são considerados uma escolha primária de como modificar o código principal e o código de terceiros. 

A base de código principal e qualquer módulo de terceiros pode despachar um evento em um local escolhido no código. O observador, que é declarado em um arquivo `events.xml` e está escutando o evento despachado pelo nome, pode trabalhar em um nível global ou ser restrito a qualquer &quot;área&quot; do Adobe Commerce, como `frontend`, `adminhtml`, `graphql`, `webapi_rest` e `crontab`.

#### Como declarar um observador

Os observadores podem ser configurados em um arquivo `events.xml` global ou específico da área.

```xml
    <event name="sales_model_service_quote_submit_before">
        <observer name="set_reward_flag_order" instance="Adobe\RewardAdjustments\Observer\SetOrderRewardFlag" />
    </event>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\RewardAdjustments\Observer;

use Magento\Framework\Event\ObserverInterface;
use Magento\Framework\Event\Observer;
use Magento\Quote\Model\Quote;
use Magento\Sales\Api\Data\OrderInterface;

class SetOrderRewardFlag implements ObserverInterface
{
    /**
     * @param Observer $observer
     * @return void
     */
    public function execute(Observer $observer)
    {
        $event = $observer->getEvent();
        /* @var $order OrderInterface */
        $order = $event->getOrder();
        /** @var $quote Quote $quote */
        $quote = $event->getQuote();

        // do something to the order and/or quote object here
    }
}
```

#### O que pode ser alterado com um observador

Observadores só se aplicam ao código PHP dentro da plataforma Adobe Commerce. Você só pode modificar os dados e objetos específicos que são transmitidos com a expedição do evento.

#### Quando usar um observador

Sempre que disponível! Se os observadores estivessem mais disponíveis e flexíveis, então os observadores tomariam o segundo lugar nesta lista. Os observadores têm menos sobrecarga de processamento do que os plug-ins, eles estão menos disponíveis e menos flexíveis.

#### Desvantagens

Embora os observadores sejam uma excelente maneira de interceptar e modificar o código, o despacho dos eventos deve ser adicionado ao código principal ou de terceiros para que esteja disponível para que seu código acompanhe. Isso torna o conceito de usar observadores um pouco limitado. Você está limitado a eventos que um desenvolvedor teve a visão para incluir no código.

Além disso, outro fator limitante dos observadores é que o evento despachado fornece acesso apenas aos dados e objetos específicos que o desenvolvedor decidiu transmitir juntamente com o evento.

### Plug-in

Um plug-in é um conceito flexível introduzido na plataforma Adobe Commerce. Ele permite que você intercepte, substitua e modifique qualquer método público do PHP. Os plug-ins permitem modificar os argumentos que entram em um método antes da execução do método direcionado, modificar o resultado após a execução do método direcionado ou substituir totalmente o método direcionado. Você pode modificar muitos métodos de uma classe PHP direcionada dentro de um único arquivo de plug-in. Além disso, você pode usar o argumento `$subject` para executar qualquer método público que exista na classe PHP direcionada.

#### Como declarar um plug-in

Os plug-ins podem ser configurados em um arquivo `di.xml` global ou específico da área.

```xml
    <type name="Magento\Catalog\Api\CategoryRepositoryInterface">
        <plugin name="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin" type="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin"/>
    </type>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\CatalogAdjustments\Plugin;

class CategoryRepositoryPlugin
{
    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param int $categoryId
     * @param int $storeId
     *
     * @return array
     */
    public function beforeGet($subject, $categoryId, $storeId = null): array
    {
        // modify the $categoryId or $storeId arguments or perform some other functionality prior to execution of the `get` method
        return [$categoryId, $storeId];
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Closure $origMethod
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function aroundGet($subject, $origMethod, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you can do something before calling the original method
        $result = $origMethod($categoryId, $storeId);
        // here you can do something after calling the original method
        // you can also NOT call the original method at all and instead, substitute our own functionality

        return $result;
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Magento\Catalog\Api\Data\CategoryInterface $result
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function afterGet($subject, $result, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you modify the result produced by the original `get` function or you can execute some other functionality
        // note that you also have access to the original function arguments. it's too late to modify them, but if needed, they are available for reading

        return $result;
    }
}
```

#### O que pode ser alterado com um plug-in

Esta funcionalidade só está disponível para classes PHP de destino. Você pode alterar a entrada ou saída de um método público e usar um plug-in para acionar outra funcionalidade. Se vários plug-ins tiverem como alvo a mesma classe PHP, uma ordem de classificação para a execução de plug-ins pode ser definida para permitir que seu plug-in seja executado antes ou depois de outros plug-ins.

#### Quando usar um plug-in

Sempre que a substituição de dependência não estiver disponível. Plug-ins são usados com frequência em toda a base de código principal, código de terceiros e podem ser usados com frequência em seu próprio código personalizado. Normalmente, quando você precisa modificar uma funcionalidade que não pertence ou é controlada por seu código personalizado, um plug-in é a melhor maneira de seguir em frente.

#### Desvantagens

Não é possível modificar propriedades ou métodos protegidos. As despesas gerais de processamento são superiores às de um observador. Isso não é realmente um argumento para não usar plugins, a diferença é trivial. No entanto, isso é algo bom para se ter em mente.

### Substituição de dependência

A injeção de dependência é um conceito de codificação orientado a objetos padrão no qual você transmite as dependências necessárias para uma classe com o construtor. No entanto, a plataforma Adobe Commerce leva isso um passo além, fornecendo vários caminhos para substituir dependências por XML. Basicamente, substituição de dependência. A substituição de dependência não é adequada para todas as situações, mas permite escrever código mínimo, sobrecarga baixa e você pode direcionar apenas partes exatas de código. É possível modificar métodos privados e protegidos com substituição de dependência.

#### Como usar a substituição de dependência

A substituição de dependência pode ser feita globalmente ou em uma área específica.

```php
<?php

class SomeClass
{
    public function __construct(
        private readonly AllowedCountries $allowedCountriesReader
    ) {}

    /**
     * Check is address allowed for store
     *
     * @param AddressInterface $address
     * @param int|null $storeId
     * @return bool
     */
    private function isAddressAllowedForWebsite(AddressInterface $address, $storeId): bool
    {
        $allowedCountries = $this->allowedCountriesReader->getAllowedCountries(ScopeInterface::SCOPE_STORE, $storeId);

        return in_array($address->getCountryId(), $allowedCountries);
    }
}
```

```php
<?php

use Magento\Store\Model\ScopeInterface;

class OverrideAllowedCountries extends AllowedCountries
{
    /**
     * Retrieve all allowed countries for scope or scopes
     *
     * @param string $scope
     * @param string|null $scopeCode
     * @return array
     * @since 100.1.2
     */
    public function getAllowedCountries(
        $scope = ScopeInterface::SCOPE_WEBSITE,
        $scopeCode = null
    ) {
        // do some stuff here
        // you can call the original method or override it completely
        
        return $something;
    }
}
```

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Vendor\Namespace\SomeClass">
        <arguments>
            <argument name="allowedCountriesReader" xsi:type="object">OverrideAllowedCountries</argument>
        </arguments>
    </type>
</config>
```

Depois de seguir essas etapas, você terá modificado com êxito o comportamento de um método privado.

#### O que pode ser alterado com a substituição de dependência

Métodos públicos, protegidos e privados podem ser alterados com a substituição de dependências. Como em um plug-in, você pode modificar os argumentos que entram, substituir completamente a função ou modificar a saída da função.

#### Quando usar a substituição de dependência

Essa é uma boa primeira opção quando ela realmente alcançaria o objetivo desejado, supondo que nada muito complexo tenha de ser feito para ser implementado.

#### Desvantagens

Não muitos. Não é utilizável em todas as situações. A principal desvantagem é que você deve estender a classe original que contém a funcionalidade que deseja modificar. Isso vai contra o princípio da &quot;Composição sobre Herança&quot;.
