---
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8ad9e4b6d83ebc05c78a8b84c0c06e00d7563bc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953474"
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie les informations à récupérer sur une demande de point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>Membres  
 BPREQI_BPLOCATION  
 Initialize/utiliser le `bpLocation` champ (emplacement de point d’arrêt) de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structure.  
  
 BPREQI_LANGUAGE  
 Initialize/utiliser le `guidLanguage` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_PROGRAM  
 Initialize/utiliser le `pProgram` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_PROGRAMNAME  
 Initialize/utiliser le `bstrProgramName` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_THREAD  
 Initialize/utiliser le `pThread` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_THREADNAME  
 Initialize/utiliser le `bstrThreadName` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_PASSCOUNT  
 Initialize/utiliser le `bpPassCount` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_CONDITION  
 Initialize/utiliser le `bpCondition` champ (condition de point d’arrêt) de la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_FLAGS  
 Initialize/utiliser le `dwFlags` champ la `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` structure.  
  
 BPREQI_ALLOLDFIELDS  
 Initialize/utiliser tous les champs pour la de la `BP_REQUEST_INFO` structure.  
  
 BPREQI_VENDOR  
 Initialize/utiliser le `guidVendor` champ `BP_REQUEST_INFO2` structure.  
  
 BPREQI_CONSTRAINT  
 Initialize/utiliser le `bstrConstraint` champ `BP_REQUEST_INFO2` structure.  
  
 BPREQI_TRACEPOINT  
 Initialize/utiliser le `bstrTracepoint` champ `BP_REQUEST_INFO2` structure.  
  
 BPREQI_ALLFIELDS  
 Spécifie tous les champs pour le `BP_REQUEST_INFO2` structure.  
  
## <a name="remarks"></a>Notes  
 Passé en tant qu’argument à la [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) et [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) méthodes pour spécifier les champs de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2 ](../../../extensibility/debugger/reference/bp-request-info2.md) structures doivent être initialisées.  
  
 Ces indicateurs sont également utilisées pour indiquer les champs de la `BP_REQUEST_INFO` et `BP_REQUEST_INFO2` structures sont utilisées et valides lorsque chaque structure est retournée.  
  
 Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
