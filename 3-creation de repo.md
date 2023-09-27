### Créer un repo github

![Texte alternatif](./images/referentiel.JPG)

### Création de token github

![Texte alternatif](./images/token1.png)
![Texte alternatif](./images/token2.png)
![Texte alternatif](./images/token3.jpg)

### ``Connectez-vous en SSH sur le serveur CI``

### `` ssh -i trainingVM_key.pem azureuser@51.145.93.152``

### Clonage du référentiel Azure sample

``git clone https://github.com/Azure-Samples/msdocs-python-flask-webapp-quickstart.git``

``cd msdocs-python-flask-webapp-quickstart``

``rm -rf .git .github``

``git init``

``git add .``

``git commit -m "Initial commit"``

``git remote add origin https://renauddahou:token@github.com/renauddahou/neosofttrain.git``

ou

``git remote set-url origin https://renauddahou:token@github.com/renauddahou/neosofttrain.git``

``git push -u origin master``


#### Testons notre applications

``sudo apt install python3-pip``

``pip3 install -r requirements.txt``

``nano app.py``

``app.run(host='0.0.0.0')``

``python3 app.py``

http://51.145.93.152:5000


```python

```
