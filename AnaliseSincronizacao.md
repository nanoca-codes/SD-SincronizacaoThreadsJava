# Relátorio sobre Analises de sincronização no JAVA

#### O que é uma análise de sincronização?

Uma análise de sincronização nada mais é que um processo que visa garantir a consitencia e atualização dos dados ou processos e em diversos sistemas ou dispositivos, os matendo funcionando de forma coordenada e harmonica.

Na área da programação, a soncronização de processos evita que múltiplos programas acessem os mesmos dados ao mesmo tempo e de forma incorreta, fazendo assim o sistema funcionar de forma coerente.


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



### 2. Execução feita com Monitores 

Na segunda atividade a proposta foi executar um programa utilizando **monitores**, os quais controlam o acesso e evitam que interferências simultâneas ocorram. Nessa execução a palavra ***synchronized*** foi adicionada nos métodos armazenar e carregar, o que garantiu que apenas uma thread por vez acessasse a váriavel **DADO**.

![Print da segunda execução.]("C:\Users\acoli\OneDrive\Pictures\Screenshots\Captura de tela 2025-11-06 154623.png") 

No inicio da execução a mensagem **"Iniciando"** e no final a mensagem **"Finalizando** mostram que o acesso está sendo feito de uma forma controlada e sequenial, diferente da primeira execução. Isso faz que não existam mais leituras e fora de ordem ou repetidas já que cada valor é produzido e lido na sequência correta.

Ao usar os monitores, o programa passou a funcionar de forma controlada e previsível, eliminando a condição de corrida. Isso fez com que as threads trabalhassem em turnos diferentes, respeitando a integridade dos dados mesmo que pequenas pausas de espera entre as operações ocorressem.


