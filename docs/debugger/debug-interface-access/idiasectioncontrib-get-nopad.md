---
title: IDiaSectionContrib::get_nopad | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51fb2c4ff2f27cee8fcc989139f5ae14c2641394
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642142"
---
# <a name="idiasectioncontribgetnopad"></a>IDiaSectionContrib::get_nopad
Récupère un indicateur qui spécifie si la section ne doit pas être complétées à concurrence de la limite de mémoire suivante.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_nopad(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne `TRUE` si la section ne doit pas être complétées à concurrence de la limite de mémoire suivante ; sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Il s’agit d’une propriété que se produite généralement uniquement sur les fichiers plus anciens.

## <a name="see-also"></a>Voir aussi
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)