---
title: Créer un plug-in d’enregistreur pour les tests de performances web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e86f026ec4d4133635ba5cf9d6c37970abe6e139
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58415899"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Procédure : Créer un plug-in d’enregistreur

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> permet de modifier un test de performances web enregistré. La modification se produit une fois le bouton **Arrêter** sélectionné dans la barre d’outils de **l’Enregistreur de test de performances web**, mais avant l’enregistrement et la présentation du test dans l’éditeur de test de performances web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Un plug-in d’enregistreur vous permet d’effectuer votre propre corrélation personnalisée sur des paramètres dynamiques. Avec la fonctionnalité de corrélation intégrée, les tests de performances web détectent les paramètres dynamiques dans l’enregistrement web une fois l’opération terminée, ou quand l’option **Promouvoir les paramètres dynamiques en paramètres de test web** est utilisée dans la barre d’outils de **l’Éditeur de test de performances web**. Toutefois, la fonctionnalité de détection intégrée ne trouve pas toujours tous les paramètres dynamiques. Par exemple, il ne trouve pas d'ID de session, qui obtient généralement sa valeur modifiée entre 5 à 30 minutes. Par conséquent, vous devez exécuter le processus de corrélation manuellement.

Le <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> permet d'écrire le code de votre plug-in personnalisé. Ce plug-in peut effectuer une corrélation ou modifier le test de performances web de différentes manières avant qu’il soit enregistré et présenté dans l’éditeur de test de performances web. Par conséquent, si vous déterminez qu'une variable dynamique spécifique doit être mise en corrélation pour de nombreux enregistrements, vous pouvez automatiser le processus.

Vous pouvez également utiliser un plug-in d’enregistreur pour ajouter des règles d’extraction et de validation, ajouter des paramètres de contexte ou convertir les commentaires en transactions dans un test de performances web.

Les procédures suivantes décrivent le mode de création du code rudimentaire pour un plug-in d'enregistreur, déployez le plug-in et exécutez-le. L'exemple de code qui suit les procédures montre comment utiliser Visual C# pour créer un plug-in d'enregistreur de la corrélation avec des paramètres dynamiques personnalisés.

## <a name="create-a-recorder-plug-in"></a>Créer un plug-in d’enregistreur

### <a name="to-create-a-recorder-plug-in"></a>Pour créer un plug-in d'enregistreur

1.  Ouvrez une solution contenant le projet de test de performances web et de charge avec le test de performances web pour lequel vous souhaitez créer un plug-in d’enregistreur.

2.  Ajoutez ensuite un nouveau projet **Bibliothèque de classes** à la solution.

3.  Dans **l’Explorateur de solutions**, dans le dossier de projet de la nouvelle bibliothèque de classes, cliquez avec le bouton droit sur le dossier **Références**, puis sélectionnez **Ajouter une référence**.

    > [!TIP]
    > **RecorderPlugins** est un exemple de dossier de projet de nouvelle bibliothèque de classes.

     La boîte de dialogue **Ajouter une référence** s’affiche.

4.  Sélectionnez l’onglet **.NET**.

5.  Faites défiler la liste vers le bas et sélectionnez **Microsoft.VisualStudio.QualityTools.WebTestFramework**, puis choisissez **OK**.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** est ajouté dans le dossier **Références** dans **l’Explorateur de solutions**.

6. Écrivez le code de votre plug-in d'enregistreur. Commencez par créer une classe publique qui dérive de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>.

7. Remplacez la méthode <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> .

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Les arguments d’événement fournissent deux objets utilisables : le résultat enregistré et le test de performances web enregistré. Ils permettent d’itérer au sein du résultat pour trouver certaines valeurs, puis d’accéder à la même demande dans le test de performances web pour effectuer des modifications. Vous pouvez également modifier simplement le test de performances web pour ajouter un paramètre de contexte ou paramétrer certaines parties de l’URL.

    > [!NOTE]
    > Si vous modifiez le test de performances web, définissez également la propriété <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> sur True : `e.RecordedWebTestModified = true;`

8. Ajoutez d’autres lignes de code en fonction des opérations que le plug-in d’enregistreur devra exécuter à l’issue de l’enregistrement web. Par exemple, vous pouvez ajouter le code pour gérer la corrélation personnalisée comme l'illustre l'exemple ci-dessous. Il est également possible de créer un plug-in d’enregistreur pour notamment convertir les commentaires en transactions ou ajouter des règles de validation au test de performances web.

9. Dans le menu **Générer**, choisissez **Générer \<nom du projet de la bibliothèque de classes>**.

Ensuite, déployez le plug-in d’enregistreur pour l’inscrire auprès de Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Déployer le plug-in d’enregistreur

Après avoir compilé le plug-in d’enregistreur, placez la DLL ainsi créée dans un de ces deux emplacements :

- *%ProgramFiles(x86)%\Microsoft Visual Studio\\[version]\\[édition]\Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [version]\WebTestPlugins*

> [!WARNING]
> Après avoir copié le plug-in d'enregistreur dans l'un des deux emplacements, vous devez redémarrer Visual Studio pour enregistrer le plug-in d'enregistreur.

### <a name="execute-the-recorder-plug-in"></a>Exécuter le plug-in d’enregistreur

1.  Créez un test de performances web.

     La boîte de dialogue **Activer WebTestRecordPlugins** s’affiche.

2.  Cochez la case du plug-in d’enregistreur et choisissez **OK**.

     À l’issue de l’enregistrement du test de performances web, le nouveau plug-in d’enregistreur sera exécuté.

    > [!WARNING]
    > Vous pouvez obtenir une erreur semblable au cas suivant lorsque vous exécutez un test de performances web ou un test de charge qui utilise votre plug-in :
    >
    > **Échec de la requête : Exception dans le \<plug-in> événement : Impossible de charger le fichier ou l’assembly '\<"Nom du plug-in".dll>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' ou l’une de ses dépendances. Le système ne parvient pas à localiser le fichier spécifié.**
    >
    > Cela se produit si vous effectuez des modifications du code dans l’un de vos plug-ins et si vous créez une autre version de la DLL **(Version=0.0.0.0)**. Toutefois, le plug-in fait toujours référence à la version du plug-in d’origine. Pour résoudre ce problème, procédez comme suit :
    >
    > 1. Dans le projet de test de performances web et de charge, un message d’avertissement s’affiche dans les références. Supprimez et rajoutez la référence à la DLL de votre plug-in.
    > 2. Supprimez le plug-in de votre test ou de l'emplacement approprié, puis rajoutez-le.

## <a name="example"></a>Exemple

Cet exemple montre comment créer un plug-in d’enregistreur pour le test de performances web personnalisé afin de réaliser une corrélation personnalisée des paramètres dynamiques.

> [!NOTE]
> Une liste complète de l'exemple de code se trouve à la fin de cette rubrique.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Effectue une itération au sein du résultat pour rechercher la première page avec ReportSession

Cette partie de l'exemple de code effectue une itération au sein de chaque objet enregistré et recherche le corps de la réponse de ReportSession.

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

### <a name="add-an-extraction-rule"></a>Ajouter une règle d'extraction

Maintenant qu'une réponse a été trouvée, vous devez ajouter une règle d'extraction. Cette partie de l’exemple de code crée la règle d’extraction à l’aide de la classe <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>, puis recherche la bonne demande dans le test de performances web pour y ajouter la règle d’extraction. Chaque objet résultant a une nouvelle propriété nommée DeclarativeWebTestItemId, qui est utilisée dans le code pour obtenir la bonne demande auprès du test de performances web.

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

### <a name="replace-query-string-parameters"></a>Remplacer les paramètres de chaîne de requête

Maintenant, le code recherche tous les paramètres de chaîne de requête dont le nom ReportSession et remplacez la valeur par {{SessionId}} comme indiqué dans cette partie de l'exemple de code :

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Générer et exécuter un test de performances web codé](../test/generate-and-run-a-coded-web-performance-test.md)