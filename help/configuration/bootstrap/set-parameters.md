---
title: Definir o valor dos parâmetros de inicialização
description: Saiba como definir parâmetros de inicialização para o aplicativo do Commerce.
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# Parâmetros do Bootstrap

Este tópico demonstra como definir os valores dos parâmetros de inicialização do aplicativo do Commerce. Consulte [Visão geral da inicialização e inicialização do aplicativo](initialization.md).

A tabela a seguir discute os parâmetros de inicialização que você pode definir:

| Parâmetro do Bootstrap | Descrição |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Especifica o diretório personalizado e os caminhos de URL |
| MAGE_PROFILER | Ativa gráficos de dependência e criação de perfil do HTML |

>[!INFO]
>
>- Nem todos os parâmetros de inicialização estão documentados.
>- Agora você define o modo do aplicativo (desenvolvedor, padrão, produção) usando o comando [`magento deploy:mode:set {mode}`](../cli/set-mode.md).

## Definir parâmetros usando uma variável de ambiente

Esta seção discute como definir os valores dos parâmetros de inicialização usando variáveis de ambiente.

### Definir o modo do aplicativo

Você pode especificar variáveis de inicialização como variáveis de ambiente em todo o sistema, o que permite que todos os processos as usem.

Por exemplo, você pode usar a variável de ambiente do sistema `MAGE_PROFILER` para especificar um modo da seguinte maneira:

```
MAGE_PROFILER={firebug|csv|<custom value>}
```

Defina a variável usando um comando específico do shell. Como os shells têm sintaxe diferente, consulte uma referência como [unix.stackexchange.com][unix-stackx].

Exemplo de shell Bash para CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Se um `PHP Fatal error` for exibido no navegador depois que você definir um valor de criador de perfil, reinicie o servidor Web. O motivo pode estar relacionado ao cache de código de bytes do PHP, que armazena em cache códigos de bytes e classpaths do PHP.

## Definir parâmetros para o Apache ou o Nginx

Esta seção discute como especificar o modo para Apache ou Nginx.

### Configuração do Nginx

Consulte a [configuração de amostra do Nginx] no _GitHub_.

### Configuração do Apache .htaccess

Uma maneira de definir o modo de aplicativo é editando `.htaccess`. Dessa forma, não é necessário alterar as configurações do Apache.

Você pode modificar `.htaccess` em qualquer um dos locais a seguir, dependendo do seu ponto de entrada para o aplicativo do Commerce:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Para definir uma variável**:

1. Abra qualquer um dos arquivos anteriores em um editor de texto e adicione ou remova o comentário da configuração desejada.

   Por exemplo, para especificar um [modo](application-modes.md), remova o comentário do seguinte:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Defina o valor de `MAGE_PROFILER` para qualquer um dos seguintes:

   ```
   firebug
   csvfile
   <custom value>
   ```

1. Salve as alterações em `.htaccess`; não é necessário reiniciar o Apache para que a alteração tenha efeito.

### Configuração do Apache

O Apache Web Server dá suporte à configuração do modo de aplicativo usando diretivas `mod_env`.

A diretiva `mod_env` do Apache é um pouco diferente na [versão 2.2] e [versão 2.4] do Apache.

Os procedimentos a seguir mostram como definir o modo do aplicativo em um host virtual Apache. Esta não é a única maneira de usar diretivas `mod_env`; consulte a documentação do Apache para obter detalhes.

>[!TIP]
>
>A seção a seguir presume que você já configurou o host virtual. Caso contrário, consulte um recurso como o [este tutorial do DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Para especificar uma variável de inicialização para o Apache no Ubuntu**:

1. Como um usuário com privilégios `root`, abra o arquivo de configuração de host virtual em um editor de texto.

   Por exemplo, se o nome do host virtual for `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. Em qualquer lugar na configuração do host virtual, adicione a seguinte linha:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Por exemplo,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Salve as alterações e saia do editor de texto.
1. Ative o host virtual se ainda não tiver feito isso:

   ```bash
   a2ensite <virtual host config file name>
   ```

   Por exemplo,

   ```bash
   a2ensite my.magento.conf
   ```

1. Após definir o modo, reinicie o servidor Web:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>Esta seção pressupõe que você já configurou o host virtual. Caso contrário, consulte um recurso como o [este tutorial do DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Para especificar uma variável de inicialização para o Apache no CentOS**:

1. Como um usuário com privilégios `root`, abra o `/etc/httpd/conf/httpd.conf` em um editor de texto.

1. Em qualquer lugar na configuração do host virtual, adicione a seguinte linha:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Por exemplo,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Salve as alterações e saia do editor de texto.

1. Após definir o modo, reinicie o servidor Web:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache versão 2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache versão 2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Configuração de amostra do Nginx]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
