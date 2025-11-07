# 🎯 Exercício Prático: Qualidade de Dados com PySpark

**MBA Engenharia de Dados - Avaliação Prática**

---

## 📋 Contexto do Exercício

Você foi contratado como **Engenheiro de Dados** pela empresa **TechCommerce**, um e-commerce em crescimento. A empresa está enfrentando sérios problemas de qualidade em sua base de dados de clientes e vendas, impactando:

- 📊 Relatórios gerenciais incorretos
- 📧 Campanhas de marketing falhando
- 🚚 Entregas em endereços errados
- 💰 Perda de receita estimada em R$ 2M/ano

**Sua missão:** Implementar um sistema de monitoramento e correção de qualidade de dados usando PySpark.

---

## 🎯 Objetivos de Aprendizagem

Ao final deste exercício, você será capaz de:

1. ✅ Implementar as 6 dimensões de qualidade de dados
2. ✅ Calcular KQIs (Key Quality Indicators) 
3. ✅ Criar dashboards de monitoramento
4. ✅ Aplicar técnicas de data cleansing
5. ✅ Gerar relatórios executivos de qualidade

---

## 📊 Dataset Fornecido

Você receberá um arquivo CSV com dados de clientes e vendas contendo os seguintes problemas intencionais:

```
clientes_vendas.csv
├── id_cliente (int)
├── nome_completo (string)
├── email (string) 
├── telefone (string)
├── cpf (string)
├── data_nascimento (string)
├── endereco (string)
├── cidade (string)
├── estado (string)
├── cep (string)
├── data_cadastro (string)
├── status_cliente (string)
├── valor_ultima_compra (double)
├── data_ultima_compra (string)
└── categoria_cliente (string)
```

---

## 🚀 Parte 1: Análise Exploratória (25 pontos)

### 1.1 Setup Inicial (5 pontos)
```python
# TODO: Configurar SparkSession com as configurações adequadas
# TODO: Carregar o dataset CSV
# TODO: Exibir schema e primeiras linhas
```

### 1.2 Data Profiling Básico (10 pontos)
Implemente funções para calcular:
- Total de registros
- Número de colunas
- Tipos de dados por coluna
- Estatísticas básicas (count, mean, std, min, max) para colunas numéricas

### 1.3 Identificação de Problemas (10 pontos)
Crie um relatório inicial identificando:
- Campos com valores nulos
- Possíveis duplicatas
- Valores fora do padrão esperado
- Inconsistências óbvias

---

## 🔍 Parte 2: Implementação das Dimensões de DQ (40 pontos)

### 2.1 Completude (8 pontos)
```python
def analisar_completude(df):
    """
    TODO: Implementar análise de completude
    - Calcular % de preenchimento por coluna
    - Identificar campos críticos com alta taxa de nulos
    - Retornar DataFrame com resultados
    """
    pass
```

### 2.2 Validade (8 pontos)
```python
def validar_formatos(df):
    """
    TODO: Implementar validações de formato
    - Email: formato válido
    - CPF: 11 dígitos e algoritmo de validação
    - Telefone: 10-11 dígitos
    - CEP: 8 dígitos no formato XXXXX-XXX
    - Data: formato válido e não no futuro
    """
    pass
```

### 2.3 Unicidade (8 pontos)
```python
def analisar_duplicatas(df):
    """
    TODO: Detectar duplicatas
    - Por ID (chave primária)
    - Por CPF (identificador único)
    - Por combinação nome + data_nascimento
    - Calcular taxa de duplicação
    """
    pass
```

### 2.4 Consistência (8 pontos)
```python
def verificar_consistencia(df):
    """
    TODO: Verificar consistência entre campos
    - data_ultima_compra >= data_cadastro
    - status_cliente vs valor_ultima_compra
    - cidade vs estado (usar lista de referência)
    - categoria_cliente vs valor_ultima_compra
    """
    pass
```

### 2.5 Acurácia (8 pontos)
```python
def detectar_anomalias(df):
    """
    TODO: Detectar possíveis problemas de acurácia
    - Nomes com caracteres especiais ou números
    - Idades impossíveis (< 16 ou > 120 anos)
    - Valores de compra outliers (Z-score > 3)
    - CEPs inexistentes (usar faixas válidas)
    """
    pass
```

---

## 📈 Parte 3: KQIs e Dashboard (20 pontos)

### 3.1 Cálculo de KQIs (10 pontos)
Implemente o cálculo dos seguintes indicadores:

| KQI | Meta | Fórmula |
|-----|------|---------|
| **Completude Geral** | >95% | (Campos preenchidos / Total campos) * 100 |
| **Taxa de Emails Válidos** | >98% | (Emails válidos / Total emails) * 100 |
| **Taxa de Duplicação** | <2% | (Registros duplicados / Total) * 100 |
| **Consistência Temporal** | >99% | (Datas consistentes / Total) * 100 |
| **Acurácia de CPF** | >95% | (CPFs válidos / Total CPFs) * 100 |

### 3.2 Dashboard Visual (10 pontos)
```python
def gerar_dashboard_qualidade(kqis):
    """
    TODO: Criar dashboard visual
    - Exibir KQIs com status (🟢🟡🔴)
    - Calcular score geral de qualidade
    - Mostrar tendência (melhorou/piorou)
    - Destacar KQIs críticos
    """
    pass
```

---

## 🧹 Parte 4: Data Cleansing (15 pontos)

### 4.1 Estratégia de Limpeza (5 pontos)
Defina e documente sua estratégia:
- Quais registros serão removidos?
- Quais campos serão corrigidos automaticamente?
- Quais problemas precisam de intervenção manual?

### 4.2 Implementação da Limpeza (10 pontos)
```python
def aplicar_limpeza(df):
    """
    TODO: Implementar limpeza automatizada
    - Remover duplicatas mantendo o mais recente
    - Padronizar formatos (telefone, CEP)
    - Corrigir espaços extras em nomes
    - Filtrar registros com problemas críticos
    - Aplicar regras de negócio
    """
    pass
```

---

## 📊 Entregáveis Esperados

### 1. Notebook Jupyter (.ipynb)
- Código completo e executável
- Comentários explicativos
- Resultados das análises

### 2. Relatório Executivo (.md)
```markdown
# Relatório de Qualidade de Dados - TechCommerce

## Resumo Executivo
- Score geral de qualidade: X%
- Principais problemas identificados
- Impacto estimado no negócio

## KQIs Atuais vs Metas
[Tabela com resultados]

## Recomendações
1. Ações imediatas
2. Melhorias de processo
3. Investimentos necessários
```

### 3. Dataset Limpo
- Arquivo Parquet com dados corrigidos
- Metadados de qualidade
- Log de transformações aplicadas

---

## 🏆 Critérios de Avaliação

| Critério | Peso | Descrição |
|----------|------|-----------|
| **Implementação Técnica** | 40% | Código PySpark correto e eficiente |
| **Análise de Qualidade** | 30% | Identificação precisa dos problemas |
| **KQIs e Métricas** | 20% | Cálculos corretos e relevantes |
| **Documentação** | 10% | Clareza e completude do relatório |

### Níveis de Desempenho:
- 🥇 **Excelente (90-100%)**: Implementação completa + insights avançados
- 🥈 **Bom (80-89%)**: Implementação correta das funcionalidades principais
- 🥉 **Satisfatório (70-79%)**: Implementação básica com alguns problemas
- ❌ **Insuficiente (<70%)**: Implementação incompleta ou incorreta

---

## 💡 Dicas de Sucesso

### Técnicas:
- Use `cache()` em DataFrames reutilizados
- Prefira `filter()` antes de `groupBy()`
- Utilize `coalesce()` para otimizar partições

### Validações:
- Teste com subconjunto dos dados primeiro
- Valide cada função individualmente
- Compare resultados com análise manual

### Documentação:
- Explique suas decisões de limpeza
- Justifique os thresholds escolhidos
- Documente limitações e suposições

---

## 🚀 Desafios Extras (Bônus)

Para alunos que desejam ir além:

### 🌟 Nível Avançado (+10 pontos)
- Implementar Great Expectations para validação
- Criar pipeline automatizado de qualidade
- Integrar com sistema de alertas

### 🌟 Nível Expert (+15 pontos)
- Usar Delta Lake para versionamento
- Implementar data lineage tracking
- Criar API REST para consulta de qualidade

---

## 📅 Prazo de Entrega

**Data limite:** [Definir conforme cronograma da turma]

**Formato de entrega:**
- Repositório Git com código e documentação
- Apresentação de 10 minutos dos resultados
- Demo ao vivo do dashboard implementado

---

## 🆘 Suporte

- **Dúvidas técnicas:** Fórum da disciplina
- **Problemas com ambiente:** Slack do curso
- **Office hours:** Terças 19h-20h

**Boa sorte! 🍀**

---

*"A qualidade nunca é um acidente; é sempre o resultado de um esforço inteligente."* - John Ruskin