---
title: Definir o valor dos parâmetros de inicialização
description: Saiba como definir parâmetros de inicialização para o aplicativo Commerce.
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# parâmetros de Bootstrap

Este tópico demonstra como definir os valores dos parâmetros de inicialização de aplicativos do Commerce. Consulte [Visão geral da inicialização e bootstrapping do aplicativo](initialization.md).

A tabela a seguir discute os parâmetros de inicialização que você pode definir:

| parâmetro Bootstrap | Descrição |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Especifica o diretório personalizado e os caminhos de URL |
| MAGE_PROFILER | Ativa gráficos de dependência e criação de perfil de HTML |

>[!INFO]
>
>- Nem todos os parâmetros de inicialização estão documentados.
>- Agora, defina o modo do aplicativo (desenvolvedor, padrão, produção) usando a variável [`magento deploy:mode:set {mode}`](../cli/set-mode.md) comando.


## Definir parâmetros usando uma variável de ambiente

Esta seção discute como definir os valores dos parâmetros de inicialização usando variáveis de ambiente.

### Definir o modo do aplicativo

Você pode especificar variáveis de inicialização como variáveis de ambiente em todo o sistema, o que permite que todos os processos as usem.

Por exemplo, você pode usar a variável `MAGE_PROFILER` system environment variable para especificar um modo da seguinte maneira:

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

Defina a variável usando um comando específico do shell. Como os shells têm sintaxe diferente, consulte uma referência como [unix.stackexchange.com][unix-stackx].

Exemplo de shell Bash para CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Se um `PHP Fatal error` for exibido no navegador depois que você definir um valor de profiler, reinicie o servidor Web. O motivo pode estar relacionado ao cache de código de bytes do PHP, que armazena em cache códigos de bytes e classpaths do PHP.

## Definir parâmetros para o Apache ou o Nginx

Esta seção discute como especificar o modo para Apache ou Nginx.

### Configuração do Nginx

Consulte a [Configuração de amostra do Nginx] em _GitHub_.

### Configuração do Apache .htaccess

Uma maneira de definir o modo do aplicativo é editando `.htaccess`. Dessa forma, não é necessário alterar as configurações do Apache.

Você pode modificar `.htaccess` em qualquer um dos seguintes locais, dependendo do seu ponto de entrada para o aplicativo Commerce:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Para definir uma variável**:

1. Abra qualquer um dos arquivos anteriores em um editor de texto e adicione ou remova o comentário da configuração desejada.

   Por exemplo, para especificar um [modo](application-modes.md), exclua o comentário do seguinte:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Defina o valor de `MAGE_PROFILER` a qualquer dos seguintes:

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. Salvar as alterações em `.htaccess`; não é necessário reiniciar o Apache para que a alteração tenha efeito.

### Configuração do Apache

O Apache Web Server suporta a configuração do modo de aplicativo usando `mod_env` diretivas.

O Apache `mod_env` diretiva é ligeiramente diferente na [Apache versão 2.2] e [Apache versão 2.4].

Os procedimentos a seguir mostram como definir o modo do aplicativo em um host virtual Apache. Essa não é a única maneira de usar `mod_env` diretivas; consulte a documentação do Apache para obter detalhes.

>[!TIP]
>
>A seção a seguir presume que você já configurou o host virtual. Caso contrário, consulte um recurso como [este tutorial do DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Para especificar uma variável de inicialização para o Apache no Ubuntu**:

1. Como usuário com `root` privilégios, abra o arquivo de configuração do host virtual em um editor de texto.

   Por exemplo, se o host virtual for nomeado como `my.magento`,

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
>Esta seção pressupõe que você já configurou o host virtual. Caso contrário, consulte um recurso como [este tutorial do DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Para especificar uma variável de inicialização para o Apache no CentOS**:

1. Como usuário com `root` privilégios, abrir `/etc/httpd/conf/httpd.conf` em um editor de texto.

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
