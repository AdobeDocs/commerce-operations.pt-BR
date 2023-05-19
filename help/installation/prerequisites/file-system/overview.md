---
title: Propriedade e permissões do arquivo
description: Saiba mais sobre a importância das permissões do sistema de arquivos ao trabalhar com instalações locais do Adobe Commerce e do Magento Open Source.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# Propriedade e permissões do arquivo

É importante proteger sua instalação do Adobe Commerce ou do Magento Open Source em um ambiente de desenvolvimento para ajudar a evitar problemas relacionados a pessoas ou processos não autorizados que acessam o sistema e podem prejudicá-lo. Use as seguintes diretrizes de propriedade e permissões do sistema de arquivos para proteger sua instalação.

## Proprietário do sistema de arquivos

O proprietário do sistema de arquivos é um usuário que possui e mantém permissões de gravação para arquivos no sistema de arquivos.

Há dois tipos de proprietários de sistemas de arquivos:

- **Hospedagem compartilhada com um único usuário**

   Os provedores de hospedagem compartilhada permitem fazer logon no servidor de aplicativos como um usuário. Como usuário único, você pode fazer logon, transferir arquivos por FTP e executar o servidor Web. Você tem a opção de configurar um [`umask`](#restrict-access-with-a-umask) para restringir ainda mais o acesso, especialmente em um ambiente de produção.

- **Hospedagem privada com dois usuários**

   A hospedagem privada é útil se você gerenciar um servidor de aplicativos. Cada usuário tem uma responsabilidade específica:

   - A variável _usuário do servidor da web_ O executa o Administrador e a loja.

   - A variável _usuário da linha de comando_ executa tarefas cron e utilitários de linha de comando.
   Ambos os usuários exigem as mesmas permissões para o sistema de arquivos, portanto, é melhor usar um [grupo compartilhado](configure-permissions.md#set-ownership-and-permissions-for-two-users) e defina uma [`umask`](#restrict-access-with-a-umask).

### Restringir o acesso com uma máscara

Para aumentar a segurança, principalmente em um ambiente de produção em um sistema de hospedagem compartilhado, você pode usar `umask` para restringir o acesso. A `umask`—também referido como _máscara de criação do sistema de arquivos_—é um conjunto de bits que controla como as permissões de arquivo são definidas para arquivos recém-criados.

>[!WARNING]
>
>A segurança do sistema de arquivos é complexa e importante. É altamente recomendável que você consulte um administrador de sistema ou administrador de rede experiente antes de decidir o nível de permissões a serem definidas. Fornecemos um mecanismo para você usar, mas criar uma estratégia de permissões é sua responsabilidade.

O Adobe Commerce e o Magento Open Source usam uma máscara padrão de três bits: `002`. Subtraia a máscara padrão dos padrões UNIX de 666 para arquivos e 777 para diretórios.

Por exemplo:

- **775 para diretórios**—Controle total pelo usuário, controle total pelo grupo e permite que todos atravessem o diretório. Normalmente, essas permissões são exigidas por provedores de hospedagem compartilhados.

- **664 para arquivos**—Gravável pelo usuário, gravável pelo grupo e somente leitura para todos os outros.

Para obter mais informações sobre como criar uma `magento_umask` arquivo, consulte [Definir uma máscara](../../next-steps/set-umask.md).

## Modos de permissões, propriedade e aplicativo

Recomendamos permissões e propriedade diferentes quando você usa os diferentes modos de aplicativo Adobe Commerce e Magento Open Source:

- Padrão
- Desenvolvedor
- Produção

Consulte [Sobre modos](../../../configuration/bootstrap/application-modes.md) no _Guia de configuração_.

Abordamos ainda mais as recomendações de permissões no [Permissões de acesso a sistemas de arquivos](../../../configuration/deployment/file-system-permissions.md) no _Guia de configuração_.

>[!TIP]
>
>Antes de instalar o Adobe Commerce ou o Magento Open Source, consulte [Configurar a propriedade e as permissões do arquivo](configure-permissions.md).
