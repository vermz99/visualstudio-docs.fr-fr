---
title: Élément LocalizedDescription (schéma du module linguistique VSIX) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 766a1732-bbaf-4875-b276-feb42169633a
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e509573518ebf779cb15bc2859bacc61c336f7f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505856"
---
# <a name="localizeddescription-element-vsix-language-pack-schema"></a>Élément LocalizedDescription (schéma du module linguistique VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [LocalizedDescription élément (schéma du module linguistique VSIX)](https://docs.microsoft.com/visualstudio/extensibility/localizeddescription-element-vsix-language-pack-schema).  
  
Obligatoire. Fournit une description localisée de l’extension.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<LocalizedDescription>Localized description of the extension</LocalizedDescription>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|Aucun.||  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun.||  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obligatoire. Fournit l’élément racine pour un module linguistique VSIX.|  
  
## <a name="text-value"></a>Valeur texte  
 Obligatoire. Description textuelle de l’extension dans le langage cible.  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|Espace de noms|http://schemas.microsoft.com/developer/vsx-schema-lp/2010|  
|Nom du schéma|Schéma du module linguistique VSIX|  
|Fichier de validation|VSIXLanguagePackSchema.xsd|  
|Peut être vide|Non applicable|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma du module linguistique VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localisation de Packages VSIX](../extensibility/localizing-vsix-packages.md)   
 [Référence du schéma 1.0 Extension VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
