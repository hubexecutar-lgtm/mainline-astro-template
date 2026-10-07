# Design System — Risco Cognitivo

Esta pasta é a **fonte de verdade** de identidade, tokens, componentes, padrões de página e rotas do site. Ela substitui o ADR-001, a regra de personalização por contagem de caracteres, que foi removida.

## Como está organizada

| Pasta | Conteúdo |
|---|---|
| `source/` | Kit original `risco-cognitivo-design-kit-v1.0.0`, preservado byte a byte. Os 33 originais conferem com os `sha256` do `source/MASTER-INDEX.csv`. Não edite. |
| `01-brand/` … `16-routes/` | Camada normalizada: cada área aponta para as fontes em `source/` e lista as regras canônicas. Não duplica conteúdo. |
| `audit/` | Os 9 entregáveis da auditoria (ver abaixo). |

## Entregáveis da auditoria

1. [DOCUMENT-INVENTORY](audit/DOCUMENT-INVENTORY.csv)
2. [DESIGN-SYSTEM-INDEX](audit/DESIGN-SYSTEM-INDEX.md)
3. [TOKEN-MAP](audit/TOKEN-MAP.md)
4. [COMPONENT-INVENTORY](audit/COMPONENT-INVENTORY.md)
5. [PAGE-PATTERN-MAP](audit/PAGE-PATTERN-MAP.md)
6. [ROUTE-MATRIX](audit/ROUTE-MATRIX.md)
7. [GAP-REGISTER](audit/GAP-REGISTER.md)
8. [CONFLICT-REGISTER](audit/CONFLICT-REGISTER.md)
9. [IMPLEMENTATION-PLAN](audit/IMPLEMENTATION-PLAN.md)

## Regras de uso

- **Precedência:** fundamentos (cor) → contratos editoriais → sistemas visuais → handoffs → referências externas. Detalhe no CONFLICT-REGISTER.
- Um valor ausente é **GAP** e nunca é inventado. Quem resolve um GAP atualiza o GAP-REGISTER no mesmo PR.
- Toda mudança visual no site cita o ID de origem (token, CMP-xxx, PAT-xxx, CONF-xxx ou GAP-xxx).
- Navegação completa: [INDEX.md](INDEX.md).
