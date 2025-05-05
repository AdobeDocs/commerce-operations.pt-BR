---
title: 'ACSD-62952: data do registro de presentes exibida imprecisamente na loja'
description: Aplique o patch ACSD-62952 para corrigir o problema do Adobe Commerce em que a data do Registro de presentes é exibida incorretamente na vitrine.
feature: Gift, Storefront
role: Admin, Developer
source-git-commit: 1fad4ecf1bab1df7a106ca12fe0431f19b65fb68
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-62952: data do registro de presentes exibida imprecisamente na loja

O patch ACSD-62952 corrige o problema em que a data do Registro de presentes é exibida incorretamente na loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 está instalado. A ID do patch é ACSD-62952. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A data do evento exibida na loja para um Registro de presentes compartilhados é mostrada incorretamente como um dia anterior à data real.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no front-end como o cliente do.
1. No painel [!UICONTROL My Account], clique em **[!UICONTROL Gift Registry]**.
1. Se não houver um registro existente, crie um e especifique qualquer data.
1. Adicione qualquer item ao carrinho.
1. Na página do carrinho, clique em **[!UICONTROL Add all items to Gift Registry]**.
1. Compartilhe o Registro de presentes.

<u>Resultados esperados</u>:

O Registro de presentes exibe a data de evento correta.

<u>Resultados reais</u>:

O e-mail Registro de presentes aberto a partir do convite exibe a data do evento como um dia antes.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: Atualizações e patches > Aplicar patches no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.

