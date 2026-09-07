# KCAZ — Achadinhos

Vitrine de produtos afiliados da Kcaz. Página estática (`index.html`) que lê os
produtos de uma planilha do Google publicada em CSV.

## Como adicionar / editar produtos

Tudo pela planilha do Google — sem mexer em código, sem deploy manual.
Veja o passo a passo em [`COMO-ADICIONAR-PRODUTOS.md`](COMO-ADICIONAR-PRODUTOS.md).

Resumo das colunas: `Código` · `Nome` · `Preço` · `Link` · `Imagem`.

> **Importante:** nas colunas `Link` e `Imagem`, cole o endereço em **texto puro**
> (`https://...`). Não use "Inserir link" do Sheets — o CSV publicado só exporta
> o texto visível, não o link escondido.

## Deploy

Hospedado na Vercel, conectado a este repositório. Todo `git push` na branch
`main` gera um novo deploy automaticamente.
