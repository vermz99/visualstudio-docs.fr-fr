---
title: IEnumDebugErrorBreakpoints2::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2::Clone
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Clone
ms.assetid: f6fb4985-8dd6-4a9b-98e0-15dbc64cc9ec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce1b25c032dcdd7b2b9d1b2908904d1eaee6cd9e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698532"
---
# <a name="ienumdebugerrorbreakpoints2clone"></a>IEnumDebugErrorBreakpoints2::Clone
Retourne une copie de l’énumération actuelle comme un objet distinct.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Clone(
   IEnumDebugErrorBreakpoints2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugErrorBreakpoints2 ppEnum
);
```

#### <a name="parameters"></a>Paramètres
 `ppEnum`

 [out] Retourne une copie de cette énumération en tant qu’objet distinct.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 La copie de l’énumération a le même état que l’original au moment de que cette méthode est appelée. Toutefois, les États de la copie et la version d’origine sont distincts et peuvent être modifiées individuellement.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)