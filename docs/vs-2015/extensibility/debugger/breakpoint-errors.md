---
title: Erreurs de point d’arrêt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c9400e28e54476b027e6d57e97d7d0178511a10a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938583"
---
# <a name="breakpoint-errors"></a>Erreurs de point d’arrêt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ce qui suit décrit le processus lorsqu’un point d’arrêt tente de se lier au code, mais échoue :  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Résolution d’une erreur de point d’arrêt  
  
1.  Le moteur de débogage (dé) envoie une [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) pour le Gestionnaire de session de débogage (SDM).  
  
2.  Les appels SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) pour obtenir le point d’arrêt de l’erreur.  
  
3.  Les appels SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) pour obtenir le point d’arrêt en attente dont provenance le point d’arrêt de l’erreur.  
  
4.  Les appels SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) pour obtenir la raison de l’échec le point d’arrêt de l’erreur à lier.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)
