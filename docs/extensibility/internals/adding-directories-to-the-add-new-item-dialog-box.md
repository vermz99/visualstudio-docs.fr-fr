---
title: Ajout de répertoires à la boîte de dialogue Nouvel élément Ajouter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfe4578b4896c137f3bcef8418c5dc0cafd70798
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604208"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Ajouter des répertoires à la boîte de dialogue Ajouter un nouvel élément
L’exemple de code suivant montre comment inscrire un nouvel ensemble de répertoires pour les **ajouter un nouvel élément** boîte de dialogue. Répertoires pour la **ajouter un nouvel élément** boîte de dialogue sont différents pour chaque projet. Par conséquent, les répertoires sont enregistrés sous la **projets** sous-clé, trouvé dans **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

## <a name="registry-script"></a>Script de Registre

```
NoRemove Projects
{
  NoRemove %GUID_Project%
  {
    NoRemove AddItemTemplates
    {
      NoRemove TemplateDirs
      {
        ForceRemove %CLSID_Package%
        {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
          {
            val TemplatesDir = s '%Template_Path%'
            val SortPriority = d 2000
          }
        }
      }
    }
  }
}
```

 Le `%Template_Path%` valeur spécifie le chemin d’accès complet du répertoire qui contient les modèles de projet. Ces modèles peuvent être soit *.vsz* fichiers ou des fichiers de modèle de prototype à cloner.

 Le `SortPriority` valeur spécifie un ordre de priorité.

## <a name="add-items-to-an-existing-project"></a>Ajouter des éléments à un projet existant
 Vous pouvez également ajouter des éléments à un projet existant. Par exemple, pour un [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projet, vous pouvez ajouter des éléments à la  *\<racine > \Program Files\Microsoft Visual Studio\VC #\CSharpProjectItems\LocalProjectItems* dossier. Dans ce cas, `%GUID_Project%` est le GUID pour un projet c# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Vous pouvez également étendre un projet existant par un sous-type de projet de programmation. Avec un sous-type de projet, vous pouvez étendre un projet sans avoir à écrire un nouveau type de projet. Pour plus d’informations sur les sous-types de projet, consultez [les sous-types de projet](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Voir aussi
- [Inscrire les modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Ajouter des répertoires à la boîte de dialogue Nouveau projet](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)