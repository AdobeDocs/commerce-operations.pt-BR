---
title: 'ACSD-65983: erro ao reconfigurar a cotação de produto agrupada no Admin'
description: Aplique o patch ACSD-65983 para corrigir o problema do Adobe Commerce em que um erro aparece ao tentar configurar um produto em pacote na tela [!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit] no back-end.
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a8f2b273bcbcf135677ad7ca289398bf660e02e
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# ACSD-65983: erro ao reconfigurar a cotação de produto agrupada no Admin

O patch ACSD-65983 corrige o problema em que a reconfiguração de uma cotação de produto agrupada no back-end do administrador retorna um erro. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-65983. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A reconfiguração de uma cotação de produto agrupada no back-end do administrador retorna um erro.

<u>Etapas a serem reproduzidas</u>:

1. Vá para o painel Admin e habilite o **[!UICONTROL B2B Feature]**: **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Feature]**.
1. Crie um produto agrupado com valor fixo (Por exemplo: *$10*) e adicione três ou mais produtos simples com valor *0*, *2* na **Opção 1** e *outros* na **Opção 2**.
1. Crie uma conta da empresa no front-end.
1. Vá para **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**, atribua a empresa e os produtos criados ao catálogo compartilhado novo/personalizado.
1. Faça logon como um **Usuário da empresa** no front-end e adicione um produto simples ao carrinho do pacote.
1. Abra a página do carrinho e envie como uma **Solicitar uma Cotação**.
1. Ir para o back-end e editar a cotação criada.
1. Na seção **Item de Cotação**, clique no botão **Configurar**.
1. Selecione outro produto simples da **Opção 2**.
1. Agora clique no botão **OK** e veja a mensagem de erro.

<u>Resultados esperados</u>:

Você pode configurar com êxito os itens de cotação solicitados do Administrador normalmente, sem nenhuma mensagem de erro exibida.

<u>Resultados reais</u>:

Você verá a mensagem de erro:

*Um problema técnico com o servidor criou um erro. Tente novamente para continuar o que estava fazendo. Se o problema persistir, tente novamente mais tarde.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas
