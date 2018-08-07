# `printf` function

Antes de estudar o assunto é necessario vê suas dependencias, nesse caso usamos o [`stdio.h`](http://man7.org/linux/man-pages/man3/stdio.3.html)[1] que é o a biblioteca que trás várias das funções que usamos no C.

## Primeiras analizes

Diante das primeiras analizes obtive alguns detalhes a respeito das bibliotecas usadas:
![Ldd print the dependencies](https://raw.githubusercontent.com/Jul10l1r4/Testes-de-disassembly/master/printf/img/ldd1.png)

Dentro do `stdio.h` possuimos:
    *   linux-ldso.so
    *   libc.so
    *   ld-linux-x86-x64.so
Esses arquivos são as dependencias da biblioteca `stdio.h`.

## Observações primárias
Por padrão as três bibliotecas são usadas em todas as compilações criadas pelo gcc, em alguma
plataforma gnu/linux.

### Detalhes de `linux-ldso.so`
É um carregador (vinculador) dinâmico (que fornece tipagem e prepara [colocando bibliotecas necessarias] para a compilação)[2]. No ELF(Executable and linkable format, que é o padrão de objetos executaveis do unix) a `ldso` é referenciada como a seção `.interp`.



[1] https://www.gnu.org/software/m68hc11/examples/stdio_8h-source.html
[2] http://man7.org/linux/man-pages/man8/ld.so.8.html
