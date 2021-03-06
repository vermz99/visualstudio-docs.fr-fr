---
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c45b1bae11710063d089aeca61a9d20fb6e907a4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691096"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Cette interface représente les informations nécessaires pour créer et lier n’importe quel type de point d’arrêt. Il est une extension de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 En général, le Gestionnaire de session de débogage (SDM) implémente cette interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le moteur de débogage (dé) accède à cette interface en appelant [QueryInterface](/cpp/atl/queryinterface) sur l’interface IDebugBreakpointRequest2 reçu dans un appel à [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes héritées de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), le `IDebugBreakpointRequest3` interface expose la méthode suivante.

|Méthode|Description|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Obtient les informations de demande de point d’arrêt qui décrit cette demande de point d’arrêt.|

## <a name="remarks"></a>Notes
 Cette interface est utilisée pour fournir des informations supplémentaires pour l’Allemagne via le [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structure. Ces informations supplémentaires incluent l’ID de fournisseur de l’Allemagne (sous la forme d’un GUID), le nom d’un point de trace et le nom d’une contrainte de point d’arrêt.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)