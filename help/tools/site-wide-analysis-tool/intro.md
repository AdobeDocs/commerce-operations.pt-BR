---
title: '[!DNL Site-Wide Analysis Tool]'
description: Saiba mais sobre a  [!DNL Site-Wide Analysis] Ferramenta, seus usos, o processo de instalação e como obter acesso
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 23c5da67003ecd1939ea168a843e974b65977063
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>A partir de 23 de abril de 2024, o [!DNL Site-Wide Analysis Tool] será descontinuado para todos os clientes locais do Adobe Commerce.

Este guia fornece uma visão geral holística do [!DNL Site-Wide Analysis Tool]. Ele descreve os usos, as instruções passo a passo para instalação e como acessar a ferramenta.

## O que é [!DNL Site-Wide Analysis Tool]?

O [!DNL Site-Wide Analysis Tool] é uma ferramenta de autoatendimento proativa e um repositório central que inclui insights e recomendações detalhados do sistema para garantir a segurança e a operabilidade da sua instalação do Adobe Commerce. Ele fornece monitoramento de desempenho em tempo real, relatórios e conselhos 24 horas por dia, 7 dias por semana, para identificar possíveis problemas e melhor visibilidade das configurações de integridade, segurança e aplicativos do site. Ele ajuda a reduzir o tempo de resolução e a melhorar a estabilidade e o desempenho do site.

>[!NOTE]
>
>O [!DNL Site-Wide Analysis Tool] relata dados no nível do sistema. Para obter relatórios sobre dados de aplicativos de produtos, vendas, marketing e outros dados de comércio do Adobe Commerce, consulte [Relatórios do Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/start/reporting/reports-menu).

![Painel da Ferramenta de Análise do Site](../../assets/tools/swat-dashboard.png){zoomable="yes"}

Veja este [vídeo de introdução](https://www.youtube.com/watch?v=KW2R8ki_RG4) para saber mais.

## Visão geral da ferramenta

- **Painel**
   - Mostra a integridade geral do sistema com notificações de problemas detectados e recomendações específicas por prioridade.<br>
Ele também inclui um gráfico histórico para rastrear como a integridade do site muda ao longo do tempo.
   - Mostra o **[!UICONTROL Security Center Widget]** que permite acessar:
      - [Conformidade de versão &lbrace;Tech [!DNL Stack] com [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=pt-BR)
      - [Boletim de Segurança do Adobe](https://helpx.adobe.com/br/security/security-bulletin.html)
      - [Recomendações de [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=pt-BR)
      - [[!DNL Site-Wide Analysis Tool] Recomendações de Segurança de Práticas Recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=pt-BR)

- **Informações** - Fornece informações de contato do cliente e um resumo dos tíquetes atuais, com informações detalhadas sobre cada produto Adobe Commerce instalado.

- **Recommendations** - Fornece uma [Pontuação do Índice de Integridade SWAT](#swat-health-index.md) para rastrear a integridade do site e lista recomendações com base nas práticas recomendadas para resolver problemas detectados em seu site:
   - Para alterações que exijam uma atualização de infraestrutura, envie uma solicitação de suporte.
   - Para alterações que exigem uma atualização de aplicativo, faça você mesmo as alterações.
   - Para alterações que exigem intervenção manual, como uma [implantação de código](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=pt-BR#deployment-workflow), peça ajuda ao administrador ou desenvolvedores do sistema.

- **Exceções** - Lista os erros lançados pelo aplicativo causados por condições anormais sem um manipulador de erros.

- **Extensões** - Lista todas as extensões e bibliotecas de terceiros.

- **Patches** - Integrado ao [!DNL Quality Patches Tool], fornece uma lista de todos os patches disponíveis específicos para a sua Instância do Adobe Commerce.

## Integrações com outras ferramentas de suporte da Adobe Commerce

Veja todos os insights importantes sobre seu site em um só lugar. [!DNL Site-Wide Analysis Tool] permite que você obtenha acesso direto e informações de [!UICONTROL Security Center Widget], [!DNL Upgrade Compatability Tool] e [!DNL Managed Alerts].

- **[!UICONTROL Security Center Widget]** - Exibe insights de segurança para o site.<br>
As informações de segurança mostradas incluem [Conformidade técnica [!DNL Stack] com a versão [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=pt-BR), [Adobe Security Bulletin](https://helpx.adobe.com/br/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=pt-BR), and [[!DNL Site-Wide Analysis Tool] Recomendações de Segurança de Práticas Recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=pt-BR).<br>
O [[!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=pt-BR) fornece aos clientes do Adobe Commerce e do Magento Open-Source informações em tempo real sobre o status de segurança de sua loja, detectando proativamente o malware e notificando-os se a loja está comprometida.

- [**[!DNL Upgrade Compatability Tool]**](../../upgrade/upgrade-compatibility-tool/overview.md) - Executa a instância personalizada do Adobe Commerce com base na versão de atualização de destino e retorna um resumo de problemas críticos, erros e avisos que devem ser resolvidos, tornando o processo de análise de atualização mais fácil, rápido e barato.

- [**[!DNL Managed Alerts]**](https://support.magento.com/hc/en-us/sections/360010758472-Managed-alerts-for-Adobe-Commerce) - Monitore várias métricas para controlar proativamente o desempenho da plataforma e fornecer instruções específicas sobre como solucionar problemas, para que os comerciantes possam evitar tempo de inatividade crítico e se manter informados sobre sua CPU, o desempenho do aplicativo, o disco, a memória e o banco de dados.

## Para quem este guia se destina?

Comerciantes e parceiros que desejam ter mais visibilidade de seus sites da Adobe Commerce. Ele permite que os comerciantes melhorem a experiência dos clientes e alinhem-se mais de perto com as práticas recomendadas e os problemas fundamentais.

## Demonstração do [!DNL Site-Wide Analysis Tool]

Assista a este vídeo para saber mais sobre o [!DNL Site-Wide Analysis Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/3412498?captions=por_br&quality=12)
