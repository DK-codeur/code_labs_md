summary: installer flutter sur windows
id: installer-flutter-sur-windows
categories: Sample
tags: medium
status: Published 
authors: JKP-DEV
Feedback Link: https://jkp-dev.com

# Configuration requise 
Duration: 2

Pour installer et exécuter Flutter, votre environnement de développement doit répondre à ces exigences minimales :

- Systèmes d'exploitation : Windows 7 SP1 ou version ultérieure (64 bits), basé sur x86-64.
- Espace disque : 1,64 Go (n'inclut pas l'espace disque pour IDE/outils).
- Outils : Flutter dépend de la disponibilité de ces outils dans votre environnement.
Windows PowerShell 5.0 ou plus récent (préinstallé avec Windows 10)
Git pour Windows 2.x, avec l' option Utiliser Git à partir de l'invite de commande Windows.

Si Git pour Windows est déjà installé, assurez-vous que vous pouvez exécuter gitdes commandes à partir de l'invite de commande ou de PowerShell.

# Obtenir le SDK Flutter
Duration: 3

1 - Téléchargez le bundle d'installation suivant pour obtenir la dernière version stable du SDK Flutter :

[Telecharger flutter SDK](https://docs.flutter.dev/development/tools/sdk/releases)

2 - Extrayez le fichier zip et placez le contenu flutter dans l'emplacement d'installation souhaité pour le SDK Flutter (par exemple, C:\Users\<your-user-name>\Documents).


Negative
:  Attention : n'installez pas Flutter dans un répertoire C:\Program Files\qui nécessite des privilèges élevés.

Si vous ne souhaitez pas installer une version fixe du bundle d'installation, vous pouvez ignorer les étapes 1 et 2. Au lieu de cela, récupérez le code source du référentiel Flutter sur GitHub et modifiez les branches ou les balises si nécessaire. Par example:

### A command line

    ./gradlew :runTask

Vous êtes maintenant prêt à exécuter les commandes Flutter dans la console Flutter.

# Mettez à jour votre chemin
Duration: 3

Si vous souhaitez exécuter des commandes Flutter dans la console Windows standard, procédez comme suit pour ajouter Flutter à la PATHvariable d'environnement :

- Dans la barre de recherche Démarrer, saisissez « env » et sélectionnez Modifier les variables d'environnement pour votre compte.
- Sous Variables utilisateur, vérifiez s'il existe une entrée appelée Path :
  - Si l'entrée existe, ajoutez le chemin d'accès complet à flutter\binusing ;comme séparateur des valeurs existantes.
  - Si l'entrée n'existe pas, créez une nouvelle variable utilisateur nommée Pathavec le chemin complet vers flutter\bincomme valeur.

Vous devez fermer et rouvrir toutes les fenêtres de console existantes pour que ces modifications prennent effet.


Positive
:   Remarque : à partir de la version de développement 1.19.0 de Flutter, le SDK Flutter contient la dartcommande à côté de la flutter commande afin que vous puissiez exécuter plus facilement les programmes de ligne de commande Dart. Le téléchargement du SDK Flutter télécharge également la version compatible de Dart, mais si vous avez téléchargé le SDK Dart séparément, assurez-vous que la version Flutter de dartest la première dans votre chemin, car les deux versions peuvent ne pas être compatibles. La commande suivante vous indique si les commandes flutteret dart proviennent du même binrépertoire et sont donc compatibles.
