---
title: Configuration de sessions de performance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c479a2c62d40b52c085f56b424cf3151e93f487c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54774694"
---
# <a name="configuring-performance-sessions"></a>Configuration de sessions de performance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permettent de collecter une grande variété de données de performances pour de nombreux types d’applications. Cette section vous montre comment utiliser l’Assistant Performance et les propriétés de la session de performance et du fichier binaire cible pour configurer les outils de profilage de manière à collecter les données qui vous intéressent. Vous pouvez aussi utiliser les propriétés de configuration des outils de profilage pour contrôler la quantité de données collectées dans une exécution de profilage. Pour plus d’informations, consultez [Contrôle de la collecte de données](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
>  Dans de nombreux cas, l’utilisation des propriétés par défaut de l’Assistant Performance permet de collecter les données de profilage de manière efficace. Pour plus d’informations, consultez [Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md) et [Bien démarrer avec les outils d’analyse des performances](../profiling/getting-started-with-performance-tools.md).  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Définir les options de profilage de base** : vous devez configurer [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] pour qu’il utilise le serveur de symboles Microsoft. De cette façon, vous êtes sûr d’avoir accès aux symboles, tels que les noms de fonctions et de paramètres, qui correspondent à la version actuelle de Windows et aux autres applications Microsoft. Vous pouvez également spécifier d’autres options générales avant le début d’une session de profilage, telles que des autorisations système pour les outils de profilage et les noms des fichiers de données de profilage.|-   [Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Guide pratique pour sérialiser les informations de symboles](../profiling/how-to-serialize-symbol-information.md)<br />-   [Guide pratique pour définir la session active](../profiling/how-to-set-the-current-session.md)<br />-   [Guide pratique pour définir les autorisations](../profiling/how-to-set-permissions.md)<br />-   [Guide pratique pour définir les options de nom de fichier de données de profilage](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Spécifier les données que vous voulez collecter** : les procédures que vous utilisez pour configurer une session de profilage varient selon le type d’application cible que vous voulez profiler et le type de données de performance à collecter.|-   [Guide pratique pour choisir une méthode de collecte](../profiling/how-to-choose-collection-methods.md)<br />-   [Collecte de statistiques de performance à l’aide de l’échantillonnage](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Collecte de données liées à l’allocation et à la durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Collecte de données de minutage détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Guide pratique pour profiler du code JavaScript dans des pages web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Collecte de données de concurrence de threads et de processus](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Collecte de données de performance supplémentaires](../profiling/collecting-additional-performance-data.md)|  
|**Définir des options de configuration avancée** : quand vous profilez des applications .NET Framework qui chargent plusieurs versions du common language runtime (CLR), vous pouvez spécifier la version à profiler. Lorsque vous avez plusieurs fichiers .exe dans une session de performance, vous pouvez définir l’ordre de démarrage des fichiers binaires.|-   [Guide pratique pour spécifier le runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Guide pratique pour spécifier le binaire à démarrer](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Contrôle de la collecte de données](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Explorateur de performances](../profiling/performance-explorer.md)
