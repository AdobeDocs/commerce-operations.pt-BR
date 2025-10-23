---
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---
# Notas de versão do Magento Open Source (v2.4.9-alpha2)

## Destaques na v2.4.9-alpha2

Os destaques a seguir se aplicam à versão 2.4.9-alpha2 do Magento Open Source.

### Estrutura

#### Adicionar suporte para OpenSearch 3

O Adobe Commerce 2.4.9 agora é totalmente compatível com o OpenSearch 3.x. Essa atualização permite que os comerciantes se beneficiem de melhor desempenho, segurança e suporte a longo prazo, mantendo a compatibilidade com versões anteriores do OpenSearch 2.x.

_AC-11846_

#### Atualização da versão Nginx de 1.26 para 1.28

A versão do Nginx usada em ambientes de desenvolvimento e teste em todas as versões atualmente compatíveis do Adobe Commerce é atualizada de 1.26 para 1.28, alinhando-se com a versão estável mais recente do Nginx disponível.
O teste de nível PR agora é executado em relação ao Nginx 1.28, confirmando a compatibilidade e o suporte totais para todas as versões do Adobe Commerce.

_AC-14104_

#### Investigue a versão mais recente do jquery-validate

Atualização da biblioteca jQuery Validate para a versão 1.21.0 para aprimorar os recursos de validação de formulários, melhorar a experiência do usuário e garantir a compatibilidade moderna do navegador em todos os Adobe Commerce Forms nas interfaces de administrador e de front-end.

_AC-14403 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Investigue a versão mais recente da jquery-ui

A biblioteca da interface do usuário jQuery foi atualizada para a versão 1.14.1 para aprimorar os widgets da interface do usuário, melhorar a acessibilidade e garantir a compatibilidade moderna do navegador em todos os componentes de administração e interface de front-end do Adobe Commerce.

_AC-14417 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### Investigar a versão mais recente less.js

Atualização do pré-processador de CSS Less.js para a versão 4.2.2 para aprimorar o desempenho da compilação de CSS, melhorar o suporte à sintaxe e modernizar o processo de criação de tema em todos os temas de front-end e de administrador do Adobe Commerce.

_AC-14418 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Investigue a versão mais recente do Moment-Timzone-with-data.js

Atualização da biblioteca Fuso horário de momento para a versão 0.5.43 para aprimorar os recursos de manipulação de fuso horário, atualizar os dados de fuso horário com as alterações mais recentes do banco de dados de fuso horário IANA e melhorar a precisão do processamento de data/hora em todas as operações internacionais e de vários fusos horários da Adobe Commerce.

_AC-14419 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Investigue a versão mais recente underscore.js

Atualização da biblioteca de utilitários Underscore.js para a versão 1.13.7 para aprimorar os recursos de programação funcional do JavaScript, melhorar o desempenho da manipulação de dados e garantir a compatibilidade moderna do navegador em todos os componentes de front-end e interface de administrador do Adobe Commerce.

_AC-14420 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Migração do TinyMCE para o Hugerte.org

Devido ao fim do suporte para o TinyMCE 5 e 6 e às incompatibilidades de licenciamento com o TinyMCE 7, a implementação atual do editor do Adobe Commerce WYSIWYG é migrada do TinyMCE para o editor HugeRTE de código aberto (https://hugerte.org/).
Essa migração garante que o Adobe Commerce permaneça em conformidade com o licenciamento de código aberto, evita vulnerabilidades conhecidas do TinyMCE 6 e fornece uma experiência de edição moderna e compatível para comerciantes e desenvolvedores.

_AC-14568_

#### Adicionar suporte completo ao Valkey 8.x para 2.4.9-alpha2

O Adobe Commerce 2.4.9 tem um suporte completo a comandos CLI para Valkey, espelhando a funcionalidade Redis existente no momento. Configuração de administração e nuvem atualizada para permitir configuração perfeita do Valkey.
Essa atualização garante que o Adobe Commerce permaneça inovador e com bom desempenho, oferecendo suporte ao Valkey 8.x, proporcionando aos comerciantes e desenvolvedores uma alternativa confiável para o Redis quando chegar ao fim da vida útil.

_AC-14604_

### Outro

#### Atualizar o serviço AWS Valkey 8.x para build e teste do CNS

Atualizar o serviço AWS Valkey 8.x para build do CNS

_AC-14470_

#### 2.4.9-alpha2 - Melhorias da qualidade principal de agosto

_AC-14700_

### Segurança

#### Melhorias de segurança para 2.4.9-alpha2

_AC-14610_

### Envio

#### Migrar a integração USPS de APIs de Ferramentas da Web desatualizadas para novas APIs RESTful USPS

Para estar em conformidade com o anúncio da desativação das APIs herdadas de ferramentas da Web pelo USPS até 25 de janeiro de 2026, a integração do USPS do Adobe Commerce será migrada para as novas APIs do USPS RESTful.

Principais aprimoramentos:

* Suporte à API dupla: os usuários administradores agora podem escolher entre a API herdada de Ferramentas da Web e a nova API RESTful USPS por meio das configurações.
* Atualização de autenticação: OAuth 2.0 implementado para acesso seguro à API.
* Formato de dados aprimorado: transição de XML para JSON para uma comunicação mais limpa e eficiente.
* Novos campos de administrador:
   * URL REST do gateway (com base no modo: Desenvolvimento ou Ativo)
   * Segredo do ID do cliente &amp;amp;
   * Tipo de conta, Número da conta
   * CRID, MID, Código de identificação do correio
   * AES/ITN para remessas internacionais
   * Métodos de envio permitidos específicos para REST

Essa migração garante que a Adobe Commerce permaneça em conformidade com os padrões USPS, melhora a confiabilidade do sistema e garante integrações de envio que não se tornarão obsoletas para os comerciantes.

_AC-13257_
