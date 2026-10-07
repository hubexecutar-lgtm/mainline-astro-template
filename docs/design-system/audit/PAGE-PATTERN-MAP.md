# PAGE-PATTERN-MAP

Cada padrão tem uma superfície (`data-surface` no `<body>`), o que limita regras como "H1 centralizado" à superfície certa (EDITORIAL-LAYOUT). Os componentes citados são os do `COMPONENT-INVENTORY.md`.

Todo padrão segue o layout comum do developer handoff §6.0: skip link → Navbar → `<main id="main">` → Footer, com um único `h1`.

## PAT-HOME — Home (`surface="home"`)

Narrativa obrigatória, definida no prompt de trabalho §14:

| # | Região | Pergunta que responde | Componentes | Fonte do conteúdo |
|---|---|---|---|---|
| 1 | PROBLEMA | Por que isto importa? | Hero (`h1`, lead, CTA primário "Ler o artigo fundador", CTA secundário "Ver mapas") | copy atual da Home + artigo fundador (BLK-RC-001/002) |
| 2 | CONCEITO | O que é risco cognitivo? | Section + Definition-like callout (soft blue) | BLK-RC-003, a definição de trabalho |
| 3 | SISTEMA | Como o risco se forma? | Section + grid de FeatureCards (2 col, span 2 no terceiro) com MicroCard | artigo, seções de mecanismo |
| 4 | MAPA | Como explorar? | FeatureCard `span=2` → `/mapas` | ESQUEMAS-EDITORIAIS ("mapas") |
| 5 | CONTEÚDO | O que ler? | Section + ArticleCard (`featured` para o fundador) + link "Todos os artigos" | coleção `blog` |
| 6 | FERRAMENTAS | O que fazer? | FeatureCard → `/ferramentas` | ESQUEMAS-EDITORIAIS ("4. O QUE FAZER") |
| 7 | PRÓXIMA AÇÃO | E agora? | CTA band + FAQ | FAQ atual |

- **Espaçamento:** `--space-16` a `--space-24` entre seções. A troca de fundo só acontece com mudança de função (MDX §8).
- **Responsivo:** grids de 2 colunas viram 1, com a ordem do DOM igual à ordem de leitura e os CTAs em largura total.

## PAT-BLOG-INDEX — Blog (`surface="blog-index"`)

PageHeader (eyebrow "Blog", `h1`, lead) → ArticleCard `featured` (o mais recente ou o marcado) → grid de ArticleCard `vertical` (1/2/3 colunas) → EmptyState se não houver posts → CTA band.

- Filtros e tópicos ficam fora: não estão documentados (prompt §18).
- A paginação fica adiada (CMP-061).

## PAT-ARTICLE — Artigo (`surface="article"`)

Gramática do MDX-CONTRACT §1:

```
Breadcrumb (Blog › título)
ArticleHeader: Eyebrow? · H1 centralizado (frontmatter) · Lead centralizado · data
Divider
KeyPoints / Callout summary   (obrigatório acima de 300 palavras)
Section H2 → P{1–4} → [1 SupportBlock] → P
...
References (reference-list)
RelatedContent (próximo artigo / ferramenta relacionada)
```

- **Coluna:** 68ch, alinhada à esquerda, sem justificar, corpo de 18px/1.6.
- **Orçamento por H2:** no máximo 1 bloco pesado e 1 leve, nunca pesado ao lado de pesado e nunca callout seguido de callout (MDX §13).
- **Mobile:** 1 coluna, e tabelas e diagramas rolam só dentro do próprio container.
- **TOC:** opcional, fora desta etapa (LEITURA-COGNITIVA).

## PAT-MAP — Mapas (`surface="page"`) · INFERENCE

PageHeader → EmptyState "Mapas em preparação", com explicação de uma frase e link para o artigo fundador → RelatedContent (artigos).

Quando houver mapas: grid de MapCards (FeatureCard) → página de detalhe.

## PAT-TOOL — Ferramentas (`surface="page"`) · INFERENCE

Mesma estrutura do PAT-MAP. Itens previstos pela série editorial: ferramentas, checklists, planejamento.

## PAT-ABOUT — Sobre (`surface="page"`)

PageHeader → prosa (máximo 68ch) → FeatureCards de valores → CTA band. O bloco Investors do template sai (GAP-019).

## PAT-UTILITY — FAQ, Contato, Privacidade, 404, Login/Signup (`surface="page"`)

PageHeader → conteúdo do bloco do template restilizado → CTA de saída.

- O 404 mostra `h1`, uma linha de texto e 3 links úteis (Home, Blog, Mapas).
- Login e Signup continuam como estão, com `noindex` (handoff §6.1).
