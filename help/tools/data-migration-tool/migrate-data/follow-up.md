---
title: Acompanhamento da migração de dados
description: Saiba como validar se a migração de dados de Magento 1 para Magento 2 foi bem-sucedida e que todas as funcionalidades estão funcionando como esperado.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# Acompanhamento da migração de dados

Alguns comportamentos e lógicas de Magento 1 foram implementados de forma diferente na Magento 2. O [!DNL Data Migration Tool] cuida disso. Há alguns aspectos de migração que você deve conhecer e, às vezes, você deve tomar pequenos passos para que algumas funcionalidades funcionalidades funcionem sem problemas após a migração.

## Informações

### Banco de dados dividido não suportado

O [!DNL Data Migration Tool] não suporta bancos de dados divididos.

### Preços do Grupo convertidos em Preços de Escala

Todos os Preços do Grupo são convertidos automaticamente em Preços da Camada durante a migração.

### Nova numeração para entidades de vendas

Números de referência para Pedidos, NFFs, Entregas, Avisos de Crédito e RMA migram como estão. Após a migração, as novas regras de atribuição de número de Magento 2 serão aplicadas. A numeração das novas entidades de venda é diferente.

## Etapas

### Salvar novamente os segmentos do cliente [Somente Adobe Commerce]

Após a migração, os segmentos do cliente devem ser salvos no Painel de administração para que fiquem ativos e em execução.

### Configurar fuso horário

A ferramenta não migra as configurações de fuso horário, portanto, é necessário configurar manualmente o fuso horário após a migração em **Lojas** > **Configuração** > **Opções de localidade** > **Fuso horário**.

Por padrão, o Magento armazena dados de hora no fuso horário UTC-0 no banco de dados e os exibe de acordo com as configurações atuais do fuso horário. Se os dados de tempo já tiverem sido salvos no banco de dados em uma zona diferente de UTC-0, você deverá converter o tempo existente em UTC-0 usando a variável [!DNL Data Migration Tool]&#39;s `\Migration\Handler\Timezone` manipulador.

No exemplo a seguir, o Magento 1 economizou tempo incorretamente na zona UTC-7 no banco de dados (por exemplo, devido a uma extensão de terceiros defeituosa). Para converter adequadamente a hora de criação da conta do cliente para a zona UTC-0 após a migração, siga estas etapas:

1. Copie o `map-customer.xml.dist` arquivo de configuração do diretório apropriado do [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) na `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` arquivo.

1. Atualize o `<customer_map_file>` nó no `config.xml` e remova o `.dist` extensão de `map-customer.xml.dist`

1. Adicione a seguinte regra ao `map-customer.xml` arquivo:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="../map.xsd">
  <!--...-->
  <destination>
      <field_rules>
          <!--...-->
          <transform>
              <field>customer_entity.created_at</field>
              <handler class="\Migration\Handler\Timezone">
                  <param name="offset" value="-7" />
              </handler>
          </transform>
      </field_rules>
  </destination>
</map>
```
