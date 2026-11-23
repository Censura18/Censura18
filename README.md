# Censura 18

Página publicada no GitHub Pages com a campanha **Black Friday** da Censura 18.

## Conteúdo

- `index.html` — página inicial: campanha Black Friday em 21 páginas.
- `Encerramento do site C18.html` — a mesma campanha Black Friday. O nome do arquivo é
  mantido de propósito, para preservar a URL já divulgada.
- `assets/black-friday/page-01.jpg` … `page-21.jpg` — as 21 páginas da campanha em JPEG
  (convertidas do PDF da campanha), compartilhadas pelas duas páginas.

## Características

- **Sem build:** são arquivos HTML estáticos, servidos diretamente pelo GitHub Pages.
  As imagens ficam no próprio repositório (sem CDN, fontes remotas ou hospedagem em terceiros).
- **Responsiva:** abaixo de 560 px de largura cada página ocupa 100% da tela e a imagem
  escala junto, sem necessidade de pinçar ou dar zoom.
- **Link na última página:** o pill "ACESSE JÁ O NOSSO LINK" da arte é clicável (área que
  cobre o pill e a linha da URL) e leva a `https://censura18.my.canva.site/c18`.
  Um anel fino sobre o pill sinaliza que é botão — sem texto duplicado, já que a tipografia
  da campanha continua sendo a da imagem. O rótulo acessível (`aria-label` + texto `.sr-only`) é
  "Clique aqui no nosso link: censura18.my.canva.site/c18".
- **Carregamento leve:** apenas a primeira página é carregada imediatamente
  (`fetchpriority="high"`); as demais usam `loading="lazy"`.

## Publicação

O site fica em **https://censura18.com.br/** — domínio próprio que aponta para o
repositório **`Censura18/Censura18`** (conta/organização `Censura18`, GitHub Pages com
`CNAME: censura18.com.br`). Este repositório também publica uma cópia em
**https://lucienealves63.github.io/Censura-18/**.

> **Atenção:** os dois repositórios são publicações independentes. A cada atualização de
> campanha, copie `index.html` e a pasta `assets/` também para o repositório
> `Censura18/Censura18`, senão o `censura18.com.br` continua exibindo a campanha antiga.

A publicação em `lucienealves63.github.io/Censura-18` é feita pelo workflow
[`.github/workflows/pages.yml`](.github/workflows/pages.yml) a cada push na `main`:

- o Pages está configurado no modo **GitHub Actions** (`build_type: workflow`), então nenhum build
  é executado — o repositório é apenas empacotado (`actions/upload-pages-artifact`) e publicado
  (`actions/deploy-pages`);
- o environment `github-pages` aceita deploy **somente da branch `main`**;
- dá para disparar manualmente em **Actions → Deploy GitHub Pages → Run workflow**.

Links:

- site principal (domínio próprio): https://censura18.com.br/
- cópia no GitHub Pages: https://lucienealves63.github.io/Censura-18/
- URL já divulgada: https://lucienealves63.github.io/Censura-18/Encerramento%20do%20site%20C18.html

Toda alteração passa por um pull request antes de ir ao ar.

## Como atualizar a campanha

1. Gere as páginas da nova campanha em JPEG (por exemplo, a partir do PDF da campanha),
   na proporção 2209×3125.
2. Substitua os arquivos de `assets/black-friday/` (ou crie a pasta da nova campanha).
3. Atualize as referências das imagens em `index.html` e em `Encerramento do site C18.html`
   (as duas páginas devem continuar com o mesmo conteúdo), o `<title>` e este README.
4. Se a arte final mudar, meça de novo a posição do pill "ACESSE JÁ O NOSSO LINK" e ajuste
   `left/top/width/height` de `.cta-link` e `.cta-ring`.
5. **Sincronize o site do domínio:** copie `index.html` e `assets/` para o repositório
   `Censura18/Censura18` (é ele que o `censura18.com.br` exibe).
6. Faça commit e abra um pull request para a `main`.
