---
title: IDebugAlias2::GetAppDomainId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 890e215c7e575e67a4360717851bab538966f419
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715048"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Récupère l’identificateur pour le domaine d’application.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

#### <a name="parameters"></a>Paramètres
 `pappDomainId`

 [out] Retourne l’identificateur de domaine d’application.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les modifications d’identificateur de domaine application chaque fois que l’application est redémarrée et un nouveau domaine d’application est créé.

## <a name="see-also"></a>Voir aussi
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)