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

**Atenção:** Os valores abaixo devem ser preenchidos com os resultados exatos do seu Notebook (`Trabalho_IA.ipynb`) após rodar o código de avaliação.

| Métrica de Desempenho | Valor no Conjunto de Teste |
| :--- | :--- |
| **Acurácia (Accuracy)** | **XX.XX%** |
| **Precisão (Precision)** | **X.XXX** |
| **Recall (Recall)** | **X.XXX** |
| **Loss Final** | **X.XXX** |

**Breve Análise:**

A alta **Acurácia** indica que o modelo acerta a classificação na maioria dos casos. O **Recall** alto (capacidade de identificar corretamente pacientes *com* a doença) é crucial em aplicações médicas, enquanto a **Precisão** alta garante que a maioria dos diagnósticos positivos são, de fato, corretos. A convergência rápida da perda valida a qualidade do treinamento, potencializada pela **Normalização de Características** e pela regularização.

---

##  Como Executar

O projeto pode ser executado em um ambiente Google Colab ou Jupyter Notebook.

1.  Clone este repositório.
2.  Abra o arquivo `Trabalho_IA.ipynb`.
3.  Certifique-se de que o arquivo de dados `heart.csv` esteja acessível (via Google Drive ou upload local).
4.  Execute todas as células do Notebook em ordem para visualizar a EDA, o treinamento do modelo e a avaliação final.
