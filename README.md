# airflow-series
- O que é o Apache Airflow?
- Plataforma de código aberto (open source) que foi desenvolvida para orquestrar e monitorar workflows complexos utilizando uma interface gráfica e um sistema baseado em códigos.

#### Principais Componentes
- Metadatabase: Banco de dados centralizado que armazena informações sobre a execução das DAGs e tarefas.
- Schedule: Responsável por iniciar a execução das DAGs e tarefas de acordo com a programação definida.
- Executor: Componente que realiza a execução real das tarefas, podendo ser local, em containers Docker ou em clusters na nuvem.
- Workers: Processos que efetivamente executam as tarefas, gerenciados pelo executor.
- Web Service: Fornece uma interface gráfica web para monitorar e gerenciar as DAGs e atividades.
