---
title: Desativar saída do módulo
description: Saiba como desativar a saída do módulo.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# Desativar saída do módulo

Por padrão, todos os módulos são configurados para que a saída do módulo possa ser gravada em uma visualização. Desativar a saída oferece uma maneira de desativar essencialmente um módulo que não pode ser desativado devido a dependências rígidas.

Por exemplo, a variável `Customer` depende do `Review` assim, o `Review` não é possível desabilitar o módulo. No entanto, se você não quiser que os clientes forneçam revisões, poderá desativar a saída do `Review` módulo.

>[!INFO]
>
>Se um comerciante usou o Administrador para desativar a saída do módulo em uma versão anterior, você deve configurar manualmente o sistema para migrar essas configurações.

A desativação da Saída é executada nas seguintes classes:

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>Desativar a saída do módulo não desativa o módulo. O módulo permanece ativado e funcionando, mas nenhum bloco, página ou campo é renderizado no front-end ou no back-end.

## Desative a saída do módulo em uma implantação de pipeline

Para desativar a saída do módulo na implantação de pipeline ou em qualquer outra implantação, com várias instâncias do aplicativo Commerce:

1. Edite o `Backend` do módulo `config.xml` arquivo.
1. Exporte as alterações de configuração.

### Edite o `Backend` módulo `config.xml` arquivo

1. Arquivar o original `config.xml` arquivo.
1. Adicione linhas semelhantes ao seguinte à `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` , diretamente sob o `<default>` elemento:

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   Aqui:

   - `<modules_disable_output>` contém uma lista de módulos.
   - `<Magento_Newsletter></Magento_Newsletter>` especifica o módulo para o qual desabilitar a saída.
   - `1` é o sinalizador que desativa a saída para o `Magento_Newsletter` módulo.

Como resultado de amostra dessa configuração, os clientes não podem mais se inscrever para receber boletins informativos.

### Exportar as alterações de configuração

Execute o seguinte comando para exportar as alterações de configuração:

```bash
bin/magento app:config:dump
```

Os resultados são gravados no `<Magento_install_dir>/app/etc/config.php` arquivo.

Em seguida, limpe o cache para ativar a nova configuração:

```bash
bin/magento cache:clean config
```

Consulte [Exportar a configuração](../cli/export-configuration.md).

## Desative a saída do módulo em uma implantação simples

O procedimento para desabilitar a saída do módulo em uma única instância do Commerce é mais fácil porque as alterações não precisam ser distribuídas.

1. Arquivar o original `<Magento_install_dir>/app/etc/config.php` arquivo.
1. Adicione o `advanced` e `modules_disable_output` para `config.php` (se não existirem):

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

Neste exemplo, a saída da variável `Magento_Review` foi desativado e os clientes não podem mais revisar produtos.
Para reativar a saída, defina o valor como `0`.
