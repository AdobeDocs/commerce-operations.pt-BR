---
title: Política mensal de patches de segurança isolados
description: Saiba mais sobre os patches de segurança isolados mensais da Adobe Commerce, entregues na Patch Tuesday para fornecer correções de CVE direcionadas entre as versões de patches de segurança.
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
    internal-label: PCI
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 66d7c9fd19785e791635d8e8bdf3d6ff3aa27a20
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 0%
---
# Política de patch de segurança isolada mensal

Para ajudar os clientes da Adobe Commerce a aplicar correções críticas de segurança mais cedo, a Adobe Commerce agora fornece patches de segurança isolados mensalmente na Patch Tuesday (a segunda terça-feira do mês). Consulte a [programação de lançamento do Adobe Commerce](schedule.md) para ver as datas. Esses patches estão disponíveis para instalações do Adobe Commerce na nuvem, Adobe Commerce no local e Magento Open Source.

Um arquivo de patch de segurança isolado contém apenas o código necessário para resolver uma ou mais vulnerabilidades de segurança específicas, fornecido como um arquivo de code-diff com escopo restrito em vez de um pacote completo do Composer. Como as alterações são específicas às vulnerabilidades de segurança, elas podem ser revisadas, testadas e aplicadas mais rapidamente do que uma versão de patch de segurança, sem acionar a resolução de dependência mais ampla e o teste de regressão exigidos por um upgrade de versão de patch de segurança. Todos os meses, o arquivo de patch de segurança isolado é dobrado na próxima versão de patch de segurança completa, para que os clientes possam obter todos os arquivos de patch isolados lançados na próxima versão de patch de segurança (`-pN`).

## Como os patches isolados se encaixam com outros tipos de patch

Os patches de segurança isolados são um dos vários tipos de patches que a Adobe Commerce oferece para manter os clientes seguros e atualizados.

| **Tipo de patch** | **Finalidade** | **Comportamento cumulativo** | **Entrega típica** | **Função** |
| --- | --- | --- | --- | --- |
| Versão do patch de segurança (-pN) | Atualização de segurança e conformidade para uma linha de versão com suporte | Cumulativo — estabelece a linha de base de segurança atual | Pacote do compositor | Linha de base de segurança principal com suporte |
| Arquivo de patch de segurança isolado | Correção direcionada para um ou mais CVEs | Não cumulativo — aplicar em sequência | Arquivo de patch autônomo, geralmente um ZIP. Algumas correções também podem ser incluídas em Patches da nuvem para o Commerce | Correção temporária mais rápida entre versões de patch de segurança |
| Patches da nuvem para o Commerce | Correções críticas obrigatórias (incluindo correções de segurança) e alterações específicas na nuvem | Dependente de versão do pacote | Patches da nuvem para o pacote Commerce gerenciado através de ECE-Tools | Aplicado automaticamente durante a implantação na nuvem |
| Correção da Ferramenta de correções de qualidade (QPT) | Correção de qualidade ou compatibilidade opcional direcionada para um problema específico | Dependente da cadeia de patches | Pacote QPT | Oferece correções de qualidade direcionadas |
| Hotfix | Correção urgente com escopo restrito (por exemplo, um dia zero) | Específico de caso | Pacote ZIP/diff ou independente via QPT | Problemas urgentes de alto impacto |

Os dois tipos de patches de segurança desempenham funções diferentes:

* **Patches isolados** contêm apenas correções de vulnerabilidade e não são cumulativos. Eles não agrupam arquivos de patch isolados lançados anteriormente. Os comerciantes devem aplicar patches em ordem, pois cada novo patch presume que os anteriores estejam em vigor. Para aplicar um patch de segurança isolado, a instalação deve estar na versão mais recente do patch somente de segurança para sua linha suportada, pois as correções isoladas são testadas exclusivamente em relação a essa versão.

* **Os patches de segurança (`-pN`)** são lançados anualmente para todas as linhas de versão com suporte e implantados por meio do Composer. Eles incluem todos os hotfixes de segurança, conformidade e qualidade lançados anteriormente. A Adobe pode lançar patches de segurança adicionais, se necessário.

## Benefícios mensais do patch isolado

A detecção de vulnerabilidades acelerou em todo o setor. As ferramentas de análise assistida por IA agora podem examinar grandes bases de código e apresentar falhas muito mais rapidamente do que a revisão manual, reduzindo a janela entre a divulgação e a exploração. Uma cadência de patch isolada mensal fecha essa lacuna fornecendo correções assim que estiverem prontas, em vez de esperar pela próxima versão de patch de segurança programada.

O objetivo é a velocidade sem sobrecarga desnecessária. Uma correção pronta não fica na fila até a próxima versão de patch de segurança, e os comerciantes não aplicam patches com mais frequência do que o necessário. Arquivos de patch de segurança isolados resolvem essa tensão: cada um é um diferencial estreito e somente de segurança — muito mais simples de revisar e aplicar do que uma versão de patch de segurança, porque seu escopo é deliberadamente limitado.

Essa abordagem funciona porque os patches de uso único ignoram a resolução de dependência e o teste de regressão completo necessários para as versões do Composer, permitindo que eles sejam criados, validados em relação a uma linha de base conhecida e enviados rapidamente. Na infraestrutura da nuvem, essas correções são agrupadas em Patches da nuvem para o Commerce — uma atualização dos comerciantes de pacotes como parte de seu fluxo de trabalho do Composer e de implantação. Depois de atualizada, a correção é aplicada automaticamente durante a implantação sem nenhum arquivo de patch separado para localizar ou aplicar. O fluxo de trabalho manual do arquivo de patch descrito nos boletins de segurança é para instalações locais e do Magento Open Source que não executam o pipeline da Cloud.

## Aplicar patches isolados mensalmente

Para aplicar o arquivo de patch de segurança isolado mensalmente e manter-se atualizado sobre as correções mais recentes, siga o processo abaixo:

1. **Verifique a [programação de lançamento](schedule.md).**

   Novos arquivos de patch isolados mensais são enviados de acordo com a programação de lançamento. Revise o boletim de segurança correspondente para os componentes e CVEs afetados. Cada boletim está vinculado às notas de versão com instruções passo a passo para instalar o arquivo de patch isolado desse mês.

1. **Verifique o status de segurança da instalação do Commerce usando a [Ferramenta de Versão do Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/commerce-version-tool/intro).**

   A ferramenta relata quais patches mensais estão instalados no momento, quais estão ausentes e a quais CVEs a instalação permanece exposta. Isso fornece uma avaliação definitiva de qual ação é necessária, em vez de depender apenas do número da versão.

1. **Confirme sua versão da linha de base.**

   Os patches isolados só são testados na versão `-p` somente de segurança mais recente para a sua linha. Se você estiver atrasado em relação a essa linha de base, aplique-a primeiro.

1. **Aplicar todos os patches ausentes em ordem.**

   Como não são cumulativos, você não pode pular para o arquivo mais recente.

   >[!NOTE]
   >
   >**Clientes da nuvem:** verifique primeiro os Patches da nuvem instalados para a [versão](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest) do Commerce. A correção pode já estar incluída e aplicá-la manualmente pode criar um conflito ou duplicar a correção.

1. **Corresponder arquivos aos componentes instalados.**

   Aplique somente o arquivo que corresponde à sua versão de CE, EE, B2B ou outro componente.

1. **Execute novamente a Ferramenta de Versão do Commerce para confirmar.**

   Verifique se o novo patch é exibido como instalado e se os CVEs relevantes agora são relatados como protegidos.

1. **Testar e, em seguida, implantar.**

   Valide no preparo antes de promover para produção, de acordo com o processo normal de alteração.

Os clientes da nuvem também podem usar a [Automação de patch do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/caps-tool/intro) para aplicar ou reverter patches por meio do painel do Administrador, em vez das etapas manuais do Git e do Composer acima.

## Ações de patch por tipo de implantação

| **Você executou...** | **Que mudanças você deve fazer** |
| --- | --- |
| Adobe Commerce na nuvem | Os Patches da nuvem para o Commerce, fornecidos por meio das ferramentas ECE, aplicam as correções necessárias automaticamente durante a próxima implantação. Você ainda controla as etapas de ramificação, mesclagem e validação e deve verificar os Patches na nuvem das notas de versão do Commerce antes de aplicar manualmente a mesma correção. |
| Adobe Commerce no local | Confirme a versão da linha de base `-p`, baixe o arquivo correspondente a cada componente instalado, aplique em sequência e verifique com a Ferramenta de Versão do Commerce. |

## Perguntas frequentes

A correção de segurança isolada mensal é uma nova política de versão. As perguntas a seguir abordam preocupações comuns.

### Preciso de todos os patches isolados anteriores aplicados ou apenas da versão de patch de segurança mais recente?

Você precisa de ambos. Antes de aplicar um patch isolado, atualize para a linha de base somente segurança mais recente `-p`. Cada patch é testado somente contra aquela linha de base. Os patches isolados não são cumulativos, portanto, aplique os patches perdidos em sequência.

Por exemplo, se você estiver na linha de base da versão atual do `-p`, mas perdeu os patches isolados de julho e agosto, aplique julho, agosto e setembro. A próxima versão completa de `-p` redefine a sequência porque inclui todas as correções isoladas emitidas anteriormente.

### Por que não enviar apenas um pacote do Composer em vez de arquivos de correção separados?

Em uma instalação com vários componentes — CE, EE, B2B e Page Builder — uma versão mensal pode exigir arquivos de patch separados, pois cada arquivo é direcionado a uma versão específica do componente instalado. Combinar todas as correções em um pacote do Composer reintroduziria problemas de resolução de dependência e exigiria testes de regressão de superfície completa; os riscos que patches isolados são projetados para evitar. Os clientes da nuvem não precisam aplicar patches manualmente. Os Patches em nuvem para o Commerce fornecem as mesmas correções por meio do pipeline de implantação existente.

### Com patches em camadas, como sei em que estado de segurança minha instalação está?

Com o lançamento de patches de segurança mensais, a Adobe Commerce apresentou a [Ferramenta de Versão do Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/commerce-version-tool/intro), um utilitário autônomo que relata quais patches estão instalados ou ausentes e quais CVEs sua instalação está protegida. Em vez de depender dos números de versão, a ferramenta lê os metadados de patch e fornece saída legível por máquina para relatórios e integração contínua (CI).

### Isso significa que a Adobe saiu das versões cumulativas de segurança?

Não. A versão anual `-p` permanece como o ponto de verificação de segurança cumulativo principal. Patches isolados complementam essa cadência para CVEs que não podem esperar com segurança por ela. Eles não substituem versões de `-p`. Se você aplicar a versão programada de patch de segurança para sua linha a cada ano, permanecerá em um caminho totalmente compatível e receberá todas as correções que foram emitidas como um arquivo isolado no meio do caminho.

### O envio de correções fora do Composer não torna a instalação padrão menos segura?

Não. O mecanismo de entrega não afeta o resultado de segurança da correção. Um patch isolado aplica a mesma alteração de código incluída posteriormente em uma versão de patch completo (`-p`). Se a correção for fornecida como um pacote do Composer ou como um arquivo independente, isso não terá nenhuma relação com a eficácia. Os comerciantes que não aplicarem o patch permanecerão em sua linha de base de segurança existente até a próxima versão de segurança programada. A aplicação de patches isolados pode reduzir a exposição ao fornecer correções mais cedo, em vez de esperar por um ciclo de lançamento completo.

## Mais ajuda sobre este tópico

>[!MORELIKETHIS]
>
>* [Política de ciclo de vida do software](lifecycle-policy.md)
>* [Política de versão](versioning-policy.md)
>* [Cronograma de lançamento de patches](schedule.md)
>* [Ferramenta de Versão do Commerce](../tools/commerce-version-tool/intro.md)
>* [Boletins e conselhos de segurança do Adobe](https://helpx.adobe.com/security/security-bulletin.html)
