---
title: 'ACSD-51666: Erro "A sessão expirou, faça logon novamente". depois de fazer logon'
description: Aplique o patch ACSD-51666 para corrigir o problema do Adobe Commerce em que o erro *A sessão expirou, faça logon novamente.* ocorre após tentar fazer logon.
feature: Customers
role: Admin, Developer
exl-id: 8968b314-6625-45fa-9733-20560cca7089
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%
---
# ACSD-51666: Erro *A sessão expirou. Faça logon novamente.* depois de fazer logon

O patch ACSD-51666 corrige o problema em que o erro *A sessão expirou. Faça logon novamente.* ocorre depois que você tenta fazer logon. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.36 está instalado. A ID do patch é ACSD-51666. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Você recebe o erro *A sessão expirou. Faça logon novamente.* ao tentar fazer login com a nova senha de um dispositivo depois de redefinir a senha em outro dispositivo. Isso só acontece se houver uma solicitação adicional do Ajax na página adicionada por um módulo personalizado.

<u>Etapas a serem reproduzidas</u>:

1. Instale um módulo personalizado que adicione uma solicitação de Ajax em cada página da loja.
1. Crie uma nova conta.
1. Faça logoff e volte para a página de logon.
1. Abra o link *Esqueceu a senha* em outro navegador e envie o email *Redefinir senha*.
1. Abra o email de redefinição de senha no primeiro navegador e defina a nova senha.
1. Tente fazer logon no segundo navegador.

<u>Resultados esperados</u>:

Você pode fazer logon com êxito na primeira tentativa.

<u>Resultados reais</u>:

* Você vê que *A sessão expirou. Faça logon novamente.* erro.
* Você não está conectado e não é redirecionado para a página inicial.
* A segunda tentativa de logon foi bem-sucedida.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
