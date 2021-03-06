---
title: Impossible d’assigner à 'this' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a4ba5d852a7d131a88930dd66931c026074549b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149495"
---
# <a name="cannot-assign-to-this"></a>Impossible d'affecter à 'this'
Vous avez tenté d’affecter une valeur à **cela**. **Cela** est un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mot clé qui fait référence à un :

- l’objet en cours d’exécution une méthode,

- l’objet global si aucune méthode actuel (ou la méthode n’appartient pas à tout autre objet).

Une méthode est un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fonction est appelée via un objet. À l’intérieur d’une méthode, le **cela** mot clé est une référence à l’objet de la méthode a été appelée par le biais (ce qui se trouve l’objet créé en appelant le constructeur de classe avec le **nouveau** opérateur).

À l’intérieur d’une méthode, vous pouvez utiliser **cela** pour faire référence à l’objet en cours, mais vous ne pouvez pas attribuer une nouvelle valeur à **cela**.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- N’essayez pas d’affecter à **cela**. Pour accéder à une propriété ou méthode d’un objet instancié, utilisez l’opérateur point (par exemple, **circle.radius**).

  > [!NOTE]
  > Vous ne pouvez pas nommer une variable créée par l’utilisateur **cela**; il s’agit une [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mot réservé.

## <a name="see-also"></a>Voir aussi

- [Instruction this](../../javascript/reference/this-statement-javascript.md)
- [Résolution des problèmes liés aux scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)