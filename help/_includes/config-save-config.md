---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# Atualizar a configuração compartilhada

**Para atualizar a configuração**:

1. Faça logon no sistema de desenvolvimento como ou alterne para o proprietário do sistema de arquivos.

1. Altere para a raiz do aplicativo e execute o comando dump.

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Por exemplo, se o Commerce estiver instalado no `/var/www/html/magento2`, insira:

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Confirme que `app/etc/config.php` foi atualizado.

   ```bash
   git status
   ```

   Exemplo de resposta:

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >Fazer _não_ enviar alterações para o `generated`, `pub/media`ou `pub/static` diretórios para controle de origem. Você gera esses arquivos no sistema de build. O sistema de desenvolvimento deve ter código, temas e assim por diante que não estão prontos para uso no sistema de produção.

1. Fazer check-in das alterações em `app/etc/config.php` somente para controle de origem.

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
