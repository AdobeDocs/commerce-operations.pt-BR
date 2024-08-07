---
title: Acompanhamento da migração de dados
description: Saiba como validar se a migração de dados de Magento 1 para Magento 2 foi bem-sucedida e se todas as funcionalidades estão funcionando como esperado.
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Acompanhamento da migração de dados

Alguns comportamentos e lógicas da Magento 1 foram implementados de forma diferente na Magento 2. O [!DNL Data Migration Tool] toma conta dele. Você deve conhecer alguns aspectos da migração e, às vezes, é necessário seguir etapas secundárias para que algumas funcionalidades funcionem sem problemas após a migração.

## Informações

### Não há suporte para a divisão de banco de dados

O [!DNL Data Migration Tool] não dá suporte a bancos de dados divididos.

### Preços de Grupo convertidos em Preços de Nível

Todos os Preços de Grupo são convertidos automaticamente em Preços de Nível durante a migração.

### Nova numeração para entidades de vendas

Os números de referência para Ordens, NFFs, Entregas, Avisos de Crédito e RMA são migrados como estão. Após a migração, as novas regras de atribuição de número do Magento 2 serão aplicadas. A numeração das novas entidades de vendas é diferente.

## Etapas

### Salvar novamente os segmentos de clientes [somente Adobe Commerce]

Após a migração, os segmentos de clientes devem ser salvos novamente no Painel de administração para ativá-los e executá-los.

### Configurar fuso horário

A ferramenta não migra as configurações de fuso horário; portanto, você deve configurar manualmente o fuso horário após a migração em **Lojas** > **Configuração** > **Opções de Localidade** > **Fuso Horário**.

Por padrão, o Magento armazena dados de tempo no fuso horário UTC-0 no banco de dados e os exibe de acordo com as configurações atuais do fuso horário. Se os dados de hora já tiverem sido salvos no banco de dados em uma zona diferente de UTC-0, você deverá converter a hora existente em UTC-0 usando o manipulador `\Migration\Handler\Timezone` do [!DNL Data Migration Tool].

No exemplo a seguir, o Magento 1 tem salvo tempo incorretamente na zona UTC-7 no banco de dados (por exemplo, devido a uma extensão de terceiros com falha). Para converter corretamente o horário de criação da conta do cliente para a zona UTC-0 após a migração, siga estas etapas:

1. Copie o arquivo de configuração `map-customer.xml.dist` do diretório apropriado de [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) para o arquivo `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml`.

1. Atualizar o nó `<customer_map_file>` em `config.xml` e remover a extensão `.dist` de `map-customer.xml.dist`

1. Adicionar a seguinte regra ao arquivo `map-customer.xml`:

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
