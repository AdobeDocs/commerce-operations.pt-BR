---
title: 'ACSD-66093: campos de nome de cliente convidado permitem entrada de email causando emails de pedido inválido'
description: Aplique o patch ACSD-66093 para corrigir o problema do Adobe Commerce em que é possível inserir endereços de email nos campos de cliente convidado **[!UICONTROL First Name]** e **[!UICONTROL Last Name]** e enviar emails de confirmação de pedido inválidos.
feature: Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 30790492-330e-4810-8069-fce87b40ebb2
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-66093: campos de nome de cliente convidado permitem entrada de email causando emails de pedido inválido

O patch ACSD-66093 corrige o problema em que endereços de email podiam ser inseridos nos campos **[!UICONTROL First Name]** e **[!UICONTROL Last Name]** do cliente convidado, resultando em emails de confirmação de pedido inválidos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 está instalado. A ID do patch é ACSD-66093. Observe que o problema foi corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p11

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os endereços de email puderam ser inseridos nos campos **[!UICONTROL First Name]** e **[!UICONTROL Last Name]** do cliente convidado, o que resultou em emails de confirmação de pedido inválidos.

<u>Etapas a serem reproduzidas</u>:

1. Adicione produtos ao carrinho como cliente convidado.
2. Vá para o check-out.
3. Preencha o Endereço de email com &quot;test1@gmail.co&quot;.
4. Preencha **[!UICONTROL First Name]** com &quot;<test2@gmail.co>&quot;.
5. Preencha **[!UICONTROL Last Name]** com &quot;<test3@gmail.co>&quot;.
6. Preencha outros campos obrigatórios.
7. Fazer pedido.

<u>Resultados esperados</u>:

As mensagens de validação devem aparecer indicando que os campos **[!UICONTROL First Name]** e **[!UICONTROL Last Name]** não são válidos, como *O Nome não é válido! e o sobrenome não é válido!* e o pedido não devem ser feitos.

<u>Resultados reais</u>:

O pedido é feito.
**[!UICONTROL First Name]** e **[!UICONTROL Last Name]** campos são salvos como inseridos.
O email de confirmação de pedido é enviado para os três emails: test1@gmail.co, test2@gmail.co e test3@gmail.co.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
