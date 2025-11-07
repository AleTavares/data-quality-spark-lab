# Qualidade de Dados (Data Quality)

**De "Dados Limpos" para "Dados Confiáveis" (Data Trust)**

---

## Mais que "Limpeza"

A Qualidade de Dados (DQ) mede a adequação dos dados ao seu propósito de negócio. É um processo contínuo que exige atenção constante e governança estruturada.

**A DQ é a fundação essencial para:**
*   Business Intelligence (BI) preciso que orienta decisões estratégicas.
*   Modelos de Machine Learning confiáveis que geram valor real.
*   Decisões estratégicas baseadas em evidências.

Sem uma base sólida, as ferramentas mais avançadas falham em entregar resultados confiáveis.

---

## O Custo da Má Qualidade

O impacto financeiro da má qualidade de dados é um problema crítico global.

| Métrica | Valor | Descrição |
| :--- | :--- | :--- |
| **Custo Anual Global** | **$3.1T** | Estimativa de perda anual (Gartner/IBM). |
| **Tempo Desperdiçado** | **30%** | Média de tempo que analistas gastam limpando dados. |
| **Impacto na Receita** | **15-25%** | Percentual médio de impacto negativo na receita. |

**Impactos:** Decisões equivocadas, perda de clientes, multas regulatórias (LGPD), ineficiência e erosão da confiança.

---

## O Princípio Fundamental: GIGO

**Garbage In, Garbage Out**

### Entrada (Input) - Dados Problemáticos
*   Cadastros de clientes duplicados ou inconsistentes.
*   Valores de vendas faltantes ou zerados incorretamente.
*   Datas de entrega impossíveis ou mal formatadas.
*   CPFs e CNPJs inválidos que passam pela validação.

### Saída (Output) - Consequências
*   Relatórios de vendas com números incorretos.
*   Modelos de IA com viés e previsões não confiáveis.
*   Envio de produtos para endereços errados (aumento de custos).
*   Multas pesadas por não conformidade regulatória.
*   Perda de confiança dos *stakeholders*.

---

## As Dimensões da Qualidade de Dados

Um framework estruturado para medir, avaliar e gerenciar a "qualidade".

### Dimensões Essenciais (1/3)

#### 1. Acurácia
*   **Pergunta:** O dado reflete a realidade?
*   **Mede:** Se os dados representam corretamente o mundo real que descrevem.
*   **Exemplo:** O saldo da conta bancária reflete o valor correto?
*   **Impacto:** Decisões baseadas em informações falsas.

#### 2. Completude
*   **Pergunta:** Todos os dados necessários estão presentes?
*   **Mede:** Se todos os campos obrigatórios e esperados foram preenchidos.
*   **Exemplo:** O campo "telefone" ou "CEP" está preenchido?
*   **Impacto:** Impede processos automatizados e análises aprofundadas.

---

### Dimensões Essenciais (2/3)

#### 3. Consistência
*   **Pergunta:** Os dados são iguais em diferentes sistemas?
*   **Mede:** Se a mesma informação tem o mesmo valor e formato em diferentes bases (ex: CRM e Faturamento).
*   **Impacto:** Retrabalho, erros de integração e perda de confiança.

#### 4. Tempestividade (Timeliness)
*   **Pergunta:** O dado está disponível quando necessário?
*   **Mede:** Se as informações chegam no momento adequado para suportar decisões.
*   **Exemplo:** O relatório de vendas está pronto às 8h da manhã?
*   **Impacto:** Perda de relevância e decisões com informações desatualizadas.

---

### Dimensões Essenciais (3/3)

#### 5. Validade e Unicidade
*   **Pergunta:** O dado segue as regras definidas e não está duplicado?
*   **Mede:** Se os dados atendem a formatos, tipos e regras de negócio (sem duplicações indevidas).
*   **Exemplo:** O CPF está no formato válido? Não há registros duplicados do mesmo cliente?
*   **Impacto:** Falhas em processos automatizados e violações de compliance.

#### 6. Relevância
*   **Pergunta:** Estamos coletando dados úteis?
*   **Mede:** Se os dados coletados são realmente necessários e aplicáveis aos objetivos de negócio.
*   **Exemplo:** Perguntar o "time de futebol" em um cadastro bancário é relevante?
*   **Impacto:** Aumenta custos de armazenamento e risco de privacidade.

---

## As Dimensões na Prática (Exemplo)

Exemplo de problemas simultâneos em uma base de dados:

| Campo | Jon Smit | Maria Silva | Problema de DQ |
| :--- | :--- | :--- | :--- |
| **Data Nasc.** | 1990-13-40 | 1985-05-10 | **Validade** (data impossível) |
| **Email** | jon@email.com | (nulo) | **Completude** (email nulo) |
| **Status (A/B)** | Ativo/Inativo | Ativo/Ativo | **Consistência** (status diferente) |
| **Nome** | Jon Smit | Maria Silva | **Acurácia** ("Jon Smit" -> "John Smith") |

---

## O Processo de Gestão de DQ

Transformando DQ em um processo contínuo e sustentável.

### Etapa 1: Medição (Assessment)
*   **Objetivo:** Entender o estado atual.
*   **Data Profiling:** A "radiografia" completa dos dados para identificar anomalias.
*   **Análise Exploratória:** Identificar nulos, duplicações e *outliers* estatísticos.
*   **Diagnóstico Inicial:** Relatório executivo com maiores problemas e impacto potencial.

### Etapa 2: Monitoramento (Observability)
*   **Objetivo:** Garantir que a qualidade não degrade.
*   **Dashboards de DQ:** Painéis visuais para mostrar a "saúde" dos dados (KPIs: completude, duplicação, *freshness*).
*   **Alertas Proativos:** Notificações automáticas antes que dados ruins cheguem aos relatórios.
*   **Data Observability:** Visibilidade contínua de todo o *pipeline* de dados (qualidade, volume, *schema*, linhagem).

### Etapa 3: Melhoria (Improvement)
*   **Objetivo:** Corrigir e prevenir problemas.
*   **Data Cleansing (Reativo):** Correção de dados já existentes (padronização, remoção de espaços). *Limitação: Não previne futuros problemas.*
*   **Prevenção na Origem (Proativo):** Abordagem mais eficaz: validações em formulários, regras no *backend* e *constraints* no banco de dados.
*   **Data Contracts (Moderno):** Contratos formais entre produtores e consumidores de dados para especificar *schema*, validações e SLAs.

---

## Definindo Regras de Negócio e KQIs

Não se gerencia o que não se mede.

### Regras de Qualidade (Definições Claras)
*   "O campo CPF não pode ser nulo E deve passar na validação matemática."
*   "O valor da venda não pode ser negativo nem zero."
*   "A data de entrega deve ser posterior à data do pedido."

### KQIs - Key Quality Indicators (Métricas Mensuráveis)
*   % de Completude do Cadastro de Clientes (meta: >95%)
*   % de Acurácia do Endereço de Entrega (meta: >98%)
*   Taxa de Duplicação de Registros (meta: <1%)
*   Tempo Médio de Atualização dos Dados (meta: <24h)

---

## Conclusão

Qualidade de Dados não é um custo, mas um investimento direto na confiabilidade e no futuro do negócio. Dados confiáveis são a base para decisões sólidas, modelos de IA que geram valor e *compliance* regulatório efetivo.