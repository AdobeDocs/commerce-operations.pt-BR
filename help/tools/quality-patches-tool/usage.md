---
title: Uso
description: Saiba como usar a Ferramenta de correção de qualidade para aplicar e gerenciar correções para o Adobe Commerce. Descubra técnicas de teste, aplicativo e gerenciamento de patches.
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
type: Troubleshooting
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Uso

O [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) fornece patches individuais desenvolvidos pela Adobe e pela comunidade Magento Open Source. Ela permite aplicar, reverter e exibir informações gerais sobre todos os patches individuais disponíveis para a versão instalada do Adobe Commerce. Você pode aplicar patches a projetos Adobe Commerce, independentemente de quem os desenvolveu. Por exemplo, você pode aplicar uma correção desenvolvida pela comunidade para projetos do Adobe Commerce.

Assista a este [vídeo técnico](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=pt-BR) e saiba como usar a Ferramenta de correção de qualidade para Adobe Commerce.

>[!INFO]
>
>Consulte [Aplicar patches individuais](#apply-individual-patches) para obter instruções sobre como aplicar patches aos seus projetos do Adobe Commerce. Consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) para revisar uma lista completa de patches lançados.

>[!WARNING]
>
>Não é recomendável usar o [!DNL Quality Patches Tool] para aplicar um grande número de patches, pois isso aumenta a complexidade do código e dificulta a atualização para uma nova versão.

## Instalar

>[!INFO]
>
>Se ainda não estiver instalado, você deve instalar o [[!DNL Git]](https://github.com/git-guides/install-git) ou o [Patch](https://man7.org/linux/man-pages/man1/patch.1.html) antes de instalar o [!DNL Quality Patches Tool]. Adicione o pacote do Composer `magento/quality-patches` ao arquivo `composer.json`:

```bash
composer require magento/quality-patches
```

## Exibir patches individuais

Para exibir a lista de patches individuais disponíveis para a sua versão do Adobe Commerce:

```bash
./vendor/bin/magento-patches status
```

Você verá uma saída semelhante ao seguinte:

| ID | Título | Tipo | Status | Detalhes |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | O FPC está sendo desabilitado durante implantações | Opcional | Não aplicado | Componentes afetados:<br> - magento/module-page-cache |
| MCLOUD-5650 | Reter a configuração de implantação após a leitura do arquivo | Opcional | Não aplicado | Componentes afetados:<br> - magento/framework |
| MCLOUD-5684 | A paginação não está funcionando - product_list_limit=all | Opcional | Não aplicado | Componentes afetados: - magento/module-elasticsearch |
| MCLOUD-5837 | Corrigir problema do balanceador de carga | Obsoleto | Aplicado | Substituição recomendada: MC-1 <br> Componentes afetados: - magento/framework |
| PACOTE-2554 | Definir erro de informações de pagamento | Opcional | Não aplicado | Componentes afetados: <br>- amzn/amazon-pay-module |
| MC-1 | Corrige o problema 1 | Opcional | Aplicado | Componentes afetados: <br> - magento/module-cms |
| MC-2 | Corrige o problema 2 | Opcional | Não aplicado | Componentes afetados: <br> - magento/module-cms |
| MC-3 | Corrige o problema 3 | Opcional | Não aplicado | Patches necessários:<br> - MC-2 <br>Componentes afetados: <br>- magento/module-cms |
| MC-3-V2 | Correção atualizada para o problema 3, substitui o patch MC-3 | Opcional | N/D | Componentes afetados: <br>- magento/module-cms |

Adobe Commerce 2.3.5

A tabela de status inclui:

- **Tipo**:
   - `Optional` — Todos os patches do pacote [!DNL Quality Patches Tool] e do [Guia de Infraestrutura do Commerce on Cloud > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) são opcionais para instalações do Adobe Commerce.
   - `Deprecated` — A Adobe substituiu o patch individual. Se você tiver aplicado o patch, recomendamos que o reverta. A operação de reversão também remove o patch da tabela de status.

- **Status**:
   - `Applied` — O patch foi aplicado.
   - `Not applied` — O patch não foi aplicado.
   - `N/A` — O status do patch não pode ser definido devido a conflitos.

- **Detalhes**:
   - `Affected components` — A lista de módulos afetados.
   - `Required patches` — A lista de patches que devem ser aplicados para que um patch indicado funcione corretamente (dependências).
   - `Recommended replacement` — O patch que é um substituto recomendado para um patch obsoleto.

>[!INFO]
>
>Depois de atualizar para uma nova versão do Adobe Commerce, você deverá reaplicar os patches se eles não estiverem incluídos na nova versão. Consulte [Reaplicar patches após uma atualização](#re-apply-patches-after-an-upgrade).

## Aplicar patches individuais {#apply-individual-patches}

>[!WARNING]
>
>É uma prática recomendada testar todos os patches em um ambiente de preparo ou desenvolvimento antes de implantar na produção. Também é recomendável fazer backup dos dados antes de aplicar um patch. Consulte [Fazer backup e reverter sistema de arquivos, mídia e banco de dados](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html?lang=pt-BR).

Para aplicar um único patch, execute o seguinte comando, onde `MAGETWO-XXXX` é a ID do patch especificada na tabela de status:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

Você também pode aplicar vários patches ao mesmo tempo separando cada ID de patch adicional com um espaço:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Você deve limpar o cache após aplicar os patches para ver as alterações no aplicativo do Adobe Commerce:

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Considere manter uma lista de patches aplicados em um local separado. Talvez seja necessário reaplicar alguns deles após atualizar para uma nova versão do Adobe Commerce. Consulte [Reaplicar patches após uma atualização](#re-apply-patches-after-an-upgrade).

## Reverter patches individuais

>[!WARNING]
>
>É uma prática recomendada testar todos os patches em um ambiente de preparo ou desenvolvimento antes de implantar na produção. Também é recomendável fazer backup dos dados antes de aplicar um patch. Consulte [Fazer backup e reverter sistema de arquivos, mídia e banco de dados](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html?lang=pt-BR).

Para reverter um único patch, execute o seguinte comando, onde `MAGETWO-XXXX` é a ID do patch especificada na tabela de status:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

Além disso, você pode reverter vários patches ao mesmo tempo separando cada ID de patch adicional com um espaço:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

Para reverter todos os patches aplicados:

```bash
./vendor/bin/magento-patches revert --all
```

Você deve limpar o cache após reverter os patches para ver as alterações no aplicativo do Adobe Commerce:

```bash
./bin/magento cache:clean
```

## Obter atualizações

A Adobe Commerce lança periodicamente novos patches individuais. Você deve atualizar o [!DNL Quality Patches Tool] para obter novos patches individuais:

```bash
composer update magento/quality-patches
```

Exibir os patches adicionados:

>[!TIP]
>
>Os novos patches de adição são exibidos na parte inferior da tabela.

```bash
./vendor/bin/magento-patches status
```

## Reaplicar patches após um upgrade {#re-apply-patches-after-an-upgrade}

Quando você atualiza para uma nova versão do Adobe Commerce, deve reaplicar patches se eles não estiverem incluídos na nova versão.

Para reaplicar patches:

1. Atualize o [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Abra a lista de patches aplicados anteriormente, o que foi recomendado em [Aplicar patches individuais](#apply-individual-patches).

1. Aplique os patches:

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   A prática recomendada é aplicar os patches um de cada vez.

1. Limpe o cache:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >Quando você executa o comando `status`, os patches incluídos na nova versão não são mais exibidos na tabela de patches disponíveis.

## Logs

O [!DNL Quality Patches Tool] registra todas as operações no arquivo `<Magento_root>/var/log/patch.log`.
