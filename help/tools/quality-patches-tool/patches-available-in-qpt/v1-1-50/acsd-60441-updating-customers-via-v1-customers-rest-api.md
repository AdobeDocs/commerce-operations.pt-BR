---
title: 'ACSD-60441: A atualização de clientes por meio do ponto de extremidade V1/customers [!DNL REST] API gera um erro'
description: Aplique o patch ACSD-60441 para corrigir o problema do Adobe Commerce em que a atualização de clientes por meio da V1/customers [!DNL REST] API ao usar o token de acesso de integração gerado do back-end gera um erro.
feature: REST, Customers
role: Admin, Developer
exl-id: 3936c065-41a6-4860-8313-e054f9b23ac7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-60441: A atualização de clientes via ponto de extremidade de API `V1/customers` [!DNL REST] gera um erro

O patch ACSD-60441 corrige o problema em que atualizar clientes por meio da API `V1/customers` [!DNL REST] ao usar o token de acesso de integração gerado do back-end causa um erro. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 está instalado. A ID do patch é ACSD-60441. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p8

**Compatível com as versões do Adobe Commerce**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p9, 2.4.5-p8, 2.4.6-p6, 2.4.7-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A atualização de clientes por meio do ponto de extremidade de API `V1/customers` [!DNL REST] ao usar o token de acesso de integração gerado do back-end gera um erro.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma integração do Administrador.
1. Envie uma solicitação [!DNL POST] para `rest/default/V1/customers/<customer_id>` usando o token de integração.

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u>Resultados esperados</u>:

Os dados do cliente são atualizados.

<u>Resultados reais</u>:

Você recebe o seguinte erro:

    &quot;json
    {
    &quot;message&quot;: &quot;Um cliente com o mesmo endereço de email já existe em um site associado.&quot;,
    &quot;trace&quot;: ...
    }
    &quot;

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
