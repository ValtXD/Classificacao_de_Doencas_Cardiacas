# Classificador de Doenças Cardíacas com Redes Neurais Artificiais

<span style="font-weight: bold; font-size: 16px; color: #333;">Alunos</span>

<table style="border-collapse: collapse; width: 100%;">
  <tr>
    <th align="left" style="padding: 8px; border-bottom: 1px solid #ddd;">Nome</th>
    <th align="left" style="padding: 8px; border-bottom: 1px solid #ddd;">Email</th>
  </tr>
  <tr>
    <td style="padding: 8px; border-bottom: 1px solid #ddd;">Beatriz Christine Azevedo Batista</td>
    <td style="padding: 8px; border-bottom: 1px solid #ddd;">beatriz.batista@icomp.ufam.edu.br</td>
  </tr>
  <tr>
    <td style="padding: 8px; border-bottom: 1px solid #ddd;">Francisco Felipe Barros dos Santos</td>
    <td style="padding: 8px; border-bottom: 1px solid #ddd;">francisco.santos@icomp.ufam.edu.br</td>
  </tr>
  <tr>
    <td style="padding: 8px; border-bottom: 1px solid #ddd;">Ivan Marcos Freitas dos Santos</td>
    <td style="padding: 8px; border-bottom: 1px solid #ddd;">ivanm.santos@icomp.ufam.edu.br</td>
  </tr>
  <tr>
    <td style="padding: 8px; border-bottom: 1px solid #ddd;">Matheus Carvalho Reges</td>
    <td style="padding: 8px; border-bottom: 1px solid #ddd;">matheus.reges@icomp.ufam.edu.br</td>
  </tr>
</table>

## Objetivo do Projeto

Este projeto tem como objetivo desenvolver um modelo de rede neural para previsão de doenças cardíacas com base em dados clínicos de pacientes. As doenças cardiovasculares representam a principal causa de morte mundial, tornando a detecção precoce um desafio crítico para a saúde pública.

---

## Arquitetura do Modelo

O modelo implementado consiste em uma rede neural feedforward com a seguinte estrutura:

- *Camada de Entrada*: 13 neurônios (correspondendo às features)
- *Camadas Ocultas*: 
  - 64 neurônios + Dropout (30%)
  - 32 neurônios + Dropout (20%) 
  - 16 neurônios
- *Camada de Saída*: 1 neurônio com ativação sigmóide
- *Total de Parâmetros*: 3.521

---

##  Dataset

- *Fonte*: Heart Disease UCI Dataset do Kaggle
- *Amostras*: 1.025 observações
- *Variáveis*: 14 colunas (13 features + target)
- *Variável Target*: 
  - 0 = Ausência de doença cardíaca
  - 1 = Presença de doença cardíaca

---

## Metodologia e Pré-processamento

### A Importância da Normalização de Dados (StandardScaler)

A Normalização é um passo crítico no pré-processamento, especialmente para Redes Neurais Artificiais (ANNs). O dataset contém variáveis com escalas muito diferentes—por exemplo, a **idade** (`age`) varia entre 29 e 77, enquanto o **colesterol** (`chol`) pode ir de 126 a mais de 564.

#### Por que Normalizar?

1.  **Convergência Mais Rápida:** Sem a normalização, as funções de ativação e o algoritmo de **Descida do Gradiente** (usado para otimizar os pesos da rede) podem demorar muito mais para convergir. O otimizador se move mais rápido nas direções das *features* de maior escala, o que torna a busca pelo mínimo da função de perda ineficiente.

2.  **Tratamento Equitativo:** O `StandardScaler` garante que todas as *features* contribuam de forma **igual** para a perda. Ao transformar os dados para terem **média 0** e **desvio padrão 1**, evitamos que a Rede Neural dê uma importância desproporcional a *features* com valores numéricos maiores, garantindo que o aprendizado seja baseado na relevância estatística, e não na magnitude numérica.

Em resumo, a normalização é essencial para fornecer uma **"superfície de perda"** mais suave e esférica para o otimizador, permitindo que o modelo treine de forma mais **rápida** e **eficaz**.
---

### Arquitetura da ANN

O classificador foi implementado com uma arquitetura *feedforward* densa, utilizando **3 camadas ocultas** com ativação **ReLU**, e uma camada de saída **Sigmoid** para a classificação binária. O treinamento foi otimizado com **Dropout** e **Early Stopping** para garantir a robustez e evitar *overfitting*.

---

##  O Problema: Detecção Precoce de Doenças Cardíacas

As doenças cardiovasculares são a principal causa de mortalidade global. A detecção precoce é um desafio crítico na saúde pública.

O modelo desenvolvido aqui utiliza o **Dataset Heart Disease da UCI**, que inclui 13 atributos-chave (como idade, tipo de dor no peito, colesterol sérico e frequência cardíaca máxima) para determinar o *status* do paciente.

### Arquitetura da Solução

O classificador foi implementado usando a API Sequential do Keras, com a seguinte estrutura:

* **Modelo:** Rede Neural *Feedforward* Densa.
* **Camadas Ocultas:** Três camadas densas, utilizando a função de ativação **ReLU**.
* **Camada de Saída:** Um neurônio com ativação **Sigmoid** para fornecer uma probabilidade de classificação binária.
* **Técnicas de Regularização:** **Dropout** e **Early Stopping** foram aplicados durante o treinamento para mitigar o *overfitting* e garantir a generalização do modelo.

---

##  Resultados Obtidos e Performance

O modelo demonstrou um **excelente desempenho** após o treinamento e avaliação final no conjunto de testes. A performance alta valida a eficácia da abordagem de Redes Neurais para este problema de classificação de dados clínicos.

**Atenção:** Os valores abaixo foram preenchidos com os resultados mostrados do Notebook (`Trabalho_IA.ipynb`) após rodar o código de avaliação.

| Métrica de Desempenho | Valor no Conjunto de Teste |
| :--- | :--- |
| **Acurácia (Accuracy)** | **98.78%** |
| **Precisão (Precision)** | **0.988** |
| **Recall (Recall)** | **0.988** |
| **Loss Final** | **0.025** |

## Análise dos Resultados

O modelo demonstrou performance válido, com acurácia quase perfeita no conjunto de teste, um resultado que supera as expectativas iniciais do projeto. A matriz de confusão revelou zero falsos positivos e zero falsos negativos entre as 205 amostras testadas, indicando uma capacidade de classificação aparentemente perfeita.

Aspectos Positivos Técnicos:
A curva de aprendizado mostrou um comportamento ideal, com melhoria gradual e consistente tanto na acurácia de treino quanto na validação. A função de perda convergiu de forma estável, reduzindo de aproximadamente 0.78 para 0.024 ao longo do treinamento, sem apresentar oscilações significativas. As técnicas de regularização implementadas, especificamente as camadas de Dropout de 30% e 20% - demonstraram eficácia na prevenção de overfitting, mantendo as curvas de treino e validação próximas durante todo o processo. A arquitetura de rede neural com 3.521 parâmetros mostrou-se adequadamente dimensionada para a complexidade do problema.

Considerações sobre Validade Clínica:
A performance de todas as métricas é estatisticamente incomum em problemas médicos reais, especialmente na cardiologia onde a variabilidade biológica, ruído nos exames e sobreposição de sintomas normalmente impedem acurácia perfeita. Este resultado sugere que o dataset utilizado pode ter uma natureza excessivamente "limpa" ou conter padrões deterministicamente separáveis que não refletem a complexidade da prática clínica real. Em contextos médicos genuínos, é comum observar acurácias entre 85-90% para problemas de diagnóstico cardíaco, tornando estes resultados numericamente perfeitos clinicamente suspeitos.

---

### Matriz de Confusão:

| | **Previsto SEM doença** | **Previsto COM doença** |
| :--- | :---: | :---: |
| **Real SEM doença** | **100** | **0** |
| **Real COM doença** | **0** | **105** |

Explicação simples:

100 pacientes que NÃO tinham doença cardíaca → foram corretamente identificados como saudáveis

105 pacientes que SIM tinham doença cardíaca → foram corretamente identificados como doentes

0 pacientes foram classificados de forma errada

Nenhum falso positivo (pessoa saudável diagnosticada como doente)

Nenhum falso negativo (pessoa doente diagnosticada como saudável)

Resumo ainda mais simples:

O modelo acertou todos os 205 casos de teste

Não cometeu nenhum erro de diagnóstico

- *100 Verdadeiros Negativos*
- *105 Verdadeiros Positivos* 
- *0 Falsos Positivos*
- *0 Falsos Negativos*

---

### Conclusão e Análise do Experimento

O projeto demonstra com sucesso a aplicação prática de redes neurais artificiais para classificação de doenças cardíacas, servindo como um exemplo educacional valioso sobre todo o pipeline de machine learning, desde a análise exploratória inicial até a avaliação final do modelo. A implementação destacou de maneira clara a importância crítica da normalização de dados, uma vez que as variáveis clínicas apresentavam escalas significativamente diferentes (idade variando de 29-77 anos versus colesterol de 126-564 mg/dl), e comprovou a eficácia das técnicas de regularização como Dropout na prevenção de overfitting.

Do ponto de vista técnico, o modelo alcançou resultados válidos, com 100% de acurácia, precisão e recall no conjunto de teste - um desempenho que supera as expectativas convencionais para problemas de classificação binária. A arquitetura de rede neural implementada, com suas camadas densas intercaladas com camadas de Dropout, mostrou-se adequadamente dimensionada e eficiente para a tarefa proposta.

No entanto, é fundamental exercitar cautela científica ao interpretar esses resultados numericamente perfeitos. Na prática clínica real, a variabilidade biológica inerente aos pacientes, a presença de comorbidades complexas e a sobreposição de sintomas entre diferentes condições cardíacas tornam praticamente impossível alcançar acurácia absoluta. A performance impecável observada sugere que o dataset utilizado pode não capturar totalmente a complexidade e as nuances encontradas em ambientes hospitalares reais.

#### Resumo da Análise e Pré-processamento
A Análise Exploratória de Dados (EDA) revelou um dataset bem balanceado.

---

##  Como Executar

O projeto pode ser executado em um ambiente Google Colab ou Jupyter Notebook.

1.  Clone este repositório.
2.  Abra o arquivo `Trabalho_IA.ipynb`.
3.  Certifique-se de que o arquivo de dados `heart.csv` esteja acessível (via Google Drive ou upload local).
4.  Execute todas as células do Notebook em ordem para visualizar a EDA, o treinamento do modelo e a avaliação final.

---

## Acesso ao Projeto

Este projeto foi desenvolvido em um **Jupyter Notebook** no Google Colab. Você pode acessar o código completo e a execução do modelo através do link abaixo:

[**Abrir o Notebook no Google Colab**](https://colab.research.google.com/drive/1HaR_8N7j9LmBWzOcPY4oRs0OUv6btP0t?usp=sharing)
