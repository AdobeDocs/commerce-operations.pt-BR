---
title: Política de lançamento
description: Saiba mais sobre os diferentes tipos de versões do Adobe Commerce, incluindo versões secundárias, patches, patches de segurança, recursos, hotfixes, patches individuais e patches personalizados.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Política de versão do Adobe Commerce

O Adobe Commerce usa [controle de versão semântico](https://semver.org/) no nível de módulo individual (por exemplo, `magento/framework 101.1.1`), mas não para o número de versão de marketing. Por exemplo:

- **VERSÃO PRINCIPAL**—2
- **VERSÃO SECUNDÁRIA**—2.4
- **Versão do PATCH**—2.4.5
   - **Versão de correção de segurança**—2.4.5-p1
      - Correção de erro de segurança
      - Aprimoramento de segurança
- **versão de patch do BETA**—2.4.7-beta2
- **Versão de Extensibilidade, Infraestrutura e Serviços**
- **Hotfix**
- **Patch individual**
- **Patch personalizado**

## Versão SECUNDÁRIA

As seguintes diretrizes se aplicam a versões secundárias:

- É possível que ocorram alterações importantes; o código escrito para o Adobe Commerce 2.2.x pode não funcionar mais com o Adobe Commerce 2.3.x. Por exemplo, versões secundárias podem apresentar suporte para os principais requisitos e dependências do sistema, como o PHP.
- As versões dos módulos podem variar. Por exemplo, algumas alterações de módulo são introduzidas em um novo patch, enquanto outras são introduzidas em uma versão secundária.
- Versões secundárias podem incluir novos recursos que podem exigir trabalho adicional de você ou de seu parceiro de soluções durante a atualização para garantir a compatibilidade.
- As versões secundárias podem incluir correções para problemas de segurança e qualidade.

## Versão do PATCH

As versões de patches se concentram principalmente no fornecimento de correções de segurança, desempenho, conformidade e qualidade de alta prioridade para ajudar você a manter o desempenho máximo de seus sites.

As seguintes diretrizes se aplicam às versões de patch:

- A versão secundária com suporte mais recente recebe correções e melhorias completas de qualidade funcional.
- São evitadas alterações que poderiam quebrar as extensões ou a compatibilidade de código. Por exemplo, o código escrito para a versão 2.2.0 ainda deve funcionar na versão 2.2.7.
- Excepcionalmente, mudanças intensas ou patches ou hotfixes adicionais podem ser lançados para resolver problemas de segurança ou conformidade e problemas de qualidade de alto impacto. No nível do módulo, essas são, em sua maioria, alterações no nível do PATCH; às vezes, alterações de nível MENOR.

### Versão de correção de SEGURANÇA

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## Versão de correção do Beta

As versões de disponibilidade pré-geral dos recursos do Adobe Commerce são disponibilizadas publicamente para todos os clientes da Adobe Commerce e parceiros da Adobe. Ele permite um tempo extra antes que a Disponibilidade Geral analise o código e os componentes afetados.

As versões do Beta podem conter defeitos e são fornecidas &quot;NO ESTADO EM QUE SE ENCONTRAM&quot; sem garantias de nenhum tipo. A Adobe não terá nenhuma obrigação de manter, corrigir, atualizar, alterar, modificar ou oferecer suporte (por meio dos Serviços de suporte da Adobe ou de outra forma) às versões do Beta. Os clientes são aconselhados a ter cuidado e não depender, de forma alguma, do funcionamento ou do desempenho corretos das versões do Beta e/ou de qualquer documentação ou material que os acompanhe. Portanto, qualquer uso das versões do Beta é totalmente de responsabilidade do Cliente.

## Versão de recursos, infraestrutura em nuvem e extensibilidade

A infraestrutura em nuvem e as versões de recursos contêm novos recursos e atualizações de recursos que são fornecidos como serviços independentes, separados das versões de patch. Os exemplos incluem atualizações em nossos serviços e infraestrutura de hospedagem na nuvem, B2B, produtos SaaS (Serviço de catálogo, Conexão de dados, Recomendações de produtos e Live Search) e tecnologia de extensibilidade (API Mesh, Integration Starter Kit e Eventing).

## Hotfix

Hotfixes são patches que contêm correções de segurança ou qualidade de alto impacto, como correções para vulnerabilidades &quot;zero-day&quot;, que afetam muitos comerciantes. O Adobe lança hotfixes para versões do Adobe Commerce que ainda são compatíveis e afetadas por problemas críticos de segurança ou qualidade, conforme necessário. Hotfixes foram publicados na [seção Problemas conhecidos](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) da nossa Base de Dados de Conhecimento. Essas correções estão incluídas na próxima versão de patch planejada.

>[!NOTE]
>
>Hotfixes podem conter alterações incompatíveis com versões anteriores.

## Patch individual

Patches individuais contêm correções de qualidade de baixo impacto para um problema específico. Essas correções são aplicadas às versões secundárias compatíveis do Adobe Commerce. A Adobe lança patches individuais conforme necessário para o Adobe Commerce de acordo com nossa [Política de ciclo de vida do software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Os patches individuais não contêm alterações incompatíveis com versões anteriores.

## Correção isolada

Contém uma correção independente incluída no patch somente de segurança mais recente ou um patch somente de segurança futuro, que está sendo lançado separadamente para uma implementação mais rápida.

## Correção personalizada

Criado por pessoas que não são da Adobe para corrigir um problema ou modificar o código do Adobe Commerce por vários motivos. Os patches personalizados são entregues por meio da [Ferramenta de Patches de Qualidade](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
