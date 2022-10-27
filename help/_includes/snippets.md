---
source-git-commit: 74cb55f4552bc1b2dace37d9a6f7e68939d1c262
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---
# Trechos

## Somente comércio {#commerce-only}

>[!NOTE]
>
>O [!DNL Upgrade Compatibility Tool] O está disponível somente para instâncias do Adobe Commerce .

<!-- Configuration guide snippets -->

## Proprietário do sistema de arquivos {#file-system-owner}

>[!WARNING]
>
>Todos os comandos Magento CLI devem ser executados pelo [proprietário do sistema de arquivos](/help/configuration/cli/config-cli.md#prerequisites).

## Comandos de backup {#tip-backup-command}

>[!TIP]
>
>O `support:backup` comando is _not_ o mesmo backup de código executado pela `setup:backup` comando. O `support:backup` O comando destina-se a fazer backup do código para exame pelo Adobe Commerce Support.

## Somente Adobe Commerce {#ee-only}

>[!NOTE]
>
>Esse recurso está disponível somente para instâncias do Adobe Commerce .

## Split DB obsoleto {#deprecate-split-db}

>[!IMPORTANT]
>
>O recurso de banco de dados dividido era [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) na versão 2.4.2 do Adobe Commerce. Consulte [Reverter de um banco de dados dividido para um único banco de dados](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Alterações retroativas incompatíveis {#bics}

>[!NOTE]
>
>As versões do Adobe Commerce e do Magento Open Source podem conter BICs (backsupported changes, alteração incompatível com o fundo). Para analisar alterações incompatíveis com o passado, consulte [Referência BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Os principais problemas incompatíveis com o passado são descritos em [Destaques do BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). Nem todas as versões introduzem BIC importantes.

## Aviso CVE {#cve-notice}

>[!NOTE]
>
>A partir da versão 2.3.2, atribuiremos e publicaremos números de Vulnerabilidades e Exposições Comuns (CVE) indexados com cada bug de segurança relatado por terceiros. Isso permite que os usuários identifiquem vulnerabilidades não endereçadas com mais facilidade em sua implantação. Você pode saber mais sobre identificadores CVE em [CVE](https://cve.mitre.org/).
