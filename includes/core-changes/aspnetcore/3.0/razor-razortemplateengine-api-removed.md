---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032634"
---
### <a name="razor-razortemplateengine-api-removed"></a><span data-ttu-id="cb13c-101">Razor : l’API RazorTemplateEngine a été supprimée</span><span class="sxs-lookup"><span data-stu-id="cb13c-101">Razor: RazorTemplateEngine API removed</span></span>

<span data-ttu-id="cb13c-102">L’API [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) a été supprimée et remplacée par <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> .</span><span class="sxs-lookup"><span data-stu-id="cb13c-102">The [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API was removed and replaced with <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>.</span></span>

<span data-ttu-id="cb13c-103">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 25215](https://github.com/dotnet/aspnetcore/issues/25215).</span><span class="sxs-lookup"><span data-stu-id="cb13c-103">For discussion, see GitHub issue [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cb13c-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="cb13c-104">Version introduced</span></span>

<span data-ttu-id="cb13c-105">3.0</span><span class="sxs-lookup"><span data-stu-id="cb13c-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cb13c-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="cb13c-106">Old behavior</span></span>

<span data-ttu-id="cb13c-107">Un moteur de modèle peut être créé et utilisé pour analyser et générer du code pour les fichiers Razor.</span><span class="sxs-lookup"><span data-stu-id="cb13c-107">A template engine can be created and used to parse and generate code for Razor files.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="cb13c-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="cb13c-108">New behavior</span></span>

<span data-ttu-id="cb13c-109">`RazorProjectEngine` peut être créé et fournir le même type d’informations que `RazorTemplateEngine` pour analyser et générer du code pour les fichiers Razor.</span><span class="sxs-lookup"><span data-stu-id="cb13c-109">`RazorProjectEngine` can be created and provided the same type of information as `RazorTemplateEngine` to parse and generate code for Razor files.</span></span> <span data-ttu-id="cb13c-110">`RazorProjectEngine` fournit également des niveaux de configuration supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="cb13c-110">`RazorProjectEngine` also provides extra levels of configuration.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cb13c-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="cb13c-111">Reason for change</span></span>

<span data-ttu-id="cb13c-112">`RazorTemplateEngine` était trop étroitement couplée aux implémentations existantes.</span><span class="sxs-lookup"><span data-stu-id="cb13c-112">`RazorTemplateEngine` was too tightly coupled to the existing implementations.</span></span> <span data-ttu-id="cb13c-113">Ce couplage étroit a entraîné davantage de questions lorsque vous essayez de configurer correctement un pipeline d’analyse/génération Razor.</span><span class="sxs-lookup"><span data-stu-id="cb13c-113">This tight coupling led to more questions when trying to properly configure a Razor parsing/generation pipeline.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cb13c-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="cb13c-114">Recommended action</span></span>

<span data-ttu-id="cb13c-115">Utilisez `RazorProjectEngine` au lieu de `RazorTemplateEngine`.</span><span class="sxs-lookup"><span data-stu-id="cb13c-115">Use `RazorProjectEngine` instead of `RazorTemplateEngine`.</span></span> <span data-ttu-id="cb13c-116">Voici quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="cb13c-116">Consider the following examples.</span></span>

##### <a name="create-and-configure-the-razorprojectengine"></a><span data-ttu-id="cb13c-117">Créer et configurer RazorProjectEngine</span><span class="sxs-lookup"><span data-stu-id="cb13c-117">Create and configure the RazorProjectEngine</span></span>

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

##### <a name="generate-code-for-a-razor-file"></a><span data-ttu-id="cb13c-118">Générer du code pour un fichier Razor</span><span class="sxs-lookup"><span data-stu-id="cb13c-118">Generate code for a Razor file</span></span>

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

#### <a name="category"></a><span data-ttu-id="cb13c-119">Category</span><span class="sxs-lookup"><span data-stu-id="cb13c-119">Category</span></span>

<span data-ttu-id="cb13c-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cb13c-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cb13c-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="cb13c-121">Affected APIs</span></span>

- [<span data-ttu-id="cb13c-122">RazorTemplateEngine</span><span class="sxs-lookup"><span data-stu-id="cb13c-122">RazorTemplateEngine</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [<span data-ttu-id="cb13c-123">RazorTemplateEngineOptions</span><span class="sxs-lookup"><span data-stu-id="cb13c-123">RazorTemplateEngineOptions</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->
