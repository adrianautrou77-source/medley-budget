# Mapeamento do Modelo de Planilha

Arquivo de referencia analisado:

- `B26_C1_Distribution Maio variacao.xlsx`

## Estrutura encontrada

Abas principais:

- `Base`: dados brutos
- `Analise`: resumo comparativo por cenario
- `Planilha2`: recorte por natureza de conta
- `Analise mensal`: comparativo mensal
- `Planilha3`: sem uso relevante

## O que essa planilha representa

Essa planilha parece ser um modelo de analise gerencial e nao um extrato simples de lancamentos SAP.

Ela mistura pelo menos tres cenarios:

- `B26`
- `C1.26`
- `ACT-26`

Ou seja, ela funciona mais como base para comparacao de budget, forecast e realizado.

## Colunas da aba Base

- `Cenario`
- `Periodo`
- `Centro custo`
- `Conta do Razao`
- `Nº documento`
- `Elemento PEP`
- `Valor`
- `Area funcional`
- `Texto`
- `Documento de compras`
- `Material: descricao`
- `Descricao CC`
- `Analytical Nature`
- `Sub-Categorization`
- `Category`
- `Diretoria`
- `Budget Owner`
- `HFM Line`
- `Comentarios Controladoria`
- `LE`

## Relacao com o sistema atual

Hoje o HTML esta preparado para importar lancamentos em formato simples, com campos como:

- `numero_pedido`
- `descricao`
- `fornecedor`
- `data_lancamento`
- `valor`
- `tipo`
- `categoria_id`

Essa planilha modelo nao bate diretamente com esse formato.

## Conclusao pratica

Essa planilha deve ser tratada como:

1. Fonte para analise gerencial e comparativos
2. Base para relatorios executivos
3. Possivel origem de um novo importador especifico

Ela nao deve entrar automaticamente no importador atual de `lancamentos` sem regra de negocio adicional.

## Regras que ainda precisamos decidir

Antes de transformar esse modelo em importacao real, precisamos definir:

1. Qual cenario deve alimentar o dashboard:
   - `B26`
   - `C1.26`
   - `ACT-26`

2. Se cada cenario vai para uma tabela diferente ou para campos diferentes

3. Se a coluna `Periodo` representa o mes de competencia para montar visao mensal

4. Como mapear categorias:
   - `Category`
   - `Sub-Categorization`
   - `Analytical Nature`
   - `HFM Line`

## Recomendacao

O proximo passo ideal e criar um importador separado para esse modelo, com regras especificas para:

- identificar o cenario
- identificar o periodo
- consolidar por categoria
- alimentar dashboard e relatorio sem misturar com os lancamentos detalhados do SAP
