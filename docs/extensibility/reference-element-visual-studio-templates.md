---
title: Faire référence à l’élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c04f644a102af43682bd7bc7569d35f0d5eeacd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704395"
---
# <a name="reference-element-visual-studio-templates"></a>Reference, élément (modèles Visual Studio)
Spécifie la référence d’assembly à ajouter quand l’élément est ajouté à un projet.

 \<VSTemplate > \<TemplateContent > \<références > \<référence >

## <a name="syntax"></a>Syntaxe

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie les informations relatives à un assembly, le modèle utilise pour ajouter une référence de cet assembly aux projets. Il doit y avoir une `Assembly` élément dans chaque `Reference` élément.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Références](../extensibility/references-element-visual-studio-templates.md)|Regroupe les références d’assembly que le modèle ajoute aux projets.|

## <a name="remarks"></a>Notes
 `Reference` est un élément enfant obligatoire de `References`.

 Le `Reference` et `References` éléments peuvent uniquement être utilisés dans *.vstemplate* fichiers ayant une `Type` valeur d’attribut `Item`.

## <a name="example"></a>Exemple
 L’exemple suivant illustre la `TemplateContent` élément d’un modèle d’élément. Ce code XML ajoute des références à la *System.dll* et *System.Data.dll* assemblys.

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
