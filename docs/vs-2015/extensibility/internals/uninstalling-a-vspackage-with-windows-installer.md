---
title: Désinstallation d’un VSPackage avec Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 695b25ddb676f78a439d704e07344326e70b1fff
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949061"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Désinstallation d’un VSPackage avec Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La plupart du temps, le programme d’installation de Windows peut désinstaller votre VSPackage simplement en « annulation » qu’elle a effectué pour installer votre VSPackage. Les actions personnalisées abordés dans [commandes que doit être exécuté après l’Installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md) doit être exécuté après une désinstallation également. Étant donné que les appels à devenv.exe soient effectuées juste avant l’action standard de InstallFinalize pour l’installation et la désinstallation, les entrées de table CustomAction et InstallExecuteSequence servent les deux cas.  
  
> [!NOTE]
>  Exécutez `devenv /setup` après la désinstallation d’un package MSI.  
  
 En règle générale, si vous ajoutez des actions personnalisées à un package de programme d’installation de Windows, vous devez gérer ces actions pendant la restauration et de la désinstallation. Par exemple, si vous ajoutez des actions personnalisées pour s’inscrire automatiquement à votre VSPackage, vous devez ajouter des actions personnalisées pour annuler son inscription, trop.  
  
> [!NOTE]
>  Il est possible pour un utilisateur à installer votre package Visual Studio, puis désinstaller les versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] avec lequel il est intégré. Vous pouvez vous assurer que la désinstallation de votre VSPackage fonctionne dans ce scénario en éliminant les actions personnalisées qui s’exécutent du code avec des dépendances sur [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Gestion des Conditions de lancement au moment de la désinstallation  
 L’action standard LaunchConditions lit les lignes de la table LaunchCondition pour afficher l’erreur messages si les conditions ne sont pas remplies. Comme les conditions de lancement sont généralement utilisées pour vous assurer que la configuration système requise est remplies, vous pouvez généralement ignorer des conditions de lancement lors de la désinstallation en ajoutant la condition, `NOT Installed`, à la ligne LaunchConditions de la table LaunchCondition.  
  
 Une alternative consiste à ajouter `OR Installed` pour lancer des conditions qui ne sont pas importantes lors de la désinstallation. Cela garantit que la condition est toujours true lors de la désinstallation et par conséquent, n’affiche pas le message d’erreur de lancement condition.  
  
> [!NOTE]
>  `Installed` est la propriété de que programme d’installation de Windows définit lorsqu’elle détecte que votre VSPackage a déjà été installé sur le système.  
  
## <a name="see-also"></a>Voir aussi  
 [Programme d’installation de Windows](http://msdn.microsoft.com/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Détection de la configuration système requise](../../extensibility/internals/detecting-system-requirements.md)
