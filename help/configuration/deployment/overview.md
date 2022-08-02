---
title: Visão geral da implantação
description: Leia sobre as estratégias de implantação do aplicativo Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---


# Visão geral da implantação

Esses tópicos discutem o processo de implantação do aplicativo Commerce em um site de produção para o Adobe Commerce versão 2.2 e posterior. O Adobe recomenda esse método de implantação para qualquer pessoa com um site grande que não deseje experimentar o tempo de inatividade durante a implantação.

Se você implantar o Commerce em uma única máquina e tolerar algum tempo de inatividade durante a implantação, consulte [Implantação em uma única máquina](../deployment/single-machine.md).

## Implantação de pipeline

Com a versão 2.2 do Commerce, o Adobe foi introduzido _implantação de pipeline_ como uma nova maneira de implantar na produção com o mínimo de tempo de inatividade. Esse processo de implantação ocorre em diferentes sistemas e fornece uma maneira de manter configurações consistentes para todos os sistemas de implantação de pipeline. É um modelo simples, mas eficiente, que permite separar configurações comuns de configurações específicas do sistema (como host e porta) ou configurações confidenciais (como nomes e senhas).

Para usar a implantação de pipeline, o Adobe parte do princípio de que você:

- Um experiente integrador de sistemas com excelente conhecimento das opções de configuração do Adobe Commerce.
- Gerenciar um site comercial grande (milhares de unidades de manutenção de estoque (SKUs)) e manter o tempo de inatividade do site de produção ao mínimo.
- Conhecido sobre programação PHP.
- Experienciado com métodos de controle de origem.
- Seu código está em um repositório de controle de origem. Neste guia, supomos que você esteja usando um repositório baseado em Git.

### Tempo de inatividade reduzido

Ao implantar ativos estáticos e compilar o código em uma máquina separada do sistema de produção, você minimiza o tempo de inatividade. O tempo de inatividade em seu sistema de produção é limitado à quantidade de tempo necessária para transferir arquivos estáticos e código compilado para o servidor.

## Sistemas de implantação

Usamos os termos a seguir para descrever os sistemas envolvidos com a implantação.

- **Sistema de desenvolvimento**—Máquina na qual os desenvolvedores trabalham para personalizar o código; e instale extensões, temas e pacotes de idioma do Commerce Marketplace. Além disso, você faz todas as alterações de configuração em seu sistema de desenvolvimento. Você pode ter muitos sistemas de desenvolvimento.

- **Criar sistema**—Um sistema no qual você implanta ativos estáticos e compila o código para seu sistema de produção. Como você cria esses ativos em um sistema que não está em produção, o tempo de inatividade do sistema de produção é minimizado.

   Seu sistema de build não precisa ter o Commerce instalado nele. Ele precisa apenas do código do Commerce, mas nenhuma conexão de banco de dados é necessária. Além disso, o sistema de build não precisa ser um servidor separado fisicamente.

- **Sistema de armazenamento temporário**—_Opcional_. Opcionalmente, é possível configurar um sistema de preparo para usar o teste final de todo o código integrado, incluindo o UAT (User Acceptance Testing, Teste de aceitação do usuário). Configure um sistema de preparo da mesma maneira que você configura um sistema de produção. Exceto pelo fato de que o armazenamento temporário não é sua loja ativa e não processa pedidos de clientes, é idêntico à produção.

- **Sistema de produção**—Sua loja ao vivo. Você deve fazer alterações mínimas na configuração direta aqui e certamente nada que não tenha sido testado em uma instância de preparo. Se possível, faça alterações na configuração com [Correções de dados](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) que foram testadas em uma instância de preparo/desenvolvimento.

## Outros métodos de implantação

Como opção, você pode usar outros métodos de implantação, incluindo:

- Cópia segura com SCP ou rsync
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- O [Ferramenta Implantador](https://deployer.org/)

## Gerenciar a configuração

Modelagem após [fator 3 no design do aplicativo de 12 fatores](https://12factor.net/config), o Commerce agora armazena a configuração de cada sistema no próprio sistema. (As configurações de desenvolvimento são armazenadas no sistema de desenvolvimento, as configurações de produção são armazenadas no sistema de produção.)

Fornecemos uma maneira de sincronizar a configuração de seus sistemas:

- **Configuração compartilhada**—Configurações que não são específicas do sistema nem confidenciais.

   As configurações compartilhadas são configurações que você deseja que sejam consistentes nos sistemas de desenvolvimento e produção. Defina a configuração compartilhada no Administrador em seu desenvolvimento (ou no Adobe Commerce na infraestrutura em nuvem) _integração_).

   O arquivo de configuração compartilhado, `app/etc/config.php`, deve ser incluído no controle de origem para que possa ser compartilhado entre sistemas de desenvolvimento, construção e produção.

- **Configuração específica do sistema**—Configurações que variam de acordo com o sistema, como nomes de host e portas do mecanismo de pesquisa.

- **Configuração sensível**—Configurações que devem _not_ estar no controle de origem porque eles expõem informações de identificação pessoal (PII) ou configurações como chaves de API ou senhas.

   O arquivo de configuração específico do sistema, `app/etc/env.php`, _not_ ser incluídos no controle de origem ou compartilhados entre sistemas. Em vez disso, use o [`magento config:set` e `magento:sensitive:set` comandos](../cli/set-configuration-values.md) para fornecer valores para essas configurações no sistema de produção.

>[!INFO]
>
>Esses novos métodos para gerenciar sua configuração são opcionais. Não é necessário, mas é altamente recomendável usá-los.

Na maioria das vezes, as opções de configuração definidas na configuração compartilhada, específica do sistema ou confidencial não podem ser editadas no Administrador. Isso ajuda a manter suas configurações consistentes em todos os sistemas. (Opcionalmente, você pode usar a variável [`magento config:set` comando](../cli/set-configuration-values.md) sem a `--lock` para definir configurações editáveis em Admin.).

Cada opção de configuração do Commerce tem uma _caminho da configuração_. Para definir um valor para uma opção de configuração, você pode usar um comando CLI ou uma variável de ambiente para definir o valor desse caminho de configuração em um sistema específico.
