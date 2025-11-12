# Relátorio sobre Analises de sincronização no JAVA

## Sumário
* [O que é uma análise de sincronização?](#o-que-é-uma-análise-de-sincronização)
* [1. Execução feita sem sincronização](#1-execução-feita-sem-sincronização)
* [2.Execução feita com monitores](#2-execução-feita-com-monitores)
* [3. Execução feita com eventos](#3-execução-feita-com-eventos)
* [Análise pessoal](#análise-pessoal)

࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚ㅤ ࿙࿚   ࿙࿚ ㅤ⊹  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  

### O que é uma análise de sincronização?

Uma análise de sincronização nada mais é que um processo que visa garantir a consitencia e atualização dos dados ou processos e em diversos sistemas ou dispositivos, os matendo funcionando de forma coordenada e harmonica.

Na área da programação, a soncronização de processos evita que múltiplos programas acessem os mesmos dados ao mesmo tempo e de forma incorreta, fazendo assim o sistema funcionar de forma coerente.

[Voltar ao Sumário](#sumário)

࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚ㅤ ࿙࿚   ࿙࿚ ㅤ⊹  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  

## Atividades de Sincronização de Threads em Java

### 1. Execução feita sem sincronização

Na primeira atividade foi proposto uma execução sem sincronização. O programa foi rodado sem nenhuma forma de controle de acesso entre as duas threads disponibilizadas: <ins>**Produtor**</ins> e <ins>**Consumidor**</ins>

##### Exemplo da primeira execução

```
Consumidor: 0
Produtor: 0
Consumidor: 0
Consumidor: 0
Produtor: 1
Produtor: 2
Produtor: 3
Consumidor: 3
Consumidor: 3
```

Pode-se análisar que as threads foram executadas de forma desordenada e concorrente, causando leituras repetidas e inconssistentes. O consumidor leu o mesmo valor diversas vezes, mostrando que a váriavel foi acessada enquanto o produtor ainda fazia atualização de seu conteúdo, o que mostra um comportamento caracteristico de uma condição corrida, onde o resulta depende da ordem aleatória da execução das threads.

Isso faz com que notemos que, sem sincronização o programa apresenta um comportamental totalmente imprevisível, não garantindo que o consumidor leia o valor mais recente do produtor, comprometendo a conscitência e integridade dos dados.

[Voltar ao Sumário](#sumário)

࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚ㅤ ࿙࿚   ࿙࿚ ㅤ⊹  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  

### 2. Execução feita com Monitores 

Na segunda atividade a proposta foi executar um programa utilizando **monitores**, os quais controlam o acesso e evitam que interferências simultâneas ocorram. Nessa execução a palavra ***synchronized*** foi adicionada nos métodos armazenar e carregar, o que garantiu que apenas uma thread por vez acessasse a váriavel **DADO**.

##### Exemplo da segunda execução 

```
Armazenar Iniciando...
Armazenar Finalizando...
Carregar Iniciando...
Carregar Finalizando...
Produtor usando Monitor: 0
Consumidor usando Monitor: 0
Armazenar Iniciando...
Armazenar Finalizando...
Produtor usando Monitor: 1
Carregar Iniciando...
Carregar Finalizando...
Consumidor usando Monitor: 1
```

No inicio da execução as mensagem **"Iniciando"** e **"Finalizando** mostram que o acesso está sendo feito de uma forma controlada e sequenial, diferente da primeira execução. Isso faz que não existam mais leituras e fora de ordem ou repetidas já que cada valor é produzido e lido na sequência correta.

Ao usar os monitores, o programa passou a funcionar de forma controlada e previsível, eliminando a condição de corrida. Isso fez com que as threads trabalhassem em turnos diferentes, respeitando a integridade dos dados mesmo que pequenas pausas de espera entre as operações ocorressem.

[Voltar ao Sumário](#sumário)

࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚ㅤ ࿙࿚   ࿙࿚ ㅤ⊹  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  

### 3. Execução feita com Eventos

Na terceira atividade a proposta foi de executar os programas utilizando **eventos**. Os eventos são representados por pequenos comando como wait e notify, o que permite que as threads se comuniquem entre si. Nessa execução, o produtor sinalizava quando um novo dado estava disponível e só após receber uma notificação o consumidor pode lê-la.


##### Exemplo da terceira execução

```
Produtor usando Eventos: 0
Consumidor usando Eventos: 0
Consumidor usando Eventos: 1
Produtor usando Eventos: 1
Consumidor usando Eventos: 2
Produtor usando Eventos: 2
Produtor usando Eventos: 3
Consumidor usando Eventos: 3

```

Nessa etapa, as threads trabalharam de forma alternada e coordenada, o que evitou esperas desnecessárias. 
Também tivemos o ponto da comunicação direta que é feita via eventos, o que garantiu que o consumidor lesse só depois que o produtor terminou de armazenar o dado.


Com os eventos, o fluxo é muito mais natural e eficiente e também o uso deles faz com que a sincronização seja cooperativa, na qual as threads trocam sinais para trablhar de forma conjunta. Isso faz com que a execução seja muito mais ordenada, sem erros e mais fluida, otimizando o desempenho do programa e mantendo sua consistencia.

[Voltar ao Sumário](#sumário)

࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚ㅤ ࿙࿚   ࿙࿚ ㅤ⊹  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  

## Análise pessoal

Durante a atividade pude notar o quanto as sincronizações são importantes para sistemas, pois as mesmas mantem a consistência e bom funcionamento do seu programa. Obviamente algumas execuções são mais eficiente que outras, como por exemplo a **sincronização entre eventos**, que é muito mais fluida e eficiente que a **sincronização por monitores**, que demanda uma certa espera entre as threads.

Em uma conclusão geral, os mecanismos de sincronização servem para manter o desempenho, integridade e consistência de aplicações. 

[Voltar ao início](#relátorio-sobre-analises-de-sincronização-no-java)

࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  ࿙࿚ㅤ࿙࿚ㅤ ࿙࿚   ࿙࿚ ㅤ⊹  ࿙࿚   ࿙࿚ ㅤ⊹ ㅤ࿙࿚ㅤ ☆ ㅤ࿙࿚ㅤ ⊹  


