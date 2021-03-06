---
title: LC, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa9a210b61a1ba28d2dca2f81184b3d20a91ff7f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638699"
---
# <a name="lc-task"></a>LC (tâche)
Encapsule *LC.exe*, qui génère un fichier *.license* à partir d’un fichier *.licx*. Pour plus d’informations sur *LC.exe*, consultez [Lc.exe (License Compiler)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Paramètres
Le tableau ci-dessous décrit les paramètres de la tâche `LC`.

|Paramètre|Description|
|---------------|-----------------|
|`LicenseTarget`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le fichier exécutable pour lequel les fichiers *.licenses* sont générés.|
|`NoLogo`|Paramètre `Boolean` facultatif.<br /><br /> Supprime l'affichage de la bannière de démarrage Microsoft.|
|`OutputDirectory`|Paramètre `String` facultatif.<br /><br /> Spécifie le répertoire où placer les fichiers *.licenses* de sortie.|
|`OutputLicense`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le nom du fichier *.licenses*. Si vous ne spécifiez pas de nom, le nom du fichier *.licx* est utilisé et le fichier *.licenses* créé est placé dans le répertoire qui contient le fichier *.licx*.|
|`ReferencedAssemblies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les composants référencés à charger lors de la génération du fichier *.license*.|
|`SdkToolsPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin des outils du SDK, comme *resgen.exe*.|
|`Sources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les éléments contenant les composants sous licence à inclure dans le fichier *.licenses*. Pour plus d’informations, consultez la documentation pour l’indicateur `/complist` dans [Lc.exe (License Compiler)](/dotnet/framework/tools/lc-exe-license-compiler).|

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.ToolTask>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Exemple
L’exemple suivant utilise la tâche `LC` pour compiler des licences.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
<!-- Item declarations, etc -->

    <Target Name="CompileLicenses">
        <LC
            Sources="@(LicxFile)"
            LicenseTarget="$(TargetFileName)"
            OutputDirectory="$(IntermediateOutputPath)"
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">

            <Output
                TaskParameter="OutputLicenses"
                ItemName="CompiledLicenseFile"/>
        </LC>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi
- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
