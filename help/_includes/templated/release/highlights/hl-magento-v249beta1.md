---
source-git-commit: 65a9bd667d434f1deae69798696f66998e6024a0
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 0%

---
# Destaques do Magento Open Source (v2.4.9-beta1)

## Destaques na v2.4.9-beta1

Os destaques a seguir se aplicam à versão 2.4.9-beta1 do Magento Open Source.

### APIs

#### Adição de uma possibilidade de manter a herança da galeria de produtos na API REST ao atualizar um produto no nível de exibição da loja

A atualização de produto por meio da API REST em um escopo de armazenamento não faz mais com que imagens e vídeos de produto herdem alterações do escopo global se as entradas media_gallery_entries forem omitidas da carga ou definidas como NULL para evitar alterações na galeria de produtos nesse escopo. Além disso, agora é possível restaurar a herança do escopo de imagens e vídeos do produto por meio da API REST, definindo o campo correspondente como NULL.

_ACP2E-4358 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Estrutura

#### Investigue a versão principal mais recente do web-token/jwt-framework

Como parte do processo contínuo de revisão de segurança, avaliamos a versão principal mais recente da estrutura JWT para garantir a compatibilidade futura e manter padrões de segurança sólidos. Não há impacto sobre a funcionalidade existente nesta versão.

_AC-13209 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### Substituir carlos-mg89/oauth pelas funções nativas do PHP

Substituição da biblioteca carlos-mg89/oauth de terceiros por funções OAuth nativas do PHP para melhorar a segurança, reduzir as dependências externas e melhorar a estabilidade da plataforma.

_AC-14075 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### Investigar a versão mais recente do chart.js

Atualização da biblioteca de gráficos JavaScript Chart.js para a versão mais recente 4.4.8 para melhorar o desempenho de renderização do gráfico, aprimorar os recursos visuais e corrigir vulnerabilidades de segurança no painel de administração e nos módulos de relatórios.

_AC-14304 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/768b4442)_

#### Investigue a versão mais recente do jquery/uppy e uppy

Atualização da biblioteca de upload de arquivo Uppy para a versão 4.13.4 para aprimorar os recursos de upload de arquivo, melhorar a experiência do usuário e corrigir vulnerabilidades de segurança no manuseio de arquivos na interface do administrador do Adobe Commerce e em componentes de front-end.

_AC-14307 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/eb491c05)_

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

#### Atualize a versão allure-framework/allure-phpunit para 3 e remova a dependência nativa em 2.4.9-alpha1

No Adobe Commerce 2.4.9, a dependência allure-framework/allure-phpunit foi atualizada para a versão principal 3, que adiciona suporte para PHP 8.4, PHP 8.5 e moderniza nossa pilha de relatórios de teste com base em Allure. A dependência nativa anteriormente exigida pelas versões mais antigas do Allure PHPUnit foi removida, onde aplicável, simplificando a configuração e a manutenção.

_AC-14548 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Atualizar a dependência do chart.js para a versão mais recente

A dependência do chart.js foi atualizada para a versão mais recente 4.5.0

_AC-15133 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Adicionar suporte oficial para Symfony 7.4 LTS e PHP 8.5 no Adobe Commerce 2.4.9

Como parte das atualizações da plataforma Adobe Commerce 2.4.9, todas as dependências do Symfony usadas pelo pacote magento/composer foram atualizadas para as versões mais recentes do Symfony LTS 7.4. Isso alinha as ferramentas do Commerce Composer com a linha atual do Symfony LTS e remove as restrições de dependência anteriores relacionadas às versões mais antigas do Symfony. Além disso, todas as classes personalizadas que estendem as classes principais do Symfony atualizaram as declarações de tipo e assinaturas de método alinhadas aos requisitos mais recentes do Symfony antes de atualizar para o Adobe Commerce 2.4.9. Isso evitará problemas de compatibilidade e garantirá uma transição suave para os componentes da estrutura atualizados.

_AC-15170 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/c127d10b)_

### Outro

#### Captcha / reCaptha não está funcionando para API / GraphQl

No Adobe Commerce 2.4.9, quando CAPTCHA (ou reCAPTCHA) é ativado para o formulário Criar conta, a mesma validação CAPTCHA agora é imposta para a criação de contas de clientes por meio das APIs REST e GraphQL.

_AC-16245 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/fd7f30ee)_

### Segurança

#### Melhorar o desempenho de solicitações assíncronas/em massa

Correção da degradação de desempenho em pontos de extremidade da Web assíncronos em massa introduzidos após o patch de segurança APSB25-08, resultando em maior tempo de execução.

_AC-14078 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### Exigir que apenas um provedor 2FA habilitado seja configurado por usuário

Os usuários administradores agora precisam configurar apenas um dos provedores 2FA habilitados do comerciante (por exemplo, Google Authenticator ou U2F) para acessar o painel Administrador. Provedores ativados adicionais podem ser configurados posteriormente, conforme necessário. Anteriormente, quando vários provedores 2FA eram ativados (por exemplo, Google Authenticator e U2F), cada usuário administrador era solicitado a configurar todos os provedores ativados antes que pudesse fazer logon. Isso criou atrito para usuários que não tinham acesso a todos os fatores (como uma chave de hardware para U2F).

_AC-8253 - [Contribuição de código do GitHub](https://github.com/magento/security-package/commit/71e7936b)_

### Preparo e visualização

#### [Solicitação de recursos] Visualização de preparo de conteúdo no modo de exibição móvel

O recurso de visualização de preparo no painel de administração agora permite que as visualizações do dispositivo móvel simuladas em navegadores sejam renderizadas com precisão, fornecendo uma representação visual de como a atualização de preparo aparecerá em um dispositivo móvel.

_ACP2E-3397 - [Contribuição de código do GitHub](https://github.com/magento/magento2/commit/520f9e30)_
