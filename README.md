# DataOps Mini Lab - Parte 2

Pipeline de ingestao com geracao de CSV sintetico (~10 MB), orquestracao com Temporal e persistencia em MongoDB Atlas.

## Setup

1. Criar e ativar ambiente virtual

### PowerShell

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### Git Bash

```bash
python -m venv .venv
source .venv/Scripts/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

2. Configurar variaveis em `.env`

```env
MONGODB_URI=mongodb+srv://SEU_USUARIO:SUA_SENHA@SEU_CLUSTER.mongodb.net/?retryWrites=true&w=majority
MONGODB_DATABASE=dataops_lab
MONGODB_COLLECTION=orders_raw
```

## Execucao

1. Subir Temporal dev server (terminal 1)

```bash
temporal server start-dev
```

2. Subir worker (terminal 2)

```bash
python app/worker.py
```

3. Disparar workflow (terminal 3)

```bash
python app/run_workflow.py
```

## Validacoes

- Temporal Web UI: http://localhost:8233
- Atlas: database `dataops_lab`, collection `orders_raw`

## Git

```bash
git add .
git commit -m "Add fake data pipeline with Temporal and MongoDB Atlas"
git log --oneline
```
