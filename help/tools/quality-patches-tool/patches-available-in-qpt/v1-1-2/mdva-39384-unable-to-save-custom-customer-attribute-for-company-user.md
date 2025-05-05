---
title: 'MDVA-39384: Não é possível salvar atributo de cliente personalizado para usuário da empresa'
description: O patch MDVA-39384 resolve o problema em que o atributo de cliente personalizado de um usuário da empresa não é salvo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 está instalada. A ID do patch é MDVA-39384. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: Attributes, B2B, Companies
role: Developer
exl-id: 0ccaa4c5-ca43-4b25-963b-b9a547ecc71f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-39384: Não é possível salvar atributo de cliente personalizado para usuário da empresa

O patch MDVA-39384 resolve o problema em que o atributo de cliente personalizado de um usuário da empresa não é salvo. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 está instalada. A ID do patch é MDVA-39384. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O atributo personalizado do cliente para um usuário da empresa não é salvo.

<u>Pré-requisitos</u>:

Os módulos B2B são instalados.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Lojas** > Configurações > **Configuração** > **Recursos B2B** e defina a **Habilitar Empresa** como Sim.
1. Criar um atributo de cliente personalizado:
   * Valores Obrigatórios: Sim (opcional, ative-o para que o erro de validação seja exibido).
   * Mostrar na Loja: Sim.
   * Forms para uso no: todos disponíveis na lista.
1. Crie uma Empresa e faça logon como administrador da empresa.
1. Navegue até Estrutura da empresa na sua conta.
1. Clique no link **Adicionar Usuário**.
1. Preencha o formulário, incluindo o atributo personalizado.
1. Clique em **Salvar**.

<u>Resultados esperados</u>:

Os valores de atributo personalizados são salvos com o novo usuário da empresa.

<u>Resultados reais</u>:

Os valores de atributos personalizados NÃO são salvos com o novo usuário da empresa.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
