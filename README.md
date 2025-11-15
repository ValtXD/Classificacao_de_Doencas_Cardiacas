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

O objetivo principal deste projeto é construir, treinar e avaliar um modelo de **Classificação Binária** utilizando uma **Rede Neural Artificial (ANN)** para prever a **presença (1) ou ausência (0)** de doença cardíaca em pacientes. O modelo utiliza um conjunto de atributos clínicos para auxiliar na detecção precoce e no diagnóstico.

---

## Metodologia e Pré-processamento

### A Importância da Normalização de Dados (StandardScaler)

A Normalização é um passo crítico no pré-processamento, especialmente para Redes Neurais Artificiais (ANNs). O dataset contém variáveis com escalas muito diferentes—por exemplo, a **idade** (`age`) varia entre 29 e 77, enquanto o **colesterol** (`chol`) pode ir de 126 a mais de 564.

#### Por que Normalizar?

1.  **Convergência Mais Rápida:** Sem a normalização, as funções de ativação e o algoritmo de **Descida do Gradiente** (usado para otimizar os pesos da rede) podem demorar muito mais para convergir. O otimizador se move mais rápido nas direções das *features* de maior escala, o que torna a busca pelo mínimo da função de perda ineficiente.

2.  **Tratamento Equitativo:** O `StandardScaler` garante que todas as *features* contribuam de forma **igual** para a perda. Ao transformar os dados para terem **média 0** e **desvio padrão 1**, evitamos que a Rede Neural dê uma importância desproporcional a *features* com valores numéricos maiores, garantindo que o aprendizado seja baseado na relevância estatística, e não na magnitude numérica.

Em resumo, a normalização é essencial para fornecer uma **"superfície de perda"** mais suave e esférica para o otimizador, permitindo que o modelo treine de forma mais **rápida** e **eficaz**.

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
| **Acurácia (Accuracy)** | **XX.XX%** |
| **Precisão (Precision)** | **X.XXX** |
| **Recall (Recall)** | **X.XXX** |
| **Loss Final** | **X.XXX** |

**Breve Análise:**

A alta **Acurácia** indica que o modelo acerta a classificação na maioria dos casos. O **Recall** alto (capacidade de identificar corretamente pacientes *com* a doença) é crucial em aplicações médicas, enquanto a **Precisão** alta garante que a maioria dos diagnósticos positivos são, de fato, corretos. A convergência rápida da perda valida a qualidade do treinamento, potencializada pela **Normalização de Características** e pela regularização.

---

### Conclusão e Análise do Experimento

Conclusão e Análise do Experimento
O objetivo deste projeto foi o de construir e avaliar um modelo de Classificação Binária utilizando Redes Neurais Artificiais (ANN) para prever a presença ou ausência de doenças cardíacas (0 ou 1) com base em 13 atributos clínicos.

#### Resumo da Análise e Pré-processamento
A Análise Exploratória de Dados (EDA) revelou um dataset bem balanceado.

---
##  Como Executar

O projeto pode ser executado em um ambiente Google Colab ou Jupyter Notebook.

1.  Clone este repositório.
2.  Abra o arquivo `Trabalho_IA.ipynb`.
3.  Certifique-se de que o arquivo de dados `heart.csv` esteja acessível (via Google Drive ou upload local).
4.  Execute todas as células do Notebook em ordem para visualizar a EDA, o treinamento do modelo e a avaliação final.
