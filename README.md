# Развертывание Airflow на виртуальной машине через Docker Compose

## Шаг 1. Подключитесь к виртуальной машине по SSH
<img width="736" alt="image" src="https://user-images.githubusercontent.com/97543975/174013696-8b5049e2-5a55-4932-81bd-6453c63ce162.png">

## Шаг 2. Клонируйте этот репозиторий на виртуальную машину
```
sudo apt install git
git clone https://github.com/gonshteinoleg/Airflow.git
```
<img width="738" alt="image" src="https://user-images.githubusercontent.com/97543975/174015597-83734b74-1679-4f9e-a8b2-fe7f5e6fe248.png">

## Шаг 3. Добавьте необходимые библиотеки в файл requirements.txt
```
nano requirements.txt
```
<img width="734" alt="image" src="https://user-images.githubusercontent.com/97543975/174016037-4e827328-1c54-47ee-b6d2-1319435719c0.png">

## Шаг 4. Создайте репозиторий для хранения дагов
<img width="922" alt="image" src="https://user-images.githubusercontent.com/97543975/174017085-fc8ae021-69d2-4348-8dd5-aa9621aa76f8.png">

## Шаг 5. Добавьте в созданный репозиторий даг
В качестве примера, можете использовать этот
```
from datetime import datetime
from airflow import DAG
from airflow.operators.dummy_operator import DummyOperator
from airflow.operators.python_operator import PythonOperator

def print_hello():
    return 'Hello world!'

dag = DAG('hello_world', description='Hello World DAG',
          schedule_interval='0 12 * * *',
          start_date=datetime(2017, 3, 20), catchup=False)

hello_operator = PythonOperator(task_id='hello_task', 
                                python_callable=print_hello, 
                                dag=dag)

hello_operator
```
