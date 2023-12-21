### Pour lancer le minikube

`minikube start`

### Lancer le namespace pour pouvoir y greffer les secrets
`kubectl apply -f wordpress-ns`

### Création des secrets
`kubectl create secret generic mariadb --from-literal=MYSQL_ROOT_PASSWORD=wordpress --from-literal=MYSQL_DATABASE=wordpress --from-literal=MYSQL_USER=wordpress --from-literal=MYSQL_PASSWORD=wordpress -n wordpress-ns`

`kubectl create secret generic wordpress --from-literal=WORDPRESS_DB_USER=wordpress --from-literal=WORDPRESS_DB_PASSWORD=wordpress --from-literal=WORDPRESS_DB_NAME=wordpress -n wordpress-ns`

### Pour lancer la construction (aller dans le dossier où se trouve les fichiers de déploiement)

`kubectl apply -f .`

#### (Si besoin de détruire, effectuer cette commande puis attendre quelques secondes)

`kubectl delete -f .`

### Pour lancer un tunnel qui traverse WLS (entre le service à contacter et l'ordinateur local)

`minikube tunnel`


### Se rendre sur l'URL depuis le navigateur local

---------------------------

## Commande complète pour tout lancer :
`clear
kubectl delete -f .
sleep 10
echo "création du namespace..."
kubectl apply -f kube.ns.yml
echo "Génération des secrets..."
kubectl create secret generic mariadb --from-literal=MYSQL_ROOT_PASSWORD=wordpress --from-literal=MYSQL_DATABASE=wordpress --from-literal=MYSQL_USER=wordpress --from-literal=MYSQL_PASSWORD=wordpress -n wordpress-ns 
kubectl create secret generic wordpress --from-literal=WORDPRESS_DB_USER=wordpress --from-literal=WORDPRESS_DB_PASSWORD=wordpress --from-literal=WORDPRESS_DB_NAME=wordpress -n wordpress-ns
echo "Lancement des pods..."
kubectl apply -f . 
echo "Lancement des pods terminé ! Veuillez patienter 20 secondes avant de visiter l'URL (temps de lancement de la DB)"

`


