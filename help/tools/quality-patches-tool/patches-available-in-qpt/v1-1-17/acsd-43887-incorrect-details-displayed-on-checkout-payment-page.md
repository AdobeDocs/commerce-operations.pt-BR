---
title: 'ACSD-43887: detalhes incorretos exibidos na página de pagamento do check-out'
description: O patch ACSD-43887 corrige o problema em que detalhes incorretos são exibidos na página de pagamento de check-out quando os Pedidos de compra para empresas estão ativados. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 está instalada. A ID do patch é ACSD-43887. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
exl-id: e150f093-9f1a-4ba5-bdcf-90e7f42a29c3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 4560f5f5-d00c-5b5d-b61b-369d85ef7a26
    internal-label: User Account
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%
---
# ACSD-43887: detalhes incorretos exibidos na página de pagamento do check-out

O patch ACSD-43887 corrige o problema em que detalhes incorretos são exibidos na página de pagamento de check-out quando os Pedidos de compra para empresas estão ativados. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.17 está instalada. A ID do patch é ACSD-43887. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Detalhes incorretos são exibidos na página de pagamento de check-out quando Ordens de compra para empresas estão habilitadas.

<u>Pré-requisitos</u>:

1. Os módulos B2B são instalados.
1. Habilitar Empresa está definido como _Sim_. Vá para **Lojas** > **Configurações** > **Geral** > **Recursos B2B** > **Habilitar Empresa** > **Sim**.
1. Habilitar Ordens de Compra está definido como _Sim_. Vá para **Configuração de Aprovação de Pedido** > **Habilitar Ordens de Compra** > **Sim**.
1. O PayPal Express está configurado como o método de pagamento.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto virtual.
1. Registre uma conta da empresa do front-end com um Administrador de empresa.
1. Aprove a conta da empresa do back-end e defina **Habilitar Ordens de Compra** como _Sim_ ao aprovar a empresa.
1. Acesse o front-end e faça logon usando a conta de administrador da empresa criada na etapa dois.
1. Crie um &quot;Usuário padrão&quot; para a empresa. Vá para **Usuário da Empresa** > **Adicionar Novo Usuário**.
1. Crie uma &quot;Regra de aprovação&quot; para a empresa. Vá para **Regras de Aprovação** > **Adicionar Nova Regra**.

   * Tipo de regra: Total da ordem
   * Total do pedido: é maior que ou igual a US$ 1
   * Exige aprovação de: Administrador da empresa

1. Faça logout e login usando a conta &quot;Usuário padrão&quot;.
1. Adicione o produto virtual criado na etapa um ao carrinho e prossiga para o check-out.
1. Selecione PayPal Express como método de pagamento e clique em **Fazer pedido de compra**.
1. Faça logoff e logon usando a conta de administrador da empresa.
1. Vá para **Minhas Ordens de Compra** e em **Ordens de Compra da Empresa**, clique em **Exibir** para a ordem criada na etapa nove.
1. Aprovar a ordem de compra. O status da ordem de compra deve ser &quot;Aprovado: Pagamento Pendente&quot;.
1. Faça logout e login usando a conta &quot;Usuário padrão&quot; da empresa.
1. Ir para **Minhas Ordens de Compra** > **Exibir** > **Fazer Pedido**.
1. Verifique o **Resumo de Pedidos**.

<u>Resultados esperados</u>:

O resumo do pedido mostra valores diferentes de zero corretos.

<u>Resultados reais</u>:

O valor total do resumo do pedido é zero.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
