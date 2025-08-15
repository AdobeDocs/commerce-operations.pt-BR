---
title: 'ACSD-66049: vitrines em outros idiomas exibem preços incorretos devido à versão da biblioteca ICU'
description: Aplique o patch ACSD-66049 para corrigir o problema do Adobe Commerce em que as vitrines em outros idiomas exibem preços incorretos devido à incompatibilidade de versões da biblioteca ICU em ambientes PHP mais antigos (versões 63.1 a 74.1).
feature: Products
role: Admin, Developer
type: Troubleshooting
exl-id: e667d462-87f6-4db5-bf3f-3213edac2f09
source-git-commit: da11e8bd5c4937ec2a7e548ce487797b83f8fd27
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-66049: vitrines em outros idiomas exibem preços incorretos devido à versão da biblioteca ICU

O patch ACSD-66049 corrige o problema em que vitrines não em inglês exibem preços incorretos devido à incompatibilidade de versões da biblioteca ICU em ambientes PHP mais antigos (versões 63.1 a 74.1). Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 está instalado. A ID do patch é ACSD-66049. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p3 - 2.4.5-p13, 2.4.7 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As vitrines em outros idiomas exibem um preço incorreto quando são usadas versões mais antigas da biblioteca ICU do PHP (63.1 a 74.1).

<u>Etapas a serem reproduzidas</u>:

1. Verificar versão da UTI:
   * Conecte-se ao servidor via SSH e execute o comando: `php -a`
   * No prompt, digite: `echo INTL_ICU_VERSION;`
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale]** > **[!UICONTROL Locale Options]**. **[!UICONTROL Configure Locale]** = *[!UICONTROL Hebrew (Israel)]*.
1. Crie um produto com preço = 100.
1. Visualize a página do produto na loja.

<u>Resultados esperados</u>:

O preço exibido não é 0.

<u>Resultados reais</u>:

Depois de aparecer brevemente como 100, o preço é atualizado imediatamente para 0.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
