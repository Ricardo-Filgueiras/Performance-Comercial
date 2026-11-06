# Changelog

Mudanças relevantes do painel e da documentação deste projeto. Mudanças do portal inteiro estão no [changelog do portal](../../changelog.md).

O formato segue o [Keep a Changelog](https://keepachangelog.com/pt-BR/1.1.0/). O changelog registra **o que mudou**; toda entrada cita pelo nome as medidas afetadas. Cada versão recebe uma tag `performance-comercial/vX.Y.Z`.

## [Não publicado]

**Guia Comercial: indicadores com contexto** (06/11/2026). A faixa de indicadores passou a mostrar a comparação com o ano anterior, a meta comparável e o período analisado, em letra legível.

### Adicionado

- `36 Margem YoY p.p.`: diferença da margem contra o ano anterior em pontos percentuais. Fica em branco quando não há ano anterior.
- `43 Meta Comparavel` e `44 Porcentagem Meta Comparavel`: meta só dos meses com vendas (2021 tem vendas só até abril) e só quando a comparação faz sentido. Ficam em branco com filtro de unidade, forma de pagamento, cliente ou cidade, produto ou status, porque a meta existe só por vendedor e mês.
- `55 Periodo Analisado`: primeiro e último mês com vendas no filtro, com o aviso de dados fictícios.
- `67 HTML Cartoes KPI`: HTML da faixa de indicadores da guia Comercial, exibido num visual HTML Content (lite).

### Alterado

- Guia Comercial: o cartão nativo de faturamento, resultado e margem foi trocado por um visual HTML Content (lite) com a medida `67 HTML Cartoes KPI`, em 660 × 122 px. O cartão reservava uma área pequena e fixa para a imagem SVG, e o texto ficava com cerca de 6 px. As referências ao cartão antigo saíram de 4 marcadores, que guardavam só o estado de filtro dele.
- `60 SVG Cartao Faturamento v1`, `61 SVG Cartao Margem v1` e `62 SVG Cartao Resultado v1` foram redesenhadas (duas linhas, cores em `rgb()`, margem em p.p., meta comparável, pedido de escolha de ano) e ficaram **sem uso** com a troca do cartão. Continuam no modelo.

### Corrigido

- Documentação: as vendas vão de 01/01/2018 a **30/04/2021**, e não até 31/12/2021. Corrigido no aviso de dados fictícios do portal, em [Como usar](como-usar.md) e em [Sobre esta documentação](readme.md).
- Documentação: o aviso de "documentação em migração" da página inicial do portal estava desatualizado e foi trocado pelo aviso de dados fictícios.

## [2.1.0] - 2026-11-06

Tag `performance-comercial/v2.1.0`. Reúne a migração para o portal (21/10/2026) e as correções do relatório de 05/11/2026. **Nenhuma medida mudou de cálculo.**

**Migração do projeto para o portal de documentação**, com a reescrita da documentação e a reorganização das pastas, em 21/10/2026. **Nenhuma medida DAX foi alterada.** Comparado com o commit `6cf9c4c`, o projeto Power BI só tem 14 arquivos de texto com mudança de conteúdo (22 linhas acrescentadas e 15 removidas), todas listadas em "Alterado".

!!! info "Linha de base e tags"
    Ponto de partida: a tag `performance-comercial/baseline-pre-documentacao`, criada em 05/11/2026 no commit `6cf9c4c`. A versão anterior tem a tag `performance-comercial/v2.0.0`, criada em 06/11/2026 no commit `23c7839`. As datas e os commits abaixo vêm do histórico do Git.

### Adicionado

- Documentação do projeto no padrão da skill `documentacao-bi` 0.1.0, em `docs/projetos/performance-comercial/`: [escopo](escopo.md), [regras de negócio](regras-de-negocio.md), [guias do relatório](guias-do-relatorio/index.md) (8 páginas), [modelo de dados](modelo-de-dados.md), [medidas DAX](medidas-dax/index.md) (50 medidas, com "depende de" e "é usada por"), [fontes de dados](fontes-de-dados.md), [decisões técnicas](decisoes-tecnicas.md) (13 decisões), [guia do desenvolvedor](guia-do-desenvolvedor.md) e [guias anteriores](arquivo/guias-anteriores.md).
- Portal de documentação com menu por pasta, metodologia ([DataOps](../../metodologia/dataops.md) e [versionamento com Git](../../metodologia/versionamento-git.md)) e aviso de pendência. Kit e skill em `.agents/` (`6cf9c4c`).
- Guia de como atualizar o valor dos três parâmetros de caminho depois de clonar o repositório (em [Fontes de dados](fontes-de-dados.md#como-atualizar-o-valor-dos-parametros)).
- Arquivo `LICENSE` (MIT), citado pelo `README.md` mas que não existia (`148ba4d`).
- Grupo de consultas **Parâmetros de dados**, que reúne `Caminho_Extracao`, `Caminho_Dimensoes` e `Caminho_Meta` (`c116cef`).

### Alterado

- [Modelo de dados](modelo-de-dados.md) e [Medidas DAX](medidas-dax/index.md) passaram a ser geradas por `gerar_paginas.py` (skill `documentacao-bi` 0.3.0). As páginas escritas à mão foram para o [Arquivo](arquivo/modelo-de-dados-anterior.md); as descrições, as regras de negócio e as observações das 50 medidas foram levadas para acima de cada bloco `gerado`, e a seção de nomes antigos de medidas ficou no índice. As páginas por pasta de exibição mudaram de endereço: `principais`, `temporais` e `formatacoes` viraram `01-principais`, `02-temporais` e `03-formatacoes`. Nenhuma medida foi alterada.
- Projeto Power BI movido para `src/projeto/performance-comercial/` e renomeado de "Performace Comercial" para "Performance Comercial" (arquivo `.pbip` e pastas `.Report` e `.SemanticModel`) em `c116cef` e `2d2af2d`.
- Dados movidos de `src/data/` para `data/`, na raiz (`3578022`). Os valores dos três parâmetros passaram a apontar para a nova pasta (`2d2af2d`). As consultas das tabelas `fVendas`, `fMetas`, `dClientes`, `dProdutos`, `dVendedores`, `dUnidades`, `dStatus` e `dPagamento` e a consulta `dCidades` não mudaram.
- `README.md`: árvore de pastas, passo de abertura do projeto e endereço de clone corrigido.
- Repositório no GitHub renomeado de `Performace-Comercial` para `Performance-Comercial` em 04/11/2026. Links do `README.md`, de [Sobre esta documentação](readme.md) e o exemplo de caminho em [Fontes de dados](fontes-de-dados.md#como-atualizar-o-valor-dos-parametros) atualizados. O link do botão da guia Capa foi atualizado no Power BI Desktop em 05/11/2026. Os parâmetros de caminho continuam com a grafia antiga (veja as [pendências](pendencias.md#pendencias-observadas-no-modelo)).
- A pasta `site/`, com a saída do MkDocs, deixou de ser versionada e entrou no `.gitignore` (`1b1008e`). A documentação é publicada na branch `gh-pages` por `mkdocs gh-deploy`.
- Dependências de `mkdocs.yml` e `pyproject.toml`: plugins `awesome-nav`, `git-revision-date-localized` e `panzoom`, com o MkDocs fixado abaixo da versão 2.
- Anotação `PBI_ResultType` das tabelas voltou de `Exception` para `Table` (`56b7cb6`), desfazendo a mudança de `2f2c698`, de 23/04/2026. Página ativa do relatório trocada de "Analítico antes" para a Capa.
- Medidas `52 Rank Cidade`, `53 Max Y Visual 01 pg Vendedores` e `54 Nome Vendedor` movidas para a pasta de exibição `04. Auxiliares`, e as medidas `Context Medida z`, `Linha Anterior`, `Linha Atual`, `Seta para Cima`, `Seta para baixo  ( limit sup )` e `Seta para baixo  ( limit Inferior )`, da tabela `zMetricas`, para a pasta `Tooltip Rosca`. Nenhuma expressão mudou. Na documentação, a página *Sem pasta de exibição* deu lugar a [04. Auxiliares](medidas-dax/04-auxiliares.md) e [Tooltip Rosca](medidas-dax/tooltip-rosca.md).
- Ao salvar, o Power BI Desktop atualizou as versões de schema do relatório e o `compatibilityLevel` do modelo (de 1601 para 1606), redimensionou um cartão da guia Comercial e ligou a largura automática de colunas de uma tabela da mesma guia.

### Corrigido

No **relatório**:

- Os visuais, marcadores e filtros que apontavam para 25 nomes antigos de medidas foram reapontados para os nomes atuais, em 89 arquivos (694 referências), entre eles `01 Faturamento`, `07 Comissao`, `09 Resultado`, `10 Margem`, `40 Meta`, `41 Porcentagem Meta` e `52 Rank Cidade`. A correspondência completa está em [Nomes antigos de medidas](medidas-dax/index.md#nomes-antigos-de-medidas-no-relatorio). Nenhuma medida mudou.
- Botões sem destino ou com marcador inexistente: na guia Comercial, "Botão desempenho on" passou a apontar para `RankCidVisivel` e o botão de menu "geral" para a própria guia; na Comercial antes, "Botão desempenho on" e "botão rank on" passaram a apontar para `Desempenho Por Cidade v1` e `Rank Todas cidades v1`, e o botão de menu "geral" para a própria guia (ver [Guias do relatório](guias-do-relatorio/index.md#problemas-encontrados-nos-botoes)).

Correções na **documentação** (o modelo não foi alterado):

- Colunas de `dClientes` (`Cliente`, `Cidade`, `UF`, `Estado`), `dVendedores` (`Vendedor`, `URL Foto`, `Gerente`), `dProdutos` (`Produto`) e `fMetas` (`Valor Meta`), que a documentação de 30/01/2026 descrevia de outra forma.
- `dCalendario`: valores `Sem1` e `Tri1`, hierarquia `Data` (Ano, Mes Abreviado, Dia), período de 01/01/2018 a 31/12/2021 e a definição de `Datas com Venda`.
- `dStatus`: os valores são Válidas e Inválidas, e não "Efetivado" e "Cancelado".
- `42 Diferença Meta`: usa valor absoluto (`ABS`), e não "Faturamento − Meta".
- Despesa e impostos: a descrição de frete, ICMS, PIS e COFINS foi retirada, porque não está no modelo.

### Removido

- As páginas antigas `docs/01 visao geral.md`, `02 dicionario dados.md`, `03 guia medidas dax.md`, `04 relacionamentos.md`, `05 changelog.md` e `06 boas praticas.md`, mais `docs/estrutura_definition_legivel.md` e `docs/requisitos.md`, depois de migradas para as páginas do projeto. O histórico delas continua no Git.

### Problemas conhecidos (não corrigidos)

- O arquivo `.github/workflows/docs.yml` está vazio, e a documentação é publicada manualmente.

## [2.0.0] - 2026-01-30

Versão registrada na documentação anterior. No Git, o modelo dessa versão está no commit `23c7839`, de 02/02/2026, marcado com a tag `performance-comercial/v2.0.0` (criada em 06/11/2026). Os itens abaixo vêm do changelog anterior e foram conferidos contra o modelo atual; o Git não permite separar essas mudanças das outras do mesmo commit.

### Adicionado

- `03 Lucro Bruto` (faturamento menos custo) e `04 Margem Bruta` (essa diferença dividida pelo faturamento), na pasta `01.Principais`.
- Documentação em seis páginas numeradas (visão geral, dicionário de dados, guia de medidas DAX, relacionamentos, changelog e boas práticas).
- Prefixo numérico nos nomes das medidas, nas faixas descritas no [Guia do desenvolvedor](guia-do-desenvolvedor.md#nomes).

### Alterado

- Medidas renomeadas com prefixo numérico, por exemplo `Faturamento` para `01 Faturamento`, `Meta` para `40 Meta` e `rank cidade` para `52 Rank Cidade`. Hoje a tabela `_Medidas` tem 44 medidas, todas numeradas. A documentação anterior falava em 48 medidas renomeadas, número que não bate com o modelo.
- Medidas de variação no tempo reescritas com variáveis (`VAR`): `23 Faturamento YoY %`, `24 Faturamento MoM %`, `27 Margem YoY %`, `28 Margem MoM %`, `31 Resultado YoY %`, `32 Resultado MoM %`, `34 Comissao YoY %` e `35 Comissao MoM %`.
- Descrição (`///`) acrescentada às medidas `03 Lucro Bruto`, `04 Margem Bruta`, `10 Margem`, `12 Positivação Clientes` e `13 Positivação Produtos`.
- Pastas de exibição: `01.Principais`, `02. Temporais`, `03. Formatações` e `.Visuais SVG`.

### Corrigido

- `12 Positivação Clientes` e `13 Positivação Produtos` passaram a contar só as vendas válidas (`Id Status = 1`). Segundo a documentação anterior, antes contavam todas.
- Divisões com `DIVIDE(..., ..., BLANK())`, para não dar erro quando o denominador é zero: `10 Margem`, `23 Faturamento YoY %`, `24 Faturamento MoM %`, `27 Margem YoY %`, `28 Margem MoM %`, `31 Resultado YoY %`, `32 Resultado MoM %`, `34 Comissao YoY %`, `35 Comissao MoM %` e `41 Porcentagem Meta`.

## Histórico anterior a 2.0.0

Reconstruído a partir do Git. O projeto não tinha versões nem tags antes da 2.0.0. A documentação anterior citava versões "1.0.0" e "1.5.0" com datas estimadas, que **não** foram mantidas aqui, porque o histórico não as confirma.

| Data | Commit | O que mudou |
|---|---|---|
| 2025-10-22 | `1812783`, `cd6a9ab`, `06b3f4c` | Início do repositório, com o painel em arquivo `.pbix` e os dados em `src/data/` |
| 2025-10-24 | `8703e41` | Painel passa ao formato PBIP; modelo e primeira guia Comercial, com o gráfico de evolução do faturamento |
| 2025-10-24 | `f133257` | Cartões SVG de variação contra o ano anterior |
| 2025-10-27 | `e605e67`, `c68eea1`, `ee3781d`, `0e2804a` | Ajuste das consultas das dimensões, visual de conteúdo HTML, botões que alternam tabela e ranking por cidade e primeira dica de ferramenta |
| 2025-11-03 | `4ed3100`, `f033698` | Dica de ferramenta dos vendedores por gerente (com a tabela `zMetricas`) e dica da tabela de vendedores por cidade, com uma nova página |
| 2025-11-04 | `16f76c2`, `47aca61`, `1df255a` | Guia Mapa Calor e início da guia Vendedores |
| 2025-11-05 | `fb30781`, `34c0567` | Guia Vendedores e Capa finalizadas; menu lateral e navegação |
| 2025-11-11 | `e0dd518`, `fb3fb1b` | Versão "completa" do painel, com as imagens e as guias "antes"; ajuste do README e da seção de portfólio |
| 2026-02-02 | `63872c7`, `23c7839` | Modelo removido e recolocado no mesmo dia; renomeação das medidas e documentação em seis páginas (ver 2.0.0) |
| 2026-04-23 | `0773ea2` | MkDocs Material, `.gitattributes` e documentação movida para `docs/`; `.pbix` original removido |
| 2026-04-23 | `2f2c698` | Página ativa do relatório e anotação `PBI_ResultType` das tabelas |

## Planejado

Sem data prevista, ver [Escopo](escopo.md#planejado-ainda-nao-implementado): ticket médio, curva ABC de produtos, produtividade por vendedor e projeção de meta.
