---
title: Paramètres personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 21d85eb55e20eb27a67856cec1fea7f6fa539b41
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504448"
---
# <a name="custom-parameters"></a>Paramètres personnalisés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [personnalisé paramètres](https://docs.microsoft.com/visualstudio/extensibility/internals/custom-parameters).  
  
Paramètres personnalisés contrôlent le fonctionnement d’un Assistant après le démarrage d’un Assistant. Un fichier .vsz connexes fournit un tableau de paramètres définis par l’utilisateur qui sont empaquetées par l’environnement de développement intégré (IDE) et passé à l’Assistant sous forme de tableau de chaînes au démarrage de l’Assistant. Ensuite, l’Assistant analyse le tableau de chaînes et utilise les informations pour contrôler le fonctionnement réel de l’Assistant. De cette manière, un Assistant peut personnaliser les fonctionnalités en fonction du contenu du fichier .vsz.  
  
 Paramètres de contexte, quant à eux, définissent l’état du projet que lorsque l’Assistant est démarré. Pour plus d’informations, consultez [paramètres de contexte](../../extensibility/internals/context-parameters.md).  
  
 Voici un exemple d’un fichier .vsz comportant des paramètres personnalisés :  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 L’auteur du fichier .vsz ajoute les valeurs des paramètres. Lorsqu’un utilisateur sélectionne **nouveau projet** ou **ajouter un nouvel élément** dans le menu fichier ou en double-cliquant sur un projet dans **l’Explorateur de solutions**, l’IDE collecte ces valeurs dans un tableau de chaînes. L’IDE puis appelle le projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> méthode avec le <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> indicateur ensemble et les appels de projet la <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> méthode qui est responsable de l’exécution de l’Assistant et en retournant le résultat.  
  
 L’Assistant est responsable de l’analyse du tableau de chaînes et agir sur les chaînes en conséquence. De cette manière, en implémentant des paramètres personnalisés, vous pouvez créer un Assistant qui effectue un éventail de fonctions. En d’autres termes, un Assistant peut avoir trois fichiers .vsz différents. Chaque fichier transmet différents jeux de paramètres personnalisés pour contrôler le comportement de l’Assistant dans diverses situations.  
  
 Pour plus d’informations, consultez [Assistant (. Fichier vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Paramètres de contexte](../../extensibility/internals/context-parameters.md)   
 [Assistants](../../extensibility/internals/wizards.md)   
 [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
