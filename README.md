# IINF250
## Connection au cluster Openshift
Pour vous connecter au cluster Openshift mis à disposition : 

Téléchargez sur votre machine le paquet OKD suivant : 
https://github.com/okd-project/okd/releases/download/4.15.0-0.okd-2024-03-10-010116/openshift-client-windows-4.15.0-0.okd-2024-03-10-010116.zip

Copiez le fichier oc.exe dans C:\Windows\System32

Allez sur l'url https://console-openshift-console.apps.openshift.kakor.ovh authentifiez-vous avec l'utilisateur ipi-gp-x (le x étant le numéro de groupe) en choisisant "KeystoneIDP".

Une fois authentifié (attention à ne pas recharger la page même si l'affichage prends du temps), allez en haut à droite de la page et sélectionnez l'option "Copy login Command" et réauthentifiez vous. 

Cliquez sur le lien Display Token et copiez dans votre terminal sur VScode la ligne de commande qui à été donné avec oc. 

Pour vérifier que vous êtes authentifiés, lancez la commande ```oc get pod```

## Création de l'environnement

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

## Installez Helm 

Téléchargez le binaire pour votre machine (ex WIndows sur un CPU intel ou AMD) : https://get.helm.sh/helm-v3.17.2-windows-amd64.zip
Pour les autres possibilités allez sur ce lien : https://github.com/helm/helm/releases/tag/v3.17.2

Créez un dossier C:/exe, mettez dans ce dossier le fichier helm.exe présent dans l'archive. 

Modifiez le path de votre windows via l'outil **Modifiier les Variables d'environnement système** (Variables d'environnement > Path (double click) > Nouveau et mettez C:\exe). 

Enregistrez et quitter les modifications. 

Pour vérifier que ça marche, réouvrez visual studio code ou une fenêtre Powershell pour tester d'exécuter des commandes ```helm --help```

## Débutez dans Helm
Lien vers la doc: 
https://helm.sh/docs/chart_template_guide/builtin_objects/

Afin de créer votre premier repo helm, vous pouvez utiliser la commande suivante :
```
helm create <nomdurepo>
```

Une fois la chart helm générée, vous pouvez supprimer le contenu du dossier templates, et vider le contenu du fichier values.yaml

Pendant la rédaction de la chart helm, vous pouvez utiliser la commande ```helm template monrepo monrepo/ -f monrepo/values.yaml``` pour vérifier le fonctionnement de votre chart. 

Afin de commencer la mise en place de la chart de TP, l'on peut récupérer les fichier yaml présents dans le dossier correction. 
