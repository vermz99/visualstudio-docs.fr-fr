---
title: PROVIDER_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 803d9569c611e3c4cd70f2c82ecd525716d8ddb3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687495"
---
# <a name="providerflags"></a>PROVIDER_FLAGS
Spécifie les propriétés souhaitées doivent être obtenues à partir d’un fournisseur de programme.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
typedef DWORD PROVIDER_FLAGS;
```

```csharp
public enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
```

## <a name="members"></a>Membres
 Indicateurs PFLAG_NONE non spécifiés.

 PFLAG_REMOTE_PORT appelant veut une liste des programmes sur un ordinateur différent de celui [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

 PFLAG_DEBUGGEE le processus est en cours de débogage par cette instance de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

 PFLAG_ATTACH_TODEBUGGEE [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] est attaché au programme en cours de débogage, mais ne la démarre pas.

 PFLAG_REASON_WATCH [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] surveille les événements.

 PFLAG_GET_PROGRAM_NODES appelant souhaite le `ProgramNodes` champ la [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) structure.

 PFLAG_GET_IS_DEBUGGER_PRESENT appelant souhaite le `fIsTheDebuggerPresent` champ la `PROVIDER_PROCESS_DATA` structure.

## <a name="remarks"></a>Notes
 Ces indicateurs sont passées aux méthodes suivantes :

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

  Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)