### Introdução
Neste projeto vamos construir um classificador Naive-Bayes para determinar o sentimento de um comentário.

### Instalando o ambiente
O jeito mais simples de começar a trabalhar com Spark é instalar um container com tudo pronto! No site https://hub.docker.com/r/jupyter/pyspark-notebook vemos uma imagem Docker que já vem com pyspark e jupyter lab. Instale a imagem com o comando:

```docker pull jupyter/pyspark-notebook```
Vamos iniciar o ambiente de trabalho com o comando docker run. Para isso precisamos tomar alguns cuidados:

Temos que mapear nosso diretorio local de trabalho para um diretório interno do container, de modo que alterações feitas dentro do container (nesta pasta escolhida) sejam gravadas no nosso diretorio local. No container temos um usuário padrão com username jovyan. No homedir desse usuario temos uma pasta vazia work, que vai servir como local de mapeamento do nosso diretorio local de trabalho. Podemos então fazer esse mapeamendo com a opção -v do comando docker run da seguinte forma:
```-v <diretorio>:/home/jovyan/work```
onde <diretorio> representa seu diretorio local de trabalho.

Para acessar o jupyter notebook e o dashboard do Spark a partir do nosso browser favorito temos que abrir algumas portas do container com a opção -p. As portas são 8888 (para o próprio jupyter notebook) e 4040 (para o dashboard do Spark). Ou seja, adicionaremos às opções do docker runo seguinte:
```-p 8888:8888 -p 4040:4040```
Desta forma, ao acessar localhost:8888 na nossa máquina, estaremos acessando o servidor Jupyter na porta 8888 interna do container.

Vamos iniciar o container no modo interativo, e vamos especificar que o container deve ser encerrado ao fechar o servidor Jupyter. Faremos isso com as opções -it e -rm
Portanto, o comando completo que eu usei na minha máquina Windows para iniciar o container é:

```
docker run -it --rm -p 8888:8888 -p 4040:4040 -v ${PWD}:/home/jovyan/work jupyter/pyspark-notebook
  ```

Agora abra esse notebook lá no container!
