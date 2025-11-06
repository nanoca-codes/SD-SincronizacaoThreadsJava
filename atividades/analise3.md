No primeiro teste (sem sincronização) o produtor e o consumidor acessavam a váriavel ao mesmo tempo, o que gerava valores repetidos e fora de ordem.
Já no segundo teste (usando os monitores), o acesso ficou mias controlado e os dados passaram a ser armazenados e lidos um de cada vez.
No terceiro teste (usando eventos) a comunicação entre as threads ficou mais eficiente e também mais organizada, fazendo com que o produtor e consumidor
trabalhassem um de cada vez e de forma sincronizada.
