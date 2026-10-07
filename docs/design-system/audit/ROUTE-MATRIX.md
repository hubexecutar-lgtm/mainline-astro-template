# ROUTE-MATRIX

Rotas atuais vêm de `src/pages/*`. As rotas novas estão marcadas com a origem. Nenhuma rota existente muda de URL.

| Rota | Arquivo | Tipo de página | Propósito | Entradas | Saídas | CTA primário | CTA secundário | Componentes | Fonte do conteúdo | Mobile | Vazio | Carregando | Erro | Origem |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| `/` | pages/index.astro | PAT-HOME | apresentar problema → ação | busca, links externos, logo | /blog/risco-cognitivo, /mapas, /ferramentas, /blog | Ler o artigo fundador | Ver mapas | Hero, Section, FeatureCard, MicroCard, ArticleCard, CTA, FAQ | página + coleção blog | pilha, CTAs em largura total | seção CONTEÚDO some se não houver posts | n/a (estático) | n/a | existente |
| `/blog` | pages/blog/index.astro | PAT-BLOG-INDEX | listar artigos | Navbar, Home | /blog/[slug] | abrir artigo | — | PageHeader, ArticleCard, EmptyState | coleção blog (sem `draft`) | 1 coluna | EmptyState "Nenhum artigo publicado" | n/a | n/a | existente |
| `/blog/[slug]` | pages/blog/[...slug].astro | PAT-ARTICLE | ler | /blog, Home, RSS | artigo relacionado, ferramenta, /blog | próximo artigo | ferramenta relacionada | Breadcrumb, ArticleHeader, KeyPoints, Callout, Diagram, DataTable, Figure, RelatedContent | MDX | 1 coluna de 68ch, rolagem local em diagramas | n/a | n/a | slug inexistente → 404 | existente |
| `/mapas` | pages/mapas.astro (novo) | PAT-MAP | explorar mapas | Navbar, Home (MAPA) | artigo fundador, /blog | Ler o artigo fundador | Ver ferramentas | PageHeader, EmptyState, RelatedContent | GAP-011 | pilha | EmptyState (estado atual) | n/a | n/a | INFERENCE: ESQUEMAS-EDITORIAIS "4. O QUE FAZER → mapas"; pedido do usuário |
| `/ferramentas` | pages/ferramentas.astro (novo) | PAT-TOOL | aplicar | Navbar, Home (FERRAMENTAS), artigo | artigo fundador, /mapas | Ler o artigo fundador | Ver mapas | PageHeader, EmptyState, RelatedContent | GAP-012 | pilha | EmptyState (estado atual) | n/a | n/a | INFERENCE: ESQUEMAS-EDITORIAIS "ferramentas, checklists, planejamento"; pedido do usuário |
| `/about` | pages/about.astro | PAT-ABOUT | proposta do projeto | Navbar ("Proposta"), Footer | /blog, /contact | Ler o artigo fundador | Contato | PageHeader, FeatureCard, CTA | página | pilha | n/a | n/a | n/a | existente (o handoff sugere `/sobre`; a URL é mantida para não quebrar links, CONF registrado) |
| `/faq` | pages/faq.astro | PAT-UTILITY | dúvidas | Navbar, Home | /contact | Contato | — | PageHeader, FAQ | bloco faq | — | n/a | n/a | n/a | existente |
| `/contact` | pages/contact.astro | PAT-UTILITY | contato | Navbar, FAQ | — | enviar | — | Contact (UI) | bloco contact | pilha | n/a | n/a | sem backend (GAP-018): formulário sem envio real | existente |
| `/pricing` | pages/pricing.astro | PAT-UTILITY | "Começar" | Navbar | /signup | — | — | Pricing, PricingTable | conteúdo do template | — | — | — | — | existente; **conteúdo fictício (GAP-019)**: sai da Navbar até haver oferta real, e a rota é mantida |
| `/privacy` | pages/privacy.mdx | PAT-UTILITY | dados pessoais | Footer | — | — | — | prose | MDX | — | — | — | — | existente |
| `/login`, `/signup` | pages/login.astro, signup.astro | PAT-UTILITY | conta | Navbar | — | entrar | criar conta | blocks | — | — | — | — | — | existente; `noindex` |
| `/404` | pages/404.astro | PAT-UTILITY | erro | qualquer | /, /blog, /mapas | Home | Blog | PageHeader, links | — | — | — | — | — | existente |
| `/rss.xml` | pages/rss.xml.js | feed | — | autodiscovery | — | — | — | — | coleção blog | — | — | — | — | existente |
| `/listings*`, `/app/tasks` | — | — | — | — | — | — | — | — | — | — | — | — | — | FORA (CONF-008) |

## Fluxos validados (prompt §17)

| Fluxo | Caminho | Elo que garante |
|---|---|---|
| HOME → BLOG → ARTIGO → RELACIONADO | `/` CONTEÚDO → `/blog` → `/blog/[slug]` → RelatedContent | ArticleCard + RelatedContent |
| HOME → MAPAS → DETALHE | `/` MAPA → `/mapas` → (detalhe: GAP-011) | FeatureCard `href` + EmptyState com saída |
| HOME → FERRAMENTA → EXECUÇÃO | `/` FERRAMENTAS → `/ferramentas` → (execução: GAP-012) | idem |
| ARTIGO → FERRAMENTA | `/blog/[slug]` → `/ferramentas` | CTA secundário do RelatedContent |
| ARTIGO → PRÓXIMO | `/blog/[slug]` → próximo por data | RelatedContent |

Cada página responde a três perguntas:

- **Onde estou?** Breadcrumb ou eyebrow, mais o `h1`.
- **O que posso fazer aqui?** O lead.
- **Qual é a próxima ação?** O CTA primário ou o RelatedContent.
