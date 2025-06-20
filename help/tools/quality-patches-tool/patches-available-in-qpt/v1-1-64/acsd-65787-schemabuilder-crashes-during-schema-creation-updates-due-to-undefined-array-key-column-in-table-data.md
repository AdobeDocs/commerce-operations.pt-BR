---
title: 'ACSD-65787: o SchemaBuilder falha durante a criação ou atualização do esquema devido a uma "coluna" de chave de matriz indefinida nos dados da tabela'
description: Aplique o patch ACSD-65787 para corrigir o problema do Adobe Commerce em que a classe SchemaBuilder falha durante a criação ou as atualizações do esquema devido a uma "coluna" de chave de matriz indefinida ao processar dados da tabela.
feature: Backend Development, Deploy
role: Admin, Developer
exl-id: c01d1799-13fe-4657-a480-698efbe45a30
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-65787: `SchemaBuilder` falha durante a criação ou atualização do esquema devido a uma &quot;coluna&quot; de chave de matriz indefinida nos dados da tabela

O patch ACSD-65787 corrige o problema em que a classe `SchemaBuilder` falha durante a criação ou as atualizações do esquema devido a uma &quot;coluna&quot; de chave de matriz indefinida ao processar dados da tabela. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 está instalado. A ID do patch é ACSD-65787. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A classe `SchemaBuilder` falha durante a criação ou as atualizações do esquema devido a uma &quot;coluna&quot; de chave de matriz indefinida ao processar dados da tabela.

<u>Etapas a serem reproduzidas</u>:

1. Execute o seguinte comando:

```
bin/magento setup:upgrade
```

<u>Resultados esperados</u>:

Nenhum erro.

<u>Resultados reais</u>:

```
Error "Warning: Undefined array key "column" in SchemaBuilder.php on line 90
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
