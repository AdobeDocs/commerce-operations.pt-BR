---
title: Guia de Solução de Problemas do [!DNL Adobe Commerce Patching Automation]
description: Solucionar problemas comuns e mensagens de erro no [!DNL Adobe Commerce Patching Automation]
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 0%

---

# Guia de solução de problemas do [!DNL Adobe Commerce Patching Automation]

Ao usar o [!DNL Patching Automation] para operações de patch, você pode encontrar mensagens de erro e problemas que podem impedir o êxito do aplicativo de patch ou da reversão. Este guia fornece soluções para os problemas mais comuns.

## Etapas rápidas de solução de problemas

### Se a operação de patch falhar

* Verifique o status da operação para entender em qual estágio houve falha
* Revisar mensagens de erro para motivos específicos de falha
* Examinar logs de erros para obter detalhes técnicos
* Siga as soluções fornecidas neste guia

>[!TIP]
>
>No Cloud Console, os logs de implantação estão disponíveis no Feed de atividades do projeto, mesmo após a exclusão de um ambiente de integração temporário.

### Duração das operações de patch

Para a maioria dos ambientes, a linha do tempo a seguir descreve quanto tempo as operações de patch devem levar, mas pode levar mais tempo, dependendo do tamanho e da complexidade do ambiente:

* **Pré-processando:** 2-5 minutos
* **Patches:** 5-15 minutos
* **Pós-processamento:** 10-40 minutos
* **Total:** 15-60 minutos

>[!NOTE]
>
>O tempo de pós-processamento é estimado a partir do histórico de implantação do próprio ambiente, portanto, pode estar fora do intervalo acima para ambientes de implantação excepcionalmente rápida ou lenta.

### Cancelamento de uma correção em andamento

>[!WARNING]
>
>Depois que uma operação de patch começar, ela poderá ser concluída. O sistema inclui procedimentos de limpeza que são executados mesmo se as operações falharem. Interromper o processo pode deixar o ambiente em um estado inconsistente.

## Mensagens de sucesso comuns

* **&quot;Trabalho concluído com êxito&quot;** - O patch foi aplicado/revertido com êxito sem problemas.

* **&quot;O patch foi aplicado&quot;** - Você está tentando aplicar um patch que já foi aplicado. O sistema detectou que o patch já está presente no ambiente. Nenhuma ação é necessária.

* **&quot;O patch foi revertido&quot;** - Você está tentando reverter um patch que já foi revertido. O sistema detectou que o patch não está aplicado no momento. Nenhuma ação é necessária.

## Mensagens e soluções de erro comuns

>[!NOTE]
>
>Nem todos os erros possíveis estão listados abaixo. Uma falha não listada durante a verificação preliminar é exibida como o &quot;Erro durante a verificação preliminar&quot; genérico; uma falha não listada durante a validação é exibida como o &quot;Erro durante o pós-processamento&quot; genérico — entre em contato com o suporte com o texto exato do erro de qualquer maneira. Durante a correção, uma falha imprevista mostra a mensagem de erro subjacente bruta diretamente em vez de qualquer fallback genérico.

### Erros de prontidão do ambiente

#### &quot;A última implantação não foi bem-sucedida. Verifique se o ambiente está estável antes de aplicar ou reverter patches.&quot;

**Quando ocorrer:** No início da verificação preliminar, antes de qualquer validação específica de patch

**Causa:** a implantação mais recente do ambiente de destino não foi concluída com êxito

**Solução:** reimplante seu ambiente de destino e confirme se a implantação foi concluída com êxito (verifique seu log de implantação no Cloud Console) antes de tentar novamente a operação de patch.

### Correção de erros de aplicação

#### &quot;O patch não pode ser aplicado porque o [!DNL Patching Automation] detectou esses problemas na sua base de código ou no arquivo de patch&quot;

**Quando ocorrer:** Durante a verificação preliminar

**Causa:** o patch está em conflito com sua base de código atual OU há um problema com o patch em si

**Soluções:**

* Revise os logs de erro detalhados fornecidos para identificar se é um problema de base de código ou de patch
* Verifique se há personalizações conflitantes em seu código
* Verifique se o patch é compatível com a sua versão do Adobe Commerce
* Considere resolver conflitos manualmente ou entre em contato com o suporte

#### &quot;Você está tentando reverter um patch que não foi aplicado através do [!DNL Patching Automation]. É provável que o patch tenha sido aplicado manualmente.&quot;

**Quando ocorrer:** Durante operações de reversão

**Causa:** Você está tentando reverter um patch que não foi aplicado através de [!DNL Patching Automation]

**Solução:** Use o mesmo método usado para aplicar o patch originalmente ou contate o suporte para obter assistência manual

### Erros de ambiente e validação

#### &quot;O ambiente não está sincronizado com o pai&quot;

**Quando ocorrer:** Durante a validação, na verificação de sincronização pré-mesclagem — antes que o ambiente de integração seja mesclado ao seu ambiente de destino

**Causa:** seu ambiente de integração difere do ambiente pai, geralmente porque o ambiente de destino foi alterado enquanto o patch estava sendo testado

**Soluções:**

* Repita a operação de patch depois que o ambiente de destino estiver estável
* Evite fazer alterações no ambiente de destino enquanto uma operação de patch estiver em andamento
* Entre em contato com o suporte se os problemas de sincronização persistirem

#### &quot;Falha na verificação pós-mesclagem: os ambientes não estão sincronizados após a mesclagem.&quot;

**Quando ocorrer:** Durante a validação, depois que o ambiente de integração já tiver sido mesclado ao seu ambiente de destino

**Causa:** o código no código dos dois ambientes não corresponde após a mesclagem, geralmente um atraso temporário de propagação da API Platform.sh em vez de um conflito real

**Soluções:**

* Aguarde alguns minutos e verifique o status do ambiente novamente. Esse problema geralmente é resolvido sozinho
* Se os ambientes ainda não corresponderem após alguns minutos, entre em contato com o Suporte da Adobe.

#### &quot;Não é possível criar o trabalho de patch no ambiente de produção quando o cron está habilitado e o modo de manutenção está desabilitado. Ative o modo de manutenção e desative as tarefas cron antes de aplicar os patches.&quot;

**Quando ocorrer:** Durante a verificação preliminar de ambientes de produção

**Causa:** o ambiente de produção não atende às condições de segurança necessárias

**Soluções:**

* Habilitar modo de manutenção para o armazenamento de produção
* Desabilitar trabalhos cron no ambiente de produção
* Verifique se ambas as condições foram atendidas antes de tentar novamente
* Como alternativa, marque a caixa de seleção Substituir na interface do usuário para ignorar essas verificações e continuar mesmo assim. Use a opção de substituição somente se você entender o risco de corrigir a produção sem as proteções em vigor

>[!IMPORTANT]
>
> [!DNL Patching Automation] não habilita automaticamente o modo de manutenção ou desabilita trabalhos cron - eles devem ser feitos externamente por você

#### &quot;A operação de patch foi concluída, mas a verificação de integridade do ambiente falhou. Isso indica possíveis problemas com a implantação. Revise o status do ambiente e considere reverter a alteração.&quot;

**Quando ocorrer:** Após o aplicativo de patch ou a reversão, durante a validação

**Causa:** o patch foi aplicado ou revertido com êxito, mas a verificação de integridade subsequente falhou

**Soluções:**

* Teste a loja, a finalização crítica e os fluxos de trabalho do administrador para confirmar se os clientes foram realmente afetados
* No Cloud Console, revise o status do ambiente e inspecione os logs de aplicativo e implantação no feed de projetos **Atividade**. Procure erros associados à operação ou implantação do patch.
* Acione uma reimplantação manual para determinar se a falha de verificação de integridade foi causada por um problema transitório de implantação ou infraestrutura.
* Se o problema persistir, reverta o patch. Se o patch for gerenciado por [!DNL Patching Automation] e a operação estiver disponível, selecione [!UICONTROL Revert]. Se o patch for um patch personalizado no diretório `m2-hotfixes`, exclua o arquivo de patch do repositório do projeto. Confirme, envie a alteração e reimplante o ambiente.
* Se o problema persistir, entre em contato com o Suporte da Adobe.Inclua as seguintes informações em sua solicitação de suporte: ID do projeto de suporte, ID do ambiente e esta mensagem exata: a última operação não foi concluída corretamente, portanto, o suporte pode precisar confirmar o estado do ambiente.

### Erros de autenticação e acesso

#### &quot;Acesso negado&quot;

**Quando ocorrer:** Quando sua conta não tiver as permissões necessárias durante a criação ou o acesso ao ambiente

**Causa:** sua conta de usuário não tem as permissões necessárias

**Soluções:**

* Verifique sua função de usuário e suas permissões
* Entre em contato com o administrador do sistema
* Verificar se você tem permissões de gerenciamento de ambiente
* Verifique se você tem permissões de implantação

### Erros de integração do GitHub

#### &quot;Não há credenciais Git disponíveis para o provedor &quot;github&quot;. Instale o aplicativo GitHub de Automação de Patches para este repositório&quot;

**Quando ocorrer:** Durante operações de patch para projetos conectados ao GitHub

**Causa:** o aplicativo GitHub [!DNL Patching Automation] não está instalado em seu repositório

**Solução:** Siga as etapas em [Configurar a integração do GitHub para [!DNL Patching Automation]](github-integration.md)

#### &quot;Falha na solicitação da API do GitHub&quot;

**Quando ocorrer:** Durante operações de patch para projetos conectados ao GitHub

**Causa:** um problema temporário impediu o serviço de se conectar ao GitHub

**Solução:** aguarde alguns minutos e repita a operação. Se o erro persistir, entre em contato com o [suporte da Adobe Commerce Cloud](https://experienceleague.adobe.com/home?lang=pt-BR#support)

#### &quot;Ambiente não criado dentro do tempo limite&quot; (projeto conectado ao GitHub)

**Quando ocorrer:** Durante a criação do ambiente de integração

**Causa:** a integração GitHub do projeto tem a opção `fetch-branches` desabilitada. Como resultado, as ramificações temporárias enviadas pelo serviço não são sincronizadas e o ambiente de integração nunca é criado.

**Solução:** Habilite a [`fetch-branches` opção](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration) da integração e repita a operação. Consulte [Configurar a integração do GitHub para [!DNL Patching Automation]](github-integration.md).

### Erros de ativação de ambiente

#### &quot;Não é possível ativar o ambiente de integração.&quot;

**Quando ocorrer:** Quando [!DNL Patching Automation] não puder ativar o ambiente de integração temporária necessário para testar o patch com segurança.

**Causa:** Depende dos detalhes adicionais exibidos junto com o erro:

**Se os detalhes mencionarem os pacotes do Composer ou do Adobe Commerce:**

* Faça logon em [https://account.magento.com/](https://account.magento.com/) (ou peça ao proprietário da conta que o faça) e confirme se a sua conta tem acesso à base de código do Commerce Enterprise.
* Verifique se o par de chaves públicas/privadas do Composer do seu projeto está correto. Consulte [Chaves de autenticação](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/authentication-keys).
* Faça logon em [https://account.magento.com/](https://account.magento.com/) (ou peça ao proprietário da conta para fazer isso) e confirme se a sua conta tem acesso à base de código do Commerce Enterprise.
* Verifique se as chaves de autenticação pública e privada do Composer do seu projeto estão corretas. Consulte [Chaves de autenticação](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/authentication-keys).
* Confirme se o pacote chamado na mensagem de erro está disponível para a sua versão do Commerce. Consulte [pacotes Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/release/packages/adobe-commerce).

**Se os detalhes mencionarem slots ou recursos do ambiente:**

* No Cloud Console, abra a visão geral do projeto e revise os ambientes e seus status. Desativar ou excluir quaisquer ambientes de integração não utilizados: selecione o ambiente. Vá para **[!UICONTROL Settings]>[!UICONTROL General]**. Defina o status do ambiente como inativo.

  Alternativamente, use a CLI: `magento-cloud environment:list` / `magento-cloud environment:deactivate <environment-name>`
* Verifique se o projeto tem recursos suficientes, por exemplo, espaço em disco.
* Verifique se o ambiente pai está estável (sem implantação ativa) no momento da operação.
* Entre em contato com o Suporte da Adobe se precisar aumentar o limite do ambiente.

**Para qualquer outra causa:** revise os logs de erro detalhados na Interface de Automação de Patches ou contate o suporte com o texto de erro exato.

## Obtendo ajuda

**Quando contatar o suporte:**

Entre em contato com o suporte da Adobe Commerce Cloud quando:

* As mensagens de erro não são claras ou não têm detalhes suficientes
* Falha consistente nas operações de patch
* Você precisa de assistência para a resolução manual de conflitos
* As verificações de integridade falham, mas a causa não é aparente
* Você precisa de ajuda com problemas de sincronização do ambiente

**Informações a serem fornecidas:**

Ao entrar em contato com o suporte, forneça:

* **ID do projeto** - O identificador do projeto do Adobe Commerce Cloud
* **ID do Ambiente** - O ambiente específico onde o problema ocorreu
* **ID da Operação** - O identificador de operação [!DNL Patching Automation]
* **Detalhes do erro** - Concluir mensagens e logs de erro
* **Etapas a serem reproduzidas** - O que você estava fazendo quando ocorreu o erro
* **Tentativas anteriores** - O que você já tentou resolver

### Recursos adicionais

Para obter informações técnicas mais detalhadas:

* Revisar os logs de erros completos fornecidos com operações com falha
* Consulte a documentação do Adobe Commerce para obter orientação específica sobre patches
* Entre em contato com o suporte da Adobe Commerce Cloud para obter problemas específicos do ambiente

### Tópicos relacionados

* [Documentação da Adobe Commerce Cloud](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/overview)
* [Guia de instalação do Adobe Commerce](/help/installation/overview.md)
* [Introdução à automação de patches](intro.md)
* [Como acessar o](access.md)
* [Visão geral do fluxo de trabalho](workflow.md)
* [Integração com o GitHub](github-integration.md)
* [Práticas recomendadas](best-practices.md)
