---
title: Filtres de Service des commandes importantes pour la langue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f253f053f9f8fc9a7e377d78ae46307262c13006
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951062"
---
# <a name="important-commands-for-language-service-filters"></a>Commandes importantes pour les filtres du service de langage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Si vous souhaitez créer un filtre de service de langage complet, envisagez de gérer les commandes suivantes. La liste complète des identificateurs de commande est définie dans le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> énumération pour le code managé et l’en-tête Stdidcmd.h de fichier pour unmanaged [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] code. Vous pouvez trouver le fichier Stdidcmd.h dans *chemin d’installation de Visual Studio SDK*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Commandes pour un Handle  
  
> [!NOTE]
>  Il n’est pas obligatoire pour filtrer toutes les commandes dans le tableau suivant.  
  
|Commande|Description|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur clique sur. Cette commande indique qu’il est temps de fournir un menu contextuel. Si vous ne gérez pas cette commande, l’éditeur de texte fournit un menu de raccourci par défaut sans toutes les commandes spécifiques au langage. Pour inclure vos propres commandes de ce menu, gérer la commande et afficher un menu contextuel vous-même.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|En général, envoyées lorsque l’utilisateur tape CTRL + J. Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour afficher la zone de saisie semi-automatique d’instruction.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape un caractère. Surveiller cette commande pour déterminer le moment de la saisie d’un caractère de déclencheur et pour fournir la déclaration de saisie semi-automatique, des conseils de méthode et des marqueurs de texte, telles que la coloration de syntaxe, correspondance des accolades et des marqueurs d’erreur. Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour la saisie semi-automatique des instructions et la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> pour obtenir des conseils (méthode). Pour prendre en charge les marqueurs de texte, surveiller cette commande pour déterminer si le caractère tapé requiert que vous mettez à jour votre marqueurs.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape la touche ENTRÉE. Surveiller cette commande pour déterminer le moment faire disparaître une fenêtre d’info-bulle de méthode en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Par défaut, l’affichage de texte gère cette commande.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape la touche Retour arrière. Analyse pour déterminer le moment faire disparaître une fenêtre d’info-bulle de méthode en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Par défaut, l’affichage de texte gère cette commande.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé à partir d’un menu ou une touche de raccourci. Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour mettre à jour de la fenêtre d’info-bulle avec les informations de paramètre.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur pointe sur une variable ou positionne le curseur sur une variable et sélectionne **Info Express** de **IntelliSense** dans le **modifier** menu. Le type de la variable de retour dans une info-bulle en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Si le débogage est actif, l’info-bulle doit également indiquer la valeur de la variable.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|En général, envoyées lorsque l’utilisateur tape CTRL + espace. Cette commande indique le service de langage pour appeler le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé à partir d’un menu, généralement **commenter la sélection** ou **Décommenter la sélection** de **avancé** dans le **modifier** menu. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Indique que l’utilisateur souhaite commenter le texte sélectionné ; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indique que l’utilisateur souhaite les marques de commentaire du texte sélectionné. Ces commandes peuvent être implémentés uniquement par le service de langage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
