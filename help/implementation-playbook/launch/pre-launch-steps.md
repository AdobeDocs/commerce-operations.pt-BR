---
title: Etapas de pré-lançamento
description: Use nossas listas de verificação de pré-lançamento para garantir uma implementação perfeita do site do Adobe Commerce.
exl-id: bd10881f-0336-4aa4-82ad-4d635010e2e4
feature: Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Etapas de pré-lançamento

Após concluir a implantação e o teste nos ambientes de preparo, você pode iniciar a preparação para o lançamento no site. O ambiente de preparo é um ambiente de quase produção executado em hardware, configurações, arquitetura e serviços semelhantes. Ele pode reduzir o tempo de inatividade e tornar sua extensão, serviço, configurações personalizadas e teste de aceitação de usuários comerciais componentes vitais para o lançamento de seus sites e lojas.

A lista de verificação de pré-lançamento é necessária para verificar o estado antes do lançamento, o que inclui as principais verificações a seguir:

- Congelamento de código para implantação
- Verifique se o tempo de inatividade foi comunicado com antecedência pelo menos um dia para a versão de manutenção e uma semana para o primeiro lançamento
- Os scripts de implantação são configurados/configurados completamente para ambientes de Produção/Preparo/Integração
- Todos os bancos de dados são configurados e idênticos entre os ambientes de preparo e produção
- Os certificados SSL (TLS) são validados para ambientes de preparo/produção
- Os serviços de email estão bem configurados e funcionando para emails transacionais
- O CDN é configurado para ambientes de preparo/produção
- Configurar verificação de segurança para ambientes de preparo/produção
   - Verificação de segurança do Adobe Commerce
- Realizar avaliação de desempenho por
   - JMeter
   - Cerco
   - Teste de página da Web
   - Velocidade da página do Google
- Validar todas as integrações de terceiros que funcionarão no aplicativo (OMS, CRM)
- Ativar a ferramenta de monitoramento de desempenho (New Relics)
- Atividades de migração de dados em ensaios (se houver)

![Diagrama que mostra a fase 1 do processo de lançamento](../../assets/playbooks/launch-steps-1.svg)

As principais diferenças entre as implementações de nuvem e no local do Adobe Commerce são os scripts e as ferramentas de implantação, bem como a configuração do SSL, do serviço de email e do CDN. Mas o processo continua o mesmo.

Para o certificado SSL(TLS), o Adobe Commerce na infraestrutura em nuvem fornece um certificado curinga do Fastly. Para começar a usá-lo, você precisa passar na validação: adicione o registro TXT do Fastly ao nome de domínio apex nas configurações de DNS. O registro TXT do Fastly pode ser encontrado na planilha de integração, caso contrário, você precisará enviar um tíquete ao suporte para obtê-lo. Substitua este texto com suas perguntas/comentários aqui. Se você usa seu próprio certificado SSL(TLS) em vez de um certificado curinga do Fastly, envie um tíquete de suporte com seu certificado anexado à configuração.

O Adobe Commerce na infraestrutura em nuvem fornece a funcionalidade SendGrid Mail para seus emails transacionais. Para planos Pro, é necessário adicionar registros SendGrid às configurações de DNS. Os registros do SendGrid podem ser encontrados na planilha de integração; caso contrário, o SI ou o comerciante devem enviar tíquetes de suporte para obtê-los. Para iniciar, você não precisa fazer alterações no DNS; o SendGrid é pré-configurado para você.

## Lista de verificação de pré-lançamento completa

A lista de verificação completa de pré-lançamento mostra todas as principais atividades cuja integridade é necessária para passar para o estado de lançamento.

- Planos de mitigação de riscos em tempo real atualizados
- Nomes de domínio corretos fornecidos
- Os emails de saída foram testados
- O certificado SSL é provisionado e configurado
- A configuração mais importante do aplicativo Adobe Commerce é atualizada corretamente
- Os URLs de base e o URL de administração de base estão definidos corretamente como nome de host final
- Senhas de administrador alteradas
- Todos os usuários com acesso ao aplicativo que não exigem mais acesso são removidos
- Configuração de pagamento para o ambiente de produção (para alguns, o pagamento está usando o modo sandbox para testes)
- Os dados de teste (cliente, lista de desejos, revisões, pedidos e dados relacionados) do banco de dados de Produção são apagados

![Diagrama que mostra a fase 2 do processo de lançamento](../../assets/playbooks/launch-steps-2.svg)
