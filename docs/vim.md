# Vim

Vim é um clone do programa editor de textos vi para Unix de Bill Joy. Foi escrito por Bram Moolenaar baseado na fonte para um porte do editor Stevie para o Amiga com a primeiro lançamento público em 1991.

## Comandos

**Comandos básicos no modo normal:**

- `esc`: sair do modo atual e ir para o modo de comando
- `j`: mover o cursor para baixo
- `k`: mover o cursor para cima
- `h`: mover o cursor para a esquerda
- `l`: mover o cursor para a direita
- `shift i`: entrar no modo de edição no caracter em que está
- `shift a`: entrar no modo de edição no final da linha
- `shift o`: entra no modo de edição em uma nova linha abaixo da atual
- `gg`: ir para o início do arquivo
- `shift g`: ir para o final do arquivo
- `w`: pular uma palavra para frente
- `b`: pular uma palavra para trás
- `ctrl ]`: pular um bloco de código para baixo
- `ctrl [`: pular um bloco de código para cima
- `y`: copiar código
- `c`: recortar código
- `p`: colar código um caractere depois do atual
- `x`: deletar caractere
- `dd`: deletar linha
- `ctrl u`: desfazer
- `ctrl r`: refazer
- `shift o`: abre uma nova linha de edição empurrando para baixo o código da linha

**Comandos no modo de comando:**

Entramos nesse modo depois de dar um esc. Perceba que aqui nós precisamos digitar dois pontos para dar o comando e dar enter no final. Aqui os comandos aparecem sendo digitados no canto inferior da tela.

- `:q`: sair do arquivo atual
- `:q!`: saída forçada do arquivo atual
- `:w`: salvar
- `:wq`: salvar e sair

**Comandos no modo visual:**

Com o v entramos no visual mode, e com os comandos do modo normal movemos o cursor para que selecione o texto que queremos. Ficará um VISUAL no canto inferior.

- `x`: deleta o que está selecionado
- `y`: copia o que está selecionado
- `s`: entra no modo de edição substituindo o que tinha antes
- `c`: recorta o código selecionado

Para copiar o código selecionado em algum lugar, dê um esc para voltar ao modo normal e depois um p (paste) no local desejado.

## Referências

- <https://dev.to/nfo94/comandos-basicos-do-vim-e-configuracoes-uteis-gkn>
