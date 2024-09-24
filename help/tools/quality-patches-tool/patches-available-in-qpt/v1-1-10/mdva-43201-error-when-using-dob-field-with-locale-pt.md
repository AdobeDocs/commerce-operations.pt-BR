---
title: "MDVA-43201: Erro ao usar o campo DOB com PT de localidade"
description: O patch MDVA-43201 resolve o problema em que ocorre um erro ao usar o atributo do cliente DOB no formulário de registro do cliente para a localidade portuguesa. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 está instalada. A ID do patch é MDVA-43201. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: B2B, Cache
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-43201: erro ao usar o campo DOB com PT de localidade

O patch MDVA-43201 resolve o problema em que ocorre um erro ao usar o atributo do cliente DOB no formulário de registro do cliente para a localidade portuguesa. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 está instalada. A ID do patch é MDVA-43201. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando o atributo DOB customer é adicionado ao formulário de registro do cliente para localidade portuguesa, o formulário fornece o erro *Argument 1 passado para iterator_to_array() must implement interface travesable, null given*.

<u>Pré-requisitos</u>:

Os módulos B2B são instalados.

<u>Etapas a serem reproduzidas</u>:

1. Acesse Admin > **Lojas** > **Configuração** > **Geral** > **Opções de Localidade**, defina a Localidade como **Português (Portugal)** e clique em **Salvar**.
1. Reindexe e limpe o cache.
1. Vá para **Lojas** > **Atributo** > **Cliente**.
1. Abra o atributo de cliente DOB e defina **Mostrar na Loja** como **Sim**.
1. Selecione tudo de **Formulário a ser usado em**.
1. Salve o atributo.
1. Acesse a página Criar nova conta no front-end.

<u>Resultados esperados</u>:

O formulário de registro do cliente da loja portuguesa não fornece nenhum erro ao adicionar o atributo DOB.

<u>Resultados reais</u>:

O formulário de registro do cliente da loja portuguesa fornece um erro ao adicionar o atributo DOB.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
