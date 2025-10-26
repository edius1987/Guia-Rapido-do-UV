# Guia Rápido do uv
 
- Autor Edius Ferreira -  Github @edius1987

Este guia lista os comandos mais utilizados e deve ser mais que suficiente para você começar a usar o uv. Para casos de uso mais avançados, consulte a [documentação do uv](https://docs.astral.sh/uv/) e seus guias.

Última atualização para a versão 0.1.0 do uv.


## Instalação e início rápido 🚀

### Instalar o uv no sistema operacional
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Exemplo de fluxo de trabalho básico
```bash
# Criar novo projeto
uv init myproj

# Adicionar pacotes
uv add django requests "pandas>=2.3"

# Remover pacote
uv remove django

# Ver árvore de dependências
uv tree

# Executar script Python diretamente (sem ativar venv)
uv run main.py
```

### Trabalhar com versões específicas do Python
```bash
# Listar versões disponíveis
uv python list

# Instalar Python 3.12
uv python install 3.12

# Criar projeto fixado no Python 3.12
uv init myproject
uv python pin 3.12
uv add django
uv run main.py  # Instalará automaticamente py3.12 e django no venv
```

### Executar ferramentas CLI
```bash
# Executar Ruff (ou outra ferramenta)
uv tool run ruff
# ou simplesmente
uvx ruff
```

### Atualizar o uv
```bash
uv self update
```

## Criando projetos 🧱

| Comando | Descrição |
|---------|-----------|
| `uv init` | Inicializa um projeto no diretório atual |
| `uv init myproj` | Inicializa um projeto `myproj` no diretório `myproj` |
| `uv init --app --package ...` | Inicializa uma aplicação empacotável (ex: CLI, aplicação web, ...) |
| `uv init --lib --package ...` | Inicializa uma biblioteca empacotável (código que você importa) |
| `uv init --python 3.X ...`¹ | Usa Python 3.X para seu projeto |

## Gerenciando dependências do projeto 🧩

| Comando | Descrição |
|---------|-----------|
| `uv add requests` | Adiciona `requests` como dependência |
| `uv add A B C` | Adiciona A, B e C como dependências |
| `uv add "pandas>=2.3"` | Adiciona pacote com especificação de versão |
| `uv add -r requirements.txt` | Adiciona dependências do arquivo `requirements.txt` |
| `uv add --dev pytest` | Adiciona `pytest` como dependência de desenvolvimento |
| `uv run pytest` | Executa o executável `pytest` instalado no seu projeto |
| `uv remove requests` | Remove `requests` como dependência |
| `uv remove A B C` | Remove A, B, C e suas dependências transitivas |
| `uv tree` | Mostra a árvore de dependências do projeto |
| `uv lock --upgrade` | Atualiza as versões das dependências |

## Gerenciamento do ciclo de vida do projeto 🔄

| Comando | Descrição |
|---------|-----------|
| `uv build` | Constrói seu projeto empacotável |
| `uv publish` | Publica seu projeto empacotável no PyPI |
| `uv version` | Verifica a versão do seu projeto |
| `uv version --bump major` | Incrementa a versão principal (ex: 0.3.2 -> 1.0.0) |
| `uv version --bump minor --bump beta` | Incrementa versão secundária para beta (ex: 1.0.0 -> 1.1.0b1 ou 1.1.0b1 -> 1.1.0b2) |
| `uv version --bump rc` | Incrementa versão para candidato de lançamento (ex: 1.1.0b1 -> 1.1.0rc1) |
| `uv version --bump stable` | Transforma em versão estável (ex: 1.1.0rc1 -> 1.1.0) |

## Gerenciando ferramentas ⚒

| Comando | Descrição |
|---------|-----------|
| `uv tool run pytest` | Executa `pytest` em um ambiente isolado |
| `uv tool run ruff` | Executa `ruff` em um ambiente isolado |
| `uv tool run textual-demo --from textual` | Executa o comando `textual-demo` do pacote `textual` |
| `uvx ...` | Alias para `uv tool run ...` |
| `uv tool install ruff` | Instala `ruff` em ambiente isolado, mas torna-o disponível globalmente |
| `uv tool install --with dep ...` | Instala a ferramenta com dependências extras (ex: plugins) |
| `uv tool list` | Lista todas as ferramentas instaladas |
| `uv tool upgrade ruff` | Atualiza a ferramenta `ruff` |
| `uv tool upgrade --all` | Atualiza todas as ferramentas |
| `uv tool uninstall ruff` | Desinstala `ruff` |
| `uv tool install -e .`² | Instala o projeto empacotável atual em modo editável |

## Trabalhando com scripts 📜

| Comando | Descrição |
|---------|-----------|
| `uv init --script myscript.py` | Inicializa o script `myscript.py` |
| `uv init --script myscript.py --python 3.X` | Inicializa o script e fixa na versão Python 3.X |
| `uv add click --script myscript.py` | Adiciona a dependência `click` ao script |
| `uv remove click --script myscript.py` | Remove a dependência `click` do script |
| `uv run myscript.py` | Executa o script `myscript.py` (sem ativar venv manualmente) |
| `uv run --python 3.X myscript.py` | Executa o script com a versão Python especificada |
| `uv run --with click myscript.py` | Executa o script junto com a dependência `click` |

**Dica:** Torne seu script executável e adicione o shebang do uv na primeira linha:
```python
#!/usr/bin/env -S uv run
```
Assim você pode executar o script diretamente como `./myscript.py` ao invés de escrever `uv run myscript.py`.

## Gerenciar versões do Python 🐍

| Comando | Descrição |
|---------|-----------|
| `uv python list` | Lista versões do Python instaladas e versões que você pode instalar |
| `uv python install 3.X` | Instala Python 3.X (ex: `uv python install 3.12`) |
| `uv python uninstall 3.X` | Desinstala Python 3.X |
| `uv run python` | Executa seu Python padrão |
| `uv run --python 3.X python` | Executa Python 3.X |
| `uv python upgrade` | Atualiza suas versões do Python |
| `uv python pin 3.X` | Fixa uma versão específica do Python no projeto |

## Para veteranos que não aprendem truques novos 

| Comando | Descrição |
|---------|-----------|
| `uv venv path/to/.venv` | Cria um ambiente virtual em `path/to/.venv` |
| `uv pip` | Interface do pip com a velocidade do uv ⚡ |

## Comandos diversos 

| Comando | Descrição |
|---------|-----------|
| `uv format` | Formata seu código com Ruff |
| `uv help cmd` | Mostra a ajuda para o comando `cmd` |
| `uv self update` | Atualiza a versão do uv para a mais recente |
| `uv self version` | Verifica a versão do uv |

---

## Notas de rodapé

1. A opção `--python 3.X` é transversal a quase tudo no uv.
2. Se seu projeto fornece uma CLI, por exemplo, isso torna a CLI globalmente disponível no seu computador. Torná-la editável com `-e` significa que se você atualizar seu código, não precisa reinstalar explicitamente.

---

**Autor:** Edius Ferreira 
**Referência:** [Documentação do uv](https://docs.astral.sh/uv/)
