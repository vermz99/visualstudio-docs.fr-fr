---
title: IDebugSymbolProvider::GetAddressesFromPosition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e615abb8bf4a535f88dd1df483540ac84e5ca5e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705214"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Cette méthode mappe une position de document dans un tableau d’adresses de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

#### <a name="parameters"></a>Paramètres
 `pDocPos`

 [in] La position du document.

 `fStatmentOnly`

 [in] Si la valeur est TRUE, limite les adresses de débogage à une seule instruction.

 `ppEnumBegAddresses`

 [out] Retourne un énumérateur pour les adresses de débogage début associé à cette instruction ou de la ligne.

 `ppEnumEndAddresses`

 [out] Retourne un [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) énumérateur pour les adresses de débogage fin associée à cette instruction ou de la ligne.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Position du document indique généralement une plage de lignes de code source. Cette méthode fournit le début et fin des adresses de débogage associés à ces lignes. Certains langages permettent aux instructions qui s’étendent sur plusieurs lignes, ou qui contient plusieurs instructions. Cette méthode fournit un indicateur pour limiter les adresses de débogage à une seule instruction.

 Il est possible qu’une seule instruction d’avoir plusieurs adresses de débogage, comme dans le cas des modèles.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)