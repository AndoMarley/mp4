
## 1 - Importer le fichier csv (liste des comptes à supprimer)
Allez dans **"input_file_test/local_project/input_file_test_0_1/contexts"** et editez le fichier Default.properties en indiquant le chemin du fichier csv à importer : 
```{}
csv_file=[chemin exacte de votre fichier]
```
vérifier ensuite si le séparateur de votre fichier csv est un:  **";"** ou un **","** (valeur par defaut: ";")
```
Separator=;
```

Notre programme est constitué de 2 job différents consistant à désactiver d'abords le compte utilisateur avant de le supprimer définitivement.

## 2 - Connection xmlrpc, Méthode désactivation compte
Allez ensuite dans **"delete/local_project/disabled_process/contexts"** puis editez Default.properties.
le context **url** doit être précis en fonction (port) de votre point de connexion (serveur interne, ...). 


```
url=http\://monbureau.univ-reunion.fr:8000/xmlrpc
username=administrator
password=ID7Jif1E
Method=account.setState
login=context.Login
```

Le context "Method" indique la méthode qu'on va appliqué 
```
Method=account.setState #pour_désactiver_le_compte
```

## 3 - Connection xmlrpc, Méthode de suppression du compte

Allez  dans **"delete/local_project/deleting_process/contexts"** puis editez Default.properties.
La configuration du context **url** doit être identique au précédent.


```
url=http\://monbureau.univ-reunion.fr:8000/xmlrpc
username=administrator
password=ID7Jif1E
Method=account.delete
login=context.Login
```

C'est le context "Method" qui doit être changé pour effectuer la suppression 
```
Method=account.delete 
```
Indiquer ensuite dans le context **output_log** le chemin où vous allez exporter le fichier log.


## 4 - Execution du programme
Allez dans le repertoire **/delete/** et lancez ensuite le fichier **"delete_run.sh"** pour Mac et Linux (et **.bat** pour windows)

Linux/Mac
```
sudo sh delete_run.sh
```

Windows
```
start delete_run.bat
```
