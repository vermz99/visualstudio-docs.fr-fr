---
title: Attendu ']' dans l’expression régulière (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 377bdd6b09c9f25b759d6bf1df2d93e9bd412be5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56839813"
---
# <a name="expected--in-regular-expression-javascript"></a>']' attendu dans l'expression régulière (JavaScript)
Vous a tenté de créer une classe de caractères pour une correspondance d’expression régulière, mais n’incluez pas le crochet droit. Combinaisons de caractères littérale individuels peuvent être assemblés dans les classes de caractères en les plaçant entre crochets. Une classe de caractères correspond à tout caractère qu’il contient. Par exemple, / [abc] / correspond à l’une des lettres « a », « b » ou « c ».  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajoutez le crochet droit à l’expression régulière.  
  
    > [!NOTE]
    >  Si vous souhaitez faire correspondre un seul crochet, l’échappement avec une barre oblique inverse - \\[, afin qu’il n’est pas interprétée comme un caractère spécial par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](https://msdn.microsoft.com/library/1400241x)