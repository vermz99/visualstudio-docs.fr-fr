---
title: IDebugApplication110::CallableWaitForHandles | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ac5482924288e52895398084aa4f5ab44e151a66
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155366"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Attend qu’une des poignées spécifiées soit signalé tout en permettant aux inter-threads appels seront publiées sur ce thread. Cette méthode doit être appelée à partir du thread de débogueur.  
  
> [!IMPORTANT]
>  [Interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `handleCount`  
 Le nombre de handles à attendre.  
  
 `pHandles`  
 L’ensemble de handles à attendre.  
  
 `pIndex`  
 Lorsque la valeur HRESULT est S_OK, l’index dans `pHandles` pour le handle qui a été signalé.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)