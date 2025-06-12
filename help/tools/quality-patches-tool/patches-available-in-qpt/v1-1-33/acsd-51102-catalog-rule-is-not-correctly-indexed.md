---
title: 'ACSD-51102: regra de catálogo aplicada a um grande número de produtos não indexados corretamente'
description: Aplique o patch ACSD-51102 para corrigir o problema do Adobe Commerce em que uma regra de catálogo aplicada a um grande número de produtos não é indexada corretamente quando a regra é ativada por uma atualização programada.
feature: Catalog Management, Products
role: Admin
exl-id: 35a8078d-667b-4101-8562-ece052b44c9c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# ACSD-51102: regra de catálogo aplicada a um grande número de produtos não indexados corretamente

O patch ACSD-51102 corrige o problema em que uma regra de catálogo aplicada a um grande número de produtos não é indexada corretamente quando a regra é ativada por uma atualização programada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 está instalado. A ID do patch é ACSD-51102. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma regra de catálogo aplicada a um grande número de produtos não é indexada corretamente quando a regra é habilitada por uma atualização agendada.

Pré-requisitos:

* O trabalho do Cron é configurado e executado a cada minuto.

<u>Etapas a serem reproduzidas</u>:

1. Crie um catálogo grande com milhares de produtos para atingir o tempo de execução dos indexadores de *regra de catálogo* de mais de 120 segundos quando as regras de catálogo estiverem sendo habilitadas.
2. Criar duas regras de catálogo com status *Ativo* definido como *Não*.  Por exemplo, *Teste 1* e *Teste 2*. Cada regra deve afetar todos os produtos no catálogo e fazer com que o indexador seja executado por mais de 120 segundos.
3. Verifique se o status do indexador é *Pronto*.
4. Crie atualizações agendadas para habilitar essas duas regras. A programação do *Teste 2* deve começar logo após *Teste 1*. Por exemplo, com uma diferença de 1 minuto.
5. Verifique os preços do produto na Loja.

<u>Resultados esperados</u>

Descontos de ambas as regras são aplicados.

<u>Resultados reais</u>

Somente o primeiro desconto de regra é aplicado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR>) no guia [!DNL Quality Patches Tool].
