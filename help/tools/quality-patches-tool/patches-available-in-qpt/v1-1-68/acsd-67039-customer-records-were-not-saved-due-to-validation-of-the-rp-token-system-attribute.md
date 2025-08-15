---
title: 'ACSD-67039: os registros do cliente não foram salvos devido à validação do atributo do sistema rp_token'
description: Aplique o patch ACSD-67039 para corrigir o problema do Adobe Commerce em que a codificação de diacríticos causa quebras de validação em rp_token.
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 231555e071ebc5edb36182f6b8d4f60acee4f61e
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-67039: os registros do cliente não foram salvos devido à validação do atributo do sistema `rp_token`

O patch ACSD-67039 corrige o problema em que os registros do cliente não eram salvos devido à validação do atributo do sistema `rp_token` e a validação de diacríticos era aplicada somente ao email do cliente resultante. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-67039. Observe que esse problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p9

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A codificação de sinais diacríticos causa falhas de validação em `rp_token`, que é excluído da validação. Os diacríticos são permitidos somente para endereços de email, conforme planejado.

<u>Etapas a serem reproduzidas</u>:

1. Instale a versão 2.4.4 do Adobe Commerce.
1. Crie um cliente.
1. Atualize o Adobe Commerce para a versão 2.4.6 da versão 2.4.4 anterior, em que o cliente já foi criado.
1. Defina a chave de criptografia para `env.php` =
   *d337b914e91ff703b1e94ba4156aadf0*
1. Defina os valores abaixo no banco de dados para qualquer cliente na tabela `customer_entity`:
*`rp_token` = *incr4869*
*`rp_token_created_at` = *2021-04-29 20:06:14*
1. No painel Admin, vá para **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Edite o cliente para o qual você acabou de atualizar os valores acima.
1. Clique em **[!UICONTROL Save Customer]** ou **[!UICONTROL Save and Continue Edit]**.

<u>Resultados esperados</u>:

Os valores do cliente são salvos com sucesso.

<u>Resultados reais</u>:

O registro do cliente não é salvo e o usuário administrador vê a mensagem de erro, *Algo deu errado ao salvar o cliente.*
O `system.log` contém o seguinte erro:

```
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas
