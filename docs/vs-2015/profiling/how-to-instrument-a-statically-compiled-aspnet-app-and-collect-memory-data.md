---
title: Guide pratique pour instrumenter une application web ASP.NET compilée statiquement et collecter des données de mémoire en utilisant la ligne de commande du profileur | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c52406ed16e23d6b3e6b86d1bba67ef52bb22e4
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "47590503"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Comment : instrumenter une application Web ASP.NET compilée statiquement et collecter des données de mémoire en utilisant la ligne de commande du profileur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : instrumenter un statiquement compilé ASP.NET Web Application et collecter des données de mémoire en utilisant la ligne de commande de Profiler](https://docs.microsoft.com/visualstudio/profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line).  
  
Cette rubrique explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour instrumenter un composant web ou un site web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] précompilé, et pour collecter des données d’allocation de mémoire .NET, des données de durée de vie des objets et des données chronologiques détaillées.  
  
> [!NOTE]
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous-répertoire \Team Tools\Performance Tools du répertoire d’installation de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils de ligne de commande du profileur, vous devez ajouter le chemin d’accès des outils à la variable d’environnement PATH de la fenêtre d’invite de commandes ou l’ajouter à la commande elle-même. Pour plus d’informations, consultez [Spécification du chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Pour collecter des données d’un composant web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] avec la méthode d’instrumentation, vous utilisez l’outil [VSInstr.exe](../profiling/vsinstr.md) pour générer une version instrumentée du composant. Sur l’ordinateur qui héberge le composant, vous remplacez la version non instrumentée du composant par la version instrumentée. Vous utilisez ensuite l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d’environnement de profilage globales et redémarrer l’ordinateur hôte. Vous démarrez ensuite le profileur.  
  
 Quand le composant instrumenté est exécuté, les données chronologiques sont collectées automatiquement dans un fichier de données. Vous pouvez suspendre et reprendre la collecte des données pendant la session de profilage.  
  
 Pour mettre fin à une session de profilage, vous fermez le processus de travail [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] qui héberge le composant, puis vous arrêtez explicitement le profileur. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.  
  
## <a name="starting-to-profile"></a>Démarrage du profilage  
  
#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Pour instrumenter un composant web ASP.NET et démarrer le profilage  
  
1.  Utilisez l’outil **VSInstr** pour générer une version instrumentée de l’application cible. Si nécessaire, remplacez les fichiers binaires de l’application sur l’ordinateur hôte ASP.NET avec les fichiers binaires instrumentés.  
  
2.  Ouvrez une fenêtre d’invite de commandes  
  
3.  Initialisez les variables d’environnement du profilage .NET. Dans une fenêtre d’invite de commandes, tapez :  
  
     **VSPerfClrEnv /globaltracegc**  
  
     - ou -  
  
     **VSPerfClrEnv /globaltracegclife**  
  
    -   **/globaltracegc** collecte les données chronologiques et d’allocation de mémoire .NET.  
  
    -   **/globaltracegclife** collecte les données chronologiques, d’allocation de mémoire .NET. et de durée de vie des objets.  
  
4.  Redémarrez l'ordinateur.  
  
5.  Ouvrez une fenêtre d’invite de commandes.  
  
6.  Démarrez le profileur. Dans une fenêtre d’invite de commandes, tapez :  
  
     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  
  
    -   L’option [/start](../profiling/start.md)**:trace** initialise le profileur.  
  
    -   L’option [/output](../profiling/output.md)**:**`OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).  
  
     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:trace**.  
  
    > [!NOTE]
    >  Les options **/user** et **/crosssession** sont généralement nécessaires pour les applications ASP.NET.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Spécifie le nom de domaine et d’utilisateur facultatif du compte propriétaire du processus de travail ASP.NET. Cette option est obligatoire si le processus s’exécute sous un compte d’utilisateur différent de celui de l’utilisateur connecté. Le nom est répertorié dans la colonne Nom d’utilisateur sous l’onglet Processus du Gestionnaire des tâches de Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si l’application s’exécute dans une autre session. L’id de session est répertorié dans la colonne d’ID de Session sur le l’onglet processus du Gestionnaire des tâches Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl).|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Pour démarrer le profileur après avoir suspendu la collecte de données, ajoutez l’option **/globaloff** sur la ligne de commande **/start**. Utilisez **/globalon** pour reprendre le profilage.|  
  
7.  Ouvrez le site web qui contient le composant instrumenté.  
  
## <a name="controlling-data-collection"></a>Contrôle de la collection de données  
 Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier à l’aide des options de **VSPerfCmd.exe**. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.  
  
#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données  
  
-   Les paires d’options suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Démarre (**/threadon**) ou arrête (**/threadoff**) la collecte des données pour le thread spécifié par l’ID de thread (`TID`).|  
  
## <a name="ending-the-profiling-session"></a>Fin d’une session de profilage  
 Pour terminer une session de profilage, fermez l’application web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], puis utilisez la commande **IISReset** d’Internet Information Services (IIS) pour fermer le processus de travail [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Appelez l’option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermez le fichier de données de profilage. La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement du profilage. Vous devez redémarrer l’ordinateur pour que les nouveaux paramètres d’environnement soient appliqués.  
  
#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage  
  
1.  Fermez l’application web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2.  Fermez le processus de travail [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Type :  
  
     **IISReset /stop**  
  
3.  Fermez le profileur. Type :  
  
     **VSPerfCmd /shutdown**  
  
4.  (Facultatif). Effacez les variables d’environnement de profilage. Type :  
  
     **VSPerfCmd /globaloff**  
  
5.  Redémarrez l'ordinateur. Si nécessaire, redémarrez IIS. Type :  
  
     **IISReset /start**  
  
## <a name="see-also"></a>Voir aussi  
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)


