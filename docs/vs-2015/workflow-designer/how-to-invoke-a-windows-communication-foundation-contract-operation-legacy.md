---
title: 'Procédure : Appeler une opération de contrat Windows Communication Foundation (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b6cdd551a0cf8ee085359f5545dd16dfac163c4d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947875"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Procédure : Appeler une opération de contrat Windows Communication Foundation (héritée)
Cette rubrique décrit comment appeler une opération de contrat [!INCLUDE[indigo1](../includes/indigo1-md.md)] à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Après avoir fait glisser un **SendActivity** activité à partir de la boîte à outils vers l’aire de conception de workflow, vous devez importer un contrat existant et déterminer quelle opération doit être appelée à partir de là **SendActivity** activité. Vous sélectionnez votre contrat et ses opérations via la [opération boîte de dialogue Choisir (hérité)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Par ailleurs, si vous utilisez un fichier de configuration avec votre service, vous devrez indiquer un jeton <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifie la configuration de point de terminaison qui sera utilisée par l'activité d'envoi pour se connecter au service de workflow.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Appel d'une opération de contrat WCF à partir d'une activité SendActivity  
  
1.  Double-cliquez sur le **SendActivity** activité dans le concepteur ou cliquez sur les points de suspension en regard du **ServiceOperationInfo** propriété dans le **propriétés** volet.  
  
2.  Lorsque le **choisir une opération** boîte de dialogue s’ouvre, cliquez sur **importation** dans le coin supérieur droit de la boîte de dialogue.  
  
     Le [Parcourir et sélectionner une boîte de dialogue de Type .NET (hérité)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) s’ouvre.  
  
3.  Recherchez un assembly ou un projet contenant le contrat souhaité.  
  
4.  Sélectionnez le contrat et cliquez sur **OK**.  
  
5.  Sous **opérations disponibles**, sélectionnez l’opération que vous souhaitez appeler et cliquez sur **OK**.  
  
### <a name="to-specify-a-channel-token"></a>Indication d'un jeton de canal  
  
1.  Sélectionnez l'activité <xref:System.Workflow.Activities.SendActivity> dans le concepteur.  
  
2.  Dans le **propriétés** volet, spécifiez un nom pour le <xref:System.Workflow.Activities.ChannelToken>. Ce nom identifie uniquement le jeton de canal.  
  
3.  Développez le nœud du jeton de canal et indiquez un nom pour le point de terminaison client à utiliser dans le champ <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. La configuration de point de terminaison correspondant au même nom dans le fichier de configuration sera utilisée pour configurer le canal.  
  
4.  Créez la configuration de point de terminaison dans le fichier de configuration, s'il n'existe pas déjà. Pour plus d’informations sur la configuration de votre client, consultez [WCF Client Overview](http://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).  
  
## <a name="see-also"></a>Voir aussi  
 [Choisissez l’opération, boîte de dialogue (hérité)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Guide pratique pour Implémenter une opération de contrat WCF (héritée)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)