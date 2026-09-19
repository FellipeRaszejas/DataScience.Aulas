# Questões — Machine Learning e Estatística

## 1. Precisão e Recall

**Recall** = dos casos que realmente são positivos (ex.: são inadimplentes de verdade), quantos o modelo conseguiu capturar.

Pergunta:

> "Estou deixando passar gente perigosa?"

**Precisão** = dos casos que o modelo marcou como positivos, quantos realmente eram positivos.

Pergunta:

> "Quando eu aponto o dedo, estou certo?"

### Situação de negócio onde a Precisão seria mais importante que o Recall

Pense em uma campanha de marketing que oferece um cartão premium apenas para clientes de altíssima renda.

Nesse caso, um **Falso Positivo** (oferecer o cartão para alguém que não se qualifica) pode gerar custos e prejudicar a imagem da empresa.

Já um **Falso Negativo** (deixar de oferecer o cartão para alguém que se qualificaria) representa principalmente uma oportunidade perdida.

Nesse cenário, é mais importante que, quando o modelo indique um cliente como adequado, ele esteja realmente correto. Portanto, a **Precisão é mais importante que o Recall**.

---

## 2. Distribuição Normal

A fórmula utilizada para encontrar um intervalo em uma distribuição Normal é:

$$
\mu \pm k\sigma
$$

Cada parte da fórmula possui uma função.

### Média ($\mu$)

A **média** funciona como o centro da distribuição.

Por exemplo, se:

$$
\mu = 640
$$

podemos considerar 640 como o centro em torno do qual os scores estão distribuídos.

### Desvio padrão ($\sigma$)

O **desvio padrão** indica o quanto os dados costumam se espalhar em torno da média.

Se:

$$
\sigma = 140
$$

cada desvio padrão representa uma distância de 140 pontos.

A partir da média:

- 1 desvio para baixo → $640 - 140 = 500$
- 1 desvio para cima → $640 + 140 = 780$

### Número de desvios ($k$)

O valor de **k** indica quantos desvios padrão queremos considerar.

Na distribuição Normal:

- aproximadamente **68%** → 1σ
- aproximadamente **95%** → 2σ
- aproximadamente **99,7%** → 3σ

### Exemplo

Considerando:

$$
\mu = 640
$$

e

$$
\sigma = 140
$$

Para aproximadamente **95% dos proponentes**, utilizamos 2 desvios padrão:

$$
640 \pm 2(140)
$$

Primeiro:

$$
2(140) = 280
$$

Depois:

$$
640 - 280 = 360
$$

$$
640 + 280 = 920
$$

Portanto, o intervalo é:

$$
360 \leq X \leq 920
$$

Ou seja, aproximadamente **95% dos proponentes estão entre 360 e 920 pontos**.

### Resumindo

> Pegamos a média porque ela representa o centro, o desvio padrão porque representa uma medida de dispersão, multiplicamos pelo número de desvios que queremos considerar e usamos ± porque a distribuição se espalha para os dois lados da média.

---

## 3. Idades iguais a 999.0

Se não tratássemos as idades iguais a **999.0** na base, esse valor seria interpretado como uma idade real.

Como 999.0 está muito distante das idades normais, ele seria um **outlier** e aumentaria artificialmente a dispersão dos dados.

Consequentemente, o **desvio padrão ficaria maior e deixaria de representar corretamente a variação das idades reais**.

O correto seria tratar 999.0 como um valor inválido/ausente antes de calcular as estatísticas.

---

## 4. Variáveis contínuas e variáveis de contagem discreta

### Distribuição Normal — `np.random.normal`

Gera valores **contínuos**, que podem assumir valores decimais.

Exemplo:

```text
1.25
2.73
4.18
5.91 m  