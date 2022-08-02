---
title: Definir o valor dos parâmetros de inicialização
description: Saiba como definir parâmetros de inicialização para o aplicativo Commerce.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---


# Parâmetros de Bootstrap

Este tópico demonstra como definir os valores dos parâmetros de inicialização do aplicativo Commerce. Consulte [Visão geral da inicialização e do bootstrapping do aplicativo](initialization.md).

A tabela a seguir discute os parâmetros de bootstrap que você pode definir:

| parâmetro Bootstrap | Descrição |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Especifica caminhos de URL e diretório personalizados |
| MAGE_PROFILER | Habilita gráficos de dependência e criação de perfis de HTML |

>[!INFO]
>
>- Nem todos os parâmetros de bootstrap estão documentados.
>- Agora você define o modo de aplicativo (desenvolvedor, padrão, produção) usando o [`magento deploy:mode:set {mode}`](../cli/set-mode.md) comando.


## Definir parâmetros usando uma variável de ambiente

Esta seção discute como definir os valores de parâmetros de bootstrap usando variáveis de ambiente.

### Defina o modo de aplicativo

Você pode especificar variáveis de bootstrap como variáveis de ambiente em todo o sistema, o que permite que todos os processos as usem.

Por exemplo, você pode usar a variável `MAGE_PROFILER` variável de ambiente do sistema para especificar um modo como segue:

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

Defina a variável usando um comando específico de shell. Como os shells têm sintaxe diferente, consulte uma referência como [unix.stackexchange.com][unix-stackx].

Exemplo de shell de base para CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Se uma `PHP Fatal error` é exibido no navegador depois que você define um valor de profiler, reinicie o servidor da Web. O motivo pode estar relacionado ao armazenamento em cache do código de bytes PHP, que armazena em cache os códigos e os caminhos de classe PHP.

## Definir parâmetros para Apache ou Nginx

Esta seção discute como especificar o modo do Apache ou Nginx.

### Configuração de próximo

Consulte a [Nova configuração de amostra] on _GitHub_.

### Configuração Apache .htaccess

Uma maneira de definir o modo de aplicativo é editando `.htaccess`. Dessa forma, não é necessário alterar as configurações do Apache.

Você pode modificar `.htaccess` em qualquer um dos seguintes locais, dependendo do seu ponto de entrada no aplicativo Commerce:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Para definir uma variável**:

1. Abra qualquer um dos arquivos anteriores em um editor de texto e adicione ou exclua o comentário da configuração desejada.

   Por exemplo, para especificar uma [modo](application-modes.md), exclua o comentário do seguinte:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Defina o valor de `MAGE_PROFILER` a qualquer um dos seguintes:

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. Salve as alterações em `.htaccess`; não é necessário reiniciar o Apache para que a alteração entre em vigor.

### Configuração do Apache

O servidor Web Apache oferece suporte para a configuração do modo de aplicativo usando `mod_env` diretivas.

O Apache `mod_env` a diretiva é um pouco diferente no [Apache versão 2.2] e [Apache versão 2.4].

Os procedimentos a seguir mostram como definir o modo de aplicativo em um host virtual do Apache. Essa não é a única maneira de usar `mod_env` diretivas; consulte a documentação do Apache para obter detalhes.

>[!TIP]
>
>A seção a seguir parte do princípio de que você já configurou o host virtual. Caso contrário, consulte um recurso como [este tutorial do DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Especificação de uma variável de bootstrap para Apache no Ubuntu**:

1. Como um usuário com `root` , abra o arquivo de configuração do host virtual em um editor de texto.

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

1. Após definir o modo , reinicie o servidor da Web:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>Esta seção supõe que você já configurou seu host virtual. Caso contrário, consulte um recurso como [este tutorial do DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Especificação de uma variável de inicialização para o Apache no CentOS**:

1. Como um usuário com `root` privilégios, abrir `/etc/httpd/conf/httpd.conf` em um editor de texto.

1. Em qualquer lugar na configuração do host virtual, adicione a seguinte linha:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Por exemplo,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Salve as alterações e saia do editor de texto.

1. Após definir o modo , reinicie o servidor da Web:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache versão 2.2]: http://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache versão 2.4]: http://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nova configuração de amostra]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: http://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
