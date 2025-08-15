---
title: Práticas recomendadas de configuração do MySQL
description: Saiba como os acionadores MySQL e as conexões subordinadas afetam o desempenho do site do Commerce e como usá-los com eficiência.
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Práticas recomendadas de configuração do MySQL

>[!NOTE]
>
>Este tópico contém termos de software padrão do setor que alguns podem considerar racistas, sexistas ou opressivos, e que podem fazer com que o leitor se sinta ferido, traumatizado ou indesejado. O Adobe está trabalhando para remover esses termos do código, da documentação e das experiências do usuário.

## Triggers

Este artigo explica como evitar problemas de desempenho ao usar acionadores MySQL. Os acionadores são usados para registrar alterações em tabelas de auditoria.

### Produtos e versões afetados

- Adobe Commerce no local
- Adobe Commerce na infraestrutura em nuvem

>[!WARNING]
>
>Para Adobe Commerce em projetos na nuvem, sempre teste as alterações de configuração no ambiente de preparo antes de alterar a configuração para o ambiente de produção.

### Impactos no desempenho

Os acionadores são interpretados como código, significando que o MySQL não os pré-compila.

Ao conectar-se ao espaço de transação do query, os acionadores adicionam overhead a um analisador e interpretador para cada query executada com a tabela. Os acionadores compartilham o mesmo espaço de transação que as consultas originais e, enquanto essas consultas competem por bloqueios na tabela, os acionadores competem independentemente por bloqueios em outra tabela.

Essa sobrecarga adicional pode afetar negativamente o desempenho do site se muitos acionadores forem usados.

>[!WARNING]
>
>O Adobe Commerce não oferece suporte a acionadores personalizados no banco de dados do Adobe Commerce, pois esses acionadores podem introduzir incompatibilidades com versões futuras do Adobe Commerce. Para obter as práticas recomendadas, consulte [Diretrizes gerais do MySQL](../../../installation/prerequisites/database/mysql.md) na documentação do Adobe Commerce.

### Uso efetivo

Para evitar problemas de desempenho ao usar acionadores, siga estas diretrizes:

- Se você tiver acionadores personalizados que gravam alguns dados quando o acionador é executado, mova essa lógica para gravar diretamente nas tabelas de auditoria. Por exemplo, adicionando uma consulta adicional no código do aplicativo, após a consulta, você pretendia criar o acionador para.
- Revise os acionadores personalizados existentes e considere removê-los e gravá-los diretamente nas tabelas do lado do aplicativo. Verifique se há gatilhos no banco de dados usando a [`SHOW TRIGGERS` Instrução SQL](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Para obter assistência, dúvidas ou preocupações adicionais, [envie um tíquete de Suporte da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Conexões subordinadas

O Adobe Commerce pode ler vários bancos de dados de forma assíncrona. Se você espera uma carga alta para o banco de dados MySQL de um site do Commerce implantado na arquitetura Pro da infraestrutura em nuvem, a Adobe recomenda ativar a conexão slave MYSQL.

Quando você ativa a conexão slave do MYSQL, o Adobe Commerce usa uma conexão somente leitura com o banco de dados para receber tráfego somente leitura em um nó não mestre. O desempenho melhora por meio do balanceamento de carga quando apenas um nó lida com o tráfego de leitura-gravação.

### Versões afetadas

Adobe Commerce na infraestrutura em nuvem, somente arquitetura Pro

### Configuração

Na infraestrutura do Adobe Commerce na nuvem, é possível substituir a configuração padrão da conexão slave do MYSQL definindo a variável [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection). Defina essa variável como `true` para usar automaticamente uma conexão somente leitura com o banco de dados.

**Para habilitar a conexão subordinada do MySQL**:

1. Na estação de trabalho local, altere para o diretório do projeto.

1. No arquivo `.magento.env.yaml`, defina `MYSQL_USE_SLAVE_CONNECTION` como verdadeiro.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Confirme as alterações no arquivo `.magento.env.yaml` e envie-o por push para o ambiente remoto.

   Depois que a implantação é concluída com sucesso, a conexão do escravo do MySQL é habilitada para o ambiente de nuvem.
