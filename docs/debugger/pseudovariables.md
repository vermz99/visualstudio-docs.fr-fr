---
title: Pseudo-variables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 336d177ec939ca0f7dfdc32535e2d2e92b0f04d2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686507"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudo-variables dans le débogueur Visual Studio
Les pseudo-variables sont des termes utilisés pour afficher certaines informations dans une fenêtre de variable ou dans la boîte de dialogue **Espion express**. Vous pouvez entrer une pseudo-variable de la même façon qu'une variable normale. Toutefois, les pseudo-variables ne sont pas des variables et ne correspondent pas à des noms de variable de votre programme.

## <a name="example"></a>Exemple
 Supposez que vous écrivez une application en code natif et que vous voulez afficher le nombre de handles alloués à votre application. Dans la fenêtre **Espion**, entrez la pseudo-variable suivante dans la colonne **Nom**, puis appuyez sur Entrée pour l’évaluer :

`$handles`

 En code natif, vous pouvez utiliser les pseudo-variables indiquées dans le tableau suivant :

|Pseudo-variable|Fonction|
|--------------------|--------------|
|`$err`|Affiche la dernière valeur d'erreur définie avec la fonction SetLastError. La valeur affichée représente la valeur retournée par la fonction GetLastError.<br /><br /> Utilisez `$err,hr` pour afficher cette valeur sous une forme décodée. Par exemple, si la dernière erreur est 3, `$err,hr` affiche `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|
|`$handles`|Affiche le nombre de handles alloués à votre application.|
|`$vframe`|Affiche l'adresse du frame de pile actuel.|
|`$tid`|Affiche l'ID du thread actuel.|
|`$env`|Affiche le bloc environnement de l'explorateur de chaînes.|
|`$cmdline`|Affiche la chaîne de ligne de commande qui a lancé le programme.|
|`$pid`|Affiche l'ID du processus.|
|`$` *registername*<br /><br /> ou<br /><br /> `@` *registername*|Affiche le contenu du registre *registername*.<br /><br /> En règle générale, vous pouvez afficher le contenu du registre en entrant simplement son nom. Vous n'avez besoin d'utiliser cette syntaxe que lorsque le nom de registre surcharge le nom d'une variable. Si le nom de registre est le même que celui d'une variable dans la portée actuelle, le débogueur interprète le nom comme étant celui de la variable. Vous pouvez alors utiliser `$`*registername* ou `@`*registername*.|
|`$clk`|Affiche le temps en cycles d'horloge.|
|`$user`|Affiche une structure avec les informations du compte qui exécute l'application. Pour des raisons de sécurité, les informations de mot de passe ne sont pas affichées.|
|`$exceptionstack`|Affiche l'arborescence des appels de procédure de l'exception Windows Runtime actuelle. `$ exceptionstack` fonctionne uniquement dans les applications UWP. `$ exceptionstack` n’est pas pris en charge pour les exceptions C++ et SEH|
|`$ReturnValue`|Affiche la valeur de retour d'une méthode .NET Framework.|

 En C# et Visual Basic, vous pouvez utiliser les pseudo-variables indiquées dans le tableau suivant :

|Pseudo-variable|Fonction|
|--------------------|--------------|
|`$exception`|Affiche des informations sur la dernière exception. Si aucune exception ne s'est produite, l'évaluation de `$exception` affiche un message d'erreur.<br /><br /> En Visual C# uniquement, quand l’Assistant Exception est désactivé, `$exception` est automatiquement ajouté à la fenêtre **Variables locales** quand une exception se produit.|
|`$user`|Affiche une structure avec les informations du compte qui exécute l'application. Pour des raisons de sécurité, les informations de mot de passe ne sont pas affichées.|

 En Visual Basic, vous pouvez utiliser les pseudo-variables indiquées dans le tableau suivant :

|Pseudo-variable|Fonction|
|--------------------|--------------|
|`$delete` ou `$$delete`|Supprime une variable implicite créée dans la fenêtre **Exécution**. La syntaxe est `$delete,` *variable* ou`$delete,` *variable*`.`|
|`$objectids` ou `$listobjectids`|Affiche tous les ID d'objet actifs en tant qu'enfants de l'expression spécifiée. La syntaxe est `$objectid,` *expression* ou`$listobjectids,` *expression*`.`|
|`$` *N* `#`|Affiche l’objet dont l’ID d’objet est égal à *N*.|
|`$dynamic`|Affiche le nœud spécial **Affichage dynamique** pour un objet qui implémente le `IDynamicMetaObjectProvider`. Interface. La syntaxe est `$dynamic,` *objet*. Cette fonctionnalité s’applique uniquement au code utilisant .NET Framework version 4.|

## <a name="see-also"></a>Voir aussi
- [Espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)
- [Fenêtres de variables](../debugger/debugger-windows.md)