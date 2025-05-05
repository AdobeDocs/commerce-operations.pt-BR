---
title: "ACSD-51899: endereço de entrega padrão preenchido automaticamente incorretamente"
description: Aplique o patch ACSD-51899 para corrigir o problema do Adobe Commerce em que o endereço de envio padrão é preenchido automaticamente com um endereço errado.
feature: Checkout
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-51899: endereço de entrega padrão preenchido automaticamente incorretamente

O patch ACSD-51899 corrige o problema em que o endereço de envio padrão é preenchido automaticamente com um endereço errado. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. A ID do patch é ACSD-51899. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O endereço de entrega padrão é preenchido automaticamente com um endereço errado

<u>Etapas a serem reproduzidas</u>:

1. Habilitar **Seleção na Loja** no método de envio.
1. Criar *estoque* e *origem*.
1. Crie o produto e atribua-o à origem.
1. Adicionar um produto ao carrinho.
1. Clique em **Prosseguir para o check-out** do minicarrinho.
1. Insira o endereço de email de teste e selecione **Escolher na loja**.
1. Clique no botão **Selecionar armazenamento** e selecione um local de armazenamento para escolher.
1. Clique no botão **avançar**.
1. Navegue até a **Home Page** clicando no logotipo da loja.
1. Abra o **Minicarrinho**.
1. Clique no hiperlink inferior chamado **Exibir e editar carrinho**.
1. Clique em **Prosseguir para o check-out**.
1. Clique no botão de envio na página de envio.

<u>Resultados esperados</u>

O campo de endereço de remessa permanece vazio exceto por *País, Região e CEP*.

<u>Resultados reais</u>

O endereço de remessa padrão é preenchido automaticamente com o endereço *coleta na loja* depois de atualizar a página.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
