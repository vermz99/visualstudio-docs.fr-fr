---
title: IDiaEnumTables::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03931580f774c29a67771d2251b51825242535c9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623552"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Récupère un tableau au moyen d’un index ou le nom.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>Paramètres
 `index`

[in] Index ou nom de la [IDiaTable](../../debugger/debug-interface-access/idiatable.md) à récupérer. Si un Variant de type integer est utilisé, il doit être comprise entre 0 et `count`-1, où `count` est renvoyé par le [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) (méthode).

 `table`

[out] Retourne un [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objet représentant la table souhaitée.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques
 Si une variante de la chaîne est spécifiée, la chaîne de noms une table particulière. Le nom doit être un des noms de table comme défini dans [constantes (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).

## <a name="example"></a>Exemple

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>Voir aussi
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [Constantes (Kit de développement logiciel Debug Interface Access)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)