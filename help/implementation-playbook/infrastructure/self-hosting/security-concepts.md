---
title: Conceitos de segurança da Adobe Commerce de auto-hospedagem
description: Saiba mais sobre as ideias e os conceitos de segurança de auto-hospedagem e as práticas recomendadas a serem consideradas. Saiba mais sobre conceitos como sistema de arquivos somente leitura, verificação de malware e muitos outros tópicos a serem considerados ao hospedar o adobe commerce.
landing-page-description: Saiba mais sobre alguns conceitos e aspectos de segurança a serem considerados ao hospedar o Adobe Commerce por conta própria.
short-description: Conheça as estratégias e os conceitos de segurança para hospedar você mesmo o Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: c4912f02-0411-466f-8c77-d610de9eb35d
feature: Install, Security
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---

# Conceitos de segurança

A segurança deve ser sempre uma consideração importante para qualquer coisa relacionada a um projeto de comércio eletrônico. Sem uma forte postura de segurança, a área de superfície que pode ser atacada é exponencialmente maior. Os conceitos e ideias apresentados fornecem métodos comprovados para reduzir as vulnerabilidades comuns normalmente exploradas.

Os conceitos a seguir não estão em nenhuma ordem específica. Elas têm o objetivo de fornecer algumas ideias e conceitos para serem considerados. Muitos são gratuitos ou exigiriam o mínimo de instalação e configuração e monitoramento subsequente. Pesquise esses tópicos fora deste tutorial para garantir que você tenha uma compreensão profunda o suficiente dos conceitos apresentados aqui.

## Sistema de arquivos somente leitura

O conceito de sistema de arquivos somente leitura foi emprestado do [Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. Isso remove completamente uma área principal usada por um mau ator. Muitas explorações aproveitaram a alteração de um arquivo que se espera esteja no aplicativo Commerce para evitar a detecção. Em vez de criar um, o ator incorreto altera o conteúdo de um arquivo existente para executar uma ação inesperada. Tornar o sistema de arquivos somente leitura reduz significativamente esse vetor de ataque.

## Usar gerenciadores de autenticação e senha de DOIS fatores

Nunca compartilhe senhas. Cada usuário administrador deve ter sua própria conta com a ACL apropriada. Certifique-se de que a identificação de dois fatores nunca seja desativada ou removida. Se você fornecer acesso de administrador a terceiros, verifique se a senha é gerada por um gerenciador de senhas e nunca é reutilizada.

## Verificações de malware

Verificações de malware normalmente são encontradas em um provedor de hospedagem que tenta se especializar no Adobe Commerce. Esta biblioteca de malware e explorações conhecidos é uma lista cada vez maior à medida que novas ameaças são descobertas, testadas e diagnosticadas. Verifique se o provedor de hospedagem tem esse serviço e se ele pode ser executado automaticamente ou somente mediante solicitação. Também há serviços que você pode assinar e que podem usar sua própria biblioteca de explorações conhecidas para verificar constantemente se há explorações em seu aplicativo de comércio. Alguns deles são apenas externos, outros podem ser adicionados à infraestrutura para fornecer uma verificação interna detalhada de todas as pastas, arquivos e até mesmo do banco de dados. Existem alguns provedores com anos de experiência nesta arena, desde Sansec.io até Sucuri e, claro, MageReport. Algumas são gratuitas e outras têm um custo associado. Saber que isso está disponível e ter uma conversa atenciosa com seu arquiteto da Adobe Commerce e a equipe do DevOps garantirá que você encontre a solução certa.

## Ferramenta de análise do site para o Commerce

A variável [Ferramenta de análise do site](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} O é uma ferramenta de autoatendimento proativa e um repositório central que inclui insights e recomendações detalhados do sistema para garantir a segurança e a operabilidade da instalação do Adobe Commerce. Ele fornece monitoramento de desempenho em tempo real, relatórios e conselhos 24 horas por dia, 7 dias por semana, para identificar possíveis problemas e melhor visibilidade das configurações de integridade, segurança e aplicativos do site. Ele ajuda a reduzir o tempo de resolução e a melhorar a estabilidade e o desempenho do site.

## Habilite e verifique as configurações para o Registro de Ações Administrativas

Isso pode ser encontrado depois de fazer logon no administrador do Adobe Commerce e navegar até Lojas > Configuração > Avançado > Administrador > Log de ações do administrador. Isso fornece uma lista de eventos que são monitorados e registrados. É útil ao fazer análises forenses em um site explorado, se a suspeita for de que eles ganharam acesso ao administrador do Commerce. Esse registro e relatório podem ser úteis para ver quais eventos o ator incorreto executou. Se qualquer registro de ações do administrador estiver desativado, isso é um sinal de que alguém pode tê-las desativado para cobertura, remova o registro ao executar determinadas ações.

## Bastion Server para acesso ao ssh

Isso é mais difícil de explicar que a maioria dos tópicos do tutorial Conceitos de segurança. A ideia básica para isso é fornecer um servidor que atue como intermediário para o acesso ao ssh. Dessa forma, seus servidores de produção nunca permitem conexões ssh externas. Você pode criar esse servidor bastião e usar uma máscara IP local para garantir que somente os servidores designados tenham permissão para inserir SSH neles.

## Revisar funções e permissões de ACL

Cada usuário administrador do Adobe Commerce recebe uma função de ACL. Essa função deve ser criada para fornecer somente a funcionalidade necessária para executar o trabalho. As funções da ACL devem ser avaliadas com frequência para garantir que não forneçam mais autoridade do que o necessário. Se necessário, crie muitas funções de ACL com responsabilidades. Se o acesso for concedido a terceiros por algum motivo, eles devem ser desativados o mais rápido possível. Pergunte a eles por quanto tempo precisam absolutamente de acesso e definir uma data de expiração automática ao criar seu usuário administrador.

## Auditoria de usuários administradores e acesso a usuários do SSH com frequência

Para detectar a criação indesejada ou não autorizada de usuários administradores, a lista de usuários administradores deve ser auditada com frequência. Uma boa regra geral é verificar quem tem acesso SSH e de administrador ao aplicativo do Adobe Commerce mensalmente. Se algum usuário novo for detectado, desative a conta dele e siga a política e o procedimento da empresa para esse incidente. É mais fácil restabelecer o acesso de um usuário do que recuperá-lo de uma exploração.

## Limpeza do banco de dados

Limite o acesso aos dados de produção. Esses colegas de equipe designados devem ter a capacidade de extrair bancos de dados de produção e limpá-los de dados reais. Se a remoção dos dados for uma opção, trunque as tabelas apropriadas, como pedidos, cotas e clientes. No entanto, às vezes você quer o conjunto completo de dados, mas os valores podem ser anonimizados. Normalmente, isso é verdadeiro em um ambiente de preparo. Também é útil antes de atualizações. Com o volume real de dados, mas anônimo garante que você esteja testando e validando o tempo para executar uma implantação para atualização corretamente. Caso tenha um conjunto limitado de dados, você pode subestimar o processo de atualização e o tempo.

+++Randomize o exemplo de informações do cliente Veja um exemplo de como alterar o endereço de email do cliente com uma sequência aleatória e todos os campos de nome e sobrenome em algumas tabelas padrão que o Adobe Commerce armazena dados. **Lembre-se de verificar se há dados confidenciais em todas as tabelas, essa lista não inclui todas as tabelas que podem armazenar dados do cliente**

```SQL
SET FOREIGN_KEY_CHECKS=0;
UPDATE customer_entity SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE email_contact SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE sales_invoice_grid SET customer_email = 'customer@example.com', customer_name  = 'Jack Smith';
UPDATE sales_order SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Smith', remote_ip = '127.0.0.1';
UPDATE sales_order_address SET region = 'Ohio', postcode = '12345-1234', lastname = 'Smith', street = '123 Main street', region_id = 44, city = 'Phoenix', telephone = NULL, firstname = 'Jane', company = NULL;
UPDATE sales_order_grid SET customer_email = 'customer@example.com', shipping_name = 'Jack', billing_name = 'Jack Smith', billing_address = '123 Main Street', shipping_address = '321 Pine Street', customer_name = 'Jane Smith';
UPDATE sales_shipment_grid SET customer_email = 'customer@example.com', customer_name = 'Jane Smith', billing_address = '123 Main street', billing_name = 'Jack Doe', shipping_name = 'Susie Smith';
UPDATE quote SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Jones', customer_dob = NULL, remote_ip = '127.0.0.1';
UPDATE quote_address SET email = 'customer@example.com', firstname = 'Jack', lastname = 'Smith', company = NULL, street = '123 Main st', city = 'AnyCity', region = 'Some State', region_id = 44, postcode = '12345-1234', telephone = NULL;
UPDATE magento_rma SET customer_custom_email = 'customer@example.com' WHERE customer_custom_email IS NOT NULL;
UPDATE customer_address_entity SET firstname = 'Jack', lastname = 'Smith', telephone = '909-555-1212', postcode = NULL,  region = NULL, street = '123 Main street', city = 'Anycity', company = NULL;
UPDATE customer_grid_flat SET name = 'Jane Doe', email = 'customer@example.com', dob = NULL, gender = NULL, taxvat = NULL, shipping_full = '', billing_full = '', billing_firstname = 'Jack', billing_lastname = 'Smith', billing_telephone = NULL, billing_postcode = NULL, billing_country_id = NULL, billing_region = NULL, billing_street = '123 Main street', billing_city = 'Anycity', billing_fax = NULL, billing_vat_id = NULL, billing_company = NULL;
UPDATE sales_creditmemo_grid SET billing_name = 'Sally', billing_address = '123 Main Street', customer_name = 'Jack Smith', customer_email = 'customer@example.com';
    
UPDATE magento_rma_grid SET customer_name = 'Jack Smith';
SET FOREIGN_KEY_CHECKS=1;
```

+++


+++Também é possível truncar tabelas em vez de tentar tornar as tabelas anônimas

```SQL
SET FOREIGN_KEY_CHECKS=0;
TRUNCATE customer_log;  
TRUNCATE customer_visitor;  
TRUNCATE magento_logging_event;
TRUNCATE oauth_consumer;
TRUNCATE oauth_nonce;
TRUNCATE oauth_token;
TRUNCATE password_reset_request_event;
TRUNCATE acknowledgement;
TRUNCATE acknowledgement_report;
TRUNCATE avatax_log;
TRUNCATE avatax_queue;
TRUNCATE cron_schedule;
SET FOREIGN_KEY_CHECKS=1;
```

+++

+++Remover informações por completo Exemplo Veja um exemplo para remover todos os pedidos, cotações, avisos de crédito e muito mais antes do lançamento ou para um ambiente de desenvolvimento inferior

```SQL
DELETE FROM `gift_message`;
DELETE FROM `inventory_reservation`;
DELETE FROM `quote`;
DELETE FROM `quote_address`;
DELETE FROM `quote_address_item`;
DELETE FROM `quote_id_mask`;
DELETE FROM `quote_item`;
DELETE FROM `quote_item_option`;
DELETE FROM `quote_payment`;
DELETE FROM `quote_shipping_rate`;
DELETE FROM `reporting_orders`;
DELETE FROM `sales_bestsellers_aggregated_daily`;
DELETE FROM `sales_bestsellers_aggregated_monthly`;
DELETE FROM `sales_bestsellers_aggregated_yearly`;
DELETE FROM `sales_creditmemo`;
DELETE FROM `sales_creditmemo_comment`;
DELETE FROM `sales_creditmemo_grid`;
DELETE FROM `sales_creditmemo_item`;
DELETE FROM `sales_invoice`;
DELETE FROM `sales_invoiced_aggregated`;
DELETE FROM `sales_invoiced_aggregated_order`;
DELETE FROM `sales_invoice_comment`;
DELETE FROM `sales_invoice_grid`;
DELETE FROM `sales_invoice_item`;
DELETE FROM `sales_order`;
DELETE FROM `sales_order_address`;
DELETE FROM `sales_order_aggregated_created`;
DELETE FROM `sales_order_aggregated_updated`;
DELETE FROM `sales_order_grid`;
DELETE FROM `sales_order_item`;
DELETE FROM `sales_order_payment`;
DELETE FROM `sales_order_status_history`;
DELETE FROM `sales_order_tax`;
DELETE FROM `sales_order_tax_item`;
DELETE FROM `sales_payment_transaction`;
DELETE FROM `sales_refunded_aggregated`;
DELETE FROM `sales_refunded_aggregated_order`;
DELETE FROM `sales_shipment`;
DELETE FROM `sales_shipment_comment`;
DELETE FROM `sales_shipment_grid`;
DELETE FROM `sales_shipment_item`;
DELETE FROM `sales_shipment_track`;
DELETE FROM `sales_shipping_aggregated`;
DELETE FROM `sales_shipping_aggregated_order`;
DELETE FROM `tax_order_aggregated_created`;
DELETE FROM `tax_order_aggregated_updated`;
DELETE FROM `magento_rma`;
DELETE FROM `magento_rma_grid`;
DELETE FROM `magento_rma_item_entity`;
DELETE FROM `magento_rma_status_history`;
DELETE FROM `magento_sales_creditmemo_grid_archive`;
DELETE FROM `magento_sales_invoice_grid_archive`;
DELETE FROM `magento_sales_order_grid_archive`;
DELETE FROM `magento_sales_shipment_grid_archive`;
DELETE FROM `sequence_creditmemo_0`;
DELETE FROM `sequence_creditmemo_1`;
DELETE FROM `sequence_creditmemo_2`;
DELETE FROM `sequence_creditmemo_7`;
DELETE FROM `sequence_invoice_0`;
DELETE FROM `sequence_invoice_1`;
DELETE FROM `sequence_invoice_2`;
DELETE FROM `sequence_invoice_7`;
DELETE FROM `sequence_order_0`;
DELETE FROM `sequence_order_1`;
DELETE FROM `sequence_order_2`;
DELETE FROM `sequence_order_7`;
DELETE FROM `sequence_rma_item_0`;
DELETE FROM `sequence_rma_item_1`;
DELETE FROM `sequence_rma_item_2`;
DELETE FROM `sequence_rma_item_7`;
DELETE FROM `sequence_shipment_0`;
DELETE FROM `sequence_shipment_1`;
DELETE FROM `sequence_shipment_2`;
DELETE FROM `sequence_shipment_7`;

## USE THE FOLLOWING WITH CAUTION - CAN CAUSE ISSUES WITH TAX/PAYMENT PROCESSORS IF YOU REUSE ORDER NUMBERS, ETC.

ALTER TABLE sequence_creditmemo_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_7 AUTO_INCREMENT=1;
```

+++

## Usar variáveis de ambiente

[!BADGE Adobe Commerce somente na nuvem]{type=Informative}

O uso de variáveis de ambiente ajuda, permitindo que você defina determinados valores que podem e devem ser alterados para cada ambiente. Por exemplo, talvez você queira ter um URL de administrador diferente para cada ambiente. Ao definir esse valor como uma Variável de ambiente, é possível configurá-lo e também fazer referência a esse valor rapidamente na interface do usuário da nuvem, quando necessário.

Você pode ler mais sobre este tópico no Experience League [Variáveis de ambiente do Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## Ferramentas de verificação de vulnerabilidade de software

O pipeline de CI/CD pode ser uma ferramenta poderosa e ajudar a automatizar algumas tarefas. Em particular, a oportunidade para um desenvolvedor confirmar um código que pode ser explorável é sempre uma possibilidade real. As revisões de código por pares normalmente capturam esses itens, mas como é um ser humano, ocorrem erros. A varredura de código automatizada ajuda a reduzir a oportunidade de vulnerabilidades inesperadas em um recurso recém-introduzido. Essas ferramentas podem até estar em vigor para bloquear a mesclagem de código na base de código ativa. Há muitas maneiras e ferramentas de oferecer verificações automatizadas de segurança e qualidade do código. Pode haver ferramentas robustas e personalizadas, mas elas exigem atualizações e ajustes constantes. Uma alternativa é aplicar ferramentas atualizadas proativamente, como synk.io e o Inspetor de código do Amazon.

## Firewall de Aplicativo Web

Um Firewall de Aplicativo Web ou WAF, como é usado com frequência ao se comunicar com DevOps ou um provedor de hospedagem.

Os firewalls de aplicações Web (WAFs) impedem que tráfego mal-intencionado entre em sites e redes ao filtrar o tráfego em relação a um conjunto de regras de segurança. O tráfego que aciona qualquer uma das regras é bloqueado antes que possa danificar seus sites ou a rede.

O Adobe Commerce Cloud WAF fornece uma política WAF com um conjunto de regras projetado para proteger seus aplicativos Web Adobe Commerce de uma ampla variedade de ataques. Se você escolher uma opção de auto-hospedagem, encontrar um WAF e configurar as regras são sua responsabilidade. Alguns provedores de hospedagem e provedores de WAF têm um conjunto genérico de regras que são um bom início, no entanto, esperam que algum trabalho funcione para o seu projeto.

O WAF examina o tráfego da Web e do administrador para identificar qualquer atividade suspeita. Ele avalia o GET e o tráfego de POST (chamadas de API HTTP) e aplica o conjunto de regras para determinar qual tráfego bloquear. O WAF pode bloquear uma grande variedade de ataques, incluindo ataques de injeção de SQL, ataques de script entre sites, ataques de exfiltração de dados e violações de protocolo HTTP.

Como um serviço baseado em nuvem, o WAF não requer hardware ou software para instalar ou manter. O Fastly, um parceiro de tecnologia existente, fornece o software e a experiência. Seu WAF sempre ativo e de alto desempenho reside em cada nó de cache na rede de delivery global do Fastly.

Para obter mais informações sobre o WAF no Adobe Commerce na nuvem fornecido pela Fastly, leia o [Perguntas frequentes sobre a Base de conhecimento Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
