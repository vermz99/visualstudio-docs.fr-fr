---
title: 'Erreur : Échec d’ouverture de session à distance du groupe de travail | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d0157b18c0b0dfce2ba69482dc1c61e1ddf3a996
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952412"
---
# <a name="error-workgroup-remote-logon-failure"></a>Erreur : Échec de l’ouverture de session à distance du groupe de travail
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette erreur affiche le message suivant :  
  
 Échec d'ouverture de session : nom d'utilisateur inconnu ou mot de passe incorrect  
  
 **Cause**  
  
 Cette erreur peut se produire lorsque vous déboguez à partir d'un ordinateur au sein d'un groupe de travail et que vous tentez de vous connecter à un ordinateur distant. Plusieurs causes sont possibles :  
  
-   Il n'existe pas de compte avec le nom et le mot de passe correspondants sur l'ordinateur distant.  
  
-   Si l’ordinateur Visual Studio et l’ordinateur distant appartiennent à des groupes de travail, cette erreur peut se produire en raison du paramètre par défaut **Stratégie de sécurité locale** sur l’ordinateur distant. L’option par défaut du paramètre **Stratégie de sécurité locale** est **Invité seul - les utilisateurs locaux s’authentifient en tant qu’invités**. Pour effectuer un débogage sur cette installation, vous devez remplacer le paramètre sur l’ordinateur distant par **Classique - les utilisateurs locaux s’authentifient eux-mêmes**.  
  
> [!NOTE]
>  Vous devez être administrateur pour exécuter les tâches suivantes.  
  
### <a name="to-open-the-local-security-policy-window"></a>Pour ouvrir la fenêtre Stratégie de sécurité locale  
  
1.  Démarrez le composant logiciel enfichable Microsoft Management Console **secpol.msc**. Tapez secpol.msc dans la zone de recherche Windows, dans la zone Exécuter de Windows, ou dans une invite de commandes.  
  
### <a name="to-add-user-rights-assignments"></a>Pour ajouter des assignations de droits utilisateur  
  
1.  Ouvrez les Paramètres régionaux  
  
2.  Ouvrez la fenêtre **Stratégie de sécurité locale**.  
  
3.  Développez le dossier **Stratégies locales**.  
  
4.  Cliquez sur **Attribution des droits utilisateur**.  
  
5.  Dans la colonne **Stratégie**, double-cliquez sur **Déboguer des programmes pour afficher les assignations de la stratégie de groupe locale** dans la boîte de dialogue **Paramètre de stratégie de sécurité locale**.  
  
     ![Droits d’utilisateur de stratégie de sécurité locale](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  Pour ajouter de nouveaux utilisateurs, cliquez sur le bouton **Ajouter un utilisateur ou un groupe**.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Pour modifier le modèle de partage et de sécurité  
  
1.  Ouvrez la fenêtre **Stratégie de sécurité locale**.  
  
2.  Développez le dossier **Stratégies locales**.  
  
3.  Cliquez sur **Options de sécurité**.  
  
4.  Dans le **stratégie** colonne, double-cliquez sur **accès réseau : Modèle de partage et de sécurité pour les comptes locaux**.  
  
5.  Dans le **accès réseau : Modèle de partage et de sécurité pour les comptes locaux** boîte de dialogue, changez la valeur à **classique - les utilisateurs locaux s’authentifient eux-mêmes** et cliquez sur le **appliquer** bouton.  
  
     ![Options de sécurité de stratégie de sécurité locale](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs de débogage à distance et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
