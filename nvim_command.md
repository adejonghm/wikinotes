# Commands

## General

undo – u
redo – Ctrl + r

## Select text using character mode (v)

change – c
yank(copy) – y
delete(cut)d
paste – Shift + p

## Select lines using line mode (Shift + v)

hereda los comando de modo visual y ademas tiene:

\> – Indent

\< – UnIndent

## Select text using block mode (Ctrl + v)

hereda los comando de modo visual y ademas tiene:

Shift + i – insert in front of block

Shift + a – insert after the block

aw – select a word

ab – select a block with ()

aB – select a block with {}

at – select a block with <>

ib – select inner block with ()

iB – select inner block with {}

it – select inner block with <>

Adicionar comentarios:

- Ctrl + v
- Seleccionar las lineas con las flechas UP/DOWN o la tecla j
- Shift + i ... Escribir el caracter de comentario.
- Esc o Ctrl + [ ... Para regresar al modo normal.

Insertar texto en el medio del bloque:

- Selecionar el punto donde se quiere insertar/reemplazar.
- c para reemplazar
- escribir el nuevo caracter y luego Esc para regressar al modo normal. Los caracteres selecionado con c se quedan en el buffer, lo que permite pegarlos despues en otro lugar.
