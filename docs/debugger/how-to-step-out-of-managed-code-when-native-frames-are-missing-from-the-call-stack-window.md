---
title: Sortant C# lorsque les frames natifs sont manquants dans la pile des appels de code | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 25021f0c3daffdaf59633fdb9bff0e2659f43d2e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043023"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Procédure : Pas à pas sortant du code managé quand des images natives manquent dans la fenêtre Pile des appels

Si votre code intègre des frames natifs invisibles dans la fenêtre **Pile des appels**, une sortie pas à pas du code managé peut produire des résultats inattendus. Pour éviter cela, vous pouvez utiliser un point d’arrêt plutôt qu’un **Pas à pas sortant**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Sortir pas à pas du code managé quand les frames natifs n’apparaissent pas dans la fenêtre Pile des appels

1.  Dans le code natif, définissez un point d'arrêt d'emplacement après l'appel de code managé.

2.  Dans le menu **Déboguer**, sélectionnez **Continuer**.

     Une fois que l'appel de code managé sera terminé, l'exécution s'arrêtera au point d'arrêt dans le code natif.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md)