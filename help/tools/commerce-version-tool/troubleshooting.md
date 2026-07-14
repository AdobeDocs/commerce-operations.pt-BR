---
title: Solução de problemas do [!DNL Commerce Version Tool]
description: Saiba como solucionar problemas do  [!DNL Commerce Version Tool] Composer, verificações internas de execução a seco, cache do Registro, saída JSON e problemas de log de auditoria.
TQID: 'https://experienceleague.adobe.com/JwRSy7pfM89WoifYUzTVPhR-WrDIvj2A2B8SaEnmyWM'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 1222
ht-degree: 0%

---

# Solução de problemas do [!DNL Commerce Version Tool]

Use esta página para solucionar problemas comuns do [!DNL Commerce Version Tool] ([!DNL CVT]) com detecção do Composer, carregamento do Registro, detecção interna de patch de execução seca, geração de saída e registro de auditoria.

## Etapas rápidas de solução de problemas

Se a ferramenta [!DNL CVT] não retornar o relatório de status de patch esperado:

- Confirme se a instalação de destino usa uma versão e uma edição do Adobe Commerce com suporte.
- Confirme se `composer.lock` está presente e corresponde ao ambiente que você deseja inspecionar.
- Confirme se o PHP e o binário `patch` do sistema estão disponíveis.
- Confirme se [!DNL CVT] pode ler o arquivo de patch do Registro.
- Revise `warnings`, `missing_patches` e `unknown_patches` na saída.
- Verifique `var/log/patch_status.log` para o resumo de auditoria da execução, se o arquivo de log for criado.

>[!TIP]
>
> O arquivo de log é mais útil quando você precisa entender por que um patch não pode ser classificado. Para cada patch desconhecido, o log registra a saída bruta das tentativas de simulação de encaminhamento e reversão, incluindo erros ou falhas de bloco.
>
> Se tiver problemas ao buscar os arquivos de registro ou patch, verifique o campo avisos no relatório. Esses detalhes não aparecem no log.

## Problemas comuns e soluções

### A versão base não pode ser detectada

Se a ferramenta [!DNL CVT] não puder localizar a versão base do Adobe Commerce, verifique estas condições:

**Verificar:**

- `composer.lock` está ausente.
- O comando `patch-status` está sendo executado fora da raiz do projeto do Adobe Commerce (ou `--root` aponta para o caminho errado), portanto `composer.lock` não foi encontrado.
- `composer.lock` existe mas não é um JSON válido ou não pode ser lido.
- `composer.lock` não contém nenhum dos pacotes base reconhecidos (`magento/product-enterprise-edition`, `magento/product-community-edition`, `magento/magento2-base`).

**Mensagens de aviso:**

Se `composer.lock` existir, mas for ilegível, não analisável ou não contiver um pacote base reconhecido, a ferramenta emitirá uma das seguintes cadeias de caracteres no campo de saída avisos:

```shell-session
No recognized Commerce base package found in composer.lock
composer.lock exists but could not be read
composer.lock could not be parsed as JSON
```

>[!NOTE]
>
> Se `composer.lock` estiver totalmente ausente, a ferramenta relata `base_version: "unknown"` com **nenhuma mensagem de aviso**. Sempre verificar `base_version` diretamente na saída. Não dependa da presença de um aviso para encontrar esse problema.

Qualquer uma das condições mencionadas anteriormente indica que a ferramenta não pode detectar a versão base. A ferramenta sai com o código `1` e nenhuma detecção de patch é executada.

**Ações:**

- Execute o comando `patch-status` a partir da raiz do projeto [!DNL Adobe Commerce] ou passe o `--root` correto.
- Confirme se `composer.lock` está presente, é atual e é um JSON válido.
- Confirme se a instalação usa uma edição Adobe Commerce com suporte para que `composer.lock` contenha um dos pacotes base reconhecidos.

### Nenhum patch se aplica à versão instalada

Se [!DNL CVT] relatar um `base_version` válido, mas `applied_patches`, `missing_patches` e `unknown_patches` estiverem vazios, a versão instalada não será coberta pelo Registro de patch atual.

**Verificar:**

- A versão [!DNL Adobe Commerce] instalada não está representada no arquivo de registro de patch. Por exemplo, uma versão mais recente do que as entradas mais recentes do registro.

**Mensagens de aviso:**

```shell-session
No patches found in registry for installed component versions (CE=2.4.7-p9)
```

Este aviso é diferente de &quot;A versão base não pode ser detectada&quot;. O `base_version` está correto, a ferramenta existe `0` e não há nada no Registro para comparação.

**Ações:**

- Confirme `base_version` na saída é o que você espera.
- Confirme se `registry_source` é `remote` ou um `cache` recente, não um obsoleto.
- Entre em contato com o suporte da Adobe Commerce se a versão já precisar ser abordada.

### O registro de patch não pode ser obtido

Se a ferramenta [!DNL CVT] não puder obter o arquivo de registro de patch mais recente, verifique as configurações de rede e cache:

**Verificar:**

- Rede indisponível.
- A solicitação do ponto de extremidade de patch do Adobe atinge o tempo limite.
- `--no-cache` foi usado e o registro remoto não pode ser acessado.
- `PATCH_REGISTRY_URL` aponta para um Registro indisponível ou não é uma URL HTTPS válida.
- Se a ferramenta [!DNL CVT] não puder obter o arquivo de registro de patch mais recente, verifique as configurações de rede e cache:

>[!NOTE]
>
>Se o arquivo de registro estiver ausente ou expirado, a ferramenta baixará o registro mais recente do host remoto.

**Mensagens de aviso:**

A ferramenta emite as seguintes cadeias de caracteres no campo de saída de avisos para este cenário:

```shell-session
Remote registry fetch failed (HTTP 403). Check PATCH_REGISTRY_URL (if set) and network connectivity.
Remote registry response was not valid JSON; ignoring.
Could not load remote registry. Using cached registry (3 hours old). CVE coverage may be incomplete.
Patch registry could not be loaded.
Could not fetch remote registry and --no-cache was set; aborting.
```

A mensagem de cache obsoleta inclui a idade real em horas, por exemplo, `(3 hours old)`.

Os avisos `patch registry could not be loaded` e `could not fetch remote registry` indicam que a ferramenta saiu sem executar a detecção de patch.

**Ações:**

- Execute novamente o comando `patch-status` quando a conectividade de rede estiver disponível.
- Permitir que a ferramenta [!DNL CVT] use o registro armazenado em cache se um aviso de cache obsoleto for aceitável para a verificação.
- Remova `--no-cache` a menos que você exija novas buscas remotas.
- Confirme se a ferramenta [!DNL CVT] pode gravar em `var/patch_metadata/` se você deseja reutilizar o cache do Registro.

### Não é possível buscar ou verificar a diferença entre patches

Se a ferramenta [!DNL CVT] não puder testar um ou mais patches aplicáveis, verifique o acesso de comparação de patches:

**Verificar:**

- Uma comparação de patch não pode ser baixada do endpoint de patch do Adobe.
- As credenciais necessárias para downloads de patch autenticados estão ausentes ou são inválidas.
- `PATCH_DIFF_BASE_URL` aponta para uma origem de comparação de patch indisponível ou não é uma URL HTTPS válida.
- A comparação de patch em cache está ausente ou não pode ser lida.
- Falha na verificação SHA-256 para uma diferença de patch baixado.
- A ferramenta [!DNL CVT] não pode gravar em `var/patch_metadata/.patch_diffs/`.

**Mensagens de aviso:**

A ferramenta emite as seguintes cadeias de caracteres no campo de saída de avisos para este cenário:

```shell-session
Patch 247p9-2026-05-001-EE requires authentication. Set credentials via COMPOSER_AUTH or auth.json.
Could not fetch patch 247p9-2026-05-001-EE (HTTP 401). Check credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch 247p9-2026-05-001-EE (HTTP 404).
Could not fetch or verify patch 247p9-2026-05-001-EE. Check network connectivity and credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch file for 247p9-2026-05-001-EE.
SHA-256 verification failed for patch 247p9-2026-05-001-EE; discarding download.
```

A ID do patch em cada mensagem é a ID de entrada de registro real, por exemplo `247p9-2026-05-001-EE`. `SHA-256 verification failed` significa que um arquivo de patch recém-baixado não corresponde à soma de verificação esperada. A ferramenta o descarta sem armazenar em cache e classifica o patch `unknown` para essa execução. Uma entrada de cache *local* corrompida foi detectada e buscada silenciosamente na mesma execução sem aviso. Em ambos os casos, nenhuma limpeza manual do cache é necessária.

**Ações:**

- Confirme a conectividade da rede e repita o comando.
- Confirme se as credenciais necessárias para downloads de patches autenticados estão configuradas.
- Confirme se a ferramenta [!DNL CVT] pode gravar em `var/patch_metadata/.patch_diffs/`.
- Preserve o aviso e os detalhes de saída se o patch permanecer classificado como desconhecido.

### Patches ausentes ou desconhecidos são reportados

Se o relatório contiver valores inesperados de `missing_patches` ou `unknown_patches`, verifique os detalhes de instalação e saída:

**Verificar:**

- Os patches mensais foram aplicados fora de sequência.
- Um patch específico de componente, como Adobe Commerce B2B (B2B) ou Adobe Commerce Page Builder, está ausente.
- `composer.lock` relata uma versão de componente instalada que requer o patch.
- Uma comparação de correção não está disponível ou o resultado da detecção é inconclusivo.

**Mensagens de aviso:**

A ferramenta emite as seguintes cadeias de caracteres no campo de saída de avisos para este cenário:

```shell-session
No file_name or sha256 for 247p9-2026-05-001-EE
Registry entry '247p9-2026-05-001-EE' requires unknown patch '247p9-2026-04-001-EE'; skipping.
descendant diffs unavailable for 247p9-2026-06-001-EE; dry-run for 247p9-2026-05-001-EE may be inaccurate
Failed to reverse-apply 247p9-2026-06-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
Failed to forward-apply prerequisite 247p9-2026-04-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
```

Quando você encontrar `may be inaccurate` em um aviso, a verificação de simulação ainda será executada, mas com confiança reduzida. O patch ainda pode ser categorizado em `applied_patches` ou `missing_patches`, não necessariamente `unknown_patches`.

Para patches desconhecidos especificamente, `var/log/patch_status.log` registra a saída bruta de execução seca de patch (avançar e retroceder), que indica quais arquivos e partes falharam na correspondência.

Se você encontrar um aviso &quot;Nenhum patch encontrado&quot;, consulte [nenhum patch se aplica à versão instalada](#no-patches-apply-to-the-installed-version) para obter orientação.

**Ações:**

- Revise os campos `applied_patches`, `missing_patches` e `unknown_patches`.
- Confirme se os patches ausentes se aplicam à edição e aos componentes instalados.
- Compare o resultado com as notas de versão de patch de segurança relevantes.
- Confirme se a base de código inspecionada corresponde ao ambiente implantado sobre o qual você pretende criar relatórios.
- Entre em contato com o suporte da Adobe Commerce se o status desconhecido bloquear o planejamento de correção.

### Saída não gerada

Se a ferramenta [!DNL CVT] for concluída, mas a saída JSON ou CSV esperada estiver ausente, verifique a sintaxe do comando e a saída do terminal:

**Ações:**

- Use a saída JSON padrão se a saída CSV não for necessária.
- Use `--format=csv` para gerar saída CSV.
- Confirme se a saída do comando não é redirecionada ou descartada pelo shell, script ou scanner que executa a ferramenta [!DNL CVT].
- Verificar `stderr` por `patch-status:` mensagens de erro.
- Se estiver redirecionando a saída para um arquivo, por exemplo `patch-status > report.json`, confirme se o shell tem permissão de gravação para esse destino. A ferramenta só grava em `stdout`.
- Confirme se a ferramenta [!DNL CVT] pode gravar em `var/log/patch_status.log`.
- Execute novamente o comando e capture a saída do terminal para solucionar problemas.

## Obtendo ajuda

Ao entrar em contato com o suporte da Adobe Commerce, forneça apenas os detalhes necessários para investigar o problema.

Incluir:

- Versão e edição do Adobe Commerce
- Versão da ferramenta [!DNL CVT]
- Origem do Registro da saída da ferramenta [!DNL CVT]
- Valores `applied_patches`, `missing_patches` e `unknown_patches` relevantes
- Avisos relevantes
- Mensagem de erro ou saída de comando

Não inclua segredos, credenciais, chaves privadas ou dados não relacionados do cliente em logs compartilhados ou anexos.

## Tópicos relacionados

- [Introdução](intro.md)
- [Gerar um relatório de status de patch](generate-report.md)
- [Notas de versão](release-notes.md)
