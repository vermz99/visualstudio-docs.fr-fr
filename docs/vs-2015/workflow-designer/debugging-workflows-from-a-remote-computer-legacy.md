---
title: Débogage de Workflows à partir d’un ordinateur distant (hérité) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f37e2f1d785399283e9da8f4ecb853f0728d9830
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948849"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Débogage de workflows d'un ordinateur distant (hérité)
Cette rubrique décrit comment déboguer des applications [!INCLUDE[wf](../includes/wf-md.md)] héritées distantes générées avec le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque votre application doit cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Lorsque vous installez [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)], une des options d’installation de composant consiste à installer le [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] du débogueur pour [!INCLUDE[wf](../includes/wf-md.md)]. Cela installe les composants de débogage distant. Ces composants de débogage distant doivent être installés sur l'ordinateur que vous utiliserez pour le débogage distant de workflows.  
  
 En outre, l'assembly qui contient la définition du workflow hérité que vous déboguez sur un ordinateur distant doit être installé dans le Global Assembly Cache (GAC) de l'ordinateur local utilisé pour le débogage. Par exemple, si un workflow hérité est exécuté sur un ordinateur distant A et que vous le déboguez à partir de l'ordinateur local B, la définition de workflow doit être présente dans le GAC de l'ordinateur B. Cela permet au concepteur de désérialiser et d'afficher sur l'ordinateur B le balisage du workflow exécuté à distance sur l'ordinateur A. Pour plus d'informations sur le Global Assembly Cache, consultez MSDN Library.  
  
 Le débogage distant [!INCLUDE[wf2](../includes/wf2-md.md)] fonctionne sur le même principe que débogage distant d'autres composants [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pour plus d’informations, consultez [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] débogage à distance dans la bibliothèque MSDN.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)