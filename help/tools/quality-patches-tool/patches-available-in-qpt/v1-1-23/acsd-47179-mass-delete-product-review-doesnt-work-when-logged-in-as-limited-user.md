---
title: 'ACSD-47179: a exclusão em massa de análises de produtos não funciona quando conectado como função de usuário limitada'
description: Aplique o patch ACSD-47179 para corrigir o problema do Adobe Commerce em que a exclusão em massa de análises de produtos não funciona quando conectado como uma função de usuário limitada.
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
exl-id: 7131ee47-fadc-4e93-b8b2-5b2e0521ad97
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-47179: a exclusão em massa de análises de produtos não funciona quando conectado como uma função de usuário limitada

O patch ACSD-47179 corrige o problema em que a exclusão em massa de análises de produtos não funciona quando conectado como uma função de usuário limitada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 está instalado. A ID do patch é ACSD-47179. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A exclusão em massa de análises de produtos não funciona quando conectado como uma função de usuário limitada.

<u>Etapas a serem reproduzidas</u>:

1. Criar um site secundário.
1. Crie uma função de usuário restrita ao site secundário com permissão total para as seguintes seções:
   * Catálogo
   * Cliente
   * Marketing
1. Crie um produto e atribua-o ao site secundário.
1. Adicione duas análises ao produto a partir do front-end.
1. Faça logon no Administrador [!DNL Commerce] usando o usuário administrador restrito recém-criado.
1. Tente excluir em massa as revisões pendentes.

<u>Resultados esperados</u>:

Um administrador com permissões suficientes pode excluir em massa as revisões pendentes.

<u>Resultados reais</u>:

Você recebe o seguinte erro: _Algo deu errado. Exceção gerada em support_report.log_

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
