---
title: Listas de verificação de requisitos
description: Use esta lista de perguntas abrangentes para ajudar você a se preparar para uma implementação do Adobe Commerce.
exl-id: 9ac485c5-d491-4022-9366-5e3a382513b6
source-git-commit: d18be812626723e203d2308be8c3f9783a19b43b
workflow-type: tm+mt
source-wordcount: '1536'
ht-degree: 0%

---

# Listas de verificação de requisitos

As seguintes questões podem servir de ponto de partida para ver quais as informações que devem ser documentadas para confirmar a preparação em termos de organização. Também podem ajudar no desenvolvimento de um RFP.

## Negócios

- Quais são os objetivos comerciais da nova plataforma de comércio eletrônico?

- Quais são os motivos para alterar sua plataforma de comércio eletrônico atual?

- Quais são os objetivos da infraestrutura do site?

- Qual é o seu período de entrega da nova plataforma de comércio eletrônico?

- Quantos de seus gerentes de projeto de TI serão atribuídos a este projeto?

- Quantos dos seus analistas empresariais serão atribuídos a este projeto?

- Quantos dos seus analistas técnicos serão atribuídos a este projeto?

- Quantos dos seus desenvolvedores do HTML serão atribuídos a este projeto?

- Que documentação existe para os processos de negócios atuais?

- Qual documentação existe para as integrações de sistema atuais?

- Qual documentação existe para os fluxos de processo atuais?

- Que documentação existe para os fluxos de dados atuais?

- Quem vai fornecer o treinamento?

- Que formação estará concluída antes da ativação?

- Qual o treinamento a ser concluído após a ativação?

- Qual suporte Adobe Commerce será necessário após o lançamento?

- Este projeto depende de outros projetos de desenvolvimento de sistemas?

- Como você vê suas vendas crescendo nos próximos 12 a 24 meses?

- Quem são seus principais concorrentes? Forneça links para seus sites. Como você deseja diferenciar sua experiência online de seus concorrentes?

- De onde você vê o crescimento futuro vindo em sua empresa?

- Qual o papel do comércio digital na sua estratégia de negócios? Quais são seus principais objetivos para configurar essa plataforma de comércio eletrônico?

- Você tem alguma marca/empresa que use como referência em como expandir seu negócio omnicanal?

- Quais equipes ou indivíduos estão liderando a estratégia de comércio eletrônico? Descreva as posições relevantes.

## Plataforma atual

- Como a plataforma atual está sendo hospedada: Interno, provedor de hospedagem, servidores de nuvem privados ou servidores de nuvem hospedados?

- Quais ambientes a plataforma atual tem: desenvolvimento, controle de qualidade, pré-produção, produção?

- Quantos servidores da Web e de banco de dados estão no ambiente de desenvolvimento?

- Quantos servidores da Web e de banco de dados estão no ambiente de controle de qualidade?

- Quantos servidores da Web e de banco de dados estão no ambiente de preparo (pré-produção)?

- Quantos servidores da Web e de banco de dados estão no ambiente de produção?

- É uma arquitetura de vários servidores com balanceamento de carga?

- É uma arquitetura de sistema de alta disponibilidade?

- Que problemas você está enfrentando com seus sites atuais?

- Tamanho atual do catálogo (número de SKUs)?

- Média de visitantes por dia?

- Média de sessões simultâneas por hora?

- Média de exibições de página por dia?

- Média de pedidos por hora e por dia?

## Requisitos da plataforma esperados

- Qual versão do Adobe Commerce você usará?

- Como a futura plataforma será hospedada: Interno, provedor de hospedagem, servidores de nuvem privados ou servidores de nuvem hospedados?

- Quais ambientes terão a futura plataforma: desenvolvimento, controle de qualidade, pré-produção, produção?

- Quantos servidores da Web e de banco de dados estarão no ambiente de desenvolvimento?

- Será uma arquitetura de sistema de alta disponibilidade?

- Quantos administradores do Adobe Commerce você terá?

- Tamanho esperado do catálogo (número de SKUs)?

- Média esperada de visitantes por dia?

- Média esperada de sessões simultâneas por hora?

- Média esperada de exibições de página por dia?

- Que dados devem ser importados do site antigo para o novo site? (Exemplo: produto, cliente, histórico do pedido)

## Sites

- Quantos sites domésticos serão implementados?

- Que línguas serão implementadas?

- Quantos sites internacionais serão implementados?

- Quais regiões serão apoiadas pelos websites?

- Que línguas serão implementadas?

- Que moedas serão implementadas?

- Você tem contratos de nível de serviço de entrega para cada país?

- Quem são seus provedores de entregas para cada país?

- Quem são os seus prestadores de contas fiscais para cada país?

- Você precisará de um tema de site internacional personalizado?

- Isso é principalmente um site B2C ou B2B? Existe algum elemento B2B2B ou B2B2C?

- Existe um design existente que é adaptado ou a plataforma será projetada do zero?

- Existe um requisito para o comércio sem periféricos (camadas de front-end e back-end separadas)?

- Quais são os pontos de interrupção (tablet/dispositivo móvel) para o design responsivo?

- Existe um requisito para um aplicativo móvel? O PWA deve ser aproveitado para o front-end móvel?

- Qualquer navegador específico que deve ser testado (exceto para os navegadores padrão IE9+, Firefox, Chrome, Safari)?

- Quais são os idiomas de cada frontend? O conteúdo traduzido está disponível ou o suporte é necessário?

- Há vários sites da Web? Em caso afirmativo, os clientes podem usar suas credenciais em todos os sites?

- Os dados do produto são compartilhados em todos os sites?

- Há alterações no design de site para site?

- Há opções de assinatura e como os assinantes são gerenciados?

- Existem requisitos específicos de SEO? Como o marketing do mecanismo de pesquisa é gerenciado?

## Integrações

- Qual sistema CMS será integrado ao Adobe Commerce? (Exemplos: WordPress, Drupal, Concreto5)

Há APIs existentes que podem ser usadas?

- O tratamento de erros de sistema foi projetado e desenvolvido para essa integração de sistemas de terceiros?

- Qual sistema ERP será integrado ao Adobe Commerce? (Exemplos: SAP, MS Dynamics NAV)

- Qual sistema de transportadora será integrado à Adobe Commerce?

- Qual sistema de software fiscal será integrado ao Adobe Commerce? (Exemplo: Taxware)

- De qual sistema os dados do produto serão importados para o Adobe Commerce?

- Frequência dos carregamentos de dados de produtos importados?

- Em qual sistema a Adobe Commerce exportará os dados do produto?

- Frequência de carregamentos de dados de produtos exportados?

- De qual sistema os dados serão importados para o Adobe Commerce?

- Frequência dos carregamentos de dados de pedidos importados?

- Em qual sistema a Adobe Commerce exportará os dados do pedido?

- Frequência dos carregamentos de dados de pedido exportados?

- Qual plataforma de análise é usada? (Exemplos: Adobe Analytics, Google Analytics)

- Haverá logon único e compartilhamento de rede social? Em caso afirmativo, quais são as redes sociais?

- Há recompensas ou programas de fidelidade em vigor? Existe alguma integração com sistemas POS para recompensas?

- Como os retornos de produtos são tratados? Espera-se que o cliente registre uma solicitação de retorno on-line?

- É necessária uma ferramenta de bate-papo online? É necessário um chatbot?

- Qual gateway de pagamento você deseja que seu site tenha?

- Qual sistema de gerenciamento de pedidos será integrado ao Adobe Commerce? (Exemplos: Microsoft Dynamics, SAP, Retail Pro)

- Qual sistema de gerenciamento de informações do produto será integrado ao Adobe Commerce? (Exemplos: Akeneo, InRiver, Bluestone)

- Qual sistema de gerenciamento de relacionamento com o cliente será integrado ao Adobe Commerce? (Exemplos: Hubspot, Salesforce, Klaviyo)

## Recursos específicos do Adobe Commerce

- Você precisará de algum tipo de teste A/B?

- Quantos administradores simultâneos podem estar trabalhando no sistema?

- Você permitirá que um cliente pegue itens comprados no site em uma loja?

- Você terá páginas promocionais?

- Você terá banners de marketing?

- Deseja que os vídeos sejam reproduzidos em uma página CMS?

- Qual será a frequência de modificação ou atualização de conteúdo?

- Que tipo de conteúdo será carregado?

- As atualizações de conteúdo serão agendadas?

- Você precisará de um site de preparo de conteúdo?

- Os clientes devem ter permissão para criar uma conta no site?

- Você usará cupons de desconto exclusivos para promoções?

- Você terá preços promocionais?

- Você terá cupons flexíveis (capacidade de definir por site, grupo de clientes, tempo, categorias ou produtos)?

- Os descontos percentuais serão oferecidos para itens únicos?

- Que tipo de funcionalidade de brinde será necessária?

- A funcionalidade do programa de recompensas será necessária?

- A funcionalidade do boletim informativo será necessária?

- Permitir que um cliente visualize ordens anteriores e selecione itens a serem trocados?

- Você permitirá que um cliente inicie o cancelamento de um pedido do site?

- Você permitirá que um cliente inicie a troca de itens do site?

- Você precisará da validação de endereço em tempo real?

- Você permitirá que um cliente inicie o retorno dos itens do site?

- A Adobe Commerce emitirá um RMA de retorno?

- Capturar informações de reembolso no Adobe Commerce?

- Você precisará de um rastreamento de pedido online para um cliente registrado?

- Você precisará de um rastreamento de pedido online para um cliente convidado?

- Executar autorização on-line e captura durante o posicionamento do pedido?

- Autorização com filtro de fraude durante a colocação de pedidos com captura atrasada

- Número de dias para receber o pagamento integral (sem autorização)?

- Capturar e executar após o termo da autorização?

- Authorize.net

- Braintree

- PayPal Express

- Crédito da loja

- Cartão-presente de plástico

- Pontos positivos

- &quot;Fale-me Mais Tarde&quot; - mais comumente conhecida como &quot;Compre Agora, Pague Depois&quot;, pois é imediatamente cobrado, mas ainda não paga

- Haverá preços de produtos diferentes em sites diferentes?

- A funcionalidade para comparar produtos diferentes será necessária?

- Que tipos de produtos você venderá?

- Qual será a frequência da adição de novos produtos?

- Qual será a frequência da atualização de produtos?

- Qual será a frequência da criação de novas categorias ou subcategorias?

- A funcionalidade &quot;Classificações e revisões&quot; será necessária?

- Você permitirá que os clientes recomendem um produto?

- Vendas: Pedidos, imposto, faturado, remessa, reembolsos, cupons, relatórios de liquidação PayPal

- Carrinho de compras: Produtos em carrinhos, artes abandonadas

- Produtos: Vendedores, produtos solicitados, mais visualizados, baixo estoque, downloads

- Clientes: Novas contas, total de clientes por ordens, clientes por número de ordens, segmentos de clientes, revisões de clientes

- Revisões de produtos

- Tags: Clientes, produtos, populares

- Termos de pesquisa

- Convites: Geral, clientes, taxa de conversão de pedido

- Você precisará do Adobe Commerce para gerar relatórios com base nos dados de uso do cupom?

- Você precisará que o Adobe Commerce gere relatórios com base nos dados de vendas?

- Você precisará de relatórios personalizados do Adobe Commerce?

- Qual é sua estratégia atual de SEO?

- Qual será sua nova estratégia de SEO?

- Quais são seus requisitos para a migração de SEO?

- Armazenar taxas fixas no Adobe Commerce?

- Permitir envio parcial?

- As informações de rastreamento de remessa devem ser armazenadas no Adobe Commerce?

- Você precisará de regras de cálculo de impostos para suas regiões domésticas?

- Exigirá regras de cálculo de impostos para as suas regiões internacionais?
