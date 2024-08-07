---
title: Programação de lançamento
description: Saiba quando a Adobe planeja anunciar o lançamento de novos recursos do Adobe Commerce.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: e9ef167f5425407f6b1850f0dd913d5d3e2bd628
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 2%

---

# Programação de lançamento

O Adobe se esforça continuamente para encontrar o equilíbrio certo entre fazer atualizações de produtos simples e previsíveis, além de fornecer melhorias e novos recursos aos participantes iniciais mais rapidamente (consulte [política de controle de versão](versioning-policy.md)). O objetivo deste cronograma é fornecer datas para quando o Adobe planeja anunciar o lançamento de novos recursos substanciais. Esses recursos podem variar ao longo do ano. No entanto, o Adobe lança regularmente e continuamente melhorias para ferramentas de extensibilidade, infraestrutura e produtos SaaS (serviços) entre as datas especificadas nesta página.

Versões do Adobe [patches](versioning-policy.md#patch-release) para cada linha de versão suportada do aplicativo Adobe Commerce PHP principal. As versões de correção são oportunidades de atualizar a base de código principal para manter sua plataforma segura, confiável e eficiente. Os recursos são independentes da base de código principal e estão disponíveis por meio de [módulo externo, extensão, ferramenta ou serviço da Web](versioning-policy.md#extensibility-infrastructure-and-services-release).

>[!NOTE]
>
>A partir de 2024, o Adobe não fornecerá mais acesso de &quot;pré-lançamento&quot; aos patches. Em vez disso, para as versões 2.4.7 e posteriores, os clientes da Adobe Commerce podem usar as [versões beta](beta.md) para acessar o código de disponibilidade pré-geral para fins de teste e desenvolvimento.

A tabela a seguir fornece as datas das versões programadas (as datas estão sujeitas a alterações):

<table>
<thead>
  <tr>
    <th>Disponibilidade geral</th>
    <th>Recursos</th>
    <th>Núcleo PHP</th>
  </tr>
</thead>
<tfoot>
   <tr>
      <td colspan="3"><strong>Legenda</strong>
         <ul>
           <li><strong><img alt="Ícone de recurso B2B" src="../assets/icons/enterprise.svg"></img> B2B</strong> — Novos recursos, melhorias e correções de erros para a extensão B2B do Adobe Commerce. Para obter detalhes sobre versões da extensão B2B, consulte as <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">Notas de versão B2B</a>.</li>
            <li><strong><img alt="Ícone de recurso de extensibilidade" src="../assets/icons/brackets.svg"></img> Extensibilidade</strong> — Novas ferramentas e serviços de desenvolvedor para extensibilidade fora do processo que são entregues independentemente das versões de patch. Por exemplo, SDK da interface do usuário do administrador, Eventos do Adobe I/O para Commerce e API Mesh.</li>
            <li><strong><img alt="Ícone de recurso de infraestrutura" src="../assets/icons/servers.svg"></img> Infraestrutura</strong> — Novos recursos e aprimoramentos da Adobe Commerce na infraestrutura em nuvem e dos pacotes do Cloud Tools Suite for Commerce, que foram projetados para implantar e gerenciar instalações e atualizações do Adobe Commerce na plataforma em nuvem.</li>
            <li><strong><img alt="Ícone de liberação de patch" src="../assets/icons/file-code.svg"></img> Patches</strong> — Atualizações para o aplicativo PHP principal do Adobe Commerce que incluem correções de segurança, conformidade, desempenho e qualidade de alta prioridade.</li>
            <li><strong><img alt="Ícone de recurso de serviços" src="../assets/icons/feature.svg"></img> Serviços</strong>—Novos recursos SaaS que são entregues independentemente das versões de patch. Por exemplo, Serviço de catálogo, Live Search e Recommendations de produto.</li>
         </ul>
      </td>
   </tr>
</tfoot>
<tbody>
  <tr>
    <td>13 de fevereiro de 2024</td>
    <td><img alt="Ícone de recurso de extensibilidade" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Extensibilidade</a><br><img alt="Ícone de recurso de infraestrutura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infraestrutura</a><br><img alt="Ícone de recurso de serviços" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Serviços</a></td>
    <td><img alt="Ícone de liberação de patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Patches de segurança</a>: 2.4.6-p4, 2.4.5-p6, 2.4.4-p7</td>
  </tr>
  <tr>
    <td>12 de março de 2024</td>
    <td>—</td>
    <td><img alt="Ícone de liberação de patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">patch do Beta</a>: 2.4.7-beta3</td>
  </tr>
  <tr>
    <td>9 de abril de 2024</td>
    <td><img alt="Ícone de recurso de extensibilidade" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Extensibilidade</a><br><img alt="Ícone de recurso de infraestrutura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infraestrutura</a><br><img alt="Ícone de recurso de serviços" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Serviços</a></td>
    <td><img alt="Ícone de liberação de patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"><strong>Adobe Commerce 2.4.7</a></strong>:<ul><li>Melhorias de desempenho</li><li>Aprimoramentos de qualidade</li><li>Aprimoramentos de segurança</li><li>Atualizações de dependência de terceiros</li></ul><img alt="Ícone de liberação de patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Patches de segurança</a>: 2.4.6-p5, 2.4.5-p7, 2.4.4-p8</td>
  </tr>
  <tr>
    <td>11 de junho de 2024</td>
    <td><img alt="Ícone de recurso de extensibilidade" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Extensibilidade</a><br><img alt="Ícone de recurso de infraestrutura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infraestrutura</a><br><img alt="Ícone de recurso de serviços" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Serviços</a></td>
    <td><img alt="Ícone de liberação de patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Patches de segurança</a>: 2.4.7-p1, 2.4.6-p6, 2.4.5-p8, 2.4.4-p9</td>
  </tr>
  <tr>
    <td>13 de agosto de 2024</td>
    <td><img alt="Ícone de recurso de extensibilidade" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Extensibilidade</a><br><img alt="Ícone de recurso de infraestrutura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infraestrutura</a><br><img alt="Ícone de recurso de serviços" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Serviços</a></td>
    <td><img alt="Ícone de liberação de patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Patches de segurança</a>: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10</td>
  </tr>
  <tr>
    <td>8 de outubro de 2024</td>
    <td><img alt="Ícone de recurso de extensibilidade" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Extensibilidade</a><br><img alt="Ícone de recurso de infraestrutura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infraestrutura</a><br><img alt="Ícone de recurso de serviços" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Serviços</a></td>
    <td><img alt="Ícone de liberação de patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">Patch do Beta</a>: 2.4.8-beta1<br><img alt="Ícone de liberação de patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Patches de segurança</a>: 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11</td>
  </tr>
</tbody>
</table>
