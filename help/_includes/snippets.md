---
source-git-commit: c8a20ad1b0b57724f389cfa5c63f6ae542758c2b
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---
# Trechos

## Somente Commerce {#commerce-only}

>[!NOTE]
>
>O [!DNL Upgrade Compatibility Tool] está disponível somente para instâncias do Adobe Commerce.

<!-- Configuration guide snippets -->

## Proprietário do sistema de arquivos {#file-system-owner}

>[!WARNING]
>
>Todos os comandos da CLI do Magento devem ser executados pelo [proprietário do sistema de arquivos](/help/configuration/cli/config-cli.md#prerequisites).

## Comandos de backup {#tip-backup-command}

>[!TIP]
>
>O comando `support:backup` é _não_ o mesmo backup de código executado pelo comando `setup:backup`. O comando `support:backup` deve fazer backup do código para ser examinado pelo Suporte da Adobe Commerce.

## Patches B2B {#b2b-patches}

>[!NOTE]
>
>Depois de instalar esse patch de segurança, os comerciantes B2B do Adobe Commerce também devem atualizar para a versão mais recente do patch de segurança B2B compatível. Consulte as [notas de versão B2B](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes).

## Somente Adobe Commerce {#ee-only}

>[!NOTE]
>
>Esse recurso está disponível somente para instâncias do Adobe Commerce.

## Dividir BD descontinuado {#deprecate-split-db}

>[!IMPORTANT]
>
>O recurso de banco de dados dividido foi [descontinuado](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) na versão 2.4.2 do Adobe Commerce. Consulte [Reverter de um banco de dados dividido para um único banco de dados](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Alterações incompatíveis com versões anteriores {#bics}

>[!NOTE]
>
>As versões do Adobe Commerce podem conter alterações incompatíveis com versões anteriores (BICs). Para revisar as alterações incompatíveis com versões anteriores, consulte [referência do BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Os principais problemas incompatíveis com versões anteriores estão descritos em [destaques da BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/). Nem todas as versões introduzem os BICs principais.

## Isenção de responsabilidade da Alpha {#alpha}

>[!IMPORTANT]
>
>As versões do [Alpha](/help/release/versioning-policy.md#alpha-patch-release) podem estar incompletas e provavelmente contêm defeitos. Eles são fornecidos &quot;NO ESTADO EM QUE SE ENCONTRAM&quot; sem garantias de nenhum tipo. A Adobe não tem nenhuma obrigação de manter, corrigir, atualizar, alterar, modificar ou oferecer suporte (por meio dos Serviços de suporte da Adobe ou de outra forma) às versões do Alpha. Os clientes não devem confiar no funcionamento ou no desempenho correto das versões do Alpha ou de qualquer documentação ou material que o acompanhe. O uso das versões do Alpha é de inteira responsabilidade do cliente.

## Isenção de responsabilidade da Beta {#beta}

>[!IMPORTANT]
>
>As versões do Beta podem conter defeitos e são fornecidas &quot;NO ESTADO EM QUE SE ENCONTRAM&quot; sem garantias de nenhum tipo. A Adobe não tem nenhuma obrigação de manter, corrigir, atualizar, alterar, modificar ou oferecer suporte (dos Serviços de suporte da Adobe ou de qualquer outro serviço) às versões beta. Os clientes devem ter cuidado e não devem depender de forma alguma do funcionamento ou do desempenho correto das versões beta e/ou de qualquer documentação ou material que as acompanhe. Portanto, qualquer uso das versões beta é de inteira responsabilidade do cliente.

## Aviso CVE {#cve-notice}

>[!NOTE]
>
>A partir da versão 2.3.2, atribuiremos e publicaremos números indexados de vulnerabilidades e exposições comuns (CVE) com cada erro de segurança relatado a nós por terceiros. Isso permite que os usuários identifiquem mais facilmente vulnerabilidades não solucionadas na implantação. Você pode saber mais sobre os identificadores CVE em [CVE](https://cve.mitre.org/).

## Outras informações sobre a versão {#other-release-info}

>[!NOTE]
>
>Embora o código para aprimoramentos e correções de erros descritos nestas notas de versão esteja incluído no Adobe Commerce, vários desses projetos (por exemplo, B2B, Page Builder e Progressive Web Applications (PWA) Studio) também são lançados independentemente. As correções de erros para esses projetos estão documentadas nas informações de versão separadas e específicas do projeto, disponíveis na documentação de cada projeto. Consulte a [visão geral da versão do produto](/help/release/release-notes/overview.md).

## Controle do processo PHP {#php-process-control}

Antes de executar indexadores no modo paralelo, você deve habilitar o suporte de Controle de Processo (`pcntl`) no PHP. Consulte [Instalação](https://www.php.net/manual/en/pcntl.installation.php) na documentação do PHP.

## Patches personalizados {#custom-patches-disclaimer}

>[!IMPORTANT]
>
>A Adobe não oferece suporte à aplicação de patches oficiais fornecidos pela Adobe usando esse método. Use o método a seguir por sua conta e risco. Para aplicar patches oficiais, use o [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Sempre realize testes abrangentes antes de implantar qualquer patch personalizado.
