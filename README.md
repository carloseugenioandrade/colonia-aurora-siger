<div align="center">

# 🚀 Sistema Inteligente da Colônia Aurora Siger

**Gerenciamento autônomo de energia para a primeira colônia humana em Marte**

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python&logoColor=white)
![Status](https://img.shields.io/badge/Status-Operacional-brightgreen?style=for-the-badge)
![Libs](https://img.shields.io/badge/Bibliotecas_externas-Nenhuma-orange?style=for-the-badge)
![Licença](https://img.shields.io/badge/Licença-MIT-purple?style=for-the-badge)

<br/>

> *"O grande desafio não é apenas reagir ao ambiente,*  
> *mas interpretar dados, identificar padrões e antecipar comportamentos."*  
> — Missão Aurora Siger, 2026

</div>

---

## 📖 Sobre o Projeto

A colônia **Aurora Siger** entrou em operação contínua em Marte. Com a latência de comunicação com a Terra tornando impossível o controle manual em tempo real, foi necessário desenvolver um sistema computacional capaz de **operar de forma autônoma**.

Este sistema integra quatro módulos para transformar dados brutos de sensores em **decisões claras e automáticas**:

```
Sensores → Dados → Análise → Previsão → Decisão → Ação
```

---

## 🗂️ Arquitetura do Sistema

```
colonia_aurora/
├── sistema_colonia.py   # Sistema principal (todos os módulos)
└── README.md            # Documentação
```

### Módulos internos

| # | Módulo | Função |
|---|--------|--------|
| 1 | **Estrutura de Dados** | Organiza dados em dicionários hierárquicos e listas |
| 2 | **Previsão (Regressão)** | Estima geração eólica a partir da velocidade do vento |
| 3 | **Análise de Energia** | Compara geração × consumo e emite alertas |
| 4 | **Lógica de Decisão** | Aplica regras automáticas com prioridade |
| 5 | **Relatório do Ciclo** | Consolida todas as decisões tomadas |

---

## ⚙️ Como Executar

**Pré-requisito:** Python 3 instalado. Nenhuma biblioteca externa necessária.

```bash
# Clone o repositório
git clone https://github.com/carloseugenioandrade/colonia-aurora-siger.git

# Entre na pasta
cd colonia-aurora-siger

# Execute
python sistema_colonia.py
```

### Modo interativo

Para informar seus próprios valores, edite a última linha do arquivo:

```python
# Em sistema_colonia.py, linha final:
executar_sistema(interativo=True)   # ← troque False por True
```

---

## 💡 Exemplo de Entrada e Saída

**Entrada (valores padrão do sistema):**

| Variável | Valor |
|----------|-------|
| Bateria | 65% |
| Geração Solar | 40 u |
| Geração Eólica | 20 u |
| Consumo Total | 70 u |
| Reserva | 10 u |
| Velocidade do Vento | 11 m/s |

**Saída do terminal:**

```
══════════════════════════════════════════════════════
  🚀  SISTEMA INTELIGENTE — COLÔNIA AURORA SIGER
══════════════════════════════════════════════════════

┌────────────────────────────────────────────────────┐
│  PAINEL DA COLÔNIA — Aurora Siger                  │
└────────────────────────────────────────────────────┘

  🔋 Bateria   [█████████████░░░░░░░]  65%  (OK)
  ⚡ Geração   [████████████░░░░░░░░]  60 u
  🔌 Consumo   [██████████████░░░░░░]  70 u
  🗄  Reserva   [████░░░░░░░░░░░░░░░░]  10 u  (máx 50)

┌────────────────────────────────────────────────────┐
│  MÓDULO 2 — PREVISÃO DE ENERGIA EÓLICA             │
└────────────────────────────────────────────────────┘

  Modelo ajustado  : energia = 2.5 × vento + (0.0)
  Entrada          : vento = 11 m/s
  Previsão         : [███████████░░░░░░░░░] ≈ 27.5 u

┌────────────────────────────────────────────────────┐
│  MÓDULO 3 — ANÁLISE DE ENERGIA                     │
└────────────────────────────────────────────────────┘

  🟠 ALERTA: consumo maior que geração.
     Ação recomendada: Usar reserva e reduzir não essenciais.

┌────────────────────────────────────────────────────┐
│  MÓDULO 4 — LÓGICA DE DECISÃO                      │
└────────────────────────────────────────────────────┘

  🟡 MODO ECONOMIA
     Condição : consumo > geração (bateria ainda ok)
     Decisão  : monitorar — reduzir opcionais se persistir

┌────────────────────────────────────────────────────┐
│  RELATÓRIO FINAL DO CICLO                          │
└────────────────────────────────────────────────────┘

  1. Previsão eólica → vento = 11 m/s → energia ≈ 27.5 u
  2. Análise energética → ALERTA: consumo maior que geração.
  3. Decisão final → MODO ECONOMIA

  📊 Eficiência energética do ciclo : 85.7%
  🔋 Carga de bateria restante      : 65%
```

---

## 🧠 Como Cada Módulo Funciona

### 🗃️ Módulo 1 — Estrutura de Dados

Os dados da colônia são armazenados em um **dicionário hierárquico** (chave-valor), permitindo acesso rápido e organizado:

```python
colonia = {
    "energia": { "bateria": 65, "geracao_solar": 40, ... },
    "clima":   { "velocidade_vento": 11, ... },
    "sistemas": {
        "energetico":    { "solar": {...}, "eolico": {...} },
        "suporte_vida":  { "oxigenio": {...}, ... },
        "nao_essenciais":{ "laboratorio": {...}, ... }
    },
    "historico": { "vento": [...], "energia_eolica": [...] }
}
```

### 📈 Módulo 2 — Regressão Linear

Implementada **do zero**, sem bibliotecas externas, pelo método dos mínimos quadrados:

```
y = a × x + b
```

Onde `x` = velocidade do vento e `y` = energia eólica gerada.  
Com `vento = 11 m/s` → `energia ≈ 27.5 u` ✔

### ⚡ Módulo 3 — Análise de Energia

| Condição | Saída |
|----------|-------|
| `consumo > geração + reserva` | 🔴 ALERTA CRÍTICO |
| `consumo > geração` | 🟠 ALERTA |
| `saldo > 20 u` | 💡 SUGESTÃO: armazenar excedente |
| Equilibrado | ✅ STATUS OK |

### 🤖 Módulo 4 — Lógica de Decisão

Regras aplicadas em ordem de prioridade. Suporte à vida **nunca é desligado**.

```
SE bateria < 20% E consumo alto  →  🔴 EMERGÊNCIA
SE bateria < 50%                 →  🟠 REDUZIR CONSUMO
SE consumo > geração             →  🟡 MODO ECONOMIA
CASO CONTRÁRIO                   →  🟢 OPERAÇÃO NORMAL
```

---

## 📊 Critérios de Avaliação Atendidos

| Critério | Como foi implementado |
|----------|-----------------------|
| ✅ Estruturação de dados | Dicionário hierárquico + listas históricas |
| ✅ Lógica de decisão | `if / elif / else` com regras combinadas |
| ✅ Modelagem e previsão | Regressão linear por mínimos quadrados (sem libs) |
| ✅ Implementação em Python | Código organizado em funções com docstrings |
| ✅ Documentação e organização | README + comentários detalhados no código |

---

## 👤 Authors

**Carlos Eugênio Rodrigues de Andrade Filho**  
RM: 570285  
📧 [carloseugenioprofissional@gmail.com](mailto:carloseugenioprofissional@gmail.com)

**Matheus Fuchelberguer Neves**  
RM: 571321  
📧 [fuchelberguer28@gmail.com](mailto:fuchelberguer28@gmail.com)

---

<div align="center">
  <sub>Projeto acadêmico — Missão Aurora Siger · 2026</sub>
</div>
