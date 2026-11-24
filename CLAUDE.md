# CLAUDE.md

Este arquivo orienta o Claude Code (claude.ai/code) ao trabalhar com o código deste repositório.

## Visão geral do projeto

Landing page acadêmica da Santa Cruz Bicycles, feita em um único arquivo `index.html` autocontido. Sem ferramentas de build, sem frameworks, sem gerenciador de pacotes: basta abrir o arquivo no navegador.

## Visualizando a página

```bash
# Qualquer uma destas opções funciona:
python3 -m http.server 8080     # depois abra http://localhost:8080
xdg-open index.html             # Linux: abre direto no navegador padrão
```

## Arquitetura

Tudo fica em `index.html`:

- **CSS**: bloco `<style>` inline no topo. Usa variáveis CSS definidas em `:root` para a paleta de cores (`--vermelho`, `--preto`, `--branco` etc.) e `--angle` para os cortes diagonais entre seções.
- **Fontes**: Google Fonts. `Barlow Condensed` para títulos, botões, rótulos e números; `Inter` para o texto corrido.
- **Seções**: cada uma tem um `id` único usado pelo menu fixo (`#marca`, `#identidade`, `#tecnologia`, `#modelos`, `#personalizacao`, `#experiencia`, `#contato`). Os números grandes em contorno no fundo vêm do atributo `data-num` (renderizado por `[data-num]::before`). Seções escuras com a classe `angle-bottom` ganham uma borda inferior diagonal, e a seção seguinte sobe por baixo dela.
- **Layout responsivo**: dois breakpoints `@media`, `max-width:1000px` (tablets) e `max-width:650px` (celulares).
- **JavaScript**: pequeno script inline no fim do `<body>`, com as animações de entrada ao rolar (IntersectionObserver), a sombra do header ao rolar e a seleção de cores na seção Personalização.
- **Imagens**: todas na raiz do projeto. As fotos de produto `MY27_*.webp` têm fundo transparente. `logo-santacruz.png` (cabeçalho), `logo-santacruz-branco.png` (rodapé) e `favicon.png` foram gerados a partir de `santa-cruz-bicycles-logo-vector.png`. `bikeazul.png`, `bikeverde.png` e `images.png` têm fundo branco, por isso os cards de modelos usam `mix-blend-mode:multiply` para escondê-lo. `docs/preview.png` é a imagem de prévia usada no README.

## Observações

- `logo01.png` é na verdade um arquivo AVIF com extensão `.png` e não é mais usado pela página.
