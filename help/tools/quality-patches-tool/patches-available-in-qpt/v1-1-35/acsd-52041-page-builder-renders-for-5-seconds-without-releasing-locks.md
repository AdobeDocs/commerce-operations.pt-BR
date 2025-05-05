---
title: 'ACSD-52041: a renderização do Page Builder não libera bloqueios'
description: Aplique o patch ACSD-52041 para corrigir o problema do Adobe Commerce em que o Page Builder é renderizado por cinco segundos sem liberar bloqueios.
feature: Page Builder
role: Admin, Developer
exl-id: 48a7fc36-e98a-4a4e-bed3-248d7d73f6cb
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52041: a renderização do Page Builder não libera bloqueios

O patch ACSD-52041 corrige o problema em que o Page Builder é renderizado por cinco segundos sem liberar bloqueios. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.48 está instalado. A ID do patch é ACSD-52041-v2. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 e 2.4.6 - 2.4.6-p2.



>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.


## Problema

O **[!DNL Page Builder]** é renderizado por *5* segundos sem liberar os bloqueios.

<u>Etapas a serem reproduzidas</u>:

1. Edite uma página do CMS, uma página de produto ou qualquer outra que tenha **[!DNL Page Builder]**.
1. Salve as alterações.
1. Observe que a página economiza tempo.

<u>Resultados esperados</u>

O conteúdo é salvo. Nenhum erro encontrado no log do navegador.

<u>Resultados reais</u>

O salvamento demora mais do que o tempo normal para ser concluído.
Erro no console: ``Page Builder was rendering for 5 seconds without releasing locks``

## Aplicar o patch

Para aplicar patches individuais às versões **2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 e 2.4.6 - 2.4.6-p2**, use os seguintes links, dependendo do seu método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR>) no guia [!DNL Quality Patches Tool].
