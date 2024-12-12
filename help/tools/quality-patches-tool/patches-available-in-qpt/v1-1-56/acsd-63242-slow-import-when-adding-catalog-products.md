---
title: 'ACSD-63242: importação lenta ao adicionar mais de 10.000 produtos de catálogo'
description: Aplique o patch ACSD-63242 para corrigir o problema do Adobe Commerce de importações lentas quando produtos de catálogo com mais de 10.000 entradas são adicionados.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 5fe00c9341414a0a2ba6b535d992d6c64e1c3b3a
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# ACSD-63242: importação lenta ao adicionar mais de 10.000 produtos de catálogo

O patch ACSD-63242 corrige o problema de importações lentas quando produtos de catálogo com mais de 10.000 entradas são adicionados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 está instalado. A ID do patch é ACSD-63242. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6-p8

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p8 e 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A importação de produtos é lenta quando produtos de catálogo com mais de 10.000 entradas são adicionados.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL System]** > **[!UICONTROL Import]** > **[!UICONTROL Products]** > **[!UICONTROL Add/Update]**.
1. Importar arquivo com mais de 10.000 entradas.

<u>Resultados esperados</u>:

A importação de produtos de catálogo é executada no tempo esperado.

<u>Resultados reais</u>:

A importação de produtos está lenta. O `var/log/exception.log` contém:

```PHP
Exception: Warning: DOMXPath::query(): Recursion limit exceeded in /var/www/html/lib/internal/Magento/Framework/Validator/HTML/ConfigurableWYSIWYGValidator.php on line 114 in /var/www/html/lib/internal/Magento/Framework/App/ErrorHandler.php:62
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
