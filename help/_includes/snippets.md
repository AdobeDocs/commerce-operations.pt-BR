---
source-git-commit: 8b9e4de2799532e4654fce63d856c2d301025f09
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---
# Trechos

## Somente comércio {#commerce-only}

>[!NOTE]
>
>A variável [!DNL Upgrade Compatibility Tool] O está disponível somente para instâncias do Adobe Commerce.

<!-- Configuration guide snippets -->

## Proprietário do sistema de arquivos {#file-system-owner}

>[!WARNING]
>
>Todos os comandos da CLI do Magento devem ser executados pelo [proprietário do sistema de arquivos](/help/configuration/cli/config-cli.md#prerequisites).

## Comandos de backup {#tip-backup-command}

>[!TIP]
>
>A variável `support:backup` é _não_ o mesmo backup de código executado pelo `setup:backup` comando. A variável `support:backup` destina-se a fazer backup do código para análise pelo Suporte da Adobe Commerce.

## Somente Adobe Commerce {#ee-only}

>[!NOTE]
>
>Esse recurso está disponível somente para instâncias do Adobe Commerce.

## Dividir BD descontinuado {#deprecate-split-db}

>[!IMPORTANT]
>
>O recurso de banco de dados dividido foi [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) na versão 2.4.2 do Adobe Commerce. Consulte [Reverter de um banco de dados dividido para um único banco de dados](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Alterações incompatíveis com versões anteriores {#bics}

>[!NOTE]
>
>As versões do Adobe Commerce e do Magento Open Source podem conter alterações incompatíveis com versões anteriores (BICs). Para revisar alterações incompatíveis com versões anteriores, consulte [Referência de BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Os principais problemas incompatíveis com versões anteriores estão descritos na [Destaques do BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). Nem todas as versões introduzem os BICs principais.

## Aviso CVE {#cve-notice}

>[!NOTE]
>
>A partir da versão 2.3.2, atribuiremos e publicaremos números indexados de vulnerabilidades e exposições comuns (CVE) com cada erro de segurança relatado a nós por terceiros. Isso permite que os usuários identifiquem mais facilmente vulnerabilidades não solucionadas na implantação. Você pode saber mais sobre identificadores CVE em [CVE](https://cve.mitre.org/).

## Outras informações sobre a versão {#other-release-info}

>[!NOTE]
>
>Embora o código para aprimoramentos e correções de erros descritos nestas notas de versão esteja incluído no Adobe Commerce, vários desses projetos (por exemplo, B2B, Page Builder e Progressive Web Application (PWA) Studio) também são lançados de forma independente. As correções de erros para esses projetos estão documentadas nas informações de versão separadas e específicas do projeto, disponíveis na documentação de cada projeto. Consulte [visão geral da versão do produto](/help/release/release-notes/overview.md).

## Controle do processo PHP {#php-process-control}

Antes de executar indexadores no modo paralelo, você deve habilitar o suporte ao Controle do processo (`pcntl`) no PHP. Consulte [Instalação](https://www.php.net/manual/en/pcntl.installation.php) na documentação do PHP.
