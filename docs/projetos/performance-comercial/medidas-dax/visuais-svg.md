<!-- pasta: .Visuais SVG -->
# .Visuais SVG

<!-- gerado:inicio resumo -->
Medidas da pasta de exibição `.Visuais SVG`: **8**. Veja o [catálogo](index.md) para as outras pastas.
<!-- gerado:fim resumo -->

## 60 SVG Cartao Faturamento v1

**Sem uso desde 06/11/2026.** O cartão da guia Comercial que mostrava esta imagem foi trocado pela faixa de KPIs em HTML, desenhada pela [`67 HTML Cartoes KPI`](#67-html-cartoes-kpi). A medida continua no modelo; a versão atual desenha duas linhas em 219 × 38, conforme a descrição do modelo abaixo.

<!-- gerado:inicio medida:60 SVG Cartao Faturamento v1 -->
- **Tabela:** `_Medidas`
- **Formato:** padrão
- **Usada nas guias:** [Vendedores](../guias-do-relatorio/vendedores.md), *Comercial antes*, *Vendedores antes*
- **Depende de:** [`23 Faturamento YoY %`](02-temporais.md#23-faturamento-yoy), [`44 Porcentagem Meta Comparavel`](01-principais.md#44-porcentagem-meta-comparavel)
- **É usada por:** nenhuma medida

```dax
-- A comparação com o ano anterior só é mostrada com um ano no filtro
VAR _umAno = HASONEVALUE( dCalendario[Ano] )
VAR _percent = IF( _umAno, [23 Faturamento YoY %] )
VAR _pctMeta = [44 Porcentagem Meta Comparavel]
-- Cores em rgb(): o caractere # quebraria a imagem data:image/svg+xml
VAR _cor =
    SWITCH( TRUE(), _percent > 0, "rgb(63,185,80)", _percent < 0, "rgb(248,81,73)", "rgb(214,215,227)" )
VAR _seta = SWITCH( TRUE(), _percent > 0, "▲ ", _percent < 0, "▼ ", "" )
VAR _linha1 =
    SWITCH(
        TRUE(),
        NOT _umAno, "Escolha um ano para comparar",
        ISBLANK( _percent ), "Sem ano anterior",
        _seta & FORMAT( _percent, "+0.0 %;-0.0 %;0.0 %" ) & " vs. ano anterior"
    )
VAR _corMeta =
    SWITCH(
        TRUE(),
        ISBLANK( _pctMeta ), "rgb(139,148,158)",
        _pctMeta >= 1, "rgb(63,185,80)",
        _pctMeta >= 0.9, "rgb(227,179,65)",
        "rgb(248,81,73)"
    )
VAR _linha2 =
    IF( ISBLANK( _pctMeta ), "Meta: não se aplica a este filtro", "Meta: " & FORMAT( _pctMeta, "0.0 %" ) & " atingida" )
RETURN
    "data:image/svg+xml,<svg viewBox='0 0 219 38' fill='none' xmlns='http://www.w3.org/2000/svg'>"
        & "<g font-family='Segoe UI' text-anchor='start'>"
        & "<text x='1' y='14' fill='" & _cor & "' font-size='13' font-weight='600'>" & _linha1 & "</text>"
        & "<text x='1' y='32' fill='" & _corMeta & "' font-size='11'>" & _linha2 & "</text>"
        & "</g></svg>"
```
<!-- gerado:fim medida:60 SVG Cartao Faturamento v1 -->

## 61 SVG Cartao Margem v1

**Sem uso desde 06/11/2026.** O cartão da guia Comercial que mostrava esta imagem foi trocado pela faixa de KPIs em HTML, desenhada pela [`67 HTML Cartoes KPI`](#67-html-cartoes-kpi). A medida continua no modelo; a versão atual desenha duas linhas em 219 × 38, conforme a descrição do modelo abaixo.

<!-- gerado:inicio medida:61 SVG Cartao Margem v1 -->
- **Tabela:** `_Medidas`
- **Formato:** padrão
- **Usada nas guias:** [Vendedores](../guias-do-relatorio/vendedores.md), *Comercial antes*, *Vendedores antes*
- **Depende de:** [`26 Margem LY`](02-temporais.md#26-margem-ly), [`36 Margem YoY p.p.`](02-temporais.md#36-margem-yoy-pp)
- **É usada por:** nenhuma medida

```dax
-- A comparação com o ano anterior só é mostrada com um ano no filtro
VAR _umAno = HASONEVALUE( dCalendario[Ano] )
VAR _pp = IF( _umAno, [36 Margem YoY p.p.] )
VAR _ly = IF( _umAno, [26 Margem LY] )
-- Cores em rgb(): o caractere # quebraria a imagem data:image/svg+xml
VAR _cor =
    SWITCH( TRUE(), _pp > 0, "rgb(63,185,80)", _pp < 0, "rgb(248,81,73)", "rgb(214,215,227)" )
VAR _seta = SWITCH( TRUE(), _pp > 0, "▲ ", _pp < 0, "▼ ", "" )
VAR _linha1 =
    SWITCH(
        TRUE(),
        NOT _umAno, "Escolha um ano para comparar",
        ISBLANK( _pp ), "Sem ano anterior",
        _seta & FORMAT( _pp, "+0.00;-0.00;0.00" ) & " p.p. vs. ano anterior"
    )
VAR _linha2 = IF( ISBLANK( _ly ), "", "Ano anterior: " & FORMAT( _ly, "0.00 %" ) )
RETURN
    "data:image/svg+xml,<svg viewBox='0 0 219 38' fill='none' xmlns='http://www.w3.org/2000/svg'>"
        & "<g font-family='Segoe UI' text-anchor='start'>"
        & "<text x='1' y='14' fill='" & _cor & "' font-size='13' font-weight='600'>" & _linha1 & "</text>"
        & "<text x='1' y='32' fill='rgb(214,215,227)' font-size='11'>" & _linha2 & "</text>"
        & "</g></svg>"
```
<!-- gerado:fim medida:61 SVG Cartao Margem v1 -->

## 62 SVG Cartao Resultado v1

**Sem uso desde 06/11/2026.** O cartão da guia Comercial que mostrava esta imagem foi trocado pela faixa de KPIs em HTML, desenhada pela [`67 HTML Cartoes KPI`](#67-html-cartoes-kpi). A medida continua no modelo; a versão atual desenha duas linhas em 219 × 38, conforme a descrição do modelo abaixo.

<!-- gerado:inicio medida:62 SVG Cartao Resultado v1 -->
- **Tabela:** `_Medidas`
- **Formato:** padrão
- **Usada nas guias:** [Vendedores](../guias-do-relatorio/vendedores.md), *Comercial antes*, *Vendedores antes*
- **Depende de:** [`30 Resultado LY`](02-temporais.md#30-resultado-ly), [`31 Resultado YoY %`](02-temporais.md#31-resultado-yoy)
- **É usada por:** nenhuma medida

```dax
-- A comparação com o ano anterior só é mostrada com um ano no filtro
VAR _umAno = HASONEVALUE( dCalendario[Ano] )
VAR _percent = IF( _umAno, [31 Resultado YoY %] )
VAR _ly = IF( _umAno, [30 Resultado LY] )
-- Cores em rgb(): o caractere # quebraria a imagem data:image/svg+xml
VAR _cor =
    SWITCH( TRUE(), _percent > 0, "rgb(63,185,80)", _percent < 0, "rgb(248,81,73)", "rgb(214,215,227)" )
VAR _seta = SWITCH( TRUE(), _percent > 0, "▲ ", _percent < 0, "▼ ", "" )
VAR _linha1 =
    SWITCH(
        TRUE(),
        NOT _umAno, "Escolha um ano para comparar",
        ISBLANK( _percent ), "Sem ano anterior",
        _seta & FORMAT( _percent, "+0.0 %;-0.0 %;0.0 %" ) & " vs. ano anterior"
    )
VAR _lyTexto =
    SWITCH(
        TRUE(),
        ABS( _ly ) >= 1E9, FORMAT( _ly / 1E9, "0.00" ) & " bi",
        ABS( _ly ) >= 1E6, FORMAT( _ly / 1E6, "0.0" ) & " mi",
        FORMAT( _ly / 1E3, "0" ) & " mil"
    )
VAR _linha2 = IF( ISBLANK( _ly ), "", "Ano anterior: R$ " & _lyTexto )
RETURN
    "data:image/svg+xml,<svg viewBox='0 0 219 38' fill='none' xmlns='http://www.w3.org/2000/svg'>"
        & "<g font-family='Segoe UI' text-anchor='start'>"
        & "<text x='1' y='14' fill='" & _cor & "' font-size='13' font-weight='600'>" & _linha1 & "</text>"
        & "<text x='1' y='32' fill='rgb(214,215,227)' font-size='11'>" & _linha2 & "</text>"
        & "</g></svg>"
```
<!-- gerado:fim medida:62 SVG Cartao Resultado v1 -->

## 63 SVG Cartao Comissao v1

Desenha, em SVG, a variação da comissão contra o ano anterior (`34 Comissao YoY %`), com seta e cor. *(descrição deduzida do código)*

<!-- gerado:inicio medida:63 SVG Cartao Comissao v1 -->
- **Tabela:** `_Medidas`
- **Formato:** padrão
- **Usada nas guias:** [Vendedores](../guias-do-relatorio/vendedores.md), *Vendedores antes*
- **Depende de:** [`34 Comissao YoY %`](02-temporais.md#34-comissao-yoy)
- **É usada por:** nenhuma medida

```dax
VAR _percent = [34 Comissao YoY %]
VAR _format = FORMAT( _percent + 0 , " +0.00 %; -0.00 %; -")
VAR _seta = 
SWITCH(
    TRUE(),
    _percent > 0 , "▲",
    _percent < 0 , "▼",
    " - "
)
VAR _cor_seta = 
SWITCH(
    TRUE(),
    _percent > 0 , "Green",
    _percent < 0 , "red",
    "#ffffff"
)

VAR _text =
    "data:image/svg+xml,
    <svg  viewBox='0 0 190 50' fill='none' xmlns='http://www.w3.org/2000/svg'>
        <g id='varia&#195;&#167;&#195;&#163;o'>
            <text id='rot_cat' fill='white' xml:space='preserve' style='white-space: pre' font-family='Segoe UI' font-size='12' font-weight='400' letter-spacing='0em'>
                <tspan x='88' y='40.9688'>Vs. Ano Anterior</tspan>
            </text>
            <text id='rot_dados' fill='"& _cor_seta &"' xml:space='preserve' style='white-space: pre' font-family='Segoe UI' font-size='14' font-weight='600' letter-spacing='0em'>
                <tspan x='88' y='21.2969'>"& _format &"</tspan>
            </text>
            <text id='seta' fill='"& _cor_seta &"' xml:space='preserve' style='white-space: pre' font-family='Segoe UI' font-size='14' font-weight='600' letter-spacing='0em'>
                <tspan x='68' y='31.2969'>"& _seta &"</tspan>
            </text>
        </g>
    </svg>
    "

RETURN 
    _text
```
<!-- gerado:fim medida:63 SVG Cartao Comissao v1 -->

## 64 SVG Tabela HTML Content Lite v1

Desenha, em SVG, uma linha de tabela por cidade, com o faturamento abreviado e a variação da margem contra o ano anterior. Alterna entre os dois ao passar o mouse. *(descrição deduzida do código)*

<!-- gerado:inicio medida:64 SVG Tabela HTML Content Lite v1 -->
- **Tabela:** `_Medidas`
- **Formato:** padrão
- **Usada nas guias:** [Comercial ](../guias-do-relatorio/comercial.md), *Comercial antes*
- **Depende de:** [`27 Margem YoY %`](02-temporais.md#27-margem-yoy), [`51 Faturamento formatação de texto`](03-formatacoes.md#51-faturamento-formatacao-de-texto)
- **É usada por:** nenhuma medida

```dax
VAR _cidade = SELECTEDVALUE( dClientes[Cidade] )

VAR _valor = [51 Faturamento formatação de texto]

VAR _margem = FORMAT(  [27 Margem YoY %], "#.0 %")
-----------------------------------
--- Formatação                 ----
-----------------------------------
var __cor_fonte =  "#D6D7E3"

VAR _cores = 
SWITCH(
    TRUE(),
    [27 Margem YoY %] > 0 , "green",
    [27 Margem YoY %] < 0 , "red",
    "#ffffff"
)

RETURN
    "
    <svg width='255' height='79' viewBox='0 0 255 65' fill='none' xmlns='http://www.w3.org/2000/svg'>

        <defs>
            <style>
                #txt_margem, #txt_cidade, #txt_faturamento  {
                    transition: .7s
                }
                

                svg:hover #txt_faturamento  {
                    transform: translateX( -126px)
                }
                svg:hover #txt_cidade {
                    transform: translateX(126px)
                }
                svg:hover  #txt_margem {
                    transform: translateX( -126px)
                }

            </style>
        </defs>

        <g id='tabela_cidades'>
            <line id='divisor' x1='127.5' y1='14' x2='127.5' y2='50' stroke='white' stroke-opacity='0.1'/>
            <text id='txt_cidade' fill='"& __cor_fonte &"' font-family='Segoe UI' font-size='11' font-weight='600'>
                <tspan x='28' y='34.0547'> " & _cidade & " </tspan>
            </text>
            <text id='txt_faturamento' fill='"& __cor_fonte &"' font-family='Segoe UI' font-size='15' font-weight='600'>
                <tspan x='155' y='26.2109'> R$ "& _valor &" </tspan>
            </text>
            <text id='txt_margem' fill='"& _cores &"' font-family='Segoe UI' font-size='15' font-weight='600'>
                <tspan x='155' y='53.2109'> "& _margem &" </tspan>
            </text>
        </g>
    </svg>
    "
```
<!-- gerado:fim medida:64 SVG Tabela HTML Content Lite v1 -->

## 65 SVG Percentual Meta Velocimetro

Medida de nome "velocímetro", cuja expressão é apenas o valor `1`. *(descrição deduzida do código)*

- **Observação:** O formato de exibição é `0` e a expressão é o valor fixo `1`.

<!-- gerado:inicio medida:65 SVG Percentual Meta Velocimetro -->
- **Tabela:** `_Medidas`
- **Formato:** `0`
- **Usada nas guias:** nenhum visual
- **Depende de:** nenhuma medida
- **É usada por:** nenhuma medida

```dax
1
```
<!-- gerado:fim medida:65 SVG Percentual Meta Velocimetro -->

## 66 Meta Cor

Cor da meta conforme o percentual atingido: verde a partir de 60%, vermelho abaixo de 10% e cinza entre os dois. *(descrição deduzida do código)*

- **Regra de negócio:** [Metas](../regras-de-negocio.md#metas)

<!-- gerado:inicio medida:66 Meta Cor -->
- **Tabela:** `_Medidas`
- **Formato:** padrão
- **Usada nas guias:** [Vendedores](../guias-do-relatorio/vendedores.md), *Vendedores antes*
- **Depende de:** [`41 Porcentagem Meta`](01-principais.md#41-porcentagem-meta)
- **É usada por:** nenhuma medida

```dax
SWITCH(
    TRUE(),
    [41 Porcentagem Meta] >= 0.6, "green",
    [41 Porcentagem Meta] < 0.10 , "red",
    "grey"
)
```
<!-- gerado:fim medida:66 Meta Cor -->

## 67 HTML Cartoes KPI

HTML da faixa de KPIs da guia Comercial, para o visual HTML Content (lite): faturamento, resultado e margem, cada um com a comparação contra o ano anterior (só com um ano no filtro), a meta comparável no faturamento e o período analisado. Os tamanhos de fonte são em px reais.

<!-- gerado:inicio medida:67 HTML Cartoes KPI -->
- **Tabela:** `_Medidas`
- **Formato:** padrão
- **Usada nas guias:** [Comercial ](../guias-do-relatorio/comercial.md)
- **Depende de:** [`01 Faturamento`](01-principais.md#01-faturamento), [`09 Resultado`](01-principais.md#09-resultado), [`10 Margem`](01-principais.md#10-margem), [`23 Faturamento YoY %`](02-temporais.md#23-faturamento-yoy), [`26 Margem LY`](02-temporais.md#26-margem-ly), [`30 Resultado LY`](02-temporais.md#30-resultado-ly), [`31 Resultado YoY %`](02-temporais.md#31-resultado-yoy), [`36 Margem YoY p.p.`](02-temporais.md#36-margem-yoy-pp), [`44 Porcentagem Meta Comparavel`](01-principais.md#44-porcentagem-meta-comparavel), [`55 Periodo Analisado`](04-auxiliares.md#55-periodo-analisado)
- **É usada por:** nenhuma medida

```dax
VAR _umAno = HASONEVALUE( dCalendario[Ano] )
-- Valores
VAR _fat = [01 Faturamento]
VAR _res = [09 Resultado]
VAR _mg = [10 Margem]
VAR _fatP = IF( _umAno, [23 Faturamento YoY %] )
VAR _resP = IF( _umAno, [31 Resultado YoY %] )
VAR _resLY = IF( _umAno, [30 Resultado LY] )
VAR _mgPP = IF( _umAno, [36 Margem YoY p.p.] )
VAR _mgLY = IF( _umAno, [26 Margem LY] )
VAR _meta = [44 Porcentagem Meta Comparavel]
VAR _periodo = [55 Periodo Analisado]
-- Cores
VAR _verde = "#3FB950"
VAR _vermelho = "#F85149"
VAR _amarelo = "#E3B341"
VAR _neutro = "#D6D7E3"
VAR _apagado = "#8B949E"
-- Textos de valor
VAR _fatTxt =
    SWITCH( TRUE(), ABS( _fat ) >= 1E9, FORMAT( _fat / 1E9, "0.00" ) & " bi", ABS( _fat ) >= 1E6, FORMAT( _fat / 1E6, "0.0" ) & " mi", FORMAT( _fat / 1E3, "0" ) & " mil" )
VAR _resTxt =
    SWITCH( TRUE(), ABS( _res ) >= 1E9, FORMAT( _res / 1E9, "0.00" ) & " bi", ABS( _res ) >= 1E6, FORMAT( _res / 1E6, "0.0" ) & " mi", FORMAT( _res / 1E3, "0" ) & " mil" )
VAR _resLYTxt =
    SWITCH( TRUE(), ABS( _resLY ) >= 1E9, FORMAT( _resLY / 1E9, "0.00" ) & " bi", ABS( _resLY ) >= 1E6, FORMAT( _resLY / 1E6, "0.0" ) & " mi", FORMAT( _resLY / 1E3, "0" ) & " mil" )
-- Linha de comparação: seta, valor e cor
VAR _cmpFat =
    SWITCH(
        TRUE(),
        NOT _umAno, "<span style='color:" & _neutro & "'>Escolha um ano para comparar</span>",
        ISBLANK( _fatP ), "<span style='color:" & _neutro & "'>Sem ano anterior</span>",
        "<span style='color:" & IF( _fatP >= 0, _verde, _vermelho ) & "'>" & IF( _fatP >= 0, "▲ ", "▼ " ) & FORMAT( _fatP, "+0.0 %;-0.0 %" ) & " vs. ano anterior</span>"
    )
VAR _cmpRes =
    SWITCH(
        TRUE(),
        NOT _umAno, "<span style='color:" & _neutro & "'>Escolha um ano para comparar</span>",
        ISBLANK( _resP ), "<span style='color:" & _neutro & "'>Sem ano anterior</span>",
        "<span style='color:" & IF( _resP >= 0, _verde, _vermelho ) & "'>" & IF( _resP >= 0, "▲ ", "▼ " ) & FORMAT( _resP, "+0.0 %;-0.0 %" ) & " vs. ano anterior</span>"
    )
VAR _cmpMg =
    SWITCH(
        TRUE(),
        NOT _umAno, "<span style='color:" & _neutro & "'>Escolha um ano para comparar</span>",
        ISBLANK( _mgPP ), "<span style='color:" & _neutro & "'>Sem ano anterior</span>",
        "<span style='color:" & IF( _mgPP >= 0, _verde, _vermelho ) & "'>" & IF( _mgPP >= 0, "▲ ", "▼ " ) & FORMAT( _mgPP, "+0.00;-0.00" ) & " p.p. vs. ano anterior</span>"
    )
-- Linha de detalhe
VAR _detFat =
    IF(
        ISBLANK( _meta ),
        "<span style='color:" & _apagado & "'>Meta: não se aplica a este filtro</span>",
        "<span style='color:" & SWITCH( TRUE(), _meta >= 1, _verde, _meta >= 0.9, _amarelo, _vermelho ) & "'>Meta: " & FORMAT( _meta, "0.0 %" ) & " atingida</span>"
    )
VAR _detRes = IF( ISBLANK( _resLY ), "&nbsp;", "Ano anterior: R$ " & _resLYTxt )
VAR _detMg = IF( ISBLANK( _mgLY ), "&nbsp;", "Ano anterior: " & FORMAT( _mgLY, "0.00 %" ) )
-- Blocos
VAR _bloco = "<div style='flex:1;padding:0 14px;border-left:1px solid rgba(255,255,255,.12)'>"
VAR _rot = "<div style='font-size:13px;font-weight:300;color:#C9CCE0'>"
VAR _val = "<div style='font-size:26px;font-weight:600;line-height:32px;color:#FFFFFF'>"
VAR _cmp = "<div style='font-size:13px;font-weight:600;margin-top:2px'>"
VAR _det = "<div style='font-size:12px;color:#C9CCE0;margin-top:2px'>"
RETURN
    "<div style='font-family:Segoe UI,sans-serif;color:#FFFFFF;height:100%;box-sizing:border-box;padding:6px 4px'>"
        & "<div style='font-size:11px;color:" & _apagado & ";text-align:right;padding:0 14px 4px'>" & _periodo & "</div>"
        & "<div style='display:flex'>"
        & "<div style='flex:1;padding:0 14px'>" & _rot & "Faturamento</div>" & _val & "R$ " & _fatTxt & "</div>" & _cmp & _cmpFat & "</div>" & _det & _detFat & "</div></div>"
        & _bloco & _rot & "Resultado</div>" & _val & "R$ " & _resTxt & "</div>" & _cmp & _cmpRes & "</div>" & _det & _detRes & "</div></div>"
        & _bloco & _rot & "Margem</div>" & _val & FORMAT( _mg, "0.00 %" ) & "</div>" & _cmp & _cmpMg & "</div>" & _det & _detMg & "</div></div>"
        & "</div></div>"
```
<!-- gerado:fim medida:67 HTML Cartoes KPI -->
