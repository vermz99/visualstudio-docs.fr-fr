---
title: 'CA1054 : Paramètres URI ne doivent pas être chaînes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f7af579cf92a785f9850805ae06743a15364eade
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938504"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054 : Les paramètres URI ne doivent pas être des chaînes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type déclare une méthode avec un paramètre de chaîne dont le nom contient « uri », « Uri », « urn », « Urn », « url » ou « Url » et le type ne déclare pas une surcharge correspondante qui accepte un <xref:System.Uri?displayProperty=fullName> paramètre.

## <a name="rule-description"></a>Description de la règle
 Cette règle fractionne le nom du paramètre en jetons basés sur la convention de casse mixte et vérifie si chaque jeton est égal à « uri », « Uri », « urn », « Urn », « url » ou « Url ». S’il existe une correspondance, la règle suppose que le paramètre représente un identificateur de ressource uniforme (URI). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. Si une méthode accepte une représentation sous forme de chaîne d’un URI, une surcharge correspondante doit être fournie qui prend une instance de la <xref:System.Uri> classe, qui fournit ces services de manière sûre et sécurisée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez le paramètre pour un <xref:System.Uri> tapez ; il s’agit d’une modification avec rupture. Vous pouvez également fournir une surcharge de la méthode qui prend un <xref:System.Uri> paramètre ; il s’agit d’une modification sans rupture.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si le paramètre ne représente pas un URI.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type, `ErrorProne`, qui enfreint cette règle et un type, `SaferWay`, qui satisfait la règle.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1056 : Propriétés de l’URI ne doivent pas être de chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055 : Les valeurs doivent être pas des chaînes de retour URI](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234 : Passez des objets System.Uri au lieu de chaînes](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057 : Surcharges d’URI de chaîne appellent les surcharges de System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
