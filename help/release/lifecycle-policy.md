---
title: Política de ciclo de vida do software
description: Saiba mais sobre as principais datas relacionadas ao fim do suporte de software das versões do Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
nudge: true
source-git-commit: 5846c83cd31e3d253a5ae0b0064b860e5c7af286
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 1%

---


# política de ciclo de vida do Adobe Commerce

Para simplificar a política de ciclo de vida do Adobe Commerce e atender às necessidades críticas dos clientes, a Adobe oferece uma janela de suporte padrão de três anos a partir da data de disponibilidade geral (GA) para cada versão e lança correções de qualidade durante esse período. Para obter datas e detalhes sobre o fim do suporte de software para cada versão, consulte a tabela [Fim do suporte de software](#end-of-software-support).

A Adobe não fornece correções de segurança e qualidade para serviços e dependências de software de terceiros (como PHP e MySQL) que podem chegar ao fim da vida útil enquanto os clientes estão no período de suporte estendido ou de três anos para o Adobe Commerce. Consulte os [requisitos do sistema](../installation/system-requirements.md) para obter uma lista completa de tecnologias de terceiros testadas e com suporte.

## Suporte Standard

O período de suporte padrão de três anos a partir da data de disponibilidade geral (GA). O suporte Standard inclui correções de qualidade, patches de segurança e suporte completo do Adobe Commerce on-call.

- **Correções de qualidade** - Os clientes podem acessar correções de qualidade entrando em contato com o [Suporte da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) ou por meio do autoatendimento [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR).

- **Correções de segurança** - A Adobe fornece correções de segurança por meio de patches de segurança cumulativos e [arquivos de patch de segurança isolados](versioning-policy.md#isolated-security-patch-file) não cumulativos para o período de suporte de três anos.

- **Hotfixes** - Para problemas críticos de segurança, como vulnerabilidades inexistentes, a Adobe fornece [hotfixes](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) para todos os clientes em uma versão com suporte, mesmo que eles não estejam na versão mais recente de patch ou patch de segurança. Observe que um hotfix não é abrangente e não trata de todos os problemas de segurança que seriam resolvidos com a atualização para a versão mais recente.

## Suporte estendido

A Adobe incentiva os clientes a atualizarem o mais rápido possível. No entanto, para fornecer maior flexibilidade para se alinhar aos planos de atualização e às necessidades de negócios, a Adobe oferece um ano de suporte adicional sem custo adicional para clientes Adobe Commerce nas versões 2.4.6 e 2.4.7. A extensão de suporte inclui patches de qualidade e segurança para o aplicativo principal. O suporte estendido para as versões 2.4.4 e 2.4.5 do Adobe Commerce termina em abril e agosto de 2026, conforme planejado.

>[!NOTE]
>
>O Adobe está introduzindo uma política de atualização de versão imposta para o Adobe Commerce na nuvem. A partir de **1 de junho de 2027**, o Adobe não manterá mais ambientes na nuvem executando versões não compatíveis do Commerce e se reserva o direito de desativá-los. Se você estiver executando na Nuvem, será necessário migrar para uma versão do Adobe Commerce com suporte ou migrar para a [!DNL Adobe Commerce as a Cloud Service] antes da data publicada de [fim do suporte estendido](lifecycle-policy.md#end-of-support-dates) para a sua linha de lançamento. Consulte a [Política de imposição de atualização de versão da nuvem](version-upgrade-enforcement-policy.md) para obter datas de imposição, versões afetadas e o que acontece se você permanecer em uma versão sem suporte.

## Período de transição apenas para efeitos de segurança

Um período de transição único e limitado no tempo disponível apenas para as versões 2.4.4, 2.4.5 e 2.4.6, cujo suporte estendido terminou em 2025 ou 2026. O período de transição somente para segurança fornece apenas correções de segurança isoladas limitadas. As correções de qualidade do Adobe Commerce não são fornecidas. Esse período não é equivalente ao suporte padrão ou estendido e não será estendido. Trate-o como um período de migração, não como um nível de suporte de longo prazo.

>[!IMPORTANT]
>
>O período transitório apenas para efeitos de segurança é uma exceção única. Ela não será estendida além das datas publicadas. Trate o período somente de segurança como tempo de migração, não como um nível de suporte de longo prazo.

## Datas de fim de suporte

A tabela a seguir mostra o ciclo de vida completo de cada versão do Adobe Commerce, incluindo as novas datas de imposição de atualização de versão para o Adobe Commerce em ambientes na nuvem.

| Versão | Disponibilidade geral | Fim do suporte padrão | Fim do suporte estendido | Fim do período apenas de segurança | [Data de imposição de atualização de versão (somente nuvem)](version-upgrade-enforcement-policy.md) |
| --------- | ---------------------- | ------------------------ | ------------------------- |-----------------------------| ----------------------------------------------- |
| Adobe Commerce 2.4.9 | 12 de maio de 2026 | 31 de maio de 2029 | TBD | N/D | TBD |
| Adobe Commerce 2.4.8 | 8 de abril de 2025 | 31 de maio de 2028 | TBD | N/D | TBD |
| Adobe Commerce 2.4.7 | 9 de abril de 2024 | 31 de maio de 2027 | 31 de maio de 2028 | N/D | 1 de junho de 2028 |
| Adobe Commerce 2.4.6 | 14 de março de 2023 | 11 de agosto de 2026 | 30 de agosto de 2027 | 31 de maio de 2028 | 1 de junho de 2028 |
| Adobe Commerce 2.4.5 | 9 de agosto de 2022 | 12 de agosto de 2025 | 12 de agosto de 2026 | 31 de maio de 2027 | 1 de junho de 2027 |
| Adobe Commerce 2.4.4 | 12 de abril de 2022 | 12 de abril de 2025 | 14 de abril de 2026 | 31 de maio de 2027 | 1 de junho de 2027 |

{style="table-layout:auto"}

## Cronograma do suporte

O cronograma de suporte mapeia os períodos de suporte trimestral por trimestre para cada linha de lançamento do Adobe Commerce. Use as tabelas fornecidas anteriormente neste tópico para datas finais exatas.

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
    <th colspan="4">2028</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="2"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**Chave**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>Suporte Standard</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>Suporte estendido</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>Correções de segurança estendida</td>
  </tr>
 </tbody>
</table>

## Dependências de plataforma

Permanecer em uma versão compatível do Commerce também requer dependências de plataforma compatíveis. A Adobe não fornece correções de segurança e qualidade para serviços e dependências de software de terceiros — como MariaDB, OpenSearch, Redis, Valkey, RabbitMQ e outras — que podem chegar ao fim da vida útil enquanto você estiver no período de suporte estendido ou de três anos para o Adobe Commerce. Consulte [Segurança de responsabilidade compartilhada e modelo operacional](../security-and-compliance/shared-responsibility.md) para obter detalhes.

Você é responsável por manter todas as dependências de terceiros e serviços da plataforma nas versões que têm suporte ativo. Consulte [Requisitos do sistema](../installation/system-requirements.md) para obter a lista completa de tecnologias de terceiros testadas e com suporte.

## Fim da vida útil do PHP e conformidade com o PCI

Você é responsável por monitorar o status de suporte das versões do PHP usadas em seus ambientes.

As seguintes versões do PHP usadas pelas linhas de lançamento mais antigas do Commerce atingiram ou chegarão ao fim da vida útil, o que tem implicações diretas na conformidade com o PCI.

| versão do PHP | Data de término da vida útil | Versões do Commerce afetadas | Impacto de conformidade com o PCI |
| ------------- | ------------------ | ---------------------------- | ------------------------ |
| PHP 8.1 | 31 de dezembro de 2025 | 2.4.4, 2.4.5 e 2.4.6 (onde o PHP 8.1 é usado) | Conformidade com o PCI em risco — executar o PHP 8.1 além de sua data de fim de vida útil significa que vulnerabilidades de segurança no PHP podem não receber correções, o que coloca a conformidade com o PCI em risco. Avalie o status da conformidade e priorize a atualização. |
| PHP 8.2 | 31 de dezembro de 2026 | 2.4.6 (onde o PHP 8.2 é usado) | Conformidade com o PCI em risco a partir do final de 2026 — planeje a atualização ou migração antes do final de 2026 para manter a conformidade com o PCI. |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>**Aviso de conformidade com o PCI:** a conformidade com o PCI é responsabilidade do comerciante. A Adobe recomenda que os comerciantes de versões afetadas consultem seu avaliador de segurança qualificado e priorizem a mudança para uma versão Commerce e uma versão PHP compatíveis o mais rápido possível. Para obter as linhas do tempo de suporte do PHP, consulte [versões do PHP compatíveis](https://www.php.net/supported-versions.php) e [fim da vida útil do PHP](https://www.php.net/eol.php).

## Opções de atualização e migração

Se você estiver em uma versão que está se aproximando ou que ultrapassou suas datas de fim de suporte, tome uma ação agora. Se você permanecer em uma versão não compatível, sua loja corre o risco de vulnerabilidades de segurança, problemas de conformidade e perda de suporte. O Adobe fornece os seguintes caminhos para migrar para uma versão compatível.

### Caminho recomendado: migrar para o Adobe Commerce as a Cloud Service

[!DNL Adobe Commerce as a Cloud Service] é a plataforma de comércio hospedada de última geração da Adobe e o destino de longo prazo recomendado da Adobe para todos os clientes do Adobe Commerce na nuvem.

- O Adobe gerencia automaticamente toda a infraestrutura, patches e upgrades.
- Você está sempre em uma infraestrutura compatível — a situação de fim de vida útil não se repete.
- Você tem acesso aos recursos mais recentes da Adobe: merchandising alimentado por IA, arquitetura de vitrine combinável e integrações nativas da Adobe Experience Cloud.
- Você elimina ciclos recorrentes de atualização.

Entre em contato com a equipe de conta da Adobe para iniciar uma avaliação de migração. Consulte [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/commerce/cloud-service/overview) para obter uma visão geral do produto.

### Caminho alternativo: atualizar para um Adobe Commerce compatível na nuvem ou versão local

Se você não puder migrar para o [!DNL Adobe Commerce as a Cloud Service] imediatamente, será possível atualizar para a versão mais recente do Adobe Commerce na nuvem com suporte no momento. Isso leva você a uma pilha de infraestrutura moderna e totalmente compatível, preservando seu modelo existente de implantação do Commerce na nuvem.

Observe que esse caminho não elimina obrigações de atualização futuras. Os clientes com Adobe Commerce em implantações na nuvem devem continuar atualizando à medida que as linhas de versão atingem suas datas de imposição de atualização de versão.
