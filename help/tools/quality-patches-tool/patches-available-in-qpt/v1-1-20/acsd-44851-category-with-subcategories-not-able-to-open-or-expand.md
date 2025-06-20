---
title: 'ACSD-44851: Categoria com subcategorias não capazes de abrir ou expandir'
description: Este artigo fornece uma solução para o problema em que o usuário não consegue abrir ou expandir uma categoria com subcategorias.
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-44851: Categoria com subcategorias não capazes de abrir ou expandir

O patch ACSD-44851 resolve o problema em que o usuário não consegue abrir ou expandir uma categoria com subcategorias. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 está instalada. A ID do patch é ACSD-44851. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário não pode abrir ou expandir uma categoria com subcategorias.

<u>Etapas a serem reproduzidas</u>:

1. No Administrador do Adobe Commerce, crie uma árvore de categorias com duas categorias raiz e algumas subcategorias para cada uma delas.
1. Abra a visualização/emulador móvel ou reduza a largura da janela até que o layout se torne móvel.
1. Abra o menu principal do catálogo.
1. Tente expandir as categorias raiz.
1. Tente abrir a categoria.

<u>Resultados esperados</u>:

O menu é acessível.

<u>Resultados reais</u>:

O segundo nível do menu móvel não abre.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Ferramentas de correção de qualidade > Uso](/help/tools/quality-patches-tool/usage.md) no guia Ferramenta de correção de qualidade.

* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
