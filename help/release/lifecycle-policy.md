---
title: Política de ciclo de vida do software
description: Saiba mais sobre as principais datas relacionadas ao fim do suporte de software das versões do Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 7b32ed40efb7e72810f571c8b4b71a77c8aa6a20
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 4%

---


# política de ciclo de vida do Adobe Commerce

Para o Adobe Commerce 2.4.4 e versões subsequentes:

- Para simplificar a política de ciclo de vida do Adobe Commerce e atender às necessidades críticas dos clientes, a Adobe expandiu a janela de suporte para três anos a partir da data de disponibilidade geral (GA) do Adobe Commerce 2.4.4 e posteriores. O Adobe fornece correções de qualidade para a versão 2.4.4 e posteriores, por um período de suporte de três anos. Os clientes podem acessar as correções de qualidade entrando em contato com o [Suporte da Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) ou por meio do autoatendimento [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) se a versão ainda estiver qualificada para suporte de qualidade. A tabela a seguir descreve as datas de fim do suporte de software para as linhas de versão do Adobe Commerce.

- O Adobe fornece correções de segurança por meio de uma versão de patch de segurança para o período de suporte de três anos.

- Para problemas críticos de segurança, como vulnerabilidades &quot;zero-day&quot;, o Adobe fornece [hotfixes](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) para todos os clientes em uma versão com suporte, mesmo que eles não estejam na versão mais recente de patch ou patch de segurança. Observe que um hotfix não é abrangente e não trata de todos os problemas de segurança que seriam resolvidos com a atualização para a versão mais recente.

- O Adobe não fornece correções de segurança e qualidade para serviços e dependências de software de terceiros (como PHP e MySQL) que podem chegar ao fim da vida útil enquanto os clientes estão no período de suporte de três anos do Adobe Commerce. Consulte os [requisitos do sistema](../installation/system-requirements.md) para obter uma lista completa de tecnologias de terceiros testadas e com suporte.

- O Adobe oferece compatibilidade com serviços e dependências de software de terceiros enquanto os clientes estão no período de suporte de três anos para o Adobe Commerce no escopo de versões de patches somente de segurança, mas somente quando é possível fazê-lo sem introduzir alterações incompatíveis com versões anteriores.

## Suporte estendido

O Adobe incentiva os clientes a atualizarem o mais rápido possível. No entanto, para fornecer maior flexibilidade para alinhar-se aos planos de atualização e às necessidades de negócios, o Adobe oferece uma extensão de suporte de um ano sem custo adicional para clientes Adobe Commerce nas versões 2.4.4 e 2.4.5. A extensão de suporte inclui patches de qualidade e segurança para o aplicativo principal por até um ano.

>[!NOTE]
>
>O suporte estendido está disponível somente para clientes do Adobe Commerce. Não está disponível para a base de código Magento Open Source.

## Fim do suporte de software

| Versão | Disponibilidade geral | Fim do suporte regular<sup>1</sup> | Fim do suporte estendido | Versão dependente do PHP | Versão dependente de MariaDB |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 9 de abril de 2024 | 9 de abril de 2027 | N/D | 8.2 e 8.3 | 10,6 |
| Adobe Commerce 2.4.6 | 14 de março de 2023 | 11 de agosto de 2026<sup>2</sup> | N/D | 8.1 e 8.2 | 10,6 |
| Adobe Commerce 2.4.5 | 9 de agosto de 2022 | 9 de agosto de 2025 | 11 de agosto de 2026 | 8,1 | 10.6<sup>3</sup> |
| Adobe Commerce 2.4.4 | 12 de abril de 2022 | 12 de abril de 2025 | 14 de abril de 2026 | 8,1 | 10.6<sup>4</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> O fim do suporte de software inclui correções de fim de qualidade e de fim de segurança.
>- <sup>2</sup> Atualizado para alinhar com o fim do suporte estendido para 2.4.5.
>- <sup>3</sup> Começando com o patch de segurança 2.4.5-p11.
>- <sup>4</sup> Começando com o patch de segurança 2.4.4-p12.
>- Consulte [Política de Ciclo de Vida de Software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

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
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="8"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
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
   <td>Suporte regular</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>Suporte estendido</td>
  </tr>
 </tbody>
</table>
