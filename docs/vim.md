# Vim

Vim é um clone do programa editor de textos vi para Unix de Bill Joy. Foi escrito por Bram Moolenaar baseado na fonte para um porte do editor Stevie para o Amiga com a primeiro lançamento público em 1991.

## Comandos

**Comandos básicos no modo normal:**

- `esc`: entrar no modo de comando
- `0` : mover o cursor para o início da linha em que o cursor está posicionado.
- `a` : inserir texto após a posição atual do cursor.
- `A` : inserir texto no final da linha atual.
- `dd` : deletar linha atual.
- `[n]+dd` : deletar n linhas a partir da linha atual.
- `G` : ir para o fim do arquivo.
- `[n]+G` : ir para a n-ésima linha do arquivo.
- `h` : voltar um caractere.
- `H` : ir para a primeira linha exibida na tela atual.
- `i` : inserir texto a partir da posição atual do cursor.
- `I` : inserir texto no início da linha atual.
- `j` : descer uma linha.
- `J` : juntar a linha atual com a linha seguinte.
- `[n]+J` : juntar n linhas consecutivas a partir da linha atual.
- `k` : subir uma linha.
- `l` : avançar um caractere.
- `L` : ir para a última linha exibida na tela atual.
- `n` : procurar, a partir da posição atual do cursor, a próxima ocorrência do texto definido no último comando /.
- `N` : procurar, a partir da posição atual do cursor e indo em direção ao início do arquivo, a próxima ocorrência do texto definido no último comando /.
- `o` : inserir uma linha em branco após a linha atual.
- `O` : inserir uma linha em branco acima da linha atual.
- `p` : inserir linhas copiadas após a linha atual.
- `P` : inserir linhas copiadas antes da linha atual.
- `r` : substituir o caractere atual.
- `R` : substituir um conjunto de caracteres.
- `s` : deletar o caractere atual e inserir texto.
- `S` : apagar linha e inserir novo texto na linha.
- `u` : desfazer a última alteração feita no texto e ainda não desfeita.
- `U` : desfazer a última alteração feita no texto.
- `x` : apagar caractere onde o cursor está posicionado.
- `$` : mover o cursor para o fim da linha em que o cursor está posicionado.
- `[n]+y` : copiar n linhas a partir da linha atual.
- `yy` : copiar a linha atual.
- `[n]+Y` : copiar n linhas a partir da linha atual.
- `YY` : copiar a linha atual.
- `CTRL+B` : voltar uma página.
- `CTRL+F` : avançar uma página.
- `F1` : exibir tela de ajuda.
- `[n]+ENTER` : ir para n linhas abaixo da linha atual.
- `[n]+.` : repetir o último comando que alterou o texto n vezes a partir da posição atual do cursor.
- `[n]+~+ENTER` : inverter a caixa (case) dos n caracteres seguintes ao cursor.
- `/texto` : procurar pela primeira ocorrência do texto especificado a partir da posição atual do cursor.

**Comandos no modo de comando:**

Entramos nesse modo depois de dar um esc. Perceba que aqui nós precisamos digitar dois pontos para dar o comando e dar enter no final. Aqui os comandos aparecem sendo digitados no canto inferior da tela.

- `:r arquivo` : incluir arquivo a partir da linha atual do cursor.
- `:q+ENTER` : sair da tela de ajuda.
- `:q!` : sair do vim sem salvar as alterações.
- `:w <nome>` : salvar arquivo com o nome especificado.
- `:wq` : sair do vim salvando as alterações.
- `:X` : criptografa o arquivo.

**Comandos no modo visual:**

Com o v entramos no visual mode, e com os comandos do modo normal movemos o cursor para que selecione o texto que queremos. Ficará um VISUAL no canto inferior.

- `x`: deleta o que está selecionado
- `y`: copia o que está selecionado
- `s`: entra no modo de edição substituindo o que tinha antes
- `c`: recorta o código selecionado

Para copiar o código selecionado em algum lugar, dê um esc para voltar ao modo normal e depois um p (paste) no local desejado.

## Referências

- <https://dev.to/nfo94/comandos-basicos-do-vim-e-configuracoes-uteis-gkn>
