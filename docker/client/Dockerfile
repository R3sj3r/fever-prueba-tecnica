FROM python:bookworm
WORKDIR /app
COPY . /app

RUN pip install --upgrade pip
RUN pip install -r requirements.txt
RUN cp /app/certs/server.crt /usr/local/share/ca-certificates/server.crt
RUN cp /app/certs/server.example.com.crt /usr/local/share/ca-certificates/server.example.com.crt
RUN cp /app/certs/server.local.crt /usr/local/share/ca-certificates/server.local.crt
RUN update-ca-certificates
CMD ["python", "client.py"]
