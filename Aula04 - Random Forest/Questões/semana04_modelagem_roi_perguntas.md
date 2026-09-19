# Semana 4 — Perguntas de Fixação (Modelagem, Avaliação e ROI)

## 1. Explique com suas palavras como o Random Forest toma uma decisão final, usando a ideia de "votação".

**Moda:** o voto da maioria, como em um tribunal de justiça.

**Analogia:** um tribunal de justiça, onde cada juiz (árvore) dá o seu veredito.

A ideia de "votação" significa que o Random Forest treina dezenas ou centenas de Árvores de Decisão independentes. Para classificar um novo cliente, cada árvore analisa os dados e dá o seu voto (ex.: "Inadimplente" ou "Bom Pagador"). A decisão final do modelo é dada pela moda — o voto da maioria simples de todas as árvores.

---

## 2. Os resultados dessa semana (recall de 73%) foram piores que os da Semana 2 (AUC de 0,98). Por que isso é esperado e até "normal" ao sair de um exemplo de brinquedo para dados reais?

**Dados de brinquedo:** sintéticos ou ultra-simplificados. São dados perfeitos, sem ruído (ou sem dados nulos/faltantes) e com clara separação entre as classes — por isso é fácil atingir um resultado tão alto, o que é um pouco ilusório (AUC de 98%).

**Recall (dados reais):** a realidade traz imprevistos, dificuldade de diferenciar o mau e o bom pagador (sobreposição de perfis) e desbalanceamento de classes. Essa queda é o padrão esperado ao se deparar com o mundo real.

---

## 3. O que significou o fato das colunas de ruído terem ficado com importância próxima de zero no gráfico de Feature Importance? Por que isso é uma validação importante do modelo?

Porque elas contêm apenas números aleatórios ou irrelevantes — não têm poder preditivo nem relação causal/estatística com a inadimplência.

---

## 4. Por que o resultado financeiro (ROI) costuma ser mais convincente para um gestor de negócio do que a métrica técnica (recall, AUC) sozinha?

Como pudemos ver, o resultado financeiro (ROI) é mais convincente porque o gestor de negócios toma decisões baseadas em orçamento e lucro/prejuízo em reais (R$), e não em abstrações matemáticas como AUC ou Recall. O ROI traduz o impacto do modelo diretamente na última linha do balanço da empresa (ex.: "o modelo economizou R$ 1,2 milhão em calotes").

**ROI = Retorno sobre o Investimento.**

Para trazer valores mais precisos ao mundo empresarial, o resultado deve ser dividido pelo impacto financeiro.