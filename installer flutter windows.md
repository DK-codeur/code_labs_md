summary: installer flutter sur windows
id: installer-flutter-sur-windows
categories: Sample
tags: medium
status: Published 
authors: JKP-DEV
Feedback Link: https://jkp-dev.com

# INSTALLER FLUTTER SUR WINDOWS
## Configuration requise 
Duration: 2

Pour installer et exécuter Flutter, votre environnement de développement doit répondre à ces exigences minimales :

- Systèmes d'exploitation : Windows 7 SP1 ou version ultérieure (64 bits), basé sur x86-64.
- Espace disque : 1,64 Go (n'inclut pas l'espace disque pour IDE/outils).
- Outils : Flutter dépend de la disponibilité de ces outils dans votre environnement.
Windows PowerShell 5.0 ou plus récent (préinstallé avec Windows 10)
Git pour Windows 2.x, avec l' option Utiliser Git à partir de l'invite de commande Windows.

Si Git pour Windows est déjà installé, assurez-vous que vous pouvez exécuter gitdes commandes à partir de l'invite de commande ou de PowerShell.

## Obtenir le SDK Flutter
Duration: 3

1 - Téléchargez le bundle d'installation suivant pour obtenir la dernière version stable du SDK Flutter :

[Telecharger flutter SDK](https://docs.flutter.dev/development/tools/sdk/releases)

2 - Extrayez le fichier zip et placez le contenu flutter dans l'emplacement d'installation souhaité pour le SDK Flutter (par exemple, C:\Users\<your-user-name>\Documents).


Negative
:  Attention : n'installez pas Flutter dans un répertoire C:\Program Files\qui nécessite des privilèges élevés.

Si vous ne souhaitez pas installer une version fixe du bundle d'installation, vous pouvez ignorer les étapes 1 et 2. Au lieu de cela, récupérez le code source du référentiel Flutter sur GitHub et modifiez les branches ou les balises si nécessaire. Par example:

### 
    git clone https://github.com/flutter/flutter.git -b stable


Vous êtes maintenant prêt à exécuter les commandes Flutter dans la console Flutter.

## Mettez à jour votre chemin
Duration: 3

Si vous souhaitez exécuter des commandes Flutter dans la console Windows standard, procédez comme suit pour ajouter Flutter à la PATHvariable d'environnement :

- Dans la barre de recherche Démarrer, saisissez « env » et sélectionnez Modifier les variables d'environnement pour votre compte.
- Sous Variables utilisateur, vérifiez s'il existe une entrée appelée Path :
  - Si l'entrée existe, ajoutez le chemin d'accès complet à flutter\binusing ;comme séparateur des valeurs existantes.
  - Si l'entrée n'existe pas, créez une nouvelle variable utilisateur nommée Pathavec le chemin complet vers flutter\bincomme valeur.

Vous devez fermer et rouvrir toutes les fenêtres de console existantes pour que ces modifications prennent effet.


Positive
:   Remarque : à partir de la version de développement 1.19.0 de Flutter, le SDK Flutter contient la dartcommande à côté de la flutter commande afin que vous puissiez exécuter plus facilement les programmes de ligne de commande Dart. Le téléchargement du SDK Flutter télécharge également la version compatible de Dart, mais si vous avez téléchargé le SDK Dart séparément, assurez-vous que la version Flutter de dartest la première dans votre chemin, car les deux versions peuvent ne pas être compatibles. La commande suivante vous indique si les commandes flutteret dart proviennent du même binrépertoire et sont donc compatibles.


### 
    where flutter dart
    C:\path-to-flutter-sdk\bin\flutter
    C:\path-to-flutter-sdk\bin\flutter.bat
    C:\path-to-dart-sdk\bin\dart.exe        :: this should go after `C:\path-to-flutter-sdk\bin\`   commands
    C:\path-to-flutter-sdk\bin\dart
    C:\path-to-flutter-sdk\bin\dart.bat

Positive
: Comme indiqué ci-dessus, la commande dartdu SDK Flutter ne vient pas en premier. Mettez à jour votre chemin pour utiliser les commandes d' C:\path-to-flutter-sdk\bin\avant les commandes de C:\path-to-dart-sdk\bin\(dans ce cas). Après avoir redémarré votre shell pour que la modification prenne effet, la réexécution de la wherecommande devrait indiquer que les commandes flutteret dartdu même répertoire viennent désormais en premier.

### 
    C:\>where flutter dart
    C:\dev\src\flutter\bin\flutter
    C:\dev\src\flutter\bin\flutter.bat
    C:\dev\src\flutter\bin\dart
    C:\dev\src\flutter\bin\dart.bat
    C:\dev\src\dart-sdk\bin\dart.exe

Positive
: Cependant, si vous utilisez PowerShell, il wheres'agit d'un alias de Where-Objectcommande, vous devez donc l'utiliser à la where.exeplace.

###
    PS C:\> where.exe flutter dart
Pour en savoir plus sur la dartcommande, exécutez -la à dart -h partir de la ligne de commande ou consultez la page de l' outil de fléchettes .

## Excecuter flutter doctor
Duration: 1
À partir d'une fenêtre de console dont le chemin contient le répertoire Flutter (voir ci-dessus), exécutez la commande suivante pour voir s'il existe des dépendances de plate-forme dont vous avez besoin pour terminer la configuration :
###
    C:\src\flutter>flutter doctor

Cette commande vérifie votre environnement et affiche un rapport sur l'état de votre installation Flutter. Vérifiez attentivement la sortie pour d'autres logiciels que vous pourriez avoir besoin d'installer ou d'autres tâches à effectuer (indiquées en gras ).

Par example:
###
    [-] Android toolchain - develop for Android devices
    • Android SDK at D:\Android\sdk
    ✗ Android SDK is missing command line tools; download from https://goo.gl/XxQghQ
    • Try re-installing or updating your Android SDK,
      visit https://docs.flutter.dev/setup/#android-setup for detailed instructions.

Les sections suivantes décrivent comment effectuer ces tâches et terminer le processus de configuration. Une fois que vous avez installé toutes les dépendances manquantes, vous pouvez réexécuter la flutter doctorcommande pour vérifier que vous avez tout configuré correctement.

Positive
:  Remarque : Si flutter doctorle plug-in Flutter ou le plug-in Dart d'Android Studio ne sont pas installés, passez à Configurer un éditeur pour résoudre ce problème.

Negative
: Avertissement : L'outil Flutter peut occasionnellement télécharger des ressources à partir des serveurs de Google. En téléchargeant ou en utilisant le SDK Flutter, vous acceptez les conditions d'utilisation de Google .

Par exemple, lorsqu'il est installé à partir de GitHub (par opposition à une archive préemballée), l'outil Flutter téléchargera le SDK Dart à partir des serveurs Google immédiatement lors de la première exécution, car il est utilisé pour exécuter l' flutteroutil lui-même. Cela se produira également lorsque Flutter est mis à jour (par exemple en exécutant la flutter upgradecommande).

L' flutteroutil utilise Google Analytics pour rapporter les statistiques d'utilisation des fonctionnalités et envoyer des rapports de plantage . Ces données sont utilisées pour aider à améliorer les outils Flutter au fil du temps.

Les analyses de l'outil Flutter ne sont pas envoyées lors de la toute première exécution. Pour désactiver la création de rapports, exécutez flutter config --no-analytics. Pour afficher le réglage actuel, utilisez flutter config. Si vous désactivez l'analyse, un événement de désactivation est envoyé, puis aucune autre information n'est envoyée par l'outil Flutter.

Les outils Dart peuvent également envoyer des statistiques d'utilisation et des rapports d'erreur à Google. Pour contrôler la soumission de ces métriques, utilisez les options suivantes sur l' dartoutil :

--enable-analytics: Active l'analyse anonyme.
--disable-analytics: désactive l'analyse anonyme.
La politique de confidentialité de Google décrit la manière dont les données sont traitées par ces services.

## Configuration Androïd
Duration: 3
Positive
:  Remarque : Flutter s'appuie sur une installation complète d'Android Studio pour fournir ses dépendances de plateforme Android. Cependant, vous pouvez écrire vos applications Flutter dans un certain nombre d'éditeurs ; une étape ultérieure en parle.

### Installer AndroidStudio
1 - Téléchargez et installez Android Studio.

2 - Démarrez Android Studio et passez par «l'assistant de configuration d'Android Studio».
Cela installe le dernier SDK Android, les outils de ligne de commande du SDK Android et les outils de construction du SDK Android, qui sont requis par Flutter lors du développement pour Android.

3 - Exécutez flutter doctorpour confirmer que Flutter a localisé votre installation d'Android Studio. Si Flutter ne peut pas le localiser, exécutez flutter config --android-studio-dir <directory>pour définir le répertoire dans lequel Android Studio est installé.


### Configurer votre appareil Android
Pour préparer l'exécution et le test de votre application Flutter sur un appareil Android, vous avez besoin d'un appareil Android exécutant Android 4.1 (API niveau 16) ou supérieur.

1 - Activez les options de développeur et le débogage USB sur votre appareil. Des instructions détaillées sont disponibles dans la documentation Android .

2 - Windows uniquement : installez le pilote USB Google .

3 - À l'aide d'un câble USB, branchez votre téléphone à votre ordinateur. Si vous y êtes invité sur votre appareil, autorisez votre ordinateur à accéder à votre appareil.

4 - Dans le terminal, exécutez la flutter devicescommande pour vérifier que Flutter reconnaît votre appareil Android connecté. Par défaut, Flutter utilise la version du SDK Android sur laquelle adb est basé votre outil. Si vous souhaitez que Flutter utilise une installation différente du SDK Android, vous devez définir la ANDROID_SDK_ROOTvariable d'environnement sur ce répertoire d'installation.


### Configurer l'émulateur Android
Pour préparer l'exécution et le test de votre application Flutter sur l'émulateur Android, suivez ces étapes :

1 - Activez l'accélération de VM sur votre ordinateur.

2 - Lancez Android Studio , cliquez sur l' icône AVD Manager et sélectionnez Créer un périphérique virtuel…
  - Dans les anciennes versions d'Android Studio, vous devez plutôt lancer Android Studio > Tools > Android > AVD Manager et sélectionner Create Virtual Device… . (Le sous-menu Android n'est présent que dans un projet Android.)
  - Si vous n'avez pas de projet ouvert, vous pouvez choisir Configurer > AVD Manager et sélectionner Créer un périphérique virtuel…
  - 
3 - Choisissez une définition de périphérique et sélectionnez Suivant .

4 - Sélectionnez une ou plusieurs images système pour les versions d'Android que vous souhaitez émuler, puis sélectionnez Suivant . Une image x86 ou x86_64 est recommandée.

5 - Sous Performances émulées, sélectionnez Matériel - GLES 2.0 pour activer l'accélération matérielle .

6 - Vérifiez que la configuration AVD est correcte et sélectionnez Terminer .
Pour plus de détails sur les étapes ci-dessus, voir [Gestion des AVD](https://developer.android.com/studio/run/managing-avds) .

7 - Dans Android Virtual Device Manager, cliquez sur Exécuter dans la barre d'outils. L'émulateur démarre et affiche le canevas par défaut pour la version du système d'exploitation et l'appareil que vous avez sélectionnés.

### Accepter les licences Android
Avant de pouvoir utiliser Flutter, vous devez accepter les licences de la plateforme Android SDK. Cette étape doit être effectuée après avoir installé les outils répertoriés ci-dessus.

1 - Assurez-vous qu'une version de Java 8 est installée et que votre JAVA_HOMEvariable d'environnement est définie sur le dossier du JDK.

Les versions 2.2 et supérieures d'Android Studio sont livrées avec un JDK, cela devrait donc déjà être fait.

2 - Ouvrez une fenêtre de console élevée et exécutez la commande suivante pour commencer à signer des licences.

###
    $  flutter doctor --android-licenses
3 - Lisez attentivement les termes de chaque licence avant de les accepter.

4 - Une fois que vous avez fini d'accepter les licences, exécutez flutter doctorà nouveau pour confirmer que vous êtes prêt à utiliser Flutter.


## L'installation de Windows
Duration: 2

Negative
:  Attention : Bêta (Win32) et Alpha (UWP) ! Cette zone couvre la prise en charge du bureau Windows, qui est disponible en version bêta (Win32) et en version alpha (UWP). La variante UWP est prise en charge par la communauté.

Vous pouvez essayer un instantané bêta de la prise en charge du bureau Win32 sur le canal stable, ou vous pouvez suivre les dernières modifications apportées au bureau sur le betacanal. Pour Windows UWP, vous devez être sur le mastercanal.

Pour plus d'informations, consultez la section Bureau dans Quoi de neuf dans Flutter 2.2 , un article gratuit sur Medium.

### Exigences Windows supplémentaires
Pour le développement de bureau Windows, vous avez besoin des éléments suivants en plus du SDK Flutter :
  - Visual Studio 2022 pour Flutter 2.9 beta et versions ultérieures, Visual Studio 2019 pour Flutter 2.8.1 et versions antérieures. Notez que Visual Studio est différent de Visual Studio Code . Pour Win32, vous devez installer la charge de travail "Développement de bureau avec C++", y compris tous ses composants par défaut. Pour UWP, vous devez installer la charge de travail "Développement de la plate-forme Windows universelle", avec les outils UWP C++ en option.

### Activer la prise en charge du bureau
Sur la ligne de commande, exécutez la commande suivante pour activer la prise en charge du bureau Win32 :

###
    $ flutter config --enable-windows-desktop

Pour la prise en charge du bureau Windows UWP, exécutez les commandes suivantes pour basculer vers le mastercanal, mettre à niveau Flutter et activer UWP.
###
    $ flutter channel master
    $ flutter upgrade
    $ flutter config --enable-windows-uwp-desktop

Pour plus d'informations, voir [Prise en charge de bureau pour Flutter](https://docs.flutter.dev/desktop)

## Configuration Web
Duration: 2

Flutter prend en charge la création d'applications Web dans le stablecanal. Toute application créée dans Flutter 2 se construit automatiquement pour le Web. Pour ajouter la prise en charge Web à une application créée avant que le Web ne soit stable, suivez les instructions sur la [création d'une application Web avec Flutter](https://docs.flutter.dev/get-started/web) lorsque vous avez terminé la configuration ci-dessus.


## Configurer un éditeur
Duration: 3

Vous pouvez créer des applications avec Flutter à l'aide de n'importe quel éditeur de texte combiné à nos outils de ligne de commande. Cependant, nous vous recommandons d'utiliser l'un de nos plugins d'éditeur pour une expérience encore meilleure. Ces plugins vous fournissent la complétion de code, la coloration syntaxique, les aides à l'édition de widgets, la prise en charge de l'exécution et du débogage, etc.

Suivez les étapes ci-dessous pour ajouter un plugin d'éditeur pour Android Studio, IntelliJ, VS Code ou Emacs. Si vous souhaitez utiliser un autre éditeur, ce n'est pas grave, passez à [l' étape suivante : Test drive](https://docs.flutter.dev/get-started/test-drive).

### Installer le VS code 
VS Code est un éditeur léger avec prise en charge de l'exécution et du débogage de l'application Flutter.
  - [VS Code](https://code.visualstudio.com/) , dernière version stable

### Installez les plugins Flutter et Dart

1 - Démarrez le code VS.

2 - Appelez Affichage > Palette de commandes… .

3 - Tapez "installer" et sélectionnez Extensions : Installer les extensions .

4 - Tapez "flutter" dans le champ de recherche des extensions, sélectionnez Flutter dans la liste, puis cliquez sur Installer . Cela installe également le plugin Dart requis.

### Validez votre configuration avec le Flutter Doctor
1 - Appelez Affichage > Palette de commandes… .
2 - Tapez "docteur" et sélectionnez Flutter : Exécuter Flutter Doctor .
3 - Examinez la sortie dans le volet OUTPUT pour tout problème. Assurez-vous de sélectionner Flutter dans la liste déroulante des différentes options de sortie.

## Conclusion
Merci. etape Suivante, [créer votre première applicatin flutter](http://jkp-dev.com)


