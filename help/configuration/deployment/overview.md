---
title: Visão geral da implantação
description: Leia sobre as estratégias de implantação do aplicativo Commerce.
feature: Configuration, Deploy
exl-id: d5ed6fb3-2dd2-49df-802b-6d712ecd9ccf
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# Visão geral da implantação

Estes tópicos discutem o processo de implantação do aplicativo Commerce em um site de produção do Adobe Commerce versão 2.2 e posterior. A Adobe recomenda esse método de implantação para qualquer pessoa com um site grande que não queira enfrentar o tempo de inatividade durante a implantação.

Se você implantar o Commerce em uma única máquina e puder tolerar algum tempo de inatividade durante a implantação, consulte [Implantação em um único computador](../deployment/single-machine.md).

## Implantação de pipeline

Com a versão 2.2 do Commerce, o Adobe foi introduzido _implantação de pipeline_ como uma nova maneira de implantar na produção com tempo de inatividade mínimo. Esse processo de implantação ocorre em diferentes sistemas e fornece uma maneira de manter configurações consistentes para todos os sistemas de implantação de pipeline. É um modelo simples, mas eficiente, que permite separar definições de configuração comuns de configurações específicas do sistema (como host e porta) ou configurações confidenciais (como nomes e senhas).

Para usar a implantação do pipeline, o Adobe presume que você esteja:

- Um integrador de sistemas experiente, com excelente conhecimento das opções de configuração do Adobe Commerce.
- Gerenciar um grande site do Commerce (milhares de unidades de manutenção de estoque (SKUs)) e manter o tempo de inatividade do site de produção em um nível mínimo.
- Conhecido sobre programação PHP.
- Experiente com métodos de controle de origem.
- Seu código está em um repositório de controle de origem. Neste guia, pressupomos que você esteja usando um repositório baseado em Git.

### Redução do tempo de inatividade

Ao implantar ativos estáticos e compilar código em um computador separado do sistema de produção, você minimiza o tempo de inatividade. O tempo de inatividade do sistema de produção é limitado à quantidade de tempo necessária para transferir arquivos estáticos e código compilado para o servidor.

## Sistemas de implantação

Usamos os termos a seguir para descrever os sistemas envolvidos na implantação.

- **Sistema de desenvolvimento**—Máquina na qual os desenvolvedores trabalham para personalizar o código e instalar extensões, temas e pacotes de linguagem do Commerce Marketplace. Além disso, você faz todas as alterações de configuração no sistema de desenvolvimento. Você pode ter muitos sistemas de desenvolvimento.

- **Criar sistema**— Um sistema no qual você implanta ativos estáticos e compila o código para seu sistema de produção. Como você cria esses ativos em um sistema que não está em produção, o tempo de inatividade do sistema de produção é minimizado.

  Seu sistema de build não precisa ter o Commerce instalado. Ele precisa apenas do código do Commerce, mas nenhuma conexão de banco de dados é necessária. Além disso, o sistema de build não precisa ser um servidor separado fisicamente.

- **Sistema de preparo**—_Opcional_. Opcionalmente, é possível configurar um sistema de preparo para usar no teste final de todo o código integrado, incluindo o Teste de aceitação do usuário (UAT). Configure um sistema de preparo da mesma forma que configura um sistema de produção. Exceto pelo fato de que o armazenamento temporário não é sua loja ao vivo e não processa pedidos de clientes, ele é idêntico à produção.

- **Sistema de produção**—Sua loja ao vivo. Você deve fazer o mínimo de alterações diretas na configuração aqui e certamente nada que não tenha sido testado em uma instância de preparo. Se possível, faça alterações na configuração com [Patches de dados](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) que foram testados em uma instância de Armazenamento temporário/Desenvolvimento.

## Outros métodos de implantação

Como opção, você pode usar outros métodos de implantação, incluindo:

- Cópia segura com SCP ou rsync
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- A variável [Ferramenta de implantação](https://deployer.org/)

## Gerenciar a configuração

Modelagem após [fator 3 no design do aplicativo de 12 fatores](https://12factor.net/config), o Commerce agora armazena a configuração de cada sistema no próprio sistema. (As configurações de desenvolvimento são armazenadas no sistema de desenvolvimento, as configurações de produção são armazenadas no sistema de produção.)

Fornecemos uma maneira de sincronizar a configuração de seus sistemas:

- **Configuração compartilhada**—Configurações que não são específicas do sistema nem confidenciais.

  As configurações compartilhadas são configurações que você deseja manter consistentes nos sistemas de desenvolvimento e produção. Defina a configuração compartilhada no Administrador em sua infraestrutura de desenvolvimento (ou Adobe Commerce on cloud) _integração_).

  O arquivo de configuração compartilhado, `app/etc/config.php`, deve ser incluído no controle do código-fonte para que possa ser compartilhado entre os sistemas de desenvolvimento, compilação e produção.

- **Configuração específica do sistema**—Configurações que variam de acordo com o sistema, como nomes de host e portas de mecanismos de pesquisa.

- **Configuração sensível**—Configurações que devem _não_ estar no controle do código-fonte porque eles expõem informações de identificação pessoal (PII) ou configurações como chaves de API ou senhas.

  O arquivo de configuração específico do sistema, `app/etc/env.php`, deve _não_ ser incluídos no controle de origem ou compartilhados entre sistemas. Use o botão [`magento config:set` e `magento:sensitive:set` comandos](../cli/set-configuration-values.md) para fornecer valores para essas configurações no sistema de produção.

>[!INFO]
>
>Esses novos métodos para gerenciar sua configuração são opcionais. Não é necessário, mas é altamente recomendável usá-los.

Na maioria das vezes, as opções de configuração definidas na configuração compartilhada, específica do sistema ou confidencial não podem ser editadas no Administrador. Isso ajuda a manter as configurações consistentes em todos os sistemas. (Opcionalmente, você pode usar a variável [`magento config:set` comando](../cli/set-configuration-values.md) sem o `--lock` opção para definir as configurações editáveis no Admin.)

Cada opção de configuração do Commerce tem uma _caminho de configuração_. Para definir um valor para uma opção de configuração, você pode usar um comando da CLI ou uma variável de ambiente para definir o valor desse caminho de configuração em um sistema específico.
