# Como adicionar produtos na vitrine KCAZ

A vitrine lê os produtos de uma **planilha do Google**. Depois de configurada,
adicionar produto = adicionar uma linha na planilha. **Não precisa mexer em código
nem fazer deploy.**

---

## Passo 1 — Criar a planilha (só uma vez)

1. Acesse https://sheets.new (cria uma planilha nova)
2. Menu **Arquivo → Importar → Fazer upload** e envie o arquivo `produtos.csv`
   deste projeto. Em "Importar arquivo", escolha **Substituir planilha**.
   - Isso já cria as colunas certas: `codigo`, `nome`, `precoAntigo`,
     `precoNovo`, `link`, `imagem`
3. Dê um nome à planilha (ex.: "Produtos KCAZ")

## Passo 2 — Publicar a planilha na web (só uma vez)

1. Menu **Arquivo → Compartilhar → Publicar na web**
2. Na aba **Link**:
   - Em "Conteúdo a publicar": deixe a planilha inteira ou a aba "Página1"
   - No formato, troque de "Página da Web" para
     **Valores separados por vírgula (.csv)**
3. Clique em **Publicar** e copie o link gerado
   (algo como `https://docs.google.com/spreadsheets/d/e/2PACX-.../pub?output=csv`)

## Passo 3 — Ligar a planilha no site (só uma vez)

1. Abra o arquivo `index.html`
2. Perto do topo do `<script>`, ache a linha:
   ```js
   const SHEET_CSV_URL = '';
   ```
3. Cole seu link entre as aspas:
   ```js
   const SHEET_CSV_URL = 'https://docs.google.com/spreadsheets/d/e/2PACX-.../pub?output=csv';
   ```
4. Salve e envie pro GitHub (a Vercel publica sozinha):
   ```
   git add index.html
   git commit -m "Liga a planilha de produtos"
   git push
   ```

---

## No dia a dia — adicionar/editar/remover produto

1. Abra a planilha no Google Sheets (funciona no celular)
2. **Adicionar:** preencha uma nova linha
   **Editar:** mude a célula (preço, nome, link...)
   **Remover:** apague a linha inteira
3. Pronto. O site atualiza sozinho (pode levar alguns minutos para o Google
   propagar a versão publicada). Não precisa commit, não precisa deploy.

### O que vai em cada coluna

| Coluna        | O que colocar                                        | Exemplo |
|---------------|-----------------------------------------------------|---------|
| `codigo`      | O código que você fala no vídeo. Pode ser com ou sem `#` | `#05` ou `05` |
| `nome`        | Nome do produto que aparece no card                  | `Suporte de Celular Articulado` |
| `precoAntigo` | Preço "de" (riscado). Deixe em branco se não tiver   | `129,90` |
| `precoNovo`   | Preço "por". O selo de desconto (-%) é calculado sozinho | `79,90` |
| `link`        | Seu link de afiliado                                 | `https://s.click.aliexpress.com/e/...` |
| `imagem`      | Link direto de uma imagem (de preferência quadrada)  | `https://.../foto.jpg` |

Preço pode ser escrito como `79,90`, `79.90` ou `79` — o site entende.

### Dica sobre imagens

- O jeito mais rápido: clicar com o botão direito na foto do produto (AliExpress,
  Amazon, Shopee) → "Copiar endereço da imagem" → colar na coluna `imagem`.
- Se a imagem sumir com o tempo, hospede a sua: pode subir para o próprio
  repositório numa pasta `img/` e usar o link `raw.githubusercontent.com`, ou
  usar um serviço como imgur/Cloudinary.

---

## Enquanto a planilha não estiver ligada

O site funciona lendo o arquivo local `produtos.csv` (os 4 exemplos). Assim dá
para testar o visual antes de configurar o Google Sheets.
