# airflow-series
- O que é o Apache Airflow?
- Plataforma de código aberto (open source) que foi desenvolvida para orquestrar e monitorar workflows complexos utilizando uma interface gráfica e um sistema baseado em códigos.

#### Principais Componentes
- Metadatabase: Banco de dados centralizado que armazena informações sobre a execução das DAGs e tarefas. Todas as informações que eu vejo no painel são armazenadas dentro dele.
- Schedule: Responsável por iniciar a execução das DAGs e tarefas de acordo com a programação definida. É o coração onde todos os agendamentos de execução acontecem.
- Executor: Componente que realiza a execução real das tarefas, podendo ser local, em containers Docker ou em clusters na nuvem.
- Workers: Processos que efetivamente executam as tarefas, gerenciados pelo executor. Onde de fato as atividades são executadas.
- Web Service: Fornece uma interface gráfica web para monitorar e gerenciar as DAGs e atividades. Interface gráfica. 

### Tipos de Executores
- SequentialExecutor: desencolvimento e teste. Single Worker process.
- LocalExecuter: pode executar múltiplos processos simultâneos.
- CeleryExecuter: o mais utilizado, orquestrador de processos em python. 
- KubernetesExecutor: quando se está dentro de um cluster de kubernetes.

- O Astro utiliza o kubernetes como backbone.

### DAG
- DAG é um conjunto de tarefas.
- Parâmetros importantes para criar uma DAG.

```python
@dag(
  dag_id = s3-users-file,
  start_date = datetime(2023, 10, 2),
  max_active_runs = 1,
  schedule_interval = None,
  catchup = False
)
```

- Conceitos chaves de uma task:
  - task definition: definição utilizando python (BashOperator, PythonOperator, SnowflakeOperator).
  - task instance: especifica a execução (DAG ID, task ID, execution date).
  - task dependencies: ordena a definição de execução (>>, set_downstream, est_upstream).

- Hook (gancho): interface de alto nível que se comunica/interage com sistemas externos.

- Operator: instanciação que alguma tarefa que eu quero executar.
  - Sensor: espera algo acontecer.
  - Deferrable Operator: nova proposta para o sensor. Consome menos recursos.

- Types of operators: action, transfer, sensor, branch, specialized, deferrable.

- Branch: https://www.astronomer.io/docs/learn/airflow-branch-operator
