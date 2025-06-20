---
title: 'ACSD-51291: O administrador restrito pode adicionar imagens/vídeos ao produto atribuído a vários sites'
description: Aplique o patch ACSD-51291 para corrigir o problema do Adobe Commerce, em que o administrador restrito com acesso a um site pode adicionar imagens/vídeos a um produto atribuído a vários sites.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: a4edd034-f718-4559-9993-11609f0d0efa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-51291: O administrador restrito pode adicionar imagens/vídeos ao produto atribuído a vários sites

O patch ACSD-51291 corrige o problema em que um administrador restrito com acesso a um site pode adicionar imagens/vídeos a um produto atribuído a vários sites. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 está instalado. A ID do patch é ACSD-51291. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um administrador restrito com acesso a um site pode adicionar imagens/vídeos a um produto atribuído a vários sites.

<u>Etapas a serem reproduzidas</u>

1. Faça logon como administrador.
1. Crie um segundo site, loja e exibição de loja.
1. Crie uma segunda função de administrador com recursos somente para o segundo site, loja e visualização de loja.
1. Crie um segundo administrador e atribua-o à nova função de administrador restrito.
1. Crie um novo produto e atribua-o aos sites padrão e aos novos sites.
1. Faça logoff do perfil de administrador principal.
1. Faça logon como o novo administrador restrito.
1. Edite o produto criado, que foi atribuído a ambos os sites.
1. Abra a guia **[!UICONTROL Images and Videos]**.

<u>Resultados esperados</u>:

* A seguinte mensagem é exibida:

  *O administrador restrito tem permissão para executar ações com imagens ou vídeos, somente quando o administrador tem direitos a todos os sites aos quais o produto está atribuído.*

* O botão **[!UICONTROL Add Video]** não está ativo.

<u>Resultados reais</u>:

O administrador restrito pode adicionar imagens e vídeos mesmo quando o produto é atribuído a um site ao qual ele não tem acesso.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
