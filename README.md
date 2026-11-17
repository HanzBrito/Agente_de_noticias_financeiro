# 📰 Agente de Notícias Financeiro

Agente de IA, feito com [CrewAI](https://docs.crewai.com), que busca, analisa e resume notícias do mercado financeiro. <ajuste: o que ele entrega no final, por exemplo um relatório em .md>

## Estrutura do projeto

```
agente_noticias/
├── .env                      # Variáveis locais (LLM, chaves). NÃO versionar
├── .gitignore
├── pyproject.toml            # Dependências e metadados do projeto
├── README.md
├── knowledge/                # Arquivos de contexto para os agentes (opcional)
├── tests/
└── src/
    └── agente_noticias/
        ├── main.py           # Ponto de entrada: define os inputs e inicia a crew
        ├── crew.py           # Monta a crew: liga agentes e tarefas
        ├── config/
        │   ├── agents.yaml   # Papel, objetivo e histórico de cada agente
        │   └── tasks.yaml    # Descrição e saída esperada de cada tarefa
        └── tools/
            └── custom_tool.py  # Ferramentas customizadas (busca, APIs etc.)
```

| Arquivo/Pasta | Para que serve |
|---|---|
| `config/agents.yaml` | Define **quem** são os agentes (função, objetivo, backstory). |
| `config/tasks.yaml` | Define **o que** cada agente deve fazer e o formato da resposta. |
| `crew.py` | Conecta agentes e tarefas e define como são executados. |
| `main.py` | Roda a crew; é aqui que você altera os inputs (ex.: tema ou ativo). |
| `tools/` | Ferramentas que os agentes podem usar. |
| `.env` | Configuração local do LLM e chaves de API. |

## Como criar e executar

```bash
# 1. Criar o projeto (já feito; só para referência)
crewai create crew agente_noticias

# 2. Entrar na pasta e instalar as dependências
cd agente_noticias
crewai install

# 3. Executar o agente
crewai run
```

## Configuração do `.env`

O `.env` fica **apenas na sua máquina** e diz à CrewAI qual LLM usar. Exemplos:

```env
# LLM local via Ollama
MODEL=ollama/<modelo>
API_BASE=http://localhost:11434

# ou LLM em nuvem
# MODEL=<provedor>/<modelo>
# <PROVEDOR>_API_KEY=sua_chave_aqui
```

> ⚠️ Nunca suba o `.env` para o GitHub. Confirme que ele está no `.gitignore`.

## Requisitos
- Python <versão do seu pyproject.toml>
- [uv](https://docs.astral.sh/uv/) (usado pelo `crewai install`)
- <LLM local rodando, se for o caso>
