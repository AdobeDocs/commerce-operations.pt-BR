---
title: Caminhos de atualização recomendados para 2022
description: Revise as recomendações para planejar sua atualização do Adobe Commerce ou Magento Open Source em 2022.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 0%

---


# Caminhos de atualização recomendados para 2022

Uma implementação de eCommerce é uma evolução — nunca foi realmente concluída. Sua empresa deve estar um passo à frente das tendências, introduzindo os recursos e funcionalidades mais recentes que mantêm seus clientes envolvidos. Com o tempo, esses recursos adicionais aumentam o espaço físico e a complexidade geral da implementação.

Alguns dos fatores gerais que afetam o nível de esforço necessário para seu projeto de atualização incluem, entre outros,:

| Complexidade técnica | Planejamento e estratégia |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Extensão das personalizações | Clareza dos requisitos, decisões de hesitação e alcance |
| Número de extensões | Sua frequência de atualização |
| Número de integrações com terceiros (OMS, ERP) | Sua estratégia de teste |
| Codificação para práticas recomendadas |  |

Os seguintes são caminhos recomendados pela Adobe Commerce para manter seu site seguro e com desempenho ao longo de 2022.

## Atualização das versões 2.3.0-2.3.6 (opção 1)

![](../../assets/upgrade-guide/2.3.0-2.3.6-option1.png)

Você pode ir de qualquer linha 2.3.x para 2.4.3. No entanto, quanto mais tempo você passar sem uma atualização, mais esforço será ir diretamente para 2.4.3, já que a base de código mudou mais.

Por exemplo, se você estiver na versão 2.3.4, lançada em janeiro de 2020, estará em uma versão que tem quase dois anos, portanto, a base de código de 2.4.3, quando comparada à 2.3.4, é muito maior. É por isso que o Adobe recomenda atualizar com frequência, pois o nível de esforço tende a ser ainda maior se você atrasar a atualização por um período prolongado.

Quando estiver no 2.4.3, então no primeiro trimestre você pode continuar seguro ao tomar 2.4.3-p2, o que é um baixo esforço, pois é uma versão de segurança leve. Em seguida, no terceiro trimestre, você pode pegar o patch completo 2.4.5 e mais um patch de segurança leve para manter-se seguro no quarto trimestre. Esse caminho requer duas atualizações de alto esforço até o final de 2022.

## Atualização das versões 2.3.0-2.3.6 (opção 2)

![](../../assets/upgrade-guide/2.3.0-2.3.6-option2.png)

Como alternativa, você pode atualizar da 2.3.x diretamente para a 2.4.4 em março de 2022. A partir da versão 2.4.4, você pode pegar o patch de segurança leve no terceiro trimestre e depois atualizar para a versão 2.4.5-p1 no quarto trimestre, que inclui todas as atualizações que estavam na versão 2.4.5 e patches de segurança adicionais.

Considerações principais ao decidir entre essas duas opções:

| Opção 1: Atualizar para 2.4.3-p1 ou -p2 | Opção 2: Atualizar para 2.4.4 ou 2.4.4-p1 |
|--------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| Requer duas atualizações significativas antes do final de 2022 para permanecer seguro, compatível com PCI e receber suporte de qualidade | Requer um upgrade significativo e uma atualização de baixo custo antes do final de 2022 para manter-se seguro, compatível com PCI e receber suporte de qualidade |
| Permite que você chegue a uma versão compatível com PCI mais cedo | Possivelmente enfrentar uma janela mais longa até chegar a uma versão compatível com PCI, já que a linha 2.3 atinge EOL em abril de 2022 |
| Consideração de tempo: pode atrasar a mudança para uma nova versão PHP até o final do ano (agosto) | Consideração de tempo: pode começar a migrar para uma nova versão PHP no início do ano (março) |

## Atualização de 2.3.7 (opção 1)

![](../../assets/upgrade-guide/2.3.7-option1.png)

Como na versão mais recente do 2.3.7, você está em uma linha que está recebendo apenas versões de segurança. No primeiro trimestre de ’22, o Adobe está lançando a última versão de 2.3, que é 2.3.7-p3, juntamente com uma versão de segurança (2.4.3-p2) e uma versão completa (2.4.4).

Sua primeira opção seria pegar o 2.3.7-p3 e obter as correções de segurança mais recentes. Em agosto, você poderá fazer a versão 2.4.5. Por fim, no quarto trimestre, você pode tomar a versão de segurança leve com base na versão completa 2.4.5. Neste cenário, você teria uma versão EOL por alguns meses até assumir a 2.4.5. No entanto, a 2.3.x atualmente não oferece suporte de qualidade e você teria as vulnerabilidades de segurança mais recentes corrigidas.

## Atualização de 2.3.7 (opção 2)

![](../../assets/upgrade-guide/2.3.7-option2.png)

Sua segunda opção seria pegar a versão 2.3.7-p3 para obter as correções de segurança mais recentes rapidamente, já que os patches de segurança da sua linha atual são um baixo esforço para implementar, então você pode iniciar a atualização para 2.4.4.

Em agosto, você poderia pegar 2.4.4-p1, que seria uma versão de segurança leve, e depois no quarto trimestre tirar 2.4.5-p1, que inclui todas as atualizações incluídas na versão 2.4.5 e as versões de segurança mais recentes.

Você também pode ir de 2.3.7-p3 para 2.4.4-p1, mas observe que 2.4.4-p1 é um &quot;aumento pesado&quot;, pois você basicamente está obtendo todas as atualizações incluídas na 2.4.4 e as atualizações de segurança na 2.4.4-p1. Decidir se você deseja iniciar esse aumento mais pesado na linha 2.4.4 em março ou agosto é da sua responsabilidade e de sua equipe.

Considerações principais ao decidir entre essas duas opções:

| Opção 1: Atualize para 2.3.7-p3 e depois para 2.4.5 | Opção 2: Atualize para 2.3.7-p3 e depois para 2.4.4 |
|--------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Receba as atualizações de segurança mais recentes com um patch de segurança de baixo esforço primeiro | Receba as atualizações de segurança mais recentes com um patch de segurança de baixo esforço primeiro |
| Requer uma atualização significativa antes do final de 2022 para permanecer seguro, compatível com PCI e receber suporte de qualidade | Requer um upgrade significativo e uma atualização de baixo custo antes do final de 2022 para manter-se seguro, compatível com PCI e receber suporte de qualidade |
| Enfrente uma janela mais longa até chegar a uma versão compatível com PCI como a linha 2.3 atinge EOL em abril | Consideração de tempo: pode começar a migrar para uma nova versão PHP no início do ano (março) |
| Considerações de tempo: pode atrasar a atualização de maior esforço até agosto | Considerações de tempo: O pode iniciar a atualização de maior esforço em março e, em seguida, fazer uma atualização de baixo custo em outubro |

## Atualização de 2.4.0 para 2.4.2

![](../../assets/upgrade-guide/2.4.0-2.4.2.png)

Como você está na versão 2.4.0-2.4.2, recomendamos que você atualize para 2.4.4 no primeiro trimestre. Este é um esforço relativamente alto devido às mudanças na versão 2.4.4 causadas pela mudança para o PHP 8.1. No entanto, o restante das atualizações do ano são esforços menores, portanto, você só precisa realizar uma atualização de nível superior em 2022.

## Atualização da versão 2.4.3

![](../../assets/upgrade-guide/2.4.3.png)

Como você está no 2.4.3, tomar 2.4.3-p2 no primeiro trimestre seria o menor esforço. Em agosto, você poderá fazer a versão 2.4.5. Por fim, no quarto trimestre, você pode tomar a versão de segurança leve com base na versão completa 2.4.5. Nesse cenário, você só faz uma atualização de nível superior em 2022.
