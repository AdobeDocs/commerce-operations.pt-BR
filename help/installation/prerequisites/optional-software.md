---
title: Software opcional
description: Saiba mais sobre o software opcional que você pode instalar para oferecer suporte às instalações locais do Adobe Commerce.
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Software opcional

É altamente recomendável instalar o NTP para garantir que as tarefas relacionadas ao cron sejam executadas corretamente. (As datas do servidor podem estar no passado ou no futuro, por exemplo.)

Os outros utilitários opcionais discutidos neste tópico podem ajudá-lo com a sua instalação; no entanto, eles não são necessários para instalar ou usar o Adobe Commerce.

## Instalando e Configurando o NTP (Network Time Protocol)

[NTP](https://www.ntp.org/) permite que os servidores sincronizem seus relógios do sistema usando [servidores de pool disponíveis globalmente](https://www.ntppool.org/en/). Recomendamos que você use servidores NTP confiáveis, sejam eles soluções de hardware dedicadas à sua rede interna ou servidores públicos externos.

Se você estiver implantando o Adobe Commerce em vários hosts, o NTP é uma maneira simples de garantir que seus relógios estejam todos sincronizados, independentemente do fuso horário em que os servidores estiverem. Além disso, as tarefas relacionadas ao cron (como indexação e emails transacionais) dependem da precisão do relógio do servidor.

### Instalar e configurar o NTP no Ubuntu

Digite o seguinte comando para instalar o NTP:

```bash
apt-get install ntp
```

Continuar com [Usar servidores de pool NTP](#use-ntp-pool-servers).

### Instalar e configurar o NTP no CentOS

Para instalar e configurar o NTP:

1. Digite o seguinte comando para localizar o software NTP apropriado:

   ```bash
   yum search ntp
   ```

1. Selecione um pacote a ser instalado. Por exemplo, `ntp.x86_64`.

1. Instale o pacote.

   ```bash
   yum -y install ntp.x86_64
   ```

1. Digite o seguinte comando para que o NTP seja iniciado quando o servidor for iniciado.

   ```bash
   chkconfig ntpd on
   ```

1. Prossiga para a próxima seção.

### Usar servidores de pool NTP

A seleção de servidores de pool depende de você. Se você usa servidores de pool NTP, o ntp.org recomenda que você use [servidores de pool](https://www.ntppool.org/en/) próximos ao fuso horário de seus servidores, conforme discutido na [página do projeto de pool NTP](https://www.ntppool.org/en/use.html). Se você tiver um servidor NTP privado disponível para todos os hosts em sua implantação, poderá usar esse servidor.

1. Abra `/etc/ntp.conf` em um editor de texto.

1. Procure linhas semelhantes ao seguinte:

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Substitua essas linhas ou adicione linhas adicionais que especificam seu servidor de pool NTP ou outros servidores NTP. É uma boa ideia especificar mais de um.

1. Este é um exemplo de uso de três servidores NTP com base nos Estados Unidos:

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. Salve as alterações em `/etc/ntp.conf` e saia do editor de texto.

1. Reinicie o serviço.

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. Digite `date` para verificar a data do servidor.

   Se a data estiver incorreta, verifique se a porta do cliente NTP (normalmente, UDP 123) está aberta no firewall.

   Experimente o comando `ntpdate _[pool server hostname]_`. Se falhar, procure o erro que ele retorna.

   Se tudo falhar, tente reinicializar o servidor.

## Criar phpinfo.php

O arquivo [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) exibe uma grande quantidade de informações sobre o PHP e suas extensões.

>[!NOTE]
>
>Use `phpinfo.php` em um sistema de desenvolvimento _only_. Pode ser um problema de segurança na produção.

Adicione o seguinte código em qualquer lugar no docroot do servidor Web:

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Para obter mais informações, consulte a [página de manual phpinfo](https://www.php.net/manual/en/function.phpinfo.php).

Para exibir os resultados, insira o seguinte URL no campo de local ou endereço do navegador:

```http
http://<web server host or IP>/phpinfo.php
```

Se um erro 404 (Não encontrado) for exibido, verifique o seguinte:

* Inicie o servidor Web, se necessário.
* Verifique se o firewall permite o tráfego na porta 80.

  [Ajuda do Ubuntu](https://help.ubuntu.com/community/UFW)

  [Ajuda para CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

O aplicativo phpMyAdmin é um utilitário de administração de banco de dados gratuito e fácil de usar. Você pode usá-lo para verificar e manipular o conteúdo do banco de dados. Você deve fazer login no phpMyAdmin como o usuário administrativo do banco de dados MySQL.

Para obter mais informações sobre phpMyAdmin, consulte a [página inicial do phpMyAdmin](https://www.phpmyadmin.net/).

Para informações mais detalhadas sobre a instalação, consulte a [documentação de instalação do phpMyAdmin](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>Use phpMyAdmin em um sistema de desenvolvimento _only_. Pode ser um problema de segurança na produção.

1. Para usar o phpMyAdmin, digite o seguinte comando no campo de endereço ou localização do seu navegador:

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Quando solicitado, faça logon usando seu banco de dados MySQL `root` ou o nome de usuário e senha do usuário administrativo.
