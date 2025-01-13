---
title: 'ACSD-55339: Resolvendo problema de corte de SKU em cotações negociáveis para Adobe Commerce'
description: Aplique o patch ACSD-55339 para corrigir o problema do Adobe Commerce em que as SKUs do produto com zeros à esquerda são cortadas, causando erros de negociação.
feature: B2B, Quotes
role: Admin, Developer
source-git-commit: 5153eadfe0d90c256bf6d294fcebb1dd8c0a7093
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-55339: Resolvendo problema de corte de SKU em cotações negociáveis para Adobe Commerce

O patch ACSD-55339 corrige o problema em que as SKUs do produto com zeros à esquerda são cortadas, resultando em erros durante o processo de negociação. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.56 está instalado. A ID do patch é ACSD-55339. Observe que o problema está programado para ser corrigido no Adobe Commerce B2B 1.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

SKUs de produtos numéricos com zeros à esquerda são cortadas quando usadas em cotações negociáveis, resultando em erros que impedem a atualização de quantidades ou a definição de preços.

<u>Etapas a serem reproduzidas</u>:

1. Acesse a seção criação de produto no painel de administração.
1. Defina o [!UICONTROL SKU] para o produto como 01910.
1. Faça logon na loja e execute as seguintes operações:
   1. Adicionar produto ao carrinho.
   1. Exibir e editar o carrinho.
   1. Solicitar uma cotação.
1. Vá para [!UICONTROL admin] > [!UICONTROL Quote] > [!UICONTROL View] e [!UICONTROL Add Products by SKU] - 01910.

**Observação:** o SKU é exibido como *1910* em vez de *01910*. Essa discrepância impede que o usuário atualize a quantidade ou defina os preços, pois nenhum produto com o SKU 1910 existe no catálogo.

<u>Resultados esperados</u>:

A cotação negociável deve ser atualizada com sucesso sem erros.

<u>Resultados reais</u>:

Uma mensagem de aviso é exibida indicando que o produto não existe.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
