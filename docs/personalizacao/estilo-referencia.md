# Estilo de referência: o que foi aplicado

Fonte: `openai-brand-styling.md` (valores CSS extraídos de uma página pública, sem medição em navegador). Regra: [ADR-002](../adr/ADR-002-css-global-home-blog-artigos.md), que abre uma exceção ao ADR-001 para o CSS global.

Os valores foram usados como **escala de tipografia, neutros e raios**. A identidade da marca OpenAI não foi usada.

## Aplicado

| Item | Onde | Valor |
|---|---|---|
| Tema escuro | `.dark` em `global.css` | fundo `#000000`, texto `#ffffff`, secundário `#999999` |
| Escala tipográfica | tokens `--type-*` | h1 32 a 64px, h3 24 a 30px, h4 20 a 22px, corpo 17px/28px, legenda 14px/22,96px |
| Títulos | só no artigo | peso 500; H1 com −0,03em; H2 usa a escala h3; H3 usa a escala h4 |
| Corpo do artigo | `[data-surface="article"] .prose` | 17px, linha de 28px, −0,01em, parágrafos a 24px |
| Raios editoriais | tokens `--radius-editorial-*` | 0,25rem, 0,38rem e 1rem |
| Bordas | `--line-strong` | `#ffffff33` no escuro |
| Acessibilidade | seções 14 e 15 do CSS | foco visível nos links do artigo; sem animação e sem rolagem suave com `prefers-reduced-motion` |

A Home e o índice do Blog ficaram com o mesmo layout: o build novo e o anterior têm altura idêntica em 7 larguras (1440 a 360px), nos dois temas.

## Validação

- `npm run check:slots`, `npm run build`, `npm run cf:check` e o lint passam.
- Estilos computados medidos no Chromium: corpo 17px/28px; H2 30px/39,6px e H1 64px em 1440px; H2 24px e H1 32,5px em 390px.
- Sem rolagem horizontal no artigo em 1440 e 390px.

## Não aplicado, e por quê

| Item do documento | Motivo |
|---|---|
| Fonte "OpenAI Sans" | É proprietária e não está disponível ao projeto. Ficam DM Sans (títulos) e Inter (corpo), o que o ADR-002 §4.1 já define. As quebras de linha diferem da referência. |
| Wordmark OpenAI e Blossom | Pertencem a outra marca. O site usa a marca Risco Cognitivo. |
| Acentos Sol, Terra e Luna | São cores da ilustração daquela página, e o próprio documento diz que não são paleta universal. O site não tem componente equivalente. |
| Sombras, fotografia, tamanho mínimo do logo | Estão marcados como GAP no documento. Não foram inventados. |
| Tipografia da Home | Aplicá-la mudaria as quebras de linha do texto já ajustado e verificado. Precisa de decisão (ver abaixo). |
| Container de 1440px e grade de 12 colunas | O ADR-002 mantém o container atual de 1220px e os breakpoints existentes. |

## Pendências

1. **Home:** decidir se a escala tipográfica também vale para ela. Se sim, o texto precisa ser reajustado de novo, linha a linha.
2. **Artigo `risco-cognitivo`:**
   - Há dois `h1`: o do cabeçalho e o `# título` do Markdown. O ADR-002 §5.3 pede um só. A correção é no arquivo `.md`.
   - Falta `image` no cabeçalho do arquivo; o cabeçalho do artigo e o card do Blog mostram uma imagem quebrada.
3. **`lang="en"`** continua no layout, e o texto do Blog ainda está em inglês ("Explore our blog…").
