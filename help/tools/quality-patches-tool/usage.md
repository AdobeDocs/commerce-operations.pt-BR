---
title: Uso
description: Saiba como usar o [!DNL Quality Patches Tool].
source-git-commit: 7ce26f10b92632c077d37ae03d68594ba2444098
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 0%

---

# Uso

O [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) O fornece patches individuais desenvolvidos pelo Adobe e pela comunidade do Magento Open Source. Ele permite aplicar, reverter e exibir informações gerais sobre todos os patches individuais disponíveis para a versão instalada do Adobe Commerce ou do Magento Open Source. Você pode aplicar patches a projetos do Adobe Commerce e do Magento Open Source, independentemente de quem desenvolveu o patch. Por exemplo, você pode aplicar um patch desenvolvido pela comunidade a projetos da Adobe Commerce.


>[!INFO]
>
>Consulte [Aplicar patches individuais](#apply-individual-patches) para obter instruções sobre como aplicar patches a seus projetos do Adobe Commerce ou Magento Open Source. Consulte [Patches disponíveis](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) para revisar uma lista completa de patches lançados.

>[!WARNING]
>
>Não é recomendável usar a variável [!DNL Quality Patches Tool] para aplicar grandes números de patches, pois aumenta a complexidade do código e dificulta a atualização para uma nova versão.

## Instalar

>[!INFO]
>
>Se ele ainda não estiver instalado, você deve instalar [[!DNL Git]](https://github.com/git-guides/install-git) ou [Correção](https://man7.org/linux/man-pages/man1/patch.1.html) antes de instalar o [!DNL Quality Patches Tool]. Adicione o `magento/quality-patches` Pacote do compositor para o seu `composer.json` arquivo:

```bash
composer require magento/quality-patches
```

## Exibir patches individuais

Para exibir a lista de patches individuais disponíveis para sua versão do Adobe Commerce ou do Magento Open Source:

```bash
./vendor/bin/magento-patches status
```

Você verá uma saída semelhante à seguinte:

| Id | Título | Tipo | Status | Detalhes |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | A FPC está sendo desativada durante as implantações | Opcional | Não aplicado | Componentes afetados:<br> - magento/module-page-cache |
| MCLOUD-5650 | Manter configuração de implantação após a leitura do arquivo | Opcional | Não aplicado | Componentes afetados:<br> - magento/estrutura |
| MCLOUD-5684 | Paginação Não está funcionando - product_list_limit=all | Opcional | Não aplicado | Componentes afetados: - magento/module-elasticsearch |
| MCLOUD-5837 | Corrigir problema do balanceador de carga | Obsoleto | Aplicado | Substituição recomendada: MC-1 <br> Componentes afetados: - magento/estrutura |
| PACOTE-2554 | Definir erro de informações de pagamento | Opcional | Não aplicado | Componentes afetados: <br>- amzn/amazon-pay-module |
| MC-1 | Correções 1 | Opcional | Aplicado | Componentes afetados: <br> - magento/module-cms |
| MC-2 | Correções problema 2 | Opcional | Não aplicado | Componentes afetados: <br> - magento/module-cms |
| MC-3 | Correções problema 3 | Opcional | Não aplicado | Correções necessárias:<br> - MC-2 <br>Componentes afetados: <br>- magento/module-cms |
| MC-3-V2 | Correção atualizada para o problema 3, substitui o patch MC-3 | Opcional | N/D | Componentes afetados:  <br>- magento/module-cms |

Adobe Commerce 2.3.5.

A tabela de status inclui:

- **Tipo**:
   - `Optional` — Todos os patches do [!DNL Quality Patches Tool] e [Correções da nuvem](https://devdocs.magento.com/cloud/project/project-patch.html) são opcionais para instalações do Adobe Commerce e Magento Open Source.
   - `Deprecated` — o Adobe substituiu o patch individual. Se tiver aplicado o sistema transdérmico, recomendamos que o reverta. A operação reverter também remove o patch da tabela de status.

- **Status**:
   - `Applied` — O patch foi aplicado.
   - `Not applied` — O sistema não foi aplicado.
   - `N/A` — O status do patch não pode ser definido devido a conflitos.

- **Detalhes**:
   - `Affected components` — A lista de módulos afetados.
   - `Required patches` — A lista de patches que devem ser aplicados para que um patch indicado funcione corretamente (dependências).
   - `Recommended replacement` — O patch que é um substituto recomendado para um patch obsoleto.

>[!INFO]
>
>Depois de atualizar para uma nova versão do Adobe Commerce ou do Magento Open Source, você deve reaplicar os patches se eles não estiverem incluídos na nova versão. Consulte [Reaplicar patches após uma atualização](#re-apply-patches-after-an-upgrade).

## Aplicar patches individuais {#apply-individual-patches}

>[!WARNING]
>
>É uma prática recomendada testar todos os patches em um ambiente de preparo ou desenvolvimento antes de implantá-los na produção. Também é recomendável fazer backup dos seus dados antes de aplicar um patch. Consulte [Faça backup e reverta o sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

Para aplicar um único patch, execute o seguinte comando onde `MAGETWO-XXXX` é a ID de patch especificada na tabela de status:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

Você também pode aplicar vários patches ao mesmo tempo separando cada ID de patch adicional com um espaço:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Você deve limpar o cache após aplicar os patches para ver as alterações no aplicativo Adobe Commerce:

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Considere manter uma lista de patches aplicados em um local separado. Talvez seja necessário reaplicar alguns deles após atualizar para uma nova versão do Adobe Commerce ou do Magento Open Source. Consulte [Reaplicar patches após uma atualização](#re-apply-patches-after-an-upgrade).

## Reverter patches individuais

>[!WARNING]
>
>É uma prática recomendada testar todos os patches em um ambiente de preparo ou desenvolvimento antes de implantá-los na produção. Também é recomendável fazer backup dos seus dados antes de aplicar um patch. Consulte [Faça backup e reverta o sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

Para reverter um único patch, execute o seguinte comando onde `MAGETWO-XXXX` é a ID de patch especificada na tabela de status:

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

Você deve limpar o cache após reverter os patches para ver as alterações no aplicativo Adobe Commerce:

```bash
./bin/magento cache:clean
```

## Obter atualizações

O Adobe Commerce lança periodicamente novos patches individuais. Você deve atualizar o [!DNL Quality Patches Tool] para obter novos patches individuais:

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

## Reaplicar patches após uma atualização {#re-apply-patches-after-an-upgrade}

Ao atualizar para uma nova versão do Adobe Commerce ou do Magento Open Source, você deve reaplicar os patches se os patches não estiverem incluídos na nova versão.

Para reaplicar patches:

1. Atualize o [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Abra a lista de patches aplicados anteriormente, que foi recomendada em [Aplicar patches individuais](#apply-individual-patches).

1. Aplique os patches:

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   A prática recomendada é aplicar patches um de cada vez.

1. Limpe o cache:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >Quando você executa a variável `status` , os patches incluídos na nova versão não são mais exibidos na tabela de patches disponíveis.

## Registro

O [!DNL Quality Patches Tool] registra todas as operações no `<Magento_root>/var/log/patch.log` arquivo.
