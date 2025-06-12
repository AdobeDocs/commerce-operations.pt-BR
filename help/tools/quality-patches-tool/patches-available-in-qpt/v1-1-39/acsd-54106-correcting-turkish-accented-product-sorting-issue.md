---
title: 'ACSD-54106: Retificação da classificação de caracteres acentuados turcos na categoria de produto'
description: Aplique o patch ACSD-54106 para corrigir o problema do Adobe Commerce em que a classificação de produto de categoria por nome para caracteres com acento turco está incorreta.
feature: Categories, Products, Search
role: Admin
exl-id: 45c8efbb-85d0-4d25-9d7e-9c41a97e80fa
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-54106: Retificação da classificação de caracteres acentuados turcos na categoria de produto

O patch ACSD-54106 corrige o problema em que a classificação de produto de categoria por nome para caracteres acentuados turcos está incorreta. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39 está instalado. A ID do patch é ACSD-54106. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A classificação de produtos em categorias por nome está incorreta para caracteres com acento turco.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no painel de administração.
1. Crie produtos simples nomeados da seguinte maneira e atribua-os a qualquer categoria:

* Nome A
* Nome Ç
* Nome D
* Nome ➡
* Nome M
* Nome Ö
* Nome Ü
* Nome Y
* Nome Z

1. Navegue até a loja e acesse a categoria que contém os produtos.
1. Modifique a ordem de classificação para *[!UICONTROL By Name]*.

<u>Resultados esperados</u>:

Os produtos são classificados corretamente na seguinte ordem:

* Nome A
* Nome Ç
* Nome D
* Nome ➡
* Nome M
* Nome Ö
* Nome Ü
* Nome Y
* Nome Z

<u>Resultados reais</u>:

Os produtos são classificados incorretamente na seguinte ordem:

* Nome A
* Nome D
* Nome M
* Nome Y
* Nome Z
* Nome Ç
* Nome Ö
* Nome Ü
* Nome ➡

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
