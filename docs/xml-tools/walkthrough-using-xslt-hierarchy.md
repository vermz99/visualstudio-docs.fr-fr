---
title: 'Procédure pas à pas : À l’aide de XSLT Hierarchy'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e7c7e93fa0ba58f7888212c48e28d21bd564ae7c
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526306"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>Procédure pas à pas : Utiliser XSLT hierarchy

L’outil XSLT Hierarchy simplifie de nombreuses tâches de développement XML. Une feuille de style XSLT utilise souvent des instructions `includes` et `imports`. La compilation démarre à partir de la feuille de style principale, mais lorsque vous constatez une erreur en compilant une feuille de style XSLT, l'erreur peut provenir d'une autre source que la feuille de style principale. La résolution de l'erreur ou la modification de la feuille de style peut nécessiter l'accès à des feuilles de style incluses ou importées. L'exécution pas à pas de la feuille de style dans le débogueur peut ouvrir des feuilles de style incluses et importées, et vous pouvez ajouter un point d'arrêt à un point dans une ou plusieurs des feuilles de style incluses.

L'outil XSLT Hierarchy peut aussi s'avérer utile pour placer des points d'arrêt sur les règles de modèle intégrées. Les règles de modèle sont des modèles spéciaux générés pour chaque mode de la feuille de style et appelés par `xsl:apply-templates` lorsqu'aucun autre modèle ne correspond au nœud. Pour implémenter le débogage dans les règles de modèle intégrées, le débogueur XSLT génère le fichier avec les règles dans le dossier temporaire et les compile avec la feuille de style principale. Si vous n'exécutez pas le code pas à pas à partir d'un `xsl:apply-template`, il peut être difficile de trouver les feuilles de style incluses dans la feuille de style principale ou de trouver et ouvrir la feuille de style avec les règles de modèle intégrées.

L'exemple dans cette rubrique illustre le débogage dans une feuille de style référencée.

## <a name="to-debug-in-a-referenced-style-sheet"></a>Pour déboguer dans une feuille de style référencée

1. Ouvrez un document XML dans Visual Studio. Cet exemple utilise le document suivant :

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

1. Ajoutez le code suivant *xslincludefile.xsl*:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3.  Ajoutez le code suivant *xslinclude.xsl* fichier :

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4.  Ajouter un point d’arrêt au niveau de l’instruction `<xsl:include href="xslincludefile.xsl" />`.

5.  Démarrez le débogage.

6.  Lorsque le débogueur s’arrête au niveau de l’instruction `<xsl:include href="xslincludefile.xsl" />`, appuyez sur la **pas à pas détaillé** bouton. Le débogage peut être poursuivi dans la feuille de style référencée. La hiérarchie est visible et le concepteur affiche le chemin d’accès correct.

## <a name="see-also"></a>Voir aussi

- [Générateur de profils XSLT](../xml-tools/xslt-profiler.md)