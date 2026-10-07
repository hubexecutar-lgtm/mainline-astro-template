# Risco Cognitivo — Design Kit

Pacote documental organizado para consulta, design e handoff de implementação.

- ID do pacote: RC-DESIGN-KIT-001 (atribuído nesta organização).
- VERSION: 1.0.0
- AREA: Design / Editorial / Handoff
- WORKFLOW: Inventariar → classificar → preservar → indexar → verificar
- OWNER: A DEFINIR
- STATUS: VERIFIED para organização e integridade; aprovação de design A DEFINIR.
- INPUT: Archive(6).zip, 33 arquivos úteis.
- OUTPUT: diretório com 33 originais e 5 arquivos de governança/validação.
- DEPENDS_ON: arquivo de origem recebido.
- BLOCKS: organização não bloqueada; pendências afetam aplicação e validação editorial.
- AUTOMATION_LEVEL: A4 para organização, comparação de bytes e inventário.
- EVIDENCE: [Verificação](07-validacao/verification.json).
- HANDOFF: resolver [pendências](00-governanca/DECISIONS.md) antes de consolidar tokens ou implementar regras conflitantes.

## Comece aqui

1. Consulte o [índice completo](MASTER-INDEX.csv) para localizar cada arquivo.
2. Leia as [regras e pendências](00-governanca/DECISIONS.md).
3. Consulte fundamentos, layout e componentes em `02-design-system/`.
4. Leia os contratos e orientações em `03-editorial/`.
5. Use `04-handoff/` e `06-operacao/` para preparar a implementação.
6. Consulte referências e exemplos conforme necessário; eles não são aprovação de regras.

## Diretórios

| Pasta | Conteúdo |
|---|---|
| 00-governanca | Decisões, limites e mapeamento origem/destino |
| 01-referencias/marca | Referência externa OpenAI |
| 01-referencias/visuais | 16 imagens preservadas; sem classificação visual inferida |
| 02-design-system/fundamentos | Sistema de cores |
| 02-design-system/layout | Composição editorial |
| 02-design-system/componentes | Hierarquia de cards |
| 02-design-system/linguagem-visual | Figuras, isometria e ilustração |
| 03-editorial/leitura | Leitura cognitiva |
| 03-editorial/contratos | Blocos e MDX |
| 03-editorial/arquitetura | Organização da série editorial |
| 04-handoff/site | Especificação do site Astro |
| 04-handoff/editorial | Tokens aplicados a blog e ebooks |
| 04-handoff/storyboard | HTML de componentes e usos |
| 05-exemplos | Exemplo editorial original |
| 06-operacao | Tutorial de aplicação |
| 07-validacao | Verificação do pacote e auditoria histórica |

## Preservação e limites

O conteúdo dos 33 arquivos foi preservado byte a byte. Somente caminhos e nomes externos foram organizados. IDs, títulos, tabelas, instruções e referências dentro dos arquivos permanecem intactos. Os IDs RC-KIT-FILE são identificadores novos do inventário, não substituem IDs existentes. Campos não determinados estão marcados A DEFINIR.

Não houve consolidação de tokens, revisão técnica das normas citadas, aprovação de design ou implementação do site. Metadados de transporte `__MACOSX` não integram o conteúdo útil do pacote. Consulte o mapeamento para nomes originais e os hashes para integridade.

## Arquivos

- [MOBILE_REF_UI.JPG](01-referencias/visuais/ref-001-mobile-ref-ui.jpg)
- [INK_REF_.PNG](01-referencias/visuais/ref-002-ink-ref-.png)
- [STORE_CARDS_REF.PNG](01-referencias/visuais/ref-003-store-cards-ref.png)
- [VETORIAL_REF.JPG.PNG](01-referencias/visuais/ref-004-vetorial-ref.jpg.png)
- [UI-COMPONETS.JPG](01-referencias/visuais/ref-005-ui-componets.jpg)
- [VETORI_REF.JPG](01-referencias/visuais/ref-006-vetori-ref.jpg)
- [FIGURES_REF.JPG](01-referencias/visuais/ref-007-figures-ref.jpg)
- [FLOW_CHART_REF.JPG](01-referencias/visuais/ref-008-flow-chart-ref.jpg)
- [VETORIAL_REF_.PNG](01-referencias/visuais/ref-009-vetorial-ref-.png)
- [COMPONETS_REF.PNG](01-referencias/visuais/ref-010-componets-ref.png)
- [VETORIAL_REF.PNG](01-referencias/visuais/ref-011-vetorial-ref.png)
- [VETORIAL_REF.JPG](01-referencias/visuais/ref-012-vetorial-ref.jpg)
- [GRAFICO_REF_.PNG](01-referencias/visuais/ref-013-grafico-ref-.png)
- [COMPONETS_UI_REF.JPG](01-referencias/visuais/ref-014-componets-ui-ref.jpg)
- [CARDS_REF.PNG](01-referencias/visuais/ref-015-cards-ref.png)
- [COMPONETS_REFF.JPG](01-referencias/visuais/ref-016-componets-reff.jpg)
- [Developer Handoff Spec ΓÇö Branded Mainline Astro Site.md](04-handoff/site/developer-handoff-mainline-astro.md)
- [Storyboard de componentes e handoff de uso.html](04-handoff/storyboard/storyboard-componentes.html)
- [Handoff editorial tokens para artigos de blog e ebooks.md](04-handoff/editorial/handoff-tokens-blog-ebooks.md)
- [TUTOTIAL.md](06-operacao/tutorial.md)
- [OBRAND-STYLING-001.md](01-referencias/marca/obrand-styling-001.md)
- [VECTOR-FIGURE-CONTRACT v1.0.md](02-design-system/linguagem-visual/vector-figure-contract.md)
- [MDX_CONTRACT.md](03-editorial/contratos/mdx-contract.md)
- [CARD-HIERARCHY-SYSTEM v0.1,.md](02-design-system/componentes/card-hierarchy-system.md)
- [INFOGRAPHIC-ISOMETRIC-SYSTEM v0.1..md](02-design-system/linguagem-visual/infographic-isometric-system.md)
- [EDITORIAL-LAYOUT-SYSTEM v0.1, complementar ao BRAND-COLOR-SYSTEM v0.1..md](02-design-system/layout/editorial-layout-system.md)
- [LEITURA CONGTIVA.md](03-editorial/leitura/leitura-cognitiva.md)
- [IMAGE-ILLUSTRATION-SYSTEM v0.1 ΓÇö Architectural Technical Line Art.md](02-design-system/linguagem-visual/image-illustration-system.md)
- [BLOCKS-CONTRAT.md](03-editorial/contratos/blocks-contract.md)
- [BRAND-COLOR-SYSTEM.md](02-design-system/fundamentos/brand-color-system.md)
- [ESQUERMAS PLAIN TXT.md](03-editorial/arquitetura/esquemas-editoriais.md)
- [MDX EXEMPLO.md](05-exemplos/mdx-exemplo.md)
- [risco-cognitivo-reading-flow-v1.audit.yaml](07-validacao/auditorias/risco-cognitivo-reading-flow-v1.audit.yaml)
