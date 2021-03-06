---
title: Prise en charge des éditions de Visual Studio pour Visualization and Modeling SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 41f89449ab412a53d779bfc3fb4cf9ac52ded239
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953720"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Prise en charge des éditions de Visual Studio pour la visualisation &amp; Modeling SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les éléments suivants sont des listes d’éditions de Visual Studio qui sont prises en charge avec [!INCLUDE[dsl](../includes/dsl-md.md)] dans les environnements de création et de déploiement. Pour plus d’informations sur ces éditions, consultez le Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [centre de développement](http://go.microsoft.com/fwlink/?LinkId=75628).

## <a name="authoring-edition"></a>Édition de création
 Pour définir un DSL, vous devez avoir installé les composants suivants :

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|SDK Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

## <a name="deployment-editions"></a>Éditions de déploiement
 [!INCLUDE[dsl](../includes/dsl-md.md)] prend en charge les configurations suivantes pour déployer les langages spécifiques à un domaine que vous créez :

-   Visual Studio Enterprise

-   Visual Studio Professional

-   Package redistribuable Visual Studio Shell (mode intégré) redistributable package

-   Package redistribuable Visual Studio Shell (mode isolé) package redistribuable

> [!NOTE]
>  Pour rendre un DSL puisse s’exécuter sur un produit Shell, vous devez définir le **pris en charge les éditions de Visual Studio** champ dans le manifeste d’Extension. Pour plus d’informations, consultez [Déploiement de solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Voir aussi
 [Glossaire des Outils Domain-Specific Language](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
