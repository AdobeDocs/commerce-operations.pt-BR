---
title: Ferramentas da plataforma
description: Escolha as ferramentas de plataforma recomendadas para a implementação do Adobe Commerce.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# Ferramentas da plataforma

Não há escassez de aspectos que devam ser bem pensados e rigorosamente testados para manter um site de comércio eletrônico em funcionamento sem interferência. Você não só precisa identificar as soluções certas para lidar com todos os aspectos do site, desde armazenamento de dados e programação até armazenamento em cache e segurança, como também precisa do processo certo para garantir a entrega de uma plataforma que funcione sem problemas e possa ser construída e otimizada com eficiência.

Esta seção oferece não apenas uma visão das ferramentas, soluções, processos e metodologias que foram testados e aprimorados em várias implementações da Adobe Commerce, mas também nossas recomendações para as quais as soluções se encaixam melhor nas necessidades e objetivos específicos da empresa.

A tabela a seguir inclui soluções que recomendamos e que podem ser usadas no Adobe Commerce para direcionar o desempenho na plataforma:

| Finalidade | Ferramenta |
|------------------------------------------|-------------------------|
| Banco de dados | MySQL, MariaDB, Percona |
| Linguagem de programação | PHP, JS, HTML, MENOS CSS |
| Ambiente de desenvolvimento integrado (IDE) | Eclipse, PHPStorm |
| Servidor da Web | Nginx, Apache |
| Serviços de armazenamento em cache | Redis, Varnish |
| Serviços de pesquisa | Elasticsearch |
| Serviços de fila de mensagens | RabbitMQ |
| Ferramenta de verificação de segurança | SonarQube, ZAP |

## Banco de dados

Existem três ferramentas diferentes que usamos dependendo das necessidades da marca. O MySQL é uma ótima solução de linha de base como o banco de dados do Adobe Commerce se você não espera que sua loja manipule cargas extremas.

O MariaDB é mais voltado para a comunidade e funciona melhor para usuários que se preocupam mais com os recursos do que com o desempenho puro. O MariaDB suporta uma grande variedade de mecanismos de banco de dados, criptografia de disco, interconectividade horizontal complexa e recursos de dimensionamento, o que pode ser interessante para grandes lojas Adobe Commerce.

A Percona é uma bifurcação do MySQL que centraliza o desempenho e o manuseio de carga de pico. Escolha MariaDB se precisar de mais qualidade de vida e recursos DevOps. Procure Percona se o objetivo for obter desempenho de alta carga em conjuntos de dados em grande escala.

## Linguagem de programação

O Adobe Commerce é um aplicativo baseado em PHP e as versões mais recentes são sempre compatíveis com a versão PHP estável mais recente (por exemplo, a Adobe Commerce versão 2.4 recomenda o uso do PHP 7.4). Para obter mais segurança e desempenho, há vários fatores a serem considerados ao configurar o PHP para obter velocidade e eficiência máximas no processamento de solicitações. A loja da Web do Adobe Commerce é criada com o HTML, o JavaScript e o pré-processador MENOS CSS.

## Servidores da Web

A Adobe Commerce é totalmente compatível com os servidores da Web Nginx e Apache. O Adobe Commerce fornece arquivos de configuração recomendados de amostra para ambos:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

A amostra Nginx contém configurações para melhor desempenho e é projetada para que pouca reconfiguração seja necessária.

## Serviços de armazenamento em cache

O Adobe Commerce fornece várias opções para armazenar o cache e os dados da sessão, incluindo Redis, Memcache, sistema de arquivos e banco de dados. Para uma configuração com vários nós da Web, Redis é a melhor opção.

É altamente recomendável usar o Varnish como servidor de cache de página inteira para sua loja. A Adobe Commerce distribui um arquivo de configuração de amostra para o Varnish que contém todas as configurações recomendadas para desempenho.

## Serviços de pesquisa

Para o Adobe Commerce versão 2.4 e posterior, todas as instalações devem ser configuradas para usar o Elasticsearch como solução de pesquisa de catálogo. O Elasticsearch oferece pesquisas rápidas e avançadas em produtos do catálogo. O Elasticsearch é opcional para versões anteriores à versão 2.4, mas é recomendado.

## Serviços de fila de mensagens

As filas de mensagens fornecem um mecanismo de comunicação assíncrono no qual o remetente e o destinatário de uma mensagem não se conectam. O RabbitMQ é um corretor de mensagens de código aberto que oferece um sistema de mensagens confiável, altamente disponível, escalável e portátil.

## Ferramentas de segurança

O [Ferramenta Adobe Commerce Security Scan](https://docs.magento.com/user-guide/magento/security-scan.html) permite que você monitore regularmente seus sites da loja e receba atualizações para riscos conhecidos de segurança, malware e software desatualizado. Normalmente, você começa a usar essa ferramenta quando inicia o teste de aceitação do usuário (UAT). Além da ferramenta Adobe Commerce Security Scan, que é gratuita e está disponível para todas as implementações e versões do Adobe Commerce, há outras opções que podem ser usadas durante o processo de CI/CD e antes de cada versão.

A SonarQube é uma plataforma de gerenciamento de qualidade de código aberto, projetada para analisar e medir a qualidade técnica do seu código. SonarQube não apenas fornece um relatório completo de erros de código, erros de sintaxe e vulnerabilidades, como também oferece sugestões e exemplos para corrigir seu código. O SonarQube é perfeito para usar em um ambiente CI/CD como uma ferramenta capaz de analisar o código antes de ser implantado.

Zed Attack Proxy (ZAP) é uma ferramenta gratuita de teste de segurança usada por milhares de usuários de esferográfica ao redor do mundo. O ZAP é desenvolvido pela OWASP e é uma das ferramentas mais preferidas para testes de segurança manuais.
