---
title: Prática recomendada para configurar a conexão slave do MySQL
description: Saiba como configurar a conexão do escravo do MySQL para sites do Adobe Commerce implantados na infraestrutura de nuvem.
role: Developer
feature: Best Practices
exl-id: d65bc80a-c4ec-4ea4-aff1-110592838201
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Prática recomendada para configurar a conexão slave do MySQL

>[!NOTE]
>
>Este artigo contém termos de software padrão do setor que alguns podem considerar racistas, sexistas ou opressivos e que podem fazer com que o leitor se sinta ferido, traumatizado ou indesejado. O Adobe está trabalhando para remover esses termos de nosso código, documentação e experiências do usuário.

Para sites do Adobe Commerce implantados na arquitetura Pro da infraestrutura em nuvem, a Adobe recomenda ativar a conexão slave MYSQL para o banco de dados por padrão.

O Adobe Commerce pode ler vários bancos de dados de forma assíncrona. Quando você ativa a conexão slave do MYSQL, o Adobe Commerce usa uma conexão somente leitura com o banco de dados para receber tráfego somente leitura em um nó não principal. O desempenho melhora por meio do balanceamento de carga quando apenas um nó lida com o tráfego de leitura-gravação.

## Versões afetadas

Adobe Commerce na infraestrutura em nuvem, arquitetura Pro

## Configurar conexão do MySQL slave

Na infraestrutura do Adobe Commerce na nuvem, é possível substituir a configuração padrão da conexão subordinada do MYSQL, definindo o [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) variável. Defina essa variável como true para usar automaticamente uma conexão somente leitura com o banco de dados.

**Para habilitar a conexão do escravo do MySQL**:

1. Na estação de trabalho local, altere para o diretório do projeto.

1. No `.magento.env.yaml` , defina o `MYSQL_USE_SLAVE_CONNECTION` para verdadeiro.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Confirme o `.magento.env.yaml` alterações no arquivo e envio para o ambiente remoto.

   Depois que a implantação é concluída com sucesso, a conexão do escravo do MySQL é habilitada para o ambiente de nuvem.

Saiba mais sobre como personalizar o ambiente de nuvem substituindo a configuração existente do Commerce por [Variáveis de ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) no _guia da infraestrutura do Adobe Commerce na nuvem_.

## Informações adicionais

- [Gargalo de alta carga do MySQL no Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Práticas recomendadas de banco de dados para o Adobe Commerce na infraestrutura em nuvem](database-on-cloud.md)
