---
title: "ACSD-52148: o logon de administrador do Google v3 reCAPTCHA falha ocasionalmente"
description: Aplique o patch ACSD-52148 para corrigir o problema do Adobe Commerce em que o logon de administrador do Google v3 reCAPTCHA falha ocasionalmente.
feature: Admin Workspace
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-52148: falha ocasional de logon do administrador do Google v3 reCAPTCHA

O patch ACSD-52148 corrige o problema em que o logon do administrador do Google v3 reCAPTCHA falha ocasionalmente. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. A ID do patch é ACSD-52148. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O logon de administrador do Google v3 reCAPTCHA falha ocasionalmente.

<u>Etapas a serem reproduzidas</u>:

1. Ative o Google v3 reCAPTCHA para fazer logon como administrador.
1. Faça logon como Administrador transmitindo o captcha.

<u>Resultados esperados</u>

O administrador está conectado com sucesso.

<u>Resultados reais</u>

* Falha na verificação do *reCAPTCHA.O erro* é exibido ocasionalmente.
* Um erro é registrado em log-

  ```
  report.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []
  ```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
