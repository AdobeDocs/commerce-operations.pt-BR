---
title: Visão geral do fluxo de trabalho [!DNL Adobe Commerce Patching Automation]
description: Saiba mais sobre o  [!DNL Adobe Commerce Patching Automation] processo de fluxo de trabalho, incluindo terminologia, fases de fluxo de trabalho e operações para gerenciamento automatizado de patches.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 0%

---

# Visão geral do fluxo de trabalho [!DNL Adobe Commerce Patching Automation]

Este tópico fornece uma visão geral de alto nível de como as operações de patch funcionam usando o [!DNL Adobe Commerce Patching Automation].

## Terminologia

* **Operações** - as principais ações executadas pelo serviço:
  * Aplicar
  * Reverter
* **Fases** - as três fases do fluxo de trabalho:
  * Verificação preliminar
  * Patches
  * Validação
* **Ambiente** - o ambiente da Adobe Commerce Cloud onde os patches são aplicados.

## Operações

O [!DNL Patching Automation] oferece suporte a duas *operações* principais para o gerenciamento de patches no ambiente da Adobe Commerce Cloud:

* **Aplicar operação** - adiciona alterações de patch à sua base de código por meio de um processo seguro e validado. Os patches são aplicados colocando os arquivos de patch na pasta `m2-hotfixes`.

* **Operação de reversão** - remove os patches aplicados anteriormente da sua base de código removendo arquivos de patch da pasta `m2-hotfixes`.

>[!IMPORTANT]
>
>As operações de reversão só estão disponíveis para patches originalmente aplicados através de [!DNL Patching Automation]. Os patches aplicados manualmente ou por outros métodos não podem ser revertidos com este serviço.

## Fases

O fluxo de trabalho [!DNL Patching Automation] usa três *fases* que são sempre executadas nesta ordem para garantir que os patches sejam aplicados de forma segura e confiável:

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

A fase Patch aplica ou reverte o patch em um ambiente de integração temporário. Durante esse estágio, o serviço cria um ambiente de integração temporário para aplicar com segurança o patch, confirmar sua implantação e verificar se ele passa em uma verificação de integridade — antes de fazer qualquer alteração no ambiente real.

Essa abordagem oferece:

* **Segurança** - mantém o ambiente de destino intacto até que o ambiente de integração seja implantado com êxito e seja aprovado na verificação de integridade
* **Recurso de reversão** - se forem detectados problemas
* **Isolamento** - para cada operação de patch

#### Estágio 2a: criação de ambiente de integração

**A criação de ramificação** - [!DNL Patching Automation] cria uma ramificação de ambiente de integração temporária chamada `{target-environment}-CAPS-{patch-id}`

**Configuração do ambiente** - O ambiente de integração é criado como filho do ambiente de destino

**Sincronização de código** - O ambiente de integração herda o estado de código exato do ambiente de destino (a mesma base de código)

**Sem clonagem de dados** - O ambiente de integração não recebe uma cópia dos dados do ambiente de destino (banco de dados, mídia ou outro conteúdo armazenado); somente a base de código é usada para aplicar e verificar o patch

**Requisitos de recursos** - A capacidade total de armazenamento do seu projeto na nuvem está definida em seu contrato. (Verifique na página da sua conta ou `magento-cloud subscription:info`). Cada alocação de disco do ambiente é configurada separadamente, por meio da propriedade `disk` em `.magento.app.yaml`/`.magento/services.yaml`. Consulte [Gerenciar espaço em disco](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) para obter detalhes. Se uma operação de patch falhar devido a limitações de armazenamento, verifique o uso de disco do ambiente de integração (`magento-cloud db:size` / `magento-cloud mount:size`) em relação à alocação configurada.

#### Estágio 2b: aplicação de patches no ambiente de integração

**Teste seguro** - O patch é aplicado ao ambiente de integração, não diretamente ao ambiente de destino

**Gerenciamento de arquivos** - Os arquivos de patch são colocados na pasta `m2-hotfixes`

**Operações do Git** - as alterações são confirmadas e enviadas para a ramificação do ambiente de integração

**Ativação do ambiente** - O ambiente de integração é ativado para implantar o código corrigido

**Verificação de integridade** - Depois de ativada, [!DNL Patching Automation] confirma o seguinte antes de prosseguir com a mesclagem: o ambiente de integração foi implantado com êxito e está íntegro, o aplicativo é iniciado e suas conexões de banco de dados e cache estão acessíveis.

>[!NOTE]
>
>Se o projeto usar um repositório GitHub externo, o serviço manipulará a autenticação automaticamente usando o [[!DNL Patching Automation] Aplicativo GitHub](github-integration.md). Nenhuma credencial adicional é necessária além da instalação do aplicativo.

#### Estágio 2c: mesclar de volta ao ambiente de destino

**Verificação de sincronização** - Antes de mesclar, o serviço confirma que o ambiente de integração ainda está ativo, sincronizado com o ambiente de destino e íntegro. Se o destino tiver sido alterado durante a aplicação de patch, a operação pára aqui em vez de mesclar

**Check-out do ambiente** - O serviço faz o check-out do ambiente de destino localmente

**Operação de mesclagem** - A ramificação do ambiente de integração é mesclada ao ambiente de destino

**Tratamento de conflitos** - Se ocorrer um conflito de mesclagem, a operação falhará e será relatada como um erro; ela não será resolvida automaticamente

**Implantação** - As alterações mescladas são implantadas no ambiente de destino

**Verificação** - O serviço verifica se a mesclagem foi bem-sucedida e se os ambientes estão sincronizados

### Ciclo de vida do ambiente de integração

Os ambientes de integração têm um ciclo de vida específico durante a fase de correção:

* **Criação** - Criada no início da fase de correção
* **Período ativo** - Permanecer ativo durante o teste e o aplicativo de patch
* **Limpeza** - Excluída imediatamente se a operação falhar durante a fase de Patch, antes da mesclagem. Caso contrário, excluído durante a fase de Validação, após a mesclagem, independentemente de a validação ser aprovada ou não

### Fase 3: Validação

A fase de Validação confirma que o aplicativo com patch é iniciado com êxito e passa por uma verificação de integridade.

**O que acontece:**

* **Verificação de integridade do aplicativo** - verifica se o aplicativo foi iniciado e executado corretamente e se suas conexões de banco de dados e cache estão acessíveis
* **Limpeza** - remove o ambiente de integração temporária e atualiza o status do trabalho para refletir a conclusão. A atividade do ambiente permanece visível no feed de atividades do projeto.

>[!IMPORTANT]
>
>Ao contrário das Fases 1 e 2, esta verificação de integridade é executada *após*, pois o patch já foi mesclado ao ambiente de destino. Se falhar, a mesclagem não será revertida automaticamente. O ambiente de destino pode ser deixado em um estado interrompido, e é necessária intervenção manual (como reverter o patch) para restaurá-lo. Consulte [Solução de problemas](troubleshooting.md) para saber o que fazer se isso acontecer.

## Indicadores de sucesso

**Aplicar operação:**

* &quot;Trabalho concluído com êxito&quot; - Patch aplicado sem problemas
* &quot;O patch foi aplicado&quot; - O patch já estava presente (nenhuma ação é necessária)
* Arquivo de patch colocado com sucesso na pasta `m2-hotfixes`
* Todas as verificações de validação passaram
* Verificações de integridade do aplicativo bem-sucedidas

**Operação de reversão:**

* &quot;Trabalho concluído com êxito&quot; - Patch revertido sem problemas
* &quot;O patch foi revertido&quot; - O patch já foi revertido (nenhuma ação é necessária)
* Arquivo de patch removido com êxito da pasta `m2-hotfixes`
* Todas as verificações de validação passaram
* Verificações de integridade do aplicativo bem-sucedidas

## Proteções do ambiente de produção

Aplicar ou reverter patches em um ambiente de produção traz mais risco do que em outros ambientes, portanto, o [!DNL Patching Automation] inclui duas proteções específicas para produção.

### Confirmação antes de iniciar

Antes de qualquer operação de aplicação ou reversão começar em um ambiente de produção, você será solicitado a confirmar a operação em uma caixa de diálogo. Essa etapa de confirmação protege contra a inicialização acidental de um trabalho na produção.

### Pré-condições recomendadas

A Adobe recomenda ativar o modo de manutenção e desativar os trabalhos cron antes de corrigir um ambiente de produção. Por padrão, o [!DNL Patching Automation] verifica se ambas as condições foram atendidas e bloqueia a operação com uma notificação se uma das condições não for atendida. Se você entender os riscos de continuar sem o modo de manutenção ou com os trabalhos cron ativados, marque a caixa de seleção de substituição na interface do usuário para ignorar essa verificação.

* **Modo de manutenção** - Recomendável para ser habilitado
* **Trabalhos do Cron** - Recomendável desabilitar

## Tópicos relacionados

* [Introdução à automação de patches](intro.md)
* [Como acessar o](access.md)
* [Integração com o GitHub](github-integration.md)
* [Práticas recomendadas](best-practices.md)
* [Solução de problemas](troubleshooting.md)
