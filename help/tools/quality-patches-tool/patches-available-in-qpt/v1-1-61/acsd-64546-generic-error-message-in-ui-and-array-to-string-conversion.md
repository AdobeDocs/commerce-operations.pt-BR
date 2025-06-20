---
title: 'ACSD-64546: Mensagem de erro genérico na interface e exceção de conversão de matriz em cadeia de caracteres durante a criação do rótulo UPS'
description: Aplique o patch ACSD-64546 para corrigir o problema do Adobe Commerce em que uma mensagem de erro genérica é exibida na interface do usuário e a exceção de conversão de matriz em string é registrada durante a criação do rótulo UPS. O patch garante que o erro correto seja mostrado na interface e nos logs.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 458371bc-4afe-4675-b090-5797e05c5b88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-64546: Exceção de mensagem de erro genérica na interface do usuário e *Conversão de matriz em cadeia de caracteres* durante a criação do rótulo UPS

O patch ACSD-64546 corrige o problema em que uma mensagem de erro genérica é exibida na interface e a exceção *Array para conversão de sequência* é registrada durante a criação do rótulo UPS, garantindo que o erro correto seja mostrado na interface e nos logs. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 está instalado. A ID do patch é ACSD-64546. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**
* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma mensagem de erro genérica é exibida na interface do usuário e a exceção *Matriz para conversão de cadeia de caracteres* ocorre durante a criação do rótulo UPS.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma conta de cliente com um endereço válido.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL GENERAL]** > **[!UICONTROL General]** > **[!UICONTROL Store Information]** e adicione um endereço válido.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Shipping settings]** > **[!UICONTROL Origin]** e adicione um endereço válido.
1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Delivery methods]** > **[!UICONTROL UPS]** e configure o UPS.
1. Fazer um pedido usando [!UICONTROL UPS].
1. Remova a ID de usuário e a senha da UPS de `core_config_data` no banco de dados.
1. Limpar cache de configuração.
1. Abra a ordem criada no **[!UICONTROL Admin]**.
1. Criar uma nova remessa.
   1. Marque a caixa de seleção **[!UICONTROL Create Shipping Label]**.
   1. Clique em **[!UICONTROL Submit shipment]**.
   1. Adicionar o produto a um pacote. Especifique o tamanho do pacote (comprimento, largura e altura).
   1. Clique em **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

A mensagem de erro real é exibida na interface do usuário e nos logs do.

<u>Resultados reais</u>:

* O seguinte erro é exibido na interface do usuário:
  *Ocorreu um erro ao criar o rótulo de remessa.*
* A exceção *Array para conversão de cadeia de caracteres* impede que a mensagem de erro real seja exibida ou armazenada nos logs.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:
* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: Atualizações e patches > Aplicar patches no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:
* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
