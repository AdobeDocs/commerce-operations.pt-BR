---
title: Segurança das instalações no local
description: Saiba mais sobre como melhorar a postura de segurança de sua instalação do Adobe Commerce ou Magento Open Source no local.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# Segurança das instalações no local

[Linux aprimorado de segurança (SELinux)](https://selinuxproject.org/page/Main_Page) permite que os administradores do CentOS e do Ubuntu tenham maior controle de acesso sobre seus servidores. Se você estiver usando o SELinux *e* O Apache deve iniciar uma conexão com outro host. Você deve executar os comandos discutidos nesta seção.

>[!NOTE]
>
>O Adobe não tem nenhuma recomendação sobre o uso do SELinux; você pode usá-lo para segurança aprimorada, se desejar. Se você usar o SELinux, deverá configurá-lo corretamente ou o Adobe Commerce e o Magento Open Source poderão funcionar de maneira imprevisível. Se você optar por usar o SELinux, consulte um recurso como o [Wiki do CentOS](https://wiki.centos.org/HowTos/SELinux) para configurar regras para permitir a comunicação.

## Sugestão para instalar com o Apache

Se você optar por habilitar o SELinux, poderá ter problemas ao executar o instalador, a menos que altere o *contexto de segurança* de alguns diretórios como segue:

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

Os comandos anteriores funcionam somente com o servidor Web Apache. Devido à variedade de configurações e requisitos de segurança, não garantimos que esses comandos funcionem em todas as situações. Para obter mais informações, consulte:

* [página principal](https://linux.die.net/man/8/httpd_selinux)
* [Laboratório de servidor](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Ativar comunicação entre servidores

Se o Apache e o servidor de banco de dados estiverem no mesmo host, use o seguinte comando se planeja usar integrações que usam `curl` (ex. Paypal e USPS).
Para permitir que o Apache inicie uma conexão com outro host com o SELinux habilitado:

1. Para determinar se o SELinux está ativado, use o seguinte comando:

   ```bash
   getenforce
   ```

   `Enforcing` é exibido para confirmar que o SELinux está em execução.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## Abrir portas no firewall

Dependendo dos requisitos de segurança, talvez seja necessário abrir a porta 80 e outras portas no firewall. Devido à natureza sensível da segurança de rede, o Adobe recomenda que você consulte o departamento de TI antes de continuar. A seguir, algumas referências sugeridas:

* Ubuntu: [Página de documentação do Ubuntu](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [Tutorial do CentOS](https://wiki.centos.org/HowTos/Network/IPTables).
