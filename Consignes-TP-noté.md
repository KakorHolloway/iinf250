# Consignes du TP 
## Préparation
Le but de ce TP est de vous faire pratiquer la syntaxe de helm. 

Récupérez les fichier yaml présent dans le dossier correction afin de pouvoir créer votre propre chart helm. 
Pour créer la charte, vous pouvez soit utiliser la commande ```helm create```, soit vous inspirer de l'exemple. 

Mettez les fichiers de la correction dans le dossier templates. 

## Instruction
Voici le modifications que je souhaite avoir pour transformer ces fichiers en une chart helm utilisable :

- Tous les objets Kubernetes doivent avoir un nom qui commence par les 6 premières lettres de votre déploiement (.Relaese.Name)
- Je veux pouvoir personnaliser l'url de ma route tout en évitant que celle-ci ne finisse pas par ".apps.openshift.kakor.ovh" (par exemple toto.toto.com ne doit pas fonctionner mais toto.apps.openshift.kakor.ovh oui) 
- Je veux que mes déploiement possèdent des labels signifiant le type d'environnement qui sera utilisé (env), tout en permettant à l'utilisateur d'en ajouter au besoin. 
- Je veux qu'à l'envie, l'utilisateur puisse créer ou non des volumes nfs. Ces volumes nfs montée sur le pod mysql sur /var/lib/mysql dépendent du server 192.168.1.56 et du path /Volume1/public/nfs-share-openshift/groupe-x
- Je veux que la version et le nom de l'image soient varaibilisés
- Je veux pouvoir personaliser le port d'écoute de mon service mysql en entrée mais que par défault si la variable n'existe pas on soit sur du 3306
- Chiffrez en amont les mots de passe en base64 en partant d'une valeur helm donnée. 
- Ajoutez la possibilité de pouvoir si on le souhaite modifier les valeurs en CPU et RAM des deployment mysql et mediawiki tout en limitant à un maximum de 1Go de ram sur les deux. 
- Créez le fichier NOTE afin que celui-ci donne l'url de la route à l'utilisateur afin qu'il puisse se connecter 

Déployez la solution sur le cluster Kubernetes mis à disposition (cf README.md)

## Pour le rendu 

Rendez-moi un fichier zip avec la chart helm mise à jour, commentez les lignes que vous avez modifier afin d'exprimer vos choix de conception (ex: #J'ai mis la fonction randNumeric car je voulais un nombre aléatoire vis à vis de l'instruction 1)

Renseignez dans un fichier README.md dans le dossier de votre chart le nom des participants.