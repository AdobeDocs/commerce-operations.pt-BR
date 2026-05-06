---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.78'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.78.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0c45d7ba61be21d0983b242cfdbe0b9591dd5c5c
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.78

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.78.

O QPT v1.1.78 inclui os seguintes patches:
1. **ACP2E-4416**: corrige o problema em que os pontos de premiação do cliente não são inicializados quando criados no Administrador.
1. **ACP2E-4419**: corrige o problema em que os cartões-presente não são aplicados corretamente no check-out após a validação bem-sucedida do reCAPTCHA v2 (&#39;Não sou um robô&#39;) na loja.
1. **ACP2E-4431**: corrige o problema em que os Produtos Relacionados correspondentes às regras de destino são excluídos durante o processo de reindexação.
1. **ACP2E-4448**: corrige o problema em que as alterações de configuração feitas durante as interrupções do Redis não são refletidas após a recuperação do Redis, fazendo com que valores obsoletos persistam.
1. **[ACP2E-4456](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4456.md)**: corrige um problema em que cancelar um pedido usando uma mutação do GraphQL não faz a transição de um pedido pago inteiramente com cartões-presente para o status Fechado.
1. **[ACP2E-4452](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4452.md)**: corrige o problema em que os preços dos produtos na página [!UICONTROL Quick Order] incluem impostos, independentemente da configuração de exibição de imposto.
1. **ACP2E-4507**: corrige o problema em que a configuração de Opções de Senha não é aplicada para solicitações de redefinição de senha do cliente feitas por meio de mutações do GraphQL.
1. **ACP2E-4513**: corrige o problema em que imagens CAPTCHA expiradas não são excluídas do sistema.
1. **ACP2E-4522**: corrige o problema em que um erro de chave duplicada intermitente ocorre na tabela quote_coupons quando várias solicitações de mesclagem de carrinho ou salvamento de cotação são executadas ao mesmo tempo.
1. **[ACP2E-4448](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4448.md)**: corrige o problema em que as alterações de configuração feitas durante as interrupções do Redis não são refletidas após a recuperação do Redis, fazendo com que valores obsoletos persistam.
1. **[ACP2E-4416](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4416.md)**: corrige o problema em que os pontos de premiação do cliente não são inicializados quando criados no Administrador.
1. **[ACP2E-4431](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4431.md)**: corrige o problema em que [!UICONTROL Related Products] correspondidos pelas regras de destino são excluídos durante o processo de reindexação.
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)**: corrige o problema em que os cartões-presente não são aplicados corretamente no check-out após a validação bem-sucedida do reCAPTCHA v2 (&#39;Não sou um robô&#39;) na loja.
1. **ACP2E-4448**: corrige o problema em que as alterações de configuração feitas durante as interrupções do Redis não são refletidas após a recuperação do Redis, fazendo com que valores obsoletos persistam.
1. **ACP2E-4452**: corrige o problema em que os preços dos produtos na página Pedido Rápido incluem impostos, independentemente da configuração de exibição de imposto.
1. **ACP2E-4456**: corrige um problema em que cancelar um pedido usando uma mutação do GraphQL não faz a transição de um pedido pago inteiramente com cartões-presente para o status Fechado.
1. **[ACP2E-4507](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4507.md)**: corrige o problema em que a configuração [!UICONTROL Password Options] não é aplicada às solicitações de redefinição de senha do cliente feitas por meio de mutações do GraphQL.
1. **ACP2E-4513**: corrige o problema em que imagens CAPTCHA expiradas não são excluídas do sistema.
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)**: corrige o problema em que um erro de chave duplicada intermitente ocorre na tabela quote_coupons quando várias solicitações de mesclagem de carrinho ou salvamento de cotação são executadas ao mesmo tempo.
1. **ACP2E-4528**: corrige o problema na validação da cidade em endereços de clientes, o que agora permite um caractere de barra (/) e rejeita caracteres inválidos, como !, &quot;, # e ?.
1. **[ACP2E-4535](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4535.md)**: corrige um problema em que o envio do formulário de esqueci a senha faz com que a sessão seja destruída ou gerada novamente (alterações de PHPSESSID) e o carrinho de convidado é limpo.
1. **ACP2E-4540**: corrige o problema em que a biblioteca Fotorama não estava carregando corretamente, fazendo com que apenas a primeira imagem anexada ficasse visível.
1. **ACP2E-4555**: corrige o problema em que números de telefone modernos contendo &quot;.&quot; ou &quot;/&quot; não são validados corretamente.
1. **ACP2E-4565**: corrige o problema em que a consulta do GraphQL da Empresa retorna &quot;O cliente atual não está autorizado&quot; quando o cabeçalho X-Adobe-Company é usado.
1. **ACP2E-4591**: corrige o problema em que os segmentos de clientes baseados na contagem de pedidos, como &quot;Compradores pela primeira vez&quot;, não eram atualizados quando os pedidos eram feitos por meio da API REST.
1. **[ACP2E-4540](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4540.md)**: corrige o problema em que a biblioteca Fotorama não estava carregando corretamente, fazendo com que apenas a primeira imagem anexada ficasse visível.
1. **[ACP2E-4555](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4555.md)**: corrige o problema em que números de telefone modernos contendo &quot;.&quot; ou &quot;/&quot; não são validados corretamente.
1. **[ACP2E-4565](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4565.md)**: corrige o problema em que a consulta do GraphQL da Empresa retorna &quot;O cliente atual não está autorizado&quot; quando o cabeçalho X-Adobe-Company é usado.
1. **ACP2E-4591**: corrige o problema em que os segmentos de clientes baseados na contagem de pedidos, como &quot;Compradores pela primeira vez&quot;, não eram atualizados quando os pedidos eram feitos por meio da API REST.
1. **[ACP2E-4609](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4609.md)**: corrige o problema em que a página Minhas Cotações não mostra cotações quando algumas cotações contêm produtos excluídos.
1. **ACP2E-4591**: corrige o problema em que os segmentos de clientes baseados na contagem de pedidos, como &quot;Compradores pela primeira vez&quot;, não eram atualizados quando os pedidos eram feitos por meio da API REST.
1. **ACP2E-4609**: corrige o problema em que a página Minhas Cotações não mostra cotações quando algumas cotações contêm produtos excluídos.
1. **[ACP2E-4613](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4613.md)**: corrige o problema em que grandes estruturas de diretório de mídia causavam respostas gettree lentas, resultando em tempos de carregamento estendidos para a árvore de diretório **[!UICONTROL Media Gallery]**.
1. **ACP2E-4628**: corrige o problema em que importar clientes com endereços de email em maiúsculas resulta no erro de chave de matriz indefinida, quando o Compartilhamento de Conta está definido como Global.
1. **[ACP2E-4665](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4665.md)**: corrige o problema em que produtos derivados de produtos configuráveis contendo vídeos nas galerias de produtos não são listados quando solicitados por meio da API REST.
1. **ACP2E-4665**: corrige o problema em que produtos derivados de produtos configuráveis contendo vídeos nas galerias de produtos não são listados quando solicitados por meio da API REST.
1. **ACP2E-4732**: corrige um problema em que a indexação parcial era interrompida para clientes com um grande número de atualizações quando a coluna version_id na tabela changelog atingia seu valor máximo.
1. **ACP2E-4763**: corrige o problema em que a consulta customerOrders do GraphQL retorna valores inflados de original_price_inclusion_tax e original_row_total_inclusion_tax quando os Preços do catálogo estão definidos como Imposto incluso, devido ao imposto ser aplicado duas vezes.
1. **ACSD-60989**: corrige o problema em que a modificação de uma coluna com uma chave estrangeira por meio de um esquema declarativo causa erros no MariaDB.

Use o menu à esquerda para navegar até uma página de patch específica.
