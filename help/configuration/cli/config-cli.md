---
title: Ferramenta de linha de comando
description: Use a ferramenta de linha de comando do Commerce para executar tarefas de instalação e configuração.
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Ferramenta de linha de comando

O Commerce tem uma interface de linha de comando (CLI) —`<magento_root>/bin/magento`—que executa tarefas de instalação e configuração, incluindo:

- Instalar o Commerce (e tarefas relacionadas, como atualizar o esquema do banco de dados, criar uma configuração de implantação)
- Limpeza do cache
- Gerenciamento de índices, incluindo a reindexação
- Criação de dicionários de tradução e pacotes de tradução
- Gerando classes inexistentes, como fábricas e interceptores para plug-ins, gerando a configuração de injeção de dependência para o gerenciador de objetos
- Implantação de arquivos de visualização estáticos
- Criação de CSS a partir de menos

Os benefícios adicionais incluem:

- Um único comando (`<magento_root>/bin/magento list`) lista todos os comandos de instalação e configuração disponíveis.
- Interface de usuário consistente com base no Symfony.
- A CLI é extensível para que desenvolvedores de terceiros possam se &quot;conectar&quot; a ela. Isso tem o benefício adicional de eliminar a curva de aprendizado dos usuários.
- Os comandos para módulos desativados não são exibidos.

Este tópico discute a configuração do software Adobe Commerce usando a CLI. Para obter informações sobre como instalar o Commerce, consulte [Fluxo de instalação](../../installation/overview.md) no _Guia de instalação_.

## Pré-requisitos

Antes de começar a usar a CLI, verifique se:

1. Seu sistema atende aos requisitos discutidos em [Requisitos do sistema](../../installation/system-requirements.md) no _Guia de instalação_.
1. Você concluiu todas as tarefas de pré-requisito discutidas em [Pré-requisitos](../../installation/prerequisites/overview.md) no _Guia de instalação_.
1. Depois de fazer logon no servidor do Commerce, alterne para um usuário que tenha permissões para gravar no sistema de arquivos do Commerce. Consulte [alternar para o proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md) no _Guia de instalação_.

## Execução de comandos

Para o shell bash, use a seguinte sintaxe para alternar para o proprietário do sistema de arquivos e insira o comando ao mesmo tempo:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Se o proprietário do sistema de arquivos não permitir logons, você poderá usar o seguinte:

```bash
sudo -u <file system owner> <command>
```

**Para executar comandos CLI de qualquer diretório**:

Adicionar `<magento_root>/bin` ao seu sistema `PATH`.

Exemplo de shell bash para CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

Como opção, você pode executar o seguinte:

- `cd <magento_root>/bin` e executá-los como `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` é um subdiretório do docroot do seu servidor Web
