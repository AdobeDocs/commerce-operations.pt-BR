---
title: Prática recomendada para configurar a conexão escrava do MySQL
description: Saiba como configurar a conexão escrava MySQL para sites Adobe Commerce implantados na infraestrutura de nuvem.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cb86772e9ceabc580ec32ad6ae1206a71ea03946
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Prática recomendada para configurar a conexão escrava do MySQL

>[!NOTE]
>
>Este artigo contém termos de software padrão do setor que alguns podem achar racistas, sexistas ou opressivos e que podem fazer o leitor se sentir machucado, traumatizado ou indesejado. O Adobe está trabalhando para remover esses termos de nosso código, documentação e experiências do usuário.

Para sites Adobe Commerce implantados na arquitetura cloud Infrastructure Pro, o Adobe recomenda habilitar a conexão escrava MYSQL para o banco de dados por padrão.

O Adobe Commerce pode ler vários bancos de dados de forma assíncrona. Ao habilitar a conexão escrava MYSQL, o Adobe Commerce usa uma conexão somente leitura com o banco de dados para receber tráfego somente leitura em um nó não principal. O desempenho melhora através do balanceamento de carga quando apenas um nó lida com o tráfego de leitura e gravação.

## Versões afetadas

Adobe Commerce na infraestrutura em nuvem, arquitetura Pro

## Configurar conexão escrava MySQL

Na infraestrutura de nuvem do Adobe Commerce on, é possível substituir a configuração padrão da conexão escrava MYSQL definindo a variável [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) variável. Defina essa variável como true para usar automaticamente uma conexão somente leitura no banco de dados.

**Para habilitar a conexão escrava MySQL**:

1. Na estação de trabalho local, altere para o diretório do projeto.

1. No `.magento.env.yaml` , defina o `MYSQL_USE_SLAVE_CONNECTION` para verdadeiro.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Confirme o `.magento.env.yaml` alterações de arquivo e envio para o ambiente remoto.

   Depois que a implantação é concluída com êxito, a conexão escrava MySQL é habilitada para o ambiente de nuvem.

Saiba mais sobre como personalizar o ambiente de nuvem substituindo a configuração existente do Commerce por [Variáveis de ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) no _Guia de infraestrutura do Adobe Commerce on cloud_.

## Informações adicionais

- [Gargalo de alta carga do MySQL no Adobe Commerce na infraestrutura de nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Práticas recomendadas do banco de dados para o Adobe Commerce na infraestrutura em nuvem](database-on-cloud.md)
