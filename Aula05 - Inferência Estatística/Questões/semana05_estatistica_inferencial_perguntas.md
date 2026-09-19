# Semana 5 — Perguntas de Fixação (Estatística Inferencial)

## 1. Usando a metáfora da sopa, explique a diferença entre população e amostra. Por que a estatística inferencial é necessária quando trabalhamos só com amostra?

Você não precisa provar toda a sopa para saber se está boa — uma concha já serve. Porém, população e amostra não são exatamente como uma sopa: é necessário, ao analisar uma amostra específica, utilizar a estatística inferencial como forma de comprovar que a "concha" (a amostra) é equivalente ao restante da sopa (a população).

**Conceito:** estatística inferencial = trabalhar com a margem de erro e a incerteza.

---

## 2. Como você interpreta um p-valor de 0,03? E um de 0,20? O que muda na decisão em cada caso?

- **p-valor = 0,03:** a chance de o resultado ser coincidência é de 3% — portanto, rejeita-se H0 (não é coincidência).
- **p-valor = 0,20:** a chance de o resultado ser coincidência é de 20% — portanto, não se rejeita H0 (é coincidência).

---

## 3. Por que testar se uma variável segue Distribuição Normal é importante antes de aplicar certas fórmulas estatísticas? Dê um exemplo de variável que normalmente NÃO é Normal e explique por quê.

É importante testar a normalidade porque muitos testes estatísticos tradicionais (chamados paramétricos) assumem que os dados seguem uma curva em formato de sino. Se a variável não for Normal, esses testes podem gerar conclusões erradas.

**Exemplo de variável NÃO Normal:** uso de dados de internet (GB) ou renda. A maioria das pessoas consome volumes baixos/médios, mas uma pequena minoria usa volumes gigantescos, criando uma cauda longa e tirando a simetria da curva.

---

## 4. Explique com suas palavras como funciona o Teste Qui-Quadrado. O que significa comparar "Observado" com "Esperado"?

Avalia se duas características têm relação entre si.

**Exemplos de analogia:**
- Caloteiro (estatística) nunca é policial (categoria).
- Caloteiro (estatística) sempre torce pro Vasco (categoria).

---

## 5. Qual a diferença entre o Teste Qui-Quadrado de Independência (duas variáveis categóricas) e o de Aderência (Goodness-of-Fit)?

O teste de Aderência (Goodness-of-Fit) questiona: *"A distribuição real dos meus dados (o que observei) combina (adere) com a distribuição teórica ou esperada que eu tinha em mente?"*

**Exemplo — Estoque e Vendas (Distribuição de Tamanhos de Camisetas):**

**Cenário:** o comprador de uma loja de roupas pede peças ao fornecedor na seguinte proporção histórica: 10% P, 20% M, 40% G e 30% GG.

**Observado na semana:** ele vendeu 225 camisetas e quer saber se as vendas reais acompanharam essa proporção.

| Tamanho | Esperado | Observado |
|---|---|---|
| P | 22,5 | 25 |
| M | 45 | 41 |
| G | 90 | 91 |
| GG | 67,5 | 68 |

**Aplicação do Goodness-of-Fit:** o teste compara o Observado com o Esperado para verificar se o comportamento de compra mudou (o que exigiria alterar o pedido ao fornecedor) ou se a pequena variação foi mero acaso.

---

## Conceitos das questões 4 e 5

- **Frequência Observada:** é a contagem real dos dados que coletamos na prática (ex.: quantos clientes de cartão de crédito realmente cancelaram).
- **Frequência Esperada:** é a contagem matemática que esperaríamos encontrar se as duas variáveis fossem totalmente independentes (se não houvesse relação alguma entre elas).
- **A lógica:** quanto maior for a diferença entre o que foi observado e o que era esperado, maior será o valor do Qui-Quadrado — indicando que existe, sim, uma relação real entre as características.