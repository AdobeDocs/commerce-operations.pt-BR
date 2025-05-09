---
title: 'ACSD-63406: Cotações persistentes expiradas não limpas quando o trabalho persistence_clear_expired cron é executado'
description: Aplique o patch ACSD-63406 para corrigir o problema do Adobe Commerce em que as aspas persistentes expiradas não são apagadas por nenhum trabalho cron quando o trabalho "persistent_clear_expired" cron é executado.
feature: Quotes, Shopping Cart
role: Admin, Developer
source-git-commit: b3bb6ae825f4912b19e2d1f88b5d55835d9769ff
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACSD-63406: Aspas persistentes expiradas não limpas quando o trabalho `persistent_clear_expired` do cron é executado

O patch ACSD-63406 corrige o problema em que as aspas persistentes expiradas não são apagadas por nenhum trabalho cron quando o trabalho cron `persistent_clear_expired` é executado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 está instalado. A ID do patch é ACSD-63406. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Aspas persistentes expiradas não são apagadas por nenhum trabalho cron quando o trabalho cron `persistent_clear_expired` é executado.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma categoria e um produto.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]**.
   1. Defina todas as opções como *Sim*.
   1. Defina **[!UICONTROL Persistence Lifetime (seconds)]** como *60*.
1. Crie uma conta de cliente na loja e faça logon.
1. Adicione um produto ao carrinho.
1. Saia, aguarde 60 segundos e faça logon novamente.

<u>Resultados esperados</u>:

O trabalho cron `persistent_clear_expired` deve excluir aspas persistentes com base nas configurações de tempo de vida de persistência na configuração.

<u>Resultados reais</u>:

O valor `is_persistent` da cotação do cliente permanece *1* na tabela de cotações.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
