---
title: 'ACSD-49628: [!DNL Page Builder] Erros CORS impedem o salvamento do produto'
description: Aplique o patch ACSD-49628 para corrigir o problema do Adobe Commerce em que os erros  [!DNL Page Builder] CORS impedem o salvamento do produto.
feature: Categories, Page Builder, Products
role: Admin
exl-id: 5bceddfa-5fbf-4ebe-a233-de7720764849
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-49628: [!DNL Page Builder] erros do CORS impedem o salvamento do produto

O patch ACSD-49628 corrige o problema em que [!DNL Page Builder] erros do CORS impedem que um administrador salve um produto. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.32 está instalado. A ID do patch é ACSD-49628. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL Page Builder] Erros do CORS impedem o salvamento de um produto.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como administrador.
1. Crie uma função de usuário com as seguintes permissões:

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. Não adicione nenhuma permissão *[!UICONTROL Content]*.
1. Crie outro usuário administrador e atribua as funções criadas acima a esse usuário.
1. Crie um produto e faça logout.
1. Faça logon como o segundo administrador.
1. Tente editar e salvar o produto.

<u>Resultados esperados</u>:

O segundo administrador pode salvar o produto, mas o botão **[!UICONTROL Edit with Page Builder]** não é exibido para o administrador sem nenhuma permissão *[!UICONTROL Content]*.

<u>Resultados reais</u>:

O segundo administrador não pode salvar o produto devido a vários erros [!DNL Page Builder].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
