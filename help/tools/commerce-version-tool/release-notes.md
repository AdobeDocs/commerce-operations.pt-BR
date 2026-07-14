---
title: Notas de versão do [!DNL Commerce Version Tool]
description: Saiba mais sobre  [!DNL Commerce Version Tool] versões, incluindo novos relatórios de status de patch, status de proteção CVE, saída CSV e comportamento de cache.
feature: Release Notes
TQID: 'https://experienceleague.adobe.com/38I3U5y9rmurP5gVhalfUq7DlcUb-JpF5eUam1nwEyk'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 180
ht-degree: 2%

---

# Notas de versão do [!DNL Commerce Version Tool]

Essas notas de versão descrevem atualizações para [!DNL Commerce Version Tool] ([!DNL CVT]).

## Versão 1.0.0 — junho de 2026 {#version-1-0-0}

### Novos recursos

- **Relatório de status de patch** - Relatórios sobre quais patches de segurança mensais do Adobe Commerce são aplicados, estão ausentes ou não puderam ser classificados para uma instalação do Adobe Commerce.
- **Status de proteção CVE** - Mapeia os resultados do patch para valores de status de proteção por CVE: `PROTECTED`, `VULNERABLE`, `UNKNOWN` e `NOT_APPLICABLE`.
- **Suporte a vários componentes** - Detecta componentes instalados do Adobe Commerce a partir de `composer.lock`, incluindo B2B (B2B) do Adobe Commerce, Adobe Commerce Page Builder, Adobe Commerce Inventory e outros componentes representados no arquivo de registro de patch.
- **Saída JSON e CSV** - Fornece saída JSON por padrão para consumo programático e saída CSV para planilhas, scanners, painéis e ferramentas de conformidade.
- **Comportamento do cache compatível com offline** - Armazena o arquivo do Registro em cache localmente após cada busca bem-sucedida. Se o registro remoto não estiver disponível, a ferramenta [!DNL CVT] poderá usar o registro em cache com um aviso.
- **Entrega agrupada** - É enviada dentro de arquivos de correção de segurança mensais do Adobe Commerce. A aplicação do patch instala o [!DNL CVT] em `vendor/bin/patch-status` sem nenhuma etapa de instalação separada.

## Tópicos relacionados

- [Introdução](intro.md)
- [Gerar um relatório de status de patch](generate-report.md)
- [Solução de problemas](troubleshooting.md)
