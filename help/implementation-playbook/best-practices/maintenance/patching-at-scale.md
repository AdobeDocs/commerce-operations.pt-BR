---
title: Práticas recomendadas para distribuição de patches em escala
description: Saiba como o patch centralizado para o Adobe Commerce pode ajudar você a gerenciar projetos empresariais.
role: Developer
feature: Best Practices
badge: label="Contribuição de Anton Evers, arquiteto técnico sênior, Adobe" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="Contribuição de Anton Evers"
source-git-commit: d8ee656b4b1741b39f2eef1f5628a299377e774c
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---


# Práticas recomendadas para distribuição de patches do Adobe Commerce em escala

Se você gerenciar várias instalações do Adobe Commerce, [aplicação de patches](../../../upgrade/patches/apply.md) pode ser um processo complexo. _Patch centralizado_ é uma parte essencial do [arquitetura de referência global](../../architecture/global-reference.md) e uma prática recomendada para as empresas. Ele ajuda a aplicar os patches corretos em todas as instalações do Adobe Commerce. Este tópico explica como obter a distribuição centralizada de patches para todos os tipos de Adobe Commerce [patches](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>O conteúdo a seguir foi publicado originalmente no [Distribuindo patches do Adobe Commerce em escala](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) publicação no Blog da Adobe Tech. Ela foi modificada para se concentrar nas etapas e amostras de código para implementar uma estratégia de patch centralizada. Consulte a publicação original para obter mais detalhes sobre os diferentes tipos de correções descritos aqui.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Estratégia

Como há vários tipos diferentes de patches e muitas maneiras de aplicá-los, como você sabe qual patch é aplicado primeiro? Quanto mais patches você tiver, maior a chance de eles serem aplicados no mesmo arquivo ou na mesma linha de código. Os patches são aplicados na seguinte ordem:

1. **Patches de segurança** fazem parte da base de código estático de uma versão do Adobe Commerce.
1. **Patches do compositor** até `composer install` e `composer update` plug-ins como [cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. Todos **patches necessários** incluído na [Patches da nuvem para o Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) pacote.
1. Selecionado **correções de qualidade** incluído na [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **Patches personalizados** e os patches de suporte do Adobe Commerce na `/m2-hotfixes` diretório em ordem alfabética por nome de patch.

   >[!IMPORTANT]
   >
   >Quanto mais patches você aplicar, mais complexo será o código. Códigos complexos podem dificultar a atualização para uma nova versão do Adobe Commerce e aumentar seu custo total de propriedade.

Se você for responsável por manter várias instalações do Adobe Commerce, garantir que todas as instâncias tenham o mesmo conjunto de patches instalados pode ser desafiador. Cada instalação tem seu próprio repositório Git, `/m2-hotfixes` diretório e `composer.json` arquivo. A única garantia que você tem é que o **patches de segurança** e **patches necessários** para usuários da nuvem são instalados como parte da sua versão principal do Adobe Commerce.

Atualmente, não há uma solução única centralizada para esse problema, mas o Composer oferece uma maneira de preencher a lacuna. A variável [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) permite que você [aplicar patches de dependências](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Você pode criar um pacote do Composer que instale todos os seus patches e, em seguida, exigir esse pacote em todos os seus projetos.

Isso abrange **patches de segurança**, **patches necessários**, e **Patches do compositor**, mas e os patches de qualidade e o conteúdo do `/m2-hotfixes` diretório?

## Aplicar patches e hotfixes de qualidade

Você pode instalar patches de qualidade na infraestrutura de nuvem e em instalações locais usando o `vendor/bin/magento-patches apply` comando. Você deve garantir que a variável `vendor/bin/magento-patches apply` comando é executado depois de `composer install` operações.

>[!NOTE]
>
>Na infraestrutura em nuvem, você também pode instalar patches de qualidade, listando-os no `.magento.env.yaml` arquivo. O exemplo descrito aqui requer o uso de `vendor/bin/magento-patches apply` comando.

Você pode especificar os patches a serem aplicados na `composer.json` arquivo de um pacote de componente Composer personalizado, em seguida, crie um pacote de plug-in que execute o comando depois de `composer install` operações.

Em resumo, este exemplo de patch centralizado requer a criação de dois pacotes personalizados do Composer:

- **Pacote do componente:** `centralized-patcher`

   - Define a lista de patches de qualidade e `m2-hotfixes` para instalar
   - Exige o `centralized-patcher-composer-plugin` pacote, que executa o `vendor/bin/magento-patches apply` comando depois `composer install` operações

- **Pacote de plug-ins:** `centralized-patcher-composer-plugin`

   - Define um `CentralizedPatcher` Classe PHP que lê a lista de correções de qualidade do `centralized-patcher` pacote
   - Executa o `vendor/bin/magento-patches apply` comando para instalar a lista de patches de qualidade após `composer install` operações

### `centralized-patcher`

Você pode criar um pacote de componente do Composer (`centralized-patcher`) para gerenciar centralmente todos os patches de qualidade e `/m2-hotfixes` em todas as instalações do Adobe Commerce.

O pacote de componentes deve:

- Copie o conteúdo de `/m2-hotfixes` em todas as suas instalações durante a implantação.
- Defina a lista de patches de qualidade a serem instalados.
- Execute o `vendor/bin/magento-patches` comando para instalar a mesma lista de patches de qualidade em todas as instalações (usando o [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) pacote de plug-in como uma dependência).

Para criar o `centralized-patcher` pacote do componente:

1. Criar um `composer.json` arquivo com o seguinte conteúdo:

   >[!NOTE]
   >
   >A variável `require` o atributo no exemplo a seguir mostra um `require` dependência do [pacote de plug-in](#centralized-patcher-composer-plugin) que você deve criar posteriormente neste exemplo.

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. Criar um `/m2-hotfixes` diretório dentro do pacote e adicione-o ao `map` atributo no seu `composer.json` arquivo. A variável `map` O atributo contém arquivos a serem copiados deste pacote para a raiz do projeto de destino do qual você deseja aplicar patch.

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >A variável `centralized-patcher` o pacote copia o conteúdo do `/m2-hotfixes` no diretório m2-hotfixes do projeto target em `composer install`.  Como os scripts de implantação em nuvem aplicam hotfixes m2 após `composer install`, todos os hotfixes são instalados pelo mecanismo de implantação.

1. Defina os patches de qualidade a serem instalados no `quality-patches` atributo.

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


A variável `quality-patches` atributo na amostra de código anterior contém dois patches da variável [lista completa de patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) como exemplo.  Esses patches de qualidade são instalados em todos os projetos que exigem o `centralized-patcher` pacote usando o `vendor/bin/magento-patches apply` comando.

Para fins de teste, você pode criar um exemplo de patch (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>Você deve colocar seus próprios patches no `m2-hotfixes` diretório junto com os patches recebidos diretamente do Suporte da Adobe Commerce.

Um exemplo de arquivo de patch (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

Como este exemplo usa o método local para instalar patches de qualidade, você deve garantir que o `vendor/bin/magento-patches apply` comando é executado depois de `composer install` operações. Este plug-in é acionado depois de `composer install` operações, que executa o `vendor/bin/magento-patches apply` comando.

Para criar o `centralized-patcher-compose-plugin` pacote do componente:

1. Criar um `composer.json` arquivo com o seguinte conteúdo:

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. Crie um arquivo PHP e defina um `CentralizedPatcher` classe para ler a lista de patches de qualidade no [`centralized-patcher`](#centralized-patcher) pacote de componentes e instale-os imediatamente após cada `composer install` operação.

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>Consulte a [exemplos de código](#code-examples) para ver os dois pacotes descritos neste exemplo em ação.


## O que fazer com patches específicos de projetos

Você pode ter um cenário em que apenas 95% dos patches são necessários em todos os projetos, enquanto alguns patches se aplicam apenas a uma instância específica. A forma regular de aplicar patches ainda funciona. Você pode manter patches específicos do projeto na `/m2-hotfixes` patches de qualidade de diretório e instalação por projeto.

Se você usar essa abordagem, **não** confirmar todos os patches no `/m2-hotfixes` diretório que foi copiado para o projeto pelo `centralized-patcher` pacote de componentes. Você pode evitar confirmações acidentais adicionando `/m2-hotfixes` ao seu `.gitignore` arquivo. Depois de atualizar o `.gitignore` arquivo, lembre-se de que qualquer `/m2-hotfixes` deve ser adicionado usando o `git add –force` comando.

## Execução de diferentes versões do Adobe Commerce

Defina a dependência correta no `centralized-patcher` pacote de componentes. Por exemplo, talvez você precise do Adobe Commerce 2.4.5-p2 para uma versão específica do seu pacote, que só fornece patches compatíveis com o Adobe Commerce 2.4.5-p2. Você pode ter outra versão deste pacote compatível com o Adobe Commerce 2.4.4.

## Compreender o resultado

Assim como com o Adobe Commerce na infraestrutura em nuvem, este artigo presume que o processo de implantação usa o `composer install` e não `composer update` ou `git pull` para implantar o novo código em seus servidores. O fluxo da instalação de patch centralizada terá a seguinte aparência:

1. Instalação do Composer

   - Instala o Adobe Commerce, incluindo segurança -p1 ou -p2 e patches funcionais
   - Combina centralizado `/m2-hotfixes` e suporte a patches com informações específicas de `/m2-hotfixes` e patches de suporte
   - Aplica todos os patches instalados com o `cweagans/composer-patches` Pacote do compositor

1. Depois `composer install`

   - O plug-in do Composer instala correções de qualidade centralizadas

1. Implantação

   - Os patches necessários e os patches de qualidade específicos do projeto são instalados com base no `.magento.env.yaml` (Adobe Commerce somente em projetos de infraestrutura em nuvem).
   - Patches personalizados e patches de suporte do `/m2-hotfixes` Os diretórios são instalados em ordem alfabética pelo nome do patch.

Dessa forma, você pode gerenciar centralmente todos os patches de todas as suas instalações e pode garantir melhor a segurança e a estabilidade das lojas Adobe Commerce. Use os seguintes métodos para verificar o status do patch:

- [Projetos de infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [Projetos no local](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Exemplos de código

- [Patches centralizados no Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Patches centralizados no Adobe Commerce na infraestrutura em nuvem](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Plug-in do Compositor do patcher centralizado](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Componente de correção centralizado](https://github.com/AntonEvers/centralized-patcher)
