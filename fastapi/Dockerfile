FROM python:3.11-bullseye

# uncomment if using pyodbc for sqlserver connections
# RUN apt-get update
# RUN apt-get -y install curl

# RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
# RUN curl https://packages.microsoft.com/config/debian/11/prod.list > /etc/apt/sources.list.d/mssql-release.list
# RUN apt-get update
# RUN ACCEPT_EULA=Y apt-get -y install msodbcsql18 unixodbc-dev

COPY src /src
COPY app.py /app.py
COPY config.py /config.py
COPY manager.py /manager.py
COPY requirements.txt /requirements.txt

RUN pip install --upgrade pip
RUN pip install -r /requirements.txt

ENV TZ=America/Edmonton

EXPOSE 5000

CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "5000"]