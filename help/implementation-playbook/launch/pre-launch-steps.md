---
title: Etapas de pré-lançamento
description: Use nossas listas de verificação de pré-lançamento para garantir uma implementação sem problemas do site Adobe Commerce.
exl-id: bd10881f-0336-4aa4-82ad-4d635010e2e4
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Etapas de pré-lançamento

Quando tiver concluído a implantação e o teste nos ambientes de preparo, você poderá iniciar a preparação para o lançamento do site. O armazenamento temporário é um ambiente de quase produção executado em hardware, configurações, arquitetura e serviços semelhantes. Ele pode reduzir o tempo de inatividade e tornar sua extensão, serviço, configurações personalizadas e componentes essenciais de teste de aceitação de usuários comerciantes para liberar seus sites e lojas.

A lista de verificação de pré-lançamento é necessária para verificar antes do estado de inicialização, que inclui as seguintes verificações principais:

- Congelamento de código para implantação
- Certifique-se de que o tempo de inatividade tenha sido comunicado antecipadamente pelo menos um dia para a versão de manutenção e uma semana para a primeira inicialização
- Os scripts de implantação são configurados/configurados completamente para ambientes de produção/armazenamento temporário/integração
- Todos os bancos de dados são configurados e idênticos entre os ambientes de preparo e produção
- Os certificados SSL (TLS) são validados para ambientes de preparo/produção
- Os serviços de email estão bem configurados e funcionam para emails transacionais
- O CDN está configurado para ambientes de preparo/produção
- Configurar a verificação de segurança para ambientes de preparo/produção
   - Análise de segurança do Adobe Commerce
- Faça uma avaliação de desempenho por
   - JMeter
   - Cerco
   - Teste de página da Web
   - Velocidade de página do Google
- Validar todas as integrações de terceiros que funcionarão no aplicativo (OMS, CRM)
- Habilitar ferramenta de monitor de desempenho (Novos Relics)
- Atividades de migração de dados em ensaio (se for caso disso)

![Diagrama que mostra a fase 1 do processo de lançamento](../../assets/playbooks/launch-steps-1.svg)

As principais diferenças entre as implementações locais e de nuvem do Adobe Commerce são os scripts e as ferramentas de implantação, bem como a configuração para SSL, Serviço de email e CDN. Mas o processo continua o mesmo.

Para o certificado SSL(TLS), o Adobe Commerce na infraestrutura de nuvem fornece um certificado curinga Fastly. Para começar a usá-lo, você precisa passar a validação: adicione o registro Fastly TXT ao nome do domínio de anexo nas configurações de DNS. O registro TXT Fastly pode ser encontrado na planilha integrada; caso contrário, é necessário enviar o suporte a um tíquete para obtê-lo. Substitua este texto com suas perguntas/comentários aqui. Se você usar seu próprio certificado SSL(TLS) em vez de um certificado curinga Fastly, envie um tíquete de suporte com seu certificado anexado à configuração.

A infraestrutura em nuvem do Adobe Commerce fornece a funcionalidade SendGrid Mail para seus emails transacionais. Para planos Pro, você precisa adicionar registros SendGrid às suas configurações de DNS. Os registros SendGrid podem ser encontrados na planilha de integração, caso contrário, o SI ou o comerciante devem enviar tíquetes de suporte para obtê-los. Para iniciar, não é necessário fazer alterações no DNS; SendGrid é pré-configurado para você.

## Lista de verificação de pré-lançamento completa

A lista de verificação de pré-lançamento completa mostra todas as principais atividades cuja integridade é necessária para migrar para o estado de inicialização.

- Planos de redução dos riscos em tempo real atualizados
- Foram fornecidos os nomes de domínio corretos
- Emails de saída foram testados
- O certificado SSL está provisionado e configurado
- Toda a configuração importante do aplicativo Adobe Commerce é atualizada corretamente
- URLs base e URL de administrador base são definidos corretamente como nome de host final
- As senhas de administrador são alteradas
- Todos os usuários com acesso ao aplicativo que não exigem mais acesso são removidos
- Configuração de pagamento para o ambiente de produção (para alguns, o pagamento está usando o modo sandbox para testes)
- Os dados de teste (cliente, lista de desejos, revisões, pedidos e dados relacionados) do banco de dados de Produção são apagados

![Diagrama que mostra a fase 2 do processo de lançamento](../../assets/playbooks/launch-steps-2.svg)
