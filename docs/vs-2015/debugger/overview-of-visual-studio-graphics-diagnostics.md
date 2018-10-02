---
title: Vue d’ensemble de Visual Studio Graphics Diagnostics | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddd429d9-ac70-4ac4-9e69-299c6ea2df09
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2321e590591d6c3d80b41c58147820cf0248f403
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495754"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Vue d’ensemble de Visual Studio Graphics Diagnostics
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue d’ensemble de Visual Studio Graphics Diagnostics](https://docs.microsoft.com/visualstudio/debugger/graphics/overview-of-visual-studio-graphics-diagnostics).  
  
Visual Studio *Graphics Diagnostics* est un ensemble d’outils pour l’enregistrement, puis en analysant les problèmes de rendu et de performances dans les applications Direct3D. Graphics Diagnostics peut être utilisé sur les applications qui s’exécutent localement sur votre PC Windows, dans un émulateur d’appareil Windows, ou sur un PC ou un appareil distant.  
  
## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>Utilisation de Graphics Diagnostics pour déboguer les problèmes de rendu  
 Le débogage des problèmes de rendu dans une application riche en graphiques n'est pas aussi simple que de démarrer dans un débogueur et d'exécuter du code pas-à-pas. Dans chaque frame, des centaines de milliers de pixels uniques sont produits (chacun dépend d'un jeu complexe d'état, de données, de paramètres, et de code), il est possible que seuls quelques pixels présentent le problème que vous essayez de diagnostiquer. Pour compliquer encore plus les choses, le code qui génère chaque pixel est exécuté sur du matériel spécialisé qui traite des centaines de pixels en parallèle. Les outils et les techniques de débogage classiques (qui sont difficiles à exploiter même dans du code de thread léger) sont inefficaces face à autant de données.  
  
 Les outils Graphics Diagnostics de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sont conçus pour vous aider à identifier les problèmes de rendu en commençant par les artefacts visuels qui indiquent le problème, puis en remontant à la source du problème en se concentrant uniquement sur le code de nuanceur associé, les étapes de canalisation, les appels de dessin, les ressources et l'état du périphérique dans le code source de l'application.  
  
## <a name="directx-version-compatibility"></a>Compatibilité des versions DirectX  
 Graphics Diagnostics prend en charge les applications qui utilisent Direct3D 12, Direct3D 11 et Direct3D 10. Par ailleurs, il fournit une prise en charge limitée des applications qui utilisent Direct2D. Il ne prend pas en charge les applications qui utilisent des versions antérieures de Direct3D, DirectDraw ou d'autres API graphiques.  
  
### <a name="windows-10-and-direct3d-12"></a>Windows 10 et Direct3D 12  
 Windows 10 intègre la prochaine version de Direct3D, *Direct3D 12*, ce qui diffère sensiblement de Direct3D 10 et Direct3D 11. Ces différences permettent à DirectX d'être en phase avec le matériel graphique moderne et d'exploiter tout son potentiel. En outre, elles apportent également d'importants changements en matière d'API et octroient une plus grande responsabilité au programmeur qui doit gérer les problèmes de contention et de durée de vie des ressources. Il est crucial de pouvoir doter les programmeurs d'outils de débogage sophistiqués pour leur permettre d'effectuer cette transition. Ainsi, dans Visual Studio 2015, Graphics Diagnostics prend directement en charge Direct3D 12. Malgré les différences, Graphics Diagnostics avec Direct3D 12 assure la parité des fonctionnalités par rapport à Graphics Diagnostics et Direct3D 11.2, à l'exception pour l'instant de la fonctionnalité d'analyse des frames. Bientôt, la prise en charge de l'analyse des frames dans Direct3D 12 sera ajoutée, ainsi que de nouveaux outils de diagnostic qui vous aideront à résoudre de nouveaux genres de bogues dans Direct3D 12.  
  
 Windows 10 assure également la prise en charge des versions précédentes de Direct3D, ainsi que des jeux et applications qui reposent sur ces dernières. Graphics Diagnostics dans Visual Studio 2015 continue à prendre en charge Direct3D 10 et Direct3D 11 sur Windows 10, ainsi que sur Windows 8.1.  
  
### <a name="windows-81-and-direct3d-112"></a>Windows 8.1 et Direct3D 11.2  
 Dans [!INCLUDE[win81](../includes/win81-md.md)], DirectX 11.2 inaugure de nouvelles fonctionnalités qui prennent en charge la capture d'informations graphiques pendant toute son exécution. [!INCLUDE[win81](../includes/win81-md.md)] utilise la nouvelle capture basée sur le runtime, connu sous le nom *capture robuste*— exclusivement pour toutes les versions de DirectX qui [!INCLUDE[win81](../includes/win81-md.md)] prend en charge. La capture robuste prend aussi en charge les nouvelles fonctionnalités de Direct3D 11.2.  
  
### <a name="limited-direct2d-support"></a>Prise en charge limitée de Direct2D  
 Étant donné que Direct2D est une API en mode utilisateur générée d'après Direct3D, vous pouvez utiliser Graphics Diagnostics pour déboguer les problèmes de rendu dans les applications qui utilisent Direct2D. Toutefois, étant donné que seuls les événements de Direct3D sous-jacents sont stockés à la place des événements de niveau supérieur de Direct2D, les événements de Direct2D n'apparaîtront pas dans la liste des événements graphiques. En outre, comme les relations entre les événements de Direct2D et les événements de Direct3D qui en résultent ne sont pas toujours claires, le fait d'utiliser Graphics Diagnostics pour déboguer les problèmes de rendu dans des applications qui utilisent Direct2D n'est pas simple. Vous pouvez toujours utiliser Graphics Diagnostics pour obtenir des informations sur les problèmes de bas niveau de rendu dans les applications qui utilisent Direct2D.  
  
## <a name="graphics-diagnostics-features-in-visual-studio"></a>Fonctionnalités Graphics Diagnostics dans Visual Studio  
 Graphics Diagnostics possède une interface dédiée, la fenêtre Graphics Analyzer, pour diagnostiquer les problèmes de rendu. Toutefois, il ajoute également certains outils à l'interface de Visual Studio.  
  
### <a name="the-graphics-toolbar-visual-studio"></a>Barre d'outils Graphics (Visual Studio)  
 La barre d’outils Graphics fournit un accès rapide aux commandes Graphics Diagnostics.  
  
 Le **démarrer les Diagnostics** bouton exécute l’application dans Graphics Diagnostics. Lorsqu’une application s’exécute dans Graphics Diagnostics, le **capturer le frame rendu suivant** bouton est activé.  
  
### <a name="diagnostics-capture-interface"></a>Interface de capture de Diagnostics  
 Quand vous exécutez votre application dans Graphics Diagnostics, Visual Studio affiche une interface de session de diagnostic que vous pouvez utiliser pour capturer des frames, et qui affiche également la charge actuelle de l'UC et du GPU. La charge de l'UC et du GPU s'affiche pour vous aider à identifier les frames que vous souhaitez peut-être capturer en raison de leurs caractéristiques de performances, plutôt que les erreurs de rendu.  
  
 Toutefois, ce n'est pas le seul moyen de capturer des frames. Vous pouvez également capturer des frames à l'aide de l'interface de capture par programmation, ou à l'aide du programme de capture en ligne de commande, dxcap.exe.  
  
 Consultez [capture les informations graphiques](../debugger/capturing-graphics-information.md) pour plus d’informations.  
  
### <a name="gpu-usage"></a>Utilisation du GPU  
 Graphics Diagnostics peut également profiler les performances de votre application Direct3D. Comme le profilage des données est altéré par l'enregistrement des détails relatifs aux événements graphiques, cette opération est distincte de la capture de frame à examiner à l'aide de Graphics Analyzer.  
  
 Consultez [utilisation du GPU](../debugger/gpu-usage.md) pour plus d’informations.  
  
### <a name="directx-control-panel"></a>Panneau de configuration DirectX  
 Le panneau de configuration DirectX est un composant DirectX que vous pouvez utiliser pour modifier la manière dont DirectX se comporte (par exemple, vous pouvez activer la version de débogage des composants d'exécution DirectX, sélectionner le type de messages de débogage qui sont stockés, et désactiver certaines fonctionnalités du matériel graphique utilisées pour émuler le matériel ayant des capacités moindres). Ce niveau de contrôle sur DirectX peut vous aider à déboguer et à tester votre application DirectX. Vous pouvez accéder au panneau de configuration DirectX à partir de Visual Studio.  
  
##### <a name="to-open-the-directx-control-panel"></a>Pour ouvrir le panneau de configuration DirectX  
  
-   Dans la barre de menus, choisissez **déboguer**, **Graphics**, **le panneau de configuration DirectX**.  
  
## <a name="graphics-analyzer"></a>Graphics Analyzer  
 Visual Studio Graphics Analyzer est une interface dédiée pour l'examen des problèmes de rendu et de performances dans les frames que vous avez capturés. Dans Graphics Analyzer, vous trouverez plusieurs outils qui vous aideront à explorer et comprendre le comportement de rendu de votre application. Chaque outil expose des informations d'un genre distinct concernant le frame inspecté. Par ailleurs, les outils sont conçus pour être utilisés conjointement afin d'identifier intuitivement la source d'un problème de rendu, à partir du moment où il est apparu dans le tampon de trame.  
  
 Cette illustration montre une disposition typique des outils dans Graphics Analyzer.  
  
 ![Tous les graphiques du débogueur windows](../debugger/media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")  
  
### <a name="the-graphics-toolbar-graphics-analyzer"></a>Barre d'outils Graphics (Graphics Analyzer)  
 La barre d'outils Graphics fournit un accès rapide aux fenêtres d'outils Graphics Analyzer.  
  
 ![La barre d’outils Graphics en mode de diagnostics graphiques](../debugger/media/vsg-toolbar.png "vsg_toolbar")  
  
### <a name="graphics-log-document"></a>Document journal de graphisme  
 Dans Graphics Analyzer, le document journal de graphisme est la fenêtre d'outil la plus importante. Cette fenêtre représente tous les frames capturés durant l'exécution de votre application dans Graphics Diagnostics. À ce stade, vous pouvez sélectionner un autre frame pour examiner ou choisir un pixel spécifique à analyser avec l'outil Historique des pixels. L'image de tampon de trame affichée dans ce document change pour refléter l'événement actuellement sélectionné, ce qui vous permet de voir la façon dont le tampon de trame est affecté au fil du temps.  
  
 Le [Document journal de graphisme](../debugger/graphics-log-document.md) est également le point d’entrée pour l’outil d’analyse des frames, ce qui vous aide à comprendre les performances d’un cadre en modifiant la façon dont certains aspects du rendu sont configurés et en fournissant des résultats de benchmark à comparer avec la version d’origine.  
  
### <a name="event-list"></a>Liste des événements  
 Les événements graphiques marquent chaque appel d'API Direct3D et chaque événement défini par l'utilisateur.  
  
 Le [liste des événements](../debugger/graphics-event-list.md) montre tous les événements graphiques enregistrés durant le frame que vous examinez. Pour identifier plus facilement ce qui est important, vous pouvez visualiser la liste des événements hiérarchiquement, en fonction des dernières modifications d'état relatives à l'appel de dessin, ou sous forme de chronologie. En outre, les événements sont des événements à code de couleurs selon la file d'attente à laquelle ils appartiennent. Vous pouvez filtrer la liste pour inclure uniquement les événements qui vous intéressent.  
  
 Quand vous sélectionnez un événement dans la liste, le reste des outils Graphics Analysis reflètent l'état du frame au moment de l'événement. De cette façon, vous pouvez voir l'effet d'un événement sur le GPU. Par exemple, vous pouvez voir l'effet immédiat d'un appel de dessin sur le tampon de trame, même s'il est masqué par d'autres appels de dessin. Certains événements ont également des liens hypertexte que vous pouvez suivre pour plus d'informations sur leurs paramètres ou les objets de ressource associés.  
  
### <a name="pipeline-stages"></a>Étapes de canalisation  
 Chaque appel de dessin dans votre application passe par la canalisation graphique fournie par Direct3D. À chaque étape de canalisation, la sortie de l'étape précédente est transformée par un petit programme appelé nuanceur. Elle est ensuite transmise à l'étape suivante, jusqu'à son rendu final à l'écran. De nombreuses erreurs de rendu se produisent à la frontière entre les étapes de canalisation quand le format de sortie est différent de ce qui est attendu à l'étape suivante, ou quand une étape produit simplement des résultats incorrects. Normalement, vous obtenez uniquement le résultat final visible sur votre écran. Vous ne pouvez pas distinguer facilement où l'erreur est survenue durant la canalisation.  
  
 Le [canalisation](../debugger/graphics-pipeline-stages.md) fenêtre visualise le résultat de chaque étape indépendamment, afin que vous pouvez déterminer plus facilement l’étape à laquelle un problème de rendu apparaît en premier. Une fois que vous avez identifié l'étape, vous pouvez démarrer le débogage de son nuanceur directement à partir de la fenêtre Étapes de canalisation.  
  
### <a name="graphics-state"></a>État graphique  
 Les opérations de rendu dépendent beaucoup de l'état de plusieurs objets. Des problèmes de rendu de toutes sortes sont provoqués par un état mal configuré.  
  
 Le [état](../debugger/graphics-state.md) fenêtre collecte les informations d’état relatives à chaque appel de dessin au même endroit, afin qu’il est plus facile à trouver, et également mises en surbrillance les modifications d’état qui se sont produites depuis le dernier appel de dessin.  
  
### <a name="pixel-history"></a>Historique des pixels  
 Dans les scènes complexes, il n'est pas rare qu'un pixel soit ombré plusieurs fois dans un seul frame. La couleur précédente est parfois simplement remplacée, mais il arrive également que les couleurs soient combinées pour obtenir des effets tels que la transparence. Quand le résultat de la combinaison n'a pas l'apparence souhaitée, vous ne pouvez pas déterminer facilement si cela est dû au fait qu'une des couleurs est incorrecte, ou s'il s'agit d'un problème de combinaison. Parfois, un objet peut être absent, car sa contribution au pixel a été rejetée pour une raison quelconque.  
  
 Le [historique des pixels](../debugger/graphics-pixel-history.md) fenêtre permet de visualiser l’historique complet du nuanceur de chaque pixel de l’image, y compris les contributions rejetées. Pour les contributions qui n'ont pas été rejetées, elle affiche les résultats bruts du nuanceur et montre comment chaque nouvelle couleur a été combinée à la précédente. Avec ces informations, il est beaucoup plus facile de localiser la source des erreurs dans les pixels qui fusionnent les résultats du nuanceur, ou quand un objet rendu est manquant, car sa contribution au pixel a été rejetée de façon incorrecte.  
  
### <a name="event-call-stack"></a>Pile des appels des événements  
 Le code du nuanceur n'est pas la seule source des problèmes de rendu dans une application Direct3D. Parfois, le code source de votre application passe un paramètre incorrect ou ne configure pas correctement Direct3D. Il existe un type d'erreur que la fonctionnalité décrite précédemment, Historique des pixels, peut vous aider à identifier. Il s'agit de l'erreur liée à l'absence d'un objet rendu, en raison du rejet de tous ses pixels. Ce genre d'erreur se produit généralement quand vous avez configuré un paramètre de manière incorrecte, par exemple le paramètre qui contrôle la façon dont le test de profondeur est effectué. En principe, vous trouverez votre erreur quelque part dans la pile des appels de l'appel de dessin de l'objet manquant.  
  
 Le [pile des appels des événements](../debugger/graphics-event-call-stack.md) fenêtre affiche la pile des appels complète de chaque événement graphique dans la liste des événements, et permet même d’atteindre de votre application du code source si les informations de débogage sont disponibles. Il s'agit d'un outil puissant qui vous permet de suivre une erreur depuis sa première apparition, dans le GPU, jusqu'à son origine dans le code source de votre application.  
  
### <a name="object-table"></a>Table des objets  
 Chaque frame rendu par votre application s'appuie probablement sur des centaines, voire des milliers d'objets de ressource. Cela peut inclure les mémoires tampons d’arrière-plan, les cibles de rendu, les textures, les mémoires tampons de vertex, les mémoires tampons d’index, les mémoires tampons générales, quasiment tout ce dont Direct3D se souvient en tant qu’objet.  
  
 Le [Table des objets](../debugger/graphics-object-table.md) affiche tous les objets qui existent au moment de l’événement graphique sélectionné dans la liste des événements. Dans la mesure où la plupart des objets d'une application classique sont des textures, la liste des événements est optimisée pour montrer rapidement les détails pertinents relatifs aux images. La colonne Type vous indique le type d'objet présent dans chaque ligne, alors que la colonne Format indique le sous-type ou la version de l'objet. D'autres informations sont également affichées. Certains objets possèdent également des liens hypertexte que vous pouvez suivre pour afficher l'objet avec une visionneuse plus spécialisée. C'est le cas, par exemple, pour les textures (vous pouvez afficher la texture en tant qu'image) ou les mémoires tampons (vous pouvez choisir la façon dont la visionneuse de mémoire tampon analyse et affiche les octets bruts de mémoire tampon en définissant le format de la mémoire tampon).  
  
### <a name="frame-analysis"></a>Analyse des frames  
 Les graphiques de votre application ne doivent pas seulement être corrects, ils doivent également être rapides. Cela doit aussi se vérifier sur les appareils moins puissants, tels que les ordinateurs portables avec des cartes graphiques intégrées ou les téléphones mobiles. Enfin, les graphiques doivent être esthétiquement parfaits.  
  
 Le [analyse des frames](../debugger/graphics-frame-analysis.md) outil explore les optimisations de performances potentielles en changeant automatiquement la manière dont l’application utilise Direct3D et en fournissant des résultats de test d’évaluation pour la comparaison. Par exemple, l'analyse des frames peut activer le mappage MIP (ou MIP mapping) sur chaque texture, ce qui permet de révéler les textures susceptibles de tirer parti du mappage MIP mais pour lesquelles il n'est pas actuellement activé. Sur le matériel compatible, l'analyse des frames présente également des informations collectées à partir des compteurs de performances du GPU. Ce genre d'informations permet d'identifier les problèmes de performances au niveau du matériel, par exemple un nombre élevé de blocages d'extraction de texture ou de pertes dans le cache.  
  
 Toutefois, l'analyse des frames ne se réduit pas à une question de vitesse. Elle vise à atteindre les meilleures performances possibles avec un minimum de concessions sur la qualité visuelle. Parfois, un effet impressionnant sur un affichage de grande taille n'a pas le même impact sur le petit écran d'un téléphone, où un effet plus simple peut s'avérer tout aussi réussi sans épuiser la batterie. Les modifications automatiques et les benchmarks fournis par Graphics Analysis peuvent vous aider à trouver l'équilibre approprié pour votre application sur toute une gamme d'appareils.  
  
## <a name="see-also"></a>Voir aussi  
 [Outil de ligne de commande de Capture](../debugger/command-line-capture-tool.md)   
 [Débogueur HLSL](../debugger/hlsl-shader-debugger.md)


