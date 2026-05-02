---
title: Segurança de instalação local
description: Saiba mais sobre maneiras de melhorar a postura de segurança da instalação local do Adobe Commerce.
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Segurança de instalação local

[O SELinux (Security Enhanced Linux)](https://selinuxproject.org/page/Main_Page) permite que os administradores CentOS e Ubuntu tenham maior controle de acesso sobre seus servidores. Se você estiver usando o SELinux *and*, o Apache deverá iniciar uma conexão com outro host. Execute os comandos discutidos nesta seção.

>[!NOTE]
>
>O Adobe não tem recomendações sobre como usar o SELinux; você pode usá-lo para melhorar a segurança, se desejar. Se você usar o SELinux, precisará configurá-lo corretamente ou o Adobe Commerce poderá funcionar de forma imprevisível. Se você optar por usar o SELinux, consulte um recurso como o [wiki do CentOS](https://wiki.centos.org/HowTos/SELinux) para configurar regras para habilitar a comunicação.

## Sugestão para instalar com o Apache

Se você optar por habilitar o SELinux, poderá ter problemas ao executar o instalador, a menos que altere o *contexto de segurança* de alguns diretórios da seguinte maneira:

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

Os comandos anteriores funcionam somente com o servidor Web Apache. Devido à variedade de configurações e requisitos de segurança, não garantimos que esses comandos funcionem em todas as situações. Para obter mais informações, consulte:

* [página do manual](https://linux.die.net/man/8/httpd_selinux)
* [Laboratório de servidores](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Habilitar comunicação entre servidores

Se o Apache e o servidor de banco de dados estiverem no mesmo host, use o seguinte comando se você planeja usar integrações que usam o `curl` (por exemplo, Paypal e USPS).
Para permitir que o Apache inicie uma conexão com outro host com o SELinux ativado:

1. Para determinar se o SELinux está habilitado, use o seguinte comando:

   ```shell
   getenforce
   ```

   `Enforcing` é exibido para confirmar que o SELinux está em execução.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## Abrindo portas no firewall

Dependendo dos requisitos de segurança, talvez você precise abrir a porta 80 e outras portas do firewall. Devido à natureza confidencial da segurança de rede, a Adobe recomenda que você consulte seu departamento de TI antes de continuar. A seguir estão algumas referências sugeridas:

* Ubuntu: [Página da documentação do Ubuntu](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [instruções do CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).
