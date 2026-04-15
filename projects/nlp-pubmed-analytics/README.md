# 🧬 NLP PubMed Analytics Pipeline

Um pipeline completo, otimizado e resiliente de Processamento de Linguagem Natural (PLN) para extracao, processamento e analise de abstracts de artigos cientificos da base de dados medica PubMed.

## 🚀 Visao Geral
Este projeto foi desenvolvido com foco em Engenharia Analitica e boas praticas de software. O pipeline coleta dados de quatro especialidades medicas (Cardiologia, Oncologia, Neurologia e Dermatologia) e aplica tecnicas de Machine Learning tradicional e Deep Learning (Transformers) para extrair insights automatizados.

## 🧠 Funcionalidades e Arquitetura
O codigo e orientado a objetos e estruturado em uma classe unificada (`NLPPipeline`) com as seguintes etapas:

1. **Data Ingestion:** Coleta automatizada via API do NCBI (Biopython) com logica de retry para tolerancia a falhas.
2. **Pre-processamento:** Limpeza de texto, remocao de caracteres, stopwords medicas customizadas e lematizacao otimizada com `@lru_cache`.
3. **Vetorizacao:** Geracao de embeddings semanticos utilizando `sentence-transformers` (`all-MiniLM-L6-v2`) com fallback automatico para `TF-IDF`.
4. **Classificacao:** Modelos `Random Forest` e `GaussianNB`, alem de classificacao Zero-Shot via `BART`.
5. **Modelagem de Topicos (LDA):** Descoberta de clusters de palavras utilizando `Gensim`.
6. **Sumarizacao Automatica:** Geracao de resumos abstrativos e extrativos (LSA e Transformers) com rotinas de contingencia.

> **Destaque Tecnico:** O projeto possui um `PackageManager` customizado. Se uma biblioteca pesada (como PyTorch ou Transformers) falhar por problemas de infraestrutura local, o codigo nao quebra; ele executa automaticamente algoritmos de fallback estatisticos para entregar a analise.

## 📁 Arquivos deste Projeto
- `Davi_pln_pubmed.ipynb`: notebook principal do projeto.
- `patch_embedding_notebook.py`: script utilitario para ajuste de embeddings no notebook.
- `README.md`: documentacao do projeto.

## 🛠️ Como Executar o Projeto

1. Volte para a raiz do repositorio e crie/ative o ambiente virtual:
```bash
python -m venv .venv
# Windows
.\.venv\Scripts\activate
# Linux/Mac
# source .venv/bin/activate
```

2. Instale as dependencias da raiz do repositorio:
```bash
pip install -r requirements.txt
```

3. Abra e execute o notebook deste projeto:
- `projects/nlp-pubmed-analytics/Davi_pln_pubmed.ipynb`
