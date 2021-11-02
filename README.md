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
          
          

4 - Escreva um script que crie um diretório ./DATA na sua pasta home, onde DATA deve ser a data atual do sistema obtida a partir do comando date (no formato hora-dia-mes-ano); e copie todos os arquivos do diretório atual para este novo diretório. Pode usar, se quiser a variável $HOME.


