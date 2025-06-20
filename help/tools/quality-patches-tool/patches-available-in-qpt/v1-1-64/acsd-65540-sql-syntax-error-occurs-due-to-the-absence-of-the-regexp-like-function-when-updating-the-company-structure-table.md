---
title: 'ACSD-65540: Ocorre um erro SQL devido à falta da função REGEXP_LIKE nas atualizações de company_structure'
description: Aplique o patch ACSD-65540 para corrigir o problema do Adobe Commerce em que ocorre erro de SQL devido à falta da função REGEXP_LIKE em atualizações de company_structure.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: a3e60742-60d4-41e3-93c3-506cc5a1c4a3
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# ACSD-65540: Ocorre um erro SQL devido à ausência da função `REGEXP_LIKE` em `company_structure` atualizações

O patch ACSD-65540 corrige o problema em que ocorre um erro de SQL devido à falta da função `REGEXP_LIKE` nas atualizações `company_structure`. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 está instalado. A ID do patch é ACSD-65540.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce B2B (todos os métodos de implantação) 1.5.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce B2B (todos os métodos de implantação) 1.5.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erro de sintaxe SQL devido à ausência da função `REGEXP_LIKE` em `company_structure` atualizações.

<u>Etapas a serem reproduzidas</u>:

1. Atualize [!DNL B2B] para a versão 1.5.2.
1. Execute o seguinte comando:

```
bin/magento setup:upgrade
```

<u>Resultados esperados</u>:

Atualização concluída com sucesso.

<u>Resultados reais</u>:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
