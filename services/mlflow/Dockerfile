FROM python:3.8.2
# Installing packages from PyPi
RUN pip install mlflow[extras]==2.0.1 && \
    pip install psycopg2-binary==2.8.5 && \
    pip install boto3==1.15.16
# Defining start up command
EXPOSE 5000
ENTRYPOINT ["mlflow", "server"]