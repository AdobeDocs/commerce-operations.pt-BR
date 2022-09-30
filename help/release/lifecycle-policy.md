---
title: Política de ciclo de vida do software
description: Saiba mais sobre as principais datas de fim do suporte de software para versões do Adobe Commerce.
source-git-commit: 79f36e3728e6bc436e8093bd4051143a48e681d6
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 5%

---


# Política de ciclo de vida do Adobe Commerce

Para o Adobe Commerce 2.4 e versões subsequentes:

- Para simplificar melhor nossa política de ciclo de vida, o Adobe fornece correções de qualidade para a linha da versão 2.4 até a data de fim do suporte para a versão PHP em que se baseia. Um cliente pode acessar correções de qualidade entrando em contato com [Suporte Adobe Commerce](https://developer.adobe.com/commerce/contributor/community/support/) ou através do autoatendimento [Ferramenta Correções de Qualidade](https://devdocs.magento.com/quality-patches/tool.html) se a sua versão ainda for elegível para apoio de qualidade. Consulte a tabela abaixo para obter as datas de Fim do Suporte de Software para as linhas de lançamento da Adobe Commerce.

- O Adobe fornece correções de segurança somente por meio do patch ou da versão de patch de segurança mais recente, mesmo que a versão de um cliente ainda esteja qualificada para suporte de qualidade. Ao contrário de correções de qualidade, as correções de segurança não podem ser enviadas para versões secundárias anteriores nem para versões de patches anteriores em versões secundárias compatíveis.

- Para problemas críticos de segurança, como vulnerabilidades de zero dia, o Adobe fornece [hotfixes](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) para todos os clientes em uma versão compatível, mesmo que não estejam na versão de patch ou patch de segurança mais recente. É importante observar que um hotfix não é abrangente e não aborda todos os problemas de segurança que seriam corrigidos ao atualizar para a versão mais recente.

## Fim do suporte de software

| Versão | Data de lançamento | Fim do suporte de software<sup>1</sup> | Versão PHP dependente |
| -------------------------------- | ----------------- | ----------------------------------- | --------------------------- |
| Adobe Commerce 2.3 | 28 de novembro de 2018 | 8 de setembro de 2022<sup>2</sup> | PHP 7.3 e 7.4<sup>3</sup> |
| Adobe Commerce 2.4.0-2.4.3 | 28 de julho de 2020 | 28 de novembro de 2022 | PHP 7.4 |
| Adobe Commerce 2.4.4-2.4.6 | 12 de abril de 2022 | 25 de novembro de 2024 | PHP 8.1 |

<sup>1 O Fim do Suporte de Software inclui correções de qualidade e fim das correções de segurança.</sup><br>
<sup>2 A data de término do suporte de software para 2.3 foi estendida até 8 de setembro de 2022 para dar mais tempo aos clientes para atualizarem para a versão 2.4.4, que estará disponível em geral em 8 de março de 2022.</sup><br>
<sup>3 2.3.0-2.3.6 depende do PHP 7.3; 2.3.7 depende do PHP 7.4.</sup>

>[!NOTE]
>
>Consulte [Política de ciclo de vida do software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table>
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Comércio</td>
    <td>PHP</td>
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
    <td>2.4.0 - 2.4.3</td>
    <td style="text-align:center">7,4</td>
    <td colspan="3" style="background-color:#67ac68;"></td>
    <td style="background-color:#cd3c3c;">Novembro</td>
    <td colspan="8" ></td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td rowspan="2" style="text-align:center">8,1</td>
    <td></td>
    <td colspan="10" style="background-color:#67ac68;">Mar</td>
    <td rowspan="2" style="background-color:#cd3c3c;">Novembro</td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="9" style="background-color:#67ac68;">Ago</td>
  </tr>
</tbody>
</table>

## Chave

<table>
  <thead>
   <tr>
    <th></th>
    <th></th>
   </tr>
  </thead>
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">Suportado</td>
   <td>Versão que foi totalmente testada pelo Adobe e é compatível.</td>
  </tr>
  <tr>
   <td style="background-color:#cd3c3c;">Fim do suporte de software</td>
   <td>Versão que chegou ao fim do suporte de software.</td>
  </tr>
 </tbody>
</table>
