---
title: IDiaFrameData::execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78440c703ece2aa54e54594d57156dbb17848915
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617702"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Effectue le déroulement de pile et renvoie les résultats dans une interface de frame de parcours de pile.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Paramètres
 `frame`

[in] Un [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objet qui contient l’état des registres de frame.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant montre les valeurs de retournés possibles pour cette méthode.

|Value|Description|
|-----------|-----------------|
|E_DIA_INPROLOG|Impossible d’exécuter un frame de pile, tandis que dans le code de prologue.|
|E_DIA_SYNTAX|Analyser l’erreur s’est produite dans le programme de frame.|
|E_DIA_FRAME_ACCESS|Impossible de registres d’accès ou de la mémoire.|
|E_DIA_VALUE|Erreur dans le calcul d’une valeur (par exemple, la division par zéro).|

## <a name="remarks"></a>Remarques
 Cette méthode est appelée pendant le débogage pour dérouler la pile. Le [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objet est implémenté par l’application cliente pour recevoir des mises à jour aux registres et de fournir des méthodes utilisées par le `execute` (méthode).

## <a name="see-also"></a>Voir aussi
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)