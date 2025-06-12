---
title: 'ACSD-48784: preços de segmento do cliente armazenados incorretamente em cache entre grupos de clientes'
description: Aplique o patch ACSD-48784 para corrigir o problema do Adobe Commerce em que os preços de segmento do cliente são armazenados em cache incorretamente entre grupos de clientes.
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
exl-id: a691c61c-fdba-4d6a-8314-095dfb0ba4a1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48784: preços de segmento do cliente armazenados incorretamente em cache entre grupos de clientes

O patch ACSD-48784 corrige o problema em que os preços de segmento do cliente são armazenados incorretamente em cache entre grupos de clientes. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 está instalado. A ID do patch é ACSD-48784. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os preços de segmento do cliente são armazenados incorretamente em cache entre grupos de clientes.

<u>Pré-requisitos</u>:

Configurar [!DNL Varnish] ou [!DNL Fastly].

<u>Etapas a serem reproduzidas</u>:

1. Habilite o armazenamento em cache de página inteira em sua loja.
1. Faça logon no site como um usuário com preços especiais de grupo de clientes.
1. Acesse a página de um produto com preços especiais para o grupo de clientes. Observe o *preço especial*.
1. Em um navegador separado, abra a mesma página do produto que um usuário convidado sem fazer logon. Observe o preço normal.
1. Acesse a interface administrativa do Adobe Commerce e limpe a Adobe Commerce e o cache do [!DNL Fastly] para esse armazenamento.
1. No navegador conectado, remova o cookie `X-Magento-Vary`.
1. No navegador conectado, recarregue a mesma página de produto várias vezes até que o cache seja totalmente liberado.
1. No navegador não conectado, recarregue a página do produto para ver agora os preços do grupo de clientes.

<u>Resultados esperados</u>:

A página do produto mostra o preço correto para grupos de clientes específicos.

<u>Resultados reais</u>:

* Os usuários convidados verão o preço especial de usuário conectado.
* O minicarrinho mostra o preço correto depois que o produto é adicionado a ele.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
