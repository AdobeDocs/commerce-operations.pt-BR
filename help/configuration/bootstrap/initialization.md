---
title: Inicialização e inicialização do aplicativo
description: Leia sobre a inicialização e a lógica de inicialização do aplicativo Commerce.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---


# Visão geral da inicialização e do bootstrap

Para executar o aplicativo Commerce, as seguintes ações são implementadas em [pub/index.php][index]:

- Incluir [app/bootstrap.php][bootinitial], que executa rotinas de inicialização essenciais, como manipulação de erros, inicialização do carregador automático, definição de opções de criação de perfis e definição do fuso horário padrão.
- Crie uma instância de [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Crie uma instância do aplicativo Commerce: [\Magento\Framework\AppInterface][app-face]
- Executar Comércio

## Lógica de execução do Bootstrap

[O objeto de bootstrap][bootinitial] O usa o seguinte algoritmo para executar o aplicativo Commerce:

1. Inicializa o manipulador de erros.
1. Cria o [gerenciador de objetos][object] e serviços básicos compartilhados que são usados em todos os lugares e afetados pelo ambiente. Os parâmetros de ambiente são inseridos corretamente nesses objetos.
1. Afirma que o modo de manutenção é _not_ habilitado; caso contrário, será encerrado.
1. Afirma que o aplicativo Commerce está instalado; caso contrário, será encerrado.
1. Inicia o aplicativo Commerce.

   Qualquer exceção não capturada durante a inicialização do aplicativo é automaticamente retornada ao Commerce na `catchException()` método que pode ser usado para lidar com a exceção. Este último deve regressar `true` ou `false`:

   - If `true`: O comércio lidou com a exceção com êxito. Não precisa fazer mais nada.
   - If `false`: (ou qualquer outro resultado vazio) O Commerce não lidava com a exceção. O objeto bootstrap executa a sub-rotina padrão de tratamento de exceções.

1. Envia a resposta fornecida pelo objeto do aplicativo.

   >[!INFO]
   >
   >As afirmações de que o aplicativo Commerce está instalado e não no modo de manutenção são o comportamento padrão do `\Magento\Framework\App\Bootstrap` classe . Você pode modificá-lo usando um script de ponto de entrada ao criar o objeto bootstrap.

   Exemplo de script de ponto de entrada que modifica o objeto bootstrap:

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

## Tratamento de exceções padrão

O objeto bootstrap especifica como o aplicativo Commerce lida com exceções não capturadas da seguinte maneira:

- Em [modo desenvolvedor](../bootstrap/application-modes.md#developer-mode), exibe a exceção como está.
- Em qualquer outro modo, o tenta registrar a exceção e exibe uma mensagem de erro genérica.
- Encerra o Commerce com código de erro `1`

## Aplicativos de pontos de entrada

Temos os seguintes aplicativos de ponto de entrada (ou seja, aplicativos definidos pelo Commerce que são usados pelo servidor Web como um índice de diretório):

### Ponto de entrada HTTP

[\Magento\Framework\App\Http][http] opera da seguinte forma:

1. Determina o [área de aplicação](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Inicia o controlador frontal e os sistemas de roteamento para localizar e executar uma ação de controlador.
1. Usa um objeto de resposta HTTP para retornar o resultado obtido da ação do controlador.
1. Tratamento de erros (na seguinte ordem de prioridade):

   1. Se estiver usando [modo desenvolvedor](../bootstrap/application-modes.md#developer-mode):
      - Se o aplicativo Commerce não estiver instalado, redirecione para o Assistente de configuração.
      - Se o aplicativo Commerce estiver instalado, exiba um erro e o código de status HTTP 500 (Internal Server Error).
   1. Se o aplicativo Commerce estiver em modo de manutenção, exiba uma landing page &quot;Service Unavailable&quot; amigável ao usuário com código de status HTTP 503 (Service Unavailable).
   1. Se o aplicativo Commerce for _not_ instalado, redirecione para o Assistente de configuração.
   1. Se a sessão for inválida, redirecione para a página inicial.
   1. Se houver algum outro erro de inicialização de aplicativo, exiba uma página &quot;Página não encontrada&quot; amigável para o usuário com o código de status HTTP 404 (Não encontrada).
   1. Em qualquer outro erro, exiba uma página &quot;Serviço indisponível&quot; amigável com resposta HTTP 503 e gere um relatório de erro e exiba sua ID na página.

### Ponto de entrada de recurso estático

[\Magento\Framework\App\StaticResource][static-resource] é um aplicativo para recuperação de recursos estáticos (por exemplo, CSS, JavaScript e imagens). Ele adia todas as ações com um recurso estático até que o recurso seja solicitado.

>[!INFO]
>
>O ponto de entrada para arquivos de visualização estáticos não é usado em [modo de produção](application-modes.md#production-mode) para evitar possíveis explorações no servidor. No modo de produção, o aplicativo Commerce espera que todos os recursos necessários existam no `<your Commerce install dir>/pub/static` diretório.

No modo padrão ou de desenvolvedor, uma solicitação de um recurso estático inexistente é redirecionada para o ponto de entrada estático de acordo com as regras de regravação especificadas pelo `.htaccess`.
Quando a solicitação é redirecionada para o ponto de entrada, o aplicativo Commerce analisa a URL solicitada com base nos parâmetros recuperados e encontra o recurso solicitado.

- Em [desenvolvedor](application-modes.md#developer-mode) , o conteúdo do arquivo é retornado para que toda vez que o recurso for solicitado, o conteúdo retornado esteja atualizado.
- Em [default](application-modes.md#default-mode) , o recurso recuperado é publicado para que possa ser acessado pelo URL solicitado anteriormente.

   Todas as futuras solicitações para o recurso estático são processadas pelo servidor da mesma forma que os arquivos estáticos; ou seja, sem envolver o ponto de entrada. Se for necessário sincronizar os arquivos publicados com os originais, a variável `pub/static` diretório deve ser removido; como resultado, os arquivos são republicados automaticamente com a próxima solicitação.

### Ponto de entrada do recurso de mídia

[Magento\MediaStorage\App\Media][media] recupera recursos de mídia (ou seja, quaisquer arquivos carregados no armazenamento de mídia) do banco de dados. Ele é usado sempre que o banco de dados é configurado como um armazenamento de mídia.

`\Magento\Core\App\Media` O tenta localizar o arquivo de mídia no armazenamento do banco de dados configurado e gravá-lo no `pub/static` , em seguida, retorna seu conteúdo. Em caso de erro, retorna um código de status HTTP 404 (Not Found) no cabeçalho sem conteúdo.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
