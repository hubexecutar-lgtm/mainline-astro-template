# DESIGN-SYSTEM-INDEX

Índice das regras com sua classe de origem. A navegação por pastas está em `../INDEX.md`.

| Classe | Significado |
|---|---|
| FACT_USER | valor definido na documentação |
| FACT_VISUAL | padrão observado numa referência visual citada por um contrato |
| REFERENCE_PUBLIC | WCAG, W3C COGA, BDA ou GOV.UK, conforme citado no kit |
| PROJECT_DECISION | decisão operacional deste projeto (inclui as decisões do usuário de 2026-10-07) |
| INFERENCE | dedução necessária, não documentada |
| GAP | ausente |
| NEEDS_CONFIRMATION | ambíguo |

## Sistema identificado

```
BRAND (01)            BRAND-COLOR-SYSTEM ............................ FACT_USER
  └── TOKENS (02)     TOKEN-MAP ...................................... FACT_USER + INFERENCE (mapeamento shadcn)
COGNITIVE READING     LEITURA-COGNITIVA + MDX-CONTRACT .............. REFERENCE_PUBLIC + PROJECT_RULE
  ├── TYPOGRAPHY (03) escalas por superfície ........................ estimativas dos handoffs (≈)
  ├── LAYOUT (04)     EDITORIAL-LAYOUT-SYSTEM ....................... FACT_VISUAL + PROJECT_DECISION
  └── READING (07)    Reading Flow Contract v1.0 .................... PROJECT_RULE
VISUAL LANGUAGE
  ├── CARDS (10)      CARD-HIERARCHY-SYSTEM ......................... FACT_VISUAL + PROJECT_DECISION
  ├── IMAGES (11)     IMAGE-ILLUSTRATION + IMAGE-USAGE .............. PROJECT_RULE + PROJECT_DECISION
  ├── FIGURES (12)    VECTOR-FIGURE-CONTRACT ........................ PROJECT_RULE
  └── INFOGR. (13)    INFOGRAPHIC-ISOMETRIC-SYSTEM .................. REFERENCE_PUBLIC (geometria) + PROJECT_RULE
EDITORIAL
  ├── BLOCKS (08)     BLOCKS-CONTRACT ............................... PROJECT_RULE
  └── MDX (14)        componentes autorizados ....................... PROJECT_RULE
SITE
  ├── COMPONENTS (09) COMPONENT-INVENTORY ........................... handoff (estrutura) + reuso do repo
  ├── PATTERNS (15)   PAGE-PATTERN-MAP .............................. PROJECT_DECISION
  └── ROUTES (16)     ROUTE-MATRIX .................................. existentes + INFERENCE (/mapas, /ferramentas)
```

## Regras-chave por classe

| ID | Regra | Classe | Fonte |
|---|---|---|---|
| R-001 | Canvas `#FFFDFA`; texto `#000`; secundário `#545454` | FACT_USER | BRAND |
| R-002 | Ação, link e botão em `#2D5CE6` com texto branco | FACT_USER | BRAND |
| R-003 | Verde = solução, vermelho = risco, amarelo = atenção (GAP) | FACT_USER | BRAND |
| R-004 | Texto preto sobre verde e vermelho | REFERENCE_PUBLIC (WCAG 1.4.3, medido) | MDX §8 |
| R-005 | Texto 4.5:1; texto grande e UI 3:1 | REFERENCE_PUBLIC | MDX §8 |
| R-006 | Cor nunca é o único canal de informação | REFERENCE_PUBLIC (WCAG 1.4.1) | EDITORIAL-LAYOUT |
| R-007 | Coluna de leitura de 68ch (60–72, máximo 80) | PROJECT_RULE | MDX §3 |
| R-008 | Corpo do artigo 18px / 1.6, à esquerda, sem justificar | PROJECT_DECISION ⊂ REFERENCE_PUBLIC (BDA) | LEITURA |
| R-009 | Reflow a 320px sem rolagem horizontal | REFERENCE_PUBLIC (WCAG 1.4.10) | MDX §3 |
| R-010 | Um `h1` (do frontmatter), centralizado no artigo; sem saltar níveis | PROJECT_RULE + REFERENCE_PUBLIC | MDX §4; EDITORIAL-LAYOUT |
| R-011 | Frase 8–20 palavras; parágrafo 20–60; 1–4 parágrafos por H2 | PROJECT_RULE | MDX §2 |
| R-012 | Resumo ou KeyPoints obrigatório acima de 300 palavras | REFERENCE_PUBLIC (COGA) → PROJECT_RULE | MDX §5 |
| R-013 | Por H2: até 1 bloco pesado e 1 leve; sem pesado ao lado de pesado; sem callout seguido de callout | PROJECT_RULE | MDX §13; BLOCKS |
| R-014 | Blockquote só para citação externa com fonte | PROJECT_RULE | MDX §11 |
| R-015 | Tabelas sem bordas verticais, com caption e `th` | FACT_VISUAL + REFERENCE_PUBLIC | EDITORIAL-LAYOUT; MDX §9 |
| R-016 | Cards com profundidade máxima de 2; micro card = label + valor | PROJECT_DECISION | CARD-HIERARCHY |
| R-017 | Card principal neutro; cor semântica só no micro card | PROJECT_DECISION | CARD-HIERARCHY |
| R-018 | Figuras 80–95% neutras; cor só com significado | PROJECT_RULE | VECTOR |
| R-019 | Isometria 30/90/150, sem ponto de fuga | REFERENCE_PUBLIC (Autodesk) | INFOGRAPHIC |
| R-020 | Imagem = elemento isolado sobre o canvas; sem foto full-bleed por padrão | PROJECT_DECISION | prompt; IMAGE-ILLUSTRATION |
| R-021 | MDX só com os componentes autorizados | PROJECT_RULE | MDX §13 |
| R-022 | Troca de fundo só com mudança de função; no máximo 1 superfície colorida por H2 | PROJECT_RULE | MDX §8 |
| R-023 | Navegação e regiões consistentes entre rotas | REFERENCE_PUBLIC (COGA) | LEITURA |
| R-024 | Tema escuro derivado e verificado | INFERENCE | CONF-011 |
| R-025 | Fonte DM Sans + Inter | PROJECT_DECISION (default) | GAP-007 |
| R-026 | Efeito de headline "round 0 / spread 100 / 19%" | NEEDS_CONFIRMATION | GAP-006 |
