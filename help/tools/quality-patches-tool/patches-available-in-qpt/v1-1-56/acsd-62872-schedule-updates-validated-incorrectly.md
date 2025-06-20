---
title: 'ACSD-62872: atualizações de programação validadas incorretamente'
description: Aplique o patch ACSD-62872 para corrigir o problema do Adobe Commerce com validação de atributo exclusivo, em que as atualizações programadas são validadas incorretamente.
feature: Catalog Management, Admin Workspace
role: Admin, Developer
exl-id: bd0d452b-aae3-4682-8a2c-471a7f8bf132
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# ACSD-62872: atualizações de programação validadas incorretamente

O patch ACSD-62872 corrige o problema com a validação de atributo único em que as atualizações programadas são validadas incorretamente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 está instalado. A ID do patch é ACSD-62872. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch é marcado como obsoleto para as versões 2.4.4 - 2.4.6-p8 na versão 1.1.58 QPT.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A atualização agendada para um atributo personalizado é validada incorretamente.

<u>Etapas a serem reproduzidas</u>:

1. Crie um atributo personalizado para categorias.
1. Navegue até **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Crie uma nova categoria.
1. Na mesma categoria, vá para a seção **[!UICONTROL Scheduled Updates]**.
1. Configure uma nova atualização para esta categoria a qualquer momento futuro.
1. Antes de iniciar a atualização agendada, tente editar a atualização agendada criada para a categoria.

<u>Resultados esperados</u>:

Deve poder atualizar a atualização agendada.

<u>Resultados reais</u>:

Erro: *O valor do atributo &quot;Atributo Personalizado&quot; não é exclusivo. Defina um valor exclusivo e tente novamente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na Infraestrutura em Nuvem: [Atualizações e Patches > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) no guia do Commerce na Infraestrutura em Nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
