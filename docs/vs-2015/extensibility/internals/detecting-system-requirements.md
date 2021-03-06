---
title: Detecting System Requirements | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cdc69441de852e16adc047465aeec30003fe5170
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953511"
---
# <a name="detecting-system-requirements"></a>Détection de la configuration système requise
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage ne peut pas fonctionner, sauf si Visual Studio est installé. Lorsque vous utilisez le programme d’installation de Microsoft Windows pour gérer l’installation de votre VSPackage, vous pouvez configurer le programme d’installation pour détecter si Visual Studio est installé. Vous pouvez également configurer pour vérifier le système pour d’autres exigences, par exemple, une version particulière de Windows ou une quantité spécifique de mémoire vive.  
  
## <a name="detecting-visual-studio-editions"></a>Détection des éditions de Visual Studio  
 Pour déterminer si une édition de Visual Studio est installée, vérifiez que la valeur de la clé de Registre d’installation est (REG_DWORD) 1 dans le dossier approprié, comme indiqué dans le tableau suivant. Notez qu’il existe une hiérarchie des éditions de Visual Studio :  
  
1. Entreprise  
  
2. Professional  
  
3. Communauté  
  
   Lorsqu’une édition « supérieure » est installée, les clés de Registre pour cette édition, ainsi que pour les éditions de « inférieures » sont ajoutés. Autrement dit, si l’édition Enterprise est installée, la clé d’installation est définie sur 1 pour l’entreprise, ainsi que pour les éditions Professional et Community. Par conséquent, vous devez ne vérifier que pour l’édition « le plus élevée », que vous avez besoin.  
  
> [!NOTE]
>  Dans la version 64 bits de l’Éditeur du Registre, les clés de 32 bits sont affichées sous HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. Les clés de Visual Studio sont sous HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Produit|Touche|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (intégré et isolé)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Détecter quand Visual Studio est en cours d’exécution  
 Votre package Visual Studio ne peut pas être inscrit correctement si Visual Studio est en cours d’exécution lorsque le VSPackage est installé. Le programme d’installation doit détecter lorsque Visual Studio est en cours d’exécution et refuser puis à installer le programme. Programme d’installation de Windows ne vous permettent d’utiliser les entrées de table pour activer la détection de ce type. Au lieu de cela, vous devez créer une action personnalisée, comme suit : Utilisez le `EnumProcesses` fonction permettant de détecter le processus devenv.exe et définissez une propriété du programme d’installation qui est utilisée dans une condition de lancement ou de manière conditionnelle soit afficher une boîte de dialogue qui invite l’utilisateur à fermer Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
