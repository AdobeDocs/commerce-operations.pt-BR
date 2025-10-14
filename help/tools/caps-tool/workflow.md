---
title: Como o fluxo de trabalho  [!DNL Cloud Automation Patching Service (CAPS)]  funciona
description: Saiba mais sobre o  [!DNL Cloud Automation Patching Service (CAPS)] processo de fluxo de trabalho, incluindo terminologia, fases de fluxo de trabalho e operações para gerenciamento automatizado de patches.
hide: true
hidefromtoc: true
source-git-commit: eff8c0ae9e1d9db6b46ba7cfbb915685ab5b194d
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 0%

---

# Como o fluxo de trabalho [!DNL Cloud Automation Patching Service (CAPS)] funciona

Este tópico fornece uma visão geral de alto nível de como as operações de patch funcionam usando o [!DNL CAPS (Cloud Automation Patching Service)].

## Terminologia

* **Operações** - as principais ações executadas por [!DNL CAPS]:
   * Aplicar
   * Reverter
* **Fases** - as três fases do fluxo de trabalho:
   * Verificação preliminar
   * Patches
   * Validação
* **Ambiente** - o ambiente da Adobe Commerce Cloud onde os patches são aplicados.

## Operações

O [!DNL CAPS] oferece suporte a duas *operações* principais para o gerenciamento de patches no ambiente da Adobe Commerce Cloud:

* **Aplicar operação** - adiciona alterações de patch à sua base de código por meio de um processo seguro e validado. Os patches são aplicados colocando arquivos de patch na pasta &quot;m2-hotfixes&quot;.

* **Operação de reversão** - remove os patches aplicados anteriormente da base de código removendo arquivos de patch da pasta &#39;m2-hotfixes&#39;.

>[!IMPORTANT]
>
>As operações de reversão só estão disponíveis para patches originalmente aplicados através de [!DNL CAPS]. Os patches aplicados manualmente ou por outros métodos não podem ser revertidos com este serviço.

## Fases

O fluxo de trabalho [!DNL CAPS] usa três *fases* que são sempre executadas nesta ordem para garantir que os patches sejam aplicados de forma segura e confiável:

* **Verificação preliminar** - valida a compatibilidade de patches e a preparação do ambiente.
* **Patches** - aplica ou reverte o patch em um ambiente de integração.
* **Validação** - valida o aplicativo de patch e executa verificações de integridade.

## Detalhes da fase

### Fase 1: Verificação preliminar

A fase de Verificação Preliminar valida que o patch pode ser aplicado com segurança em seu ambiente.

**O que acontece:**

* **Proteções do ambiente de produção** (Somente ambientes de produção):
   * Verifica se o armazenamento está no modo de manutenção
   * Verifica se os trabalhos cron estão desabilitados
   * Bloqueia patches se as condições não forem atendidas
   * Exibe caixa de diálogo de confirmação se as condições forem atendidas
* **Validação de patch** - verifica se o arquivo de patch é válido e compatível
* **Avaliação do ambiente** - verifica a preparação e os recursos do ambiente
* **Detecção de conflitos** - identifica possíveis conflitos com o código existente
* **Verificação de dependência** - valida a compatibilidade de versão do Adobe Commerce

### Fase 2: Patches

A fase Patch aplica ou reverte o patch em um ambiente de integração temporário para teste. Durante esse estágio, o [!DNL CAPS] cria um ambiente de teste temporário para aplicar e testar com segurança o patch antes de fazer alterações no ambiente real.

Essa abordagem oferece:

* **Segurança** - mantém o ambiente de destino intacto até a validação do patch
* **Teste** - em um ambiente real antes de afetar a produção
* **Recurso de reversão** - se forem detectados problemas
* **Isolamento** - para cada operação de patch

#### Estágio 2a: criação de ambiente de integração

**A criação de ramificação** - [!DNL CAPS] cria uma ramificação de ambiente de integração temporária chamada `{target-environment}-CAPS-{patch-id}`

**Configuração do ambiente** - O ambiente de integração é criado como filho do ambiente de destino

**Sincronização de código** - O ambiente de integração herda o estado exato do ambiente de destino

**Requisitos de recursos** - [!DNL CAPS] cria um ambiente temporário usando a base de código do ambiente de destino. De acordo com a documentação da Adobe Commerce Cloud, cada ambiente (incluindo ambientes de integração) tem alocação de armazenamento separada com base em seu plano de armazenamento contratado. A quantidade de armazenamento que você contratou representa o armazenamento total de cada ambiente. Na maioria dos casos, você não enfrentará problemas com as limitações de recursos. Se você encontrar algum erro com limitações de recursos, verifique o tamanho do aplicativo e o armazenamento contratado no seu plano.

#### Estágio 2b: aplicação de patches no ambiente de integração

**Teste seguro** - O patch é aplicado ao ambiente de integração, não diretamente ao ambiente de destino

**Gerenciamento de arquivos** - Os arquivos de patch são colocados no diretório `m2-hotfixes/`

**Operações do Git** - as alterações são confirmadas e enviadas para a ramificação do ambiente de integração

**Ativação do ambiente** - O ambiente de integração é ativado para implantar o código corrigido

#### Estágio 2c: mesclar de volta ao ambiente de destino

**Check-out do ambiente** - [!DNL CAPS] faz o check-out local do ambiente de destino

**Operação de mesclagem** - A ramificação do ambiente de integração é mesclada ao ambiente de destino

**Resolução de conflitos** - Se ocorrerem conflitos, eles serão resolvidos automaticamente quando possível

**Implantação** - As alterações mescladas são implantadas no ambiente de destino

**Verificação** - [!DNL CAPS] verifica se a mesclagem foi bem-sucedida e se os ambientes estão sincronizados

**Limpeza de ambiente** - O ambiente de integração temporário é excluído para liberar recursos

## Ciclo de vida do ambiente de integração

Os ambientes de integração têm um ciclo de vida específico durante a fase de correção:

* **Criação** - Criada no início da fase de correção
* **Período ativo** - Permanecer ativo durante o teste e o aplicativo de patch
* **Limpeza** - Excluída automaticamente após mesclagem bem-sucedida ou se a operação falhar

### Fase 3: Validação

A fase de Validação garante que o aplicativo corrigido funcione corretamente e executa verificações de integridade.

**O que acontece:**

* **Verificação de integridade do aplicativo** - verifica se o aplicativo foi iniciado e executado corretamente
* **Limpeza** - remove o ambiente temporário, atualiza os logs, notifica a conclusão

## Indicadores de sucesso

**Aplicar operação:**

* &quot;Trabalho concluído com êxito&quot; - Patch aplicado sem problemas
* &quot;O patch foi aplicado&quot; - O patch já estava presente (nenhuma ação é necessária)
* Arquivo de patch colocado com sucesso na pasta &#39;m2-hotfixes&#39;
* Todas as verificações de validação passaram
* Verificações de integridade do aplicativo bem-sucedidas

**Operação de reversão:**

* &quot;Trabalho concluído com êxito&quot; - Patch revertido sem problemas
* &quot;O patch foi revertido&quot; - O patch já foi revertido (nenhuma ação é necessária)
* Arquivo de patch removido com sucesso da pasta &quot;m2-hotfixes&quot;
* Todas as verificações de validação passaram
* Verificações de integridade do aplicativo bem-sucedidas

## Proteções do ambiente de produção

O [!DNL CAPS] inclui proteções específicas para ambientes de produção para evitar interrupções acidentais e garantir que os patches sejam validados com segurança antecipadamente.

### Pré-condições para patch de produção

Antes de aplicar patches a ambientes de produção, o [!DNL CAPS] verifica se há duas condições críticas:

* **Modo de manutenção** - O repositório deve estar no modo de manutenção
* **Trabalhos Cron desabilitados** - os trabalhos Cron devem ser desabilitados

Se nenhuma das condições for atendida, o aplicativo de patch será bloqueado e o usuário será notificado.

## Tópicos relacionados

* [Introdução ao CAPS](intro.md)
* [Como acessar o](access.md)
* [Práticas recomendadas](best-practices.md)
* [Solução de problemas](troubleshooting.md)
