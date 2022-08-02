---
title: Ferramenta Linha de comando
description: Use a ferramenta de linha de comando do Commerce para executar tarefas de instalação e configuração.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Ferramenta Linha de comando

O Commerce tem uma interface de linha de comando (CLI)—`<magento_root>/bin/magento`—que executa tarefas de instalação e configuração, incluindo:

- Instalar o Commerce (e tarefas relacionadas, como atualizar o esquema do banco de dados, criar uma configuração de implantação)
- Limpar o cache
- Gerenciamento de índices, incluindo reindexação
- Criação de dicionários de tradução e pacotes de tradução
- Geração de classes inexistentes, como fábricas e interceptores para plug-ins, gerando a configuração de injeção de dependência para o gerenciador de objetos
- Implantação de arquivos de visualização estáticos
- Criando CSS de Menos

Os benefícios adicionais incluem:

- Um único comando (`<magento_root>/bin/magento list`) lista todos os comandos de instalação e configuração disponíveis.
- Interface de usuário consistente com base em Simfonia.
- A CLI é extensível para que desenvolvedores de terceiros possam &quot;conectar-se&quot; a ela. Isso tem o benefício adicional de eliminar a curva de aprendizado dos usuários.
- Os comandos para módulos desativados não são exibidos.

Este tópico discute a configuração do software Adobe Commerce e Magento Open Source usando a CLI. Para obter informações sobre como instalar o Commerce, consulte [Visão geral da instalação](https://devdocs.magento.com/guides/2.4/install-gde/bk-install-guide.html) no _Guia de instalação_.

## Pré-requisitos

Antes de começar a usar a CLI, verifique se:

1. Seu sistema atende aos requisitos discutidos no [Requisitos do sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) no _Guia de instalação_.
1. Você concluiu todas as tarefas de pré-requisito discutidas em [Pré-requisitos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/prereq-overview.html) no _Guia de instalação_.
1. Depois de fazer logon no servidor do Commerce, mude para um usuário com permissões para gravar no sistema de arquivos do Commerce. Consulte [mudar para o proprietário do sistema de ficheiros](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) no _Guia de instalação_.

## Execução de comandos

Para o shell bash, use a seguinte sintaxe para alternar para o proprietário do sistema de arquivos e inserir o comando ao mesmo tempo:

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

- `cd <magento_root>/bin` e execute-os como `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` é um subdiretório do docroot do servidor da Web
