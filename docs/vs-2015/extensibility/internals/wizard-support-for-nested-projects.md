---
title: Prise en charge de l’Assistant pour les projets imbriqués | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4621627faae761bfe63b7fd056427a3771d21582
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507521"
---
# <a name="wizard-support-for-nested-projects"></a>Prise en charge de l’Assistant pour les projets imbriqués
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [prise en charge de l’Assistant pour les projets imbriqués](https://docs.microsoft.com/visualstudio/extensibility/internals/wizard-support-for-nested-projects).  
  
L’IDE exécute deux Assistants projet parent pour les projets imbriqués peut implémenter : le **nouveau projet** Assistant et le **ajouter un élément** Assistant.  
  
 Si un utilisateur démarre la **nouveau projet** Assistant en sélectionnant **ajouter un projet** et en cliquant sur **nouveau projet** dans le menu fichier ou en sélectionnant **ajouter** et cliquant **nouveau projet** dans l’Explorateur de solutions, l’IDE exécute la **ajouter** commande et l’implémentation du projet parent de la **ajouter**renvoie un fichier de projet de modèle ou un fichier de l’Assistant (.vsz) qui dispose d’un ensemble de paramètres de contexte.  
  
 De même, d’un projet parent mise en œuvre de **AddItem** Assistants retourne un fichier .vsz qui possède un ensemble différent de paramètres de contexte.  
  
 Pour plus d’informations sur les Assistants, consultez [Assistant (. Fichier vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [paramètres de contexte](../../extensibility/internals/context-parameters.md) et [inscription Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)
