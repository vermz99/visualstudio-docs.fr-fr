---
title: IDebugClassField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e062bcfd3b607fe48e2f2c5609b350a463c2f437
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953489"
---
# <a name="idebugclassfield"></a>IDebugClassField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente une classe en tant que type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente le [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface. Cette interface est une spécialisation qui représente un type de classe.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Un nombre d’interfaces ont des méthodes qui peuvent retourner cette interface, notamment [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), et [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). En outre, vous pouvez utiliser [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) pour obtenir cette interface à partir de la [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface si les [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) méthode retourne l’indicateur `FIELD_TYPE_CLASS`.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaces, cette interface implémente les éléments suivants :  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Crée un énumérateur pour les classes de base de cette classe.|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Détermine si une interface spécifique est définie dans la classe.|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Crée un énumérateur pour les classes imbriquées de cette classe.|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Obtient la classe qui définit cette classe.|  
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Crée un énumérateur pour les interfaces implémentées par cette classe.|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Crée un énumérateur pour les constructeurs de cette classe.|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Obtient le nom de l’indexeur par défaut.|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Crée un énumérateur pour les énumérateurs imbriquées de cette classe.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
