Pour lancer le minikube
`minikube start`

Pour lancer la construction (aller dans le dossier où se trouve les fichiers de déploiement)
`kubectl apply -f .`

(Si besoin de détruire, effectuer cette commande puis attendre quelques secondes)
`kubectl delete -f .`

Pour lancer un tunnel qui traverse WLS (entre le service à contacter et l'ordinateur local)
`minikube tunnel`

Se rendre sur l'URL depuis le navigateur local



