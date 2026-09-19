# Semana 2 — Perguntas de Fixação (Métricas e Distribuições)

## 1. Por que a Acurácia pode ser uma métrica enganosa quando os dados são desbalanceados (ex: 80% adimplentes, 20% inadimplentes)? Dê um exemplo numérico.

Porque ela calcula apenas a taxa de acertos — lembra por que a mediana é mais precisa que a média? Com dados desbalanceados, a acurácia "quebra" e não consegue perceber os casos das pontas (fraudes, inadimplentes etc.).

**Exemplo numérico:**

Considere um banco com 100 clientes: 80 adimplentes e 20 inadimplentes.

Se um modelo classificar todos os 100 clientes como adimplentes, ele acertará 80 de 100 casos.

**Acurácia = 80%**, embora o modelo não tenha detectado nenhum inadimplente!

---

## 2. Explique a diferença entre Precisão e Recall com suas palavras. No contexto de análise de crédito, qual das duas importa mais e por quê?

**Precisão:** mede o quanto o sistema acerta quando afirma que "fulano dará calote" e ele realmente dá calote. Termo técnico: quando o sistema acusa ser inadimplente e realmente é.

**Recall:** de todos os inadimplentes reais, quantos o sistema conseguiu identificar corretamente?

A importância de cada métrica é subjetiva ao que se precisa analisar em um modelo — em determinado momento, uma métrica pode ser mais relevante que a outra. Não está errado pensar assim, mas o ideal é a explicação abaixo:

> **Importância no crédito:** embora a relevância dependa do contexto, na análise de crédito tradicional o Recall costuma ser priorizado para a classe de inadimplentes. É preferível negar crédito a um bom pagador por engano (perda de oportunidade) do que emprestar a um mau pagador e sofrer um calote (perda direta de capital).

---

## 3. O que significa um Falso Negativo nesse contexto de crédito, e por que ele custa mais caro que um Falso Positivo?

**Conceitos:**

- **Verdadeiro:** quando o sistema diz que algo vai acontecer e acontece.
- **Falso:** o sistema disse que algo iria acontecer e não acontece (acontece o contrário).
- **Positivo:** significa a presença do evento que o modelo busca — se está analisando calotes, a presença do calote é positiva.
- **Negativo:** quando esse dado não está presente.

**Tabela:**

| Sigla | Significado | Explicação |
|---|---|---|
| **VP** (Verdadeiro Positivo) | O sistema afirma que o cliente vai dar calote, e ele realmente dá calote | Nesse cenário o sistema acertou 100%: você não emprestou o dinheiro e não teve prejuízo |
| **FP** (Falso Positivo) | O sistema alerta que algo negativo vai acontecer, mas ocorre o oposto — "fulano vai dar calote", porém ele pagaria | É ruim porque o sistema tem um problema e gera perda de oportunidade |
| **FN** (Falso Negativo) | O sistema erra e causa um prejuízo real. Exemplo: "sistema diz que é bom pagador", você empresta e leva calote | É o pior caso: 100% de falha, com prejuízo e defeito no sistema |
| **VN** (Verdadeiro Negativo) | O sistema acerta, mas não é algo alarmante — na verdade é até bom | O sistema disse que ia pagar, e pagou; não há motivo de preocupação |

**Contexto para entender melhor:** o modelo de exemplo sempre busca o pior caso. Se você tem um VP, é porque evitou cair no golpe de um mau pagador — logo, quando o sistema diz que é golpe, isso é positivo, pois evitamos cair no golpe.

---

## 4. Por que o AUC é considerado uma métrica mais completa do que olhar só a acurácia com limiar fixo de 0.50?

A acurácia pode "quebrar" com dados desbalanceados, enquanto a curva AUC trabalha com uma precisão maior.

**Aprofundando o AUC:** um modelo de machine learning nunca dá uma resposta de "sim" ou "não" — ele avalia os dados que tem e retorna uma probabilidade do que pode acontecer (de acordo com o que foi programado para fazer; se o objetivo é prever calote, ele traz a probabilidade de haver calote). Com esses dados, o usuário deve tomar a decisão final de sim ou não.

**Problema de usar limiar fixo:**

Imagine um banco usando o limite fixo de 50%. Um bom pagador teria somente 5% de probabilidade (0,05) de dar calote, e um mau pagador teria 35% de probabilidade (0,35). É óbvio, nesse contexto, quem seria o mau pagador — porém, com o limiar fixo, o sistema ainda poderia classificar o mau pagador errado (como bom pagador), pois 35% é um valor baixo em termos absolutos (abaixo de 50%), mesmo sendo altíssimo dentro do contexto dessa base de dados.

---

## 5. Explique por que a variável `renda_mensal` foi gerada com distribuição Exponencial e não Normal. O que isso significa visualmente na forma da distribuição?

**Conceitos:**

- **Distribuição Normal:** resultado da soma de diversos fatores independentes. Quanto mais nos afastamos do centro, a probabilidade cai igualmente para os dois lados — a simetria fica exatamente no centro.
- **Distribuição Exponencial:** valores baixos são comuns, enquanto valores altos são casos raros.
  - **Cauda longa (long tail):** a linha se estende para a direita quase até o infinito. É nessa cauda longa que ficam os super-ricos (executivos, grandes empresários) — poucos em quantidade, mas que atingem valores discrepantes (outliers).

---

## 6. Para que serve o `np.clip` na geração de dados sintéticos? Dê um exemplo de quando ele evitaria um valor absurdo.

O funcionamento consiste em mapear um valor máximo e um valor mínimo: a partir do momento em que o dado ultrapassa um desses limites, ele é reajustado para o respectivo valor máximo/mínimo.