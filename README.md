# 🧬 NLP PubMed Analytics Pipeline

Um pipeline completo, otimizado e resiliente de Processamento de Linguagem Natural (PLN) para extração, processamento e análise de abstracts de artigos científicos da base de dados médica PubMed.

## 🚀 Visão Geral
Este projeto foi desenvolvido com foco em Engenharia Analítica e boas práticas de software. O pipeline coleta dados de quatro especialidades médicas (Cardiologia, Oncologia, Neurologia e Dermatologia) e aplica técnicas de Machine Learning tradicional e Deep Learning (Transformers) para extrair insights automatizados.

## 🧠 Funcionalidades e Arquitetura
O código é orientado a objetos e estruturado em uma classe unificada (`NLPPipeline`) com as seguintes etapas:

1. **Data Ingestion:** Coleta automatizada via API do NCBI (Biopython) com lógica de *retry* para tolerância a falhas.
2. **Pré-processamento:** Limpeza de texto, remoção de caracteres, stopwords médicas customizadas e lematização otimizada com `@lru_cache`.
3. **Vetorização:** Geração de embeddings semânticos utilizando `sentence-transformers` (`all-MiniLM-L6-v2`) com *fallback* automático para `TF-IDF`.
4. **Classificação:** Modelos `Random Forest` e `GaussianNB`, além de classificação *Zero-Shot* via `BART`.
5. **Modelagem de Tópicos (LDA):** Descoberta de clusters de palavras utilizando `Gensim`.
6. **Sumarização Automática:** Geração de resumos abstrativos e extrativos (LSA e Transformers) com rotinas de contingência.

> **Destaque Técnico:** O projeto possui um `PackageManager` customizado. Se uma biblioteca pesada (como PyTorch ou Transformers) falhar por problemas de infraestrutura local, o código não quebra; ele executa automaticamente algoritmos de fallback estatísticos para entregar a análise.

## 📁 Arquivos Incluídos no GitHub
- `Davi_pln_pubmed.ipynb`: notebook principal do projeto.
- `.env.example`: modelo de variáveis de ambiente.
- `README.md`: documentação do projeto.
- `requirements.txt`: dependências necessárias.
- `.gitignore`: regras para manter arquivos sensíveis e temporários fora do repositório.

## 🛠️ Como Executar o Projeto

1. Clone o repositório:
```bash
git clone https://github.com/seu-usuario/nlp-pubmed-analytics.git
cd nlp-pubmed-analytics
```

2. Crie e ative um ambiente virtual:
```bash
python -m venv .venv
# No Windows
.\.venv\Scripts\activate
# No Linux/Mac
# source .venv/bin/activate
```

3. Instale as dependências:
```bash
pip install -r requirements.txt
```

4. Configure as variáveis de ambiente:
```bash
copy .env.example .env
```
No Windows, edite o arquivo `.env` e adicione sua chave do NCBI:
```bash
ENTREZ_API_KEY=sua_chave_aqui_sem_aspas
```

5. Execute o Jupyter Notebook:

Abra o arquivo `Davi_pln_pubmed.ipynb` no Jupyter e execute todas as células.

## ⚠️ Observações de Segurança
- Não suba o arquivo `.env` para o GitHub.
- O `.gitignore` já bloqueia o `.env`, ambientes virtuais e outros artefatos temporários.
- Apenas o notebook `Davi_pln_pubmed.ipynb` está liberado para ser adicionado ao repositório.

## ✅ Checklist de Padrão Ouro
- [x] `.gitignore` configurado corretamente
- [x] `.env.example` criado
- [x] `requirements.txt` criado
- [x] `README.md` criado
- [x] Apenas `Davi_pln_pubmed.ipynb` exposto para commit

## 💡 Próximos Passos
- Verifique se o `.env` não está rastreado com `git status`
- Adicione os arquivos selecionados com:
```bash
git add .gitignore .env.example requirements.txt README.md Davi_pln_pubmed.ipynb
```
- Faça o commit e o push para o GitHub.
