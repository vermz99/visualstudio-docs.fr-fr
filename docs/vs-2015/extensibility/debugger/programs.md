---
title: Programmes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c9beccd5e72c26d695d443c4ab2aa4198e71784
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953822"
---
# <a name="programs"></a>Programs
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En termes d’architecture du débogueur, une **programme**:  
  
-   Est un conteneur pour un ensemble de threads et un ensemble de modules. Un programme n’a aucune analogie unique dans le système d’exploitation Windows.  
  
     Un programme est un genre de sous-processus. Par exemple, lorsque vous déboguez un site Web, un script peut être considéré comme un programme. Même si un script s’exécute dans le processus de moteur de script, indépendamment des autres scripts, il également possède son propre ensemble de threads. Un moteur de débogage (dé) joint à un programme et non à un processus ou un thread.  
  
-   Peut identifier lui-même et le processus est en cours d’exécution, elle peut être attaché pour être détaché et décrivent le DE qui l’a créé, le cas échéant. Un programme peut exécuter, arrêter, continuer et se terminer.  
  
-   Peut énumérer tous ses threads. Un programme peut également fournir son propre flux de code machine et pouvez énumérer tous les contextes de code d’une position de document donné.  
  
-   Est représenté par un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interface, créée avant que le programme est attaché, ou dans le cadre du processus d’attachement, selon l’implémentation. Lorsqu’un port énumère les programmes d’un processus, chaque programme est créé conformément à un correspondant [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface passée en tant qu’argument à [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Tandis que les moteurs de débogage également créer `IDebugProgram2` interfaces pour les programmes, ces programmes ne sont pas créés conformément à un nœud de programme. Le `IDebugProgramNode2` interfaces créés par un DE sont utilisés pour le débogage réel, tandis que ceux créés par un port sont utilisés uniquement pour découvrir les programmes qui sont exécutent dans un processus.  
  
## <a name="see-also"></a>Voir aussi  
 [Processus](../../extensibility/debugger/processes.md)   
 [Nœuds de programme](../../extensibility/debugger/program-nodes.md)   
 [Modules](../../extensibility/debugger/modules.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Position du document](../../extensibility/debugger/document-position.md)   
 [Contexte de code](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
