---
title: 'ACSD-52133: A conta do cliente não pode ser salva após uma atualização'
description: Aplique o patch ACSD-52133 para corrigir o problema do Adobe Commerce em que uma conta de cliente não pode ser salva após uma atualização.
feature: Customers, Upgrade
role: Admin
exl-id: 4a0e6ed8-3e35-40ce-bb49-8ccfcde437a0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-52133: A conta do cliente não pode ser salva após uma atualização

O patch ACSD-52133 corrige o problema em que uma conta de cliente não pode ser salva após uma atualização. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. A ID do patch é ACSD-52133. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A conta do cliente não pode ser salva após uma atualização.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce versão 2.4.4.
1. Crie um cliente.
1. Atualize o Adobe Commerce para 2.4.6 a partir da versão anterior da 2.4.4, na qual um cliente já foi criado.
1. Defina a chave de criptografia conforme abaixo em `env.php`:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Defina os valores abaixo no banco de dados para qualquer cliente na tabela `customer_entity`:

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Vá para **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Edite o cliente para o qual os valores acima foram atualizados.
1. Clique em **[!UICONTROL Save Customer]** ou **[!UICONTROL Save and Continue Edit]**

<u>Resultados esperados</u>:

O cliente foi salvo com sucesso sem erros.

<u>Resultados reais</u>:

* O registro do cliente não foi salvo.
* O administrador vê a seguinte mensagem de erro: *Algo deu errado ao salvar o cliente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool]
* [Práticas recomendadas para modificar tabelas de banco de dados](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
