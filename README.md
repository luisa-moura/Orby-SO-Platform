# Orby Desktop

Aplicativo desktop para gestão de clientes e Ordens de Serviço de assistência técnica.

## Requisitos

- Python 3.11 ou superior
- PySide6
- openpyxl (para arquivos XLSX)

## Como executar

```powershell
.\orby_env\Scripts\python.exe main.py
```

No VS Code, selecione o interpretador `orby_env\\Scripts\\python.exe` para que o editor reconheça o PySide6.

O banco de dados `orby.db` é criado automaticamente na primeira execução, na pasta do projeto.

## Funcionalidades iniciais

- Clientes: cadastro, edição, exclusão protegida e importação CSV/XLSX.
- Ordens de Serviço: abertura, edição, atualização de status e exclusão.
- Dashboard: indicadores de OS e faturamento.
- Importação com prévia, mapeamento de colunas, validação, duplicidades, confirmação e relatório.
