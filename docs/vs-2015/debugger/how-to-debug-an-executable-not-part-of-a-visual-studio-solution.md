---
title: 'Comment : déboguer une partie non exécutable d’une Solution Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36acf39ce892afb2a2601b3149987aa8d7e9f4ab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508201"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Comment : déboguer un fichier exécutable ne faisant pas partie d'une solution Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : déboguer un fichier exécutable ne fait pas partie d’une Solution Visual Studio](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-an-executable-not-part-of-a-visual-studio-solution).  
  
Vous pouvez être amené à déboguer un exécutable qui ne fait pas partie d'un projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Il peut s'agir d'un exécutable créé en dehors de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou reçu de la part d'un tiers.  
  
 La réponse usuelle à ce problème consiste à démarrer l'exécutable en dehors de Visual Studio, puis à l'attacher à l'aide du débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pour plus d’informations, consultez[attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 L'attachement à une application requiert quelques étapes manuelles, qui prennent tout de même quelques secondes. Ce léger décalage peut rendre l'attachement inutile si vous essayez de déboguer un problème survenant au démarrage. De même, si vous déboguez un programme qui n'attend aucune entrée d'utilisateur et se termine rapidement, vous risquez de ne pas avoir le temps de l'attacher. Si [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] est installé, vous pouvez créer un projet EXE pour un tel programme.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Pour créer un projet EXE pour un exécutable existant  
  
1.  Sur le **fichier** menu, cliquez sur **Open** et sélectionnez **projet**.  
  
2.  Dans le **ouvrir un projet** boîte de dialogue, cliquez sur la liste déroulante liste située en regard du **nom de fichier** zone, puis sélectionnez **tous les fichiers de projet**.  
  
3.  Localiser le fichier exécutable, puis cliquez sur **OK**.  
  
     Cela permet de créer une solution temporaire contenant l'exécutable.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Pour importer un exécutable dans une solution Visual Studio  
  
1.  Sur le **fichier** menu, pointez sur **ajouter un projet**, puis cliquez sur **projet existant**.  
  
2.  Dans le **ajouter un projet existant** boîte de dialogue, cliquez sur la liste déroulante liste située en regard du **nom de fichier** zone, puis sélectionnez **tous les fichiers de projet**.  
  
3.  Recherchez et sélectionnez l'exécutable.  
  
4.  Cliquez sur **OK**.  
  
5.  Démarrer l’exécutable en choisissant une commande d’exécution, telles que **Démarrer**, à partir de la **déboguer** menu.  
  
    > [!NOTE]
    >  Tous les langages de programmation ne prennent pas en charge les projets EXE. Installez [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] si vous devez utiliser cette fonctionnalité.  
  
     Lorsque vous déboguez un exécutable sans le code source, les fonctionnalités de débogage disponibles sont limitées, que vous attachiez l'exécutable en cours d'exécution ou que vous l'ajoutiez à une solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si l'exécutable a été généré sans informations de débogage dans un format compatible, les fonctionnalités disponibles sont encore plus limitées. Si vous disposez du code source, la meilleure approche consiste à l'importer dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour y créer une version Debug de l'exécutable[!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Fichiers DBG](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)


