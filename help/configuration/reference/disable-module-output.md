---
title: Desabilitar saída do módulo
description: Saiba como desativar a saída do módulo.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Desabilitar saída do módulo

Por padrão, todos os módulos são configurados para que a saída do módulo possa ser gravada em uma visualização. Desativar a saída oferece uma maneira de essencialmente desativar um módulo que não pode ser desativado devido a dependências permanentes.

Por exemplo, o módulo `Customer` depende do módulo `Review`, portanto, o módulo `Review` não pode ser desabilitado. No entanto, se você não quiser que os clientes forneçam análises, poderá desativar a saída do módulo `Review`.

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

Para desativar a saída do módulo na implantação do pipeline ou qualquer outra implantação, com várias instâncias do aplicativo do Commerce:

1. Edite o arquivo `config.xml` do módulo `Backend`.
1. Exporte as alterações de configuração.

### Editar o arquivo `config.xml` do módulo `Backend`

1. Arquivar o arquivo `config.xml` original.
1. Adicione linhas semelhantes às seguintes ao arquivo `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml`, diretamente sob o elemento `<default>`:

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
   - `1` é o sinalizador que desabilita a saída para o módulo `Magento_Newsletter`.

Como resultado de exemplo dessa configuração, os clientes não podem mais se inscrever para receber boletins informativos.

### Exportar as alterações de configuração

Execute o seguinte comando para exportar as alterações de configuração:

```bash
bin/magento app:config:dump
```

Os resultados são gravados no arquivo `<Magento_install_dir>/app/etc/config.php`.

Em seguida, limpe o cache para ativar a nova configuração:

```bash
bin/magento cache:clean config
```

Consulte [Exportar a configuração](../cli/export-configuration.md).

## Desabilitar saída do módulo em uma implantação simples

O procedimento para desativar a saída do módulo em uma única instância do Commerce é mais fácil, pois as alterações não precisam ser distribuídas.

1. Arquivar o arquivo `<Magento_install_dir>/app/etc/config.php` original.
1. Adicionar as seções `advanced` e `modules_disable_output` ao arquivo `config.php` (se elas não existirem):

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

Neste exemplo, a saída do módulo `Magento_Review` foi desabilitada e os clientes não podem mais revisar produtos.
Para reabilitar a saída, defina o valor como `0`.
