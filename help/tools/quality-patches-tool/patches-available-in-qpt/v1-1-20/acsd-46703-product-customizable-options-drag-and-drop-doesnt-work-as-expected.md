---
title: 'ACSD-46703: o arrastar e soltar da personalização do produto não funciona'
description: Este artigo fornece uma solução para o problema em que as opções personalizáveis do produto de arrastar e soltar não funcionam conforme esperado.
feature: Products
role: Developer
exl-id: 38b9490a-c9d4-4f8e-b90f-69bf50a6b571
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-46703: o arrastar e soltar da personalização do produto não funciona

O patch ACSD-46703 corrige o problema em que as opções personalizáveis do produto (arrastar e soltar) não funcionam conforme esperado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 está instalada. A ID do patch é ACSD-46703. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da [Ferramenta de Patches de Qualidade]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários não podem arrastar e soltar as opções personalizáveis de uma página para outra.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Adicione opções personalizáveis ao produto simples e certifique-se de adicionar mais de 20 opções, resultando em paginação.
1. Tente mover uma opção personalizável (arrastar e soltar) dentro da mesma página.
1. Agora tente mover uma opção personalizável da página dois para a página um.

<u>Resultados esperados</u>:

* Você pode arrastar e soltar as opções personalizáveis de uma página para outra.
* É possível classificar os valores usando a funcionalidade arrastar e soltar, mesmo para várias páginas.

<u>Resultados reais</u>:

Você não pode mover nenhum valor para outra página usando a funcionalidade arrastar e soltar.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Ferramentas de correção de qualidade > Uso](/help/tools/quality-patches-tool/usage.md) no guia Ferramenta de correção de qualidade.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
