---
title: '[!DNL Adobe Commerce Patching Automation]'
description: Saiba mais sobre  [!DNL Adobe Commerce Patching Automation], seus usos, como acessá-lo e as práticas recomendadas para aplicação automática de patches
hide: true
source-git-commit: f70924d6f0d1777104c59f3f9e776360308abceb
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!DNL Adobe Commerce Patching Automation]

O [!DNL Adobe Commerce Patching Automation] é uma ferramenta que automatiza o processo de aplicação e reversão de patches para Adobe Commerce em ambientes na nuvem. Ele oferece aos administradores de projeto do Commerce um fluxo de trabalho simplificado para aplicar e reverter patches. A validação e as verificações de integridade integradas ajudam a garantir que os ambientes em nuvem permaneçam estáveis e seguros.

Este guia foi projetado para comerciantes e parceiros da Adobe Commerce Cloud que desejam simplificar o processo de aplicação de patches, reduzir o risco de problemas relacionados a patches, melhorar a segurança e a estabilidade do ambiente e automatizar operações de patch de rotina.

## [!DNL Patching Automation] tópicos

* **[Como acessar](access.md)**
* **[Visão geral do fluxo de trabalho](workflow.md)**
* **[Integração com o GitHub](github-integration.md)**
* **[Práticas recomendadas](best-practices.md)**
* **[Solução de problemas](troubleshooting.md)**

## Visão geral da ferramenta

* **Interface de usuário**
  * Disponibilidade de patch e exibição de status em tempo real para combinações específicas de projeto e ambiente
  * Informações abrangentes sobre status de patch mostrando progresso, erros e outras mensagens relevantes
  * [!UICONTROL Patch Management Dashboard] para:
    * Exibição de patches disponíveis
    * Aplicação de patches com operação de um clique
    * Reverter patches aplicados anteriormente
    * Monitoramento do status e dos resultados da operação de patch

* **Serviço de patch automatizado com fluxo de trabalho estruturado**
  * **Verificação preliminar** - Valida a compatibilidade de patches e a preparação do ambiente
  * **Patches** - Aplica ou reverte patches automaticamente em ambientes de integração
  * **Validação** - Executa uma verificação de integridade para confirmar se o aplicativo é iniciado e se suas conexões de banco de dados e cache estão acessíveis

* **Recursos de segurança**
  * Valida a compatibilidade de patches antes do aplicativo
  * Aplica o patch em um ambiente de integração temporário primeiro, confirmando sua implantação com êxito e aprovação em uma verificação de integridade, antes de mesclar com seu ambiente de destino e, em seguida, executa uma verificação de integridade final imediatamente após a implantação
  * Aplica patches à pasta `m2-hotfixes` com remoção automática durante a reversão

## Integrações com a Adobe Commerce Cloud

O [!DNL Patching Automation] é totalmente integrado à infraestrutura da Adobe Commerce Cloud e funciona perfeitamente com seus ambientes de nuvem existentes. Ele aproveita os recursos nativos em nuvem para obter o desempenho ideal, fornece registro e monitoramento detalhados e se integra às ferramentas de suporte da Adobe Commerce Cloud.

## Tutorial em vídeo

Saiba mais sobre o [!DNL Adobe Commerce Patching Automation] e como essa ferramenta ajuda os usuários a encontrar e aplicar patches de segurança rapidamente. O vídeo a seguir mostra como acessá-lo pelo painel da Ferramenta de análise do site (SWAT), escolher o projeto e o ambiente e aplicar patches com um clique.

>[!VIDEO](https://video.tv.adobe.com/v/3476252/?captions=por_br&learn=on&enablevpops)

## Casos de uso comuns

* **Patches de segurança** - Aplique rapidamente atualizações críticas de segurança
* **Reversão de patch** - Reverta com segurança patches problemáticos aplicados por meio do serviço
* **Conformidade com a segurança** - Mantenha os padrões de segurança com correção automatizada
* **Estabilidade operacional** - Confirma que o aplicativo inicia e passa por uma verificação de integridade após cada operação de patch
