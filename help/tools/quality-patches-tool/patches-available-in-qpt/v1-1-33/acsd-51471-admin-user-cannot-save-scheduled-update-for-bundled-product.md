---
title: 'ACSD-51471: o usuário administrador não pode salvar a atualização programada para o produto agrupado'
description: Aplique o patch ACSD-51471 para corrigir o problema do Adobe Commerce em que um usuário administrador não pode salvar uma atualização agendada para um produto empacotado que usa um produto simples com uma atualização agendada.
exl-id: d8134111-63f0-4476-a407-677bda52fa90
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-51471: o usuário administrador não pode salvar a atualização programada para o produto agrupado

O patch ACSD-51471 corrige o problema em que um usuário administrador não pode salvar uma atualização agendada para um produto empacotado que usa um produto simples com uma atualização agendada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 está instalado. A ID do patch é ACSD-51471. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários administradores não podem salvar uma atualização agendada para um produto empacotado que usa um produto simples que tem uma atualização agendada.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples.
1. Adicione uma atualização agendada para o produto simples com apenas *Data de Início* e sem *Data de Término*.
1. Após a atualização ser aplicada, altere o SKU do produto.
1. Crie um produto empacotado e adicione o produto simples criado na Etapa 1 como um produto secundário.
1. Crie uma atualização agendada para o produto agrupado para habilitar o produto agrupado. Forneça a *Data de Início* e a *Data de Término* para a atualização agendada.
1. Salve a atualização programada.

<u>Resultados esperados</u>:

A atualização agendada foi salva com sucesso.

<u>Resultados reais</u>:

O seguinte erro ocorre ao salvar a atualização agendada: *O produto solicitado não existe. Verifique o produto e tente novamente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
