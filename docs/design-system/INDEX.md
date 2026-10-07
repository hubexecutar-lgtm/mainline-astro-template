# INDEX

```
docs/design-system/
├── README.md                  ponto de entrada
├── INDEX.md                   este arquivo
├── 01-brand/                  BRAND-COLOR-SYSTEM · OBRAND (referência externa)
├── 02-tokens/                 fonte única de valores → src/styles/global.css
├── 03-typography/             escalas da Home e do artigo
├── 04-layout/                 EDITORIAL-LAYOUT-SYSTEM
├── 05-responsive/             mobile-first, reflow a 320px
├── 06-accessibility/          WCAG 2.2 AA · W3C COGA · BDA
├── 07-reading-flow/           Reading Flow Contract v1.0 (MDX-CONTRACT)
├── 08-editorial/              BLOCKS-CONTRACT · série editorial
├── 09-components/             inventário · storyboard
├── 10-cards/                  CARD-HIERARCHY-SYSTEM
├── 11-images/                 IMAGE-USAGE-CONTRACT · IMAGE-ILLUSTRATION-SYSTEM
├── 12-vector-figures/         VECTOR-FIGURE-CONTRACT
├── 13-infographics/           INFOGRAPHIC-ISOMETRIC-SYSTEM
├── 14-mdx/                    componentes MDX autorizados
├── 15-page-patterns/          PAT-HOME · BLOG-INDEX · ARTICLE · MAP · TOOL · ABOUT · UTILITY
├── 16-routes/                 matriz de rotas
├── audit/                     9 entregáveis
└── source/                    kit original (preservado)
    ├── 00-governanca/         DECISIONS.md · MAPPING.json
    ├── 01-referencias/        marca/ (OBRAND) · visuais/ (16 imagens)
    ├── 02-design-system/      fundamentos · layout · componentes · linguagem-visual
    ├── 03-editorial/          leitura · contratos · arquitetura
    ├── 04-handoff/            site · editorial · storyboard
    ├── 05-exemplos/           mdx-exemplo.md
    ├── 06-operacao/           tutorial.md
    ├── 07-validacao/          verification.json · auditorias/
    ├── MASTER-INDEX.csv
    └── README.md
```

## Contratos visuais e onde estão

| Contrato | Arquivo de origem | Área |
|---|---|---|
| BRAND-COLOR-SYSTEM v0.1 | `source/02-design-system/fundamentos/brand-color-system.md` | 01, 02 |
| EDITORIAL-LAYOUT-SYSTEM v0.1 | `source/02-design-system/layout/editorial-layout-system.md` | 04 |
| CARD-HIERARCHY-SYSTEM v0.1 | `source/02-design-system/componentes/card-hierarchy-system.md` | 10 |
| IMAGE-ILLUSTRATION-SYSTEM v0.1 | `source/02-design-system/linguagem-visual/image-illustration-system.md` | 11 |
| IMAGE-USAGE-CONTRACT | sem arquivo de origem; formalizado em `11-images/README.md` (GAP-016) | 11 |
| VECTOR-FIGURE-CONTRACT v1.0 | `source/02-design-system/linguagem-visual/vector-figure-contract.md` | 12 |
| INFOGRAPHIC-ISOMETRIC-SYSTEM v0.1 | `source/02-design-system/linguagem-visual/infographic-isometric-system.md` | 13 |
| READING-FLOW-CONTRACT v1.0 | `source/03-editorial/contratos/mdx-contract.md` | 07, 14 |
| BLOCKS-CONTRACT | `source/03-editorial/contratos/blocks-contract.md` | 08 |
| COGNITIVE READING | `source/03-editorial/leitura/leitura-cognitiva.md` | 06, 07 |
