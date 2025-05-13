---
title: 'ACSD-64532: a variável ENV definida como *false* é tratada como uma string *false* em vez de BOOLEAN *FALSE*'
description: Aplique o patch ACSD-64532 para corrigir o problema do Adobe Commerce em que uma variável "ENV" definida como *false* é tratada como uma string "false" em vez de "BOOLEAN" *FALSE*.
feature: Variables
role: Admin, Developer
source-git-commit: 603b4f92ab3bbf4702d5373bd02dfdd770f57d5b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# ACSD-64532: a variável ENV definida como &quot;false&quot; é tratada como uma cadeia de caracteres &quot;false&quot; em vez de BOOLEAN FALSE

O patch ACSD-64532 corrige o problema em que a variável `ENV` definida como *false* é tratada como uma cadeia de caracteres *false* em vez de `BOOLEAN` *FALSE*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 está instalado. A ID do patch é ACSD-64532. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
Adobe Commerce (todos os métodos de implantação) 2.4.6-p8

**Compatível com as versões do Adobe Commerce:**
Adobe Commerce (todos os métodos de implantação) 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A variável `ENV` definida como *false* é tratada como uma cadeia de caracteres *false* em vez de um `BOOLEAN` *FALSE*.

<u>Etapas a serem reproduzidas</u>:
1. Adicione `env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK` com o valor *false* às variáveis de ambiente no Adobe Commerce na infraestrutura de nuvem.
1. Aguarde a reimplantação.
1. Execute o script verificando o valor:

   ```php
   <?php
   require '../app/bootstrap.php';
   $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
   $objectManager = $bootstrap->getObjectManager();
   $deploymentConfig = $objectManager->get('Magento\Framework\App\DeploymentConfig');
   $useAppLock = $deploymentConfig->get('indexer/use_application_lock');
   
   var_dump($useAppLock);
   
   $configParsedValue = $deploymentConfig->get('indexer/use_application_lock') ?: false;
   
   var_dump($configParsedValue); 
   ```

<u>Resultados esperados</u>:
`$configParsedValue`, que é o resultado do método `isUseApplicationLock()`, deve retornar um valor negativo para ser interpretado corretamente dentro do método `\Magento\Indexer\Model\Mview\View\State::getStatus()`.

<u>Resultados reais</u>:
`$configParsedValue` tem um valor de *`string(5) false`*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:
* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
