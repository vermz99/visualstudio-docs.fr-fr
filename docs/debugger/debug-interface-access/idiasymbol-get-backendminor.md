---
title: IDiaSymbol::get_backEndMinor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4cbdaf9a259e199c0cc32141e961e74f9c91c8c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628622"
---
# <a name="idiasymbolgetbackendminor"></a>IDiaSymbol::get_backEndMinor
Récupère le numéro de version mineure de back-end du compilateur.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_backEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne le numéro de version secondaire du serveur principal. Consultez la section Notes.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 Un compilateur est généralement constitué de deux éléments principaux : le serveur frontal (analyseur), qui gère l’analyse du code source dans un format intermédiaire, et un back-end (Générateur de code), qui convertit le formulaire intermédiaire en assembly. Il n’est pas rare pour le serveur frontal avoir une version différente de celle du serveur principal.

 Un serveur frontal ou le numéro de version de serveur principal est composé de trois parties : \<majeure >.\< mineure >. \<Générer >, où \<majeure > est le numéro de version principale, \<mineure > est le numéro de version mineure et \<Générer > est le numéro de build. Par exemple, 13.10.3077.

## <a name="requirements"></a>Spécifications

|Spécification|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)