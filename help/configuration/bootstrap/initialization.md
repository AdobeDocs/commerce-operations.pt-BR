---
title: Inicialização e inicialização do aplicativo
description: Leia sobre a inicialização e a lógica de inicialização do aplicativo Commerce.
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Visão geral da inicialização e bootstrap

Para executar o aplicativo Commerce, as seguintes ações são implementadas em [pub/index.php][index]:

- Incluir [app/bootstrap.php][bootinitial], que executa rotinas de inicialização essenciais, como manipulação de erros, inicialização do carregador automático, definição de opções de perfil e definição do fuso horário padrão.
- Criar uma instância de [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Crie uma instância do aplicativo Commerce: [\Magento\Framework\AppInterface][app-face]
- Executar o Commerce

## Lógica de execução de Bootstrap

[O objeto de inicialização][bootinitial] O usa o seguinte algoritmo para executar o aplicativo Commerce:

1. Inicializa o manipulador de erros.
1. Cria o [gerenciador de objetos][object] e serviços básicos compartilhados que são usados em todos os lugares e afetados pelo ambiente. Os parâmetros de ambiente são inseridos corretamente nesses objetos.
1. Afirma que o modo de manutenção é _não_ ativado; caso contrário, termina.
1. Afirma que o aplicativo Commerce está instalado; caso contrário, encerra.
1. Inicia o aplicativo Commerce.

   Qualquer exceção não detectada durante a inicialização do aplicativo é automaticamente enviada de volta para o Commerce na `catchException()` que você pode usar para tratar a exceção. Este último deve retornar `true` ou `false`:

   - Se `true`: o comércio tratou a exceção com êxito. Não há necessidade de fazer mais nada.
   - Se `false`: (ou qualquer outro resultado vazio) o Commerce não lidou com a exceção. O objeto de inicialização executa a sub-rotina padrão de tratamento de exceções.

1. Envia a resposta fornecida pelo objeto de aplicativo.

   >[!INFO]
   >
   >As afirmações de que o aplicativo Commerce está instalado e não em modo de manutenção são o comportamento padrão do `\Magento\Framework\App\Bootstrap` classe. Você pode modificá-lo usando um script de ponto de entrada ao criar o objeto de inicialização.

   Exemplo de script de ponto de entrada que modifica o objeto de inicialização:

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## Tratamento de exceção padrão

O objeto de inicialização especifica como o aplicativo Commerce trata as exceções não capturadas da seguinte maneira:

- Entrada [modo de desenvolvedor](../bootstrap/application-modes.md#developer-mode), exibe a exceção como está.
- Em qualquer outro modo, o tenta registrar a exceção e exibir uma mensagem de erro genérica.
- Encerra o Commerce com o código de erro `1`

## Aplicativos de ponto de entrada

Temos os seguintes aplicativos de ponto de entrada (ou seja, aplicativos definidos pelo Commerce que são usados pelo servidor Web como um índice de diretório):

### Ponto de entrada HTTP

[\Magento\Framework\App\Http][http] funciona da seguinte forma:

1. Determina o [área de aplicação](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Inicia o controlador frontal e os sistemas de roteamento para localizar e executar uma ação do controlador.
1. Usa um objeto de resposta HTTP para retornar o resultado obtido da ação do controlador.
1. Tratamento de erros (na seguinte ordem de prioridade):

   1. Se você estiver usando [modo de desenvolvedor](../bootstrap/application-modes.md#developer-mode):
      - Se o aplicativo Commerce não estiver instalado, redirecione para o Assistente de configuração.
      - Se o aplicativo Commerce estiver instalado, exiba um erro e o código de status HTTP 500 (Erro interno do servidor).
   1. Se o aplicativo Commerce estiver em modo de manutenção, exiba uma página de aterrissagem amigável &quot;Serviço indisponível&quot; com o código de status HTTP 503 (Serviço indisponível).
   1. Se o aplicativo Commerce estiver _não_ instalado, redirecionar para Assistente de configuração.
   1. Se a sessão for inválida, redirecione para a página inicial.
   1. Se houver qualquer outro erro de inicialização do aplicativo, exiba uma página amigável &quot;Página não encontrada&quot; com o código de status HTTP 404 (Não encontrada).
   1. Em qualquer outro erro, exiba uma página amigável &quot;Serviço indisponível&quot; com resposta HTTP 503 e gere um relatório de erros e exiba sua ID na página.

### Ponto de entrada de recurso estático

[\Magento\Framework\App\StaticResource][static-resource] O é um aplicativo para recuperar recursos estáticos (por exemplo, CSS, JavaScript e imagens). Ele adia qualquer ação com um recurso estático até que o recurso seja solicitado.

>[!INFO]
>
>O ponto de entrada para arquivos de exibição estáticos não é usado em [modo de produção](application-modes.md#production-mode) para evitar possíveis explorações no servidor. No modo de produção, o aplicativo Commerce espera que todos os recursos necessários existam no `<your Commerce install dir>/pub/static` diretório.

No modo padrão ou de desenvolvedor, uma solicitação para um recurso estático não existente é redirecionada para o ponto de entrada estático de acordo com as regras de regravação especificadas pelo apropriado `.htaccess`.
Quando a solicitação é redirecionada para o ponto de entrada, o aplicativo Commerce analisa o URL solicitado com base nos parâmetros recuperados e encontra o recurso solicitado.

- Entrada [desenvolvedor](application-modes.md#developer-mode) , o conteúdo do arquivo é retornado para que, sempre que o recurso for solicitado, o conteúdo retornado esteja atualizado.
- Entrada [padrão](application-modes.md#default-mode) , o recurso recuperado é publicado para ser acessível pela URL solicitada anteriormente.

   Todas as solicitações futuras do recurso estático são processadas pelo servidor da mesma forma que os arquivos estáticos; ou seja, sem envolver o ponto de entrada. Se for necessário sincronizar os arquivos publicados com os originais, a variável `pub/static` O diretório deve ser removido; como resultado, os arquivos são automaticamente republicados com a próxima solicitação.

### Ponto de entrada do recurso de mídia

[Magento\MediaStorage\App\Media][media] recupera recursos de mídia (ou seja, quaisquer arquivos carregados no armazenamento de mídia) do banco de dados. Ele é usado sempre que o banco de dados é configurado como um armazenamento de mídia.

`\Magento\Core\App\Media` O tenta encontrar o arquivo de mídia no armazenamento de banco de dados configurado e gravá-lo na `pub/static` e, em seguida, retornar seu conteúdo. Em caso de erro, ele retorna um código de status HTTP 404 (Não encontrado) no cabeçalho sem conteúdo.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
