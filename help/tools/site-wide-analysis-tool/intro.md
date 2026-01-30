---
title: '[!DNL Site-Wide Analysis Tool]'
description: Saiba mais sobre a  [!DNL Site-Wide Analysis] Ferramenta, seus usos, o processo de instalação e como obter acesso
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 62ca9093228d4d928d6c61c4c5dcf26e142c9fdb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>A partir de 23 de abril de 2024, o [!DNL Site-Wide Analysis Tool] será descontinuado para todos os clientes locais do Adobe Commerce.

Este guia fornece uma visão geral holística do [!DNL Site-Wide Analysis Tool]. Ele descreve os usos, as instruções passo a passo para instalação e como acessar a ferramenta.

## O que é o [!DNL Site-Wide Analysis Tool]?

O [!DNL Site-Wide Analysis Tool] é uma ferramenta de autoatendimento proativa e um repositório central que inclui insights e recomendações detalhados do sistema para garantir a segurança e a operabilidade da sua instalação do Adobe Commerce. Ele fornece monitoramento de desempenho em tempo real, relatórios e conselhos 24 horas por dia, 7 dias por semana, para identificar possíveis problemas e melhor visibilidade das configurações de integridade, segurança e aplicativos do site. Ele ajuda a reduzir o tempo de resolução e a melhorar a estabilidade e o desempenho do site.

>[!NOTE]
>
>Depois de aplicar uma recomendação, pode levar alguns dias para que ela seja atualizada no Painel da ferramenta de análise do site ou no relatório gerado.
>
>O [!DNL Site-Wide Analysis Tool] relata dados no nível do sistema. Para obter relatórios sobre dados de aplicativos de produtos, vendas, marketing e outros dados de comércio do Adobe Commerce, consulte [Relatórios do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu).

![Painel da Ferramenta de Análise do Site](../../assets/tools/swat-dashboard.png){zoomable="yes"}

Veja este [vídeo de introdução](https://www.youtube.com/watch?v=KW2R8ki_RG4) para saber mais.

## Visão geral da ferramenta

- **Painel**
   - Mostra a integridade geral do sistema com notificações de problemas detectados e recomendações específicas por prioridade.<br>
Ele também inclui um gráfico histórico para rastrear como a integridade do site muda ao longo do tempo.
   - Mostra o **[!UICONTROL Security Center Widget]** que fornece links para os seguintes recursos:
      - [Conformidade de versão &lbrace;Tech [!DNL Stack] com [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)
      - [Boletim de Segurança do Adobe](https://helpx.adobe.com/security/security-bulletin.html)
      - [Recomendações de [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan)
      - [[!DNL Site-Wide Analysis Tool] Recomendações de Segurança de Práticas Recomendadas](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations)

- **Informações** - Fornece informações de contato do cliente e um resumo dos tíquetes atuais, com informações detalhadas sobre cada produto Adobe Commerce instalado.

- **Recommendations** - Fornece uma [Pontuação do Índice de Integridade SWAT](#swat-health-index.md) para rastrear a integridade do site e lista recomendações com base nas práticas recomendadas para resolver problemas detectados em seu site:
   - Para alterações que exijam uma atualização de infraestrutura, envie uma solicitação de suporte.
   - Para alterações que exigem uma atualização de aplicativo, faça você mesmo as alterações.
   - Para alterações que exigem intervenção manual, como uma [implantação de código](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow), peça ajuda ao administrador ou desenvolvedores do sistema.

- **Exceções** - Lista os erros lançados pelo aplicativo causados por condições anormais sem um manipulador de erros.

- **Extensões** - Lista todas as extensões e bibliotecas de terceiros.

- **Patches** - Integrado ao [!DNL Quality Patches Tool], fornece uma lista de todos os patches disponíveis específicos para a sua Instância do Adobe Commerce.

## Integrações com outras ferramentas de suporte da Adobe Commerce

Veja insights importantes sobre seu site em um só lugar. [!DNL Site-Wide Analysis Tool] permite que você obtenha acesso direto e informações de [!UICONTROL Security Center Widget], [!DNL Upgrade Compatibility Tool] e [!DNL Managed Alerts].

- **[!UICONTROL Security Center Widget]** - Exibe insights de segurança para o site.<br>
As informações de segurança incluem [Conformidade técnica [!DNL Stack] com a versão [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirement), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan), and [[!DNL Site-Wide Analysis Tool] Recomendações de Segurança de Práticas Recomendadas](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations).

  O [[!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) fornece aos clientes do Adobe Commerce e do Magento Open-Source informações em tempo real sobre a postura de segurança da loja, detectando proativamente o malware e alertando-os se a loja estiver comprometida.

- **[[!DNL Upgrade Compatibility Tool]](../../upgrade/upgrade-compatibility-tool/overview.md)** - Verifica a instância do Adobe Commerce em relação à versão da atualização e sinaliza problemas críticos, erros e avisos para corrigir antes da atualização. A solução desses problemas simplifica o processo de atualização.&quot;

- **[[!DNL Managed Alerts]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce)** - Monitore as métricas principais (CPU, desempenho do aplicativo, disco, memória e integridade do banco de dados) e forneça etapas de solução de problemas claras para ajudar os comerciantes a ficarem à frente dos problemas e evitar tempo de inatividade.

## Para quem este guia se destina?

Comerciantes e parceiros que desejam ter mais visibilidade de seus sites da Adobe Commerce. Ele permite que os comerciantes melhorem a experiência dos clientes e alinhem-se mais de perto com as práticas recomendadas e os problemas fundamentais.

## Demonstração do [!DNL Site-Wide Analysis Tool]

Assista a este vídeo para saber mais sobre o [!DNL Site-Wide Analysis Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
