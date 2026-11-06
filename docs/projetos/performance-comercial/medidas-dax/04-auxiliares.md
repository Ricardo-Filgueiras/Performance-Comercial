<!-- pasta: 04. Auxiliares -->
# 04. Auxiliares

<!-- gerado:inicio resumo -->
Medidas da pasta de exibição `04. Auxiliares`: **4**. Veja o [catálogo](index.md) para as outras pastas.
<!-- gerado:fim resumo -->

## 52 Rank Cidade

Posição da cidade no ranking de faturamento, entre todas as cidades de `dClientes`. *(descrição deduzida do código)*

<!-- gerado:inicio medida:52 Rank Cidade -->
- **Tabela:** `_Medidas`
- **Formato:** `0`
- **Usada nas guias:** [Comercial ](../guias-do-relatorio/comercial.md), *Comercial antes*
- **Depende de:** [`01 Faturamento`](01-principais.md#01-faturamento)
- **É usada por:** nenhuma medida

```dax
RANKX(
    ALL( dClientes[Cidade] ) , [01 Faturamento] 
)
```
<!-- gerado:fim medida:52 Rank Cidade -->

## 53 Max Y Visual 01 pg Vendedores

Maior faturamento diário no contexto selecionado, multiplicado por 1,5. Pelo nome, define o limite do eixo Y do visual 01 da guia Vendedores. *(descrição deduzida do código)*

<!-- gerado:inicio medida:53 Max Y Visual 01 pg Vendedores -->
- **Tabela:** `_Medidas`
- **Formato:** padrão
- **Usada nas guias:** [Vendedores](../guias-do-relatorio/vendedores.md), *Vendedores antes*
- **Depende de:** [`01 Faturamento`](01-principais.md#01-faturamento)
- **É usada por:** nenhuma medida

```dax
MAXX(
    ALLSELECTED(
        dCalendario[Dia]
    ), [01 Faturamento] * 1.5

)
```
<!-- gerado:fim medida:53 Max Y Visual 01 pg Vendedores -->

## 54 Nome Vendedor

Nome do vendedor selecionado no filtro (vazio se houver mais de um). *(descrição deduzida do código)*

<!-- gerado:inicio medida:54 Nome Vendedor -->
- **Tabela:** `_Medidas`
- **Formato:** padrão
- **Usada nas guias:** *TooltipRosca*
- **Depende de:** nenhuma medida
- **É usada por:** nenhuma medida

```dax
SELECTEDVALUE( dVendedores[Vendedor] )
```
<!-- gerado:fim medida:54 Nome Vendedor -->

## 55 Periodo Analisado

Texto com o primeiro e o último mês com vendas no filtro atual, mais o aviso de dados fictícios. Ex.: jan/2021 a abr/2021 · dados fictícios.

<!-- gerado:inicio medida:55 Periodo Analisado -->
- **Tabela:** `_Medidas`
- **Formato:** padrão
- **Usada nas guias:** nenhum visual
- **Depende de:** nenhuma medida
- **É usada por:** [`67 HTML Cartoes KPI`](visuais-svg.md#67-html-cartoes-kpi)

```dax
VAR _ini = CALCULATE( MIN( dCalendario[Id Data] ), dCalendario[Datas com Venda] = TRUE() )
VAR _fim = CALCULATE( MAX( dCalendario[Id Data] ), dCalendario[Datas com Venda] = TRUE() )
RETURN
    IF(
        ISBLANK( _ini ),
        "Sem vendas no período · dados fictícios",
        FORMAT( _ini, "mmm/yyyy" ) & " a " & FORMAT( _fim, "mmm/yyyy" ) & " · dados fictícios"
    )
```
<!-- gerado:fim medida:55 Periodo Analisado -->
