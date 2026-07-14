---
title: Gerar um relatório de status de patch
description: Saiba como usar o [!DNL Commerce Version Tool] para gerar relatórios de status de patch do Adobe Commerce em formato JSON ou CSV.
TQID: 'https://experienceleague.adobe.com/-lC-20YMpbTM3tTZjbBO5zD5gb9n7cRah5Ycy8wQoyw'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: cb0391ae368b53a795535f3adb636628a339b963
workflow-type: tm+mt
source-wordcount: 590
ht-degree: 2%

---

# Gerar um relatório de status de patch

Use o [!DNL Commerce Version Tool] ([!DNL CVT]) para gerar um relatório de status de patch para uma instalação do Adobe Commerce. O relatório identifica patches de segurança mensais aplicados, ausentes e desconhecidos e retorna a saída JSON por padrão.

## Pré-requisitos

Antes de executar [!DNL CVT], confirme se:

- A instalação de destino usa uma versão e uma edição compatíveis do Adobe Commerce.
- `composer.lock` está presente e corresponde ao ambiente que você deseja inspecionar.
- O PHP e o binário do sistema `patch` estão disponíveis.
- Você pode ler os arquivos do projeto no ambiente em que executa o comando.
- A ferramenta pode gravar em `var/patch_metadata/` e `var/log/` se você quiser arquivos de cache e entradas de log de auditoria.
- As credenciais estão disponíveis por meio de `COMPOSER_AUTH` ou `auth.json` se patches com direitos forem aplicados à instalação.

A ferramenta [!DNL CVT] verifica `COMPOSER_AUTH`, o projeto Adobe Commerce `auth.json` e o Composer global `auth.json` quanto a credenciais de patch restritas a direitos.

## Gerar o relatório

Na raiz do projeto Adobe Commerce, execute:

```bash
php vendor/bin/patch-status
```

Para verificar outra instalação do Adobe Commerce, use a opção `--root`:

```bash
php vendor/bin/patch-status --root=/path/to/commerce
```

## Opções de comando

JSON é o formato de saída padrão. A saída em CSV é compatível com scanners, painéis e relatórios de conformidade.

| Opção | Descrição |
| --- | --- |
| `--root=PATH` | Especifica o caminho para a raiz de instalação do Adobe Commerce. O padrão é o diretório atual. |
| `--format=json\|csv` | Define o formato de saída. O padrão é `json`. |
| `--no-cache` | Ignora os caches de registro e patch-diff, força novas buscas remotas e sai com um erro se o registro remoto não estiver disponível. |
| `--version`, `-V` | Imprime a versão da ferramenta. |
| `--help`, `-h` | Imprime a mensagem de ajuda. |

{style="table-layout:auto"}

## Revisar saída em JSON e CSV

O exemplo a seguir mostra a saída JSON padrão.

```bash
php vendor/bin/patch-status
```

```json
{
  "base_version": "2.4.7-p9",
  "installed_components": {
    "CE": "2.4.7-p9",
    "EE": "2.4.7-p9",
    "B2B": "1.5.2-p5"
  },
  "applied_patches": [
    "247p9-2026-05-001-CE",
    "247p9-2026-05-001-EE"
  ],
  "missing_patches": [
    "247p9-2026-06-001-CE",
    "247p9-2026-06-001-EE"
  ],
  "unknown_patches": [],
  "vulnerability_status": {
    "CVE-2026-12354": { "status": "PROTECTED" },
    "CVE-2026-67890": { "status": "VULNERABLE" }
  },
  "registry_source": "remote",
  "warnings": []
}
```

Para gerar saída CSV, use a opção `--format=csv`:

```bash
php vendor/bin/patch-status --format=csv
```

A saída CSV produz uma linha por CVE e é adequada para planilhas, scanners, painéis e ferramentas de conformidade.

## Entender os resultados do relatório

Revise patches ausentes e desconhecidos antes de fazer declarações de status de segurança.

### Valores de status do patch

O relatório de status do patch agrupa os resultados do patch pelos seguintes valores:

| Status do patch | Significado |
| --- | --- |
| Aplicado | A ferramenta [!DNL CVT] detecta o patch de segurança mensal na base de código do Adobe Commerce. |
| Ausente | O patch se aplica à versão ou ao componente do Adobe Commerce instalado, mas a ferramenta [!DNL CVT] não o detecta. |
| Desconhecido | A ferramenta não pode confirmar o status do patch no registro disponível, na comparação de patches ou no resultado da detecção. |

{style="table-layout:auto"}

### Valores de status da CVE

A saída JSON relata os valores de status da CVE em maiúsculas.

| Status da CVE | Significado |
| --- | --- |
| `PROTECTED` | O patch aplicável é detectado para o CVE ou componente. |
| `VULNERABLE` | Um patch aplicável está ausente para o CVE ou componente. |
| `UNKNOWN` | A ferramenta [!DNL CVT] não pode determinar o status do CVE a partir dos dados de detecção e registro disponíveis. |
| `NOT_APPLICABLE` | O CVE se aplica a um componente que não está instalado, como o B2B (B2B) do Adobe Commerce, o Adobe Commerce Page Builder ou o Adobe Commerce Inventory. |

{style="table-layout:auto"}

### Campos principais de saída

O relatório pode incluir as seguintes informações:

- **Versão base do Adobe Commerce** - A versão base instalada detectada de `composer.lock`.
- **Origem do Registro** - Se os metadados de patch vieram de `remote`, `cache` ou `stale_cache`.
- **Componentes instalados** - áreas de pacote do Adobe Commerce detectadas de `composer.lock`.
- **Patches aplicados** - Patches de segurança mensais detectados na base de código do Adobe Commerce.
- **Patches ausentes** - Patches de segurança mensais que se aplicam, mas não são detectados.
- **Patches desconhecidos** - Patches que a ferramenta [!DNL CVT] não pode classificar.
- **Status de vulnerabilidade por CVE** - Cobertura de CVE mapeada para status protegido, vulnerável, não aplicável ou desconhecido.
- **Avisos** - Condições que podem afetar a confiabilidade ou a integridade do relatório.

## Registro e cache de patches

O arquivo de Registro de patch contém os metadados de patch que a ferramenta [!DNL CVT] usa para determinar quais patches se aplicam a uma versão instalada. A ferramenta usa um novo cache de registro quando disponível, busca o registro remoto quando necessário e pode usar um cache obsoleto com um aviso se a rede não estiver disponível. Use `--no-cache` somente quando precisar de novas buscas remotas.

## Tópicos relacionados

- [Introdução](intro.md)
- [Solução de problemas](troubleshooting.md)
- [Notas de versão](release-notes.md)
