---
title: Prise en charge du Service de langage pour le débogage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7be41a5078e9f8dc009dda0d34394092234cd7e6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948811"
---
# <a name="language-service-support-for-debugging"></a>Prise en charge du service de langage pour le débogage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un service de langage peut fournir des fonctionnalités qui prennent en charge d’un débogueur via le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interface. Ces fonctionnalités incluent la validation des points d’arrêt et en fournissant une liste d’expressions pour les **automatique** fenêtre.  
  
 Toutefois, vous devez disposer d’un évaluateur d’expression pour déboguer votre langue. L’évaluateur d’expression est chargée d’évaluer des expressions afin de générer des valeurs pendant le débogage. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez :  
  
-   [Évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Exemple d’évaluateur d’Expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Résultats de la compilation  
 Le type du compilateur détermine ce que vous devez faire pour implémenter le débogage pour votre langue. Si votre compilateur cible le système d’exploitation Windows et écrit un fichier .pdb, vous pouvez déboguer des programmes avec le moteur est intégré à Visual Studio de débogage du code natif. Si votre compilateur produit Microsoft intermediate language (MSIL), vous pouvez déboguer des programmes avec le moteur, ce qui est également intégré à Visual Studio de débogage du code managé. Si votre compilateur cible un système d’exploitation propriétaire ou un environnement d’exécution différents, vous devez écrire votre propre moteur de débogage.  
  
 Pour plus d’informations sur l’implémentation de débogage pour votre langage, consultez [mise en route](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) dans le SDK de débogage de Visual Studio.
