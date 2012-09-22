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
 * copier les sources du répertoire `assets/www` de votre projet android vers votre projet web
 * dans le projet web renommer `cordova-2.1.0.js`en `cordova-2.1.0-android.js`
 * copier le fichier `cordova-2.1.0.js`du projet ios dans le projet web sous le nom `cordova-2.1.0-ios.js`
 * dans le projet web, modifier le fichier `index.html`pour avoir
  
```html
<html>
  <head>
    <meta name="viewport" content="width=320; user-scalable=no" />
    <meta http-equiv="Content-type" content="text/html; charset=utf-8">
    <title>PhoneGap</title>
      <link rel="stylesheet" href="master.css" type="text/css" media="screen" title="no title">
<scripttype="text/javascript">
// <![CDATA[
if (navigator.userAgent.toLowerCase().match(/android/)) {

document.write('<script charset="utf-8" src="cordova-2.1.0-android.js"><\/script>');

} else if (navigator.userAgent.toLowerCase().match(/iphone/) 
   || navigator.userAgent.toLowerCase().match(/ipod/) 
	|| navigator.userAgent.toLowerCase().match(/ipad/)) {

document.write('<script charset="utf-8" src="cordova-2.1.0-ios.js"><\/script>');

}
// ]]>      
      <script type="text/javascript" charset="utf-8" src="main.js"></script>

  </head>
  <body onload="init();" id="stage" class="theme">
    <h1>Welcome to Cordova!</h1>
    <h2>this file is located at assets/www/index.html</h2>
    <div id="info">
        <h4>Plateform is ready: <span id="isReady"> &nbsp;</span></h4>
        <h4>Platform: <span id="platform"> &nbsp;</span>,   Version: <span id="version">&nbsp;</span></h4>
        <h4>Name: <span id="name">&nbsp;</span></h4>
        <h4>Width: <span id="width"> &nbsp;</span>,   Height: <span id="height">&nbsp;</span></h4>
     </div>
    <a href="#" class="btn large" onclick="getLocation();">Get Location</a>
    <a href="#" class="btn large" onclick="check_network();return false;">Check Network</a>
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


