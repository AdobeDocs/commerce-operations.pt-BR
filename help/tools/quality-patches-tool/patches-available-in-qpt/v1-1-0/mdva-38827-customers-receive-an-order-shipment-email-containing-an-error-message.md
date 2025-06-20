---
title: 'MDVA-38827: Os clientes recebem o erro de envio de pedido por email'
description: 'O patch MDVA-38827 corrige o problema em que os clientes recebem um email de envio de pedido contendo a seguinte mensagem de erro: *Desculpe, ocorreu um erro ao gerar esse conteúdo*. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 está instalada. A ID do patch é MDVA-38827. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.'
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ab522c9c-2983-4c2f-b341-4487bdbee34d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-38827: Os clientes recebem o erro de envio de pedido por email

O patch MDVA-38827 corrige o problema em que os clientes recebem um email de remessa de pedido contendo a seguinte mensagem de erro: *Ocorreu um erro ao gerar este conteúdo*. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 está instalada. A ID do patch é MDVA-38827. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando a opção Notificar Clientes por Email para remessa está selecionada, os clientes recebem um email contendo a seguinte mensagem de erro: *Ocorreu um erro ao gerar este conteúdo*.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Marketing** > **Comunicações** > **Modelos de email** e selecione **Adicionar Novo Modelo**.
   * Selecione **Vendas Magento** > **Nova Remessa**.
   * Clique em **Carregar Modelo**.
   * Adicione um nome de modelo (por exemplo, Modelo de envio principal) e clique em **Salvar**.
1. Ir para **Loja** > Configurações > **Configuração** > **Vendas** > **Email de Vendas**:
   * Habilitar **Comentários da Remessa**.
   * Selecione **Modelo de envio principal** (consulte a parte &quot;Adicionar um nome de modelo&quot; da Etapa 1) em Modelo de email de comentário de remessa e Modelo de email de comentário de remessa para convidado.
1. Fazer um pedido. Vá para o painel Administrador > **Vendas** > **Pedido**, clique em **Exibir** e envie o pedido.
1. O estado do pedido será alterado de Pendente para Processando.
1. Clique em **Remessas** no menu da barra lateral esquerda e em **Exibir** para ver o pedido.
1. Adicione um comentário ao **Texto do Comentário** abaixo de **Histórico da Remessa** e marque a caixa de seleção **Notificar Cliente por Email**.
1. Clique em **Enviar Comentário**.

<u>Resultados esperados</u>:

Email de vendas com comentários de remessa gerado.

<u>Resultados reais</u>:

A seguinte mensagem de erro é recebida no email: *Ocorreu um erro ao gerar este conteúdo.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
