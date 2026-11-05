<!-- pasta: 04. Auxiliares -->
# 04. Auxiliares

<!-- gerado:inicio resumo -->
Medidas da pasta de exibição `04. Auxiliares`: **3**. Veja o [catálogo](index.md) para as outras pastas.
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
