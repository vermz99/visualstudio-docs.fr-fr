---
title: Analyse du code pour les avertissements de Code managé | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4e1d74a44db244ed83e7d05fb09e66c96475466c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503393"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Analyse du code pour les avertissements liés au code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [analyse du Code pour les avertissements de Code géré](https://docs.microsoft.com/visualstudio/code-quality/code-analysis-for-managed-code-warnings).  
  
L’outil Analyse du code managé fournit des avertissements qui indiquent des violations de règle dans les bibliothèques de code managé. Les avertissements sont organisés en domaines de règles, tels que la conception, la localisation, les performances et la sécurité. Chaque avertissement indique une violation d’une règle d’analyse du code managé. Cette section fournit des explications et des exemples détaillés de chaque avertissement d’analyse du code managé.  
  
 Le tableau suivant indique le type d’informations fourni pour chaque avertissement.  
  
|Élément|Description|  
|----------|-----------------|  
|Type|TypeName de la règle.|  
|CheckId|Identificateur unique de la règle. CheckId et Category sont utilisés pour la suppression à la source d’un avertissement.|  
|Category|Catégorie de l’avertissement.|  
|Modification avec rupture|Indique si la correction d’une violation de la règle constitue une modification avec rupture. Une modification avec rupture signifie qu’un assembly qui présente une dépendance à la cible ayant provoqué la violation ne se recompile pas avec la nouvelle version corrigée ou peut échouer au moment de l’exécution en raison de la modification. Quand plusieurs corrections sont possibles et qu’au moins l’une d’elles est une modification avec rupture et qu’une autre ne l’est pas, les caractéristiques « Avec rupture » et « Sans rupture » sont toutes deux spécifiées.|  
|Cause|Code managé spécifique qui contraint la règle à générer un avertissement.|  
|Description|Décrit les problèmes sous-jacents à l’avertissement.|  
|Comment corriger les violations|Explique comment modifier le code source pour satisfaire la règle et l’empêcher de générer un avertissement.|  
|Quand supprimer les avertissements|Décrit les circonstances dans lesquelles il est possible de supprimer un avertissement de la règle en toute sécurité.|  
|Exemple de code|Exemples qui violent la règle et exemples corrigés qui satisfont la règle.|  
|Avertissements connexes|Avertissements connexes.|  
  
## <a name="in-this-section"></a>Dans cette section  
  
|||  
|-|-|  
|[Avertissements par CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Répertorie tous les avertissements par CheckId.|  
|[Avertissements relatifs au chiffrement](../code-quality/cryptography-warnings.md)|Avertissements gérant la sécurité des bibliothèques et des applications via l’utilisation correcte du chiffrement.|  
|[Avertissements liés à la conception](../code-quality/design-warnings.md)|Avertissements qui prennent en charge de la conception correcte des bibliothèques comme spécifié par le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] instructions de conception.|  
|[Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)|Avertissements gérant les applications et les bibliothèques universelles.|  
|[Avertissements liés à l’interopérabilité](../code-quality/interoperability-warnings.md)|Avertissements gérant l’interaction avec les clients COM.|  
|[Avertissements liés à la facilité de maintenance](../code-quality/maintainability-warnings.md)|Avertissements gérant la maintenance des bibliothèques et des applications.|  
|[Mobility Warnings](../code-quality/mobility-warnings.md)|Avertissements gérant l’optimisation de la consommation d’énergie.|  
|[Avertissements liés à l’affectation de noms](../code-quality/naming-warnings.md)|Avertissements gérant l’adhésion aux conventions d’affectation de noms de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] instructions de conception.|  
|[Avertissements liés aux performances](../code-quality/performance-warnings.md)|Avertissements gérant les hautes performances des applications et des bibliothèques.|  
|[Portability Warnings](../code-quality/portability-warnings.md)|Avertissements gérant la portabilité sur différentes plateformes.|  
|[Avertissements liés à la fiabilité](../code-quality/reliability-warnings.md)|Avertissements gérant la fiabilité des bibliothèques et des applications, notamment une utilisation adaptée des threads et de la mémoire.|  
|[Avertissements liés à la sécurité](../code-quality/security-warnings.md)|Avertissements gérant la sécurité des bibliothèques et des applications.|  
|[Avertissements liés à l’utilisation](../code-quality/usage-warnings.md)|Avertissements qui prennent en charge l’utilisation adéquate de le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].|  
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|Erreurs qui se produisent si la stratégie d’analyse du code n’est pas satisfaite au moment de l’archivage.|


