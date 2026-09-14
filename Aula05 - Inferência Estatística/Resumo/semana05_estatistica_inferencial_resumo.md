# Semana 5 — Estatística Inferencial

> Leitura rápida pra relembrar.

## A metáfora da sopa
Não precisa provar a panela inteira pra saber se a sopa está boa — uma colherada bem misturada basta.
- **População** = todos os clientes (a panela)
- **Amostra** = os 3.000 do CSV (a colherada)
- **Inferência estatística** = a matemática que garante que a conclusão da colherada vale pra panela toda

## Teste de Hipóteses — o tribunal
- **H₀ (Nula)**: "é coincidência, não há efeito real" (presunção de inocência)
- **H₁ (Alternativa)**: "existe efeito real"
Só rejeita H₀ se as provas forem fortes o suficiente.

## p-valor — o termômetro do acaso
> "Qual a chance desse resultado ter aparecido só por sorte?"
- **p ≤ 0,05** → chance de coincidência é pequena demais → rejeita H₀ → **"isso é real"**
- **p > 0,05** → ainda pode ser coincidência → não rejeita H₀

## Erro Tipo I e Tipo II — o alarme de incêndio
| | Você diz "sem problema" | Você diz "há problema" |
|---|---|---|
| **Não há problema mesmo** | ✅ Acerto | ❌ Tipo I (alarme falso) |
| **Há problema de verdade** | ❌ Tipo II (falha em detectar) | ✅ Acerto |

🔗 **É A MESMA COISA QUE A MATRIZ DE CONFUSÃO DA SEMANA 2!** Tipo I = Falso Positivo. Tipo II = Falso Negativo.

## Teste de Normalidade — a curva do sino
Testa se os dados seguem a Distribuição Normal (necessário pra várias fórmulas clássicas).
- `score_serasa` → tende a ser Normal
- `renda_mensal` → **NÃO é Normal** (cauda longa, igual visto na Semana 3)

3 testes: **Shapiro-Wilk** (até 5.000 linhas, mais confiável), **Kolmogorov-Smirnov** (maior distância da curva ideal), **Anderson-Darling** (foco nos extremos/outliers).

## Teste Qui-Quadrado — o detetive de categorias
Usado quando as variáveis são **categorias**, não números.
Compara **Observado** (o que aconteceu de verdade) vs **Esperado** (o que aconteceria se não houvesse relação nenhuma).
Se a diferença for grande demais pra ser acaso (p ≤ 0,05) → existe relação real.
Variante: **Aderência (Goodness-of-Fit)** → testa se uma única categoria está distribuída de forma equilibrada.
