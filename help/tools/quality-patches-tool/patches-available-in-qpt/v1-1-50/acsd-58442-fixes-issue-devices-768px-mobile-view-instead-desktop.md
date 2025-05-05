---
title: 'ACSD-58442: corrige o problema em que dispositivos com largura de 768px são tratados como móveis, fazendo com que o menu e o cabeçalho sejam carregados na exibição móvel, não no desktop'
description: Aplique o patch ACSD-58442 para corrigir o problema do Adobe Commerce em que dispositivos com uma largura de 768px são tratados como móveis, fazendo com que o menu e o cabeçalho sejam carregados em uma visualização móvel em vez de em desktop.
feature: Storefront
role: Admin, Developer
exl-id: 86ea64aa-10fc-4fa3-9902-918fb8983ca0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-58442: corrige o problema em que dispositivos com largura de 768px são tratados como móveis, fazendo com que o menu e o cabeçalho sejam carregados na exibição móvel, não no desktop

O patch ACSD-58442 corrige o problema do Adobe Commerce em que dispositivos com uma largura de 768px são tratados como móveis, fazendo com que o menu e o cabeçalho sejam carregados em uma visualização móvel em vez de em um desktop. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 está instalado. A ID do patch é ACSD-58442. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O sistema agora trata os dispositivos com uma largura de 768 px como desktop, garantindo que o menu e o cabeçalho sejam carregados corretamente. Anteriormente, os dispositivos com uma largura de 768 px eram tratados como móveis, fazendo com que o menu e o cabeçalho fossem carregados em uma visualização móvel.

<u>Etapas a serem reproduzidas</u>:

1. Carregue a página inicial em um iPad Mini ou use a ferramenta de inspeção do navegador para redimensionar o navegador para uma largura de *768px*.
1. Abra o menu principal.

<u>Resultados esperados</u>:

Cargas de menu e cabeçalho como uma visualização de desktop.

<u>Resultados reais</u>:

Cargas de menu e cabeçalho como uma visualização móvel.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
