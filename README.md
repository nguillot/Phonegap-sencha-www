# Regroupement des projets android et ios

L'idée est d'avoir un projet regroupement le code commun entre IOS et android. Il sera utilisé inclus dans les projets Android et IOS.

Voici l'organisation des projets:
```
Phonegap-sencha-www
   '- www <-----------------code communs
Phonegap-sencha-ios
   |- code spécifique à IOS
   '- www <-----------------sous module git (ou utilisation des svn externals) pour inclure le projet web
   
Phonegap-sencha-android
   |- code spécifique à android
   '- www <-----------------sous module git (ou utilisation des svn externals) pour inclure le projet web   
```

## Création du projet WWW
 * créer un nouveau répertoire pour votre projet web
 * copier le fichier `cordova-2.1.0.js`du projet android dans le projet web sous le nom `cordova-2.1.0-android.js`
 * copier le fichier `cordova-2.1.0.js`du projet ios dans le projet web sous le nom `cordova-2.1.0-ios.js`
 * créer le fichier `cordova-loader.js` pour avoir

```javascript
function isAndroid(){
    return navigator.userAgent.indexOf("Android") > 0;
}

function isiOS(){
    return ( navigator.userAgent.indexOf("iPhone") > 0 || navigator.userAgent.indexOf("iPad") > 0
        || navigator.userAgent.indexOf("iPod") > 0);
}

if(isAndroid()){
    document.write('<script charset="utf-8" src="cordova-2.1.0-android.js"><\/script>');
}else if(isiOS()){
    document.write('<script charset="utf-8" src="cordova-2.1.0-ios.js"><\/script>');
}
```

 * dans le projet web, créer le fichier `index.html` pour avoir
  
```html
<html>
  <head>
    <meta name="viewport" content="width=320; user-scalable=no" />
    <meta http-equiv="Content-type" content="text/html; charset=utf-8">
    <title>PhoneGap</title>
    <script type="text/javascript" charset="utf-8" src="cordova-loader.js"></script>
    <script type="text/javascript">
        document.addEventListener("deviceready", function () {
            alert('Our first PhoneGap app');
        }, false);
     </script>
  </head>
  <body id="stage" class="theme">
    <h1>Welcome to Cordova!</h1>
  </body>
</html>
```

 * enregistrez votre projet sous github (commandes à tapper dans un terminal à la racine de votre projet):
```
  $ git init

  $ git add .

  $ git commit -m "first commit"
  
  $ git remote add origin https://github.com/nguillot/Phonegap-sencha-www.git
  
  $ git push -u origin master
```   

Votre repository est désormais sur github!


