# COMPONENT-INVENTORY

Ordem de construção: primeiro reutilizar e depois estender. Um componente novo só nasce quando nenhum dos existentes resolve o requisito.

As três camadas:
- **Primitivos:** `src/components/ui/*`, shadcn, 52 arquivos.
- **Patterns:** `src/components/patterns/*`, novos, compostos a partir dos primitivos.
- **Blocks:** `src/components/blocks/*`, seções de página.

Estado:
- **EXISTE:** já está no repositório e fica como está.
- **RESTYLE:** já está e só muda via tokens.
- **ADAPTAR:** já está e ganha props ou variantes.
- **NOVO:** a criar.
- **FORA:** fora de escopo (CONF-008).

Tokens citados: ver `TOKEN-MAP.md`. A acessibilidade segue o developer handoff §11 e a LEITURA-COGNITIVA.

## Primitivos shadcn já instalados (reuso obrigatório)

accordion, alert, alert-dialog, aspect-ratio, avatar, badge, breadcrumb, button, button-group, calendar, card, carousel, chart, checkbox, collapsible, command, context-menu, dialog, drawer, dropdown-menu, empty, field, form, hover-card, input, input-group, input-otp, item, kbd, label, menubar, navigation-menu, pagination, popover, progress, radio-group, resizable, scroll-area, select, separator, sheet, sidebar, skeleton, slider, spinner, switch, table, tabs, textarea, toggle, toggle-group, tooltip.

Nenhum primitivo novo precisa ser instalado. O `empty.tsx` cobre o EmptyState, o `table.tsx` a DataTable, o `pagination.tsx` e o `breadcrumb.tsx` a navegação, e o `separator.tsx` o Divider.

## Inventário

| ID | Componente | Camada / arquivo | Propósito | Variantes | Estados | Props principais | Tokens | Responsivo | A11y | Do | Don't | Fonte | Estado |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **GLOBAL** |||||||||||||||
| CMP-001 | Navbar | blocks/navbar.tsx | navegação global, presente em todas as rotas | desktop, mobile (menu) | ativo `aria-current`, aberto/fechado | links de `consts.ts` | background, foreground, primary | menu em sheet abaixo de lg | skip link antes; foco visível | links iguais em todas as rotas (COGA: consistência) | links que mudam de lugar por rota | handoff §6.0 | ADAPTAR (links /blog, /mapas, /ferramentas) |
| CMP-002 | Footer | blocks/footer.tsx | links secundários, legal | — | — | grupos de links | muted-foreground | colunas → pilha | `<footer>`, landmarks | — | links mortos (`#`) | handoff §6.0 | ADAPTAR (remover `#` e "Xwitter") |
| CMP-003 | Container | classe `container` | largura de página | — | — | — | max-w-7xl, px-4/6/8 | fluido | — | um só container | containers ad hoc | handoff §3.3 | EXISTE |
| CMP-004 | Section | patterns/section.astro | SECTION H0 com eyebrow, header e conteúdo | `tone: page \| subtle` | — | `id`, `labelledBy`, `eyebrow`, `title`, `lead` | surface-page, surface-subtle | padding por breakpoint | `<section aria-labelledby>` | uma ideia por seção | alternar fundo por decoração (MDX §8) | CARD-HIERARCHY H0–H3; handoff `SectionPanel` | NOVO |
| CMP-005 | Divider | ui/separator.tsx | transição forte | horizontal | — | — | line-subtle 1px | — | `role="separator"` ou decorativo | uso excepcional | linha dupla ou preta pesada | EDITORIAL-LAYOUT divider_system | RESTYLE |
| **TIPOGRAFIA** |||||||||||||||
| CMP-010 | Eyebrow | patterns/eyebrow.tsx | contexto antes do título | `dark-gray`, `indigo`, `plain` | — | `children`, `variant` | #545454 ou #0E025D com branco bold | — | texto real, não imagem | curto, 1–3 palavras | substituir o título | BRAND usage_rules.eyebrow | NOVO |
| CMP-011 | Heading / Lead / Caption | estilos em `global.css` por superfície | hierarquia | display (Home), h1 (artigo, centralizado), h2, h3 | — | — | escalas da TOKEN-MAP §4 | clamp | um `h1` por rota; sem saltar níveis | heading descritivo, 3–8 palavras | heading decorativo | MDX §4 | ADAPTAR (CSS) |
| **AÇÕES** |||||||||||||||
| CMP-020 | Button | ui/button.tsx | ação | default (azul), outline, ghost, link | hover, focus, disabled, loading | `variant`, `size`, `asChild` | primary/primary-foreground, ring | largura total no mobile quando for CTA | ≥44px, foco 2px | um primário por região | dois primários lado a lado | BRAND button.primary | RESTYLE |
| CMP-021 | Link | `a` em `.prose` | navegação inline | — | visited, hover, focus | — | action-blue, sublinhado | — | sublinhado (cor não é o único canal) | texto descritivo | "clique aqui" | EDITORIAL-LAYOUT contrast_policy | ADAPTAR (CSS) |
| CMP-022 | CTA band | patterns/cta.astro | próxima ação no fim da página | — | — | `title`, `primary`, `secondary?` | surface-subtle | pilha no mobile | — | 1 ação principal | três CTAs | prompt §17 | NOVO |
| **CARDS** (profundidade máxima 2) |||||||||||||||
| CMP-030 | FeatureCard | patterns/feature-card.tsx sobre ui/card | tema ou função (H4) | `span: 1 \| 2` | hover (só se for link) | `icon`, `title`, `description`, `visual?`, `micro?` | superfície neutra (#ECECEC), sem borda forte | 2 col → 1 col; preserva a hierarquia interna | um único link com `::after` estendido | ícone → título → descrição → respiro → visual → micro | card inteiro em cor semântica; card dentro de card | CARD-HIERARCHY | NOVO |
| CMP-031 | MicroCard | patterns/micro-card.tsx | métrica, status ou evidência (H5) | `metric`, `status` | — | `label`, `value`, `tone?: risk \| solution \| brand` | card #FFF, shadow-sm, valor preto/semântico | compacto | cor sempre junto com texto | label + valor, no máximo 2 grupos | parágrafos, botões, tabela | CARD-HIERARCHY micro_card | NOVO |
| CMP-032 | Badge | ui/badge.tsx | classificação rápida (H6) | default, outline, semantic | — | — | rounded-sm, text-xs | — | texto, não só cor | 1–2 palavras | frase | CARD-HIERARCHY | RESTYLE |
| CMP-033 | ArticleCard | patterns/article-card.tsx sobre ui/card | entrada para artigo | `featured`, `vertical` | hover, focus | `title`, `description`, `href`, `date`, `category?`, `image?` | card, foreground, muted-foreground | featured: horizontal → vertical no mobile | título é o único link; data com `Intl` | — | imagem quebrada quando falta `image` (usar a variante sem imagem) | handoff §5.4 (variantes reduzidas) | NOVO (substitui o card de blocks/blog-posts.tsx) |
| CMP-034 | ToolCard / MapCard | = FeatureCard com `href` | entrada para ferramenta ou mapa | — | vazio (EmptyState) | iguais ao FeatureCard | — | — | — | reaproveitar o FeatureCard | criar componente próprio | prompt §15; reuso | REUSO (sem arquivo novo) |
| CMP-035 | RiskCard | = MicroCard `tone="risk"` | sinal de risco | — | — | — | risk + texto preto | — | texto "Risco" explícito | — | card vermelho cheio | CARD-HIERARCHY semantic | REUSO |
| **EDITORIAL** (componentes MDX autorizados, MDX §13) |||||||||||||||
| CMP-040 | KeyPoints | patterns/mdx/key-points.astro | resumo obrigatório acima de 300 palavras (3–5 itens) | — | — | `children` (lista) | surface-subtle | — | `<aside aria-label="Pontos-chave">` + `<ul>` | logo após o lead | segundo artigo dentro do resumo | MDX §5 | NOVO |
| CMP-041 | Callout | patterns/mdx/callout.astro | destaque funcional, no máximo 1 por H2 | `key`, `definition`, `note`, `risk`, `solution` (`attention` bloqueado: GAP-005) | — | `variant`, `title?` (≤5 palavras) | soft blue / #545454 / #0E025D; risk e solution só como faixa com texto preto | largura da coluna | `<aside>` com título; cor não é o único sinal | prosa → callout → prosa | callout seguido de callout; callout dentro de callout | MDX §7, §8 | NOVO |
| CMP-042 | Definition | patterns/mdx/definition.astro | definir termo | — | — | `term`, `children` | soft blue | — | `<dl>` | curto | parágrafos longos | MDX §13 | NOVO |
| CMP-043 | Quote | blockquote em `.prose` | só citação externa | — | — | `cite` obrigatório | border-left line | — | `<figure><blockquote><figcaption>` | atribuição + fonte | usar como callout (CONF-006) | MDX §11 | ADAPTAR (CSS) |
| CMP-044 | DataTable | patterns/mdx/data-table.astro sobre ui/table | comparação tabular (bloco pesado) | — | — | `caption` (obrigatória), `source?`, colunas/linhas | sem bordas verticais; linhas horizontais | rolagem horizontal local | `<caption>`, `<th scope>` | ≤6 colunas, ≤15 linhas | tabela para layout | EDITORIAL-LAYOUT editorial_table; MDX §9 | NOVO |
| **VISUAL** (blocos pesados) |||||||||||||||
| CMP-050 | Figure | patterns/mdx/figure.astro | imagem com função editorial | `cutout`, `line-art`, `scene` (exceção) | — | `src`, `alt` (obrigatório), `caption`, `source?` | canvas da marca ao redor | largura da coluna | alt + figcaption | elemento isolado + espaço negativo | foto full-bleed como fundo | IMAGE-USAGE (11-images); MDX §10 | NOVO |
| CMP-051 | VectorFigure | patterns/mdx/vector-figure.astro | figura SVG mono-first | — | — | `title`, `desc`, slot SVG | figure-* tokens | escala no viewBox | `<svg role="img">` + `<title>` / `<desc>` | cor só com significado | rainbow; uma cor por elemento | VECTOR-FIGURE-CONTRACT | NOVO |
| CMP-052 | Diagram | patterns/mdx/diagram.astro | diagrama em texto pré-formatado (o `AsciiDiagram` da auditoria) | — | — | `caption`, `alt` | mono, surface-subtle | rolagem horizontal local | `<figure>`, `role="img"` + `aria-label` no `<pre>` | caption que explica | diagrama sem texto vizinho | auditoria YAML; GAP-013 | NOVO |
| CMP-053 | Infographic | — | síntese isométrica | — | — | — | rampa de solução | — | — | — | — | INFOGRAPHIC-ISOMETRIC | ADIADO (GAP-014; nenhum conteúdo pede) |
| **NAVEGAÇÃO** |||||||||||||||
| CMP-060 | Breadcrumb | ui/breadcrumb.tsx | onde estou (artigo, mapas, ferramentas) | — | — | itens | muted-foreground | trunca no meio | `<nav aria-label="Trilha">` | — | — | prompt §17 | RESTYLE |
| CMP-061 | Pagination | ui/pagination.tsx | blog com mais de N posts | — | disabled | — | — | — | `aria-current` | — | — | handoff §6.1 | ADIADO (1 post real) |
| CMP-062 | RelatedContent | patterns/related.astro | próximo artigo, ferramenta relacionada | — | vazio → oculto | `items: ArticleCard[]` | — | 3 → 1 col | `<nav aria-label>` | ≤3 itens | — | MDX gramática (RelatedContent?) | NOVO |
| CMP-063 | EmptyState | ui/empty.tsx | rota sem conteúdo (/mapas, /ferramentas, blog vazio) | — | — | `title`, `description`, `action` | muted | — | texto, não só ícone | dizer o que vem e oferecer saída | página em branco | handoff §9.2 | REUSO |
| CMP-064 | PageHeader | patterns/page-header.astro | h1 + lead das rotas internas | `center` (artigo), `left` | — | `eyebrow?`, `title`, `lead?`, `breadcrumb?` | — | — | `h1` único | — | — | EDITORIAL-LAYOUT hero; handoff §6 | NOVO |
| **BLOCKS DO TEMPLATE** |||||||||||||||
| CMP-070 | Hero | blocks/hero.tsx | PROBLEMA na Home | — | — | — | — | — | único `h1` | — | imagem de template como identidade | — | ADAPTAR |
| CMP-071 | Features | blocks/features.tsx | SISTEMA ou MAPA na Home | — | — | — | — | — | — | — | — | — | ADAPTAR → FeatureCard |
| CMP-072 | ResourceAllocation | blocks/resource-allocation.tsx | CONCEITO na Home | — | — | — | — | — | — | — | — | — | ADAPTAR |
| CMP-073 | FAQ | blocks/faq.tsx | dúvidas | — | — | — | — | — | — | — | — | — | RESTYLE |
| CMP-074 | Logos, Testimonials, Pricing, PricingTable, Investors | blocks/* | prova social, preços | — | — | — | — | — | — | — | conteúdo fictício | GAP-019 | FORA da Home até haver conteúdo real |
| CMP-075 | Listing*, Task*, AmenityStrip, StatsBlock, ServiceCards | — | imobiliária e tarefas | — | — | — | — | — | — | — | — | CONF-008 | FORA |
