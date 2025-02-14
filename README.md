Pour vous connecter au cluster Openshift mis à disposition : 

Téléchargez sur votre machine le paquet OKD suivant : 
https://github.com/okd-project/okd/releases/download/4.15.0-0.okd-2024-03-10-010116/openshift-client-windows-4.15.0-0.okd-2024-03-10-010116.zip

Copiez le fichier oc.exe dans C:\Windows\System32

Allez sur l'url https://console-openshift-console.apps.openshift.kakor.ovh authentifiez-vous avec l'utilisateur ipi-gp-x (le x étant le numéro de groupe) en choisisant "KeystoneIDP".

Une fois authentifié (attention à ne pas recharger la page même si l'affichage prends du temps), allez en haut à droite de la page et sélectionnez l'option Copy token et réauthentifiez vous. 

Cliquez sur le lien Display Token et copiez dans votre terminal sur VScode la ligne de commande qui à été donné avec oc. 

Pour vérifier que vous êtes authentifiés, lancez la commande ```oc get pod```

Une fois authentifiez, tentez de reproduire dans votre propre repo git l'architecture présentée en créant un fichier par objet Kubernetes. 

Pour vous aider, commancez simplement à créer les deployment sans les secrets et les volumes puis ajoutez-les petits à petit. 

Les variables d'environnement à positionner dans le deployment pour mediawiki sont les suivantes :

```
MEDIAWIKI_DB_NAME
MEDIAWIKI_DB_HOST
MEDIAWIKI_DB_PORT
MEDIAWIKI_DB_USER
MEDIAWIKI_DB_PASSWORD
```

Et pour mysql :

```
MYSQL_DATABASE
MYSQL_USER
MYSQL_PASSWORD
MYSQL_ROOT_PASSWORD
```