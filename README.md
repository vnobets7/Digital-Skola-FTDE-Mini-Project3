![image](https://github.com/vnobets7/Digital-Skola-FTDE-Mini-Project3/blob/main/images/apache-spark-only-icon.png)

# Digital-Skola-FTDE-Mini-Project3
## Deskripsi Mini-Project3
Bagian dari tugas Fast-Track homework, yang merupakan tugas individual. Membuat Batch data processing menggunakan apache spark/pyspark dan orchestration dengan Apache Airflow.

## Data stack
- Postgres (source)
- TiDB (data warehouse)
- Docker/Docker desktop/WSL2+Ubuntu+Docker
- Apache spark/pyspark
- Apache airflow
- Pandas library
- Postman
- Dbeaver

##  Simple Project Architecture
Berikut ini merupakan ilustrasi dari project yang dibuat. <br>
![Project Architecture](https://github.com/vnobets7/Digital-Skola-FTDE-Mini-Project2/blob/main/images/Project-architecture.png)

## Getting Started
1. Clone the repository:
    ```bash
    git clone https://github.com/airscholar/e2e-data-engineering.git
    ```

2. Navigate to the project directory:
   ```
   cd Digital-Skola-FTDE-Mini-Project3
   ```

3. Create docker volume
   ```
   docker volume create postgres_airflow
   ```

4. Create your docker images
   ```
   docker build -t my-airflow .
   ```

5. Starts the containers in the background
   ```
   docker compose up -d
   ```

6. Run the docker environment env
   ```
   docker run --mount
   ```

7.  Make sure that no containers are in an good condition
   ```
   docker ps
   ```

8. Open port 8080 and check airflow on web if UI airflow already running

9. Set db connection on airflow
* postgresDB
   ```
   create database connection postgres DB on dbeaver
   ```
* TiDB
   ```
   create database connection TiDB on dbeaver
   ```

10. Login into your airflow account on UI airflow

11. Check if d_1_batch_processing_spark exists

11. Trigger the DAG grom the tree view

## Data Pipeline
### The DAG list
![DAG-list](https://github.com/vnobets7/Digital-Skola-FTDE-Mini-Project3/blob/main/images/DAG-list.PNG)

### The graph view
![airflow-task](https://github.com/vnobets7/Digital-Skola-FTDE-Mini-Project3/blob/main/images/airflow-task.PNG)

## Confirm the data 
### Check data already exists on TiDB
![dbeaver-TiDB](https://github.com/vnobets7/Digital-Skola-FTDE-Mini-Project3/blob/main/images/dbeaver-TiDB.png)

### Check data already exists with docker
   ```
   docker exec -it [images id] bash
   ```
* Output:
![data-on-TiDB](https://github.com/vnobets7/Digital-Skola-FTDE-Mini-Project3/blob/main/images/data-on-TiDB.PNG)

## API Spec on TiDB
### top_country_ricky API
Request: 
- Method : GET
- Endpoint :
- Header :
    - Accept: application/json

Response:
```
{
  "type": "sql_endpoint",
  "data": {
    "columns": [
      {
        "col": "index",
        "data_type": "BIGINT",
        "nullable": true
      },
      {
        "col": "country",
        "data_type": "VARCHAR",
        "nullable": true
      },
      {
        "col": "total",
        "data_type": "BIGINT",
        "nullable": true
      },
      ...
      {
        "country": "Netherlands",
        "date": "2024-09-05",
        "index": "108",
        "total": "5"
      }
    ],
    "result": {
      "code": 200,
      "message": "Query OK!",
      "start_ms": 1725719752054,
      "end_ms": 1725719752784,
      "latency": "730ms",
      "row_count": 109,
      "row_affect": 0,
      "limit": 1000
    }
  }
}
```
