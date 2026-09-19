Por que o parâmetro class_weight='balanced' no Random Forest é fundamental quando lidamos com classes desbalanceadas? Como ele altera a penalização do modelo?
No contexto dado em aula, o modelo sem ajustes pode atingir 95% de acurancia simplesmente chutando que todo mundo seria um bom pagador e ignorando os inadimplentes

Logo se utiliza o class_weight="balaced" pois ele calcula pesos inversamente proporcionais as frequencias das classes na base de dados 
Tradução:Se o machine learning cometer um erro na classe minoritária, esse erro do algoritmo é multipilicado por um peso maior do que quando ele erra a classe majoritária. Obrigando as random forrest a priorizarem regras que percebam corretamente os padrões da classe rara.

Ao analisar o gráfico de Feature Importance, por que variáveis como ruido_estocastico e numero_da_sorte_app obtiveram valores de importância próximos de zero?
O feature importance (métrica de relevância que o modelo usou na tomada de uma decisão) está medido o quanto cada variável contribui na redução da incerteza e dividir os dados de forma limpa ao longo de todas as árvores
Essas variaveuis da questão não se aplicam estatisticamente com a inadimplencia
Aprendendo a filtrar os "ruidos aleatorios" que podem haver no meio dos dados



Se o custo de um Falso Negativo aumentasse de R5.000,00, o que deveria ser feito com o limiar de probabilidade (threshold) de aprovação do modelo?
O limiar precisaria ser reduzido por exemplo, baixando a régua de corte de $50\%$ para $30\%$ ou $20\%$).
Resuma as principais vantagens do algoritmo Random Forest em relação a uma única Árvore de Decisão simples.

4. Resumo das Vantagens do Random Forest vs. Árvore de Decisão SimplesAspectoÁrvore de Decisão SimplesRandom Forest (Ensemble)Variança e OverfittingAlta tendência a decorar os dados de treino (memoriza ruídos).Baixa variância; combina centenas de árvores reduzindo o overfitting.EstabilidadeSensível: pequenas mudanças nos dados alteram toda a árvore.Alta estabilidade: mudanças isoladas afetam poucas árvores do conjunto.Tomada de DecisãoUma única regra rígida (se/senão) do topo à base.Votação da maioria (moda) entre centenas de sub-modelos independentes.AmostragemTreina com 100% da base e todas as colunas.Usa Bootstrap (amostras aleatórias de dados) e amostragem aleatória de atributos por nó.