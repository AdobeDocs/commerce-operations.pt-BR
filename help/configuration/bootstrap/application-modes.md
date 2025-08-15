---
title: Modos de aplicação
description: O aplicativo Commerce pode operar em diferentes modos, dependendo das suas necessidades. Exibir uma lista detalhada dos modos de aplicação disponíveis.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: c415c3427f513255b9d4ebe1d24ba4024df21928
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Modos de aplicação

Você pode executar o aplicativo Commerce em qualquer um dos _modos_ a seguir:

| Nome do modo | Descrição | Suporte na nuvem |
| ------------------------ | ------------------- | ------------- |
| [padrão](#default-mode) | Implante e execute o aplicativo do Commerce em um único servidor sem alterar as configurações. _Não_ otimizado para produção. | não |
| [desenvolvedor](#developer-mode) | Ideal para desenvolvimento ao estender ou personalizar o aplicativo do Commerce. | não |
| [produção](#production-mode) | Implante e execute o aplicativo do Commerce em um sistema de produção. | Sim |
| [manutenção](#maintenance-mode) | Impeça o acesso a um site ao executar atualizações e configurações. | Sim |

Consulte [Definir o modo de operação](../cli/set-mode.md) para saber como alterar manualmente os modos de operação do Adobe Commerce.

## Suporte na nuvem

Devido ao sistema de arquivos somente leitura, há uma restrição estrita contra a alteração dos modos em ambientes de nuvem remotos e ele não pode ser substituído pelo Suporte da Adobe Commerce. Não tente alterar os modos modificando o arquivo `app/etc/env.php` porque o pacote `ece-tools` substitui o arquivo com base em várias fontes de configuração.

A infraestrutura do Adobe Commerce na nuvem executa automaticamente o aplicativo no modo de _manutenção_ durante uma implantação, o que coloca o site offline até que a implantação seja concluída. Caso contrário, o aplicativo permanecerá no modo de _produção_. Consulte [Processo de implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) no _guia do Commerce on Cloud Infrastructure_.

Se você usa o Cloud Docker para Commerce como uma ferramenta de desenvolvimento, é possível implantar seu projeto de infraestrutura em nuvem em um ambiente do Docker no modo _desenvolvedor_, mas o desempenho é mais lento devido a operações adicionais de sincronização de arquivos. Consulte [Implantar o ambiente do Docker](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) no _Guia do Cloud Docker for Commerce_.


## Modo padrão

O modo _padrão_ permite implantar o aplicativo Commerce em um único servidor sem alterar as configurações. No entanto, o modo padrão não é otimizado para produção devido ao impacto adverso no desempenho de arquivos estáticos. Criar arquivos estáticos e armazená-los em cache tem um impacto maior no desempenho do que gerá-los usando a ferramenta de criação de arquivos estáticos.

No modo padrão:

- As exceções são gravadas nos arquivos de log, em vez de serem exibidas
- Arquivos de visualização estáticos são armazenados em cache
- Oculta cabeçalhos personalizados de solicitação e resposta HTTP `X-Magento-*`

O Commerce opera no modo padrão se nenhum outro modo for especificado.

## Modo de desenvolvedor

O modo _desenvolvedor_ é recomendado para estender e personalizar o aplicativo do Commerce. Os arquivos de exibição estáticos não são armazenados em cache, mas gravados no diretório `pub/static` sob demanda.

No modo de desenvolvedor:

- Habilita a [compilação automática de código](../cli/code-compiler.md) e depuração avançada
- As exceções não capturadas são exibidas no navegador
- O logon do sistema em `var/report` é explícito
- Uma exceção é lançada no manipulador de erros, em vez de ser registrada
- Uma exceção é lançada quando um assinante de evento não pode ser chamado
- Mostra cabeçalhos personalizados de solicitação e resposta HTTP `X-Magento-*`

>[!NOTE]
>
>Esse modo não é compatível com o ambiente da Adobe Commerce Cloud e o Suporte da Adobe Commerce não pode facilitar a alteração do modo do aplicativo.

## Modo de produção

O modo de _produção_ é melhor para implantar o aplicativo Commerce em um sistema de produção. Depois de otimizar o ambiente de servidor, como o banco de dados e o servidor Web, execute a [ferramenta de implantação de arquivos de exibição estática](../cli/static-view-file-deployment.md) para gravar arquivos de exibição estática no diretório `pub/static`. Isso melhora o desempenho, fornecendo todos os arquivos estáticos necessários na implantação, em vez de forçar o aplicativo Commerce a localizar e copiar dinamicamente arquivos estáticos (materializar) sob demanda durante o tempo de execução.

Alguns campos, como as seções Avançado e Configuração do sistema do desenvolvedor no Administrador, não estão disponíveis no modo de produção. Por exemplo, você _não pode_ habilitar ou desabilitar tipos de cache usando o Administrador. Você pode habilitar e desabilitar tipos de cache _somente_ usando a [linha de comando](../cli/manage-cache.md#config-cli-subcommands-cache-en).

No modo de produção:

- Os arquivos de visualização estáticos são servidos somente a partir do cache
- Erros e exceções são registrados no sistema de arquivos e nunca são exibidos ao usuário
- Alguns campos de configuração no Administrador não estão disponíveis

## Modo de manutenção

O modo de _manutenção_ limita ou impede o acesso a um site durante tarefas de melhorias, atualizações e configuração. Por padrão, o site redireciona os visitantes para uma página `Service Temporarily Unavailable` padrão.

Você pode criar uma [página de manutenção personalizada](../../upgrade/troubleshooting/maintenance-mode-options.md), habilitar e desabilitar manualmente o modo de manutenção e configurar o modo de manutenção para permitir que os visitantes de endereços IP autorizados vejam o armazenamento normalmente. Consulte [habilitar e desabilitar o modo de manutenção](../../installation/tutorials/maintenance-mode.md) no _Guia de Instalação_.

Se você estiver usando o Commerce na infraestrutura em nuvem, o aplicativo do Commerce será executado no modo de manutenção durante a fase de implantação. Quando a implantação é concluída com sucesso, o aplicativo do Commerce volta a ser executado no modo de produção. Consulte [Ganchos de implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) no _guia do Commerce on Cloud Infrastructure_.

No modo de manutenção:

- Os visitantes do site são redirecionados para uma página padrão de `Service Temporarily Unavailable`
- O diretório `var/` contém o arquivo `.maintenance.flag`
- É possível limitar o acesso de visitantes com base em endereços IP
