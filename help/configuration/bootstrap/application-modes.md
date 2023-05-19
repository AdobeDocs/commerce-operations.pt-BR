---
title: Modos de aplicação
description: O aplicativo Commerce pode operar em diferentes modos, dependendo das suas necessidades. Exibir uma lista detalhada dos modos de aplicação disponíveis.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# Modos de aplicação

Você pode executar o aplicativo Commerce em qualquer uma das seguintes opções _modos_:

| Nome do modo | Descrição | Suporte na nuvem |
| ------------------------ | ------------------- | ------------- |
| [padrão](#default-mode) | Implante e execute o aplicativo Commerce em um único servidor sem alterar as configurações. _Não_ otimizado para produção. | não |
| [desenvolvedor](#developer-mode) | Ideal para desenvolvimento ao estender ou personalizar o aplicativo Commerce. | não |
| [produção](#production-mode) | Implante e execute o aplicativo Commerce em um sistema de produção. | Sim |
| [manutenção](#maintenance-mode) | Impeça o acesso a um site ao executar atualizações e configurações. | Sim |

Consulte [Definir o modo de operação](../cli/set-mode.md) para saber como alterar manualmente os modos de operação do Adobe Commerce.

## Suporte na nuvem

Não há necessidade de gerenciar os modos de aplicativo para um projeto de infraestrutura em nuvem. Devido ao sistema de arquivos somente leitura, não é possível alterar os modos nos ambientes de nuvem remotos. O Adobe Commerce na infraestrutura em nuvem executa automaticamente o aplicativo no _manutenção_ durante uma implantação, o que coloca o site offline até que a implantação seja concluída. Caso contrário, a aplicação _produção_ modo. Consulte [Processo de implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) no _Guia do Commerce na infraestrutura em nuvem_.

Se você usa o Cloud Docker for Commerce como uma ferramenta de desenvolvimento, é possível implantar seu projeto de infraestrutura em nuvem em um ambiente do Docker no _desenvolvedor_ mas o desempenho é mais lento devido a operações adicionais de sincronização de arquivos. Consulte [Implantar o ambiente do Docker](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) no _Guia do Cloud Docker for Commerce_.

## Modo padrão

A variável _padrão_ permite implantar o aplicativo Commerce em um único servidor sem alterar nenhuma configuração. No entanto, o modo padrão não é otimizado para produção devido ao impacto adverso no desempenho de arquivos estáticos. Criar arquivos estáticos e armazená-los em cache tem um impacto maior no desempenho do que gerá-los usando a ferramenta de criação de arquivos estáticos.

No modo padrão:

- As exceções são gravadas nos arquivos de log, em vez de serem exibidas
- Arquivos de visualização estáticos são armazenados em cache
- Oculta personalizado `X-Magento-*` Cabeçalhos de solicitação e resposta HTTP

O Commerce opera no modo padrão se nenhum outro modo for especificado.

## Modo de desenvolvedor

A variável _desenvolvedor_ é recomendado para estender e personalizar o aplicativo Commerce. Os arquivos de visualização estáticos não são armazenados em cache, mas gravados no `pub/static` diretório sob demanda.

No modo de desenvolvedor:

- Habilita [compilação automática de código](../cli/code-compiler.md) e depuração avançada
- As exceções não capturadas são exibidas no navegador
- Logon do sistema `var/report` é explícito
- Uma exceção é lançada no manipulador de erros, em vez de ser registrada
- Uma exceção é lançada quando um assinante de evento não pode ser chamado
- Mostra personalizado `X-Magento-*` Cabeçalhos de solicitação e resposta HTTP

## Modo de produção

A variável _produção_ é melhor para implantar o aplicativo Commerce em um sistema de produção. Depois de otimizar o ambiente de servidor, como o banco de dados e o servidor Web, você deve executar o [ferramenta de implantação de arquivos de visualização estática](../cli/static-view-file-deployment.md) para gravar arquivos de visualização estáticos no `pub/static` diretório. Isso melhora o desempenho, fornecendo todos os arquivos estáticos necessários na implantação, em vez de forçar o aplicativo Commerce a localizar e copiar dinamicamente arquivos estáticos (materializar) sob demanda durante o tempo de execução.

Alguns campos, como as seções Avançado e Configuração do sistema do desenvolvedor no Administrador, não estão disponíveis no modo de produção. Por exemplo, você _não é possível_ ative ou desative os tipos de cache usando o Administrador. Você pode ativar e desativar os tipos de cache _somente_ usando o [linha de comando](../cli/manage-cache.md#config-cli-subcommands-cache-en).

No modo de produção:

- Os arquivos de visualização estáticos são servidos somente a partir do cache
- Erros e exceções são registrados no sistema de arquivos e nunca são exibidos ao usuário
- Alguns campos de configuração no Administrador não estão disponíveis

## Modo de manutenção

A variável _manutenção_ limita ou impede o acesso a um site durante tarefas de melhorias, atualizações e configuração. Por padrão, o site redireciona os visitantes para um local `Service Temporarily Unavailable` página.

Você pode criar um [página de manutenção personalizada](../../upgrade/troubleshooting/maintenance-mode-options.md), habilite e desabilite manualmente o modo de manutenção e configure o modo de manutenção para permitir que os visitantes de endereços IP autorizados vejam o armazenamento normalmente. Consulte [ativar e desativar modo de manutenção](../../installation/tutorials/maintenance-mode.md) no _Guia de instalação_.

Se você estiver usando o Commerce na infraestrutura em nuvem, o aplicativo do Commerce será executado no modo de manutenção durante a fase de implantação. Quando a implantação é concluída com sucesso, o aplicativo Commerce retorna ao modo de produção. Consulte [Ganchos de implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) no _Guia do Commerce na infraestrutura em nuvem_.

No modo de manutenção:

- Os visitantes do site são redirecionados para um padrão `Service Temporarily Unavailable` página
- A variável `var/` o diretório contém o `.maintenance.flag` arquivo
- É possível limitar o acesso de visitantes com base em endereços IP
