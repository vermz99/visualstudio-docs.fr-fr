---
title: Detach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c65f17d9c37cf885460be8a2c9c3560d12f64dd5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630338"
---
# <a name="detach"></a>Detach
L’option **Detach** de VSPerfCmd.exe déconnecte le profileur des processus spécifiés, ou de tous les processus si aucun processus n’est spécifié. Le profilage doit avoir été initialisé avec la méthode d’échantillonnage.

 Un profilage qui a été démarré avec l’option **Launch** ou **Attach** peut être déconnecté avec **Detach**. Le profileur peut être réattaché avec des commandes **Attach** ultérieures.

 **Detach** ne ferme pas le fichier de données de profilage. Utilisez l’option **Shutdown** pour arrêter le profilage et fermer le fichier de données.

> [!NOTE]
>  Si l’option **Start** a été spécifiée avec l’option **Crosssession**, les appels à **VSPerfCmd /Attach** ou **VSPerfCmd /Detach** doivent également spécifier **Crosssession**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Paramètres
 `PIDs|ProcessNames` `PID` - Identificateur système numérique d’un ou de plusieurs processus.

 `ProcessNames` : nom du processus. Si plusieurs instances du processus nommé sont en cours d’exécution, les résultats sont imprévisibles.

 Séparez les processus par des virgules.

 Si aucun processus n’est spécifié, le profileur est détaché de tous les processus profilés.

## <a name="valid-options"></a>Options valides
 Les options suivantes de **VSPerfCmd** peuvent être combinées avec l’option **Attach** sur une même ligne de commande.

 **Crosssession** Active le profilage d’applications dans d’autres sessions que l’ouverture de session. Obligatoire si l’option **Start** a été spécifiée avec l’option **Crosssession**.

## <a name="example"></a>Exemple
 Dans cet exemple, la commande **Detach** interrompt le profilage et la commande **Shutdown** ferme le fichier de données du profileur.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)