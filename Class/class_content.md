# Observabilidade

## Introdução

- Aula 1: Introdução

- Aula 2: O que é realmente Observabilidade
    - Na teoria de controle, a observabilidade é definida como uma medida de quão bem os estados internos de um sistema podem ser inferidos a partir do conhecimento das saídas externas desse sistema. Simplificando, observabilidade é quão bem você pode entender seu sistema complexo.

- Aula 3: Observabilidade Vs Monitoramento
    - Monitoramento nos mostra que há algo errado
    - Monitoramento se baseia em saber com antecedência quais sinais você deseja monitorar
    - Observabilidade nos permite perguntar o porquê

- Aula 4: Os 3 pilares da Observabilidades
    - Métricas
    - Logs
    - Tracing
    ![Observabilidade](img/observability.png)

## Elastic Stack

- Aula 5: Introdução ao Elastic Stack
    - Voltando no tempo: Era conhecido como ELK Stack
        - Elastisearch: Search engine e analytics
        - Logstash: Processador de dados através de pipelines que consegue receber, transformar e enviar dados simultaneamente
        - Kibana: Permite usuários a visualizarem os dados do elasticsearch em diversas perspectivas
    - Elastisearch
        ![Observabilidade](img/observability3.png)
        - Search engine e analytics
        - Apache Lucene
        - 2010: Elasticsearch N.V (Elastic)
        - Rápido
        - Escalável
        - API Rest
        - Análise e visualização geoespacial
        - Application, website e enterprise search
        - Logging e analytics
        - Trabalha de forma distribuída através de shards que possuem redundância de dados.
        - Pode escalar milhares de servidores e manipular petabytes de dados

- Aula 6: Mais sobre Logstash
    - Logstash
        ![Observabilidade](img/observability2.png)
        - Engine coletora de dados em tempo real
        - Iniciou como manipulador de logs
        - Trabalha com pipelines
        - Recebe dados de múltiplas fontes
        - Normaliza e transforma dados
        - Envia dados para múltiplas fontes
        - Plugins

- Aula 7: Sobre o Kibana
    - Kibana
        ![Observabilidade](img/observability4.png)
        - Ferramenta de visualização e exploração de dados
        - Usada com: Logs, Análise de séries, Monitoramento de aplicações e inteligência operacional
        - Integrado com Elasticsearch
        - Agregadores e filtragem de dados
        - Dashboards
        - Gráficos interativos
        - Mapas

- Aula 8: Beats e Elastic Stack
    - Qual a diferença entre ELK Stack e Elastic Stack?
        Beats
        ![Observabilidade](img/observability5.png)
        - Beats foi anunciado em 2015
        - "Lightweight data shipper"
        - Agente Coletor de dados
        - Integrado facilmente com Elasticsearch ou Logstash
        - Logs, Métricas, Network data, Audit Data, Uptime Monitoring
        - Você pode contruir seu próprio Beat
        Elastic Stack
        ![Observabilidade](img/observability6.png)
        Elastic
        - Empresa por trás das soluções
        - Cloud Solution
        - Oferecem plugins e recursos licenciados
        - Produtos
            - APM
            - Maps
            - Site Search
            - Enterprise Search
            - App Search
            - Infrastructure
    
- Aula 9: Iniciando com Elasticsearch e Kibana
    - Site da elastic <https://www.elastic.co/pt/>
    - Github elastic <https://github.com/elastic>
    - Copiando o dockercompose do repositório
    ```
    docker-compose up -d
    ```
    ```
    http://localhost:5601
    ```
    - Estou utilizando a versão 7.13.0 igual a do curso para poder seguir. Os comandos abaixo foram tentativas de instalação das novas versões (8.0)
        - Irá pedir um token, para isso precisa rodar o seguinte comando:
        ```
        docker exec -it elasticsearch /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana
        ```
        ``` 
        docker exec kibana kibana-verification-code
        ```

- Aula 10: Visão geral do Kibana
    - Mostrou um pouco da ferramentas e algumas abas de onde iremos trabalhar.

- Aula 11: Metricbeat
    - Criando o arquivo metricbeats.yaml
    - Inserindo o metricbeat dentro do docker-compose
    ```
    docker-compose up -d
    ```
    - Adicionada a seguinte linha no arquivo docker-compose devido a um erro de permissão no arquivo do metricbeat.
    ```
    command: ["--strict.perms=false"]
    ```
    - Visualizando as primeiras métricas e Dashboards

- Aula 12: Uptime e Heartbeat
    - Criando o arquivo heatbeat.yaml
    ```
    docker-compose up -d
    ```
    - Inserida a mesma linha de permissão que foi colocada no arquivo do metricbeat também dentro do heartbeat.
    ```
    command: ["--strict.perms=false"]
    ```
    - Verificando a aba Uptime

- Aula 13: Configurando APM
    - Criando o arquivo apm-server.yaml
    - Inserida a mesma linha de permissão que foi colocada nos arquivos do metricbeat e do heartbeat dentro do arquivo de apm
    ```
    command: ["--strict.perms=false"]
    ```

- Aula 14: APM na prática
    - Documentação de agents de APM <https://www.elastic.co/guide/en/apm/agent/index.html>
    - Criando a pasta APP e subindo a aplicação:
    ```
    docker-compose up -d
    ```
    - Mostrando a aba do Kibana de APM
