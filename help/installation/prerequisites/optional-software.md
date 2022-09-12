---
title: Software opcional
description: Saiba mais sobre o software opcional que você pode instalar para suportar instalações locais do Adobe Commerce e Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---


# Software opcional

É altamente recomendável instalar o NTP para garantir que as tarefas relacionadas ao cron sejam executadas corretamente. (As datas do servidor podem estar no passado ou no futuro, por exemplo.)

Os outros utilitários opcionais discutidos neste tópico podem ajudá-lo com sua instalação; no entanto, eles não precisam instalar ou usar o Adobe Commerce ou o Magento Open Source.

## Instalando e Configurando o Protocolo de Hora da Rede (NTP)

[NTP](https://www.ntp.org/) permite que os servidores sincronizem os relógios do sistema usando [servidores de pool disponíveis globalmente](https://www.ntppool.org/en/). Recomendamos que você use servidores NTP confiáveis, sejam eles soluções de hardware dedicadas na sua rede interna ou servidores públicos externos.

Se você estiver implantando o Adobe Commerce ou o Magento Open Source em vários hosts, o NTP é uma maneira simples de garantir que seus relógios sejam todos sincronizados, independentemente do fuso horário em que os servidores estejam. Além disso, as tarefas relacionadas ao cron (como indexação e e-mails transacionais) dependem do relógio do servidor ser preciso.

### Instalar e configurar o NTP no Ubuntu

Digite o seguinte comando para instalar o NTP:

```bash
apt-get install ntp
```

Continue com [Usar servidores de pool NTP](#use-ntp-pool-servers).

### Instalar e configurar o NTP no CentOS

Para instalar e configurar o NTP:

1. Digite o seguinte comando para localizar o software NTP apropriado:

   ```bash
   yum search ntp
   ```

1. Selecione um pacote para instalar. Por exemplo, `ntp.x86_64`.

1. Instale o pacote .

   ```bash
   yum -y install ntp.x86_64
   ```

1. Digite o seguinte comando para que o NTP seja iniciado quando o servidor for iniciado.

   ```bash
   chkconfig ntpd on
   ```

1. Continue com a próxima seção.

### Usar servidores de pool NTP

A seleção de servidores de pool depende de você. Se você usar servidores de pool NTP, ntp.org recomenda usar [servidores de pool](https://www.ntppool.org/en/) que estejam próximos do fuso horário de seus servidores, como discutido na seção [Página de projeto do pool NTP](https://www.ntppool.org/en/use.html). Se você tiver um servidor NTP privado disponível para todos os hosts em sua implantação, poderá usar esse servidor.

1. Abrir `/etc/ntp.conf` em um editor de texto.

1. Procure linhas semelhantes a:

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Substitua essas linhas ou adicione linhas adicionais que especificam seu servidor de pool NTP ou outros servidores NTP. É uma boa ideia especificar mais de um.

1. Um exemplo do uso de três servidores NTP baseados nos Estados Unidos é o seguinte:

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. Salve as alterações em `/etc/ntp.conf` e saia do editor de texto.

1. Reinicie o serviço.

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. Enter `date` para verificar a data do servidor.

   Se a data estiver incorreta, verifique se a porta do cliente NTP (normalmente, UDP 123) está aberta no firewall.

   Experimente o `ntpdate _[pool server hostname]_` comando. Se ele falhar, procure o erro que retorna.

   Se tudo o resto falhar, tente reiniciar o servidor.

## Criar phpinfo.php

O [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) O arquivo exibe uma grande quantidade de informações sobre [PHP](https://glossary.magento.com/php) e suas extensões.

>[!NOTE]
>
>Use `phpinfo.php` num sistema de desenvolvimento _only_. Pode ser um problema de segurança na produção.

Adicione o seguinte código em qualquer lugar da raiz do seu servidor da Web:

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Para obter mais informações, consulte o [página manual do phpinfo](https://www.php.net/manual/en/function.phpinfo.php).

Para visualizar os resultados, insira o seguinte [URL](https://glossary.magento.com/url) no campo de local ou endereço do navegador:

```http
http://<web server host or IP>/phpinfo.php
```

Se um erro 404 (Não encontrado) for exibido, verifique o seguinte:

* Inicie o servidor da Web, se necessário.
* Certifique-se de que o firewall permita tráfego na porta 80.

   [Ajuda para o Ubuntu](https://help.ubuntu.com/community/UFW)

   [Ajuda para CentOS](https://wiki.centos.org/HowTos/Network/IPTables)

## phpMyAdmin

O aplicativo phpMyAdmin é um utilitário de administração de banco de dados gratuito e fácil de usar. Você pode usá-lo para verificar e manipular o conteúdo do banco de dados. Você deve fazer logon no phpMyAdmin como o usuário administrativo do banco de dados MySQL.

Para obter mais informações sobre phpMyAdmin, consulte o [página inicial do phpMyAdmin](https://www.phpmyadmin.net/).

Para obter informações mais detalhadas sobre instalação, consulte o [documentação de instalação do phpMyAdmin](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>Use phpMyAdmin em um sistema de desenvolvimento _only_. Pode ser um problema de segurança na produção.

1. Para usar phpMyAdmin, digite o seguinte comando no campo de endereço ou local do navegador:

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Quando solicitado, faça logon usando seu banco de dados MySQL `root` ou o nome de usuário e senha do administrador.
