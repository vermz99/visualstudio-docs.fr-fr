---
title: VSPackages et infrastructure de Package gérée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 7f8d5da0d246cb6b0faa8b424f8039697686cd2a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950181"
---
# <a name="vspackages-and-the-managed-package-framework"></a>VSPackages et infrastructure de package gérée
Vous pouvez réduire le temps de développement en créant un VSPackage avec le package géré classes framework (MPF) au lieu d’à l’aide des classes COM interop.  
  
 Il existe deux façons de créer un VSPackage managé :  
  
-   Utilisez le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modèle de projet de Package  
  
     Pour plus d’informations, consultez [Procédure pas à pas : Création d’une commande de Menu à l’aide du modèle de Package Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
-   Créer votre VSPackage sans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modèle de projet de Package  
  
     Par exemple, vous pouvez copier un exemple de VSPackage et modifier les GUID et les noms. Vous trouverez des exemples dans la section VSX de [galerie de Code](http://code.msdn.microsoft.com/vsx/).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Classes MPF (Managed Package Framework)](../misc/managed-package-framework-classes.md)  
 Décrit et répertorie les fichiers DLL et les espaces de noms de classe MPF.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Procédure pas à pas : Création d’une commande de Menu à l’aide du modèle de Package Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Explique comment créer un VSPackage managé.  
  
 [VSPackages gérés](../misc/managed-vspackages.md)  
 Présente les aspects de VSPackages qui s’appliquent au code managé.