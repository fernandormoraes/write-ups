## Gamer R - TJCTF 2020 - Reversing

Nesse desafio, no primeiro momento, eu quis explorar o jogo para poder fazer pontos sem que nada me atrapalhasse, então esse foi meu foco inicial, e acabou que isso foi o suficiente pra poder pegar a flag.

Utilizei o dnSpy para fazer o reverse, carreguei a Assemble-CSharp.dll, que é geralmente onde os scripts feitos para o jogo ficam na Unity.

![Classes que podemos achar vasculhando adll](https://i.imgur.com/iFhEN4j.jpg)
DuckColissionSystem e KnifeMoveSystem parecem ser muito interessantes para começar a exploração, até porque o que precisamos é que os patos não colidam com as facas que lançamos e precisamos dar uma agilizada nessa faca.

No DuckCollisionSystem, temos a classe hitBoxRadius com o valor **0.6f**, já sabemos o que fazer, podemos zerar esse valor e os patos não irão colidir mais com as facas.

Em KnifeMoveSystem, temos a classe speed com o valor **15f**, setei como **800f** para as facas serem rápidas o suficiente para agilizar no desafio.

E isso foi o suficiente, no score, enquanto pontuando, algumas letras aparecerão, essas serão as letras da flag(e de um texto inicial que só serve para atrapalhar), mas pronto, já temos a flag:

![Cheatando no jogo](https://i.imgur.com/KiDR0C2.jpg)

here's the flag you're looking for! haha jkjk... unless...?  
  
**tjctf{orenji_orange}**

