---
title: 'AC-14985: erro ao enviar emails SMTP usando TLS'
description: Aplique o patch AC-14985 para corrigir o problema do Adobe Commerce em que ocorre um erro ao enviar email do Simple Mail Transfer Protocol (SMTP) usando o Transport Layer Security (TLS).
feature: Configuration
role: Admin, Developer
type: Troubleshooting
exl-id: 98d91421-ebfd-4414-ade3-f25d29541874
source-git-commit: 515e6d1f00c910455a2ffddf70c4a450184e7e81
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# AC-14985: erro ao enviar emails SMTP usando TLS

O patch AC-14985 corrige um problema em que ocorre um erro ao enviar email do Simple Mail Transfer Protocol (SMTP) usando o Transport Layer Security (TLS). Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 está instalado. A ID do patch é AC-14985. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ocorre um erro ao enviar email via SMTP com TLS ativado.

<u>Etapas a serem reproduzidas</u>:

1. Defina a configuração SMTP da seguinte maneira:
* Transporte: SMTP
* Host: url.to.smtp.host
* Porta: 587
* SSL: TLS

<u>Resultados esperados</u>:

O email é enviado com sucesso sem erros.

<u>Resultados reais</u>:

O seguinte erro é exibido:

```
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
