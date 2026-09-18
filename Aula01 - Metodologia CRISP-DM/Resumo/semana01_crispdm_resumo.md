# Semana 1 — CRISP-DM: Visão Geral

> Leitura rápida pra relembrar. Foco no que costuma passar batido — não no óbvio.

## O que é, e por que "cíclico" de verdade
Roteiro de **6 fases** pra qualquer projeto de Ciência de Dados. "Cíclico" não é força de expressão: se uma fase falha, você **volta** pra uma fase anterior — não recomeça do zero, e não segue em frente ignorando o problema.

🔁 **Exemplo real de retorno no ciclo:** o modelo treinado na Fase 4 (Modeling) sai com desempenho ruim. Isso quase nunca é "culpa do algoritmo" — na maioria das vezes o problema está nos dados que alimentam ele. Então você volta pra Fase 3 (Data Preparation): revê outliers que passaram despercebidos, refaz a imputação, cria novas features. Só depois volta a treinar.

## As 6 fases (com o porquê de cada termo)

**1. Business Understanding**
Aqui você separa duas coisas que parecem a mesma, mas não são:
- **Meta de negócio** = o resultado que a empresa quer ver no mundo real (dinheiro, tempo, risco). Não tem nada de técnico nela.
- **Meta técnica** = a tradução dessa meta em algo que um modelo consegue medir e perseguir.

> Exemplo: a meta de **negócio** é "parar de perder R$ 50 mil/mês com a prensa quebrando". A meta **técnica** é "prever a falha com 2h de antecedência, com Acurácia > 85% e Recall > 80%". Uma é o problema; a outra é a régua que decide se a solução resolveu o problema.

**2. Data Understanding**
Fase de diagnóstico — você **só olha**, ainda não conserta nada. Duas coisas centrais:
- **dtypes e nulos**: conferir se cada coluna tem o tipo certo (número vs texto) e quantos valores estão faltando (`NaN`).
- **Outliers**: valores que fogem completamente do padrão esperado da variável — não é "número grande", é número que não faz sentido físico ou estatístico. Um sensor de temperatura marcando **999°C** não é "um valor alto", é um defeito de leitura.

> Exemplo: 1.000 leituras de sensor, encontrados **15 valores nulos** e **1 outlier (999°C)** vindo de falha do próprio sensor.

**3. Data Preparation**
🔥 **CONSOME MAIS DE METADE DO TEMPO DO PROJETO INTEIRO! (50-70%)** — é aqui que a maior parte dos problemas da Fase 2 são de fato corrigidos:
- **Imputação**: preencher os `NaN` com algum valor razoável. Normalmente a **mediana**, porque ela não é puxada por outliers como a média é.
- **Remoção de outliers via IQR**: método que usa o intervalo entre o 1º e o 3º quartil dos dados pra definir o que é "fora da curva" e descartar (ou tratar) esses registros.
- **Feature engineering**: criar colunas novas que carregam mais informação útil do que as colunas originais sozinhas — combinações, razões, agregações.

> Exemplo: pressão imputada pela mediana (6.0 bar); registros com temperatura > 150°C removidos pelo método IQR; criada a razão "Temperatura / Pressão" como feature nova.

**4. Modeling**
Aqui a escolha do algoritmo importa, mas o "porquê" da escolha importa mais:
- **Escolher algoritmo**: por exemplo Random Forest, que combina várias árvores de decisão votando juntas — reduz o risco de uma árvore isolada "decorar" ruído dos dados.
- **Separar Treino/Teste** (ex: 70/30): o modelo só aprende com o conjunto de treino; o conjunto de teste fica "escondido" dele, simulando dados novos que ele nunca viu. Sem essa separação, você não sabe se o modelo realmente aprendeu ou só decorou os exemplos.
- **`.fit()`**: o comando que efetivamente treina o modelo nos dados de treino.

**5. Evaluation**
Não basta o modelo acertar muito — é preciso confirmar quatro coisas antes de aprovar:
1. Ele bate a **meta de negócio** da Fase 1 (não só a métrica técnica isolada).
2. Ele performa bem em dados **que não viu no treino** (o conjunto de teste) — senão pode estar só "decorando".
3. Os erros que ele comete são **aceitáveis** pro contexto (um Falso Negativo custa mais caro que um Falso Positivo? Depende do problema).
4. Os resultados fazem **sentido** — as variáveis que o modelo usou pra decidir são coerentes com o problema real, não coisas aleatórias.

> Exemplo: Acurácia 89.2%, Recall 84.5% → bateu a meta técnica **e** a de negócio → **Aprovado para Deploy!**

**6. Deployment**
O modelo sai do notebook e vira parte do sistema da empresa de verdade:
- **API REST**: outros sistemas da empresa passam a "perguntar" ao modelo em tempo real, enviando dados e recebendo a predição de volta.
- **Docker**: empacota o modelo e suas dependências num container, garantindo que ele rode igual em qualquer máquina/servidor.
- **Monitoramento de Data Drift / Model Drift**: com o tempo, os dados do mundo real mudam (padrão de consumo, comportamento de sensores, etc.) e o modelo pode começar a errar mais — por isso ele precisa ser observado e retreinado periodicamente, não é "treinar uma vez e esquecer".

## Frase pra guardar
**"O ciclo só fecha quando o modelo sai do notebook e começa a gerar dinheiro de verdade lá na produção — e continua sendo observado depois disso."**