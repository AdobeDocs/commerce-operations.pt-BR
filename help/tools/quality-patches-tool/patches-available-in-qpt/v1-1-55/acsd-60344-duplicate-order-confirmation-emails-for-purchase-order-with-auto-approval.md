---
title: 'ACSD-60344: Emails de confirmação de pedido duplicados ao usar [!UICONTROL Purchase Order] com aprovação automática'
description: Aplique o patch ACSD-60344 para corrigir o problema do Adobe Commerce em que emails de confirmação de pedido duplicados estão sendo enviados ao usar um [!UICONTROL Purchase Order] com aprovação automática.
feature: Purchase Orders
role: Admin, Developer
exl-id: c4d415ee-b1ac-4094-9209-19b91f9a7666
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344: Emails de confirmação de pedido duplicados ao usar *[!UICONTROL Purchase Order]* com aprovação automática

O patch ACSD-60344 corrige o problema em que emails de confirmação de pedido duplicados estão sendo enviados ao usar um *[!UICONTROL Purchase Order]* com aprovação automática. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-60344. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6-p4

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Emails de confirmação de pedido duplicados são enviados ao usar um *[!UICONTROL Purchase Order]* com aprovação automática.

<u>Pré-requisitos</u>

Habilitar módulos B2B e *[!UICONTROL Purchase Order]*.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma conta de empresa e habilite *[!UICONTROL Purchase Order]* para ela.
1. Crie uma conta de usuário regular e adicione-a à conta da empresa como um usuário da empresa.
1. Fazer um pedido usando esta conta.
1. Execute o cron e verifique os emails.

<u>Resultados esperados</u>:

Somente um email de confirmação de pedido é recebido por pedido.

<u>Resultados reais</u>:

Dois emails de confirmação de pedido são recebidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
