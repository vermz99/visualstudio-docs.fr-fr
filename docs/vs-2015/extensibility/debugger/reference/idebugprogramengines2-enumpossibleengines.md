---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
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
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 971c4d44cc5b12460b9f715a60537687665b0e1d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504083"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProgramEngines2::EnumPossibleEngines](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines).  
  
Retourne les GUID de tous les moteurs de débogage possible (dé) qui peuvent déboguer ce programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celtBuffer`  
 [in] Le nombre de GUID de dé à retourner. Il spécifie également la taille maximale de la `rgguidEngines` tableau.  
  
 `rgguidEngines`  
 [in, out] Un tableau de GUID DE doit être renseigné.  
  
 `pceltEngines`  
 [out] Retourne le nombre réel de GUID DE qui sont retournées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` ou [c#] 0x8007007A si la mémoire tampon n’est pas assez grande.  
  
## <a name="remarks"></a>Notes  
 Afin de déterminer le nombre de moteurs est, appelez cette méthode une fois avec le `celtBuffer` paramètre défini sur 0 et le `rgguidEngines` paramètre défini sur une valeur null. Cette commande renvoie `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A pour c#) et le `pceltEngines` paramètre retourne la taille de la mémoire tampon nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
