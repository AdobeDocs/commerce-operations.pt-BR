---
title: 'MDVA-41399: Não é possível acessar o Gerenciar carrinho de compras se um cliente adicionar produto à lista de desejos'
description: O patch MDVA-41399 resolve o problema em que os usuários administradores não conseguem acessar a página Gerenciar carrinho de compras se um cliente adicionar um produto à lista de desejos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 está instalada. A ID do patch é MDVA-41399. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41399: Não é possível acessar o Gerenciar carrinho de compras se um cliente adicionar produto à lista de desejos

O patch MDVA-41399 resolve o problema em que os usuários administradores não conseguem acessar a página Gerenciar carrinho de compras se um cliente adicionar um produto à lista de desejos. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 está instalada. A ID do patch é MDVA-41399. Observe que o problema foi corrigido no Adobe Commerce 2.4.2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários administradores não podem acessar a página Gerenciar carrinho de compras se um cliente adicionar um produto à lista de desejos.

<u>Pré-requisitos</u>:

1. Crie dois ou mais produtos.
1. Crie um cliente.
1. Ative o Modo de desenvolvedor.

<u>Etapas a serem reproduzidas</u>:

1. Acesse a Loja e faça logon como cliente dentre as pré-condições.
1. Adicione um produto à Lista de desejos.
1. Vá para o painel Admin, navegue até a página de edição criada pelo cliente e clique no botão **Gerenciar carrinho de compras**.

<u>Resultados esperados</u>:

O usuário administrador pode gerenciar o carrinho de compras.

<u>Resultados reais</u>:

O usuário administrador recebe uma mensagem de erro: *Ocorreu um erro. Consulte o log de erros para obter detalhes.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
