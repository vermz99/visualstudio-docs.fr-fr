---
title: Détails de Runtime de contrôle de la source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb52770557fa37a14040b686dcdfbf345a713a2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951270"
---
# <a name="source-control-runtime-details"></a>Détails du Runtime du contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un projet est ajouté au contrôle de code source lorsque l’utilisateur ajoute un fichier dans le projet de contrôle de code source, ou via un contrôleur automation, telles qu’un Assistant. Un projet ne spécifie pas d’elles-mêmes qu’il est sous contrôle de code source ; Il prend en charge le contrôle de code source, mais doit être ajouté manuellement à ce dernier.  
  
## <a name="registering-with-a-source-control-package"></a>L’inscription auprès d’un Package de contrôle de code Source  
 Lorsqu’un fichier dans votre projet est ajouté au contrôle de code source, l’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> pour vous fournir quatre chaînes opaques qui sont utilisés en tant que cookies par le système de contrôle source. Store ces chaînes dans votre fichier projet. Ces chaînes doivent être passés au Stub de contrôle de Source (le composant de Visual Studio qui gère les packages de contrôle de code source) lors du démarrage du type de projet en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Cela charge le package de contrôle de source appropriée à son tour et que vous transfère l’appel à son implémentation de `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)
