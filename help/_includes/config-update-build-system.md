---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Atualizar sistema de compilação

**Para atualizar o sistema de compilação**:

1. Faça logon no sistema de compilação como proprietário do sistema de arquivos.
1. Altere para o diretório raiz do aplicativo.

   ```shell
   cd <Magento root dir>
   ```

1. Puxe as alterações para `app/etc/config.php` do controle do código-fonte.

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. Código de compilação.

   ```shell
   bin/magento setup:di:compile
   ```

1. Depois que o código tiver sido compilado, gere arquivos de visualização estáticos.

   ```shell
   bin/magento setup:static-content:deploy -f
   ```

1. Verifique as alterações no controle de origem.

   ```shell
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
