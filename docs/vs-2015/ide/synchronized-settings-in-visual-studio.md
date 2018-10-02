---
title: Paramètres synchronisés dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e0facac569671c880004d1fc1a7aa29487e7926
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506412"
---
# <a name="synchronized-settings-in-visual-studio"></a>Paramètres synchronisés dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [synchroniser vos paramètres dans Visual Studio](https://docs.microsoft.com/visualstudio/ide/synchronized-settings-in-visual-studio).  
  
Lorsque vous utilisez le même compte de personnalisation pour vous connecter à Visual Studio sur plusieurs ordinateurs, vos paramètres sont synchronisés par défaut sur tous les ordinateurs.  
  
## <a name="synchronized-settings"></a>Paramètres synchronisés  
 Par défaut, les paramètres suivants sont synchronisés.  
  
-   Paramètres de développement (vous devez sélectionner un ensemble de paramètres la première fois que vous exécutez Visual Studio, mais vous pouvez modifier la sélection à tout moment. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).)  
  
-   Les options suivantes des pages **Outils &#124; Options** :  
  
    -   Paramètres **Thème** et paramètres de mise en majuscules de la barre de menus, dans la page d’options **Environnement**, **Général**  
  
    -   Tous les paramètres de la page d’options **Environnement**, **Polices et couleurs**  
  
    -   Tous les raccourcis clavier de la page d’options **Environnement**, **Clavier**  
  
    -   Tous les paramètres de la page d’options **Environnement, onglets et fenêtres**  
  
    -   Tous les paramètres de la page d’options **Environnement**, **Démarrage**  
  
    -   Tous les paramètres des pages d’options de l’**éditeur de texte**  
  
-   Tous les paramètres sur les pages d'options du concepteur XAML  
  
-   Alias de commande définis par l'utilisateur. Pour plus d’informations sur la façon de définir des alias de commande, consultez [Alias de commandes Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
-   Dispositions des fenêtres définies par l’utilisateur dans la page **Fenêtre &#124; Gérer les dispositions de fenêtres**  
  
## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>Désactivation des paramètres synchronisés pour un ordinateur particulier  
 Les paramètres synchronisés pour Visual Studio sont activés par défaut. Vous pouvez désactiver les paramètres synchronisés sur un ordinateur en accédant à la page **Outils &#124; Options &#124; Environnement &#124; Paramètres synchronisés**, puis en décochant la case correspondante.  Par exemple, si vous décidez de ne pas synchroniser les paramètres de Visual Studio sur l’ordinateur A, toutes les modifications de paramètres effectuées sur l’ordinateur A n’apparaissent pas sur l’ordinateur B ou sur l’ordinateur C. Les ordinateurs B et C continuent à se synchroniser entre eux, mais pas avec l’ordinateur A.  
  
## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Synchronisation des paramètres entre les éditions et les produits de la famille Visual Studio  
 Les paramètres peuvent être synchronisés entre toutes les éditions de Visual Studio 2015, y compris les éditions Express et la Community. Les paramètres sont également synchronisés entre les produits de la famille Visual Studio, tels que Blend. Toutefois, chacun de ces produits de la famille peut avoir ses propres paramètres qui ne sont pas partagés avec Visual Studio. Par exemple, les paramètres spécifiques à Blend sur l'ordinateur A seront partagés avec Blend sur l'ordinateur B, mais pas avec Visual Studio sur l'ordinateur A ou B.  
  
> [!WARNING]
>  Les paramètres ne sont pas synchronisés entre Visual Studio 2013 et Visual Studio 2015. La première fois que vous ouvrez Visual Studio 2015, vos paramètres de Visual Studio 2013 sont migrés, mais ils ne peuvent pas être migrés à nouveau vers Visual Studio 2013.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de l’IDE](../ide/personalizing-the-visual-studio-ide.md)


