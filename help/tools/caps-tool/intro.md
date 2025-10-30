---
title: '[!DNL Cloud Automation Patching Service (CAPS)]'
description: Saiba mais sobre  [!DNL Cloud Automation Patching Service (CAPS)], seus usos, como acessá-lo e as práticas recomendadas para aplicação automática de patches
hide: true
hidefromtoc: true
source-git-commit: 4bb2d597e93379dbe81bae100ccc0b94b39acf26
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# [!DNL Cloud Automation Patching Service (CAPS)]

O [!DNL Cloud Automation Patching Service] ([!DNL CAPS]) é uma ferramenta que automatiza o processo de aplicação e reversão de patches para Adobe Commerce em ambientes na nuvem. Ele oferece aos administradores de projeto do Commerce um fluxo de trabalho simplificado para aplicar e reverter patches, que inclui validação e verificações de integridade integradas para garantir que os ambientes da nuvem permaneçam estáveis e seguros.

Este guia foi projetado para comerciantes e parceiros da Adobe Commerce Cloud que desejam simplificar o processo de aplicação de patches, reduzir o risco de problemas relacionados a patches, melhorar a segurança e a estabilidade do ambiente e automatizar operações de patch de rotina.

## [!DNL CAPS] tópicos

* **[Como acessar](access.md)**
* **[Fluxo de trabalho](workflow.md)**
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
   * **Validação** - Executa verificações de integridade e garante que as funcionalidades críticas não sejam afetadas

* **Recursos de segurança**
   * Cria ambientes de integração temporários para testes
   * Valida a compatibilidade de patches antes do aplicativo
   * Fornece reversão automática em caso de falhas de validação
   * Aplica patches à pasta `m2-hotfixes` com remoção automática durante a reversão

## Integrações com a Adobe Commerce Cloud

O [!DNL CAPS] é totalmente integrado à infraestrutura da Adobe Commerce Cloud e funciona perfeitamente com seus ambientes de nuvem existentes. Ele aproveita os recursos nativos em nuvem para obter o desempenho ideal, fornece registro e monitoramento detalhados e se integra às ferramentas de suporte da Adobe Commerce Cloud.

## Tutorial em vídeo

Saiba mais sobre o Serviço de patch automatizado da Adobe Cloud e como essa ferramenta ajuda os usuários a encontrar e aplicar rapidamente os patches de segurança. O vídeo a seguir mostra como acessá-lo pelo painel SWAT, escolher o projeto e o ambiente e aplicar patches com um clique.

>[!VIDEO](https://video.tv.adobe.com/v/3476247/?learn=on&enablevpops)

## Casos de uso comuns

* **Patches de segurança** - Aplique rapidamente atualizações críticas de segurança
* **Reversão de patch** - Reverter com segurança patches problemáticos aplicados através de [!DNL CAPS]
* **Conformidade com a segurança** - Mantenha os padrões de segurança com correção automatizada
* **Estabilidade operacional** - Garanta a estabilidade do ambiente por meio da validação automatizada
