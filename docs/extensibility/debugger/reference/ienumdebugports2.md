---
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b39eff84e1933c6181b3e6ae03bd6055b33570e2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716075"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Cette interface énumère les ports d’un fournisseur de l’ordinateur ou le port.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface pour représenter une liste de ports créé par le fournisseur. Visual Studio implémente cette interface pour prendre en charge son propre fournisseur de port.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Appelez [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) pour obtenir cette interface représentant une liste de ports créé par le fournisseur de port. Appelez [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) pour obtenir cette interface représentant une liste des ports qui ont été enregistrés sur le disque.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumDebugPorts2`.

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Récupère un nombre spécifié de ports dans une séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Ignore un nombre spécifié de ports dans une séquence d’énumération.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Réinitialise une séquence d’énumération au début.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Obtient le nombre de ports dans un énumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio utilise cette interface pour aider à remplir une liste des ports utilisés pour attacher au processus.

 En règle générale, un moteur de débogage n’utilise pas cette interface.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)