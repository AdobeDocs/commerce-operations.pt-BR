---
title: Política de lançamento
description: Saiba mais sobre os diferentes tipos de versões do Adobe Commerce, incluindo menor importância, patch, patch de segurança, recurso, hotfix, patch individual e patch personalizado.
source-git-commit: f9bbfb86d2197ee7252602edba455ebcae5a2b18
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---


# Política de versão do Adobe Commerce

Adobe Commerce e Magento Open Source use [controle de versão semântico](https://semver.org/) no nível do módulo individual (por exemplo, `magento/framework 101.1.1`), mas não para o número da versão de marketing. Por exemplo:

- **Versão IMPORTANTE**—2
- **Versão MENOR**—2.4
- **Versão do PATCH**—2.4.1
   - **Versão de patch de SEGURANÇA**—2.4.1-p1
      - Correção de erro de segurança
      - Aprimoramento de segurança
- **Versão de recurso**
- **Hotfix**
- **Patch individual**
- **Patch personalizado**

## Versão MENOR

As seguintes diretrizes se aplicam a versões secundárias:

- É possível alterar a quebra; o código gravado para Adobe Commerce 2.2.x pode não funcionar mais com o Adobe Commerce 2.3.x. Por exemplo, versões secundárias podem introduzir suporte para os principais requisitos e dependências do sistema, como o PHP.
- As versões dos módulos podem variar. Por exemplo, algumas alterações de módulo são introduzidas em um novo patch, enquanto outras são introduzidas em uma versão secundária.
- As versões secundárias podem incluir novos recursos que podem exigir trabalho adicional de você ou de seu parceiro de solução durante a atualização para garantir a compatibilidade.
- Versões secundárias podem incluir correções para problemas de segurança e qualidade.

## Versão do PATCH

As versões de patches têm como foco principal o fornecimento de segurança, desempenho, conformidade e correções de qualidade de alta prioridade para ajudar você a manter o desempenho de seus sites no auge.

As seguintes diretrizes se aplicam às versões de patch:

- A versão secundária compatível mais recente recebe correções e aprimoramentos de qualidade funcional completos.
- As alterações que podem quebrar extensões ou a compatibilidade do código são evitadas. Por exemplo, o código gravado para a versão 2.2.0 ainda deve funcionar na versão 2.2.7.
- Excepcionalmente, podem ser lançadas alterações ou patches ou hotfixes adicionais para solucionar problemas de segurança ou conformidade e problemas de qualidade de alto impacto. No nível do módulo, trata-se principalmente de alterações no nível do PATCH; às vezes, alterações de nível MINOR.

## Versão de patch de SEGURANÇA

**Correção de erros de segurança**: Uma alteração de código de software que resolve um problema de segurança identificado e fornece os resultados esperados em uma área de produto afetada. Essas correções geralmente são compatíveis com versões anteriores.

**Aprimoramento de segurança**: Uma melhoria ou alteração na configuração do software para melhorar proativamente a segurança no aplicativo. Esses aprimoramentos de segurança ajudam a lidar com riscos de segurança que afetam a postura de segurança do aplicativo Adobe Commerce, mas podem ser incompatíveis com versões anteriores.

Com as versões de patches de segurança, você pode manter seu site mais seguro sem aplicar correções de qualidade adicionais e aprimoramentos contidos em uma versão de patch trimestral completa. As versões de patch de segurança são anexadas com &#39;-pN&#39;, onde N é a versão de patch incremental que começa com 1 (por exemplo, 2.3.5-p1). As versões de patch de segurança também podem incluir hotfixes necessários para solucionar problemas críticos que afetam o aplicativo Adobe Commerce.

Cada liberação de patch de segurança é baseada na liberação de patch completa anterior. Ele contém correções de qualidade e segurança da versão de patch anterior e correções de segurança criadas entre a versão de patch completa anterior e a versão de patch de segurança.

Com o anúncio da nossa [nova estratégia de lançamento e política de ciclo de vida atualizada](https://business.adobe.com/blog/how-to/accelerating-innovation-through-simplified-release-strategy) (16/9/2021), nossas versões de patch de segurança são diferenciadas com base em se elas são aplicáveis à versão secundária compatível mais recente ou a uma parte de uma linha de versão secundária ainda suportada:

- **Versões de patch de segurança para a versão secundária mais recente suportada**:

   - A versão de patch de segurança para a versão secundária compatível mais recente (atualmente Adobe Commerce 2.4) inclui:

      - Correções de erros de segurança criadas desde a versão anterior de patch completo.

      - Essas versões de patch de segurança também podem incluir hotfixes necessários para solucionar problemas críticos que podem afetar o aplicativo Adobe Commerce.
   - A versão de patch de segurança para a versão secundária compatível mais recente (atualmente Adobe Commerce 2.4) normalmente não inclui aprimoramentos de segurança. Em vez disso, elas são incluídas na versão completa de patch para a versão secundária mais recente suportada.


- **Versões de patch de segurança para versões secundárias anteriores suportadas**:

   - A versão de correção de segurança de uma versão secundária anterior que ainda é suportada (atualmente Adobe Commerce 2.3) inclui:

      - Correções de erros de segurança criadas desde o patch ou a versão de patch de segurança anterior e novos aprimoramentos de segurança.

      - Essas versões de patch de segurança também podem incluir hotfixes necessários para solucionar problemas críticos que afetam o aplicativo Adobe Commerce.

      |  | Bug de segurança | Aprimoramento de segurança |
      |--------------------------------------------------------------------------------|--------------|----------------------|
      | Versões de patch de segurança para a versão secundária compatível mais recente (atualmente 2.4) | X |  |
      | Versões de patch de segurança para versões secundárias anteriores e compatíveis (atualmente 2.3) | X | X |


Para obter informações gerais sobre versões de segurança, consulte [Introdução à nova versão do patch de segurança somente](https://community.magento.com:443/t5/Magento-DevBlog/Introducing-the-New-Security-Patch-Release/ba-p/141287). Para obter instruções sobre como baixar e aplicar patches de segurança, consulte [Instalação do início rápido](../installation/composer.md).

## Versão de recurso

As versões de recursos contêm novos recursos e atualizações de recursos que são fornecidos como serviços independentes, separados das versões de patches. Os exemplos incluem serviços como o Product Recommendations e o Live Search, módulos independentes como o PWA Studio e o Inventory management (MSI) e atualizações de nossos serviços e infraestrutura em nuvem.

## Hotfix

Hotfixes são patches que contêm correções de alta segurança ou qualidade, como correções para vulnerabilidades de zero dias, que afetam muitos comerciantes. O Adobe lança hotfixes para versões Adobe Commerce que ainda são suportadas e afetadas por problemas críticos de segurança ou qualidade, conforme necessário. Os hotfixes são publicados no [Seção Problemas conhecidos](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) da nossa Base de Conhecimento. Essas correções estão incluídas na próxima versão de patch planejada.

>[!NOTE]
>
>Os hotfixes podem conter alterações incompatíveis com o passado.

## Patch individual

Os patches individuais contêm correções de qualidade de baixo impacto para um problema específico. Essas correções são aplicadas às versões secundárias compatíveis com o Adobe Commerce. O Adobe lança patches individuais conforme necessário para o Adobe Commerce de acordo com nossa [Política de ciclo de vida do software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Os patches individuais não contêm alterações incompatíveis com o passado.

## Patch personalizado

Criado por não Adobe pessoal para corrigir um problema ou modificar o código Adobe Commerce por vários motivos. Os patches personalizados são entregues por meio do [Ferramenta Correções de Qualidade](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Tópicos relacionados

- [Planejamento e Orçamento para Ciclos de Atualização do Commerce](https://magento.com/sites/default/files8/2019-08/Magento-Release-Cycle-Infosheet_Aug_2019.pdf)
- [Controle de versão](https://developer.adobe.com/commerce/php/development/versioning/)
- [Próximas versões](schedule.md)
- [Política de ciclo de vida do software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
