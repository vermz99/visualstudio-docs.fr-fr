---
title: Modification de l’apparence d’une commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b028250c53ccf0d5af09671bca82848a626d3129
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953901"
---
# <a name="changing-the-appearance-of-a-command"></a>Modification de l’apparence d’une commande
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez fournir des commentaires à votre utilisateur en modifiant l’apparence d’une commande. Par exemple, vous souhaiterez une commande à un aspect différent quand il n’est pas disponible. Vous pouvez activer ou désactiver les commandes, masquer ou afficher, ou vérifier ou décochez la case dans le menu.  
  
 Pour modifier l’apparence d’une commande, effectuez l’une des actions suivantes :  
  
- Spécifier les indicateurs appropriés dans la définition de commande dans le fichier de table de commande.  
  
- Utilisez le <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> service.  
  
- Implémentez le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> d’interface et de modifier les objets de commande brutes.  
  
  Les étapes suivantes montrent comment rechercher et mettre à jour l’apparence d’une commande à l’aide de Managed Package Framework (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Pour modifier l’apparence d’une commande de menu  
  
1.  Suivez les instructions de [modification du texte d’une commande de Menu](../extensibility/changing-the-text-of-a-menu-command.md) pour créer un élément de menu nommé `New Text`.  
  
2.  Dans le fichier ChangeMenuText.cs, ajoutez le code suivant à l’aide d’instruction :  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  Dans le fichier ChangeMenuTextPackageGuids.cs, ajoutez la ligne suivante :  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  Dans le fichier ChangeMenuText.cs, remplacez le code dans la méthode ShowMessageBox avec les éléments suivants :  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Obtenir la commande que vous souhaitez mettre à jour à partir de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> de l’objet et ensuite définir les propriétés appropriées sur l’objet command. Par exemple, la méthode suivante fait la commande spécifiée à partir d’une commande VSPackage définir disponibles ou non disponible. Le code suivant fait l’élément de menu nommé `New Text` indisponible après qu’il a été cliqué.  
  
    ```csharp  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6.  Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio doit apparaître.  
  
7.  Sur le **outils** menu, cliquez sur le **ChangeMenuText appeler** commande. À ce stade le nom de la commande est **ChangeMenuText appeler**, de sorte que le Gestionnaire de commandes n’appelle pas ChangeMyCommand().  
  
8.  Sur le **outils** menu vous devriez maintenant voir **nouveau texte**. Cliquez sur **nouveau texte**. La commande doit maintenant être apparaît en grisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Comment VSPackages ajoute des éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
