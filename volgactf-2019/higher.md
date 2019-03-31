# VolgaCTF 2019 Qualifier - Higher - Stego - 100
## Chall

Higher

Take higher

[recorded.mp3](https://q.2019.volgactf.ru/files/7863b4733a16ece2b4cefd899489017d/recorded.mp3)

## Solve

Nós temos um arquivo mp3, então podemos abrir ele com o Sonic Visualizer pra ver se achamos algo, uma das ideias é ver o spectograma do audio:

![Spectogram](https://i.imgur.com/x7o7NvV.jpg)
Colunas largas ou finas, representam 0 ou 1 nesse chall, então podemos escrever o código binário:

    01010110011011110110110001100111011000010
    1000011010101000100011001111011010011100011000001110100010111110011
    0100011011000110110001011111011000110011010001101110010111110110001000110011010111110110100000110011
    00110100011100100110010001111101

Se traduzirmos pra ASCII:

**VolgaCTF{N0t_4ll_c4n_b3_h34rd}**
