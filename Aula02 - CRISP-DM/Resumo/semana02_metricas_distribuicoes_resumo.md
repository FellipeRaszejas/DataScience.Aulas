# Semana 2 — Métricas de Avaliação e Distribuições Estatísticas

> Leitura rápida pra relembrar.

## Matriz de Confusão (a base de tudo)

|  | Previu: Bom pagador | Previu: Inadimplente |
|---|---|---|
| **Era bom pagador** | VN (acerto) | FP (recusou à toa) |
| **Era inadimplente** | FN (deixou passar) 💀 | VP (acerto) |

⚠️ **FN É O ERRO MAIS CARO!** (R$ 10.000 vs R$ 600 do FP)

## As 4 métricas

- **Acurácia** = acertos totais / tudo → 🚨 ENGANA em dados desbalanceados
- **Precisão** = dos que marquei "inadimplente", quantos realmente eram
- **Recall** = dos inadimplentes reais, quantos eu peguei → **A MAIS IMPORTANTE aqui**, porque cada FN é caro
- **F1-Score** = equilíbrio entre Precisão e Recall

## Curva ROC / AUC
Testa vários limiares de decisão, não só 0.5.
- AUC = 1.0 → perfeito
- AUC = 0.5 → chute aleatório
- Exemplo visto: AUC = **0.9867** (dado de brinquedo, quase perfeito)

## Distribuições (o "porquê" dos dados sintéticos)

- **Normal (Gaussiana)**: idade, score → regra **68-95-99.7%**
- **Poisson**: contagens raras (nº de consultas, atrasos) → só inteiros ≥ 0
- **Exponencial**: renda mensal → **CAUDA LONGA À DIREITA!** (maioria ganha pouco, poucos ganham muito)
- **`np.clip`**: trava valor num intervalo (score não passa de 990 nem fica abaixo de 150)
