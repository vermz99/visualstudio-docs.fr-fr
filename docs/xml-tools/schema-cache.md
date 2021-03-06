---
title: Éditeur XML du Cache de schéma
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28f5a7ffe202e7e02b06e676501ab508ee1a4ab2
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525802"
---
# <a name="schema-cache"></a>Cache de schéma

L’éditeur XML fournit un cache de schéma dans le *%VSInstallDir%\xml\Schemas* directory. Le cache de schéma est global pour tous les utilisateurs sur votre ordinateur et inclut des schémas XML standard qui sont utilisés pour la validation de document XML et IntelliSense.

L’éditeur XML peut également rechercher des schémas situés dans la solution, des schémas spécifiés dans le **schémas** champ du document **propriétés** fenêtre et des schémas identifiés par le `xsi:schemaLocation` et `xsi:noNamespaceSchemaLocation`attributs.

Le tableau suivant décrit les schémas qui sont installés avec l’éditeur XML.

| Nom de fichier | Description |
|-| - |
| *catalog.xsd* | Schéma pour des fichiers catalogue de schémas de l'éditeur XML. Pour des informations sur les catalogues de schémas, voir ci-dessous. |
| *DotNetConfig.xsd* | Schéma pour les fichiers Web.Config, «<http://schemas.microsoft.com/.NETConfiguration/v2.0>». |
| *msbuild.xsd* | Schéma pour les fichiers make MSBuild, «<http://schemas.microsoft.com/developer/msbuild/2003>». |
| *msdata.xsd* | Schéma pour les annotations XSD ajoutées par la classe <xref:System.Data.DataSet>, « urn:schemas-microsoft-com:xml-msdata ». |
| *msxsl.xsd* | Schéma pour les extensions de bloc de script Microsoft XSLT, urn:schemas-microsoft-com:xslt. |
| *SnippetFormat.xsd* | Schéma pour les fichiers XML d'extrait de code. Pour obtenir des exemples, consultez *%VSInstallDir%\VC#\Expansions*. |
| *Soap1.1.xsd* | Schéma pour Simple Object Access Protocol (SOAP) 1.1, http://schemas.xmlsoap.org/soap/envelope/. |
| *Soap1.2.xsd* | Schéma pour Simple Object Access Protocol 1.2. |
| *SiteMapSchema.xsd* | Schéma pour le fichier XML de plan de site ASP.NET, «<http://schemas.microsoft.com/AspNet/SiteMap-File-1.0>». |
| *wsdl.xsd* | Schéma de langage de Description de Service Web, http://schemas.xmlsoap.org/wsdl/. |
| *xenc.xsd* | Schéma pour le chiffrement XML, http://www.w3.org/2000/09/xmldsig#. |
| *xhtml.xsd* | Schéma pour XHTML http://www.w3.org/1999/xhtml. |
| *xlink.xsd* | Schéma pour XLink1.0, http://www.w3.org/1999/xlink. |
| *xml.xsd* | Schéma décrivant les attributs XML : space et XML : lang, http://www.w3.org/XML/1998/namespace. |
| *xmlsig.xsd* | Schéma pour XML Digital Signatures, http://www.w3.org/2000/09/xmldsig#. |
| *xsdschema.xsd* | Schéma décrivant XSD lui-même, http://www.w3.org/2001/XMLSchema. |
| *xslt.xsd* | Schéma pour XML transforme, http://www.w3.org/1999/XSL/Transform. |

## <a name="update-schemas-in-the-cache"></a>Mettre à jour des schémas dans le cache

L'éditeur charge le répertoire de cache de schéma lors du chargement du package de l'éditeur XML et contrôle si des modifications ont été apportées pendant l'exécution. Si un schéma a été ajouté, il est automatiquement chargé dans un index en mémoire des schémas connus. Si un schéma a été supprimé, il est automatiquement effacé de l'index en mémoire. Si un schéma a été mise à jour, il invalide automatiquement le cache en mémoire de ce schéma.

> [!NOTE]
> Étant donné que le répertoire de cache de schéma est global sur votre ordinateur, n'y ajoutez que des schémas standard et utiles pour tous les projets Visual Studio susceptibles d'être créés sur votre ordinateur.

L'éditeur XML prend également en charge un nombre quelconque de fichiers catalogue de schémas dans le répertoire de cache de schéma. Les catalogues de schémas peuvent pointer vers d'autres emplacements de schémas que l'éditeur doit toujours reconnaître. Le *catalog.xsd* fichier définit le format du fichier catalogue et est inclus dans le répertoire de cache de schéma. Le *catalog.xml* fichier est le catalogue par défaut et il contient des liens vers d’autres schémas dans le *VSInstallDir%*. Voici un échantillonnage de la *catalog.xml* fichier :

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%VSInstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

L’attribut `href` peut être n’importe quel chemin de fichier ou URL http pointant vers le schéma. Le chemin de fichier peut être relatif au document de catalogue. Les variables suivantes, délimitées par %%, sont reconnues par l’éditeur et développées dans le chemin d’accès :

- VSInstallDir

- Système

- ProgramFiles

- Programs

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- LCID

Le document de catalogue peut contenir un élément `Catalog` pointant vers d'autres catalogues. Vous pouvez utiliser l'élément `Catalog` pour pointer vers un catalogue central partagé par votre équipe ou votre entreprise ou vers un catalogue en ligne partagé avec vos partenaires commerciaux. L'attribut `href` est le chemin de fichier ou l'URL http des autres catalogues. Voici un exemple d'élément `Catalog` :

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

Le catalogue peut également contrôler la façon dont les schémas sont associés aux documents XML à l'aide de l'élément spécial `Association`. Cet élément associe des schémas qui n’ont aucun espace de noms cible avec une extension de fichier particulier, ce qui peut être utile car l’éditeur XML n’effectue aucune association automatique de schémas qui n’ont pas un `targetNamespace` attribut. Dans l'exemple suivant, l'élément `Association` associe le schéma dotNetConfig à tous les fichiers dont l'extension est « config » :

```xml
<Association extension="config" schema="%VSInstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Schémas localisés

Dans de nombreux cas le *catalog.xml* fichier ne contient pas d’entrées pour les schémas localisés. Vous pouvez ajouter des entrées supplémentaires pour le *catalog.xml* fichier qui pointent vers le répertoire de schémas localisés.

Dans l'exemple suivant, un nouvel élément `Schema` a été créé et il utilise la variable %LCID% pour pointer vers le schéma localisé.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>Modifier l’emplacement du cache de schéma

Vous pouvez personnaliser l’emplacement du cache de schéma à l’aide du **divers** page d’options. Si vous avez un répertoire de schémas favoris, l'éditeur peut être configuré pour utiliser ces schémas au lieu de ceux par défaut.

> [!NOTE]
> Ce changement n'affecte que l'utilisateur actuel de Visual Studio.

### <a name="to-change-the-schema-cache-location"></a>Pour modifier l'emplacement du cache de schéma

1. À partir de la **outils** menu, sélectionnez **Options**.

2. Développez **éditeur de texte**, développez **XML**, puis cliquez sur **divers**.

3. Cliquez sur le **Parcourir** bouton sur le **schémas** champ.

4. Sélectionnez le dossier du cache de schéma et cliquez sur **OK**.

### <a name="to-add-another-directory-of-common-schemas"></a>Pour ajouter un autre répertoire de schémas courants

1. Modifier le *catalog.xml* fichier dans le répertoire de cache de schéma de l’éditeur XML.

2. Ajoutez-y un nouvel élément `<Catalog href="..."/>` pointant vers le répertoire contenant les schémas supplémentaires.

3. Enregistrez les modifications apportées.

   Le catalogue est automatiquement rechargé.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)