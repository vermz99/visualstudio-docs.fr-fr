---
title: Contexte d’évaluation d’expression | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 348fc23fbe240f36e647d12589a9255cec2afad0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947715"
---
# <a name="expression-evaluation-context"></a>Contexte d’évaluation d’expression
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogage, un **contexte d’évaluation d’expression**:  
  
-   Représente un contexte pour l’évaluation d’expression. En règle générale, un contexte d’évaluation correspond à la portée lexicale dans lequel évaluer les variables, paramètres, fonctions et méthodes. Par exemple, un contexte d’évaluation d’expression associé à un frame de pile fournit le contexte pour évaluer les variables locales, les paramètres de méthode et les membres de classe (le cas échéant).  
  
-   Il existe quand un programme s’est arrêté à un point d’arrêt. L’expression elle-même est une structure de données qui représente une expression analysée est prête pour la liaison et l’évaluation dans le contexte donné.  
  
     En plus de détails, les expressions sont créées à l’aide de la [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (méthode). Lorsqu’une expression est évaluée, il génère une chaîne imprimable contenant le nom et le type de variable ou argument et sa valeur. Cette chaîne est affichée dans la fenêtre Espion ou dans la fenêtre variables locales de l’IDE.  
  
     Étant donné un `BSTR` et un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface, un moteur de débogage (dé) pouvez créer un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface par l’analyse d’une expression. Étant donné un `IDebugExpression2` interface, l’Allemagne peut obtenir une valeur via l’évaluation de l’expression synchrones ou asynchrones. Cette valeur, ainsi que le nom et le type de la variable ou un argument, est envoyée à l’IDE pour l’affichage.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)
