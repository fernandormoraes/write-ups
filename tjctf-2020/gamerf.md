## Gamer F - Forensics - 80 Pontos

Essa é aquele tipo de desafio que te quebra por um detalhe, eu não sei se havia uma maneira diferente de resolvê-la, mas o detalhe é que uma parte da flag é recitada em japonês...isso mesmo, mas vamos lá:

Inicialmente, é possível ver que parte da flag está coberta no jogo por um quadrado branco:

![](https://i.imgur.com/vxtiBOr.jpg)

E caçando no código do jogo, é também possível ver uma variável que recebe um hexadecimal:

    if  (this.score  ==  80)  
    {  
	    string  text  =  "506172742031206f6620666c61673a20746a6374667b77683372735f";  
	    string  text2  =  "";  
	    for  (int  l  =  0;  l  <  text.Length;  l  +=  2)  
	    {  
		    text2  +=  ((char)byte.Parse(text.Substring(l,  2),  NumberStyles.HexNumber)).ToString();  
	    }  
	    this.messageText.text  =  text2;  
	    this.soundManager.Play("Win Sound");  
    }

Convertendo temos:

Part 1 of flag: tjctf{wh3rs_

Beleza, parte 1 da flag feita, a parte coberta, tem mais de uma forma de pegar a flag de lá, a mais fácil é acessar o arquivo level0, que contém a flag explicitamente:

_sn4ekk}

Que fique claro aqui, que existiam outras formas, fazendo reverse no código, pra pegar essas flags, inclusive pra pegar a segunda parte da flag, automaticamente pegamos a primeira parte que achamos no hexa, pra pegar a segunda parte, na função CheckLineCompletion do TetrisManager, eu tirei todas as verificações para a vitória do jogo, deixando apenas isso:

    if  (this.score  ==  0)  
    {  
	    string  text  =  "506172742031206f6620666c61673a20746a6374667b77683372735f";  
	    string  text2  =  "";  
	    for  (int  i  =  0;  i  <  text.Length;  i  +=  2)  
	    {  
	    text2  +=  ((char)byte.Parse(text.Substring(i,  2),  NumberStyles.HexNumber)).ToString();  
    }  
	    this.messageText.text  =  text2;  
	    this.soundManager.Play("Win Sound");  
    }

Isso vai tocar o "Win Sound" e a primeira parte da flag também, a segunda flag é soletrada em japonês, duas vezes, uma normalmente e outra em hexa, após muitas tentativas utilizando programas de "Speech to Text", diminuindo e aumentando a velocidade do audio pra que pudesse ter com mais precisão o que era falado, consegui a segunda parte da flag.

![enter image description here](https://i.imgur.com/MU3Hi17.jpg)

the_T5sp1b

Assim temos a flag completa:

**tjctf{wh3rs_the_T5sp1b_sn4ekk}**

OBS: Uma outra alternativa pra pegar a flag que é coberta pelo quadrado branco, é alterar a função ChangeOpacity que fica no UIManager, daí é só tentar aumentar ou diminuir o som para poder pegar ela.
