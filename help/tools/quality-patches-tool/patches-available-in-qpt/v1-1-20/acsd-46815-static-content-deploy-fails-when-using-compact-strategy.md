---
title: 'ACSD-46815: falha na implantação de conteúdo estático usando estratégia compacta'
description: Aplique o patch ACSD-46815 para corrigir o problema do Adobe Commerce em que a implantação de conteúdo estático falha ao usar uma estratégia compacta.
feature: Deploy, Page Content, SCD
role: Admin
exl-id: 66941a83-daf8-4bb2-a575-b615e1c5dc7c
source-git-commit: 94fba368c799f4584e27331e852c0f8abeeabbd6
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-46815: falha na implantação de conteúdo estático ao usar uma estratégia compacta

O patch ACSD-46815 corrige o problema em que a implantação de conteúdo estático falha quando a estratégia compacta é usada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20 está instalado. A ID do patch é ACSD-46815. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A implantação de conteúdo estático falha ao implantar com uma estratégia compacta.

<u>Etapas a serem reproduzidas</u>:

1. Implante o conteúdo estático com uma estratégia compacta executando o seguinte comando:

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>Resultados esperados</u>:

A implantação do conteúdo estático foi concluída sem erros.

<u>Resultados reais</u>:

A implantação de conteúdo estático falha com uma estratégia compacta. O seguinte erro ocorre durante o processo de implantação: *O conteúdo de /app/pub/static/adminhtml/Magento/base/default/.O arquivo /node_modules/@spectrum-css/vars/dist/spectrum-global.css não pode ser lido.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
