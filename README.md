AluraLangchain – Agente de IA para RH
Este repositório contém experimentos e projetos do curso de LangChain, com destaque para um agente de IA para RH, capaz de auxiliar em tarefas de triagem e análise de perfis de candidatos usando LLMs e ferramentas do LangChain.

🎯 Objetivo do agente de RH
O agente de RH foi criado para:

Receber informações de candidatos (dados pessoais, experiências, habilidades, formação).

Analisar o perfil com base em critérios pré-definidos (por exemplo, vaga alvo, stack desejada, senioridade).

Gerar insights em linguagem natural para apoiar decisões do time de recrutamento, como:

Pontos fortes do candidato.

Riscos ou gaps em relação à vaga.

Sugestões de encaixe em outros cargos/perfis.

🧠 Arquitetura em alto nível
O agente de RH é construído em cima de:

Python como linguagem principal.

LangChain para orquestrar:

LLM (API OpenAI/GPT).

Cadeias de prompts.

Ferramentas de leitura/manipulação de dados.

(Opcional, se você utilizou) Arquivos CSV/JSON com dados de candidatos para testes locais.

Fluxo geral:

Entrada de dados do candidato (via prompt, arquivo ou código).

Montagem de um contexto estruturado (perfil do candidato + critérios da vaga).

Envio desse contexto para o agente configurado no LangChain.

Geração de uma análise em linguagem natural, que pode incluir recomendações ou classificação.

⚙️ Configuração do ambiente
Clone o repositório

bash
git clone https://github.com/Miked0/AluraLangchain.git
cd AluraLangchain
Crie e ative um ambiente virtual

bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# Linux / macOS
source .venv/bin/activate
Instale as dependências

Se existir requirements.txt:

bash
pip install -r requirements.txt
Caso contrário, instale os principais pacotes:

bash
pip install langchain openai python-dotenv
Configure a chave da OpenAI

Crie um arquivo .env na raiz do projeto:

text
OPENAI_API_KEY=suachaveaqui
Ou defina como variável de ambiente:

bash
export OPENAI_API_KEY=suachaveaqui
🧩 Estrutura do projeto (sugestão)
Adapte para refletir o que você tem hoje:

text
AluraLangchain/
├─ agentes/
│  ├─ agente_rh.py        # Lógica principal do agente de RH
│  ├─ prompts_rh.py       # Prompts e templates usados pelo agente
├─ dados/
│  ├─ candidatos_exemplo.csv  # Dados de teste (opcional)
├─ main_rh.py             # Script para rodar o agente de RH via terminal
├─ README.md
agente_rh.py: define o agente do LangChain, ferramentas e cadeia de decisão.

prompts_rh.py: concentra os templates de prompt, instruções de persona e critérios de avaliação.

main_rh.py: ponto de entrada para testes rápidos do agente.

🛠️ Como rodar o agente de RH
Exemplo de execução via script (ajuste para o nome real do seu arquivo):

bash
python main_rh.py
Você pode implementar algo como:

python
from agentes.agente_rh import criar_agente_rh

if __name__ == "__main__":
    agente = criar_agente_rh()
    pergunta = input("Descreva o perfil do candidato ou cole o currículo:\n")
    resposta = agente.invoke({"input": pergunta})
    print("\nAnálise do RH:")
    print(resposta)
🧩 Comportamento do agente
Alguns comportamentos típicos que este agente pode ter (e que você pode ajustar nos prompts):

Classificar o candidato em níveis (júnior, pleno, sênior) com base na experiência descrita.

Indicar se o perfil é “alinhado”, “parcialmente alinhado” ou “não alinhado” com uma vaga descrita no contexto.

Listar pontos fortes (hard e soft skills) percebidos na descrição.

Sugerir perguntas que o recrutador pode fazer na entrevista, com base em possíveis gaps.

🧪 Exemplos de uso
1. Avaliação básica de candidato
Entrada (resumida):

Candidato com 2 anos de experiência em suporte técnico, conhecimento em Python, automação de relatórios, atendimento ao cliente e uso de CRM.

Saída esperada:

Nível sugerido: júnior / júnior+

Pontos fortes: experiência com cliente, automação, familiaridade com tecnologia.

Sugestão de vaga: suporte técnico, analista júnior de operações/CS, função híbrida de CX + dados.

2. Match com uma vaga específica
Você pode incluir no prompt:

Descrição da vaga (stack, responsabilidades, requisitos).

Perfil do candidato.

O agente responde:

Grau de aderência à vaga.

Riscos (ex.: “tem pouca experiência em X, mas forte em Y”).

Recomendações para desenvolvimento (skills a desenvolver para encaixar melhor).

🧱 Próximos passos e ideias de evolução
Algumas ideias para evoluir o agente de RH dentro deste repositório:

Integrar um CSV de candidatos e criar um agente que percorre a base e ranqueia perfis para determinada vaga.

Adicionar memória conversacional (manter histórico de candidatos já avaliados).

Conectar com APIs externas (ex.: LinkedIn, ATS) para buscar dados reais de perfis.

Criar uma interface simples com Streamlit para que o time de RH use sem precisar rodar código.

📚 Referências e inspiração
Curso LangChain: desenvolva agentes de inteligência artificial – Alura.

Curso LangChain e Python: criando ferramentas com a OpenAI.

Formação Criando agentes de IA com LangChain e LangGraph.

Repositórios oficiais da Alura com exemplos de agentes.
