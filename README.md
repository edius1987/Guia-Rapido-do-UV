# Guia Rápido doUV
Guia Rápido do UV


# Guia Rápido do uv 🚀

[![uv](https://img.shields.io/badge/uv-0.9.0-blue)](https://docs.astral.sh/uv/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Portuguese](https://img.shields.io/badge/lang-pt--BR-yellow.svg)](README.md)

Um guia rápido e prático do **uv**, o gerenciador de pacotes e projetos Python ultrarrápido, escrito em Rust. Este repositório contém um cheatsheet completo em Markdown, LaTeX e PDF para referência rápida.

## 📖 Sobre o uv

O **uv** é uma ferramenta moderna e extremamente rápida para gerenciamento de pacotes e projetos Python, desenvolvida pela [Astral](https://astral.sh/). Ele substitui ferramentas como `pip`, `pip-tools`, `pipx`, `poetry`, `pyenv` e `virtualenv` com uma única interface unificada.

### ✨ Por que usar o uv?

- ⚡ **10-100x mais rápido** que pip
- 🔧 **Tudo em um**: gerencia projetos, pacotes, versões do Python e ferramentas
- 🦀 **Escrito em Rust**: performance e confiabilidade
- 🎯 **Interface simples**: comandos intuitivos e consistentes
- 📦 **Compatível com pip**: usa o mesmo ecossistema PyPI

## 🚀 Instalação

### Linux/macOS
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Windows (PowerShell)
```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### Verificar instalação
```bash
uv --version
```

## 📚 Conteúdo deste Repositório

Este repositório oferece o guia rápido do uv em diferentes formatos:

- **[Markdown](guia-rapido-uv.md)**: Para leitura no GitHub ou em editores de texto
- **[LaTeX](guia-rapido-uv.tex)**: Para edição no Overleaf ou compilação local
- **[PDF](guia-rapido-uv.pdf)**: Versão pronta para impressão (1 página A4, 2 colunas)

## 🎯 Exemplos Rápidos

### Criar um novo projeto
```bash
uv init myproject
cd myproject
```

### Adicionar dependências
```bash
uv add django requests "pandas>=2.3"
```

### Executar código sem ativar venv
```bash
uv run main.py
```

### Trabalhar com versão específica do Python
```bash
uv python install 3.12
uv python pin 3.12
uv add fastapi
uv run main.py  # Instalará automaticamente Python 3.12 e FastAPI
```

### Executar ferramentas CLI sem instalar globalmente
```bash
uvx ruff check .
uvx black .
uvx pytest
```

## 📋 Comandos Principais

### Gerenciamento de Projetos
```bash
uv init              # Inicializa projeto
uv add <package>     # Adiciona dependência
uv remove <package>  # Remove dependência
uv tree             # Mostra árvore de dependências
uv run <script>     # Executa script no ambiente do projeto
```

### Gerenciamento do Python
```bash
uv python list      # Lista versões disponíveis
uv python install   # Instala versão do Python
uv python pin       # Fixa versão no projeto
```

### Ferramentas
```bash
uv tool run <tool>  # Executa ferramenta isolada
uvx <tool>         # Atalho para uv tool run
uv tool install    # Instala ferramenta globalmente
```

### Manutenção
```bash
uv self update     # Atualiza o uv
uv lock --upgrade  # Atualiza dependências do projeto
```

## 📖 Documentação Completa

Para informações detalhadas, consulte:

- 📄 **[Guia completo em Markdown](guia-rapido-uv.md)**
- 🌐 **[Documentação oficial do uv](https://docs.astral.sh/uv/)**

## 🎓 Casos de Uso

### Desenvolvimento de Aplicações
```bash
uv init --app myapp
uv python pin 3.12
uv add fastapi uvicorn sqlalchemy
uv run uvicorn main:app --reload
```

### Criação de Bibliotecas
```bash
uv init --lib mylib
uv add --dev pytest black ruff
uv run pytest
```

### Scripts Standalone
```bash
uv init --script analysis.py --python 3.12
uv add --script analysis.py pandas matplotlib
uv run analysis.py
```

Ou adicione o shebang no script:
```python
#!/usr/bin/env -S uv run
# /// script
# dependencies = ["pandas", "matplotlib"]
# ///

import pandas as pd
# seu código aqui...
```

E execute diretamente:
```bash
chmod +x analysis.py
./analysis.py
```

## 🔄 Migração de Outras Ferramentas

### De pip + requirements.txt
```bash
uv init
uv add -r requirements.txt
```

### De Poetry
```bash
uv init
# Copie as dependências do pyproject.toml
uv add <suas-dependências>
```

### De Pipenv
```bash
uv init
uv add $(cat Pipfile | grep -A 100 "[packages]" | grep "=" | cut -d' ' -f1)
```

## 🤝 Contribuindo

Contribuições são bem-vindas! Se você encontrou algum erro ou tem sugestões de melhorias:

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona nova feature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

## 📝 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 🙏 Créditos

- **uv**: Desenvolvido por [Astral](https://astral.sh/)
- **Tradução e adaptação**: Comunidade Python Brasil

## 🔗 Links Úteis

- [Site oficial do uv](https://astral.sh/uv/)
- [Documentação completa](https://docs.astral.sh/uv/)
- [Repositório no GitHub](https://github.com/astral-sh/uv)
- [Guia de migração](https://docs.astral.sh/uv/guides/migration/)
- [Blog da Astral](https://astral.sh/blog)

## ⭐ Apoie o Projeto

Se este guia foi útil para você, considere:

- ⭐ Dar uma estrela neste repositório
- 🐦 Compartilhar nas redes sociais
- 📢 Recomendar para colegas desenvolvedores
- 🤝 Contribuir com melhorias

---

<div align="center">

**Feito com ❤️ pela comunidade Python Brasil**


</div>
