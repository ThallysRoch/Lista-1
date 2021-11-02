#Shell script - Lista 1

1- Escreva um script que imprima uma frase motivacional fofinha =-).
  R= 
       > motivation.sh
       chmod +x motivation.sh
       vim motivation.sh
          #!/bin/bash
          
          echo "Lute pelos seus sonhos, pois ninguém fará isso por você"
          
2 - Escreva um script que pergunte ao usuário o nome de 4 diretórios e salve no arquivo out.txt todo o conteúdo destes 4 diretórios.
  R=
  
       > diretorio.sh
       chmod +x diretorio.sh
       vim diretorio.sh
          #!/bin/bash
          
          read -p "Informe o nome do primeiro diretório: " a
          read -p "Informe o segundo diretório : " b
          read -p "Informe o terceiro diretório: " c
          read -p "Informe o quarto diretório: " d
          
          ls $a >> out.txt
          ls $b >> out.txt
          ls $c >> out.txt
          ls $d >> out.txt
          
3 - Melhore o script anterior para que os nomes dos 4 diretórios sejam passados como parâmetros de linha de comando.
          vim diretorio.sh
          #!/bin/bash
          
          echo "Adicionando o conteúdo dos diretórios no arquivo out.txt
          
          ls $1 >> out.txt
          ls $2 >> out.txt
          ls $3 >> out.txt
          ls $4 >> out.txt
          cat out.txt
          
4 - Escreva um script que crie um diretório ./DATA na sua pasta home, onde DATA deve ser a data atual do sistema obtida a partir do comando date (no formato hora-dia-mes-ano); e copie todos os arquivos do diretório atual para este novo diretório. Pode usar, se quiser a variável $HOME.

    R= 
       > data.sh
       chmod +x data.sh
       vim data.sh
          #!/bin/bash
          
          DATA="$(date +%H:%d.%m.%Y)"
          dest="/home/$DATA"
          mkdir -p ${dest}
          cp * $dest
          
5 - Melhore o script anterior para que este compacte o novo diretório criado, removendo este diretório após a sua compactação. (o arquivo compactado deve ser copiado para o diretório inicial (o diretório atual, no caso).

    R= 
       > data.sh
       chmod +x data.sh
       vim data.sh
          #!/bin/bash
          
          DATA="$(date +%H:%d.%m.%Y)"
          dest="/home/$DATA"
          mkdir -p ${dest}
          cp * $dest
          zip -r ./${DATA}.zip ${HOME}
          rm -r ${dest}
          
6 - Escreva um script que imprime os conceitos de substituição de variáveis, de substituição de shell, e de substituição aritmética, com exemplos.

      R= 
       > conceitos.sh
       chmod +x conceitos.sh
       vim conceitos.sh
          #!/bin/bash

          echo "Substituição de variável é quando designamos uma variável 'a= QualquerCoisa' e o shell faz a substituição da variável pelo resultado, utilizamos o 'a' como parâmetro"
          echo "Exemplo"
          echo "A = Olá"
          a="Olá"
          echo -e 'O resultado da impressão do comando: echo $a, será:' "\n"
          echo -e "$a\n"
          
          echo "Substituição aritmética é quando utilizamos uma expressão matemática, onde o shell fará a substituição da expressão pelo resultado"
          echo -e "Como por exemplo:\n"
          echo 'O comando $(( 20 * 2 )), onde o resultado é 40, o shell se encarregará de realizar a operação e substituir pelo valor resultante, que será:'
          echo -e "\n"
          echo -e "$(( 20 * 2 ))\n"
          
          echo -e "Substituição de Shell: \n"
          echo 'Um exemplo é o comando: echo $(ls), onde será realizado o a substituição pelo resultado do comando ls. Veja o resultado a seguir:'
          echo -e "\n"
          echo $(ls)
          

7 - Escreva um script que peça para o usuário digitar um número inteiro. Armazene este número na variável y. Faça a variável y receber o valor y + 42. Imprima na tela o novo valor de y

      R= 
       > variavel.sh
       chmod +x variavel.sh
       vim variavel.sh
          #!/bin/bash
          
          read -p "Escreva um número inteiro: " num
          echo -e "\n"
          num=$((num+42))
          echo "Resultado: $num"
          
8 - Escreva um script que soma 2 números passados como argumentos de linha de comando. Por exemplo:

      $ ./a.sh 20 40
      > 60

       R= 
       > argumento.sh
       chmod +x argumento.sh
       vim argumento.sh
          #!/bin/bash
          
          echo "A soma dos dois números passados como parâmetros é: "
          a=$(($1+$2))
          echo $a
          

9 - Escreva um script que receba dois argumentos passados pela linha de comando, digamos a e b, e imprima o valor da expressão (a+1) vezes (b+2). Por exemplo:

      $ ./x.sh 0 2
      > 4
      
      
      R= 
       > expressao.sh
       chmod +x expressao.sh
       vim expressao.sh
          #!/bin/bash
          
          echo "O resultado da expressão (a+b) vezes (b+2) é: "
          a=$(( ($1+1) * ($2+2) ))
          echo $a
          

10 - Melhore o script da questão anterior para que aceite números fracionários, isto é, números com casas decimais. Por exemplo:

      $ ./x.sh 0.0 2.4
      > 4.4
      
      R= 
      
      vim expressao.sh
          #!/bin/bash
          
          echo "O resultado da expressão (a+b) vezes (b+2) é: "
          a=$(echo "($1+1) * ($2+2)" | bc)
          echo $a

11 - Escreva um script que recebe 3 nomes de arquivo como parâmetros de linha de comando e imprime a soma dos números de linhas dos 3 arquivos. Utilize a substituição de shell, substituição aritmética e o comando wc -l para contar o número de linhas de cada arquivo. Por exemplo:

$ ./z.sh a.txt b.txt c.txt
> 14

Supondo que os arquivos a.txt, b.txt e c.txt possuam o seguinte conteúdo:

#a.txt:
1
2
3

#b.txt:
0
0
0
0
0
0

#c.txt:
a
b
c
d
e

    R= 
       > linhas.sh
       chmod +x linhas.sh
       vim linhas.sh
          #!/bin/bash
          
          echo "O total de linhas destes arquivos é: "
          
          first="$(wc -l $1)"
          second="$(wc -l $2)"
          third="$(wc -l $3)"
          result=$(( first + second + third ))
          echo $result
          
          
12 - Escreva um script que exiba pelo menos 8 variáveis criadas automaticamente pelo bash, assim como o seu conteúdo e explique o significado desta variável.

Exemplo:
./vars.sh

$HOME (valor atual: /home/gabigol) variável que guarda o valor do diretório inicial do usuário atual.

$1 (valor atual: 12) Variável que guarda o valor do primeiro argumento passado pela linha de comando.

...

    R= 
       > autobash.sh
       chmod +x autobash.sh
       vim autobash.sh
          #!/bin/bash
          
          echo '$HOME, exibe o diretório inical do usuário atual'
          echo ${HOME}
          echo '$1 Variável que guarda o valor do primeiro argumento passado pela linha de comando'
          echo '$PWDD, Exibe o diretório atual, ou seja, o caminho até o local atual'
          echo ${PWD}
          echo '$SHELL, Exibe o Shell utilizado'
          echo $SHELL
          echo '$USER, Exibe o nome do usuário atual'
          echo $USER
          echo '$LANG, Exibe o idioma que está sendo usado'
          echo $LANG
          echo '$RANDOM, gera um número aleatório'
          echo $RANDOM
          echo '$UID, exibe o user id de quem executou o script'
          echo $UID
          echo '$OSTYPE, exibe o tipo do sistema operacional'
          echo $OSTYPE
