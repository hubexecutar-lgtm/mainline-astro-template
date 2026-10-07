# TOKEN-MAP

**Fonte única de cor:** `source/02-design-system/fundamentos/brand-color-system.md` (decisão de 2026-10-07, CONF-001). **Implementação:** `src/styles/global.css` vira o único lugar com valores, a partir da Fase 2. Componentes usam só utilitários ligados a tokens (developer handoff §4.4).

Legenda de origem:
- **FACT_USER:** valor definido na documentação.
- **REFERENCE_PUBLIC:** regra externa (WCAG, BDA ou W3C COGA).
- **PROJECT_DECISION:** decisão deste projeto.
- **INFERENCE:** dedução necessária.
- **GAP:** ausente.

## 1. Cor: tokens de marca

| Token canônico | Valor | Papel | Origem | Fonte |
|---|---|---|---|---|
| `--brand-bg-light-orange` / `--surface-page` | `#FFFDFA` | canvas da página | FACT_USER | BRAND-COLOR-SYSTEM; EDITORIAL-LAYOUT |
| `--brand-light-gray` / `--surface-subtle` / `--line-subtle` | `#ECECEC` | superfície auxiliar (metadados, footnotes), linha | FACT_USER | BRAND; EDITORIAL-LAYOUT |
| `--brand-dark-gray` / `--text-secondary` | `#545454` | texto secundário, eyebrow e callout escuros | FACT_USER | BRAND |
| `--brand-light-blue` | `#CBD4FF` | cor principal da marca, acento suave | FACT_USER | BRAND |
| `--brand-light-blue-soft` | `rgb(203 212 255 / 48%)`, ≈ `#E6E9FC` sobre o canvas | fundo de callout ou headline de definição | FACT_USER | BRAND; MDX §8 |
| `--brand-dark-indigo` | `#0E025D` | eyebrow ou callout institucional forte | FACT_USER | BRAND |
| `--brand-action-blue` | `#2D5CE6` | botões, links, ação, estado ativo | FACT_USER | BRAND |
| `--text-primary` | `#000000` | títulos e corpo | FACT_USER (parcial: "ou derivado escuro") | BRAND |
| `--text-on-dark` | `#FFFFFF` | texto sobre azul, cinza-escuro e índigo | FACT_USER | BRAND |
| `--semantic-solution` | `#00BF63` | solução, controle, resolvido | FACT_USER | BRAND; VECTOR §3 |
| `--semantic-risk` | `#FF0000` | risco, ponto de falha | FACT_USER | BRAND; VECTOR §3 |
| `--semantic-attention` | **GAP** | atenção, revisão | GAP-005 | BRAND |

## 2. Mapeamento para as variáveis shadcn do template (Fase 2)

Os nomes já existem em `src/styles/global.css` e são consumidos por `src/components/ui/*`. Só os valores mudam.

| Variável shadcn | Recebe | Origem do mapeamento |
|---|---|---|
| `--background` | `#FFFDFA` | FACT_USER (canvas) |
| `--foreground`, `--card-foreground`, `--popover-foreground` | `#000000` | FACT_USER |
| `--card`, `--popover` | `#FFFFFF` (micro-card, superfície elevada) | INFERENCE (CARD-HIERARCHY: "micro card: white / elevated surface") |
| `--primary` | `#2D5CE6` | FACT_USER (action blue) |
| `--primary-foreground` | `#FFFFFF` | FACT_USER |
| `--secondary`, `--muted` | `#ECECEC` | FACT_USER (superfície neutra) |
| `--secondary-foreground` | `#000000` | FACT_USER |
| `--muted-foreground` | `#545454` | FACT_USER |
| `--accent` | `--brand-light-blue-soft` | FACT_USER (destaque leve) |
| `--accent-foreground` | `#000000` | FACT_USER ("preto ou azul") |
| `--border` | `#ECECEC` | FACT_USER (line-subtle; decorativa, ver nota de contraste) |
| `--input` | `#545454` | INFERENCE: borda de input precisa de ≥3:1 (WCAG 1.4.11); `#ECECEC` dá 1.16:1 |
| `--ring` | `#2D5CE6` | INFERENCE (handoff do site: "ring = primary") |
| `--destructive` | `#FF0000` com texto preto | FACT_USER (risk) + CONF-013 |
| `--chart-1..5` | `#2D5CE6`, `#00BF63`, `#FF0000`, `#545454`, `#0E025D` | INFERENCE limitado à paleta (VECTOR: sem rainbow) |
| novos em `@theme inline`: `--color-solution`, `--color-risk`, `--color-indigo`, `--color-brand-soft` | tokens da §1 | handoff do site §3.4 |

## 3. Contraste (WCAG 2.2, calculado em 2026-10-07)

| Par (texto / fundo) | Razão | AA texto normal | AA texto grande / UI 3:1 | Fonte |
|---|---|---|---|---|
| `#000000` / `#FFFDFA` | 20.68 | PASS | PASS | MDX §8 (confirmado) |
| `#545454` / `#FFFDFA` | 7.46 | PASS | PASS | MDX §8 (confirmado) |
| `#545454` / `#ECECEC` | 6.41 | PASS | PASS | novo |
| `#000000` / `#ECECEC` | 17.78 | PASS | PASS | novo |
| `#2D5CE6` / `#FFFDFA` (link) | 5.46 | PASS | PASS | novo |
| `#FFFFFF` / `#2D5CE6` (botão) | 5.55 | PASS | PASS | MDX §8 (confirmado) |
| `#2D5CE6` / `#ECECEC` | 4.70 | PASS | PASS | novo |
| `#2D5CE6` / soft blue (`#E6E9FC`) | 4.60 | PASS | PASS | novo |
| `#000000` / soft blue | 17.43 | PASS | PASS | novo |
| `#FFFFFF` / `#545454` | 7.57 | PASS | PASS | MDX §8 |
| `#FFFFFF` / `#0E025D` | 17.72 | PASS | PASS | MDX §8 |
| `#000000` / `#00BF63` | 8.63 | PASS | PASS | MDX §8 |
| `#000000` / `#FF0000` | 5.25 | PASS | PASS | MDX §8 |
| `#FFFFFF` / `#00BF63` | 2.43 | **FAIL** | **FAIL** | MDX §8 |
| `#FFFFFF` / `#FF0000` | 4.00 | **FAIL** | PASS | MDX §8 |
| `#00BF63` / `#FFFDFA` (verde como texto/traço) | 2.40 | **FAIL** | **FAIL** | novo |
| `#FF0000` / `#FFFDFA` (vermelho como texto/traço) | 3.94 | **FAIL** | PASS | novo |
| `#ECECEC` / `#FFFDFA` (linha) | 1.16 | n/a | **FAIL** se essencial | novo |

Regras que saem desta tabela:
- Sobre verde e vermelho, o texto é sempre **preto**. Sobre azul, `#545454` e índigo, o texto é **branco**.
- **Verde nunca é texto nem traço único sobre o canvas** (2.40:1). Quando sinaliza solução, aparece como superfície com texto preto, ou junto com rótulo textual ou ícone preto. Assim a cor nunca é o único canal.
- Vermelho sobre o canvas serve como traço ou ícone gráfico (≥3:1), mas não como texto corrido.
- `#ECECEC` é linha decorativa e não pode delimitar controle (input, checkbox). Para isso vale `--input` = `#545454`.

## 4. Tipografia

| Token | Valor | Origem | Fonte |
|---|---|---|---|
| `--font-sans` / display | DM Sans | PROJECT_DECISION (default do template; GAP-007) | template |
| `--text-family` | Inter | PROJECT_DECISION (default do template; GAP-007) | template |
| corpo do artigo | 18px (`1.125rem`) / 1.6 | PROJECT_DECISION dentro de REFERENCE_PUBLIC (BDA 16–19px, ≥1.5) | LEITURA-COGNITIVA |
| corpo da UI | 16px / 1.6 | REFERENCE_PUBLIC (mínimo BDA) | LEITURA-COGNITIVA; handoff `text-body` |
| H1 do artigo | `clamp(2.25rem, 1.2rem + 4.5vw, 3.75rem)` / 1.05 / peso 400–500 / centralizado | escala: handoff editorial (estimativa ≈); peso: CONF-009 | handoff editorial §3.2; EDITORIAL-LAYOUT |
| H2 do artigo | `clamp(1.4rem, 1.1rem + 1.2vw, 1.75rem)` / 1.25 / 700 | handoff editorial (≈) | handoff editorial §3.2 |
| H3 do artigo | 1.25rem / 1.3 / 700 | handoff editorial (≈) | idem |
| Display da Home | `clamp(2.5rem, 1rem + 5vw, 4.5rem)` / 1.05 / 600 / −0.02em | handoff do site (≈) | developer handoff §3.2 |
| H2 de seção (Home) | `clamp(1.75rem, 0.5rem + 3vw, 2.75rem)` / 1.1 / 600 | handoff do site (≈) | idem |
| caption / micro-label | 0.875rem e 0.75rem / `#545454` | handoff do site + CARD-HIERARCHY | — |
| métrica (micro-value) | semibold ou bold, `tabular-nums` | FACT_USER (CARD-HIERARCHY) | — |
| ênfase | bold ≤2 por parágrafo, ≤4 palavras; sem itálico ou caixa-alta como ênfase | PROJECT_RULE | MDX §12 |

## 5. Espaço, leitura e layout

| Token | Valor | Origem | Fonte |
|---|---|---|---|
| `--space-1..24` | 4, 8, 12, 16, 24, 32, 48, 64, 96 px | PROJECT_DECISION | LEITURA-COGNITIVA (igual à escala Tailwind de 4px) |
| `--reading-width` | **68ch** (faixa 60–72ch, máximo 80ch) | PROJECT_RULE | MDX §3; CONF-005 |
| reflow mínimo | 320 CSS px sem rolagem horizontal do corpo | REFERENCE_PUBLIC (WCAG 1.4.10) | MDX §3 |
| alvo interativo | ≥24×24 px (o projeto usa 44 px em botões) | REFERENCE_PUBLIC (WCAG 2.5.8) + handoff | LEITURA; handoff §5.3 |
| proximidade de títulos | ≈2.6 lh acima, 1–1.5 lh abaixo | handoff editorial (≈) | handoff editorial §4 |
| container | `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8` | handoff do site | §3.3 |
| `--radius` | `8px` (template) | INFERENCE, GAP-010 | template |
| sombra do micro-card | `--shadow-sm` (template) | INFERENCE, GAP-010 | CARD-HIERARCHY ("subtle") |
| motion | 150, 250 e 500 ms; `cubic-bezier(0.22, 1, 0.36, 1)`; respeitar `prefers-reduced-motion` | handoff do site | §3.3, §10 |

## 6. Tokens de figura e ilustração (sem CSS na Fase 2; uso em SVG)

| Token | Valor | Fonte |
|---|---|---|
| `figure-bg` | `#FFFDFA` | VECTOR §2 |
| `figure-ink` / `figure-ink-muted` / `figure-line-subtle` | `#000000` / `#545454` / `#ECECEC` | VECTOR §2 |
| `figure-accent-brand` / `-soft` / `-indigo` | `#2D5CE6` / `#CBD4FF` / `#0E025D` | VECTOR §2 |
| `figure-accent-solution` / `-risk` / `-attention` | `#00BF63` / `#FF0000` / **GAP** | VECTOR §2 |
| proporção de cor | 80–95% neutro, 5–20% acento semântico | VECTOR §1 (PROJECT_RULE) |
| espessura do traço | guia 1×, estrutural 1.5×, ativo 2× | VECTOR §5 |
| rampa isométrica de solução | `#E7F8EE #B8EBCB #73D99A #00BF63 #007A3E` | INFOGRAPHIC (as de risco e marca são GAP-014) |
