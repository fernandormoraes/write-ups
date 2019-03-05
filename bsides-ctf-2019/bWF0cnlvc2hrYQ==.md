# BSidesSF 2019 - bWF0cnlvc2hrYQ== - 333p
## Chall
O chall nos dá um arquivo dizendo que é uma interceptação de email, o título é um base64 que decodificado retorna "matryoshka", que é um boneco com o mesmo boneco dentro só que menor, e assim você vai abrindo o boneco e ele fica cada vez menor, é praticamente isso que acontece no chall, ele foi um pouco longo pra mim que fiquei em torno de umas 6~8 horas nele(e não terminei a tempo do CTF também).

## Resolução

O email tem diversas partes codificados em base64, decodificando podemos gerar um arquivo pgp, a chave do arquivo pgp e uma imagem com um qrcode.

    key.pgp
    -----BEGIN PGP PRIVATE KEY BLOCK-----
    
    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
    =Hhg6
    -----END PGP PRIVATE KEY BLOCK-----

O QR Code eu decodifiquei online nesse site aqui https://webqr.com/ que retorna "**h4ck_the_plan3t**"

Descompactando o pgp com essa senha e a chave um arquivo hack.zip é gerado, dentro dele um arquivo file.bin, analisando com o binwalk ele diz que é um lzip, porém o lzip não descompacta, o que me fez tentar outra alternativa, http://mark0.net/soft-trid-e.html, esse site me disse que foi compactado com um programa chamado lizard https://github.com/inikep/lizard, e realmente descompactou nos trazendo um PDF, tudo que precisamos nesse pdf é da imagem que parece o wallpaper do windows xp.

Extraindo a imagem do PDF e usando o StegSolver é possível tirar um QRCode dele que retorna o seguinte:

    /Td6WFoAAATm1rRGAgAhARwAAAAQz1jM4ELCAORdABhgwwZfNTLh1bKR4pwkkcJw0DSEZd2BcWATAJkrMgnKT8nBgYQaCPtrzORiOeUVq7DDoe9feCLt9PG-MT9ZCLwmtpdfvW0n17pie8v0h7RS4dO/yb7JHn7sFqYYnDWZere/6BI3AiyraCtQ6qZmYZnHemfLVXmCXHan5fN6IiJL7uJdoJBZC3Rb1hiH1MdlFQ/1uOwaoglBdswAGo99HbOhsSFS5gGqo6WQ2dzK3E7NcYP2YIQxS9BGibr4Qulc6e5CaCHAZ4pAhfLVTYoN5R7l/cWvU3mLOSPUkELK6StPUBd0AABBU17Cf970JQABgALDhQEApzo4PbHEZ/sCAAAAAARZWg==

Decodificando ele parece um arquivo 7z, extraindo nos retorna um out.bin com algumas strings em binário, temos que decodificar na seguinte ordem:

    binary
    octal
    decimal
    hex
    ascii

Ele nos retorna um base64:

    Nlc/TyVBN11SY0ZDL2EuP1lzcSFCallwdERmMCEz

Decodificando ele nos retorna um ascii85:

    6W?O%A7]RcFC/a.?Ysq!BjYptDf0!3

Decodificando temos a flag **CTF{delat_iz_muhi_slona}**
