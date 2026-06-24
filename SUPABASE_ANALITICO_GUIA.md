# Guia do Supabase para Cruzamento de Dados

Este guia foi pensado para o modelo de planilha:

- `B26_C1_Distribution Maio variacao.xlsx`

Objetivo:

- subir a base bruta no Supabase
- cruzar cenarios como `B26`, `C1.26` e `ACT-26`
- gerar tabelas, graficos e dashboards

## Ideia da estrutura

Vamos separar em 3 camadas.

### 1. Base bruta

Tabela:

- `financeiro_base_importada`

Ela guarda a aba `Base` praticamente como veio da planilha.

### 2. Camada analitica

View ou tabela agregada para cruzamentos:

- `vw_financeiro_categoria_mes`
- `vw_financeiro_cenario_mes`
- `vw_financeiro_variacao`

### 3. Dashboard

O HTML consulta essas views para montar:

- comparativo entre cenarios
- variacao por categoria
- analise mensal
- ranking

## Tabela principal sugerida

Campos importantes:

- `cenario`
- `periodo`
- `ano`
- `centro_custo`
- `conta_razao`
- `numero_documento`
- `elemento_pep`
- `valor`
- `area_funcional`
- `texto`
- `documento_compras`
- `material_descricao`
- `descricao_cc`
- `analytical_nature`
- `sub_categorization`
- `category`
- `diretoria`
- `budget_owner`
- `hfm_line`
- `comentarios_controladoria`
- `le`

## Como colocar no Supabase

### Passo 1. Criar a tabela

Abra no Supabase:

- `SQL Editor`

Cole o arquivo:

- [supabase_analitico.sql](C:/Users/wesle/OneDrive/Desktop/app%20medly/medley-budget/supabase_analitico.sql)

e rode.

### Passo 2. Importar a planilha

Voce tem 2 caminhos.

#### Caminho simples

1. Converter a aba `Base` para CSV
2. No Supabase, abrir a tabela `financeiro_base_importada`
3. Clicar em `Insert` ou `Import data`
4. Subir o CSV

#### Caminho melhor

Depois a gente cria um importador `.xlsx` direto no HTML.

## Como cruzar os dados

Depois de importar, voce consegue responder perguntas como:

- qual categoria mais variou entre `B26` e `ACT-26`
- como ficou o total por mes
- qual diretoria pesa mais
- qual `budget owner` tem maior impacto
- qual `HFM line` concentra mais valor

## Views sugeridas

### `vw_financeiro_categoria_mes`

Serve para:

- grafico por categoria
- comparativo mensal
- filtros por cenario

### `vw_financeiro_cenario_mes`

Serve para:

- comparar `B26`, `C1.26` e `ACT-26` por mes

### `vw_financeiro_variacao`

Serve para:

- mostrar diferenca entre cenarios
- ranking de maiores variacoes

## Sugestao de dashboard

Primeira tela analitica:

1. Filtros
   - ano
   - cenario base
   - cenario comparativo
   - categoria
   - diretoria
   - budget owner

2. KPIs
   - total do cenario base
   - total do cenario comparativo
   - variacao absoluta
   - variacao percentual

3. Graficos
   - linha por mes
   - barras por categoria
   - ranking de maiores variacoes

4. Tabela dinamica
   - categoria
   - valor base
   - valor comparativo
   - variacao

## O que eu recomendo fazer primeiro

Ordem ideal:

1. criar a tabela no Supabase
2. importar a aba `Base`
3. validar se os dados entraram
4. testar as views
5. depois adaptar o HTML

## Proximo passo tecnico

Depois que voce rodar o SQL no Supabase, eu posso fazer o proximo passo:

- adaptar o sistema para ler essa nova base
- ou criar um importador proprio para esse modelo de planilha
