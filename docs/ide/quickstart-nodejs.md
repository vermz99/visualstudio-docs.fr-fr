---
title: 'Démarrage rapide : Utiliser Visual Studio pour créer votre première application Node.js'
description: Dans ce guide de démarrage rapide, vous créez une application Node.js dans Visual Studio
ms.date: 06/27/2018
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 79197d99ea04d95c369738af5832f70f4f7dc7e7
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355297"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Démarrage rapide : Utiliser Visual Studio pour créer votre première application Node.js

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application Node.js simple.

## <a name="prerequisites"></a>Prérequis

* Au préalable, vous devez avoir installé Visual Studio et la charge de travail de développement Node.js.

    ::: moniker range=">=vs-2019"
    Si vous n’avez pas encore installé Visual Studio 2019, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/)  pour l’installer gratuitement.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si vous n’avez pas encore installé Visual Studio 2017, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/)  pour l’installer gratuitement.
    ::: moniker-end

    Si vous devez installer la charge de travail, mais que vous avez déjà installé Visual Studio, cliquez sur **Outils** > **Obtenir les outils et fonctionnalités...**, qui ouvre Visual Studio Installer. Choisissez la charge de travail **Développement Node.js**, puis choisissez **Modifier**.

    ![Charge de travail Node.js dans Visual Studio Installer](../ide/media/quickstart-nodejs-workload.png)

* Le runtime Node.js doit être installé.

    Si vous ne l’avez pas déjà fait, installez la version LTS à partir du site web [Node.js](https://nodejs.org/en/download/). En règle générale, Visual Studio détecte automatiquement le runtime Node.js installé. S’il ne détecte aucun runtime installé, vous pouvez configurer votre projet pour référencer le runtime installé dans la page de propriétés (après avoir créé un projet, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Propriétés**).

## <a name="create-a-project"></a>Créer un projet

Vous allez d’abord créer un projet d’application web Node.js.

1. Si le runtime Node.js n’est pas déjà installé, installez la version LTS à partir du site web [Node.js](https://nodejs.org/en/download/).

    En règle générale, Visual Studio détecte automatiquement le runtime Node.js installé. S’il ne détecte aucun runtime installé, vous pouvez configurer votre projet pour référencer le runtime installé dans la page de propriétés (après avoir créé un projet, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Propriétés**).

1. Ouvrez Visual Studio.

1. Créer un nouveau projet.

    ::: moniker range=">=vs-2019"
    Tapez **Ctrl+Q** pour ouvrir la zone de recherche, tapez **Node.js**, puis choisissez **Créer un projet d’application web Node.js vide** (JavaScript). Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**. Dans la boîte de dialogue **Nouveau projet**, développez **JavaScript**, puis choisissez **Node.js**. Dans le volet central, choisissez **Application web Node.js vide**, puis **OK**.
    ::: moniker-end
    Si vous ne voyez pas le modèle de projet **Application web Node.js vide**, vous devez ajouter la charge de travail **Développement Node.js**. Pour obtenir des instructions détaillées, consultez les [Prérequis](#prerequisites).

    Visual Studio crée la nouvelle solution et ouvre le projet. *server.js* s’ouvre dans l’éditeur, dans le volet gauche.

## <a name="explore-the-ide"></a>Explorer l’IDE

1. Observez **l’Explorateur de solutions** dans le volet droit.

   ![Explorateur de solutions](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Votre projet mis en gras, avec le nom que vous avez donné dans la boîte de dialogue **Nouveau projet**. Sur le disque, ce projet est représenté par un fichier *.njsproj* dans le dossier de votre projet.

   - Au niveau le plus élevé figure une solution, qui a par défaut le même nom que votre projet. Une solution, représentée par un fichier *.sln* sur le disque, est un conteneur pour un ou plusieurs projets connexes.

   - Le nœud npm montre tous les packages npm installés. Vous pouvez cliquer avec le bouton droit sur le nœud npm pour rechercher et installer des packages npm à l’aide d’une boîte de dialogue.

1. Si vous souhaitez installer des packages npm ou des commandes Node.js à partir d’une invite de commandes, cliquez avec le bouton droit sur le nœud du projet et choisissez **Ouvrir l’invite de commandes ici**.

   ![Invite de commandes node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. Dans le fichier *server.js* dans l’éditeur (volet gauche), choisissez `http.createServer`, puis appuyez sur **F12** ou choisissez **Atteindre la définition** dans le menu contextuel (clic droit). Cette commande affiche la définition de la fonction `createServer` dans *index.d.ts*.

   ![Menu contextuel Atteindre la définition](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Revenez à *server.js*, placez votre curseur à la fin de la chaîne sur la ligne de code suivante, `res.end('Hello World\n');`, puis modifiez-la pour qu’elle ressemble à ceci :

    `res.end('Hello World\n' + res.connection.`

    Quand vous tapez `connection.`, IntelliSense fournit des options de saisie semi-automatique du code.

   ![Saisie semi-automatique IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Choisissez **localPort**, puis tapez `);` pour compléter l’instruction afin qu’elle ressemble à ceci :

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Exécuter l'application

1. Appuyez sur **Ctrl**+**F5** ou (**Déboguer > Démarrer sans débogage**) pour exécuter l’application. L’application s’ouvre dans un navigateur.

1. Dans la fenêtre du navigateur, le message « Hello World » s’affiche, accompagné du numéro de port local.

1. Fermez le navigateur web.

Félicitations, vous avez terminé ce guide de démarrage rapide. Vous en savez maintenant un peu plus sur l’IDE de Visual Studio et Node.js. Si vous souhaitez en savoir plus sur ses fonctionnalités, poursuivez avec l’un des tutoriels de la section **Tutoriels** dans la table des matières.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déployer l’application sur Linux App Service](../javascript/publish-nodejs-app-azure.md)

- [Tutoriel pour Node.js et Express](../javascript/tutorial-nodejs.md)
- [Tutoriel pour Node.js et React](../javascript/tutorial-nodejs-with-react-and-jsx.md)