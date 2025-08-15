---
title: Criar, editar ou desbloquear uma conta de administrador
description: Siga estas etapas para gerenciar a conta de administrador do seu aplicativo de Administrador do Adobe Commerce.
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Criar, editar ou desbloquear uma conta de administrador

Antes de usar esse comando, é necessário fazer o seguinte:

- [Criar a configuração de implantação](deployment.md)
- [Ative, no mínimo, os módulos Magento_Authorization e Magento_User](manage-modules.md)
- Criar o esquema de banco de dados

>[!NOTE]
>
>A maneira mais simples de criar o banco de dados é usar o comando `magento setup:upgrade`.

## Criar ou editar um administrador

Use este comando para criar um administrador ou editar um administrador existente.

>[!NOTE]
>
>Se você estiver editando um administrador, somente os `first name`, `last name` e `password` poderão ser editados.

Uso do comando:

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

Onde a tabela a seguir define parâmetros e valores:

| Nome | Valor | Obrigatório? |
|--- |--- |--- |
| `--admin-firstname` | Nome do usuário administrador. | Sim |
| `--admin-lastname` | Sobrenome do usuário administrador. | Sim |
| `--admin-email` | Endereço de email do usuário administrador. | Sim |
| `--admin-user` | Nome de usuário do administrador. | Sim |
| `--admin-password` | Senha de usuário administrador. A senha deve ter pelo menos 7 caracteres e incluir pelo menos um caractere alfabético e um caractere numérico. <br><br>Recomendamos uma senha mais longa e complexa. Se a string de senha contiver caracteres especiais que exigem interpretação literal (como barras invertidas ou espaços), coloque a senha entre aspas simples. | Sim |
| `--magento-init-params` | Adicione a qualquer comando para personalizar parâmetros de inicialização de aplicativo<br/><br/>Por exemplo: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Não |

Exemplo de uso:

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```
Created Magento administrator user named j.doe
```

Se você não especificar nenhum dos parâmetros obrigatórios, o aplicativo perguntará sobre eles na CLI:

```bash
bin/magento admin:user:create
```

```
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```
Created Magento administrator user named John
```

O exemplo a seguir atualiza `first name`, `last name` e `password` de `j.doe` usuário administrador:

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```
Created Magento administrator user named j.doe
```

## Desbloquear uma conta de administrador

Use esse comando para desbloquear a conta de um administrador que foi bloqueada, normalmente devido a várias tentativas de logon incorretas.

```bash
bin/magento admin:user:unlock {username}
```

Você deve especificar o nome de usuário do administrador. Exemplo:

```bash
bin/magento admin:user:unlock admin
```

```
The user account "admin" has been unlocked
```

Se a conta não estiver desbloqueada ou se houver um problema, a seguinte mensagem será exibida:

```
The user account "admin" was not locked or could not be unlocked
```

Verifique se o usuário é um administrador, se está ativo e se a conta está bloqueada. Para exibir a lista de usuários bloqueados no Admin, faça logon como administrador e clique em **Sistema** > **Permissões** > **Usuários bloqueados**.

Se a conta não existir, a seguinte mensagem será exibida:

```
Couldn't find the user account "bob"
```
