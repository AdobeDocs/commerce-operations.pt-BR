---
title: 'ACSD-53998: Bloco dinâmico baseado em segmento de cliente funciona incorretamente após o logout'
description: Aplique o patch ACSD-53998 para corrigir o problema do Adobe Commerce em que um bloco dinâmico baseado em um segmento de cliente não funciona corretamente depois de fazer logout de uma conta de cliente.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
exl-id: aa7001c7-bb35-4e5c-8ac9-3ed84b75d7cd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-53998: Bloco dinâmico baseado em segmento de cliente funciona incorretamente após o logout

O patch ACSD-53998 corrige o problema em que um bloco dinâmico baseado em um segmento de cliente não funciona corretamente depois de fazer logout de uma conta de cliente. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.39 está instalado. A ID do patch é ACSD-53998. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um bloco dinâmico baseado em um segmento de cliente não funciona corretamente depois de fazer logout de uma conta de cliente.

<u>Pré-requisitos</u>:

Instalar e habilitar [!DNL Page Builder] módulos.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois segmentos de clientes sem nenhuma condição.
1. Crie dois blocos dinâmicos para cada segmento.
1. Crie um bloco incluindo os dois blocos dinâmicos como [!DNL Page Builder] blocos dinâmicos.
1. Crie um widget incluindo o bloco acima e torne o bloco visível na seção de rodapé de todas as páginas.
1. Limpe os caches.
1. Abra a home page.
1. Faça logon como cliente.
1. Faça logout.

<u>Resultados esperados</u>:

O banner criado para clientes conectados não é exibido para usuários convidados.

<u>Resultados reais</u>:

O banner criado para o segmento de cliente conectado é exibido mesmo depois de fazer logout da conta do cliente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
