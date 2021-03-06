---
title: Création d’un contrôle de boîte à outils WPF | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 811c87f73d1122b3e97ffdef9b4d3f6c044ce941
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194825"
---
# <a name="create-a-wpf-toolbox-control"></a>Créer un contrôle de boîte à outils WPF

Le modèle de contrôle de boîte à outils WPF (Windows Presentation Framework) vous permet de créer des contrôles WPF qui sont automatiquement ajoutés à la **boîte à outils** lorsque l’extension est installée. Cette procédure pas à pas montre comment utiliser le modèle pour créer un **boîte à outils** contrôle que vous pouvez distribuer à d’autres utilisateurs.

À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Créer le contrôle de boîte à outils

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Créer une extension avec un contrôle de boîte à outils WPF

1. Créez un projet VSIX nommé `MyToolboxControl`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue en recherchant « vsix ».

2. Quand le projet s’ouvre, ajoutez un **contrôle de boîte à outils WPF** modèle d’élément nommé `MyToolboxControl`. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **ajouter** > **un nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C#** > **extensibilité** et sélectionnez **contrôle de boîte à outils WPF**. Dans le **nom** en bas de la fenêtre, modifiez le nom de fichier de commande pour *MyToolboxControl.cs*.

    La solution contient maintenant un contrôle utilisateur, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> qui ajoute le contrôle à la **boîte à outils**et un **Microsoft.VisualStudio.ToolboxControl** dans le manifeste VSIX pour l’entrée de composant  déploiement.

#### <a name="to-create-the-control-ui"></a>Pour créer le contrôle de l’interface utilisateur

1. Ouvrez *MyToolboxControl.xaml* dans le concepteur.

    Le concepteur affiche un contrôle <xref:System.Windows.Controls.Grid> contenant un contrôle <xref:System.Windows.Controls.Button>.

2. Organiser la disposition de grille. Lorsque vous sélectionnez le <xref:System.Windows.Controls.Grid> contrôler, les barres de contrôle bleues apparaissent sur les bords supérieur et gauche de la grille. Vous pouvez ajouter des lignes et des colonnes à la grille en cliquant sur les barres.

3. Ajouter des contrôles enfants à la grille. Vous pouvez positionner un contrôle enfant en le faisant glisser à partir de la **boîte à outils** à une section de la grille, ou en définissant son `Grid.Row` et `Grid.Column` attributs dans le XAML. L’exemple suivant ajoute deux étiquettes sur la ligne du haut de la grille et un bouton sur la deuxième ligne.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Renommer le contrôle

 Par défaut, votre contrôle apparaît dans le **boîte à outils** comme **MyToolboxControl** dans un groupe nommé **MyToolboxControl.MyToolboxControl**. Vous pouvez modifier ces noms dans le *MyToolboxControl.xaml.cs* fichier.

1. Ouvrez *MyToolboxControl.xaml.cs* en mode code.

2. Rechercher la `MyToolboxControl` classe et renommez-le TestControl. (Le plus rapide pour ce faire consiste à renommer la classe, puis sélectionnez **renommer** dans le menu contextuel et effectuez les étapes. (Pour plus d’informations sur la **renommer** de commande, consultez [renommer refactorisation (c#)](../ide/reference/rename.md).)

3. Accédez à la `ProvideToolboxControl` d’attribut et modifiez la valeur du premier paramètre à **Test**. Il s’agit du nom du groupe qui contiendra le contrôle dans le **boîte à outils**.

    Le code résultant doit ressembler à ceci :

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>Génération, de test et de déploiement

 Lorsque vous déboguez le projet, vous devez rechercher le contrôle est installé dans le **boîte à outils** de l’instance expérimentale de Visual Studio.

### <a name="to-build-and-test-the-control"></a>Pour générer et tester le contrôle

1. Régénérez le projet et démarrer le débogage.

2. Dans la nouvelle instance de Visual Studio, créez un projet d’application WPF. Assurez-vous que le concepteur XAML est ouvert.

3. Recherchez votre contrôle dans la **boîte à outils** et faites-la glisser vers l’aire de conception.

4. Démarrez le débogage de l’application WPF.

5. Vérifiez que votre contrôle s’affiche.

### <a name="to-deploy-the-control"></a>Pour déployer le contenu

1. Une fois que vous générez le projet testé, vous pouvez trouver la *.vsix* de fichiers dans le * \bin\debug\* dossier du projet.

2. Vous pouvez l’installer sur un ordinateur local en double-cliquant sur le *.vsix* fichier et en suivant la procédure d’installation. Pour désinstaller le contrôle, accédez à **outils** > **Extensions et mises à jour** et recherchez l’extension de contrôle, puis cliquez sur **désinstallation**.

3. Télécharger le *.vsix* fichier à un réseau ou à un site Web.

    Si vous chargez le fichier à la [Visual Studio Marketplace](https://marketplace.visualstudio.com/) site Web, les autres utilisateurs peuvent utiliser **outils** > **Extensions et mises à jour** dans Visual Studio pour rechercher le contrôler en ligne et l’installer.
