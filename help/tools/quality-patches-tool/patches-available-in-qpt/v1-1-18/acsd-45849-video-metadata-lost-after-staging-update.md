---
title: "ACSD-45849: os metadados de vídeo são perdidos após a atualização de preparo"
description: O patch ACSD-45849 corrige o problema em que os metadados de vídeo são perdidos após a aplicação de uma atualização de preparo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 está instalada. A ID do patch é ACSD-45849. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.
feature: Staging, Page Content
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-45849: os metadados de vídeo são perdidos após a atualização de preparo

O patch ACSD-45849 corrige o problema em que os metadados de vídeo são perdidos após a aplicação de uma atualização de preparo. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 está instalada. A ID do patch é ACSD-45849. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os metadados de vídeo são perdidos após a aplicação de uma atualização de preparo.

<u>Etapas a serem reproduzidas</u>:

1. Configure a chave da API do YouTube em **Admin** > **Lojas** > **Configuração** > **Catálogo** > **Vídeo de Produto**.
1. Crie um produto com um vídeo do YouTube. Observe que o URL, o título e a descrição estão preenchidos.
1. Crie uma nova atualização agendada para o produto com quaisquer parâmetros sem alterar a seção *Imagens e Vídeo*.
1. Clique em **Exibir/Editar** em Alterações agendadas.
1. Vá para **Imagens e Vídeos** e clique no vídeo.

<u>Resultados esperados</u>:

O URL, o título e a descrição contêm dados apropriados.

<u>Resultados reais</u>:

Os campos URL, title e description estão vazios.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
