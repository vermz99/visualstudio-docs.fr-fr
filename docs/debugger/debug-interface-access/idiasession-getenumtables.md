---
title: IDiaSession::getEnumTables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 759972fa02c7645ae457e0b715d835b2d717e26f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608589"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Récupère un énumérateur pour toutes les tables contenues dans le magasin de symboles.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>Paramètres
`ppEnumTables`

[out] Retourne un [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) objet. Utilisez cette interface pour énumérer les tables dans le magasin de symboles.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="example"></a>Exemple
Cet exemple présente une fonction générale qui utilise le `getEnumTables` méthode pour obtenir un objet énumérateur spécifique. Si l’énumérateur est trouvé, la fonction retourne un pointeur qui peut être casté vers l’interface souhaitée ; Sinon, la fonction retourne `NULL`.

```C++
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)
{
    IUnknown *pUnknown = NULL;
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumTables> pEnumTables;
        if (pSession->getEnumTables(&pEnumTables) == S_OK)
        {
            CComPtr<IDiaTable> pTable;
            DWORD celt = 0;
            while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&
                  celt == 1)
            {
                if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)
                {
                    break;
                }
                pTable = NULL;
            }
        }
    }
    return(pUnknown);
}
```

## <a name="see-also"></a>Voir aussi
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
