---
title: 'MDVA-39305-V3: problema de logon com habilitado [!DNL Google reCAPTCHA]'
description: Aplique o patch MDVA-39305-V3 para corrigir o problema do Adobe Commerce em que os clientes registrados não conseguem fazer logon quando o  [!DNL Google reCAPTCHA]  está habilitado. Este patch também corrige o problema em que um formulário pode ser enviado antes do  [!DNL Google reCAPTCHA] ser totalmente carregado. Além disso, ele corrige o erro *Call to a member function isDisabled() em null* quando blocos são usados em locais não padrão em uma página do CMS.
feature: Console
role: Admin
source-git-commit: 7846079987d2b7c0e9fdd0485bb3aae4f09cd6f9
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-39305-V3: problema de logon com [!DNL Google reCAPTCHA] habilitado

>[!NOTE]
>
>Este patch é uma atualização do patch [MDVA-39305](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md).

O patch MDVA-39305-V3 corrige o problema em que clientes registrados não conseguem fazer logon quando o [!DNL Google reCAPTCHA] está habilitado. Este patch também corrige o problema em que um formulário pode ser enviado antes que o [!DNL Google reCAPTCHA] seja totalmente carregado. Além disso, ele corrige o erro *Chamada para uma função membro isDisabled() em null* quando blocos são usados em locais não padrão em uma página do CMS.

Este patch foi adicionado na [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) versão 1.1.48. Ele foi atualizado na versão 1.1.58 do QPT para incluir novas versões do Adobe Commerce 2.4.7 - 2.4.7-p4. A ID do patch é MDVA-39305-V3. Observe que o problema foi corrigido nas versões 2.4.4, 2.4.5-p2 e 2.4.7 do Adobe Commerce.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4, 2.4.5-p2, 2.4.7

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problemas

### Caso I

1. Os clientes registrados não podem fazer logon usando o [!DNL Google reCAPTCHA] habilitado.
1. Um formulário pode ser enviado antes que [!DNL Google reCAPTCHA] seja totalmente carregado.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** > **[!DNL Google reCAPTCHA Storefront]** e habilite ***[!DNL Google reCAPTCHA]**.
1. Vá para o front-end.
1. Abra **[!UICONTROL Developer Tool Console]** no navegador.

<u>Resultados esperados</u>:

Nenhum aviso de CSP no console.

<u>Resultados reais</u>:

Avisos de CSP no console.

### Caso II

Erro informando que a chamada *para uma função membro isDisabled() em null* é lançada quando blocos são usados em locais não padrão em uma página do CMS.

<u>Etapas a serem reproduzidas</u>:

1. Crie um bloco estático com o conteúdo abaixo:

   ```
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. Adicionar um bloco estático em uma página do CMS de **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Add/Edit CMS page]** > **[!UICONTROL Content]**.
1. Salve a página.

<u>Resultados esperados</u>:

A página é carregada sem erros.

<u>Resultados reais</u>:

Ocorre um erro 500 na página da loja.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.


