---
title: Guia de Solução de Problemas do [!DNL Cloud Automation Patching Service (CAPS)]
description: Solucionar problemas comuns e mensagens de erro no [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---

# Guia de solução de problemas do [!DNL Cloud Automation Patching Service (CAPS)]

Ao usar o [!DNL CAPS] para operações de patch, você pode encontrar mensagens de erro e problemas que podem impedir o êxito do aplicativo de patch ou da reversão. Este guia fornece soluções para os problemas mais comuns.

## Etapas rápidas de solução de problemas

### Se a operação de patch falhar

* Verifique o status da operação para entender em qual estágio houve falha
* Revisar mensagens de erro para motivos específicos de falha
* Examinar logs de erros para obter detalhes técnicos
* Siga as soluções fornecidas neste guia

### Duração das operações de patch

Para a maioria dos ambientes, a linha do tempo a seguir descreve quanto tempo as operações de patch devem levar, mas pode levar mais tempo, dependendo do tamanho e da complexidade do ambiente:

* **Pré-processando:** 2-5 minutos
* **Patches:** 5-15 minutos
* **Pós-processamento:** 10-40 minutos
* **Total:** 15-60 minutos

### Cancelamento de uma correção em andamento

>[!WARNING]
>
>Depois que uma operação de patch começar, ela poderá ser concluída. O sistema inclui procedimentos de limpeza que são executados mesmo se as operações falharem. Interromper o processo pode deixar o ambiente em um estado inconsistente.

## Mensagens de sucesso comuns

* **&quot;Trabalho concluído com êxito&quot;** - O patch foi aplicado/revertido com êxito sem problemas.

* **&quot;O patch foi aplicado&quot;** - Você está tentando aplicar um patch que já foi aplicado. O sistema detectou que o patch já está presente no ambiente. Nenhuma ação é necessária.

* **&quot;O patch foi revertido&quot;** - Você está tentando reverter um patch que já foi revertido. O sistema detectou que o patch não está aplicado no momento. Nenhuma ação é necessária.

## Mensagens e soluções de erro comuns

### Correção de erros de aplicação

#### &quot;O patch não pode ser aplicado porque o [!DNL CAPS] detectou esses problemas na sua base de código ou no arquivo de patch&quot;

**Quando ocorrer:** Durante a verificação preliminar

**Causa:** o patch está em conflito com sua base de código atual OU há um problema com o patch em si

**Soluções:**

* Revise os logs de erro detalhados fornecidos para identificar se é um problema de base de código ou de patch
* Verifique se há personalizações conflitantes em seu código
* Verifique se o patch é compatível com a sua versão do Adobe Commerce
* Considere resolver conflitos manualmente ou entre em contato com o suporte

#### &quot;Este patch não foi gerenciado por [!DNL CAPS]. Não é possível reverter&quot;

**Quando ocorrer:** Durante operações de reversão

**Causa:** Você está tentando reverter um patch que não foi aplicado através de [!DNL CAPS]

**Solução:** Use o mesmo método usado para aplicar o patch originalmente ou contate o suporte para obter assistência manual

### Erros de ambiente e validação

#### &quot;O ambiente não está sincronizado com o pai&quot;

**Quando ocorrer:** Durante a validação

**Causa:** seu ambiente de integração é diferente do ambiente pai

**Soluções:**

* Sincronizar o ambiente com a ramificação principal
* Repita a operação de patch
* Entre em contato com o suporte se os problemas de sincronização persistirem

#### &quot;Proteções do ambiente de produção não atendidas&quot;

**Quando ocorrer:** Durante a verificação preliminar de ambientes de produção

**Causa:** o ambiente de produção não atende às condições de segurança necessárias

**Soluções:**

* Habilitar modo de manutenção para o armazenamento de produção
* Desabilitar trabalhos cron no ambiente de produção
* Verifique se ambas as condições foram atendidas antes de tentar novamente

>[!IMPORTANT]
>
> [!DNL CAPS] não habilita automaticamente o modo de manutenção ou desabilita trabalhos cron - eles devem ser feitos externamente por você

#### &quot;O patch foi aplicado, mas houve falha na verificação de integridade. Considere reverter&quot;

**Quando ocorrer:** Após o aplicativo de patch durante a validação

**Causa:** o patch foi aplicado com êxito, mas as verificações de integridade falharam

**Soluções:**

* Revisar logs de aplicativo para erros específicos
* Testar funcionalidade crítica manualmente
* Considere reverter o patch se os problemas persistirem
* Entre em contato com o suporte se precisar de assistência

### Erros de autenticação e acesso

#### &quot;Falha de autenticação para o repositório do Adobe Commerce&quot;

**Quando ocorrer:** Durante qualquer estágio

**Causa:** credenciais de repositório do Adobe Commerce inválidas ou expiradas

**Soluções:**

Há duas opções recomendadas para resolver esse problema:

**Opção 1: Corrigir `env:COMPOSER_AUTH` variável de nível de ambiente (Recomendado)**

* Verifique se você configurou as credenciais corretas para `env:COMPOSER_AUTH`.
* Acesse a configuração global clicando no ícone de engrenagem na parte superior esquerda da interface do usuário do projeto na nuvem e selecione a guia **Variáveis**.
* Selecione _Disponível durante o tempo de compilação_ e desmarque _Disponível durante o tempo de execução_.

Se a Opção 1 não resolver seu problema, continue com a Opção 2.

**Opção 2: criar e implantar o arquivo `auth.json` manualmente**

* SSH no servidor.
* Recupere o conteúdo da variável `env:COMPOSER_AUTH` atual usando:\
  `echo $COMPOSER_AUTH`
* Copie todo o conteúdo da etapa acima (no formato JSON).
* Crie um novo arquivo chamado `auth.json` com este conteúdo.
* Confirme este arquivo `auth.json` recém-criado no diretório raiz do seu repositório.
* Acione uma nova implantação.

#### &quot;Permissões insuficientes para acessar o ambiente&quot;

**Quando ocorrer:** Durante a criação ou acesso do ambiente

**Causa:** sua conta de usuário não tem as permissões necessárias

**Soluções:**

* Verifique sua função de usuário e suas permissões
* Entre em contato com o administrador do sistema
* Verificar se você tem permissões de gerenciamento de ambiente
* Verifique se você tem permissões de implantação

### Erros de recursos e cotas

#### &quot;Cota de ambiente excedida&quot;

**Quando ocorrer:** Durante a criação do ambiente

**Causa:** Você atingiu seu limite de ambiente

**Soluções:**

* Desativar ambientes não utilizados
* Limpar ramificações e implantações antigas
* Entre em contato com o suporte para solicitar aumento de cota
* Considere atualizar seu plano

#### &quot;Recursos insuficientes para a operação&quot;

**Quando ocorrer:** Durante qualquer estágio

**Causa:** seu ambiente não tem CPU, memória ou armazenamento suficientes

**Soluções:**

* Verifique o uso de recursos do ambiente
* Liberar recursos limpando arquivos
* Aguardar a disponibilização de recursos
* Entre em contato com o suporte se os problemas de recurso persistirem

## Obtendo ajuda

**Quando contatar o suporte:**

Entre em contato com o suporte da Adobe Commerce Cloud quando:

* As mensagens de erro não são claras ou não têm detalhes suficientes
* Falha consistente nas operações de patch
* Você precisa de assistência para a resolução manual de conflitos
* As verificações de integridade falham, mas a causa não é aparente
* Você precisa de ajuda com problemas de sincronização do ambiente

**Informações a serem fornecidas:**

Ao entrar em contato com o suporte, forneça:

* **ID do projeto** - O identificador do projeto do Adobe Commerce Cloud
* **ID do Ambiente** - O ambiente específico onde o problema ocorreu
* **ID da Operação** - O identificador de operação [!DNL CAPS]
* **Detalhes do erro** - Concluir mensagens e logs de erro
* **Etapas a serem reproduzidas** - O que você estava fazendo quando ocorreu o erro
* **Tentativas anteriores** - O que você já tentou resolver

### Recursos adicionais

Para obter informações técnicas mais detalhadas:

* Revisar os logs de erros completos fornecidos com operações com falha
* Consulte a documentação do Adobe Commerce para obter orientação específica sobre patches
* Entre em contato com o suporte da Adobe Commerce Cloud para obter problemas específicos do ambiente

### Tópicos relacionados

* [Documentação da Adobe Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview)
* [Guia de Instalação do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview)
* [Introdução ao CAPS](intro.md)
* [Como acessar o](access.md)
* [Fluxo de trabalho (WRK)](workflow.md)
* [Práticas recomendadas](best-practices.md)
