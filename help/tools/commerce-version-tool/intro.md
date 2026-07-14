---
title: '[!DNL Commerce Version Tool]'
description: Saiba mais sobre o [!DNL Commerce Version Tool] for Adobe Commerce e use fornecedor/bin/patch-status para verificar o status mensal do patch de segurança.
TQID: 'https://experienceleague.adobe.com/9lDQtCrcCSIFjt3jUJkqCo-rMlIhhy3tPTtPyT4wt1Q'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 586
ht-degree: 0%

---

# [!DNL Commerce Version Tool]

Os patches de segurança mensais do Adobe Commerce não são cumulativos e devem ser aplicados em sequência. O [!DNL Commerce Version Tool] ([!DNL CVT]) ajuda os comerciantes a verificar a cobertura de patches, relatando quais patches de segurança mensais estão instalados, quais patches estão ausentes e quais CVEs a instalação está protegida.

>[!IMPORTANT]
>
>A ferramenta [!DNL CVT] é apenas informativa. Ela não aplica patches, reverte patches ou modifica arquivos de origem do Adobe Commerce. Ele pode gravar arquivos armazenados em cache, arquivos temporários executados sem interrupção e entradas de log de auditoria para oferecer suporte a relatórios de status de patch.

## Visão geral da ferramenta

A ferramenta [!DNL CVT] é um executável independente incluído em cada patch de segurança mensal do Adobe Commerce. Quando o patch é aplicado a uma instalação do Adobe Commerce, a ferramenta é instalada em `vendor/bin/patch-status`. Ela requer o PHP 8.1 ou posterior e o binário `patch` do sistema. Ele não requer pacotes do Composer, extensões PHP não padrão, inicialização do Adobe Commerce ou uma etapa de instalação separada.

A ferramenta [!DNL CVT] pode ajudá-lo a:

- Detectar patches de segurança aplicados para uma instalação Adobe Commerce suportada.
- Identifique patches ausentes em uma sequência mensal de patch de segurança isolada.
- Relatar status de segurança protegido, vulnerável ou desconhecido para registros CVE (Common Vulnerabilities and Exposures, vulnerabilidades e exposições comuns) relacionados a patches.
- Produzir saída legível por máquina, como JSON ou CSV, para scanners, painéis e relatórios de conformidade.
- Detectar status de patch para plataformas e componentes compatíveis.

## Disponibilidade

A ferramenta [!DNL CVT] oferece suporte a relatórios de status de patch para as seguintes plataformas e componentes quando a Adobe fornece metadados de patch para a versão instalada no arquivo de registro de patch.

| Plataforma ou componente | Disponibilidade |
| --- | --- |
| Adobe Commerce no local | Compatível |
| [!DNL Magento Open Source] | Compatível |
| B2B (B2B) da Adobe Commerce | Compatível quando instalado |
| Adobe Commerce Page Builder | Compatível quando instalado |
| Inventário do Adobe Commerce | Compatível quando instalado |
| Componentes adicionais detectados de `composer.lock` | Compatível quando representado no arquivo de registro de patch |

{style="table-layout:auto"}

## Casos de uso comuns

Use a ferramenta [!DNL CVT] quando precisar:

- Verifique se uma instalação do Adobe Commerce inclui patches de segurança isolados necessários.
- Confirme se os conjuntos de patches ignorados ou incompletos deixam a cobertura CVE incompleta.
- Gerar saída JSON ou CSV para relatórios internos ou verificação automatizada.
- Fornecer informações sobre o status do patch antes de abrir uma solicitação de suporte ou planejar a correção.

## Diretrizes para usar resultados

Trate a saída da ferramenta [!DNL CVT] como dados de detecção que oferecem suporte ao planejamento de patches e à revisão de segurança.

Siga estas orientações:

- Execute a ferramenta [!DNL CVT] em uma instalação estável e com suporte do Adobe Commerce.
- Revise patches ausentes e desconhecidos antes de fazer declarações de status de segurança.
- Preserve a saída em JSON ou CSV para fins de auditoria e automação.
- Tratar a saída da varredura como dados operacionais relevantes para a segurança.
- Compartilhe somente os detalhes necessários para suporte ou correção.

## Detecção de patches

A ferramenta [!DNL CVT] executa a detecção em duas etapas fixas. Ambas as etapas sempre são executadas quando você gera um relatório de status de patch.

- **Detecção do compositor:** a ferramenta lê o arquivo `composer.lock` para determinar a versão base [!DNL Adobe Commerce] e as áreas do componente instalado. Se a ferramenta não puder detectar uma versão base, ela existirá com o código `1`.

- **Detecção de simulação:** Para cada patch aplicável, a ferramenta usa uma verificação de simulação contra as alterações do patch para determinar se o patch já foi aplicado, se não foi aplicado ou se o status do patch é desconhecido. A ferramenta trata das dependências de patch durante essa verificação para que os resultados reflitam a versão do componente instalado.

O relatório inclui apenas patches que se aplicam à instalação detectada e componentes instalados. Se a ferramenta não puder confirmar se um patch aplicável está presente, ela classificará o patch como desconhecido.

## Começar a usar o [!DNL CVT]

Use estes tópicos para gerar, solucionar problemas e rastrear relatórios de status de patch:

- [Gere um relatório de status de patch](generate-report.md) para executar a ferramenta [!DNL CVT], revise as opções de comando e interprete os resultados do relatório.
- [[!DNL Commerce Version Tool] solucionando problemas](troubleshooting.md) para resolver resultados inesperados ou erros de comando.
- [[!DNL Commerce Version Tool] notas de versão](release-notes.md) para revisar atualizações de versão.
