---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdfa97ccdbf139ce28ec58c07864551c4e6a7d5a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719520"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Crée un énumérateur pour les énumérateurs imbriquées de cette classe.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>Paramètres
`ppEnum`

 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des énumérations imbriquées. Retourne une valeur null si aucun énumérations imbriquées.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne S_OK, ou retourne S_FALSE s’il en existe aucun énumérateurs imbriqués. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Chaque élément de l’énumération est un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objet décrivant une énumération imbriquée.

Une énumération déclarée à l’intérieur d’une classe est considérée comme une énumération imbriquée. Par exemple, soit :

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

Le `EnumNestedEnums` méthode retournerait une [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet qui contient un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objet qui représente le `NestedEnum` énumération.

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
