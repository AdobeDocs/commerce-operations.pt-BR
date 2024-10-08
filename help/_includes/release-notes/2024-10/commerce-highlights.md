---
source-git-commit: b30fe4ed4d910ac3a99d3bcf4ff94103bcbd1369
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---
# Destaques da versão 2.4.7 beta do Adobe Commerce de outubro de 2024

## Destaques

Essa versão do Adobe Commerce inclui várias correções críticas de segurança e melhorias na plataforma.

### Segurança

Os seguintes aprimoramentos de segurança nesta versão melhoram a conformidade com as práticas recomendadas de segurança mais recentes:

>[!NOTE]
>
>Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança de Adobe APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>Configurações</strong></td>
            <td>Esta versão inclui os seguintes aprimoramentos das configurações de segurança:
              <ul>
                <li><strong>Rotação de chave de criptografia</strong>: um novo comando CLI agora está disponível para alterar sua chave de criptografia. Consulte o artigo da Base de Dados de Conhecimento <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102">Solução de Problemas de Rotação de Chaves de Criptografia: CVE-2024-34102</a> para obter detalhes.<!-- AC-12589 --></li>
                <li><strong>Configurações de senha única</strong>: esta atualização é necessária para resolver um erro introduzido por uma <a href="https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value">alteração incompatível com versões anteriores</a> na versão 2.4.7. A descrição do campo <strong>[!UICONTROL OTP Window]</strong> agora fornece uma explicação precisa da configuração e o valor padrão foi alterado de <code>1</code> para <code>29</code>.<!-- AC-11762 --></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Platform

As seguintes atualizações de plataforma para esta versão garantem que o Adobe Commerce permaneça uma plataforma robusta e confiável, pronta para atender às demandas dos ambientes de comércio modernos:

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>Banco de dados</strong></td>
            <td>Em alinhamento com a <a href="/help/release/lifecycle-policy.md">política de ciclo de vida de suporte</a>, o Adobe Commerce agora é compatível com as seguintes versões de suporte de longo prazo (LTS) das seguintes tecnologias de banco de dados:
              <ul>
                <li><strong>MariaDB 11.4 LTS</strong> <em>_(com suporte até 2029)_</em>: a versão anterior (MariaDB 10.6) chegará ao fim da vida útil em 2026, tornando essa atualização essencial para manter a integridade e o desempenho do sistema. MariaDB 10.6 ainda é suportado, mas o Adobe recomenda atualizar para MariaDB 11.4 quando atualizar para o Adobe Commerce 2.4.8.</li>
                <li><strong>MySQL 8.4 LTS</strong> <em>_(com suporte até 2032)_</em>: a versão anterior (MySQL 8.0) chegará ao fim da vida útil em 2026, tornando essa atualização essencial para manter a integridade e o desempenho do sistema. O MySQL 8.0 ainda é suportado, mas o Adobe recomenda atualizar para o MySQL 8.4 ao atualizar para o Adobe Commerce 2.4.8</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>PHP</strong></td>
            <td>Esta versão inclui as seguintes melhorias do PHP:
            <ul>
              <li><strong>PHP 8.1</strong>: esta versão remove a compatibilidade do PHP 8.1 com Adobe Commerce 2.4.8. Você deve atualizar para o PHP 8.3 antes de atualizar para o Adobe Commerce 2.4.8.</li>
              <li><strong>PHP 8.2</strong>: uma das mudanças significativas no PHP 8.2 envolve a descontinuação da passagem de nulo para parâmetros de função interna não-nulos. Esta versão aborda recursos obsoletos do PHP 8.1 nos componentes principais da plataforma e garante a compatibilidade com o PHP 8.2.</li>
              <li><strong>PHPUnit 10</strong>: esta versão aborda vários problemas críticos, aprimora a compatibilidade e garante que a estrutura de teste do Adobe Commerce se alinhe aos mais recentes padrões do setor. A Adobe recomenda que todos os fornecedores de Commerce Marketplace e clientes com personalizações verifiquem se seus testes de unidade e integração são executados no PHPUnit 10 em vez de no 9.</li>
            </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Componentes</strong></td>
            <td>Os seguintes <a href="/help/release/packages/adobe-commerce.md">componentes e dependências</a> de terceiros foram atualizados para as versões estáveis mais recentes para aprimorar a estabilidade e o desempenho da plataforma:
              <ul>
                <li>jquery/validate 1.20.x</li>
                <li>Moment.js 2.30.1</li>
                <li>monolog/monolog 3.x</li>
                <li>monolog/Require.js 2.3.7</li>
                <li>TinyMCE 7.x</li>
                <li>wikimedia/less.php 5.x</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Pesquisar</strong></td>
            <td>O Adobe Commerce agora é otimizado para OpenSearch 2.x e não é mais compatível com o Elasticsearch. Todos os módulos e classes de Elasticsearch 7 e 8 foram descontinuados na base de código. A Adobe recomenda a transição para o OpenSearch para implantações de infraestrutura local e em nuvem para garantir suporte e compatibilidade contínuos. Consulte <a href="/help/upgrade/prepare/opensearch-migration.md">Migrando para OpenSearch</a>.
              <ul>
                <li>As opções Elasticsearch 7 e Elasticsearch 8 agora são rotuladas como "(Obsoleto)" na configuração de Admin.</li>
                <li>Quando um usuário seleciona Elasticsearch como mecanismo de pesquisa na Configuração de administração, o Commerce exibe uma notificação informando: <em>"Esse mecanismo de pesquisa não é mais compatível com o Adobe. Recomendamos usar o OpenSearch como um mecanismo de pesquisa."</em></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Desempenho

Esta versão inclui os seguintes aprimoramentos de desempenho:

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>Indexadores</strong></td>
            <td>O <a href="/help/implementation-playbook/best-practices/maintenance/indexer-configuration.md#set-indexers-to-update-on-schedule">modo indexador</a> padrão para todos os indexadores agora é [!UICONTROL **Update by Schedule**] ao instalar uma nova versão do Adobe Commerce ou ao atualizar de uma versão anterior. O novo padrão garante que os indexadores estejam na configuração recomendada, melhorando o desempenho do sistema e reduzindo possíveis problemas.</td>
        </tr>
    </tbody>
</table>

### Qualidade

Esta versão inclui os seguintes aprimoramentos de qualidade:

<table style="table-layout-auto">
    <tbody>
        <tr>
           <td><strong>Inventário</strong></td>
           <td>O sistema agora opera sem a dependência anteriormente oculta do Catálogo introduzida pelo InventoryIndexer, garantindo que a criação do produto, a troca do modo de exibição, a alteração do status do estoque e outras funcionalidades relacionadas funcionem conforme esperado. Anteriormente, essa dependência oculta causava inconsistências à medida que entidades diferentes eram sincronizadas e o indexador usava entidades diferentes.</td>
        </tr>
        <tr>
            <td><strong>Pedidos</strong></td>
            <td>Para minimizar a confusão, o rótulo do botão [!UICONTROL **Submit Comment**] foi alterado para [!UICONTROL **Update**] na página <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#notes-for-this-order">detalhes do pedido</a>.</td>
        </tr>
    </tbody>
</table>

### GraphQL

Esta versão inclui os seguintes aprimoramentos do GraphQL:

<table style="table-layout-auto">
    <tbody>
        <tr>
           <td><strong>Melhorias gerais</strong></td>
           <td>Esta versão inclui os seguintes aprimoramentos gerais da API do GraphQL:
             <ul>
               <li><!--LYNX-401--><strong>StoreConfig</strong>: campos <code>grouped_product_image</code> e <code>configurable_product_image</code> adicionados ao tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-StoreConfig"><code>StoreConfig</code></a>.</li>
              <li><!--LYNX-387--><strong>CartItemPrices</strong>: os seguintes campos foram adicionados ao tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> para oferecer suporte a cálculos precisos de desconto e exibição de preços:
                <ul>
                  <li><code>original_item_price</code></li>
                  <li><code>original_row_total</code></li>
                  <li><code>row_total_including_catalog_discounts_only</code></li>
                </ul>
              </li>
              <li><!--LYNX-451--><strong>CartPrices</strong>: o campo <code>grand_total_excluding_tax</code> foi adicionado ao tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartPrices"><code>CartPrices</code></a>, fornecendo preços claros e inclusivos em impostos.</li>
              <li><!--LYNX-542--><strong>mutação updateCartItems</strong>: a mutação <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-updateCartItems"><code>updateCartItems</code></a> foi atualizada para retornar respostas bem-sucedidas com detalhes de erros em vez de exceções. Mapeamento de erros aprimorado para melhorar a clareza das notificações do usuário.</li>
              <li><!--LYNX-522--><strong>recaptchaV3Config query</strong>: Introduziu um campo <code>theme</code> para a consulta <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-recaptchaV3Config"><code>recaptchaV3Config</code></a>. Esse campo permite especificar o nome do tema a ser usado para renderizar o reCaptcha.</li>
              <li><!--LYNX-540--><strong>ProductInterface</strong>: introduziu um campo <code>quantity</code> em <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-ProductInterface"><code>ProductInterface</code></a> para fornecer detalhes de nível de estoque. Ele exibe o estoque disponível ou nulo com base nas configurações de Administração.</li>
               <li><!--LYNX-460--><strong>Produtos agrupados</strong>: exibição de preços corrigida para produtos agrupados, garantindo informações precisas de preço e moeda.</li>
               <li><!--LYNX-547--><strong>Quantidade</strong>: mensagens refinadas para notificações de quantidade insuficiente e indisponível.</li>
               <li><!--LYNX-541--><strong>Tipo IninsufficientStockError</strong>: novo tipo <code>InsufficientStockError</code> adicionado para lidar com casos em que os níveis de estoque são insuficientes. Ajustado o esquema para oferecer suporte a novos tipos de erro, aprimorando os recursos do relatório de erros.</li>
               <li><!--LYNX-476--><strong>Valor do estoque</strong>: mensagem de erro aprimorada para incluir valores de estoque disponíveis. Fornece aos usuários informações mais claras sobre os níveis de estoque durante atualizações de pedidos.</li>
               <li><!--LYNX-377--><strong>Quantidade solicitada</strong>: <code>not_available_message</code> adicionado ao <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemInterface"><code>CartItemInterface</code></a>.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Gerenciamento de clientes</strong></td>
           <td>Esta versão inclui os seguintes aprimoramentos de gerenciamento de clientes:
             <ul>
               <li><!--LYNX-391--><strong>MutationCustomerToken</strong>: tratamento de erros refinado na mutação <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-generateCustomerToken"><code>generateCustomerToken</code></a> para fornecer mensagens específicas para emails não confirmados. Oferece melhor orientação do usuário e resolução de erros.</li>
               <li><!--LYNX-390--><strong>resendConfirmationEmail mutation</strong>: uma nova mutação <code>resendConfirmationEmail</code> foi adicionada para reenviar confirmações por email.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Gerenciamento de pedidos</strong></td>
           <td>Esta versão inclui os seguintes aprimoramentos no gerenciamento de pedidos de usuários:
             <ul>
              <li><!--LYNX-470--><strong>Data da primeira ordem</strong>: um novo campo <code>date_of_first_order</code> foi adicionado ao tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrders"><code>CustomerOrders</code></a>.</li>
              <li><!--LYNX-468--><strong>OrderAddress</strong>: estendeu o tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderAddress"><code>OrderAddress</code></a> para incluir atributos personalizados, melhorando a visibilidade dos detalhes da ordem. Suporta a exibição de informações adicionais nas páginas de confirmação do pedido.</li>
              <li><!--LYNX-458--><strong>consultas guestOrder e guestOrderByToken</strong>: as consultas <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrder"><code>guestOrder</code></a> e <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrderByToken"><code>guestOrderByToken</code></a> foram atualizadas para incluir atributos de endereço personalizados, garantindo informações completas de endereço para novas contas.</li>
              <li><!--LYNX-450--><strong>Tipo de CustomerOrder</strong>: o campo <code>is_virtual</code> foi adicionado ao tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>, oferecendo suporte à identificação de produto virtual. Melhora o processamento de pedidos, distinguindo produtos virtuais e físicos.</li>
              <li><!--LYNX-449--><strong>orderItemPrices</strong>: tipo <code>OrderItemPrices</code> adicionado semelhante a <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> para <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderItemInterface"><code>OrderItemInterface</code></a> com vários campos novos para preço.</li>
              <li><!--LYNX-448--><strong>Mesclar pedidos de convidados</strong>: funcionalidade de API aprimorada para mesclar pedidos de convidados com contas de clientes com base na correspondência de email. Simplifica o gerenciamento de pedidos para clientes recorrentes.</li>
              <li><!-- LYNX-523: --><strong>campo available_actions</strong>: estendeu o tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> para incluir um campo <code>available_actions</code> para melhorar o gerenciamento de pedidos. O campo "available_actions" mapeia para uma enumeração que lista as possíveis ações que podem ser executadas na ordem.</li>
              <li><!-- LYNX-524 --><strong>Tipo de CustomerOrder</strong>: o campo <code>customer_info</code> foi adicionado ao tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>. Este campo requer e <code>OrderCustomerInfo</code>, que define os detalhes sobre o nome do cliente.</li>
              <li><!--LYNX-519--><strong>Códigos de erro para cancelamento de pedido</strong>: foram adicionados códigos de erro detalhados ao tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CancelOrderOutput"><code>CancelOrderOutput</code></a>. Tratamento de erros e feedback do usuário aprimorados para os processos de cancelamento de pedido.</li>
              <li><!--LYNX-515--><strong>Usuários convidados habilitados a criar devoluções para pedidos</strong>: a mutação <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-requestReturn"><code>requestReturn</code></a> foi ajustada para oferecer suporte a devoluções de pedidos de convidados.</li>
              <li><!--LYNX-505--><strong>mutação confirmCancelOrder</strong>: uma nova mutação <code>confirmCancelOrder</code> adicionada para facilitar o cancelamento de pedidos para os usuários convidados.</li>
             </ul>
           </td>
        </tr>
    </tbody>
</table>
