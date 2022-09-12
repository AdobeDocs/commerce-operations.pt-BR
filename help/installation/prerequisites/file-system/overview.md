---
title: Propriedade e permissões de arquivos
description: Saiba mais sobre a importância das permissões do sistema de arquivos ao trabalhar com instalações locais do Adobe Commerce e Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Propriedade e permissões de arquivos

É importante proteger sua instalação do Adobe Commerce ou Magento Open Source em um ambiente de desenvolvimento para ajudar a evitar problemas relacionados a pessoas ou processos não autorizados que acessam — e podem prejudicar — seu sistema. Use as seguintes diretrizes de propriedade e permissões do sistema de arquivos para proteger sua instalação.

## Proprietário do sistema de arquivos

O proprietário do sistema de arquivos é um usuário que possui e retém permissões de gravação para arquivos no sistema de arquivos.

Há dois tipos de proprietários de sistemas de arquivos:

- **Hospedagem compartilhada com um único usuário**

   Os provedores de hospedagem compartilhada permitem fazer logon no servidor de aplicativos como um usuário. Como um único usuário, você pode fazer logon, transferir arquivos usando FTP e executar o servidor da Web. Você tem a opção de definir uma [`umask`](#restrict-access-with-a-umask) para restringir ainda mais o acesso, especialmente em um ambiente de produção.

- **Hospedagem privada com dois usuários**

   A hospedagem privada é útil se você gerenciar um servidor de aplicativos. Cada usuário tem uma responsabilidade específica:

   - O _usuário do servidor da web_ executa o Admin e a loja.

   - O _usuário da linha de comando_ executa trabalhos cron e utilitários de linha de comando.
   Ambos os usuários exigem as mesmas permissões do sistema de arquivos, portanto, é melhor usar um [grupo compartilhado](configure-permissions.md#set-ownership-and-permissions-for-two-users) e defina uma [`umask`](#restrict-access-with-a-umask).

### Restringir o acesso com uma máscara

Para aumentar a segurança, especialmente em um ambiente de produção em um sistema de hospedagem compartilhado, você pode usar `umask` para restringir o acesso. A `umask`—igualmente designadas por _máscara de criação do sistema de arquivos_—é um conjunto de bits que controla como as permissões do arquivo são definidas para arquivos recém-criados.

>[!WARNING]
>
>A segurança do sistema de arquivos é complexa e importante. Recomendamos que você consulte um administrador de sistema ou um administrador de rede experiente antes de decidir o nível de permissões a serem definidas. Fornecemos um mecanismo para você usar, mas a criação de uma estratégia de permissões é sua responsabilidade.

Adobe Commerce e Magento Open Source usam uma máscara padrão de três bits: `002`. Subtraia a máscara padrão dos padrões UNIX 666 para arquivos e 777 para diretórios.

Por exemplo:

- **775 para diretórios**—Controle completo pelo usuário, controle total pelo grupo e permite que todos percorram o diretório. Normalmente, essas permissões são exigidas por provedores de hospedagem compartilhada.

- **664 para arquivos**—Gravável pelo usuário, gravável pelo grupo e somente leitura para todos os outros.

Para obter mais informações sobre como criar um `magento_umask` arquivo, consulte [Definir uma máscara](../../next-steps/set-umask.md).

## Permissões, propriedade e modos de aplicativo

Recomendamos permissões e propriedade diferentes quando você usa diferentes modos de aplicativo Adobe Commerce e Magento Open Source:

- Padrão
- Desenvolvedor
- Produção

Consulte [Sobre modos](../../../configuration/bootstrap/application-modes.md) no _Guia de configuração_.

Além disso, discutimos as recomendações de permissões no [Permissões de acesso aos sistemas de arquivos](../../../configuration/deployment/file-system-permissions.md) no _Guia de configuração_.

>[!TIP]
>
>Antes de instalar o Adobe Commerce ou o Magento Open Source, analise [Configurar a propriedade e as permissões do arquivo](configure-permissions.md).
