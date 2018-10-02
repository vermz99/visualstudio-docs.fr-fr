---
title: DEBUG_ADDRESS | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 05c6e00591271fc0a8c074e8018bd780c75d1857
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494536"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [DEBUG_ADDRESS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/debug-address).  
  
Cette structure représente une adresse.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Termes  
 ulAppDomainID  
 L’ID de processus.  
  
 guidModule  
 Le GUID du module qui contient cette adresse.  
  
 tokClass  
 Le jeton identifiant la classe ou un type de cette adresse.  
  
> [!NOTE]
>  Cette valeur est spécifique à un fournisseur de symboles et ne possède donc aucun sens général différent en tant qu’identificateur pour un type de classe.  
  
 Addr  
 Un [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) structure qui contient une union de structures qui décrivent les types d’adresses individuelles. La valeur `addr`.`dwKind` provient de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération, qui explique comment interpréter l’union.  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée à la [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) méthode doit être renseigné.  
  
 **Avertissement (C++ uniquement)**  
  
 Si `addr.dwKind` est `ADDRESS_KIND_METADATA_LOCAL` et si `addr.addr.addrLocal.pLocal` n’est pas une valeur null, vous devez l’appeler `Release` sur le pointeur de jeton :  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
