---
title: Verifique o problema do Adobe Commerce com a Ferramenta de correções de qualidade
description: Este artigo fornece uma visão geral da Ferramenta de correções de qualidade (QPT) e links para recursos que explicam como usá-la.
feature: Tools and External Services
role: Admin
source-git-commit: 6f311fc4c20caca8b98d4c3c06642e5f61dc614f
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Verifique o problema do Adobe Commerce com a Ferramenta de correções de qualidade

Este artigo fornece uma visão geral da Ferramenta de correções de qualidade (QPT) e links para recursos que explicam como usá-la.

## Produtos e versões afetados

* Adobe Commerce local, todas as [versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## O que são a Ferramenta de correção de qualidade

A [Ferramenta de Patches de Qualidade](https://github.com/magento/quality-patches) (QPT) são patches individuais desenvolvidos pela Adobe e pela comunidade Magento Open Source.

Ele permite:

* aplicar patches de qualidade incluídos no pacote
* reverter patches aplicados anteriormente
* veja as informações gerais sobre patches de qualidade disponíveis para a versão instalada do Adobe Commerce.

Este é um exemplo da tabela de status que você pode obter para visualizar os patches disponíveis:

![Magento_patches_list](/help/assets/tools/status_table.png)

A ferramenta tem como objetivo permitir que você faça o autoatendimento com patches para problemas que possam ocorrer com o Adobe Commerce ou aplique facilmente patches sugeridos pelo suporte da Adobe Commerce.

>[!NOTE]
>
>O QPT é apenas para correções de qualidade. Os patches de segurança estão disponíveis na [Central de Segurança do Magento](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview).

## Patches disponíveis na Ferramenta de patches de qualidade

Consulte a [Ferramenta de Patches de Qualidade](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) em nossa documentação do desenvolvedor para obter a lista de patches disponíveis.

## Como instalar e usar a Ferramenta de correções de qualidade

Os comandos de instalação e uso são diferentes para o Adobe Commerce no local e o Adobe Commerce na infraestrutura em nuvem, porque para a nuvem o pacote QPT está incluído no pacote ece-tools.

### Como instalar e usar o QPT para Adobe Commerce no local

Consulte o [Guia de Atualização de Software > Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) em nossa documentação do desenvolvedor para obter detalhes sobre como instalar e usar o QPT para aplicar e reverter patches.

### Como instalar e usar o QPT para Adobe Commerce na infraestrutura em nuvem

Consulte [Nuvem para Adobe Commerce > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) em nossa documentação do desenvolvedor para obter detalhes sobre como instalar e usar o QPT para aplicar e reverter patches no Adobe Commerce na infraestrutura em nuvem.

## Leitura relacionada

* [Notas de versão da Ferramenta de correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes) em nossa documentação do desenvolvedor.
* [Como aplicar os patches do compositor fornecidos pelo Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) na base de dados de conhecimento de suporte.
