# 📊 Qualidade de Dados com PySpark: De "Dados Limpos" para "Dados Confiáveis"

Este repositório foi desenvolvido para a disciplina **Data Collection** do MBA em Engenharia de Dados, focando em **Qualidade de Dados (Data Quality)** - o processo fundamental para garantir dados confiáveis e decisões baseadas em evidências.

## 🎯 Objetivos da Aula

Demonstrar na prática as 6 dimensões de qualidade de dados através de implementações PySpark:

- **Completude**: Identificação e tratamento de valores nulos/vazios
- **Validade**: Validação de formatos e regras de negócio
- **Unicidade**: Detecção e remoção de duplicatas
- **Consistência**: Verificação de relacionamentos entre campos
- **Acurácia**: Detecção de anomalias e outliers
- **Tempestividade**: Análise de freshness dos dados

## 📚 Conteúdo Programático

### 📖 **Material Teórico**
- **[aula.md](aula.md)**: Fundamentos de qualidade de dados, dimensões e KQIs
- **Princípio GIGO**: Garbage In, Garbage Out
- **Impacto Financeiro**: $3.1T de perdas anuais globais
- **Framework das 6 Dimensões**: Estrutura completa de avaliação

### 💻 **Implementação Prática**
- **qualidade_dados_pyspark.ipynb**: Notebook com implementações PySpark
- **Data Profiling**: Análise exploratória automatizada
- **KQIs Dashboard**: Métricas de qualidade em tempo real
- **Data Cleansing**: Correções automatizadas

### 🎯 **Exercício Prático**
- **[exercicio.md](exercicio.md)**: Desafio prático completo
- **[clientes_vendas.csv](clientes_vendas.csv)**: Dataset com problemas intencionais
- **Cenário TechCommerce**: Caso real de e-commerce

## 🏗️ Arquitetura do Ambiente

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Jupyter Lab   │    │   Apache Spark   │    │   Data Quality  │
│   (Port 8888)   │◄──►│   + PySpark      │◄──►│   Framework     │
│                 │    │   (Port 4040)    │    │                 │
└─────────────────┘    └──────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                    ┌─────────────────────┐
                    │   Docker Network    │
                    │  (172.16.240.0/24)  │
                    └─────────────────────┘
```

## 📂 Estrutura do Projeto

```
aulaQualidadeMBA/
├── 📁 notebooks/                    # Notebooks da aula
│   └── qualidade_dados_pyspark.ipynb  # Implementação completa das 6 dimensões
├── 📁 data/                         # Datasets
│   └── clientes_vendas.csv          # Dataset com problemas de qualidade
├── 📖 aula.md                       # Material teórico completo
├── 📋 exercicio.md                  # Exercício prático avaliativo
├── 🐳 docker-compose.yml            # Orquestração dos serviços
├── 🐳 Dockerfile                    # Imagem PySpark customizada
└── 📖 README.md                     # Este arquivo
```

## 🚀 Setup e Execução

### Pré-requisitos
- [Docker](https://docs.docker.com/get-docker/) 20.10+
- [Docker Compose](https://docs.docker.com/compose/install/) 2.0+
- 8GB RAM disponível
- 10GB espaço em disco

### 🔥 Executando na Maquina Local ( Docker Descktop )

1. **Clone o repositório**:
   ```bash
   git clone https://github.com/AleTavares/data-quality-spark-lab.git
   cd data-quality-spark-lab
   ```

2. **Inicie o ambiente**:
   ```bash
   docker-compose up -d --build
   ```

3. **Acesse o Jupyter Lab**:
   ```
   http://localhost:8888
   Token: tavares1234
   ```

4. **Acesse o Spark UI** (opcional):
   ```
   http://localhost:4040
   ```

### 🛑 Parar o ambiente
```bash
docker-compose down
```

## ☁️ Executando no GitHub Codespaces

O GitHub Codespaces oferece um ambiente de desenvolvimento completo na nuvem, ideal para executar este laboratório sem necessidade de instalação local.

### 🚀 **Início Rápido no Codespaces**

1. **Abra o repositório no GitHub**:
   ```
   https://github.com/AleTavares/data-quality-spark-lab
   ```

2. **Crie um novo Codespace**:
   - Clique no botão verde **"Code"**
   - Selecione a aba **"Codespaces"**
   - Clique em **"Create codespace on main"**

3. **Aguarde a inicialização** (2-3 minutos):
   - O ambiente será configurado automaticamente
   - Docker já estará disponível

### 🐳 **Executando Docker no Codespace**

4. **Inicie o ambiente PySpark**:
   ```bash
   # No terminal do Codespace
   docker-compose up -d --build
   ```

5. **Aguarde a construção** (primeira execução ~5-10 min):
   ```bash
   # Monitore o progresso
   docker-compose logs -f pyspark-quality
   ```

6. **Acesse o Jupyter Lab**:
   - O Codespace detectará automaticamente a porta 8888
   - Clique na notificação **"Open in Browser"**
   - Ou acesse via **"PORTS"** tab → porta 8888
   - **Token**: `tavares1234`

### 🔧 **Configurações Específicas do Codespace**

**Recursos Recomendados**:
- **Machine type**: 4-core (8GB RAM) ou superior
- **Storage**: Padrão (32GB) é suficiente

**Portas Expostas**:
- **8888**: Jupyter Lab (principal)
- **4040**: Spark UI (monitoramento)

**Comandos Úteis**:
```bash
# Verificar status dos containers
docker ps

# Ver logs em tempo real
docker-compose logs -f

# Parar o ambiente
docker-compose down

# Limpar recursos (se necessário)
docker system prune -f
```

### ⚠️ **Limitações do Codespace**
- **Timeout**: Codespaces gratuitos param após 30min de inatividade
- **Recursos**: Limitados conforme plano GitHub
- **Persistência**: Dados persistem enquanto o Codespace existir

### 💡 **Dicas de Uso**
- Mantenha o Codespace ativo durante a aula
- Faça commits regulares para salvar o progresso
- Use `docker-compose down` antes de parar o Codespace

---

## 🎓 Roteiro de Estudos

### **Parte 1: Fundamentos Teóricos**
1. Leia `aula.md` - Material teórico completo
   - Entenda o impacto da má qualidade ($3.1T anuais)
   - Aprenda o princípio GIGO (Garbage In, Garbage Out)
   - Conheça as 6 dimensões de qualidade
   
### **Parte 2: Implementação Prática**
2. Execute `qualidade_dados_pyspark.ipynb`
   - **Completude**: Análise de valores nulos
   - **Validade**: Validação de formatos (email, CPF, telefone)
   - **Unicidade**: Detecção de duplicatas
   - **Consistência**: Verificação entre campos relacionados
   - **Acurácia**: Detecção de anomalias e outliers
   - **Tempestividade**: Análise de freshness

### **Parte 3: KQIs e Dashboard**
3. Implemente métricas de qualidade
   - Calcule KQIs (Key Quality Indicators)
   - Crie dashboard visual de monitoramento
   - Gere relatórios executivos

### **Parte 4: Data Cleansing**
4. Aplique correções automatizadas
   - Remova duplicatas
   - Padronize formatos
   - Filtre registros problemáticos

### **Parte 5: Exercício Avaliativo**
5. Complete o `exercicio.md`
   - Cenário TechCommerce (e-commerce)
   - Dataset `clientes_vendas.csv` com problemas reais
   - Implementação completa do framework de qualidade

## 🔧 Tecnologias Utilizadas

| Tecnologia | Versão | Propósito |
|------------|--------|-----------|
| **Apache Spark** | 3.3.0 | Engine de processamento distribuído |
| **PySpark** | 3.3.0 | API Python para Spark |
| **Python** | 3.11 | Linguagem principal |
| **Jupyter Lab** | Latest | Ambiente de desenvolvimento |
| **Docker** | 20.10+ | Containerização |
| **Pandas** | Latest | Análise de dados complementar |

## 🎯 Framework de Qualidade de Dados

### ✅ **As 6 Dimensões Implementadas**

| Dimensão | Métrica | **Implementação PySpark** |
|----------|---------|---------------------------|
| **Completude** | % campos preenchidos | `count(when(col().isNotNull()))` |
| **Validade** | % formatos corretos | `regexp_match()` + validações |
| **Unicidade** | % registros únicos | `dropDuplicates()` + análise |
| **Consistência** | % relacionamentos válidos | Validações entre campos |
| **Acurácia** | % dados corretos | Detecção de outliers/anomalias |
| **Tempestividade** | Freshness dos dados | Análise temporal |

### 🚀 **Casos de Uso Empresariais**
- **Business Intelligence**: Relatórios confiáveis e precisos
- **Machine Learning**: Datasets limpos para modelos robustos
- **Compliance**: Atendimento a regulamentações (LGPD)
- **Operações**: Redução de custos operacionais
- **Tomada de Decisão**: Decisões baseadas em dados confiáveis

## 🤝 Contribuições

Este material foi desenvolvido para fins educacionais. Sugestões e melhorias são bem-vindas através de issues e pull requests.

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 📞 Suporte

Para dúvidas sobre o conteúdo da aula:
- Abra uma [issue](https://github.com/AleTavares/dataqualitySpark/issues)
- Entre em contato durante a aula

---

**🎓 MBA Engenharia de Dados - Data Collection**  
*Transformando dados em valor através da Qualidade de Dados*