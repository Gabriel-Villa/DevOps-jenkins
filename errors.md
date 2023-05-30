
### 1. El error que estás experimentando se debe a que la shell Zsh está interpretando los corchetes [ y ] como caracteres especiales y está intentando realizar una coincidencia de patrones en el archivo del keyring 

Change 

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

to

echo 'deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/' | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null


### 2. If lost the password

Edit the file:
```
sudo nano /var/lib/jenkins/config.xml
```

Change useSecurity to ***false*** 

```
<useSecurity>false</useSecurity>
```

Restart the service