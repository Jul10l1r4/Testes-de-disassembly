# `printf` function

Antes de estudar o assunto é necessario vê suas dependencias, nesse caso usamos o [`stdio.h`](http://man7.org/linux/man-pages/man3/stdio.3.html)[1] que é o a biblioteca que trás várias das funções que usamos no C.

## Primeiras analizes

Diante das primeiras analizes obtive alguns detalhes a respeito das bibliotecas usadas:
![Ldd print the dependencies](https://raw.githubusercontent.com/Jul10l1r4/Testes-de-disassembly/master/printf/img/ldd1.png)

Dentro do `stdio.h` possuimos:
* linux-ldso.so
* libc.so
* ld-linux-x86-x64.so

## Observações primárias
Por padrão as três bibliotecas exceto a `libc` são usadas em todas as compilações [e em todas as linguagens] em sistemas unix-like.

### Detalhes de `ld-linux-*.so`
É um carregador (vinculador) dinâmico [que fornece tipagem e prepara (colocando bibliotecas necessarias) para a compilação](2). No ELF(Executable and linkable format, que é o padrão de objetos executaveis do unix) a `ldso` é referenciada como a seção `.interp`.

Então será muito comum vermos `.interp` em programas compilados em unix-like, não apenas em C mas como em outras linguagens compiladas.

**`.interp`:** É uma sessão na qual costuma ser uma das primeiras, justamentes pela posição no código quanto o fato de ser executável, **Todos esses pacotes de conversão e de pre-tipagens e de tipagens são disponíveis graças ao [binutil](http://www.sourceware.org/binutils/).**
![pegando informações detalhadas](https://github.com/Jul10l1r4/Testes-de-disassembly/blob/master/printf/img/objdump.png?raw=true)

[1] https://www.gnu.org/software/m68hc11/examples/stdio_8h-source.html

[2] http://man7.org/linux/man-pages/man8/ld.so.8.html
