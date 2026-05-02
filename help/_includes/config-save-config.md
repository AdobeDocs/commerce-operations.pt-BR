---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# Atualizar a configuração compartilhada

**Para atualizar a configuração**:

1. Faça logon no sistema de desenvolvimento como ou alterne para o proprietário do sistema de arquivos.

1. Altere para a raiz do aplicativo e execute o comando dump.

   ```shell
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Por exemplo, se o Commerce estiver instalado em `/var/www/html/magento2`, digite:

   ```shell
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Confirme se `app/etc/config.php` foi atualizado.

   ```shell
   git status
   ```

   Exemplo de resposta:

   ```text
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >_não_ enviar alterações para os diretórios `generated`, `pub/media` ou `pub/static` para o controle do código-fonte. Você gera esses arquivos no sistema de build. O sistema de desenvolvimento deve ter código, temas e assim por diante que não estão prontos para uso no sistema de produção.

1. Fazer check-in das alterações em `app/etc/config.php` somente no controle do código-fonte.

   ```shell
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
