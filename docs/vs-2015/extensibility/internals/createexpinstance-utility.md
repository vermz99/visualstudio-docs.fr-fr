---
title: Utilitaire CreateExpInstance | Microsoft Docs
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
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9b08ba5ac68a09f6c44937634375add3065e5e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501313"
---
# <a name="createexpinstance-utility"></a>Utilitaire CreateExpInstance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CreateExpInstance Utility](https://docs.microsoft.com/visualstudio/extensibility/internals/createexpinstance-utility).  
  
Utiliser l’utilitaire CreateExpInstance pour créer, réinitialiser, ou supprimer une instance expérimentale de Visual Studio. Vous pouvez utiliser l’instance expérimentale pour déboguer et tester des extensions Visual Studio sans modifier le produit sous-jacent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Paramètres  
 / Création  
 Crée l’instance expérimentale.  
  
 / Réinitialisation  
 Supprime l’instance expérimentale et crée un nouveau.  
  
 /Clean  
 Supprime l’instance expérimentale.  
  
 / VSInstance  
 Le nom du répertoire qui contient l’instance de Visual Studio de base à copier.  
  
 / RootSuffix  
 Le suffixe à ajouter au nom du répertoire d’instance expérimentale.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous travaillez sur une extension Visual Studio, vous pouvez appuyer sur F5 pour ouvrir l’instance expérimentale par défaut et installer l’extension actuelle. Si aucune instance expérimentale n’est disponible, Visual Studio crée un objet qui contient les paramètres par défaut.  
  
 L’emplacement par défaut de l’instance expérimentale varie selon le numéro de version de Visual Studio. Par exemple, pour Visual Studio 2015, l’emplacement est %localappdata%\Microsoft\VisualStudio\14.0Exp\ tous les fichiers dans l’emplacement du répertoire sont considérées comme partie de cette instance. Toutes les instances expérimentales supplémentaires ne seront pas chargés par Visual Studio, sauf si le nom du répertoire est modifié à l’emplacement par défaut.  
  
 Visual Studio n’accède pas au Registre système lorsqu’il ouvre l’instance expérimentale. Cela diffère des versions antérieures de Visual Studio, qui ont utilisé une version expérimentale de la ruche du Registre.  
  
 L’utilitaire CreateExpInstance remplace l’utilitaire VsRegEx.  
  
 L’exemple suivant réinitialise l’instance expérimentale de la valeur par défaut de Visual Studio.  
  
 **CreateExpInstance.exe /Reset /VSInstance = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’un produit](../../misc/releasing-a-visual-studio-integration-product.md)
