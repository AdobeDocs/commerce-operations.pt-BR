---
title: 'ACSD-56226: consultas READ retornam dados desatualizados com "synchronous_replication" ativado'
description: Aplique o patch ACSD-56226 para corrigir o problema do Adobe Commerce em que as consultas de LEITURA retornam dados desatualizados quando o sinalizador "synchronous_replication" está ativado para conexão escrava na nuvem.
feature: System
role: Admin, Developer
type: Troubleshooting
exl-id: 5ad0e884-decb-4e09-b5b3-b38a9953a4b8
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
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
source-wordcount: '355'
ht-degree: 0%
---
# ACSD-56226: consultas READ retornam dados desatualizados com `synchronous_replication` ativado

O patch ACSD-56226 corrige o problema em que as consultas READ retornam dados desatualizados quando o sinalizador `synchronous_replication` está habilitado para conexão subordinada na Nuvem. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-56226. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

AS consultas READ retornam dados desatualizados quando o sinalizador `synchronous_replication` está habilitado. Isso faz com que a conexão subordinada seja desabilitada, resultando em sobrecarga do banco de dados.

<u>Etapas a serem reproduzidas</u>:

1. Defina `MYSQL_USE_SLAVE_CONNECTION` como *true* nas variáveis de ambiente do Adobe Commerce na infraestrutura de nuvem.
1. Adicionar a seguinte configuração a `.magento.env.yaml` para definir `synchronous_replication` como *false*:

   ```text
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. Reimplante e execute ações de front-end, como fazer logon, adicionar ao carrinho ou fazer um pedido.

<u>Resultados esperados</u>:

A conexão subordinada permanece habilitada quando `synchronous_replication` é definido como *false*.

<u>Resultados reais</u>:

A conexão subordinada está desabilitada quando `synchronous_replication` está definido como *false*, causando sobrecarga no banco de dados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
