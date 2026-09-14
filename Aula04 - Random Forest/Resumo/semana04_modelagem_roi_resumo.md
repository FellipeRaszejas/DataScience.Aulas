# Semana 4 — Modelagem (Random Forest), Avaliação e ROI

> Leitura rápida pra relembrar.

## Random Forest, em uma frase
200 "especialistas" (árvores) votando juntos, cada um vendo os dados de um jeito levemente diferente.

## `class_weight='balanced'`
Fórmula:
```
Peso da classe c = n_amostras / (n_classes × n_amostras_classe_c)
```
🔥 **QUANTO MENOR A CLASSE, MAIOR O PESO!** Isso força o modelo a prestar atenção nos inadimplentes (minoria), em vez de ignorá-los.

## Resultados reais (não são perfeitos, e tudo bem)
- Recall inadimplentes: **73%** (meta era 80% — ficou perto, mas não bateu)
- ROC-AUC: **0.8364** → "bom", não "excelente"
- Precisão inadimplentes: **67%**
- 83 Falsos Negativos (calotes que passaram) e 111 Falsos Positivos (bons clientes recusados)

⚠️ **DADOS REAIS NUNCA PERFORMAM COMO O EXEMPLO PERFEITO DO TUTORIAL!**

## Feature Importance — o raio-x do modelo
Top 5: comprometimento_renda (21%), renda_mensal (20%), score_serasa (17%), valor_parcela (8%), valor_solicitado (7%).
🎯 **AS COLUNAS DE RUÍDO FICARAM COM IMPORTÂNCIA ≈ 0!** Prova de que o modelo filtrou o lixo sozinho.

## ROI — traduzindo estatística em dinheiro
```
Sem modelo  = 311 calotes × R$10.000     = R$ 3.110.000
Com modelo  = (83 × R$10.000) + (111 × R$600) = R$ 896.600
Economia    = R$ 2.213.400
```
🔥 **MAIS DE 2 MILHÕES DE ECONOMIA**, mesmo com um modelo "imperfeito" (recall abaixo da meta). É esse número que convence um diretor financeiro, não a métrica técnica.
