---
title: IDiaFrameData::get_program | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6b893a40172bfd806130bef663da8676b513042
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636396"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
Récupère la chaîne de programme qui est utilisée pour calculer le Registre défini avant l’appel à la fonction active.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne la chaîne de programme.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 La chaîne de programme est une séquence de macros est interprétée afin d’établir le prologue. Par exemple, un frame de pile classique peut utiliser la chaîne de programme `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Le format est la notation polonaise inverse, où les opérateurs suivent les opérandes. `T0` représente une variable temporaire sur la pile. Cet exemple effectue les étapes suivantes :

1. Déplacer le contenu du Registre `ebp` à `T0`.

2. Ajouter `4` à la valeur de `T0` pour produire une adresse, obtenir la valeur de cette adresse et stockez la valeur de Registre `eip`.

3. Obtenir la valeur de l’adresse stockée dans `T0` et stocker cette valeur dans le Registre `ebp`.

4. Ajouter `8` à la valeur de `T0` et stocker cette valeur dans le Registre `esp`.

   Notez que la chaîne de programme est spécifique au processeur et à la convention d’appel défini pour la fonction représentée par le frame de pile actuel.

## <a name="see-also"></a>Voir aussi
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)