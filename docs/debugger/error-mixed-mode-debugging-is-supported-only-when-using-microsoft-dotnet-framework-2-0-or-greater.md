---
title: 'Erreur : Le débogage en mode mixte est pris en charge seulement quand vous utilisez Microsoft .NET Framework 2.0 ou supérieur | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2fb4d0dfaeb944700757c9ceec222dbd62dab9dd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681151"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>Erreur : Le débogage en mode mixte est uniquement pris en charge lorsque vous utilisez Microsoft .NET Framework 2.0 ou version ultérieure
Pour déboguer du code natif et managé mixte, vous devez disposer de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version 2.0, 3.0, 3.5 ou 4. Le débogage en mode mixte avec les versions précédentes du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] n’est pas pris en charge.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Mettez le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] à niveau avec la version 2.0, 3.0, 3.5 ou 4.

## <a name="see-also"></a>Voir aussi
- [Remote Debugging](../debugger/remote-debugging.md)