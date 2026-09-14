# Semana 3 — EDA Avançada + Pipeline de Preparação de Dados

> Leitura rápida pra relembrar.

## Média vs. Mediana
Exemplo real: média da renda = R$ 7.724, mediana = R$ 4.276.
🔥 **QUASE METADE!** A mediana deu quase a metade da média — prova de que outliers (tipo R$ 999.999,00 injetado como ruído) distorcem a média, mas não a mediana.
> Regra: pra variável com outlier possível (renda, patrimônio), **sempre confie mais na mediana**.

## IQR (Intervalo Interquartil)
Onde estão os 50% centrais dos dados (entre Q1 e Q3).
- Limite superior = Q3 + 1,5×IQR
- Limite inferior = Q1 − 1,5×IQR
- Fora disso = outlier no boxplot

## Os 4 gráficos diagnósticos
1. **Countplot do alvo** → mostra desbalanceamento (~80/20)
2. **Boxplot da idade** → outliers isolados fora dos "bigodes" (999, -15)
3. **KDE do score por status** → curvas se sobrepõem → score sozinho não decide tudo
4. **Matriz de correlação** → ruído tem correlação **≈ 0** com tudo

⚠️ **CORRELAÇÃO NÃO É CAUSALIDADE!** E correlação perto de zero só descarta relação *linear*.

## Pipeline de Data Preparation (passo a passo)
1. Padronizar strings (`.str.strip().str.upper()`)
2. Sanitizar outliers → virar `NaN` (idade fora de 18-100, renda > 200k)
3. Feature engineering → criar `comprometimento_renda` (provavelmente a variável MAIS importante depois)
4. Imputar `NaN` pela mediana
5. Remover colunas sem poder preditivo (ID, hash IP, ruído)
6. One-Hot Encoding com `drop_first=True` → **EVITA MULTICOLINEARIDADE PERFEITA!**
7. Split treino/teste com `stratify=y` → mantém a MESMA proporção de inadimplentes nos dois conjuntos
