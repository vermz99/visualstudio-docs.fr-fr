---
title: ProjectType, élément (modèles Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ac0c2b1e842dafded6e3a9bed2a9c2908ec30154
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508684"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType, élément (modèles Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [ProjectType, élément (modèles Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/projecttype-element-visual-studio-templates).  
  
Catégorie du modèle de projet pour qu’il apparaisse sous le groupe spécifié dans le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.  
  
> [!WARNING]
>  Modèles de projet sont pris en charge pour C++ à partir de Visual Studio 2012. Ils ne sont pas pris en charge pour C++ dans Visual Studio 2010 et versions antérieures.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectType >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Cette valeur spécifie le type de projet, le modèle créera et doit contenir l’une des valeurs suivantes :  
  
-   `CSharp`: Spécifie que le modèle crée un [!INCLUDE[csprcs](../includes/csprcs-md.md)] projet ou un élément.  
  
-   `VisualBasic`: Spécifie que le modèle crée un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projet ou un élément.  
  
-   `Web`: Spécifie que le modèle crée un projet Web ou un élément. Si le `ProjectType` élément contient cette valeur, le langage du projet ou de l’élément est défini dans le [ProjectSubType, élément (modèles Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Notes  
 `ProjectType` est un élément enfant obligatoire de `TemplateData`.  
  
 La valeur de la `ProjectType` élément spécifie où le modèle se trouve dans le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue. Par exemple, un modèle avec un `ProjectType` valeur `CSharp` apparaît sous le **Visual C#** nœud dans le **nouveau projet** boîte de dialogue.  
  
 Un sous-type de modèle peut être spécifié à l’aide de la [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) élément.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre les métadonnées d’un modèle de projet pour un [!INCLUDE[csprcs](../includes/csprcs-md.md)] application.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Élément ProjectSubType (modèles Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
