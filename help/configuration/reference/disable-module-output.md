---
title: Desabilitar saída do módulo
description: Saiba como desativar a saída do módulo.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Desabilitar saída do módulo

Por padrão, todos os módulos são configurados para que a saída do módulo possa ser gravada em uma visualização. Desativar a saída oferece uma maneira de essencialmente desativar um módulo que não pode ser desativado devido a dependências permanentes.

Por exemplo, a variável `Customer` O módulo depende do `Review` módulo, para que o `Review` O módulo não pode ser desativado. No entanto, se você não quiser que os clientes forneçam análises, poderá desativar a saída do `Review` módulo.

>[!INFO]
>
>Se um comerciante tiver usado o administrador para desativar a saída do módulo em uma versão anterior, será necessário configurar manualmente o sistema para migrar essas configurações.

A desabilitação de saída é executada nas seguintes classes:

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>Desativar a saída do módulo não desativa o módulo. O módulo permanece ativado e funcionando, mas nenhum bloco, página ou campo é renderizado no front-end ou back-end.

## Desabilitar saída do módulo em uma implantação de pipeline

Para desativar a saída do módulo na implantação do pipeline ou em qualquer outra implantação, com várias instâncias do aplicativo Commerce:

1. Edite o `Backend` do módulo `config.xml` arquivo.
1. Exporte as alterações de configuração.

### Edite o `Backend` módulo `config.xml` arquivo

1. Arquivar o original `config.xml` arquivo.
1. Adicione linhas semelhantes às seguintes à `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` arquivo, diretamente sob o `<default>` elemento:

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   Aqui:

   - `<modules_disable_output>` contém uma lista de módulos.
   - `<Magento_Newsletter></Magento_Newsletter>` especifica para qual módulo desabilitar a saída.
   - `1` é o sinalizador que desativa a saída para o `Magento_Newsletter` módulo.

Como resultado de exemplo dessa configuração, os clientes não podem mais se inscrever para receber boletins informativos.

### Exportar as alterações de configuração

Execute o seguinte comando para exportar as alterações de configuração:

```bash
bin/magento app:config:dump
```

Os resultados são gravados na `<Magento_install_dir>/app/etc/config.php` arquivo.

Em seguida, limpe o cache para ativar a nova configuração:

```bash
bin/magento cache:clean config
```

Consulte [Exportar a configuração](../cli/export-configuration.md).

## Desabilitar saída do módulo em uma implantação simples

O procedimento para desativar a saída do módulo em uma única instância do Commerce é mais fácil, pois as alterações não precisam ser distribuídas.

1. Arquivar o original `<Magento_install_dir>/app/etc/config.php` arquivo.
1. Adicione o `advanced` e `modules_disable_output` seções para a `config.php` arquivo (se não existirem):

   ```php
   'system' =>
     array (
       'websites' =>
       array (
         'base' =>
         array (
           'advanced' =>
           array (
             'modules_disable_output' =>
             array (
               'Magento_Review' => '1',
             ),
           ),
         ),
       ),
     ),
   ```

Neste exemplo, a saída para a variável `Magento_Review` O módulo foi desativado e os clientes não podem mais revisar os produtos.
Para reativar a saída, defina o valor como `0`.
