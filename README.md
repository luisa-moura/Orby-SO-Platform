# Orby — Gestão Operacional para Pequenas Empresas e Serviços

Sistema desktop intuitivo e de alta performance voltado para pequenas empresas, prestadores de serviços e assistências técnicas. O sistema conta com controle completo de clientes, equipamentos e ordens de serviço (OS), além de autenticação com controle de acesso baseado em perfis (RBAC), importação em lote e interface gráfica moderna no estilo Frutiger Aero.

## Funcionalidades

- Autenticação & Controle de Acesso (RBAC):
  - Gestor: Acesso irrestrito (dashboard financeiro, clientes, equipamentos, OS e importação).
  - Técnico: Acesso operacional focado em ordens de serviço, andamentos, laudos e equipamentos.
  - Atendente: Recepção e cadastro de clientes e entrada de equipamentos e OS (com diagnóstico técnico protegido).
- Gestão de Ordens de Serviço (OS):
  - Abertura, consulta, atualização de status com linha do tempo de histórico e encerramento.
  - Registro de diagnóstico técnico e valor final.
- Gestão de Clientes e Equipamentos:
  - Cadastro detalhado e vínculo direto entre clientes e equipamentos/máquinas.
  -Exclusão com integridade referencial protegida.
- Importação de Dados em Lote:
  - Suporte a arquivos .csv e .xlsx.
  - Mapeamento dinâmico de colunas, detecção de duplicidades e relatório de importação.
- Dashboard e Métricas:
  - Indicadores operacionais e controle de faturamento em tempo real.
- Design & Usabilidade:
  - Interface com tema Claro e Escuro.
  - Ícones vetoriais modernos e inicialização em menos de 3 segundos.
    

## Como executar o projeto

### Pré-requisitos

- Python 3.11 ou superior;
- Gerenciador de pacotes `pip`;
- Sistema operacional compatível com Python e PySide6.

### 1. Clonar o repositório

Substitua o endereço abaixo pela URL real do repositório:

```bash
git clone https://github.com/luisa-moura/Orby.git
cd Orby
```

### 2. Criar e ativar um ambiente virtual

**Windows (PowerShell):**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**Linux/macOS:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Instalar as dependências

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Executar a aplicação

Na raiz do projeto, execute:

```bash
python main.py
```

No Windows, se o projeto já estiver configurado com o ambiente `orby_env`, também é possível iniciar a aplicação com:

```powershell
.\orby_env\Scripts\python.exe main.py
```

> **Importante:** execute o comando a partir da raiz do projeto, onde `main.py` e o pacote `orby` estão disponíveis. O ponto de entrada inicializa a interface Qt, prepara o banco de dados e o repositório e apresenta a tela de login.

## Database

Orby utiliza **SQLite**. O banco é inicializado automaticamente pela aplicação. De acordo com a configuração documentada no projeto, o arquivo `orby.db` é criado na pasta do projeto na primeira execução.

O armazenamento contempla informações relacionadas a usuários, clientes, equipamentos, ordens de serviço e histórico de alterações de status.

## Importação de clientes

A ferramenta de importação aceita arquivos `.csv` e `.xlsx`. O fluxo inclui visualização prévia, mapeamento de colunas, validação dos dados, identificação de possíveis duplicidades, confirmação e relatório do resultado.

O projeto inclui o arquivo [`clientes_teste_importacao.csv`](clientes_teste_importacao.csv) como exemplo para testes. Antes de confirmar uma importação, confira os dados e o mapeamento exibidos pela aplicação. Prefira utilizar informações fictícias durante a validação.


## Testes e validação

O material fornecido inclui um CSV de exemplo para validar o fluxo de importação. Para testes manuais, recomenda-se verificar:

- inicialização da aplicação e acesso pela tela de login;
- cadastro, edição e exclusão protegida de clientes;
- associação entre clientes, equipamentos e ordens de serviço;
- atualização de status e registro do histórico da OS;
- importação de CSV/XLSX, incluindo validação e duplicidades;
- apresentação dos indicadores do dashboard.

  ### - Credenciais de Acesso (Ambiente de Testes)

O sistema inicializa automaticamente o banco de dados `orby.db` com três perfis pré-configurados para validação:

| **Perfil** | **Usuário** | **Senha** | **Permissões** |
|:---|:---|:---|:---|
| **Gestor** | `admin` | `admin123` | Acesso completo a todas as funções e métricas |
| **Técnico** | `tecnico` | `tec123` | Edição de OS, diagnósticos e equipamentos |
| **Atendente** | `atendente` | `atende123` | Cadastro de clientes, equipamentos e abertura de OS |


## Estrutura do Projeto

```text
.
├── orby/                         # Pacote principal da aplicação
│   ├── core/                     # Componentes de domínio, conforme a versão do projeto
│   ├── ui/                       # Interface gráfica e componentes visuais
│   ├── database.py               # Inicialização e acesso ao banco de dados
│   ├── importer.py               # Importação de dados
│   ├── repository.py              # Acesso e persistência de dados
│   └── main_window.py             # Janela principal
├── main.py                       # Ponto de entrada da aplicação
├── requirements.txt              # Dependências Python
├── clientes_teste_importacao.csv # Dados de exemplo para importação
├── Orby.spec                     # Configuração do PyInstaller
├── Orby.exe                      # Executável para Windows
├── orby.db                       # Banco de dados local (pode conter dados operacionais)
└── README.md                     # Documentação do projeto
```

A árvore apresenta os componentes principais referenciados pelos arquivos fornecidos. A estrutura exata pode variar entre versões; mantenha os diretórios e módulos existentes no repositório ao executar o projeto.
