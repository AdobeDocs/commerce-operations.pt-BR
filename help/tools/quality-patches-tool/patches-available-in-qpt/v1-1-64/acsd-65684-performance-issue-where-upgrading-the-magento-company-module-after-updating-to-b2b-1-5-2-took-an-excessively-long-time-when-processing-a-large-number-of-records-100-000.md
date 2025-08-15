---
title: 'ACSD-65684: a atualização da Magento_Company no B2B 1.5.2 é lenta, com mais de 100.000 registros na company_structure'
description: Aplique o patch ACSD-65684 para corrigir o problema do Adobe Commerce em que a atualização do módulo Magento_Company no B2B 1.5.2 demora muito devido ao processamento de um grande número de registros (~100.000+) na tabela company_structure.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: 1b45ebe4-4fb4-4fb5-b107-a2d44ec784e0
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-65684: A atualização do `Magento_Company` em [!DNL B2B] 1.5.2 está lenta, com mais de 100.000 registros em `company_structure`

O patch ACSD-65684 corrige um problema de desempenho em que a atualização do módulo `Magento_Company` no [!DNL B2B] 1.5.2 demora muito ao processar mais de 100.000 registros na tabela `company_structure`. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 está instalado. A ID do patch é ACSD-65684. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce B2B (todos os métodos de implantação) 1.5.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce B2B (todos os métodos de implantação) 1.5.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Problema de desempenho em que a atualização do módulo `Magento_Company` em [!DNL B2B] 1.5.2 demora muito para processar mais de 100.000 registros na tabela `company_structure`.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce 2.4.7-p4 com [!DNL B2B].
1. Adicionar 100.000 registros à tabela `company_structure`.
1. Atualize para o Adobe Commerce 2.4.7-p5 e o módulo [!DNL B2B] mais recente (1.5.2).
1. Aplique o patch ACSD-65540.
1. Executar:

```
bin/magento setup:upgrade
```

<u>Resultados esperados</u>:

`setup:upgrade` é concluído em um prazo razoável.

<u>Resultados reais</u>:

O `setup:upgrade` demora muito para ser concluído.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
