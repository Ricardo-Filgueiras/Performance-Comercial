# Guias do relatório

O relatório `Performance Comercial.Report` tem **12 guias**. Cada guia em uso tem uma página aqui, na ordem em que aparece no relatório. As quatro versões anteriores ("antes") estão no [Arquivo](../arquivo/guias-anteriores.md).

O nome do arquivo de cada página foi escolhido pelo assunto da guia, não pelo nome de exibição, para que o endereço não quebre se a guia for renomeada.

| # | Guia | Visuais | Como se chega |
|---:|---|---:|---|
| 1 | [Capa](capa.md) | 4 | Guia visível; é a primeira ao abrir o relatório. Os botões "Capa" das outras guias voltam para ela |
| 2 | [Comercial](comercial.md) | 26 | Navegador de páginas da Capa e botões de menu em Analítico, Mapa Calor, Vendedores |
| 3 | [Analítico](analitico.md) | 15 | Navegador de páginas da Capa e botões de menu em Comercial, Mapa Calor, Vendedores |
| 4 | [Mapa Calor](mapa-calor.md) | 20 | Navegador de páginas da Capa e botões de menu em Comercial, Analítico, Vendedores |
| 5 | [Vendedores](vendedores.md) | 22 | Navegador de páginas da Capa e botões de menu em Comercial, Analítico, Mapa Calor |
| 10 | [Dica de ferramenta: evolução do faturamento](dica-evolucao-faturamento.md) | 1 | Dica de ferramenta: aparece ao passar o mouse sobre visuais da guia Comercial |
| 11 | [Dica de ferramenta: gerente e vendedores](dica-gerente-vendedores.md) | 2 | Dica de ferramenta: aparece ao passar o mouse sobre visuais da guia Comercial |
| 12 | [Dica de ferramenta: tabela de vendedores](dica-tabela-vendedores.md) | 2 | Dica de ferramenta: aparece ao passar o mouse sobre visuais da guia Comercial |

## Guias ocultas

11 das 12 guias estão marcadas como **ocultas** (`HiddenInViewMode`): só a Capa aparece na barra de guias de quem lê o relatório. As quatro guias de análise (Comercial, Analítico, Mapa Calor e Vendedores) ficam ocultas na barra, mas são o conteúdo principal: o navegador de páginas da Capa e os botões de menu levam a elas. As três páginas de dica de ferramenta são ocultas por natureza. As quatro versões "antes" também estão ocultas e fora do navegador.

## Problemas encontrados nos botões

Corrigidos em 05/11/2026. Cada botão passou a seguir o padrão dos botões que já funcionavam:

- Na guia [Comercial](comercial.md), o botão "Botão desempenho on" apontava para o marcador inexistente `b665145e7737d486954d` e passou a apontar para `RankCidVisivel`, a visão do grupo em que ele está (o par simétrico, no outro grupo, aponta para `GeralCidadesTab`).
- Na guia Comercial, o botão do menu lateral com o ícone "geral" não tinha destino e passou a levar à própria guia, como nas outras guias.
- Na guia Comercial antes, "Botão desempenho on" e "botão rank on" apontavam para os marcadores inexistentes `b665145e7737d486954d` e `51958de021a70cbce700` e passaram a apontar para `Desempenho Por Cidade v1` e `Rank Todas cidades v1`. O botão do menu lateral da mesma guia também não tinha destino e passou a levar a ela.

!!! info "Marcadores da Comercial antes"
    Os marcadores `Desempenho Por Cidade v1` e `Rank Todas cidades v1` estão configurados para valer só para um visual cada. Por isso a troca de visão na Comercial antes pode não funcionar por completo. A guia é mantida como histórico, e a configuração não foi alterada.
