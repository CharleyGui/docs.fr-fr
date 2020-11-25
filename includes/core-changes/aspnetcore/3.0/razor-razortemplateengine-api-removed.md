---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032634"
---
### <a name="razor-razortemplateengine-api-removed"></a>Razor : l’API RazorTemplateEngine a été supprimée

L’API [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) a été supprimée et remplacée par <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> .

Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 25215](https://github.com/dotnet/aspnetcore/issues/25215).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Un moteur de modèle peut être créé et utilisé pour analyser et générer du code pour les fichiers Razor.

#### <a name="new-behavior"></a>Nouveau comportement

`RazorProjectEngine` peut être créé et fournir le même type d’informations que `RazorTemplateEngine` pour analyser et générer du code pour les fichiers Razor. `RazorProjectEngine` fournit également des niveaux de configuration supplémentaires.

#### <a name="reason-for-change"></a>Motif de modification

`RazorTemplateEngine` était trop étroitement couplée aux implémentations existantes. Ce couplage étroit a entraîné davantage de questions lorsque vous essayez de configurer correctement un pipeline d’analyse/génération Razor.

#### <a name="recommended-action"></a>Action recommandée

Utilisez `RazorProjectEngine` au lieu de `RazorTemplateEngine`. Voici quelques exemples.

##### <a name="create-and-configure-the-razorprojectengine"></a>Créer et configurer RazorProjectEngine

```csharp
RazorProjectEngine projectEngine =
    RazorProjectEngine.Create(RazorConfiguration.Default,
        RazorProjectFileSystem.Create(@"C:\source\repos\ConsoleApp4\ConsoleApp4"),
        builder =>
        {
            builder.ConfigureClass((document, classNode) =>
            {
                classNode.ClassName = "MyClassName";

                // Can also configure other aspects of the class here.
            });

            // More configuration can go here
        });
```

##### <a name="generate-code-for-a-razor-file"></a>Générer du code pour un fichier Razor

```csharp
RazorProjectItem item = projectEngine.FileSystem.GetItem(
    @"C:\source\repos\ConsoleApp4\ConsoleApp4\Example.cshtml",
    FileKinds.Legacy);
RazorCodeDocument output = projectEngine.Process(item);

// Things available
RazorSyntaxTree syntaxTree = output.GetSyntaxTree();
DocumentIntermediateNode intermediateDocument =
    output.GetDocumentIntermediateNode();
RazorCSharpDocument csharpDocument = output.GetCSharpDocument();
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [RazorTemplateEngineOptions](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->
