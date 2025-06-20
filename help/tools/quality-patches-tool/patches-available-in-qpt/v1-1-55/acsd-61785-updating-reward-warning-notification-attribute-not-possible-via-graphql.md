---
title: 'ACSD-61785: Não é possível atualizar o atributo reforço_warning_notification por meio de mutação do GraphQL e chamadas de API REST'
description: Aplique o patch ACSD-61785 para corrigir o problema do Adobe Commerce em que a atualização do atributo "recompensa_aviso_notificação" não é possível por meio de mutação do GraphQL e chamadas de API REST.
feature: REST, GraphQL, Rewards
role: Admin, Developer
exl-id: 41f40452-4240-4b4a-b1bc-0da23139f19f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785: Não é possível atualizar o atributo reforço_warning_notification por meio de mutação do GraphQL e chamadas de API REST

O patch ACSD-61785 corrige o problema em que a atualização do atributo `reward_warning_notification` não é possível por meio de mutação do GraphQL e chamadas de API REST. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 está instalado. A ID do patch é ACSD-61785. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Não é possível atualizar o atributo `reward_warning_notification` por meio de mutação do GraphQL e chamadas de API REST.

<u>Etapas a serem reproduzidas</u>:

1. Verifique o esquema/documentação da API REST e GraphQL para *Assinar atualizações de saldo* e *Assinar notificações de expiração de pontos*.

<u>Resultados esperados</u>:

É possível assinar *Atualizações de Saldo de Prêmios* e *Notificações de Expiração de Pontos* via GraphQL e REST API.

<u>Resultados reais</u>:

O GraphQL e a REST API não têm essa funcionalidade.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
