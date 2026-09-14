# Semana 1 — CRISP-DM: Visão Geral

> Leitura rápida pra relembrar. Não é aula completa, é gatilho de memória.

## O que é
Roteiro cíclico de **6 fases** pra qualquer projeto de Ciência de Dados. Cíclico = se algo dá errado numa fase, você **volta** pra uma fase anterior, não é linha reta.

## As 6 fases (em ordem)

**1. Business Understanding**
Traduzir problema de negócio em meta técnica mensurável.
> Exemplo: prensa quebra, custa **R$ 50 mil/mês**. Meta: reduzir 20% do tempo parado → prever falha com **2h de antecedência** (Acurácia > 85%, Recall > 80%).

**2. Data Understanding**
Só diagnosticar, sem mexer em nada ainda: dtypes, nulos, outliers.
> Exemplo: 1.000 leituras de sensor, achou **15 NaN** e **1 pico de 999°C** (erro de sensor).

**3. Data Preparation**
🔥 **CONSOME MAIS DE METADE DO TEMPO DO PROJETO INTEIRO! (50-70%)**
Limpeza, imputação (geralmente pela mediana), remoção de outliers via IQR, criação de features novas.
> Exemplo: imputou pressão pela mediana (6.0 bar), removeu registros com temp > 150°C, criou a razão "Temperatura/Pressão".

**4. Modeling**
Escolher algoritmo (ex: Random Forest), separar Treino/Teste (ex: 70/30), treinar (`.fit()`).

**5. Evaluation**
Validar se o modelo bate a meta de NEGÓCIO da fase 1, não só a meta técnica.
> Exemplo: Acurácia 89.2%, Recall 84.5% → bateu a meta → **Aprovado para Deploy!**

**6. Deployment**
Modelo vira API real (REST, Docker, Cloud) + monitoramento de Data Drift/Model Drift.

## Frase pra guardar
**"O ciclo só fecha quando o modelo sai do notebook e começa a gerar dinheiro de verdade lá na produção."**
