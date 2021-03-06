---
title: Implémentation d’un langage hérité1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88db1e11286c022552419fa70bb6847d36035c36
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602856"
---
# <a name="implementing-a-legacy-language-service"></a>Implémentation d’un Service de langage hérité
Vous pouvez utiliser les classes dans l’infrastructure de package managé (MPF) pour implémenter un service de langage hérité qui prend en charge un large éventail de fonctionnalités, telles que la coloration syntaxique, la correspondance d’accolade et la saisie semi-automatique IntelliSense.

 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
>  Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="in-this-section"></a>Dans cette section
- [Présentation du service de langage hérité](../../extensibility/internals/legacy-language-service-overview.md)

 Vue d’ensemble des fonctionnalités de service de langage qui sont pris en charge dans MPF.

- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Décrit ce qui est nécessaire pour implémenter un service de langage à l’aide du MPF.

- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Décrit les étapes qui sont requises pour l’inscription à un service de langage MPF [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Scanneur et analyseur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Décrit les deux analyseurs qui sont requises pour implémenter toutes les fonctionnalités d’un service de langage à l’aide du MPF.

- [Procédure pas à pas : Création d’un Service de langage hérité](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Fournit les étapes de base qui sont requises pour implémenter un service de langage MPF dans un VSPackage.

- [Procédure pas à pas : Obtention d’une liste d’extraits de Code installés (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Illustre les techniques de récupération d’une liste d’extraits de code installé.

- [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)

 Fournit des liens vers des rubriques détaillant ce qui doit être fait pour implémenter toutes les fonctionnalités d’un service de langage à l’aide du MPF.