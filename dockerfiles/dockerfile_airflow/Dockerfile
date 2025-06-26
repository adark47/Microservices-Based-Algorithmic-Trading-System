FROM bitnami/airflow:latest
# apache/airflow:latest - the latest released Airflow image with default Python version (3.12 currently)
# apache/airflow:latest-pythonX.Y - the latest released Airflow image with specific Python version
# apache/airflow:3.1.0 - the versioned Airflow image with default Python version (3.12 currently)
# apache/airflow:3.1.0-pythonX.Y - the versioned Airflow image with specific Python version

USER root
#COPY requirements.txt /requirements.txt
COPY requirements.txt /tmp/requirements.txt
RUN pip install -r /tmp/requirements.txt

ENV PYTHONPATH "${PYTHONPATH}:/usr/local/airflow/dags/q_pack"
# For airflow container defining the environment variables in the docker compose doesnt work except for the airflow variables
ENV MLFLOW_S3_ENDPOINT_URL "http://minio-image:9000"
ENV AWS_ACCESS_KEY_ID "minio-image"
ENV AWS_SECRET_ACCESS_KEY "minio-image-pass"
ENV MLFLOW_TRACKING_URI "http://mlflow-image:5500"

RUN airflow db migrate