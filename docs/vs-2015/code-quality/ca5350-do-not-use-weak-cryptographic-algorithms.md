---
title: 'CA5350 : N’utilisez pas les algorithmes de chiffrement faibles | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2997abd9a112b60e9ef692bfe87b740976007656
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951758"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350 : N’utilisez pas d’algorithmes de chiffrement faibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|Category|Microsoft.Cryptography|  
|Modification avec rupture|Sans rupture|  
  
> [!NOTE]
>  Cet avertissement a été mis à jour pour la dernière fois en novembre 2015.  
  
## <a name="cause"></a>Cause  
 Les algorithmes de chiffrement, tels que <xref:System.Security.Cryptography.TripleDES> , et les algorithmes de hachage, tels que <xref:System.Security.Cryptography.SHA1> et <xref:System.Security.Cryptography.RIPEMD160> , sont considérés comme faibles.  
  
 Ces algorithmes de chiffrement n’offrent pas autant de sécurité que leurs équivalents plus modernes. Les algorithmes de chiffrement et de hachage <xref:System.Security.Cryptography.SHA1> et <xref:System.Security.Cryptography.RIPEMD160> offrent moins de résistance aux collisions que les algorithmes de hachage plus modernes. L’algorithme de chiffrement <xref:System.Security.Cryptography.TripleDES> fournit moins de bits de sécurité que les algorithmes de chiffrement plus modernes.  
  
## <a name="rule-description"></a>Description de la règle  
 Des algorithmes de chiffrement et des fonctions de hachage faibles sont utilisés aujourd’hui pour plusieurs raisons, mais ils ne doivent pas servir à garantir la confidentialité des données qu’ils protègent.  
  
 La règle se déclenche et lève un avertissement quand elle trouve des algorithmes 3DES, SHA1 ou RIPEMD160 dans le code.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Utilisez des options de chiffrement plus fortes :  
  
-   Pour le chiffrement TripleDES, utilisez le chiffrement <xref:System.Security.Cryptography.Aes> .  
  
-   Pour les fonctions de hachage SHA1 et RIPEMD160, utilisez les fonctions de la famille [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) (par exemple, <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle quand le niveau de protection nécessaire pour les données ne nécessite pas une garantie de sécurité.  
  
## <a name="pseudo-code-example"></a>Exemple de pseudo-code  
 Au moment de l’écriture de cet article, l’exemple de pseudo-code suivant illustre le schéma détecté par cette règle.  
  
### <a name="sha-1-hashing-violation"></a>Violation de hachage SHA-1  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA1.Create();  
  
```  
  
### <a name="solution"></a>Solution  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA256.Create();  
  
```  
  
### <a name="ripemd160-br-br-hashing-violation"></a>RIPEMD160 <br /><br />Violation de hachage  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### <a name="solution"></a>Solution  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA256.Create();  
  
```  
  
### <a name="tripledes-encryption-violation"></a>Violation de chiffrement TripleDES  
  
```  
using System.Security.Cryptography;   
...    
using (TripleDES encAlg = TripleDES.Create())   
{   
  ...   
}  
```  
  
### <a name="solution"></a>Solution  
  
```  
using System.Security.Cryptography;   
...   
using (AesManaged encAlg = new AesManaged())   
{   
  ...   
}  
```