# Regroupement des projets android et ios

L'idée est d'avoir un projet regroupement le code commun entre IOS et android. Il sera utilisé inclus dans les projets Android et IOS.

Voici l'organisation des projets:
Phonegap-sencha-www
   '- www <-----------------code communs

Phonegap-sencha-ios
   |- code spécifique à IOS
   '- www <-----------------sous module git (ou utilisation des svn externals) pour inclure le projet web
   
Phonegap-sencha-android
   |- code spécifique à android
   '- www <-----------------sous module git (ou utilisation des svn externals) pour inclure le projet web   

## Création du projet WWW
 * créer un nouveau répertoire pour votre projet web
 * copier les sources du répertoire `assets/www` de votre projet android

## Mis en place sous Github
Votre repository est désormais sur github!


