---
title: Fonction n’a pas d’objet prototype valide | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31226f972ff4714dd81207cf27d862d3449184a5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840761"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La fonction ne possède pas d'objet prototype valide
Vous avez tenté d’utiliser **instanceof** pour déterminer si un objet a été dérivé d’une classe fonction particulière, mais redéfinie de l’objet `prototype` propriété en tant que `null`, ou un type d’objet externe (les deux non valide [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objets). Un objet externe peut être un objet à partir du modèle d’objet hôte (par exemple, un document dans Internet Explorer ou objet window) ou un objet COM externe.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous de la fonction `prototype` propriété fait référence à un élément valide [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de fonction](../../javascript/reference/function-object-javascript.md)   
 [Propriété prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)