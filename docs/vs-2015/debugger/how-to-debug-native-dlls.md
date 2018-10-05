---
title: 'Comment : déboguer des DLL natives | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 467b87c1a0e72c5523523aae015f03b54273907c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590750"
---
# <a name="how-to-debug-native-dlls"></a>Comment : déboguer des DLL natives
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : déboguer des DLL natives](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-native-dlls).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Lorsque vous déboguez une DLL, vous pouvez commencer le débogage à partir :  
  
-   du projet utilisé pour créer l'exécutable qui appelle la DLL ;  
  
 \- ou -  
  
-   du projet utilisé pour créer la DLL.  
  
 Si vous disposez du projet utilisé pour créer l'exécutable, démarrez le débogage à partir de ce projet. Vous pouvez ensuite ouvrir un fichier source pour la DLL et définir les points d'arrêt dans ce fichier, même s'il ne fait pas partie du projet utilisé pour créer l'exécutable. Pour plus d’informations, consultez [des points d’arrêt](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
 Si vous démarrez le débogage à partir du projet qui crée la DLL, vous devez spécifier l'exécutable que vous voulez utiliser dans le débogage de la DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Pour spécifier un exécutable pour la session de débogage  
  
1.  Dans **l’Explorateur de solutions**, sélectionnez le projet qui crée la DLL.  
  
2.  À partir de la **vue** menu, choisissez**Pages de propriétés**.  
  
3.  Dans le **Pages de propriétés** boîte de dialogue, ouvrez le **propriétés de Configuration** dossier et sélectionnez le **débogage** catégorie.  
  
4.  Dans le **commande** , spécifiez le nom de chemin d’accès pour le conteneur. Par exemple, C:\Program Files\MyApplication\MYAPP.EXE.  
  
5.  Dans le **Arguments de commande** , spécifiez les arguments nécessaires pour le fichier exécutable.  
  
 Si vous ne spécifiez pas l’exécutable dans le _projet_**Pages de propriétés** boîte de dialogue, le [exécutable pour la boîte de dialogue de Session de débogage](../debugger/executable-for-debugging-session-dialog-box.md) s’affiche lorsque vous démarrez le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)


