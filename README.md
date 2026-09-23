# miniguia-estudos-notebooklm
Guia prático de estudos utilizando a ferramenta NotebookLM
# 🤖 Caderno Temático: Criação de Agentes de IA e Ingestão de Multimídia (PDFs, Textos e Vídeos)

Este repositório contém o registro do meu estudo prático sobre **como construir Agentes de IA capazes de ingerir dados heterogêneos (PDFs, artigos em texto e transcrições de vídeos) para responder a dúvidas de usuários com base em fontes de conhecimento personalizadas**.

---

## 🎯 Contexto e Objetivos

### Contexto Escolhido
A constante evolução das arquiteturas baseadas em LLMs transformou a forma como interagimos com o conhecimento corporativo e acadêmico. No entanto, a maioria das IAs generalistas sofre com alucinações ao tentar responder sobre dados privados ou específicos. A criação de **Agentes de IA com bases de conhecimento baseadas em RAG (Retrieval-Augmented Generation)** resolve esse problema ao restringir e direcionar o contexto de resposta do modelo.

### Objetivos de Estudo
- Compreender a arquitetura por trás dos **Agentes de IA grounded** (ancorados em dados reais).
- Aprender a preparar e ingerir **PDFs, documentos em texto e vídeos** em uma base de conhecimento utilizando a ferramenta **NotebookLM**.
- Mapear os conceitos de **Chunking, Embeddings e RAG (Retrieval-Augmented Generation)** no ciclo de vida de um Agente de IA.
- Desenvolver e testar **prompts estratégicos** para otimizar o tempo de resposta e a precisão da IA.

---

## 📚 Curadoria de Fontes

Para alimentar e treinar o modelo mental no NotebookLM, foram selecionadas 4 fontes abertas cobrindo conceitos teóricos e práticos sobre Agentes de IA e RAG:

| Fonte | Tipo | Título / Assunto | Link de Acesso |
| :--- | :--- | :--- | :--- |
| **Fonte 1** | Documentação Técnica | *Microsoft AI Agents for Beginners - Chapter 05: Agentic RAG* | [Acessar Fonte](https://github.com/microsoft/ai-agents-for-beginners/blob/main/05-agentic-rag/README.md) |
| **Fonte 2** | Artigo Técnico | *Agentic RAG: Architectures, Tradeoffs, and How to Build It* | [Acessar Fonte](https://mastra.ai/articles/agentic-rag) |
| **Fonte 3** | Guia de Arquitetura | *7 AI Open Source Libraries To Build RAG, Agents & AI Search* | [Acessar Fonte](https://dev.to/vectorpodcast/7-ai-open-source-libraries-to-build-rag-agents-ai-search-27bm) |
| **Fonte 4** | Transcrição / Artigo | *Open Source Frameworks for Building AI Agents & Multi-Document RAG* | [Acessar Fonte](https://www.firecrawl.dev/blog/best-open-source-agent-frameworks) |

---

## 🧪 Engenharia de Prompts, Testes e "Cicatrizes" (Troubleshooting)

Durante a interação com o NotebookLM, testei diversas estratégias de comunicação para extrair informações precisas sobre a construção de agentes.

### 1. Pergunta Estratégica nº 1 (Mapeamento de Arquitetura)
* **Prompt Utilizado**: *"Com base exclusivamente nas fontes fornecidas, explique o ciclo passo a passo de como um agente de IA processa um documento em PDF e uma transcrição de vídeo para responder a uma dúvida de um usuário final."*
* **Resultado Obtido**: O NotebookLM detalhou satisfatoriamente a etapa de ingestão de dados, geração de embeddings, busca vetorial e a sintese da resposta mantendo os links das citações diretas das fontes.
* **Dificuldade / Cicatriz**: Inicialmente, a IA misturou conceitos de RAG tradicional com RAG Agêntico.
* **Ajuste de Prompt (Solução)**: Refinei o prompt para: *"Forneça uma comparação direta entre RAG Tradicional e Agentic RAG ao lidar com múltiplos formatos de arquivo, destacando o papel da tomada de decisão dinâmica do agente."*

### 2. Pergunta Estratégica nº 2 (Ingestão Multimídia e Limitações)
* **Prompt Utilizado**: *"Quais são os principais desafios técnicos ao fazer um Agente de IA processar dados provenientes de vídeos em comparação com arquivos PDF estruturados?"*
* **Resultado Obtido**: A IA identificou que vídeos exigem etapas intermediárias de conversão (Speech-to-Text) e tratamento de timestamps para garantir que o trecho correto do vídeo seja citado na resposta.
* **Dificuldade / Cicatriz**: O modelo gerou uma resposta muito genérica quando não restringi o foco ao contexto de busca semântica.
* **Ajuste de Prompt (Solução)**: *"A partir das fontes do caderno, liste 3 gargalos de precisão na conversão de áudio/vídeo para vetores de busca e como a verificação de Groundedness ajuda a mitigar esses erros."*

---

## 📖 Miniguia de Estudo (Entrega Final)

### 📂 1. Resumo Estruturado do Assunto

#### Como um Agente de IA Estuda Fontes Privadas?
1. **Ingestão e Pré-processamento**: O conteúdo (PDF, texto ou áudio extraído de vídeo) é limpo e formatado.
2. **Chunking (Segmentação)**: O texto é dividido em blocos menores de informação.
3. **Vetorização (Embeddings)**: Cada bloco é convertido em um vetor numérico que captura seu significado semântico.
4. **Armazenamento Vetorial**: Os vetores são indexados em um banco de dados vetorial.
5. **Orquestração pelo Agente**: Quando o usuário faz uma pergunta, o agente:
   - Analisa a intenção da pergunta.
   - Reescreve ou divide a query em subperguntas (se necessário).
   - Busca os blocos de texto mais relevantes na base de conhecimento.
   - Consolida a resposta final fundamentada (**Grounded Answer**), reduzindo drasticamente o risco de alucinações.

---

### 📚 2. Glossário de Conceitos Fundamentais

- **LLM (Large Language Model)**: Modelo de linguagem treinado em grandes volumes de dados que gera texto e raciocina sobre contexto.
- **RAG (Retrieval-Augmented Generation)**: Técnica que combina busca em bases de dados externas com a geração de texto por LLMs para responder dúvidas com precisão factual.
- **Agentic RAG**: Evolução do RAG onde um Agente autônomo possui capacidade de planejamento, escolha de ferramentas e repetição iterativa de buscas até encontrar a resposta ideal.
- **Chunking**: Processo de quebrar documentos longos em pedaços menores para que possam ser processados de forma eficiente pelas janelas de contexto do modelo.
- **Embeddings**: Representações numéricas (vetores) de palavras ou frases que permitem ao computador comparar a proximidade de significado entre textos.
- **Groundedness (Ancoragem)**: Métrica que avalia o quanto a resposta gerada por uma IA é diretamente sustentada pelo contexto de fatos fornecido nas fontes.
- **Troubleshooting de Prompts**: Técnica de ajuste contínuo e refatoração de instruções para contornar ambiguidades ou limitações de respostas de um modelo de linguagem.

---

### ⚙️ 3. Prompts Reutilizáveis para Revisões Futuras

Guarde estes prompts para utilizar quando precisar estudar novos assuntos com o NotebookLM ou outro Agente de IA:

* **Prompt de Síntese Temática**:
  > *"Atue como um especialista técnico. Resuma os conceitos fundamentais do material fornecido em formato de tópicos (bullet points), destacando a arquitetura básica, os pré-requisitos e os casos de uso práticos."*

* **Prompt de Extração de Fluxos de Trabalho**:
  > *"Crie um passo a passo em formato de lista numerada descrevendo o processo de execução de [Inserir Tecnologia/Conceito] conforme descrito nas fontes do caderno."*

* **Prompt de Teste de Conhecimento e Autoavaliação**:
  > *"Com base no material de estudo, elabore 5 perguntas de múltipla escolha com gabarito comentado ao final para testar meu conhecimento sobre este tema."*

* **Prompt de Criação de FAQ**:
  > *"Liste as 5 dúvidas mais frequentes que um desenvolvedor iniciante teria ao implementar este projeto e responda cada uma de forma objetiva usando apenas dados das fontes."*

---

### 👤 Autor
Desenvolvido como projeto de estudo para o Desafio de Projeto da **DIO (Digital Innovation One)**.
