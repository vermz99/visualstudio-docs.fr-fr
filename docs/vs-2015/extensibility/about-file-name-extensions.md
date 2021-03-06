---
title: À propos des Extensions de nom de fichier | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947223"
---
# <a name="about-file-name-extensions"></a>À propos des extensions de nom de fichier
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous inscrivez une extension de fichier d’un VSPackage, associez-la à une version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Cela est important si, et plusieurs versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est installé sur un ordinateur.  
  
 Extensions de fichier pour les VSPackages sont enregistrées sous la clé HKEY_CLASSES_ROOT avec une valeur par défaut qui pointe vers l’associée identificateur programmatique (ProgID).  
  
 Voici un exemple des informations d’inscription pour l’extension de fichier .vcproj :  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Fichiers associés [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doit avoir un ProgID avec contrôle de version, tel que `VisualStudio.vcproj.8.0`, pour permettre des installations côte à côte du produit pour gérer les associations d’extension de fichier entre les versions de produit. Un ProgID spécifique à la version vous permet également d’utiliser des verbes standards, telles qu’Ouvrir, modifier et ainsi de suite, sans vous préoccuper de remplacer ni être remplacé par d’autres applications ou les versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Dans certains cas, le ProgID associé à une extension de fichier ne doit pas être modifié. Par exemple, le ProgID pour l’extension de fichier .htm (progid = htmlfile) est codé dans plusieurs emplacements dans le système d’exploitation en dur, et est largement connue et utilisée en association avec des fichiers .htm et .html.  
  
## <a name="see-also"></a>Voir aussi  
 [L’inscription des Extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Spécification des gestionnaires de fichiers pour les extensions de nom de fichier](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
