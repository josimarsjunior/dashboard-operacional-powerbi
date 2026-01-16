# Medidas DAX – Dashboard Operacional

Este documento reúne as principais medidas e colunas calculadas utilizadas no dashboard, com foco em métricas operacionais e indicadores de desempenho.

---

## Total de Processos
Conta o número total de processos registrados.

```DAX
Total Processos =
COUNT(Fato_Processos[ID_Processo])
```

## Processos Concluídos
Filtra e contabiliza apenas os processos com status Concluído.

```DAX
Processos Concluídos =
CALCULATE(
    [Total Processos],
    Dim_Status[Status] = "Concluído"
)
```

## Processos Pendentes
Retorna a quantidade de processos ainda não concluídos.

```DAX
Processos Pendentes =
CALCULATE(
    [Total Processos],
    Dim_Status[Status] = "Pendente"
)
```

## Percentual de Processos Concluídos
Indica a taxa de conclusão dos processos em relação ao total.

```DAX
% Concluídos =
IF(
    [Processos Concluídos] = 0,
    0,
    DIVIDE([Processos Concluídos], [Total Processos])
)
```

## Tempo Médio de Conclusão
Calcula o tempo médio, em dias, para a finalização dos processos concluídos.

```DAX
Tempo Médio de Conclusão =
AVERAGE(Fato_Processos[Tempo_Conclusao_Dias])
```

## Coluna Calculada – Tempo de Conclusão
Calcula o intervalo, em dias, entre a data de abertura e a data de conclusão do processo.

```DAX
Tempo_Conclusao_Dias =
DATEDIFF(
    Fato_Processos[Data_Abertura],
    Fato_Processos[Data_Conclusão_Correta],
    DAY
)
```

## Medida para Exibição Condicional
Melhora a leitura da tabela analítica ao tratar processos ainda não concluídos.

```DAX
Tempo Conclusão (Exibição) =
VAR Tempo =
    SELECTEDVALUE(Fato_Processos[Tempo_Conclusao_Dias])
RETURN
IF(
    ISBLANK(Tempo),
    "Não concluído",
    FORMAT(Tempo, "0") & " dias"
)
```
