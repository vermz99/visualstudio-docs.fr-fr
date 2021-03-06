---
title: Si Concepteur d’activités | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ab8c9a7f49302b2308f97855c022d8e8d5126e0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952529"
---
# <a name="if-activity-designer"></a>Concepteur d'activités If
L'activité <xref:System.Activities.Statements.If> évalue une condition et exécute une activité en fonction des résultats de cette évaluation. Cette activité est très utile lors de l'utilisation d'un style de modélisation des procédures de la programmation. Une activité <xref:System.Activities.Statements.If> peut être imbriquée dans une activité <xref:System.Activities.Statements.Sequence> ou une activité <xref:System.Activities.Statements.Parallel>, par exemple. Si vous utilisez une activité <xref:System.Activities.Statements.Flowchart>, il est conseillé d'utiliser plutôt une activité <xref:System.Activities.Statements.FlowDecision>.  
  
## <a name="if-properties-in-the-workflow-designer"></a>Propriétés d'If dans Workflow Designer  
 Le tableau suivant affiche les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.If> et décrit comment les utiliser dans le concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|Condition qui détermine l'activité enfant à exécuter. Pour définir le <xref:System.Activities.Statements.If.Condition%2A>, tapez un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expression dans le **Condition** zone sur le **si** activité concepteur ou dans la grille des propriétés.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|L’activité à exécuter si le <xref:System.Activities.Statements.If.Condition%2A> est **false**. Pour ajouter une activité est exécutée par le <xref:System.Activities.Statements.If.Else%2A> créer une branche, déplacez une activité de la **boîte à outils** dans le **Else** zone sur le **si** Concepteur d’activités avec le texte d’indication » Déposer l’activité ici ».|  
|<xref:System.Activities.Statements.If.Then%2A>|False|L’activité à exécuter si le <xref:System.Activities.Statements.If.Condition%2A> est **true**. Pour ajouter une activité est exécutée par le <xref:System.Activities.Statements.If.Then%2A> créer une branche, déplacez une activité de la **boîte à outils** dans le **puis** zone sur le **si** Concepteur d’activités avec le texte d’indication » Déposer l’activité ici ».|  
  
## <a name="see-also"></a>Voir aussi  
 [Séquence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)