---
title: 'Procédure : Utiliser des Assistants avec des modèles de projet'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4ff83c2d4d28b6393f7f6d03b01e35d9cc0aa4f
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324639"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Procédure : Utiliser des Assistants avec des modèles de projet

Visual Studio fournit le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface qui, en cas d’implémentation, afin de pouvoir exécuter du code personnalisé lorsqu’un utilisateur crée un projet à partir d’un modèle.

Personnalisation du modèle de projet peut être utilisée pour afficher l’interface utilisateur personnalisée qui collecte les entrées d’utilisateur pour personnaliser le modèle, ajouter des fichiers supplémentaires au modèle, ou toute autre action autorisée sur un projet.

Le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> méthodes d’interface sont appelées à différents moments pendant que le projet est créé, dès qu’un utilisateur clique sur **OK** sur le **nouveau projet** boîte de dialogue. Chaque méthode de l’interface est nommée pour décrire le point auquel elle est appelée. Par exemple, Visual Studio appelle <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> immédiatement lorsqu’il commence à créer le projet, rendant ainsi un bon emplacement pour écrire du code personnalisé pour recueillir les entrées utilisateur.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Créer un projet de modèle de projet avec un projet VSIX

Vous commencez à créer un modèle personnalisé avec le projet de modèle de projet, qui fait partie du SDK Visual Studio. Dans cette procédure, nous allons utiliser un C# projet de modèle de projet, mais il existe également un projet de modèle de projet Visual Basic. Ensuite, vous ajoutez un projet VSIX à la solution qui contient le projet de modèle de projet.

1. Créer un C# projet de modèle de projet (dans Visual Studio, sélectionnez **fichier** > **New** > **projet** et recherchez « modèle de projet » ). Nommez-le **MyProjectTemplate**.

   > [!NOTE]
   > Vous pouvez être invité à installer le SDK Visual Studio. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Ajouter un nouveau projet VSIX dans la même solution que le projet de modèle de projet (dans **l’Explorateur de solutions**, sélectionnez le nœud de la solution, avec le bouton droit, puis sélectionnez **ajouter** > **nouveau projet**  et recherchez « vsix »). Nommez-le **MyProjectWizard.**

3. Définissez le projet VSIX comme projet de démarrage. Dans **l’Explorateur de solutions**, sélectionnez le nœud du projet VSIX, avec le bouton droit, puis sélectionnez **définir comme projet de démarrage**.

4. Ajouter le modèle de projet en tant qu’actif du projet VSIX. Dans **l’Explorateur de solutions**, sous le nœud du projet VSIX, recherchez le *source.extension.vsixmanifest* fichier. Double-cliquez dessus pour l’ouvrir dans l’éditeur de manifeste.

5. Dans l’éditeur de manifeste, sélectionnez le **actifs** onglet sur le côté gauche de la fenêtre.

6. Dans le **actifs** onglet, sélectionnez **New**. Dans le **ajouter un nouveau composant** fenêtre, pour le champ de Type, sélectionnez **Microsoft.VisualStudio.ProjectTemplate**. Dans le **Source** champ, sélectionnez **un projet dans la solution actuelle**. Dans le **projet** champ, sélectionnez **MyProjectTemplate**. Cliquez ensuite sur **OK**.

7. Générez la solution et commencez le débogage. Une seconde instance de Visual Studio apparaît. (Cela peut prendre quelques minutes.)

8. Dans la deuxième instance de Visual Studio, essayez de créer un nouveau projet avec votre nouveau modèle (**fichier** > **New** > **projet**, recherchez » MonProjet »). Le nouveau projet doit s’afficher avec une classe nommée **Class1**. Vous venez de créer un modèle de projet personnalisé ! Arrêter le débogage maintenant.

## <a name="create-a-custom-template-wizard"></a>Assistant Création d’un modèle personnalisé

Cette procédure montre comment créer un Assistant personnalisé qui ouvre un formulaire Windows avant que le projet est créé. Le formulaire permet aux utilisateurs d’ajouter une valeur de paramètre personnalisé qui est ajoutée au code source lors de la création du projet.

1. Configurer le projet VSIX pour lui permettre de créer un assembly.

2. Dans **l’Explorateur de solutions**, sélectionnez le nœud du projet VSIX. Ci-dessous **l’Explorateur de solutions**, vous devez voir le **propriétés** fenêtre. Si vous ne le faites pas, sélectionnez **vue** > **fenêtre Propriétés**, ou appuyez sur **F4**. Dans le **propriétés** fenêtre, sélectionnez les champs suivants à `true`:

   - **IncludeAssemblyInVSIXContainer**

   - **IncludeDebugSymbolsInVSIXContainer**

   - **IncludeDebugSymbolsInLocalVSIXDeployment**

3. Ajoutez l’assembly en tant que ressource au projet VSIX. Ouvrez le *source.extension.vsixmanifest* fichier et sélectionnez le **actifs** onglet. Dans le **ajouter un nouveau composant** fenêtre, pour **Type** sélectionnez **Microsoft.VisualStudio.Assembly**, pour **Source** sélectionnez **A projet dans la solution actuelle**et pour **projet** sélectionnez **MyProjectWizard**.

4. Ajoutez les références suivantes au projet VSIX. (Dans **l’Explorateur de solutions**, sous le nœud du projet VSIX, sélectionnez **références**, avec le bouton droit, puis sélectionnez **ajouter une référence**.) Dans le **ajouter une référence** boîte de dialogue, dans le **Framework** onglet, recherchez la **System.Windows Forms** assembly et sélectionnez-le. Sélectionnez maintenant le **Extensions** onglet. Rechercher la **EnvDTE** assembly et sélectionnez-le. Recherchez également le **Microsoft.VisualStudio.TemplateWizardInterface** assembly et sélectionnez-le. Cliquez sur **OK**.

5. Ajoutez une classe pour l’implémentation de l’Assistant pour le projet VSIX. (Dans **l’Explorateur de solutions**, cliquez sur le nœud du projet VSIX et sélectionnez **ajouter**, puis **un nouvel élément**, puis **classe**.) Nommez la classe **WizardImplementation**.

6. Remplacez le code dans le *WizardImplementationClass.cs* fichier par le code suivant :

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    Le **UserInputForm** référencé dans ce code est implémenté ultérieurement.

    Le `WizardImplementation` classe contient des implémentations de méthode pour chaque membre de <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. Dans cet exemple, seul le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> méthode effectue une tâche. Toutes les autres méthodes ne fait rien ou retournent `true`.

    Le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> méthode accepte quatre paramètres :

   - Un <xref:System.Object> paramètre pouvant être casté vers la racine <xref:EnvDTE._DTE> objet, pour vous permettre de personnaliser le projet.

   - Un <xref:System.Collections.Generic.Dictionary%602> paramètre qui contient une collection de tous les paramètres prédéfinis dans le modèle. Pour plus d’informations sur les paramètres de modèle, consultez [paramètres de modèle](../ide/template-parameters.md).

   - Un <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> paramètre qui contient des informations sur le type de modèle est utilisé.

   - Un <xref:System.Object> tableau qui contient un ensemble de paramètres passé à l’Assistant par Visual Studio.

     Cet exemple ajoute une valeur de paramètre à partir du formulaire d’entrée utilisateur pour le <xref:System.Collections.Generic.Dictionary%602> paramètre. Chaque instance de la `$custommessage$` paramètre dans le projet sera remplacé par le texte entré par l’utilisateur. Ajoutez les assemblys suivants à votre projet : **Système** et **System.Drawing**.

7. À présent créer le **UserInputForm**. Dans le *WizardImplementation.cs* , ajoutez le code suivant après la fin de la `WizardImplementation` classe.

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    Le formulaire d’entrée utilisateur fournit un formulaire simple pour entrer un paramètre personnalisé. Le formulaire contient une zone de texte nommée `textBox1` et un bouton nommé `button1`. Lorsque le bouton est activé, le texte à partir de la zone de texte est stocké dans le `customMessage` paramètre.

## <a name="connect-the-wizard-to-the-custom-template"></a>Connecter l’Assistant pour le modèle personnalisé

Afin que votre modèle de projet personnalisés à utiliser votre Assistant personnalisé, vous devez signer l’assembly de l’Assistant et ajoutez quelques lignes à votre modèle de projet personnalisé, il faut où trouver l’implémentation de l’Assistant Création d’un nouveau projet.

1. Signer l’assembly. Dans le **l’Explorateur de solutions**, sélectionnez le projet VSIX, avec le bouton droit, puis sélectionnez **propriétés du projet**.

2. Dans le **propriétés du projet** fenêtre, sélectionnez le **signature** onglet dans le **signature** onglet, vérification **signer l’assembly**. Dans le **choisir un fichier de clé de nom fort** champ, sélectionnez  **\<New >**. Dans le **créer une clé de nom fort** fenêtre, dans le **nom de fichier de clé** , tapez **key.snk**. Désactivez le **protéger mon fichier de clé avec un mot de passe** champ.

3. Dans le **l’Explorateur de solutions**, sélectionnez le projet VSIX et recherchez le **propriétés** fenêtre.

4. Définir le **répertoire de sortie vers la sortie de génération copie** champ **true**. Ainsi, l’assembly doit être copié dans le répertoire de sortie lors de la reconstruction de la solution. Il est toujours contenu dans le `.vsix` fichier. Vous devez voir l’assembly pour connaître sa clé de signature.

5. Régénérez la solution.

6. Vous pouvez maintenant rechercher le fichier key.snk dans le répertoire du projet MyProjectWizard (*\<votre emplacement de disque > \MyProjectTemplate\MyProjectWizard\key.snk*). Copie le *key.snk* fichier.

7. Accédez au répertoire de sortie et de trouver l’assembly (*\<votre emplacement de disque > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Coller le *key.snk* fichier ici. (Cela n’est pas absolument nécessaire, mais cela facilite les étapes suivantes).

8. Ouvrez une fenêtre de commande et accédez au répertoire dans lequel l’assembly a été créée.

9. Rechercher la *sn.exe* outil de signature. Par exemple, sur un système d’exploitation de 64 bits de Windows 10, un chemin d’accès classique serait le suivant :

     *C:\Program fichiers (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     Si vous ne trouvez pas l’outil, essayez d’exécuter **où /R. sn.exe** dans la fenêtre de commande. Prenez note du chemin d’accès.

10. Extrayez la clé publique à partir de la *key.snk* fichier. Dans la fenêtre de commande, tapez

     **\<emplacement de sn.exe > \sn.exe -p key.snk outfile.key.**

     N’oubliez pas d’entourer le chemin d’accès *sn.exe* avec des guillemets s’il existe des espaces dans les noms de répertoire !

11. Obtenir la clé publique jeton dans le fichier de sortie :

     **\<emplacement de sn.exe > \sn.exe -t outfile.key.**

     Là encore, n’oubliez pas les guillemets. Vous devez voir une ligne dans la sortie semblable à celle-ci

     **Jeton de clé publique est \<jeton >**

     Prenez note de cette valeur.

12. Ajoutez la référence à l’Assistant personnalisé pour le *.vstemplate* fichier du modèle de projet. Dans le **l’Explorateur de solutions**, recherchez le fichier nommé *MyProjectTemplate.vstemplate*et l’ouvrir. Après la fin de la \<TemplateContent >, ajoutez la section suivante :

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Où **MyProjectWizard** est le nom de l’assembly, et **jeton** est le jeton que vous avez copiée à l’étape précédente.

13. Enregistrez tous les fichiers dans le projet et régénérez.

## <a name="add-the-custom-parameter-to-the-template"></a>Ajouter le paramètre personnalisé pour le modèle

Dans cet exemple, le projet utilisé comme modèle affiche le message spécifié sous la forme d’entrée d’utilisateur de l’Assistant personnalisé.

1. Dans le **l’Explorateur de solutions**, accédez à la **MyProjectTemplate** de projet et ouvrez *Class1.cs*.

2. Dans le `Main` (méthode) de l’application, ajoutez la ligne suivante de code.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Le paramètre `$custommessage$` est remplacé par le texte entré dans le formulaire d’entrée utilisateur lorsqu’un projet est créé à partir du modèle.

Voici le fichier de code complet avant qu’il a été exporté vers un modèle.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Utilisez l’Assistant personnalisé

Vous pouvez maintenant créer un projet à partir de votre modèle et utiliser l’Assistant personnalisé.

1. Régénérez la solution et démarrez le débogage. Une seconde instance de Visual Studio doit apparaître.

2. Créer un nouveau projet MyProjectTemplate. (**Fichier** > **nouveau** > **projet**).

3. Dans le **nouveau projet** boîte de dialogue, recherchez « MonProjet » rechercher votre modèle, tapez un nom, puis cliquez sur **OK**.

     Le formulaire d’entrée de l’utilisateur d’Assistant s’ouvre.

4. Tapez une valeur pour le paramètre personnalisé, puis cliquez sur le bouton.

     Le formulaire d’entrée de l’utilisateur d’Assistant se ferme et un projet est créé à partir du modèle.

5. Dans **l’Explorateur de solutions**, cliquez sur le fichier de code source, puis cliquez sur **afficher le Code**.

     Notez que `$custommessage$` a été remplacé par le texte entré dans le formulaire d’entrée de l’utilisateur d’Assistant.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Personnaliser les modèles](../ide/customizing-project-and-item-templates.md)
- [WizardExtension, élément (modèles Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)