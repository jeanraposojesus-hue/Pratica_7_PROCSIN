# Projeto de Filtros FIR - Prática 7 🎛️

**Disciplina:** Processamento de Sinais I  
**Instituição:** CEFET/RJ  
**Autor:** Jean Raposo Soares de Jesus  
**Professor:** Rafael S. Chaves

![Status](https://img.shields.io/badge/Status-Concluído-success)
![Linguagem](https://img.shields.io/badge/Linguagem-Python_/_MATLAB-blue) ## 📋 Descrição do Projeto
Este repositório contém as implementações referentes à Aula Prática 7 de Processamento de Sinais I. O objetivo principal deste projeto é a implementação do zero de filtros digitais FIR (Finite Impulse Response), sem a utilização de funções prontas de bibliotecas para o cálculo dos coeficientes. O projeto aborda desde o desenvolvimento matemático dos filtros com diferentes janelamentos até a aplicação em um sinal de áudio corrompido por ruídos e interferências.

## 🚀 Funcionalidades e Etapas Implementadas

### 1. Projeto de Filtros FIR Básicos
Implementação de filtros FIR considerando uma frequência de amostragem ($f_s$) de 20.000 Hz e ordens $M \in \{20, 50, 100\}$. Foram aplicadas as janelas Retangular, Triangular, Bartlett, Hamming, Hann e Blackman para os seguintes tipos de filtros:
* **Passa-baixas:** $f_c = 1000$ Hz
* **Passa-altas:** $f_c = 2000$ Hz
* **Passa-faixas:** $f_{c1} = 500$ Hz e $f_{c2} = 2000$ Hz
* **Rejeita-faixas:** $f_{c1} = 1000$ Hz e $f_{c2} = 2500$ Hz

*Saídas geradas: Resposta ao impulso, diagrama de polos e zeros e resposta em frequência*.

### 2. Filtros a Partir de Respostas de Módulo Ideais
Derivação analítica da resposta ao impulso para três módulos de filtros ideais fornecidos teoricamente. Posteriormente, os filtros foram projetados com ordens $M \in \{50, 100\}$, utilizando diferentes técnicas de janelamento, com a respectiva análise das respostas e raízes.

### 3. Recuperação de Sinal de Áudio (`handel.wav`)
Aplicação prática de filtragem em um sinal original $x(t)$ que foi intencionalmente corrompido pela seguinte equação matemática:
$y(t) = x(t) + 0.05 \cos(200\pi t) + 0.075 \sin(4000\pi t) + n(t)$
* Onde há interferência de baixa frequência ($0.05 \cos(200\pi t)$), tom de alta frequência ($0.075 \sin(4000\pi t)$) e ruído branco com diferentes variâncias ($\sigma^2 \in \{10^{-2}, 10^{-1}, 1\}$).

**Nesta etapa foram realizadas:**
* **Filtragem Digital:** Remoção do ruído projetando o sistema FIR e avaliando a resposta em frequência.
* **Análise de Desempenho:** Comparação no domínio do tempo e frequência entre o sinal corrompido e o sinal recuperado $\hat{x}(t)$.
* **Métricas Quantitativas:** Avaliação do sistema utilizando SNR (Relação Sinal-Ruído) e MSE (Erro Quadrático Médio).
* **Avaliação Subjetiva:** Análise da inteligibilidade e percepção do áudio filtrado.
* **Quantização:** Teste de robustez dos filtros simulando coeficientes com representação em $b \in \{2, 4, 8, 16\}$ bits, observando o impacto na estabilidade e distorção.
* *Todas as análises foram comparadas de forma crítica com os filtros IIR desenvolvidos na Aula Prática 6*.

## 📁 Estrutura do Repositório

```text
├── src/
│   ├── filtros.py          # (Ou .m) Classes/Funções de implementação manual dos filtros FIR
│   ├── janelas.py          # Algoritmos das janelas de Bartlett, Hamming, Hann, etc.
│   ├── audio_process.py    # Script de processamento do handel.wav e cálculo de SNR/MSE
├── data/
│   └── handel.wav          # Áudio original utilizado na Parte 3
├── plots/                  # Gráficos gerados (Polos e zeros, respostas em frequência)
└── relatorio.pdf           # Discussão dos resultados e comparações com a Prática 6
