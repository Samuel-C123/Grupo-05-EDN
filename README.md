# 🎭 FaceFeeling
> Sistema de Monitoramento de Satisfação e Reação do Cliente

[![AWS](https://img.shields.io/badge/AWS-Cloud-orange?logo=amazon-aws)](https://aws.amazon.com/)
[![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)](https://python.org/)
[![Serverless](https://img.shields.io/badge/Architecture-Serverless-green)](https://aws.amazon.com/serverless/)
[![LGPD](https://img.shields.io/badge/Compliance-LGPD-red)](https://www.gov.br/cidadania/pt-br/acesso-a-informacao/lgpd)

## 📋 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Equipe](#-equipe)
- [Arquitetura](#-arquitetura)
- [Tecnologias](#-tecnologias)
- [Requisitos](#-requisitos)
- [MVP](#-mvp)
- [Instalação](#-instalação)
- [Uso](#-uso)
- [Contribuição](#-contribuição)
- [Licença](#-licença)

## 🎯 Sobre o Projeto

O **FaceFeeling** é um sistema inovador que captura expressões faciais e áudio de clientes em ambientes de varejo de forma **anônima** e **discreta**. Utilizando Inteligência Artificial na nuvem AWS, o sistema processa dados em tempo real para gerar métricas valiosas sobre a satisfação do cliente em relação a produtos específicos.

### 🎯 Objetivo Principal
Oferecer às empresas maior visibilidade sobre as reações e feedbacks dos clientes sobre produtos e serviços, resultando em uma experiência cada vez mais próxima das necessidades dos consumidores.

## 👥 Equipe

| Função | Nome |
|--------|------|
| 🎯 **Scrum Master** | Raquel da Silva Moura |
| 👩‍💻 **Líder Técnica** | Cibelli Cristina Souza Santos |
| 🏗️ **Arquitetos** | Leandro Eduardo Lima dos Santos<br>Samuel Cardoso do Nascimento |
| 💻 **Desenvolvedores** | Igor dos Santos Rocha<br>Vinícius Rosa da Costa<br>Alan Fabrício Barbosa da Silva |

## 🏗️ Arquitetura

### 📐 Filosofia de Design

- **🚀 Serverless-First**: Priorização de serviços gerenciados AWS Lambda
- **⚡ Orientada a Eventos**: Sistema reativo baseado em eventos
- **📈 Escalabilidade**: Suporte desde uma loja piloto até centenas de estabelecimentos
- **🔒 Segurança por Design**: Conformidade com LGPD integrada em cada componente

### 🔄 Fluxo de Dados

```
Dispositivo de Captura → Amazon S3 → Evento S3 → AWS Lambda → 
Serviços de IA (Rekognition, Transcribe, Comprehend) → Amazon DynamoDB → Amazon QuickSight
```

### 🛠️ Componentes Principais

| Serviço | Função |
|---------|---------|
| **📁 Amazon S3** | Armazenamento temporário de imagens e áudio |
| **⚡ AWS Lambda** | Orquestrador serverless do processamento |
| **👁️ Amazon Rekognition** | Análise de expressões faciais e emoções |
| **🎤 Amazon Transcribe** | Conversão de voz em texto |
| **🧠 Amazon Comprehend** | Análise de sentimento do texto |
| **🗃️ Amazon DynamoDB** | Banco NoSQL para metadados anônimos |
| **📊 Amazon QuickSight** | Dashboard analítico e visualização |
| **🔐 AWS IAM** | Gerenciamento de permissões e segurança |

## 💻 Tecnologias

### Hardware
- **🔌 Raspberry Pi 4** (ou similar)
- **📷 Câmera USB** (640x480)
- **🎤 Microfone USB** com VAD (Voice Activity Detection)

### Software
- **🐍 Python 3.11**
- **☁️ boto3** (AWS SDK for Python)
- **📊 Amazon QuickSight**
- **🔧 AWS CloudFormation** (IaC)

### Arquitetura
- **🌐 Serverless Architecture**
- **📱 Edge Computing**
- **🔄 Event-Driven Design**
- **📊 Real-time Analytics**

## 📋 Requisitos

### ✅ Funcionais
- ✅ Captura de expressões visuais e voz através de periféricos
- ✅ Análise de dados e identificação de padrões
- ✅ Geração de métricas para equipe de experiência do cliente

### ⚙️ Não-Funcionais
- 🔒 **Privacidade**: Garantia de segurança dos dados capturados
- 🖥️ **Usabilidade**: Interface intuitiva para equipe responsável
- 👁️ **Discrição**: Periféricos discretos ou invisíveis ao cliente
- 📈 **Escalabilidade**: Suporte a múltiplos estabelecimentos
- ⚡ **Performance**: Processamento em tempo real

## 🎯 MVP

### Produto Mínimo Viável
- **📸 Captura de expressões faciais**
- **📊 Relatório ao time responsável**
- **🏷️ Correspondência produto-captura**

## 🚀 Instalação

### Pré-requisitos
```bash
# AWS CLI configurada
aws configure

# Python 3.11+
python --version

# Dependências
pip install boto3 opencv-python
```

### Configuração do Edge Device
```bash
# Clone do repositório
git clone https://github.com/AlanFabricioBarbosa/py_escola_da_nuvem.git
cd py_escola_da_nuvem

# Instalação das dependências
pip install -r requirements.txt

# Configuração das variáveis de ambiente
export AWS_REGION=us-east-1
export S3_BUCKET_NAME=facefeeling-capture-bucket
export CONFIDENCE_THRESHOLD=85.0
```

### Deploy da Infraestrutura
```bash
# Deploy via CloudFormation
aws cloudformation deploy \
  --template-file infrastructure.yaml \
  --stack-name facefeeling-stack \
  --capabilities CAPABILITY_IAM
```

## 🎮 Uso

### 📸 Captura de Dados
```python
# Exemplo de captura automática
python capture_emotions.py --store-id STORE_01 --product-id PROD_123
```

### 📊 Visualização
1. Acesse o **Amazon QuickSight**
2. Navegue até o dashboard **FaceFeeling Analytics**
3. Visualize as métricas de satisfação por produto/loja

### 🔧 Monitoramento
```bash
# Logs da função Lambda
aws logs tail /aws/lambda/processCustomerReaction --follow

# Métricas no CloudWatch
aws cloudwatch get-metric-statistics \
  --namespace AWS/Lambda \
  --metric-name Duration \
  --dimensions Name=FunctionName,Value=processCustomerReaction
```

## 📊 Metodologia

- **📋 Framework**: Kanban
- **🔧 Ferramenta**: Trello
- **🔄 Processo**: Desenvolvimento Ágil

## 🤝 Contribuição

1. 🍴 Fork o projeto
2. 🌿 Crie sua feature branch (`git checkout -b feature/AmazingFeature`)
3. 💾 Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. 📤 Push para a branch (`git push origin feature/AmazingFeature`)
5. 🔀 Abra um Pull Request

### 📝 Padrões de Código
- **🐍 PEP 8** para Python
- **📝 Documentação** obrigatória para funções
- **🧪 Testes unitários** para novas features
- **🔒 Review de segurança** para mudanças críticas

## 🔒 Segurança e Privacidade

### 🛡️ Conformidade LGPD
- ✅ **Anonimização**: Dados processados de forma anônima
- ✅ **TTL**: Exclusão automática após período determinado
- ✅ **Criptografia**: Dados em trânsito e em repouso
- ✅ **Acesso Mínimo**: Princípio do menor privilégio (IAM)

### 🔐 Medidas de Segurança
- 🔑 **Autenticação Multi-fator** (MFA)
- 🌐 **HTTPS** para todas as comunicações
- 📊 **Auditoria** completa via CloudTrail
- 🚨 **Alertas** automáticos para anomalias

## 📈 Métricas e KPIs

| Métrica | Descrição | Objetivo |
|---------|-----------|----------|
| **😊 Satisfaction Score** | Índice de satisfação por produto | > 80% |
| **⏱️ Processing Time** | Tempo de processamento por análise | < 2s |
| **🎯 Detection Accuracy** | Precisão da detecção de emoções | > 85% |
| **📈 System Uptime** | Disponibilidade do sistema | 99.9% |

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

<div align="center">

**🎭 FaceFeeling** - Transformando expressões em insights

*Desenvolvido com ❤️ pela equipe FaceFeeling*

[🌐 Website](https://facefeeling.com) • [📧 Contato](mailto:contato@facefeeling.com) • [📋 Documentação](docs/)

</div>
**Conceitos:** Multiplicação, cálculo de volume, formatação de saída

### 4. **total_price_calculator.py** - Calculadora de Preço Total
```python
product_name = "Cadeira Infantil"
unit_price = 12.40
quantity = 3
total_price = unit_price * quantity
```
**Conceitos:** Variáveis string e float, cálculos comerciais, formatação de moeda

---

##  Atividade_02 - Cálculos e Conversões

### 1. **currency_converter.py** - Conversor de Moeda
Converte valores em reais para dólares e euros usando taxas de câmbio fixas.
**Conceitos:** Divisão, conversão de moedas, formatação de números

### 2. **discount_calculator.py** - Calculadora de Desconto
Calcula descontos percentuais em produtos.
**Conceitos:** Porcentagem, subtração, cálculos comerciais

### 3. **school_average_calculator.py** - Calculadora de Média Escolar
Calcula a média aritmética de três notas.
**Conceitos:** Média aritmética, divisão, formatação decimal

### 4. **fuel_consumption_calculator.py** - Calculadora de Consumo de Combustível
Calcula o consumo médio de combustível (km/l).
**Conceitos:** Eficiência, divisão, formatação de resultados

---

##  Atividade_03 - Programas Interativos

### 1. **age_classifier.py** - Classificador de Idade
Classifica usuários por faixa etária:
-  Criança (0-12 anos)
-  Adolescente (13-17 anos)
-  Adulto (18-59 anos)
-  Idoso (60+ anos)

**Conceitos:** `input()`, `if/elif/else`, conversão de tipos

### 2. **bmi_calculator.py** - Calculadora de IMC 
**Versão Aprimorada** com validações e recursos avançados:

#### Funcionalidades:
-  Validação de entrada (peso e altura)
-  Tratamento de erros com `try/except`
-  Classificação detalhada do IMC (6 categorias)
-  Recomendações de saúde personalizadas
-  Interface visual com emojis
-  Tabela de referência completa
-  Organização em funções

####  Classificações IMC:
| IMC | Classificação | Emoji |
|-----|---------------|-------|
| < 18.5 | Abaixo do peso | 🔵 |
| 18.5 - 24.9 | Peso normal | 🟢 |
| 25.0 - 29.9 | Sobrepeso | 🟡 |
| 30.0 - 34.9 | Obesidade grau I | 🟠 |
| 35.0 - 39.9 | Obesidade grau II | 🔴 |
| ≥ 40.0 | Obesidade grau III | 🔴 |

**Conceitos:** Funções, validação, tratamento de exceções, estruturas condicionais aninhadas

### 3. **temperature_converter.py** - Conversor de Temperatura
Converte entre Celsius, Fahrenheit e Kelvin.

#### 🌡️ Fórmulas utilizadas:
- **Celsius para Fahrenheit:** `F = C × 9/5 + 32`
- **Celsius para Kelvin:** `K = C + 273.15`
- **Fahrenheit para Celsius:** `C = (F - 32) × 5/9`
- **Kelvin para Celsius:** `C = K - 273.15`

**Conceitos:** Conversões matemáticas, estruturas condicionais, métodos de string

### 4. **leap_year_checker.py** - Verificador de Ano Bissexto
Determina se um ano é bissexto usando as regras:
-  Divisível por 4 **E**
-  **NÃO** divisível por 100 **OU** divisível por 400

**Conceitos:** Operadores lógicos, módulo (`%`), lógica booleana

---

##  Como Executar

### Pré-requisitos
- Python 3.6 ou superior instalado
- Terminal/Command Prompt

### Execução Individual
```bash
# Navegar para a pasta desejada
cd Atividade_01
cd Atividade_02
cd Atividade_03

# Executar um programa específico
python nome_do_arquivo.py
```

### Exemplos:
```bash
# Executar calculadora de IMC aprimorada
cd Atividade_03
python bmi_calculator.py

# Executar conversor de temperatura
python temperature_converter.py

# Executar calculadora de desconto
cd ../Atividade_02
python discount_calculator.py
```

---

##  Conceitos Python Abordados

| Conceito | Descrição | Arquivos |
|----------|-----------|----------|
| **Variáveis** | Armazenamento de dados | Todos |
| **Tipos de Dados** | int, float, string | Todos |
| **Operações Aritméticas** | +, -, *, / | Atividade_01, 02 |
| **F-strings** | Formatação de strings | Todos |
| **Input/Output** | `input()`, `print()` | Atividade_03 |
| **Condicionais** | `if`, `elif`, `else` | Atividade_03 |
| **Funções** | Definição e chamada | bmi_calculator.py |
| **Tratamento de Erros** | `try/except` | bmi_calculator.py |
| **Validação** | Verificação de entrada | bmi_calculator.py |
| **Operadores Lógicos** | `and`, `or`, `not` | leap_year_checker.py |

---

## 🎓 Nível de Dificuldade

| Pasta | Nível | Descrição |
|-------|-------|-----------|
| **Atividade_01** | 🟢 Iniciante | Conceitos básicos, sem interação |
| **Atividade_02** | 🟡 Intermediário | Cálculos mais complexos |
| **Atividade_03** | 🔴 Avançado | Interação, validação, estruturas |

---

##  Próximos Passos

Para continuar aprendendo Python, considere estudar:
-  Listas e dicionários
-  Estruturas de repetição (`for`, `while`)
-  Manipulação de arquivos
-  APIs e requests
-  Interfaces gráficas (tkinter)
-  Análise de dados (pandas, matplotlib)

---

##  Contribuição

Sinta-se à vontade para:
-  Reportar bugs
-  Sugerir melhorias
-  Propor novos exercícios
-  Melhorar a documentação

---

##  Licença

Este projeto é livre para uso educacional e pessoal.

---
