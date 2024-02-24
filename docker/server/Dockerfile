FROM python:bookworm
WORKDIR /app
RUN apt-get update && apt-get install -y ca-certificates
#COPY certs/rootCA.pem /usr/local/share/ca-certificates/
RUN update-ca-certificates

COPY . /app


RUN pip install --upgrade pip
#RUN pip freeze requirements.txtx
RUN pip install -r requirements.txt
EXPOSE 5000


CMD ["python", "server.py"]
