 # 🤖 Assistente de Investimentos com RPA e IA Generativa

Projeto desenvolvido como parte do **Bootcamp Santander 2026 - Automação com N8N** na [DIO](https://dio.me).

O projeto consiste em um pipeline completo de automação inteligente combinando **RPA (Robotic Process Automation) em Python**, **orquestração de microsserviços no n8n** e **geração de mensagens consultivas personalizadas com IA Generativa (LLM)**.

---

## 🏗️ Arquitetura do Projeto

```mermaid
flowchart LR
  %% Pipeline RPA + N8N + IA

  subgraph GH["GitHub Pages"]
    A["Clientes<br>(index.html)"]
    E["Investimentos<br>(data.csv)"]
  end

  subgraph PY["RPA (Python - Colab)"]
    B["Extrair Clientes<br>(BeautifulSoup)"]
  end

  subgraph N8["N8N Cloud (Orquestração)"]
    C["Webhook Entrada"]
    D["HTTP + Parser CSV"]
    M["Merge (Combine)"]
    R["Regras de Negócio"]
    IA["Agente IA (GPT-4o-mini)"]
    V["Validação Regex & Gmail"]
    
    C --> M
    D --> M
    M --> R --> IA --> V
  end

  subgraph OUT["Saída"]
    O["Mensagens e Resposta HTTP 200"]
  end

  A --> B --> C
  E --> D
  V --> O
