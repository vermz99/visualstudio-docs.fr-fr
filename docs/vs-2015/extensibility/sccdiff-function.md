---
title: Fonction SccDiff | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bacfa40d04a897d73213c833e41c199f88981c64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505777"
---
# <a name="sccdiff-function"></a>Fonction SccDiff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [fonction SccDiff](https://docs.microsoft.com/visualstudio/extensibility/sccdiff-function).  
  
Cette fonction affiche (ou éventuellement simplement vérifie) les différences entre le fichier en cours (sur le disque local) et de sa dernière version archivée dans la source de système de contrôle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 lpFileName  
 [in] Nom de fichier pour lequel la différence est demandée.  
  
 Options  
 [in] Indicateurs de commande. Pour plus d’informations, consultez la section Notes.  
  
 pvOptions  
 [in] Options spécifiques au plug-in de contrôle source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|La version de copie et le serveur de travail sont identiques.|  
|SCC_I_FILESDIFFERS|La copie de travail diffère de la version sous contrôle de code source.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
|SCC_E_FILENOTCONTROLLED|Le fichier n’est pas sous contrôle de code source.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NONSPECIFICERROR|Échec non spécifique ; différence de fichier n’a pas été obtenu.|  
|SCC_E_FILENOTEXIST|Le fichier local est introuvable.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction sert deux objectifs différents. Par défaut, il affiche une liste des modifications dans un fichier. Le plug-in de contrôle de code source s’ouvre sa propre fenêtre, dans le format choisit, pour afficher les différences entre le fichier de l’utilisateur sur le disque et la dernière version du fichier sous contrôle de code source.  
  
 Vous pouvez également l’IDE deviez simplement déterminer si un fichier a changé. Par exemple, l’IDE, peut-être déterminer si elle est sécurisée pour extraire un fichier sans en informer l’utilisateur. Dans ce cas, l’IDE passe dans le `SCC_DIFF_CONTENTS` indicateur. Le plug-in de contrôle de code source doit vérifier le fichier sur disque, octet par octet, par rapport au fichier de contrôle de code source et retournent une valeur indiquant si les deux fichiers sont différents sans rien afficher à l’utilisateur.  
  
 Optimiser les performances, le plug-in de contrôle de code source peut utiliser une alternative basée sur une somme de contrôle ou un horodatage au lieu de la comparaison octet par octet appelé pour `SCC_DIFF_CONTENTS`: ces formes de comparaison sont évidemment plus rapide mais moins fiable. Pas tous les systèmes de contrôle de source peuvent prendre en charge ces méthodes de comparaison autre, et le plug-in peut avoir à revenir à une comparaison de contenu. Tous les plug-ins de contrôle de code source doit, au minimum, prendre en charge une comparaison de contenu.  
  
> [!NOTE]
>  Les indicateurs de différence rapide s’excluent mutuellement. Il est valide de ne passer aucun indicateur, mais il n’est pas valide pour simultanément passer plusieurs. `SCC_DIFF_QUICK_DIFF`, qui est un masque qui combine tous les indicateurs, peut être utilisé pour tester, mais elle ne doit jamais être passée en tant que paramètre.  
  
|`fOption`|Signification|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|Comparaison respectant la casse (peut être utilisé pour différence rapide ou visuel).|  
|SCC_DIFF_IGNORESPACE|Ignore les espaces blancs (peut être utilisé pour différence rapide ou visuel).|  
|SCC_DIFF_QD_CONTENTS|En mode silencieux compare le fichier, octet par octet.|  
|SCC_DIFF_QD_CHECKSUM|En mode silencieux compare le fichier via une somme de contrôle pris en charge. Si non pris en charge, revient à une comparaison de contenu.|  
|SCC_DIFF_QD_TIME|En mode silencieux compare le fichier par le biais de son horodatage lors de la prise en charge. Si non pris en charge, revient à une comparaison de contenu.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
