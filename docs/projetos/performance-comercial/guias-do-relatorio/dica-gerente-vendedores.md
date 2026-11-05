# Dica de ferramenta: gerente e vendedores

## Para que serve

Dica de ferramenta da rosca de faturamento por gerente da guia [Comercial](comercial.md): detalha os vendedores do gerente sob o mouse (*deduzido dos visuais*).

## Como ler

- Um cartão com o nome do gerente e um gráfico de colunas e linhas por vendedor. As linhas "atual" e "anterior" e as setas vêm das medidas da tabela `zMetricas`, que comparam o faturamento atual com o do ano anterior.

## Navegação

Dica de ferramenta: não tem navegação. Aparece quando o mouse passa sobre um visual da guia [Comercial](comercial.md).

??? info "Detalhes técnicos"

    | Propriedade | Valor |
    |---|---|
    | Nome de exibição | TooltipRosca |
    | Ordem no relatório | 11 de 12 |
    | Oculta | sim (`HiddenInViewMode`) |
    | Tipo | dica de ferramenta |
    | Tamanho | 320 × 240 |
    | Identificador | `9b097549a60ba5037c9f` |
    | Visuais | 2 (mais 0 grupos) |

    **Tipos de visual:** `card` (1), `lineClusteredColumnComboChart` (1).

    **Medidas usadas:** [`54 Nome Vendedor`](../medidas-dax/04-auxiliares.md#54-nome-vendedor), [`Context Medida z`](../medidas-dax/tooltip-rosca.md#context-medida-z), [`Linha Anterior`](../medidas-dax/tooltip-rosca.md#linha-anterior), [`Linha Atual`](../medidas-dax/tooltip-rosca.md#linha-atual), [`Seta para Cima`](../medidas-dax/tooltip-rosca.md#seta-para-cima), [`Seta para baixo  ( limit Inferior )`](../medidas-dax/tooltip-rosca.md#seta-para-baixo-limit-inferior), [`Seta para baixo  ( limit sup )`](../medidas-dax/tooltip-rosca.md#seta-para-baixo-limit-sup).

    **Colunas usadas:**

    | Tabela | Colunas |
    |---|---|
    | `dVendedores` | `Gerente`, `Vendedor` |
    | `zMetricas` | `Metrica` |

    **Regras específicas da guia:** nenhuma além das [regras gerais](../regras-de-negocio.md)..
