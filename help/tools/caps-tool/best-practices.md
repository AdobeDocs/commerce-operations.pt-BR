---
title: Guia de práticas recomendadas do [!DNL Cloud Automation Patching Service (CAPS)]
description: Conheça as práticas recomendadas para usar o  [!DNL Cloud Automation Patching Service (CAPS)]  de maneira eficaz e segura
hide: true
hidefromtoc: true
source-git-commit: 9d377babd1059d7ec0af687755965ca4d0b541fb
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 0%

---

# Guia de práticas recomendadas do [!DNL Cloud Automation Patching Service (CAPS)]

As práticas recomendadas a seguir são essenciais para operações de patch bem-sucedidas e seguras com [!DNL Cloud Automation Patching Service] ([!DNL CAPS]). Este guia fornece práticas recomendadas abrangentes para operações eficazes de patch, gerenciamento de ambiente e excelência operacional.

## Práticas recomendadas de pré-patch

### Disponibilidade do ambiente

**Prática recomendada:** sempre prepare seu ambiente cuidadosamente antes de aplicar patches para garantir operações bem-sucedidas e minimizar riscos.

Antes de aplicar patches, verifique se o ambiente está preparado corretamente:

* **Conta da Adobe Commerce Cloud**
   * Assinatura ativa da Adobe Commerce Cloud
   * Licença válida do Adobe Commerce
   * Credenciais de acesso ao repositório configuradas
   * Permissões de projeto e ambiente

* **Recursos do ambiente**
   * Slots de ambiente disponíveis para teste temporário
   * Recursos suficientes de armazenamento, CPU e memória
   * Acesso à rede para repositórios Adobe
   * Ambiente pai estável para sincronização

* **Preparação do ambiente de produção** (para correção de produção)
   * O modo de manutenção pode ser ativado
   * Os trabalhos do Cron podem ser desabilitados
   * Procedimentos de janela de manutenção estabelecidos
   * Procedimentos de reversão documentados
   * Plano de comunicação das partes interessadas pronto

## Práticas recomendadas para aplicativos de patch

### Calendário e programação

**Prática recomendada:** agende operações de correção durante períodos de tráfego baixo e coordene com as partes interessadas para minimizar o impacto nos negócios.

**Escolha a hora certa para o aplicativo de patch:**

* **Períodos de tráfego baixo**
   * Agendar patches fora do horário de pico
   * Evite aplicar patches durante eventos de alto tráfego
   * Planejar tempo de inatividade potencial durante a validação

* **Considerações sobre o ambiente de produção**
   * **Janelas de manutenção** - Agendar patches de produção durante janelas de manutenção planejadas
   * **Comunicação com o cliente** - Notifique os clientes sobre o modo de manutenção e o tempo de inatividade esperado
   * **Coordenação da equipe** - Verifique se todos os membros da equipe estão cientes do cronograma de manutenção
   * **Preparação da reversão** - Tenha membros da equipe disponíveis para reversão imediata, se necessário

### Monitoramento e validação

**Durante operações de patch:**

* **Monitorar progresso**
   * Observar o status da operação em tempo real
   * Preste atenção a quaisquer avisos ou erros
   * Não interromper o processo depois de iniciado

* **Validar resultados**
   * Testar funcionalidade crítica após o aplicativo bem-sucedido
   * Verificar se há degradação nas métricas de desempenho
   * Verifique se as medidas de segurança permanecem intactas

## Práticas recomendadas pós-patch

### Verificação e ensaio

**Prática recomendada:** sempre verifique o sucesso do aplicativo de patch por meio de testes e monitoramento abrangentes para garantir a estabilidade e a funcionalidade do sistema.

**Após o aplicativo de patch bem-sucedido:**

* **Teste funcional**
   * Testar todos os processos críticos de negócios
   * Verificar fluxos de pagamento e check-out
   * Verificar a funcionalidade do painel do administrador

* **Monitoramento de desempenho**
   * Monitorar tempos de carregamento da página
   * Verificar desempenho do banco de dados
   * Fique atento a picos de uso de recursos

* **Validação de segurança**
   * Verifique se os recursos de segurança estão funcionando
   * Verifique se há novas vulnerabilidades de segurança
   * Testar autenticação e autorização

## Práticas recomendadas do ambiente de produção

### Teste de pré-produção

**Prática recomendada:** nunca aplique patches diretamente à produção sem testes completos em ambientes de pré-produção que espelhem a configuração da produção.

**Sempre testar patches antes da implantação de produção:**

* **Configuração de ambiente de teste**
   * Usar ambientes de preparo ou integração para testes
   * Garantir que o ambiente de teste espelhe a configuração de produção
   * Testar com dados semelhantes aos de produção quando possível

* **Teste abrangente**
   * Testar todos os processos críticos de negócios
   * Verificar fluxos de pagamento e check-out
   * Verificar a funcionalidade do painel do administrador
   * Testar todas as integrações personalizadas

* **Teste de desempenho**
   * Monitorar o impacto de patches no desempenho
   * Verifique se há degradação de desempenho
   * Verificar se o uso de recursos permanece aceitável

### Redução de riscos

**Minimizar riscos durante a aplicação de patch de produção:**

* **Plano de comunicação**
   * Notifique os clientes sobre as janelas de manutenção
   * Manter as partes interessadas informadas sobre o progresso
   * Tenha os procedimentos de encaminhamento prontos

* **Estratégia de reversão**
   * Saber como reverter patches rapidamente, se necessário
   * Disponibilizar membros da equipe para resposta imediata
   * Procedimentos de reversão de documentos

* **Monitoramento e alertas**
   * Configurar monitoramento para problemas pós-patch
   * Ter alertas para falhas críticas
   * Monitore atentamente as métricas de desempenho

## Resumo das principais práticas recomendadas

### Práticas recomendadas críticas para o sucesso de [!DNL CAPS]

* Sempre teste na pré-produção antes de aplicar patches a ambientes de produção
* Ativar modo de manutenção e desativar trabalhos cron para operações de patch de produção
* Monitore as operações de perto e tenha os procedimentos de reversão prontos
* Documentar todas as operações de patch e manter registros abrangentes
* Siga os procedimentos adequados de gerenciamento de alterações e obtenha as aprovações apropriadas
* Manter os ambientes sincronizados e manter a alocação adequada de recursos
* Estabelecer procedimentos claros de suporte e manter o treinamento da equipe
* Revisar e melhorar regularmente os processos de gerenciamento de patches

## Tópicos relacionados

* [Introdução ao CAPS](intro.md)
* [Como acessar o](access.md)
* [Fluxo de trabalho (WRK)](workflow.md)
* [Solução de problemas](troubleshooting.md)
