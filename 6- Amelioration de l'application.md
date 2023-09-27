## Amelioration de l'application

### ``Connectez-vous en SSH sur le serveur CI``

### `` ssh -i trainingVM_key.pem azureuser@51.145.93.152``

``cd msdocs-python-flask-webapp-quickstart``

``nano requirements.txt``
```
flake8
yapf
```


``nnano flake8.py``
```
#!/usr/bin/env python

import sys
import subprocess

# Exécute la commande"flake8" pour vérifier la qualité du code
result = subprocess.run(["flake8"])

# Si la commande retourne un code d'erreur, affiche un message d'erreur
# et annule le commit
if result.returncode != 0:
    print("Erreur de qualité du code détectée")
    print(result)
    sys.exit(1)

# Si la commande s'exécute avec succès, affiche un message de succès
# et continue avec le commit
print("Code de qualité vérifié avec succès.")
sys.exit(0)
```


``nano Dockerfile``
```
FROM python:3.9

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Update and install system dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    curl \
    gcc \
    libc-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY app.py flake8.py requirements.txt /app/
ADD templates /app/templates
ADD static /app/static

RUN chmod -R 777 /app

RUN pip install --no-cache-dir -r requirements.txt


EXPOSE 8000

CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:8000", "app:app"]
```


``git add .``

``git commit -m "update app"``

``git push -u origin master``


```python

```
