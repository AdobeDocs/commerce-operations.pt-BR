---
title: Propriedade e permissões do arquivo
description: Saiba mais sobre a importância das permissões do sistema de arquivos ao trabalhar com instalações locais do Adobe Commerce.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Propriedade e permissões do arquivo

É importante proteger a instalação do Adobe Commerce em um ambiente de desenvolvimento para ajudar a evitar problemas relacionados a pessoas ou processos não autorizados que acessam o sistema e podem prejudicá-lo. Use as seguintes diretrizes de propriedade e permissões do sistema de arquivos para proteger sua instalação.

## Proprietário do sistema de arquivos

O proprietário do sistema de arquivos é um usuário que possui e mantém permissões de gravação para arquivos no sistema de arquivos.

Há dois tipos de proprietários de sistemas de arquivos:

- **Hospedagem compartilhada com um único usuário**

  Os provedores de hospedagem compartilhada permitem fazer logon no servidor de aplicativos como um usuário. Como usuário único, você pode fazer logon, transferir arquivos por FTP e executar o servidor Web. Você tem a opção de configurar um [`umask`](#restrict-access-with-a-umask) para restringir ainda mais o acesso, particularmente em um ambiente de produção.

- **Hospedagem privada com dois usuários**

  A hospedagem privada é útil se você gerenciar um servidor de aplicativos. Cada usuário tem uma responsabilidade específica:

   - O _usuário do servidor Web_ executa o Administrador e a loja.

   - O _usuário da linha de comando_ executa trabalhos cron e utilitários de linha de comando.

  Ambos os usuários exigem as mesmas permissões para o sistema de arquivos, portanto, é melhor usar um [grupo compartilhado](configure-permissions.md#set-ownership-and-permissions-for-two-users) e definir um [`umask`](#restrict-access-with-a-umask).

### Restringir o acesso com uma máscara

Para aumentar a segurança, principalmente em um ambiente de produção em um sistema de hospedagem compartilhado, você pode usar o `umask` para restringir o acesso. Uma `umask` — também conhecida como _máscara de criação do sistema de arquivos_ — é um conjunto de bits que controla como as permissões de arquivos são definidas para arquivos recém-criados.

>[!WARNING]
>
>A segurança do sistema de arquivos é complexa e importante. É altamente recomendável que você consulte um administrador de sistema ou administrador de rede experiente antes de decidir o nível de permissões a serem definidas. Fornecemos um mecanismo para você usar, mas criar uma estratégia de permissões é sua responsabilidade.

O Adobe Commerce usa uma máscara padrão de três bits: `002`. Subtraia a máscara padrão dos padrões UNIX de 666 para arquivos e 777 para diretórios.

Por exemplo:

- **775 para diretórios**—Controle total pelo usuário, controle total pelo grupo e permite que todos naveguem pelo diretório. Normalmente, essas permissões são exigidas por provedores de hospedagem compartilhados.

- **664 para arquivos**—Gravável pelo usuário, gravável pelo grupo e somente leitura para todos os outros.

Para obter mais informações sobre como criar um arquivo `magento_umask`, consulte [Definir uma máscara](../../next-steps/set-umask.md).

## Modos de permissões, propriedade e aplicativo

Recomendamos permissões e propriedade diferentes ao usar os diferentes modos de aplicativo do Adobe Commerce:

- Padrão
- Desenvolvedor
- Produção

Consulte [Sobre modos](../../../configuration/bootstrap/application-modes.md) no _Guia de configuração_.

Abordamos ainda mais as recomendações de permissões em [Permissões de acesso a sistemas de arquivos](../../../configuration/deployment/file-system-permissions.md) no _Guia de configuração_.

>[!TIP]
>
>Antes de instalar o Adobe Commerce, consulte [Configurar propriedade e permissões de arquivos](configure-permissions.md).
