---
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84c36d08c7ad907006eb9f41d2f6e2c9cd77e7bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938353"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un point d’arrêt en attente dans le moteur de débogage (dé).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pBPRequest`  
 [in] Un [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) objet qui décrit le point d’arrêt en attente à créer.  
  
 `ppPendingBP`  
 [out] Retourne un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objet qui représente le point d’arrêt en attente.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne généralement `E_FAIL` si le `pBPRequest` paramètre ne correspond pas à n’importe quel langage pris en charge par le DE if le `pBPRequest` paramètre est non valide ou incomplète.  
  
## <a name="remarks"></a>Notes  
 Un point d’arrêt en attente est essentiellement une collection de toutes les informations nécessaires pour lier un point d’arrêt au code. Le point d’arrêt en attente retourné par cette méthode n’est pas lié au code jusqu'à ce que le [lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) méthode est appelée.  
  
 Pour chaque point d’arrêt en attente de l’utilisateur définit le Gestionnaire de session de débogage (SDM) appelle cette méthode dans chaque attaché DE. C’est à la DE pour vérifier que le point d’arrêt est valide pour les programmes en cours d’exécution dans cette DE.  
  
 Lorsque l’utilisateur définit un point d’arrêt sur une ligne de code, l’Allemagne est gratuite lier le point d’arrêt à la ligne la plus proche dans le document qui correspond à ce code. Cela rend possible pour l’utilisateur définir un point d’arrêt sur la première ligne d’une instruction multiligne, mais liez-le sur la dernière ligne (où tout le code est attribué dans les informations de débogage).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour une simple `CProgram` objet. Implémentation de l’Allemagne de le `IDebugEngine2::CreatePendingBreakpoint` puis de transférer tous les appels à cette implémentation de la méthode dans chaque programme.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
