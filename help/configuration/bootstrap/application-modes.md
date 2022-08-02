---
title: Modos de aplicativo
description: O aplicativo Commerce pode operar em modos diferentes dependendo de suas necessidades. Exiba uma lista detalhada dos modos de aplicativo disponíveis.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# Modos de aplicativo

Você pode executar o aplicativo Commerce em qualquer um dos seguintes _modos_:

| Nome do módulo | Descrição |
| ----------- | ----------- |
| default | Permite implantar o aplicativo do Commerce em um único servidor sem alterar as configurações. No entanto, o modo padrão não é otimizado para produção.<br>Para implantar o aplicativo Commerce em mais de um servidor ou otimizá-lo para produção, altere para um dos outros modos.<ul><li>O armazenamento em cache do arquivo de visualização estática está ativado</li><li>As exceções não são exibidas para o usuário; em vez disso, as exceções são gravadas em arquivos de log.</li><li>Oculta personalizado `X-Magento-*` Cabeçalhos de solicitação e resposta HTTP</li></ul> |
| desenvolvedor | Destinado apenas ao desenvolvimento, este modo:<ul><li>Desativa o armazenamento em cache de arquivos de visualização estática</li><li>Fornece registro detalhado</li><li>Habilitar [compilação automática de código](../cli/code-compiler.md)</li><li>Habilita a depuração aprimorada</li><li>Mostra personalizados `X-Magento-*` Cabeçalhos de solicitação e resposta HTTP</li><li>Resultados no desempenho mais lento</li><li>Mostra erros no frontend</li></ul> |
| produção | Destina-se à implantação em um sistema de produção, este modo:<ul><li>Não mostra exceções para o usuário (as exceções são gravadas somente em logs).</li><li>Serve arquivos de visualização estáticos somente do cache.</li><li>Impede a compilação automática do arquivo de código. Arquivos novos ou atualizados não são gravados no sistema de arquivos.</li><li>**Não permite ativar ou desativar tipos de cache no Administrador.** Consulte [ativação e desativação do cache](../cli/manage-cache.md#enable-or-disable-cache-types).</li><li>Alguns campos, como as seções Advanced e Developer system configuration no Admin, não estão disponíveis no modo de produção.</li></ul> |
| manutenção | Destinado a impedir o acesso a um site enquanto ele está sendo atualizado ou reconfigurado, este modo:<ul><li>Redireciona os visitantes do site para um padrão `Service Temporarily Unavailable` página.</li><li>Quando o site está em modo de manutenção, a variável `var/` O diretório contém o `.maintenance.flag` arquivo.</li><li>Você pode configurar o modo de manutenção para permitir o acesso do visitante a partir de uma lista especificada de endereços IP.</li></ul> |

>[!INFO]
>
>[Adobe Commerce na infraestrutura de nuvem](https://devdocs.magento.com/cloud/bk-cloud.html) suporta apenas os modos de produção e manutenção.

## Modo padrão

Como seu nome implica, o modo padrão é como o Commerce opera se nenhum outro modo for especificado. O modo padrão permite implantar o aplicativo Commerce em um único servidor sem alterar nenhuma configuração. No entanto, o modo padrão não é tão otimizado para produção quanto o modo de produção.

Para implantar o aplicativo Commerce em mais de um servidor ou otimizá-lo para produção, altere para um dos outros modos.

No modo padrão:

- Erros são registrados nos relatórios de arquivo no servidor e nunca são mostrados a um usuário
- Os arquivos de visualização estáticos são armazenados em cache
- O modo padrão não é otimizado para um ambiente de produção, principalmente devido ao impacto negativo no desempenho de [arquivos estáticos](https://glossary.magento.com/static-files) ser gerado dinamicamente em vez de materializado. Em outras palavras, criar arquivos estáticos e armazená-los em cache tem um impacto maior no desempenho do que gerá-los usando a ferramenta de criação de arquivos estáticos.

Consulte [Definir o modo de operação](../cli/set-mode.md).

## Modo de desenvolvedor

Execute o aplicativo Commerce no modo desenvolvedor quando estiver estendendo-o ou personalizando-o.

No modo de desenvolvedor:

- Os arquivos de visualização estáticos não são armazenados em cache; são escritas para a `pub/static` diretório sempre que forem chamados
- Exceções não capturadas são exibidas no navegador
- Logon do sistema `var/report` é verboso
- Um [exceção](https://glossary.magento.com/exception) é lançado no manipulador de erros, em vez de ser registrado
- Uma exceção é lançada quando uma [evento](https://glossary.magento.com/event) o assinante não pode ser chamado

Consulte [Definir o modo de operação](../cli/set-mode.md).

## Modo de produção

Execute o Commerce no modo de produção quando ele for implantado em um servidor de produção. Após otimizar o ambiente do servidor, como o banco de dados e o servidor da Web, execute o [ferramenta de implantação de arquivos de visualização estática](../cli/static-view-file-deployment.md) para gravar arquivos de visualização estáticos no `pub/static` diretório.

Isso melhora o desempenho fornecendo todos os arquivos estáticos necessários na implantação, em vez de forçar o Commerce a localizar e copiar (materializar) dinamicamente arquivos estáticos sob demanda durante o tempo de execução.

No modo de produção:

- Os arquivos de view estática não são materializados e os URLs para eles são compostos dinamicamente. Os arquivos de visualização estáticos são distribuídos a partir do [cache](https://glossary.magento.com/cache) somente.
- Erros são registrados no sistema de arquivos e nunca são exibidos ao usuário.
- Você pode ativar e desativar tipos de cache _only_ usando o [linha de comando](../cli/manage-cache.md#config-cli-subcommands-cache-en).
- Você _cannot_ ative ou desative os tipos de cache usando o Administrador.

## Modo de manutenção

Execute o aplicativo Commerce no modo de manutenção para colocar seu site off-line enquanto você conclui as tarefas de manutenção, atualização ou configuração. No modo de manutenção, o site redireciona os visitantes para um padrão `Service Temporarily Unavailable` página.

Você pode criar um [página de manutenção personalizada](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html), ative e desative manualmente o modo de manutenção e configure o modo de manutenção para permitir que os visitantes de endereços IP autorizados visualizem a loja normalmente. Consulte [ativar e desativar o modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

Se você estiver usando o Commerce on cloud Infrastructure, o aplicativo Commerce será executado no modo de manutenção durante a fase de implantação. Quando a implantação é concluída com êxito, o aplicativo Commerce volta a ser executado no modo de produção. Consulte [Ganchos de implantação](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-hook) no _guia Commerce Cloud_.
