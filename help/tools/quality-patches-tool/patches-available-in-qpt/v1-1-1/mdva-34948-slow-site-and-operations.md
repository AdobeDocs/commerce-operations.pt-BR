---
title: 'MDVA-34948: Lentidão do site'
description: O patch do Adobe Commerce MDVA-34948 corrige o problema de lentidão do site. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1 está instalada. A ID do patch é MDVA-34948. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.1.
feature: Observability, Configuration
role: Admin
exl-id: 3c2a2d44-7d60-42da-a0a3-785fb61d571e
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# MDVA-34948: Lentidão do site


## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce em nossa infraestrutura em nuvem 2.4.0-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce no local e Adobe Commerce em nossa infraestrutura em nuvem 2.3.6-2.3.6-p1, 2.4.0-2.4.0-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O site fica lento, o que dificulta as operações.

<u>Etapas a serem reproduzidas</u>:

1. Executar `show processlist` no MySQL.
1. Verifique se há várias consultas como:

```sql
   SELECT GET_LOCK(SYSTEM_CONFIG', '10');
```

<u>Resultados esperados</u>:

`GET_LOCK` deve ser executado imediatamente.

<u>Resultados reais</u>:

Várias consultas `GET_LOCK` ficam travadas por até 10 segundos cada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR).
