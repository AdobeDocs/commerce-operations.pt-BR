---
title: 'MDVA-40311: Erro "Chave de formulário ou segurança inválida" após fazer logon no Administrador se o caminho de administrador personalizado estiver configurado'
description: 'O patch MDVA-40311 corrige o problema em que o usuário administrador recebe uma mensagem de erro: *Chave de segurança ou formulário inválida. Atualize a página* após fazer logon no Administrador se o caminho de administração personalizado estiver configurado e a chave secreta estiver ativada. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 está instalada. A ID do patch é MDVA-40311. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.'
feature: Admin Workspace, Compliance, Security
role: Admin
exl-id: dce4914b-e32e-4af0-be24-e55680191fa3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-40311: Erro &quot;Chave de formulário ou segurança inválida&quot; após fazer logon no Administrador se o caminho de administrador personalizado estiver configurado

O patch MDVA-40311 corrige o problema em que o usuário administrador recebe uma mensagem de erro: *Chave de formulário ou segurança inválida. Atualize a página* após fazer logon no Administrador se o caminho de administração personalizado estiver configurado e a chave secreta estiver habilitada. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 está instalada. A ID do patch é MDVA-40311. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador recebe uma mensagem de erro: *Chave de formulário ou segurança inválida. Atualize a página* após fazer logon no Administrador se o caminho de administração personalizado estiver configurado e a chave secreta estiver habilitada.

<u>Etapas a serem reproduzidas</u>:

* Efetue login como o usuário Administrador usando um nome de usuário e senha válidos.

<u>Resultados esperados</u>:

O usuário pode fazer logon sem nenhuma mensagem de erro.

<u>Resultados reais</u>:

*Chave de formulário ou segurança inválida. A mensagem de erro da página* é exibida.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
