---
title: WinCounter | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9a8e381ed058c30dcbf1760f380cf065c1443cd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505107"
---
# <a name="wincounter"></a>WinCounter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [WinCounter](https://docs.microsoft.com/visualstudio/profiling/wincounter).  
  
L’option **WinCounter** spécifie un compteur de performances Windows ou d’application à collecter à des intervalles définis pendant l’exécution du profil. Les compteurs de performances Windows et d’application sont répertoriés en tant que marques dans le fichier de données de profilage. Vous pouvez spécifier plusieurs compteurs de performances à collecter dans des options distinctes.  
  
 Par défaut, les compteurs sont collectés toutes les 500 millisecondes. Utilisez l’option **AutoMark** pour spécifier un autre intervalle de collecte.  
  
 Une seule option **AutoMark** est utilisée. Si plusieurs options **AutoMark** sont spécifiées, seule la dernière est utilisée.  
  
 L’option **WinCounter** peut être utilisée seulement avec l’option **Start**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Path`  
 Compteur de performances Windows au format de chemin de compteur PDH.  
  
## <a name="required-options"></a>Options obligatoires  
 L’option **WinCounter** peut être utilisée seulement avec l’option **Start**.  
  
 **Start:** `Method`  
 L’option **Start** initialise le profileur avec la méthode de profilage spécifiée.  
  
## <a name="exclusive-options"></a>Options exclusives  
 L’option **AutoMark** peut être utilisée seulement avec l’option **WinCounter**.  
  
 **AutoMark:** `Milliseconds`  
 Spécifie le nombre de millisecondes écoulées entre les collectes des données du compteur de performances Windows.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, deux compteurs de performance Windows sont configurés être collectés à un intervalle de 1 000 millisecondes.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)


