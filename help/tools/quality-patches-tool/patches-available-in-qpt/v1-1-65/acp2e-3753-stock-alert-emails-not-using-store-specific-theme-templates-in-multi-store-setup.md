---
title: 'ACP2E-3753: Emails de alerta de estoque que não usam modelos de tema específicos da loja na configuração de várias lojas'
description: Aplique o patch do ACP2E-3753 para corrigir o problema do Adobe Commerce em que os emails de alerta do produto em uma configuração de várias lojas são sempre enviados usando o tema padrão, independentemente da configuração de loja ou tema.
feature: Themes, Personalization
role: Admin, Developer
exl-id: ad44ffdd-f122-4119-83e3-1816951b662c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8b440f30-6794-5ed6-981f-391de4e9b0cc
    internal-label: Themes
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
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
source-wordcount: '406'
ht-degree: 0%
---
# ACP2E-3753: Emails de alerta de estoque que não usam modelos de tema específicos da loja na configuração de várias lojas

O patch do ACP2E-3753 corrige o problema em que os emails de alerta do produto em uma configuração de várias lojas eram sempre enviados usando o tema padrão, independentemente da configuração de loja ou tema. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 está instalado. A ID do patch é ACP2E-3753. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p11

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Emails de alerta de produto em uma configuração de várias lojas são sempre enviados usando o tema padrão, independentemente da configuração da loja ou do tema.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois sites, lojas e visualizações de loja.
1. Crie dois temas separados e atribua-os a lojas diferentes.
1. A configuração de alerta de produto é o escopo padrão executado a cada minuto.
1. Substituir/adicionar conteúdo ao arquivo `stock.phtml` para ambos os temas. Exemplo da localização do arquivo:

   ```text
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. Crie um usuário para cada loja e assine o alerta de estoque de produtos.
1. Acione o alerta de estoque de produtos para enviar os emails.

<u>Resultados esperados</u>:

O email deve incluir as alterações no nível do tema.

<u>Resultados reais</u>:

Os emails não incluem os modelos definidos nos respectivos sites/lojas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
