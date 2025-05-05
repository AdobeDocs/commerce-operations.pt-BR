---
title: 'ACSD-62212: email [!UICONTROL Forgot Password] não traduzido para o idioma de exibição do armazenamento'
description: Aplique o patch ACSD-62212 para corrigir o problema do Adobe Commerce em que o conteúdo do email *[!UICONTROL Forgot Password]* não é traduzido para o idioma da exibição de loja.
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
source-git-commit: 8f39f7838d5c98a1dcc584edf766393012ec8820
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62212: email *[!UICONTROL Forgot Password]* não traduzido para o idioma de exibição do armazenamento

O patch ACSD-62212 corrige o problema em que o conteúdo do email *[!UICONTROL Forgot Password]* não é traduzido para o idioma de exibição da loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) 1.1.57 está instalado. A ID do patch é ACSD-62212. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao redefinir a senha por meio do GraphQL em uma visualização de loja diferente da registrada, o link para redefinir senha não corresponde à visualização de loja da qual foi iniciado.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma exibição de repositório secundário sob *[!UICONTROL Main Website Store]*.
1. Alternar *[!UICONTROL Locale]* para *[!UICONTROL French (France)]* no escopo de exibição de repositório secundário.
1. Instale o pacote de idioma em francês para traduções.
1. Crie uma conta de cliente.
1. Use a seguinte mutação do GraphQL com o cabeçalho *store* com o código de exibição de repositório secundário.

   ```
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. Verifique o email.

<u>Resultados esperados</u>:

* O idioma do assunto, do link e do conteúdo do email é consistente com o local de exibição da loja.
* A solicitação de redefinição de senha é enviada da loja onde a conta do cliente está realmente registrada, independentemente do cabeçalho da loja na solicitação.

<u>Resultados reais</u>:

O seguinte pode ser observado no email:

* O link de redefinição de senha tem o código de armazenamento &quot;padrão&quot;.
* O assunto está em inglês.
* O conteúdo está em francês.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
