# Modelo de Dados – Dashboard Operacional

Este projeto utiliza um **modelo dimensional em estrela**, estruturado no Power BI com base em boas práticas de Business Intelligence, visando melhor performance, clareza analítica e facilidade de manutenção.

---

## 🧱 Visão Geral da Modelagem

O modelo é composto por:
- 1 tabela fato central (`Fato_Processos`)
- 3 tabelas dimensão (`Dim_Tempo`, `Dim_Status`, `Dim_Equipe`)

As dimensões fornecem contexto analítico aos registros operacionais armazenados na tabela fato.

---

## 📊 Tabela Fato

### Fato_Processos
Tabela central do modelo, responsável por armazenar os registros operacionais dos processos.

**Campos principais:**
- `ID_Processo` – Identificador único do processo  
- `ID_Status` – Chave estrangeira para a dimensão de status  
- `ID_Equipe` – Chave estrangeira para a dimensão de equipes  
- `Data_Abertura` – Data de abertura do processo  
- `Data_Conclusão` – Data de conclusão do processo (nula para processos não concluídos)  

A tabela fato não contém atributos textuais descritivos, evitando redundância e garantindo maior eficiência do modelo.

---

## 🧩 Tabelas Dimensão

### Dim_Tempo
Tabela de datas utilizada para análises temporais dos processos.

**Campos principais:**
- `Data` – Data no formato calendário  
- `Ano` – Ano da data  
- `Mes` – Número do mês  
- `Mes_Nome` – Nome do mês  

Essa dimensão permite análises por período, evolução temporal e segmentação por ano e mês.

---

### Dim_Status
Dimensão responsável pela categorização do status dos processos.

**Campos principais:**
- `ID_Status` – Identificador do status  
- `Status` – Descrição do status  

**Exemplos de valores:**
- Concluído  
- Pendente  
- Em Análise  

---

### Dim_Equipe
Dimensão que representa as equipes responsáveis pelos processos.

**Campos principais:**
- `ID_Equipe` – Identificador da equipe  
- `Equipe` – Nome da equipe  

**Exemplos de valores:**
- Equipe A  
- Equipe B  
- Equipe C  

---

## 🔗 Relacionamentos

Os relacionamentos seguem o padrão **1:N**, com as dimensões filtrando a tabela fato.

- `Dim_Tempo[Data]` (1) → `Fato_Processos[Data_Abertura]` (N)  
- `Dim_Status[ID_Status]` (1) → `Fato_Processos[ID_Status]` (N)  
- `Dim_Equipe[ID_Equipe]` (1) → `Fato_Processos[ID_Equipe]` (N)  

Os filtros são **unidirecionais**, evitando ambiguidades e melhorando a performance do modelo.

---

## 🎯 Boas Práticas Aplicadas
- Modelo em estrela  
- Separação clara entre fatos e dimensões  
- Uso de chaves numéricas para relacionamento  
- Ausência de atributos textuais na tabela fato  
- Preparação adequada dos dados no Power Query  
- Estrutura otimizada para criação de medidas DAX  

---

## 📌 Considerações Finais
A modelagem adotada suporta análises operacionais e gerenciais, permitindo acompanhar o volume de processos, seus status, responsáveis e evolução ao longo do tempo de forma clara e eficiente.
