![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=flat-square&logo=python&logoColor=white)
![Data Source](https://img.shields.io/badge/Data-Yahoo_Finance-1db954?style=flat-square&logo=yahoo&logoColor=white)
![AI Model](https://img.shields.io/badge/AI-Llama_3.1-532187?style=flat-square&logo=meta&logoColor=white)
![Status](https://img.shields.io/badge/Status-PoC_(Prototype)-orange?style=flat-square)

# Análise de Cenário Financeiro via IA: Protótipo para o Agronegócio

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seixobr/ai-financial-scenario-analysis/blob/main/ai_financial_scenario_analysis.ipynb)

## Resumo Executivo
Este projeto estabelece uma **Prova de Conceito (PoC)** de um fluxo automatizado de análise financeira direcionado ao setor de Agronegócio brasileiro. Através da integração de IA Generativa com dados de mercado em tempo real, a ferramenta simula um cenário de consultoria, correlacionando a exposição cambial (**USD/BRL**) com a volatilidade de commodities (**Petróleo WTI**).

O objetivo é demonstrar como dados não estruturados (contexto de voz do produtor) e indicadores financeiros estruturados podem ser processados para gerar insights estratégicos qualitativos para exportadores do Vale do São Francisco.

## Contexto de Negócio
Exportadores no Nordeste brasileiro operam sob um framework de risco duplo:
1.  **Exposição de Receita (Long USD):** A rentabilidade é altamente sensível à taxa spot do par USD/BRL.
2.  **Exposição de Custos (Short Energia):** Os custos logísticos (frete marítimo e rodoviário) apresentam forte correlação com os preços internacionais do petróleo (WTI/Brent).

Este protótipo endereça a necessidade de síntese rápida dessas variáveis, fornecendo uma avaliação qualitativa do ambiente macroeconômico e seus impactos nas margens operacionais.

## Arquitetura Técnica
O fluxo de trabalho implementa um pipeline de processamento sequencial:

1.  **Processamento de Entrada (ASR):**
    *   **Motor:** OpenAI Whisper (Modelo Base).
    *   **Função:** Transcrição do contexto de negócio fornecido pelo produtor via áudio para texto.
2.  **Coleta de Dados de Mercado (ETL):**
    *   **Fonte:** API Yahoo Finance (`yfinance`).
    *   **Indicadores-Chave:**
        *   `BRL=X`: Taxa de Câmbio Dólar/Real (Proxy de Receita).
        *   `CL=F`: Futuros de Petróleo WTI (Proxy de Custo Logístico).
3.  **Motor de Inferência (LLM):**
    *   **Modelo:** Llama-3.1-8b-instant (via API Groq).
    *   **Método:** O modelo é instanciado com uma persona de "Consultor Financeiro Sênior" e alimentado com dados de mercado atualizados para gerar uma análise contextualizada.
4.  **Síntese de Saída (TTS):**
    *   **Motor:** gTTS (Google Text-to-Speech).
    *   **Entrega:** Resumo executivo em áudio da análise estratégica.

## Pré-requisitos do Projeto
Para replicar este ambiente, são necessárias as seguintes dependências:
*   Ambiente Python 3.10+.
*   Chave de API para Groq Cloud.
*   Bibliotecas: `openai-whisper`, `groq`, `yfinance`, `gTTS`.

## Instruções de Uso
1.  **Acesso Rápido:** Clique no botão "Open in Colab" no topo deste arquivo para executar o projeto diretamente no navegador.
2.  **Execução Local:**
    *   Clone o repositório: `git clone https://github.com/seixobr/ai-financial-scenario-analysis.git`
    *   Instale as dependências: `pip install -r requirements.txt`
    *   Certifique-se de configurar suas chaves de API de forma segura.

## Aviso Legal (Disclaimer)
Este software foi desenvolvido estritamente para **fins educacionais**. Trata-se de um protótipo para demonstração de orquestração de dados e engenharia de prompt. O sistema fornece uma **avaliação qualitativa** baseada em um recorte momentâneo de dados de mercado e não constitui, sob hipótese alguma, aconselhamento financeiro profissional, recomendação de investimento ou modelagem quantitativa de risco.
