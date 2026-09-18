# Semana 1 — Perguntas de Fixação (CRISP-DM), respondidas

---

### 1. Por que o CRISP-DM é chamado de "cíclico" e não de um processo linear? Dê um exemplo de quando você voltaria de uma fase pra outra.

**Minha resposta:**
Caso haja uma falha na parte de Modeling (modelando o sistema para fazer as análises com os dados inseridos, treinando e testando ele), se aqui a gente falhar, retornamos para o Data Preparation corrigindo esses problemas e fazendo o ciclo.

---

### 2. Na Fase 1 (Business Understanding), qual a diferença entre "meta de negócio" e "meta técnica"? Use o exemplo da fábrica (R$ 50 mil/mês).

**Sua resposta:**
Meta de negócio é o objetivo que uma empresa tem ao alcançar [algo]. Meta técnica é automatizar/analisar utilizando o software — a solução técnica que podemos aplicar para solucionar um problema.
Exemplo: corrigir máquina parada gerando prejuízo de 50k por mês.

---

### 3. O que muda entre a Fase 4 (Modeling) e a Fase 6 (Deployment)? Um modelo treinado no notebook já está "pronto" pra empresa usar?

**Minha resposta:**
Ele passa pela etapa 5, Evaluation, responsável por tentar avaliar se há algum tipo de falha, garantindo que não haja um micro erro que pode quebrar a aplicação ou trazer dados incorretos, validando antes do deploy.

**Detalhe extra que você adicionou:**
Na Fase 4 — Modeling, estamos construindo, treinando e ajustando o modelo.
Na Fase 6 — Deployment, colocamos a solução para funcionar no ambiente real da empresa.

---

### 4. Na Fase 5 (Evaluation), por que não basta o modelo ter uma boa métrica técnica? O que mais precisa ser verificado antes de aprovar o Deploy?

**Minha resposta** (você mencionou ter pesquisado para responder):
Não basta verificar se o modelo possui uma boa métrica técnica, pois uma métrica isolada não garante que o modelo esteja adequado ao problema. É necessário verificar se ele atende ao objetivo de negócio, se apresenta bom desempenho em dados que não foram utilizados no treinamento, se possui erros aceitáveis e se seus resultados fazem sentido para o contexto em que será utilizado. Somente depois dessas verificações o modelo deve ser aprovado para o Deployment.


---

## Resumo do que reforçar
- Questão 1: lembrar de explicar o **motivo** do retorno no ciclo, não só o fluxo.
- Questão 3: você já pegou o ponto principal sozinho — parabéns por isso.
- Questão 4: precisou pesquisar — vale reler o resumo da Fase 5 mais uma vez pra essa resposta vir de cabeça da próxima vez.