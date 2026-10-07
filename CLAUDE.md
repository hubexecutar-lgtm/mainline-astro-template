# CLAUDE.md

Site em Astro 5 + React 19 + shadcn/ui + Tailwind 4 (template Mainline), personalizado com a identidade **Risco Cognitivo**. É 100% estático e é publicado na Cloudflare (Workers Static Assets, ver `wrangler.jsonc`).

## Fonte de verdade: `docs/design-system/`

Toda decisão visual, de componente, de página ou de rota vem de `docs/design-system/`. Comece por `docs/design-system/README.md`.

- `docs/design-system/source/` guarda o kit original, preservado byte a byte. **Não edite.**
- Os registros ficam em `docs/design-system/audit/`: TOKEN-MAP, COMPONENT-INVENTORY, PAGE-PATTERN-MAP, ROUTE-MATRIX, CONFLICT-REGISTER e GAP-REGISTER.
- **Cor:** a fonte única é o BRAND-COLOR-SYSTEM. Os valores ficam só em `src/styles/global.css`. Componentes usam utilitários ligados a tokens, nunca HEX ou `rgb()` direto.
- **Valor ausente** é GAP: não invente. Registre no GAP-REGISTER e use o tratamento descrito lá.
- **Conflito entre documentos:** registre no CONFLICT-REGISTER com fontes e precedência. Não resolva em silêncio.
- **Primeiro reutilizar** (`src/components/ui`, `src/components/blocks`), depois estender (`src/components/patterns`). Não troque framework, rotas ou dependências sem registro.
- **Artigos MDX** só usam os componentes autorizados (`docs/design-system/14-mdx/`) e seguem o Reading Flow Contract (`07-reading-flow/`). Não reescreva conteúdo editorial para caber num componente.
- **Plano por fases:** `docs/design-system/audit/IMPLEMENTATION-PLAN.md`.

## Verificação antes de cada PR

- `npm run build`
- `npm run lint`
- `npm run cf:check`
- Telas em 360, 390, 768, 1024 e 1440 px, nos temas claro e escuro: sem rolagem horizontal, um `h1`, foco visível e contraste da TOKEN-MAP §3.

## Comandos

- `npm run dev`: servidor local
- `npm run build`: gera `dist/`
- `npm run lint`: ESLint com `--fix`
- `npm run cf:check`: build + `wrangler deploy --dry-run`
- `npm run cf:preview`: build + `wrangler dev`
- `npm run deploy`: build + deploy na Cloudflare (só com autorização explícita)
- `python3 scripts/gerar-marca.py`: gera o wordmark SVG a partir da DM Sans

## Atenção

- `src/components/blocks/navbar.tsx` e `footer.tsx` aparecem em **todas** as páginas.
