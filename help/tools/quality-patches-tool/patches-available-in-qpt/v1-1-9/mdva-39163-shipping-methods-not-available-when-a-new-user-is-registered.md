---
title: 'MDVA-39163: Métodos de envio não disponíveis para usuários recém-registrados com produtos da sessão de convidado'
description: O patch MDVA-39163 resolve o problema em que os métodos de envio não estão disponíveis quando um novo usuário é registrado e os produtos no carrinho são da sessão de convidado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 está instalada. A ID do patch é MDVA-39163. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
exl-id: 781b466b-7d8f-4ad1-9fb4-5404cd02f7d8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# MDVA-39163: Métodos de envio não disponíveis para usuários recém-registrados com produtos da sessão de convidado

O patch MDVA-39163 resolve o problema em que os métodos de envio não estão disponíveis quando um novo usuário é registrado e os produtos no carrinho são da sessão de convidado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 está instalada. A ID do patch é MDVA-39163. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os métodos de envio não estão disponíveis quando o novo usuário é registrado e os produtos no carrinho são da sessão de convidado.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Admin** > **Lojas** > **Configuração** > **Vendas** > **Métodos de Entrega**. Habilite somente o método de envio **Taxa Uniforme** e desabilite todo o resto.
1. No método de envio **Taxa Uniforme**, selecione a opção de país **Específico** disponível na configuração **Remeter para Países Aplicáveis** e selecione um país da lista (por exemplo, Estados Unidos).
1. Acesse **Administrador** > **Lojas** > **Configuração** > **Cliente** > **Configuração do Cliente** e defina **Exigir Confirmação de Email** para _Sim_.
1. Crie um novo Modelo de email em **Admin** > **Marketing** > **Modelos de email** e carregue o modelo `Footer (magento/luma)` e substitua o conteúdo do modelo por um bloco do CMS.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Vá para **Admin** > **Conteúdo** > **Design** > **Configuração** e selecione o tema relacionado ao site de front-end. Defina o &quot;Modelo de rodapé&quot; para o novo modelo de email criado.
1. Acesse o front-end e adicione um produto ao carrinho.
1. Crie um cliente; você receberá um email para confirmar o endereço de email. Clique no link de verificação. Você será conectado ao site.
1. Vá para **Minha conta** e adicione um endereço. Defina o país do endereço para o país de entrega definido na configuração do administrador anteriormente.
1. Vá para o check-out.

<u>Resultados esperados</u>:

O método de envio está disponível, pois o cliente tem um endereço compatível com o país de envio.

<u>Resultados reais</u>:

Método de envio não disponível.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
