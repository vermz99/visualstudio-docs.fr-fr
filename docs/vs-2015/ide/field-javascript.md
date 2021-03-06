---
title: '&lt;field&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2fe09070261460b7b83f54de44a07cf96d40cf2
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54766554"
---
# <a name="ltfieldgt-javascript"></a>&lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie les informations de documentation, y compris une description, pour un champ ou un membre qui est défini sur un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `name`  
 Le nom du champ ou du membre. Lorsque le `<field>` élément est utilisé dans une fonction constructeur, `name` est obligatoire et définit le membre auquel s’applique la balise. Lorsque le `<field>` élément annote directement un champ, cet attribut est ignoré, et le nom utilisé par Visual Studio est le nom du champ réel dans le code source.  
  
 `static`  
 Optionnel. Spécifie si le champ est un membre de la fonction de constructeur ou un membre de l’objet retourné par la fonction constructeur. La valeur `true` à traiter le champ en tant que membre de la fonction constructeur. La valeur `false` à traiter le champ en tant que membre de l’objet retourné par la fonction constructeur.  
  
 `type`  
 Optionnel. Le type de données du champ. Le type peut être une des opérations suivantes :  
  
- Un langage ECMAScript tapez dans la spécification ECMAScript 5, tel que `Number` et `Object`.  
  
- Un modèle DOM de l’objet, tel que `HTMLElement`, `Window`, et `Document`.  
  
- Une fonction de constructeur JavaScript.  
  
  `integer`  
  Optionnel. Si `type` est `Number`, spécifie si le champ est un entier. La valeur `true` pour indiquer que le champ est un entier ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `domElement`  
  Optionnel. Cet attribut est déconseillé ; le `type` attribut est prioritaire sur cet attribut. Cet attribut spécifie si le champ documenté est un élément DOM. La valeur `true` pour spécifier que le champ est un élément DOM ; sinon, la valeur est `false`. Si le `type` attribut n’est pas défini et `domElement` a la valeur `true`, IntelliSense traite le champ documenté comme un `HTMLElement` lors de l’exécution de saisie semi-automatique des instructions.  
  
  `mayBeNull`  
  Optionnel. Spécifie si le champ documenté peut être défini sur null. La valeur `true` pour indiquer que le champ peut être défini à null ; sinon, la valeur est `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementType`  
  Optionnel. Si `type` est `Array`, cet attribut spécifie le type des éléments du tableau.  
  
  `elementInteger`  
  Optionnel. Si `type` est `Array` et `elementType` est `Number`, cet attribut spécifie si les éléments du tableau sont des entiers. La valeur `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementDomElement`  
  Optionnel. Cet attribut est déconseillé ; le `elementType` attribut est prioritaire sur cet attribut. Si `type` est `Array`, cet attribut spécifie si les éléments du tableau sont des éléments DOM. La valeur `true` pour spécifier que les éléments sont des éléments DOM ; sinon, la valeur est `false`. Si le `elementType` attribut n’est pas défini et `elementDomElement` a la valeur `true`, IntelliSense traite chaque élément dans le tableau comme un `HTMLElement` lors de l’exécution de saisie semi-automatique des instructions.  
  
  `elementMayBeNull`  
  Optionnel. Si `type` est `Array`, spécifie si les éléments dans le tableau peuvent être définis sur null. La valeur `true` pour indiquer que les éléments dans le tableau peuvent être définies à null ; sinon, la valeur est `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `helpKeyword`  
  Optionnel. Le mot clé d’aide F1.  
  
  `locid`  
  Optionnel. L’identificateur pour les informations de localisation sur le champ. L’identificateur est un membre ID ou il correspond à la `name` valeur dans un regroupement de message défini par OpenAjax métadonnées d’attribut. Le type d’identificateur varie selon le format spécifié dans le [ \<loc >](../ide/loc-javascript.md) balise.  
  
  `value`  
  Optionnel. Spécifie le code qui doit être évalué pour une utilisation par IntelliSense au lieu du code de fonction lui-même. Pour `<field>`, cet attribut est pris en charge pour les fonctions de constructeur, mais n’est pas pris en charge pour les littéraux d’objet. Vous pouvez utiliser cet attribut est de fournir des informations de type lorsque le type de champ n’est pas défini. Par exemple, vous pouvez utiliser `value=’1’` pour traiter le type de champ en tant que nombre.  
  
  `description`  
  Optionnel. Une description pour le champ.  
  
## <a name="remarks"></a>Remarques  
 Le `name` attribut est requis lorsque vous documentez un champ dans une fonction constructeur. Pour tous les autres scénarios, tous les attributs pour le `<field>` élément sont facultatifs.  
  
 Lorsque vous documentez une fonction constructeur, le `<field>` élément doit apparaître immédiatement avant la déclaration de champ. Le `name` attribut doit correspondre au nom de champ qui est utilisé dans le code source. Pour les membres de l’objet, le `name` attribut peut être omis si le `<field>` élément apparaît immédiatement avant la déclaration de membre d’objet.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser le `<field>` élément.  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `<field>` élément avec la `static` attribut la valeur `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `<field>` élément avec la `static` attribut la valeur `false`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `<field>` élément avec la `value` attribut.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)
