# IMPLEMENTATION-PLAN

A entrega é feita por fases, com um PR por fase e aprovação do usuário entre elas. A stack não muda: Astro 5, React 19, Tailwind 4, shadcn/ui, MDX e Cloudflare.

| Fase | Entrega | Arquivos principais | Aceite |
|---|---|---|---|
| **1. Auditoria e normalização** (este PR) | kit preservado em `source/`, índice normalizado 01–16, os 9 entregáveis, CLAUDE.md sem o ADR-001 | `docs/design-system/**`, `CLAUDE.md`, `package.json`, `scripts/` | `sha256` dos 33 originais = MASTER-INDEX; build passa |
| **2. Tokens e storyboard** | valores do BRAND-COLOR-SYSTEM nas variáveis shadcn; tokens semânticos; tema escuro derivado; storyboard homogeneizado | `src/styles/global.css`, `docs/design-system/storyboard/storyboard-componentes.html` | contraste da TOKEN-MAP §3 medido no navegador; nenhum HEX ou `rgb(` em `src/components` |
| **3. Home, Blog e Artigo** | patterns (Section, Eyebrow, FeatureCard, MicroCard, ArticleCard, PageHeader, CTA, RelatedContent); componentes MDX autorizados; `risco-cognitivo` em `.mdx` com os mesmos `@block`; `lang="pt-BR"`; posts placeholder fora | `src/components/patterns/**`, `src/pages/{index,blog/*}.astro`, `src/layouts/DefaultLayout.astro`, `src/content/blog/*` | ver Verificação |
| **4. Demais rotas e QA** | `/mapas`, `/ferramentas`, About, FAQ, Contato, 404 nos padrões; Navbar e Footer; QA | `src/pages/*`, `blocks/{navbar,footer}.tsx` | ver Verificação |

## Regras durante a implementação

- Toda decisão visual cita um ID: um token da TOKEN-MAP, um CMP-xxx, um PAT-xxx, um CONF-xxx ou um GAP-xxx.
- Um GAP aberto nunca vira valor. O componente afetado fica sem a variante ou usa o default seguro registrado.
- O conteúdo editorial do golden sample não é reescrito. Só a marcação muda (blockquote → `<Callout>`, bloco ```` ```text ```` → `<Diagram>`).

## Verificação (em todo PR)

- `npm run build`, `npm run lint` e `npm run cf:check`.
- Playwright (Chromium do ambiente) em 360, 390, 768, 1024 e 1440 px, claro e escuro, em Home, Blog, Artigo, `/mapas` e `/ferramentas`, verificando:
  - sem rolagem horizontal da página;
  - um único `h1` e sequência de headings sem salto;
  - foco visível ao navegar com Tab;
  - `alt` em toda `img`;
  - `prefers-reduced-motion` respeitado.
- Contraste medido sobre as cores computadas, comparado com a TOKEN-MAP §3.
- Lint editorial do golden sample: os limites do MDX-CONTRACT §2 continuam PASS, como na auditoria YAML.
