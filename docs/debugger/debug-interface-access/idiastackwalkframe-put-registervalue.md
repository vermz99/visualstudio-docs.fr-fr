---
title: IDiaStackWalkFrame::put_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::put_registerValue method
ms.assetid: 2d8b79b6-7240-43fe-b24e-e4ff3e2c15b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 440c7d19382b813b3f34451d7c177c6e8b57f16f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613230"
---
# <a name="idiastackwalkframeputregistervalue"></a>IDiaStackWalkFrame::put_registerValue
Définit la valeur d’un Registre.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Paramètres
 `index`

[in] Une valeur comprise entre le [CV_HREG_e (énumération)](../../debugger/debug-interface-access/cv-hreg-e.md) énumération spécifiant le Registre pour écrire dans.

 `NewVal`

[in] La nouvelle valeur de Registre.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [CV_HREG_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)