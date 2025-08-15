---
title: 'ACSD-48318: Erro de aninhamento de emulação de ambiente em "system.log"'
description: Aplique o patch ACSD-48318 para corrigir o problema do Adobe Commerce em que uma mensagem de erro *main.ERROR:Environment emulation nested is not allowed* aparece em &grave;system.log&grave; toda vez que um email de fatura é enviado.
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# ACSD-48318: Erro de aninhamento de emulação de ambiente em `system.log`

O patch ACSD-48318 corrige o problema em que uma mensagem de erro *main.ERROR:Environment de aninhamento de emulação não é permitida* aparece em `system.log` toda vez que um email de fatura é enviado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 está instalado. A ID do patch é ACSD-48318. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A mensagem de erro *Aninhamento de emulação de ambiente não permitido* aparece em `system.log` toda vez que um email de fatura é enviado.

<u>Etapas a serem reproduzidas</u>:

1. Fazer um pedido e gerar uma fatura.
1. Abra a fatura do Administrador e clique em **[!UICONTROL Send Email]**.
1. Siga a mesma etapa para *memorando de crédito* e *remessa* clicando em **[!UICONTROL Send Email]**.

<u>Resultados esperados</u>:

Nenhum erro em `system.log`.

<u>Resultados reais</u>:

`system.log` está inundado com *main.ERROR: Erro* não permitido aninhamento de emulação de ambiente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
