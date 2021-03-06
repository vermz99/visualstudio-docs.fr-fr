---
title: Ouvrir une solution, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 298609aa37557eebc52dce7ca6eada2f98f2096d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54759984"
---
# <a name="open-solution-command"></a>Ouvrir une solution, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Ouvre une solution existante, en fermant toutes les autres solutions ouvertes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
File.OpenSolution filename  
```  
  
## <a name="arguments"></a>Arguments  
 `Filename`  
 Obligatoire. Chemin complet et nom de fichier de la solution à ouvrir.  
  
 La syntaxe de l’argument `filename` nécessite que les chemins contenant des espaces utilisent des guillemets.  
  
## <a name="remarks"></a>Remarques  
 La saisie semi-automatique tente de deviner le chemin et le nom de fichier à mesure que vous tapez.  
  
## <a name="example"></a>Exemple  
 Cet exemple ouvre la solution Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
