<!-- pasta: Tooltip Rosca -->
# Tooltip Rosca

<!-- gerado:inicio resumo -->
Medidas da pasta de exibição `Tooltip Rosca`: **6**. Veja o [catálogo](index.md) para as outras pastas.
<!-- gerado:fim resumo -->

## Context Medida z

Devolve o faturamento atual ou o do ano anterior, conforme o valor de `zMetricas[Metrica]` ("Atual" ou "Anterior"). *(descrição deduzida do código)*

<!-- gerado:inicio medida:Context Medida z -->
- **Tabela:** `zMetricas`
- **Formato:** padrão
- **Usada nas guias:** *TooltipRosca*
- **Depende de:** [`01 Faturamento`](01-principais.md#01-faturamento), [`22 Faturamento LY`](02-temporais.md#22-faturamento-ly)
- **É usada por:** nenhuma medida

```dax
VAR _contexto = SELECTEDVALUE( zMetricas[Metrica] )

VAR _selecao = 
SWITCH(
    TRUE(),
    _contexto = "Atual", [01 Faturamento] ,
    _contexto = "Anterior", [22 Faturamento LY],
    BLANK()

)

RETURN
    _selecao
```
<!-- gerado:fim medida:Context Medida z -->

## Linha Anterior

Faturamento do mesmo período do ano anterior (repete `22 Faturamento LY`). *(descrição deduzida do código)*

<!-- gerado:inicio medida:Linha Anterior -->
- **Tabela:** `zMetricas`
- **Formato:** padrão
- **Usada nas guias:** *TooltipRosca*
- **Depende de:** [`22 Faturamento LY`](02-temporais.md#22-faturamento-ly)
- **É usada por:** nenhuma medida

```dax
[22 Faturamento LY]
```
<!-- gerado:fim medida:Linha Anterior -->

## Linha Atual

Faturamento atual, quando a métrica selecionada é "Atual" ou não há seleção. *(descrição deduzida do código)*

<!-- gerado:inicio medida:Linha Atual -->
- **Tabela:** `zMetricas`
- **Formato:** padrão
- **Usada nas guias:** *TooltipRosca*
- **Depende de:** [`01 Faturamento`](01-principais.md#01-faturamento)
- **É usada por:** nenhuma medida

```dax
VAR _selecao = SELECTEDVALUE( zMetricas[Metrica] )

RETURN
    IF(  _selecao in {"Atual", ""} , [01 Faturamento] )
```
<!-- gerado:fim medida:Linha Atual -->

## Seta para baixo  ( limit Inferior )

Faturamento atual, quando não há métrica selecionada e o atual é menor que o do ano anterior. *(descrição deduzida do código)*

<!-- gerado:inicio medida:Seta para baixo  ( limit Inferior ) -->
- **Tabela:** `zMetricas`
- **Formato:** padrão
- **Usada nas guias:** *TooltipRosca*
- **Depende de:** [`01 Faturamento`](01-principais.md#01-faturamento), [`22 Faturamento LY`](02-temporais.md#22-faturamento-ly)
- **É usada por:** nenhuma medida

```dax
VAR _context = SELECTEDVALUE( zMetricas[Metrica] )
VAR _atual = [01 Faturamento]
VAR _anterio = [22 Faturamento LY] 

RETURN
    IF(
        _context = ""
        && _atual < _anterio,
        _atual 
    )
```
<!-- gerado:fim medida:Seta para baixo  ( limit Inferior ) -->

## Seta para baixo  ( limit sup )

Faturamento do ano anterior, quando não há métrica selecionada e o atual é menor. *(descrição deduzida do código)*

<!-- gerado:inicio medida:Seta para baixo  ( limit sup ) -->
- **Tabela:** `zMetricas`
- **Formato:** `0`
- **Usada nas guias:** *TooltipRosca*
- **Depende de:** [`01 Faturamento`](01-principais.md#01-faturamento), [`22 Faturamento LY`](02-temporais.md#22-faturamento-ly)
- **É usada por:** nenhuma medida

```dax
VAR _context = SELECTEDVALUE( zMetricas[Metrica] )
VAR _atual = [01 Faturamento]
VAR _anterio = [22 Faturamento LY] 

RETURN
    IF(
        _context = ""
        && _atual < _anterio,
        _anterio 
    )
```
<!-- gerado:fim medida:Seta para baixo  ( limit sup ) -->

## Seta para Cima

Faturamento atual, quando não há métrica selecionada e o atual é maior ou igual ao do ano anterior. *(descrição deduzida do código)*

<!-- gerado:inicio medida:Seta para Cima -->
- **Tabela:** `zMetricas`
- **Formato:** padrão
- **Usada nas guias:** *TooltipRosca*
- **Depende de:** [`01 Faturamento`](01-principais.md#01-faturamento), [`22 Faturamento LY`](02-temporais.md#22-faturamento-ly)
- **É usada por:** nenhuma medida

```dax
VAR _context = SELECTEDVALUE( zMetricas[Metrica] )
VAR _atual = [01 Faturamento]
VAR _anterio = [22 Faturamento LY] 

RETURN
    IF(
        _context = ""
        && _atual >= _anterio,
        _atual 
    )
```
<!-- gerado:fim medida:Seta para Cima -->
