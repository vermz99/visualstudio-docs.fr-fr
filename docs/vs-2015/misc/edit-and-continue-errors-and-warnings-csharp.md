---
title: Modifier & Continuer des erreurs et avertissements (c#) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.enc.error_4001
- vs.csharp.enc.error_4034
- vs.csharp.enc.error_4003
- vs.csharp.enc.error_4026
- vs.csharp.enc.error_4032
- vs.csharp.enc.error_4017
- vs.csharp.enc.error_4053
- vs.csharp.enc.error_4024
- vs.csharp.enc.error_4012
- vs.csharp.enc.error_4066
- vs.csharp.enc.error_4020
- vs.csharp.enc.error_4008
- vs.csharp.enc.error_4033
- vs.csharp.enc.error_4014
- vs.csharp.enc.error_4023
- vs.csharp.enc.error_4011
- vs.csharp.enc.error_4006
- vs.csharp.enc.error_4059
- vs.csharp.enc.error_4015
- vs.csharp.enc.error_4018
- vs.csharp.enc.error_4028
- vs.csharp.enc.error_4013
- vs.csharp.enc.error_4009
- vs.csharp.enc.error_4021
- vs.csharp.enc.error_4065
- vs.csharp.enc.error_4029
- vs.csharp.enc.error_4058
- vs.csharp.enc.error_4019
- vs.csharp.enc.error_4007
- vs.csharp.enc.error_4052
- vs.csharp.enc.error_4025
- vs.csharp.enc.error_4055
- vs.csharp.enc.error_4022
- vs.csharp.enc.error_4002
- vs.csharp.enc.error_4016
- vs.csharp.enc.error_4043
- vs.csharp.enc.error_4027
- vs.csharp.enc.error_4054
- vs.csharp.enc.error_4004
- vs.csharp.enc.error_4010
- vs.csharp.enc.error_4030
- vs.csharp.enc.error_4005
- vs.csharp.enc.error_4035
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], errors and warnings
- errors [C#], debugging
- errors [debugger], Edit and Continue
ms.assetid: c0e12b0a-8009-4a4a-979f-c804a91a5d9b
caps.latest.revision: 11
ms.author: susanno
manager: douge
ms.openlocfilehash: 98ee36f703af67b3f6ede230203676a30acf19d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508309"
---
# <a name="edit-and-continue-errors-and-warnings-c"></a>Erreurs et avertissements de Modifier & Continuer (C#)
Vous avez modifié une section de code qui n'est pas autorisée en Visual C# dans Modifier & Continuer.  
  
 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]Modifier & Continuer vous permet d'arrêter l'exécution d'un programme en mode Arrêt, d'apporter des modifications à l'exécution de code, puis de continuer l'exécution du programme avec les modifications récemment incorporées.  
  
 Les modifications de code déclaratif qui affectent la structure publique d'une classe sont interdites, et certaines modifications que vous pouvez apporter à une méthode, au corps d'une propriété ou à des déclarations privées dans une classe ne sont pas autorisées. Autant que possible, Modifier & Continuer marque le code qui ne peut pas être modifié en gris clair et affiche un message d'erreur.  
  
 Pour plus d’informations sur les modifications prises en charge dans Modifier & Continuer pour [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], consultez [les modifications de Code prises en charge (c#)](../debugger/supported-code-changes-csharp.md). Pour plus d’informations sur une erreur ou un avertissement spécifique, vous pouvez lancer une recherche ou publier une question sur le [forum de l’IDE Visual C#](http://go.microsoft.com/fwlink/?LinkId=214693)dans MSDN.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Dans le menu **Déboguer** , choisissez **Annuler** pour annuler la modification.  
  
     - ou -  
  
2.  Arrêtez la session de débogage, procédez à vos modifications et démarrez une nouvelle session de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier & Continuer (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)