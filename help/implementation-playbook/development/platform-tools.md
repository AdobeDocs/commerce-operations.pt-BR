---
title: Ferramentas da plataforma
description: Escolha as ferramentas recomendadas da plataforma para a implementação do Adobe Commerce.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
feature: Configuration
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# Ferramentas da plataforma

Não faltam aspectos que devem ser bem pensados e rigorosamente testados para manter um site de comércio eletrônico funcionando sem interferência. Você não só precisa identificar as soluções certas para lidar com todos os aspectos do site — desde o armazenamento e a programação de dados até o armazenamento em cache e a segurança — como também precisa do processo correto para garantir o fornecimento de uma plataforma que funcione sem problemas e possa ser criada e otimizada com eficiência.

Esta seção oferece não apenas uma visão das ferramentas, soluções, processos e metodologias que foram testadas e aperfeiçoadas em várias implementações do Adobe Commerce, mas também nossas recomendações para quais soluções se encaixam melhor em necessidades e objetivos específicos de negócios.

A tabela a seguir inclui soluções que recomendamos e que podem ser usadas no Adobe Commerce para impulsionar o desempenho na plataforma:

| Finalidade | Ferramenta |
|------------------------------------------|-------------------------|
| Banco de dados | MySQL, MariaDB, Percona |
| Linguagem de programação | PHP, JS, HTML, LESS CSS |
| IDE (Integrated Development Environment, ambiente de desenvolvimento integrado) | Eclipse, PHPStorm |
| Servidor da Web | Nginx, Apache |
| Armazenamento em cache de serviços | Redis, Verniz |
| Pesquisar serviços | Elasticsearch |
| Serviços de fila de mensagens | [!DNL RabbitMQ] |
| Ferramenta de verificação de segurança | SonarQube, ZAP |

## Banco de dados

Existem três ferramentas diferentes que usamos, dependendo das necessidades da marca. O MySQL é uma ótima solução de linha de base como o banco de dados do Adobe Commerce se você não espera que sua loja lide com cargas extremas.

O MariaDB é mais focado na comunidade e funciona melhor para usuários que se preocupam mais com recursos do que com o desempenho puro. O MariaDB suporta uma grande variedade de mecanismos de banco de dados, criptografia de disco, interconectividade horizontal complexa e recursos de dimensionamento, que podem ser interessantes para grandes lojas Adobe Commerce.

Percona é uma bifurcação do MySQL que se concentra no desempenho e no manuseio de carga de pico. Escolha MariaDB se precisar de mais qualidade de vida e recursos DevOps. Procure o Percona se a sua meta for obter desempenho de alta carga em conjuntos de dados de grande escala.

## Linguagem de programação

O Adobe Commerce é um aplicativo baseado em PHP e as versões mais recentes são sempre compatíveis com a versão estável mais recente do PHP (por exemplo, a versão 2.4 do Adobe Commerce recomenda o uso do PHP 7.4). Para obter mais segurança e desempenho, existem vários fatores a serem considerados ao configurar o PHP para obter o máximo de velocidade e eficiência no processamento de requisições. A loja da Web do Adobe Commerce é construída com o HTML, JavaScript e o pré-processador LESS CSS.

## Servidores da Web

O Adobe Commerce é totalmente compatível com os servidores Web Nginx e Apache. O Adobe Commerce fornece arquivos de configuração recomendados de exemplo para:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

A amostra do Nginx contém configurações para melhor desempenho e é projetada para que seja necessária pouca reconfiguração.

## Armazenamento em cache de serviços

O Adobe Commerce fornece várias opções para armazenar o cache e os dados da sessão, incluindo Redis, Memcache, sistema de arquivos e banco de dados. Para uma configuração com vários nós da Web, Redis é a melhor opção.

Recomendamos usar o Varnish como servidor de cache de página inteira para sua loja. A Adobe Commerce distribui um arquivo de configuração de exemplo para o Verniz que contém todas as configurações recomendadas para desempenho.

## Pesquisar serviços

Para a versão 2.4 e posterior do Adobe Commerce, todas as instalações devem ser configuradas para usar o Elasticsearch ou OpenSearch como a solução de pesquisa de catálogo. O Elasticsearch fornece pesquisas rápidas e avançadas em produtos do catálogo. O Elasticsearch é opcional para versões anteriores à 2.4, mas é recomendado.

## Serviços de fila de mensagens

As filas de mensagens fornecem um mecanismo de comunicação assíncrono no qual o remetente e o destinatário de uma mensagem não entram em contato entre si. [!DNL RabbitMQ] é um agente de mensagens de código aberto que oferece um sistema de mensagens confiável, altamente disponível, escalável e portátil.

## Ferramentas de segurança

A [Ferramenta de Verificação de Segurança da Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) permite monitorar regularmente os sites da loja e receber atualizações de riscos de segurança conhecidos, malware e software desatualizado. Normalmente, você começa a usar essa ferramenta ao iniciar o teste de aceitação do usuário (UAT). Além da ferramenta Adobe Commerce Security Scan, que é gratuita e está disponível para todas as implementações e versões do Adobe Commerce, há outras opções que podem ser usadas durante o processo de CI/CD e antes de cada versão.

O SonarQube é uma plataforma de gerenciamento de qualidade de código aberto, projetada para analisar e medir a qualidade técnica de seu código. O SonarQube não só fornece um relatório completo de bugs de código, erros de sintaxe e vulnerabilidades, como também oferece sugestões e exemplos para corrigir seu código. O SonarQube é perfeito para usar em um ambiente de CI/CD como uma ferramenta capaz de analisar o código antes que ele seja implantado.

O Zed Attack Proxy (ZAP) é uma ferramenta gratuita de testes de segurança usada por milhares de testadores de caneta em todo o mundo. O ZAP é desenvolvido pela OWASP e é uma das ferramentas mais preferidas para testes manuais de segurança.
