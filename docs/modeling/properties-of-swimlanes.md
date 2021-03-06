---
title: Propriétés des couloirs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab2e10eed7452bf58390513bed68fac3f4c9a0f6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55956842"
---
# <a name="properties-of-swimlanes"></a>Propriétés des couloirs
Vous pouvez ajouter des couloirs à un diagramme. Couloirs divisent un diagramme en zones verticales ou horizontales. Vous pouvez définir d’autres formes à afficher à l’intérieur des couloirs. Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Couloirs ont les propriétés qui sont répertoriées dans le tableau suivant.

|Propriété|Description|Par défaut|
|-|-|-|
|Couleur de remplissage de corps|La couleur de remplissage pour le corps du couloir.|Blanc|
|Couleur de remplissage d’en-tête|La couleur de remplissage pour l’en-tête du couloir.|Gris foncé|
|Couleur du séparateur|Couleur de la ligne de séparation.|LightGray|
|Style de séparateur de ligne|Le style de la ligne de séparation (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, ou `Custom`).|`Dash`|
|Épaisseur du séparateur|L’épaisseur de la ligne de séparation en pouces.|0.03125|
|Couleur du texte|La couleur qui est utilisée pour les éléments décoratifs de texte qui sont associés à ce couloir.|Noir|
|Modificateur d'accès|Le niveau d’accès de la classe (`public` ou `internal`).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code est générée à partir de ce couloir.|\<aucune>|
|Génère le Double dérivée|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générés. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|A le constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de couloir (`none`, `abstract` ou `sealed`).|none|
|Couloir de base|La classe de base de ce couloir.|(aucune)|
|Name|Le nom de ce couloir.|Nom actuel|
|Espace de noms|L’espace de noms qui est affilié à ce couloir.|Espace de noms actuel|
|Type de l’info-bulle|Définition de l’info-bulle (`fixed`, `variable`, ou `none`). Si `fixed`, puis la valeur de la `Fixed Tooltip Text` propriété est utilisée ; si `variable`, puis l’info-bulle est définie dans du code personnalisé.|\<aucune>|
|Notes|Remarques informelles associées à ce couloir.|\<aucune>|
|Alignement|Alignement horizontal ou vertical.|Vertical|
|Hauteur initiale|La hauteur initiale de ce couloir, en pouces. Applicable uniquement aux couloirs horizontaux.|0|
|Largeur initiale|Largeur initiale de ce couloir, en pouces. Applicable uniquement aux couloirs verticaux.|0|
|Expose la couleur du texte|Si `True`, l’utilisateur peut définir la couleur d’un couloir dans le concepteur généré. Pour définir ceci, avec le bouton droit de la forme de couloir et cliquez sur **ajouter les objets exposés**.|False|
|Description|Utilisé pour documenter le concepteur généré.|\<aucune>|
|Nom complet|Le nom qui s’affichera dans le concepteur généré pour faire référence à cette classe de couloir.|\<aucune>|
|Texte d’info-bulle fixe|Le texte qui est utilisé pour une info-bulle fixe.|\<aucune>|
|Help Keyword|Le mot clé qui est utilisé pour indexer l’aide F1 pour ce couloir.|\<aucune>|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)