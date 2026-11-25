# Gerador de Vagas · Interplan

Ferramenta interna que monta a arte de divulgação de vagas da Interplan para o LinkedIn. O RH preenche os dados da vaga e baixa a imagem pronta, sempre no padrão da marca.

## Formatos

| Formato | Tamanho | Fundo |
|---|---|---|
| Feed LinkedIn | 1080 × 1350 px | `assets/bg-feed.jpg` |
| Story | 1080 × 1920 px | `assets/bg-story.jpg` |

## O que é fixo e o que é editável

**Fixo:** logo (já vem no fundo), a chamada "Vem para a Interplan!" e o rodapé com o e-mail `trabalheconosco@interplanonline.com.br`.

**Editável:**
- Nome da vaga (no máximo 2 linhas, a fonte diminui sozinha)
- Local / modalidade (opcional)
- Responsabilidades (um item por linha)
- Requisitos (um item por linha)
- Benefícios (opcional; a seção some quando o campo fica vazio)

Se a lista ficar grande, o texto diminui para caber. Quando não couber nem assim, a tela mostra um aviso para encurtar os itens.

A ferramenta também gera o texto do post do LinkedIn com os mesmos dados, e guarda o último preenchimento no navegador.

## Como usar

É um site estático, sem build nem dependências.

- **Local:** abra o `index.html` no navegador. Se as imagens de fundo não carregarem por causa do protocolo `file://`, rode um servidor simples na pasta:
  ```bash
  python3 -m http.server 8000
  ```
  e acesse `http://localhost:8000`.
- **Online:** dá para publicar direto no GitHub Pages (Settings → Pages → branch `main`, pasta raiz).

## Estrutura

```
gerador-vagas-interplan/
├── index.html        formulário, prévia e geração da imagem (canvas)
├── assets/
│   ├── bg-feed.jpg   fundo 1080×1350
│   └── bg-story.jpg  fundo 1080×1920
└── README.md
```

## Ajustes rápidos (dentro do `index.html`)

- **E-mail e chamada do topo:** constantes `EMAIL` e `KICK` no início do script.
- **Cores:** objeto `C` (verde institucional `#006431` e verde de destaque `#00C532`).
- **Tamanhos e posições de cada formato:** objeto `FMT` (topo, tamanho do título, do texto, margem do rodapé etc.).
- **Trocar o fundo:** substitua os arquivos em `assets/` mantendo o mesmo tamanho em pixels.

Fontes: Montserrat (títulos) e Heebo (textos), via Google Fonts.
