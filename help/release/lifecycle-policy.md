---
title: Política de ciclo de vida do software
description: Saiba mais sobre as principais datas relacionadas ao fim do suporte de software das versões do Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 3bf3c4261073ab649376bb5c7fb84ea591a09869
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 2%

---


# política de ciclo de vida do Adobe Commerce

Para simplificar a política de ciclo de vida do Adobe Commerce e atender às necessidades críticas dos clientes, a Adobe oferece um período de suporte de três anos a partir da data de disponibilidade geral (GA) para cada versão e lança correções de qualidade durante esse período. Para obter datas e detalhes sobre o fim do suporte de software para cada versão, consulte a tabela [Fim do suporte de software](#end-of-software-support).

Durante o período de suporte de três anos, o cliente terá acesso a:

- **Correções de qualidade** - Os clientes podem acessar correções de qualidade entrando em contato com o [Suporte da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) ou por meio do autoatendimento [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). A tabela a seguir descreve as datas de fim do suporte de software para as linhas de versão do Adobe Commerce.

- **Correções de segurança**-O Adobe fornece correções de segurança por meio de patches de segurança cumulativos e [arquivos de patch de segurança isolados](versioning-policy.md#isolated-security-fixes) não cumulativos para o período de suporte de três anos.

- **Hotfixes**-Para problemas críticos de segurança, como vulnerabilidades inexistentes, a Adobe fornece [hotfixes](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) para todos os clientes em uma versão com suporte, mesmo que eles não estejam na versão mais recente de patch ou patch de segurança. Observe que um hotfix não é abrangente e não trata de todos os problemas de segurança que seriam resolvidos com a atualização para a versão mais recente.

A Adobe não fornece correções de segurança e qualidade para serviços e dependências de software de terceiros (como PHP e MySQL) que podem chegar ao fim da vida útil enquanto os clientes estão no período de suporte estendido ou de três anos para o Adobe Commerce. Consulte os [requisitos do sistema](../installation/system-requirements.md) para obter uma lista completa de tecnologias de terceiros testadas e com suporte.

## Suporte estendido

A Adobe incentiva os clientes a atualizarem o mais rápido possível. No entanto, para fornecer maior flexibilidade para alinhar-se aos planos de atualização e às necessidades de negócios, a Adobe oferece uma extensão de suporte de um ano sem custo adicional para clientes do Adobe Commerce nas versões 2.4.6. A extensão de suporte inclui patches de qualidade e segurança para o aplicativo principal por até um ano. O suporte estendido para as versões 2.4.4 e 2.4.5 do Adobe Commerce termina em abril e agosto de 2026, conforme planejado.

>[!NOTE]
>
>O suporte estendido está disponível somente para clientes do Adobe Commerce. Não está disponível para a base de código do Magento Open Source.

## Fim do suporte de software

| Versão | Disponibilidade geral | Fim do suporte regular<sup>1</sup> | Fim do suporte estendido |
|----------------------|----------------------|------------------------------------|-------------------------|
| Adobe Commerce 2.4.8 | 8 de abril de 2025 | 31 de maio de 2028 | TBD |
| Adobe Commerce 2.4.7 | 9 de abril de 2024 | 31 de maio de 2027 | TBD |
| Adobe Commerce 2.4.6 | 14 de março de 2023 | 11 de agosto de 2026 | 30 de agosto de 2027 |
| Adobe Commerce 2.4.5 | 9 de agosto de 2022 | 12 de agosto de 2025 | 11 de agosto de 2026 |
| Adobe Commerce 2.4.4 | 12 de abril de 2022 | 12 de abril de 2025 | 14 de abril de 2026 |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> Se você for um cliente da Adobe Commerce, poderá continuar recebendo correções de segurança e qualidade por mais um ano durante o período de suporte estendido.
>- Consulte [Política de Ciclo de Vida de Software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!IMPORTANT]
>
>A conformidade com o PCI não pode ser garantida para comerciantes que executam a versão 2.4.6 e continuam a usar o PHP 8.1, que chegou ao [fim do suporte em 2025](https://www.php.net/eol.php). Da mesma forma, o PHP 8.2 chega ao [fim da vida útil no final de 2026](https://www.php.net/supported-versions.php), criando o mesmo risco de conformidade com o PCI para os comerciantes que continuarem a usá-lo em 2027.

## Provisionamento de correções de segurança adicionais para o Adobe Commerce 2.4.4 e 2.4.5

Como exceção única, a Adobe está fornecendo um período estendido de provisionamento de correções de segurança para as versões 2.4.4 e 2.4.5 do Adobe Commerce, a fim de dar aos clientes tempo adicional para migrar para o Adobe Commerce as a Cloud Service ou atualizar para uma linha de versão compatível.

Durante esse período de provisionamento de correções de segurança, observe o seguinte:

- **Somente arquivo de patch de segurança isolado** - Um arquivo de patch de segurança isolado será lançado para essas versões de acordo com o cronograma de lançamento. Nenhuma versão de patch de segurança (nenhuma nova versão -p) será fornecida durante esse período.

  Para aplicar um arquivo de patch de segurança isolado, os clientes devem estar na versão de patch de segurança mais recente (a versão mais recente -p) para a linha de lançamento compatível, já que as correções de segurança isoladas são testadas exclusivamente em relação a essa versão.

- **Nenhuma correção de qualidade ou assistência de engenharia**. Nenhuma correção de erros, atualização de qualidade ([Ferramenta de Patches de Qualidade](../tools/quality-patches-tool/usage.md)) ou assistência de engenharia ([Suporte da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)) será fornecida para as versões 2.4.4 ou 2.4.5 durante este período.

- **Não há garantia de conformidade com o PCI:** - Como as versões 2.4.4 e 2.4.5 do PHP atingiram o fim da vida útil, a conformidade com o PCI não pode ser garantida para os comerciantes nessas versões. Continuar a executar essas versões pode colocar em risco a conformidade com o PCI.

Para manter uma cobertura de segurança completa e garantir a conformidade com o PCI, os clientes devem atualizar para uma versão atualmente compatível do Adobe Commerce o mais rápido possível ou migrar para o [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/commerce/cloud-service/overview).

| Versão | Disponibilidade geral | Fim do suporte estendido | Provisionamento de fim de correções de segurança |
|----------------------|----------------------|-------------------------|------------------------------------|
| Adobe Commerce 2.4.5 | 9 de agosto de 2022 | 11 de agosto de 2026 | Maio de 2027 |
| Adobe Commerce 2.4.4 | 12 de abril de 2022 | 14 de abril de 2026 | Maio de 2027 |

{style="table-layout:auto"}

>[!NOTE]
>
>Correções de segurança adicionais estão disponíveis somente para clientes do Adobe Commerce e não estão disponíveis para a base de código do Magento Open Source.


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
    <td colspan="6"></td>
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
   <td>Suporte regular</td>
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
