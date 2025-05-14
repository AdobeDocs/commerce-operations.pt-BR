---
title: 'ACSD-64627: Não é possível salvar atributos personalizados do cliente em [!UICONTROL Company Structure]'
description: Aplique o patch ACSD-64627 para corrigir o problema do Adobe Commerce em que os atributos personalizados do cliente não podem ser salvos ao adicionar ou editar usuários no [!UICONTROL Company Structure].
feature: B2B
role: Admin, Developer
source-git-commit: 96e20dbe336789794462232928648a22f489c88f
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---


# ACSD-64627: Não é possível salvar atributos personalizados do cliente em [!UICONTROL Company Structure]

O patch ACSD-64627 corrige o problema em que os atributos personalizados do cliente não podem ser salvos ao adicionar ou editar usuários na página **[!UICONTROL Company Structure]**. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 está instalado. A ID do patch é ACSD-64627. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3, 2.4.7-p4, 2.4.8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p8, 2.4.7-p3, 2.4.7-p4, 2.4.8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os atributos personalizados do cliente não são salvos ao adicionar ou editar usuários na página **[!UICONTROL Company Structure]**.

<u>Etapas a serem reproduzidas</u>:

1. Instale uma instância do Adobe Commerce com recursos B2B ativados.
1. Crie um novo atributo do cliente chamado *custom_upload* com o **[!UICONTROL Input Type]** definido como *[!UICONTROL File (attachment)]*.
1. Crie outro atributo do cliente chamado *image_attachment* com o **[!UICONTROL Input Type]** definido como *[!UICONTROL Image File]*.
1. Defina **[!UICONTROL Show on Storefront]** como *Sim* para tornar ambos os atributos visíveis na loja. Selecionar todos os formulários:
   * Registro do cliente
   * Editar Conta de Cliente
   * Check-out de administrador
1. Crie e ative uma nova empresa.
1. Faça logon na loja como o administrador da empresa.
1. Navegue até **[!UICONTROL Customer Account]** > **[!UICONTROL Company Structure]** ou **[!UICONTROL Customer Account]** > **[!UICONTROL Company Users]**.
1. Clique em **[!UICONTROL Add New User]**.
1. Clique em **[!UICONTROL Upload]** para o atributo *custom_upload*.
1. Clique em **[!UICONTROL Select file]** para o atributo *image_attachment*.

<u>Resultados esperados</u>:

O explorador de arquivos é aberto para ambos os atributos. Ao salvar, os valores são armazenados e os arquivos são carregados com sucesso.

<u>Resultados reais</u>:

Os botões não respondem. Nenhum explorador de arquivos é aberto ou os dados são salvos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
