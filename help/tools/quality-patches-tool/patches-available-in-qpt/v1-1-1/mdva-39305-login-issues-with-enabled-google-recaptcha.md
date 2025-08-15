---
title: 'MDVA-39305: problema de logon com o Google reCAPTCHA ativado'
description: Aplique o patch MDVA-39305 para corrigir o problema do Adobe Commerce em que os clientes registrados não conseguem fazer logon quando o Google reCAPTCHA está ativado.
feature: Console
role: Admin
exl-id: c40fd84a-73dc-42bd-8cda-58738615fbba
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-39305: problema de logon com o Google reCAPTCHA ativado

>[!NOTE]
>
>Este patch foi atualizado e a ID do patch mais recente é MDVA-39305-V3. O novo patch é criado para as versões 2.4.4, 2.4.5-p2 e 2.4.7 do Adobe Commerce. Para obter mais informações, consulte o artigo de patch [MDVA-39305-V3](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/mdva-39305-v3-login-issue-with-enabled-google-recaptcha).

O patch MDVA-39305 corrige o problema em que clientes registrados não conseguem fazer logon quando o Google reCAPTCHA está ativado. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1 está instalado. A ID do patch é MDVA-39305. Observe que o problema foi corrigido nas versões 2.4.4 e 2.4.7 do Adobe Commerce.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os clientes registrados não conseguem fazer logon usando o Google reCAPTCHA ativado.

<u>Etapas a serem reproduzidas</u>:

1. Acesse **Loja** > **Configuração** > **Segurança** > **Loja Google reCAPTCHA** e habilite o **Google reCAPTCHA**.
1. Ir para **Front-end**.
1. Abra o **Console da Ferramenta do Desenvolvedor** no navegador.

<u>Resultados esperados</u>:

Nenhum aviso de CSP no console.

<u>Resultados reais</u>:

Avisos de CSP no console.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
