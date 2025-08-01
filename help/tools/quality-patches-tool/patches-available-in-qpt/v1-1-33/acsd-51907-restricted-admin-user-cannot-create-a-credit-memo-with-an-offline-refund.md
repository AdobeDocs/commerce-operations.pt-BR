---
title: 'ACSD-51907: O usuário administrador restrito não pode criar aviso de crédito para reembolso offline'
description: Aplique o patch ACSD-51907 para corrigir o problema do Adobe Commerce em que o usuário administrador restrito não pode criar um aviso de crédito com um reembolso offline.
exl-id: 1c44d99b-7633-4768-b7e7-332f3666a5d9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# ACSD-51907: O usuário administrador restrito não pode criar aviso de crédito para reembolso offline

O patch ACSD-51907 corrige o problema de desempenho em que o usuário administrador restrito não pode criar um memorando de crédito com um reembolso offline. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. A ID do patch é ACSD-51907. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador restrito não pode criar um aviso de crédito com um reembolso offline.

<u>Etapas a serem reproduzidas</u>:

1. Crie um **cliente** no site padrão.
1. Criar **novo site** com *loja* relacionada e *exibição de loja*.
1. Defina o site padrão para o novo site, limpe os caches.
1. Alterar Configuração do Cliente: **Admin** > **Loja** > **Configuração** > **Clientes** > **Configuração do Cliente** > **Compartilhar Contas do Cliente = Global**.
1. Crie uma nova função de usuário administrador com o escopo de função definido para o novo site criado *(acesso somente a dados de vendas)* em **Administrador** > **Sistema** > **Permissões**.
1. Crie uma nova conta de administrador com esta função.
1. Criar novo pedido usando o método de pagamento online *(por exemplo, Auth.net ou PayPal)*.
1. Faça logon como um usuário administrador restrito.
1. Vá para **Vendas** > **Pedidos** > e **página de exibição de pedidos**.
1. Criar uma NFF.
1. Navegue até a guia NFFs.
1. Clique em **Fatura**.
1. Clique em **[!UICONTROL Credit Memo]**.
1. Marque a caixa de seleção **[!UICONTROL Refund to Store Credit]** e defina o campo de texto próximo ao valor *1*.
1. Clique no botão **[!UICONTROL Refund Offline]**.

<u>Resultados esperados</u>:

O memorando de crédito é criado, e *$1* é reembolsado para o crédito da loja.

<u>Resultados reais</u>:

A mensagem de erro, *Mais permissões são necessárias para exibir este item* é exibida.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
