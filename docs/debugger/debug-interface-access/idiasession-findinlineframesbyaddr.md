---
title: IDiaSession::findInlineFramesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e7dc1ac7-bb09-45be-96d2-365a9b7336e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0f35f845642089a8ee2b14c6047e809d525e5bc
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642896"
---
# <a name="idiasessionfindinlineframesbyaddr"></a>IDiaSession::findInlineFramesByAddr
Récupère une énumération qui permet au client d’effectuer une itération dans tous les cadres inline sur une adresse donnée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineFramesByAddr ( 
   IDiaSymbol*       parent,   DWORD             isect,
   DWORD             offset,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `parent`

[in] Un `IDiaSymbol` objet représentant le parent.

 `isect`

[in] Spécifie le composant de la section de l’adresse.

 `offset`

[in] Spécifie le composant de décalage de l’adresse.

 `ppResult`

[out] Contient un `IDiaEnumSymbols` objet qui contient la liste d’images qui sont récupérés.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)