---
title: 'Procédure : Connexion fichiers d’installation avec SignTool.exe (ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbbc745ae2d0a20ab14b3960e34182d7f4ed1865
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949637"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Procédure : Signer des fichiers d’installation avec SignTool.exe (ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser SignTool.exe pour signer un programme d'installation (setup.exe). Ce processus aide à garantir que les fichiers falsifiés ne sont pas installés sur les ordinateurs des utilisateurs finaux.  
  
 Par défaut, ClickOnce dispose de manifestes signés, ainsi que d'un programme d'installation signé. Toutefois, si vous souhaitez modifier ultérieurement les paramètres du programme d'installation, vous devrez également signer le programme d'installation. Si vous modifiez les paramètres après avoir signé le programme d'installation, la signature sera endommagée.  
  
 La procédure suivante génère des manifestes non signés ainsi qu'un programme d'installation non signé. La signature ClickOnce est ensuite activée dans Visual Studio pour générer des manifestes signés. Le programme d'installation n'est pas signé pour que les clients puissent signer l'exécutable avec leurs propres certificats.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Pour générer un programme d'installation non signé et le signer ultérieurement  
  
1.  Sur l'ordinateur de développement, installez le certificat avec lequel vous souhaitez signer les manifestes.  
  
2.  Sélectionnez le projet dans **l’Explorateur de solutions**.  
  
3.  Dans le menu **Projet**, cliquez sur **Propriétés** de *NomProjet*.  
  
4.  Dans la page **Connexion**, décochez **Signer les manifestes ClickOnce**.  
  
5.  Dans la page **Publier**, cliquez sur **Composants requis**.  
  
6.  Vérifiez que tous les composants requis sont sélectionnés, puis cliquez sur **OK**.  
  
7.  Dans la page **Publier**, vérifiez les paramètres de publication, puis cliquez sur **Publier maintenant**.  
  
     La solution publie le manifeste d'application non signé, le manifeste de déploiement non signé, les fichiers spécifiques à la version et le programme d'installation non signé à l'emplacement du dossier de publication.  
  
8.  Dans la page **Publier**, cliquez sur **Composants requis**.  
  
9. Dans la boîte de dialogue **Composants requis**, vérifiez que la case **Créer un programme d’installation des composants requis** est cochée.  
  
10. Dans la page **Publier**, vérifiez les paramètres de publication, puis cliquez sur **Publier maintenant**.  
  
     La solution publie le manifeste d'application signé, le manifeste de déploiement signé et les fichiers spécifiques à la version à l'emplacement du dossier de publication. Le programme d'installation non signé n'est pas remplacé par le processus de publication.  
  
11. Sur le site du client, ouvrez une invite de commandes.  
  
12. Accédez au répertoire qui contient le fichier .exe.  
  
13. Signez le fichier .exe à l'aide de la commande suivante :  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Par exemple, pour signer le programme d'installation, utilisez l'une des commandes suivantes :  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour re-signer des manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
