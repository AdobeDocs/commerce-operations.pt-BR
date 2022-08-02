---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Atualizar sistema de build

**Para atualizar o sistema de build**:

1. Faça logon no sistema de build como proprietário do sistema de arquivos.
1. Altere para o diretório raiz do aplicativo.

   ```bash
   cd <Magento root dir>
   ```

1. Puxe as alterações para `app/etc/config.php` do controle de origem.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Compilar código.

   ```bash
   bin/magento setup:di:compile
   ```

1. Depois que o código for compilado, gere arquivos de visualização estáticos.

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. Verifique as alterações no controle do código-fonte.

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
