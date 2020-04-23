---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
ms.date: 04/10/2020
ms.openlocfilehash: 1979f98a6005a414acc64c5eaa086a88aca9f033
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102825"
---
# <a name="dotnet-new"></a><span data-ttu-id="484b8-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="484b8-103">dotnet new</span></span>

<span data-ttu-id="484b8-104">**Cet article s’applique à:** ✔️ .NET Core 2.0 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="484b8-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="484b8-105">Nom</span><span class="sxs-lookup"><span data-stu-id="484b8-105">Name</span></span>

<span data-ttu-id="484b8-106">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="484b8-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="484b8-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="484b8-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="484b8-108">Description</span><span class="sxs-lookup"><span data-stu-id="484b8-108">Description</span></span>

<span data-ttu-id="484b8-109">La `dotnet new` commande crée un projet .NET Core ou d’autres artefacts basés sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="484b8-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="484b8-110">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="484b8-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="484b8-111">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="484b8-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="484b8-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="484b8-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="484b8-113">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="484b8-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="484b8-114">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="484b8-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="484b8-115">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="484b8-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="484b8-116">Vous pouvez `dotnet new --list` courir pour voir une liste de tous les modèles installés.</span><span class="sxs-lookup"><span data-stu-id="484b8-116">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="484b8-117">Si `TEMPLATE` la valeur n’est pas une correspondance exacte sur le texte dans les **Modèles** ou la colonne **Short Name** de la table retournée, un match de sous-corde est effectué sur ces deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="484b8-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="484b8-118">En commençant par .NET Core 3.0 SDK, le CLI recherche des `dotnet new` modèles dans NuGet.org lorsque vous invoquez la commande dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="484b8-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="484b8-119">Si le CLI ne peut pas trouver `dotnet new`un modèle de correspondance lors de l’invocation , même pas partielle.</span><span class="sxs-lookup"><span data-stu-id="484b8-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="484b8-120">S’il y a une nouvelle version du modèle disponible.</span><span class="sxs-lookup"><span data-stu-id="484b8-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="484b8-121">Dans ce cas, le projet ou l’artefact est créé, mais le CLI vous avertit d’une version mise à jour du modèle.</span><span class="sxs-lookup"><span data-stu-id="484b8-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="484b8-122">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="484b8-122">The command contains a default list of templates.</span></span> <span data-ttu-id="484b8-123">Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="484b8-123">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="484b8-124">Le tableau suivant montre les modèles qui viennent pré-installé avec le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="484b8-124">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="484b8-125">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="484b8-125">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="484b8-126">Cliquez sur le lien de nom court pour voir les options spécifiques de modèle.</span><span class="sxs-lookup"><span data-stu-id="484b8-126">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="484b8-127">Modèles</span><span class="sxs-lookup"><span data-stu-id="484b8-127">Templates</span></span>                                    | <span data-ttu-id="484b8-128">Nom court</span><span class="sxs-lookup"><span data-stu-id="484b8-128">Short name</span></span>                      | <span data-ttu-id="484b8-129">Langage</span><span class="sxs-lookup"><span data-stu-id="484b8-129">Language</span></span>     | <span data-ttu-id="484b8-130">Balises</span><span class="sxs-lookup"><span data-stu-id="484b8-130">Tags</span></span>                                  | <span data-ttu-id="484b8-131">Introduit</span><span class="sxs-lookup"><span data-stu-id="484b8-131">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="484b8-132">Application console</span><span class="sxs-lookup"><span data-stu-id="484b8-132">Console Application</span></span>                          | [<span data-ttu-id="484b8-133">console</span><span class="sxs-lookup"><span data-stu-id="484b8-133">console</span></span>](#console)             | <span data-ttu-id="484b8-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="484b8-134">[C#], F#, VB</span></span> | <span data-ttu-id="484b8-135">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="484b8-135">Common/Console</span></span>                        | <span data-ttu-id="484b8-136">1.0</span><span class="sxs-lookup"><span data-stu-id="484b8-136">1.0</span></span>        |
| <span data-ttu-id="484b8-137">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="484b8-137">Class library</span></span>                                | [<span data-ttu-id="484b8-138">classlib</span><span class="sxs-lookup"><span data-stu-id="484b8-138">classlib</span></span>](#classlib)           | <span data-ttu-id="484b8-139">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="484b8-139">[C#], F#, VB</span></span> | <span data-ttu-id="484b8-140">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="484b8-140">Common/Library</span></span>                        | <span data-ttu-id="484b8-141">1.0</span><span class="sxs-lookup"><span data-stu-id="484b8-141">1.0</span></span>        |
| <span data-ttu-id="484b8-142">Application WPF</span><span class="sxs-lookup"><span data-stu-id="484b8-142">WPF Application</span></span>                              | [<span data-ttu-id="484b8-143">Wpf</span><span class="sxs-lookup"><span data-stu-id="484b8-143">wpf</span></span>](#wpf)                     | <span data-ttu-id="484b8-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-144">[C#]</span></span>         | <span data-ttu-id="484b8-145">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="484b8-145">Common/WPF</span></span>                            | <span data-ttu-id="484b8-146">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-146">3.0</span></span>        |
| <span data-ttu-id="484b8-147">Bibliothèque de classe WPF</span><span class="sxs-lookup"><span data-stu-id="484b8-147">WPF Class library</span></span>                            | [<span data-ttu-id="484b8-148">wpflib (wpflib)</span><span class="sxs-lookup"><span data-stu-id="484b8-148">wpflib</span></span>](#wpf)                  | <span data-ttu-id="484b8-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-149">[C#]</span></span>         | <span data-ttu-id="484b8-150">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="484b8-150">Common/WPF</span></span>                            | <span data-ttu-id="484b8-151">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-151">3.0</span></span>        |
| <span data-ttu-id="484b8-152">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="484b8-152">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="484b8-153">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="484b8-153">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="484b8-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-154">[C#]</span></span>         | <span data-ttu-id="484b8-155">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="484b8-155">Common/WPF</span></span>                            | <span data-ttu-id="484b8-156">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-156">3.0</span></span>        |
| <span data-ttu-id="484b8-157">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="484b8-157">WPF User Control Library</span></span>                     | [<span data-ttu-id="484b8-158">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="484b8-158">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="484b8-159">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-159">[C#]</span></span>         | <span data-ttu-id="484b8-160">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="484b8-160">Common/WPF</span></span>                            | <span data-ttu-id="484b8-161">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-161">3.0</span></span>        |
| <span data-ttu-id="484b8-162">Application des formulaires Windows (WinForms)</span><span class="sxs-lookup"><span data-stu-id="484b8-162">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="484b8-163">Winforms</span><span class="sxs-lookup"><span data-stu-id="484b8-163">winforms</span></span>](#winforms)           | <span data-ttu-id="484b8-164">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-164">[C#]</span></span>         | <span data-ttu-id="484b8-165">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="484b8-165">Common/WinForms</span></span>                       | <span data-ttu-id="484b8-166">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-166">3.0</span></span>        |
| <span data-ttu-id="484b8-167">Bibliothèque de classe Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="484b8-167">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="484b8-168">winformslib</span><span class="sxs-lookup"><span data-stu-id="484b8-168">winformslib</span></span>](#winforms)        | <span data-ttu-id="484b8-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-169">[C#]</span></span>         | <span data-ttu-id="484b8-170">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="484b8-170">Common/WinForms</span></span>                       | <span data-ttu-id="484b8-171">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-171">3.0</span></span>        |
| <span data-ttu-id="484b8-172">Service aux travailleurs</span><span class="sxs-lookup"><span data-stu-id="484b8-172">Worker Service</span></span>                               | [<span data-ttu-id="484b8-173">Travailleur</span><span class="sxs-lookup"><span data-stu-id="484b8-173">worker</span></span>](#web-others)           | <span data-ttu-id="484b8-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-174">[C#]</span></span>         | <span data-ttu-id="484b8-175">Commun/Travailleur/Web</span><span class="sxs-lookup"><span data-stu-id="484b8-175">Common/Worker/Web</span></span>                     | <span data-ttu-id="484b8-176">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-176">3.0</span></span>        |
| <span data-ttu-id="484b8-177">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="484b8-177">Unit Test Project</span></span>                            | [<span data-ttu-id="484b8-178">mstest</span><span class="sxs-lookup"><span data-stu-id="484b8-178">mstest</span></span>](#test)                 | <span data-ttu-id="484b8-179">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="484b8-179">[C#], F#, VB</span></span> | <span data-ttu-id="484b8-180">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="484b8-180">Test/MSTest</span></span>                           | <span data-ttu-id="484b8-181">1.0</span><span class="sxs-lookup"><span data-stu-id="484b8-181">1.0</span></span>        |
| <span data-ttu-id="484b8-182">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="484b8-182">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="484b8-183">Nunit</span><span class="sxs-lookup"><span data-stu-id="484b8-183">nunit</span></span>](#nunit)                  | <span data-ttu-id="484b8-184">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="484b8-184">[C#], F#, VB</span></span> | <span data-ttu-id="484b8-185">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="484b8-185">Test/NUnit</span></span>                            | <span data-ttu-id="484b8-186">2.1.400</span><span class="sxs-lookup"><span data-stu-id="484b8-186">2.1.400</span></span>    |
| <span data-ttu-id="484b8-187">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="484b8-187">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="484b8-188">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="484b8-188">[C#], F#, VB</span></span> | <span data-ttu-id="484b8-189">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="484b8-189">Test/NUnit</span></span>                            | <span data-ttu-id="484b8-190">2.2</span><span class="sxs-lookup"><span data-stu-id="484b8-190">2.2</span></span>        |
| <span data-ttu-id="484b8-191">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="484b8-191">xUnit Test Project</span></span>                           | [<span data-ttu-id="484b8-192">xunit</span><span class="sxs-lookup"><span data-stu-id="484b8-192">xunit</span></span>](#test)                  | <span data-ttu-id="484b8-193">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="484b8-193">[C#], F#, VB</span></span> | <span data-ttu-id="484b8-194">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="484b8-194">Test/xUnit</span></span>                            | <span data-ttu-id="484b8-195">1.0</span><span class="sxs-lookup"><span data-stu-id="484b8-195">1.0</span></span>        |
| <span data-ttu-id="484b8-196">Composant de rasoir</span><span class="sxs-lookup"><span data-stu-id="484b8-196">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="484b8-197">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-197">[C#]</span></span>         | <span data-ttu-id="484b8-198">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="484b8-198">Web/ASP.NET</span></span>                           | <span data-ttu-id="484b8-199">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-199">3.0</span></span>        |
| <span data-ttu-id="484b8-200">Page Razor</span><span class="sxs-lookup"><span data-stu-id="484b8-200">Razor Page</span></span>                                   | [<span data-ttu-id="484b8-201">Page</span><span class="sxs-lookup"><span data-stu-id="484b8-201">page</span></span>](#page)                   | <span data-ttu-id="484b8-202">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-202">[C#]</span></span>         | <span data-ttu-id="484b8-203">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="484b8-203">Web/ASP.NET</span></span>                           | <span data-ttu-id="484b8-204">2.0</span><span class="sxs-lookup"><span data-stu-id="484b8-204">2.0</span></span>        |
| <span data-ttu-id="484b8-205">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="484b8-205">MVC ViewImports</span></span>                              | [<span data-ttu-id="484b8-206">viewimports</span><span class="sxs-lookup"><span data-stu-id="484b8-206">viewimports</span></span>](#namespace)       | <span data-ttu-id="484b8-207">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-207">[C#]</span></span>         | <span data-ttu-id="484b8-208">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="484b8-208">Web/ASP.NET</span></span>                           | <span data-ttu-id="484b8-209">2.0</span><span class="sxs-lookup"><span data-stu-id="484b8-209">2.0</span></span>        |
| <span data-ttu-id="484b8-210">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="484b8-210">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="484b8-211">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-211">[C#]</span></span>         | <span data-ttu-id="484b8-212">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="484b8-212">Web/ASP.NET</span></span>                           | <span data-ttu-id="484b8-213">2.0</span><span class="sxs-lookup"><span data-stu-id="484b8-213">2.0</span></span>        |
| <span data-ttu-id="484b8-214">Application Serveur Blazor</span><span class="sxs-lookup"><span data-stu-id="484b8-214">Blazor Server App</span></span>                            | [<span data-ttu-id="484b8-215">blazorserver</span><span class="sxs-lookup"><span data-stu-id="484b8-215">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="484b8-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-216">[C#]</span></span>         | <span data-ttu-id="484b8-217">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="484b8-217">Web/Blazor</span></span>                            | <span data-ttu-id="484b8-218">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-218">3.0</span></span>        |
| <span data-ttu-id="484b8-219">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="484b8-219">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="484b8-220">Web</span><span class="sxs-lookup"><span data-stu-id="484b8-220">web</span></span>](#web)                     | <span data-ttu-id="484b8-221">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="484b8-221">[C#], F#</span></span>     | <span data-ttu-id="484b8-222">Web/vides</span><span class="sxs-lookup"><span data-stu-id="484b8-222">Web/Empty</span></span>                             | <span data-ttu-id="484b8-223">1.0</span><span class="sxs-lookup"><span data-stu-id="484b8-223">1.0</span></span>        |
| <span data-ttu-id="484b8-224">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="484b8-224">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="484b8-225">Mvc</span><span class="sxs-lookup"><span data-stu-id="484b8-225">mvc</span></span>](#web-options)             | <span data-ttu-id="484b8-226">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="484b8-226">[C#], F#</span></span>     | <span data-ttu-id="484b8-227">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="484b8-227">Web/MVC</span></span>                               | <span data-ttu-id="484b8-228">1.0</span><span class="sxs-lookup"><span data-stu-id="484b8-228">1.0</span></span>        |
| <span data-ttu-id="484b8-229">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="484b8-229">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="484b8-230">webapp, rasoir</span><span class="sxs-lookup"><span data-stu-id="484b8-230">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="484b8-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-231">[C#]</span></span>         | <span data-ttu-id="484b8-232">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="484b8-232">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="484b8-233">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="484b8-233">2.2, 2.0</span></span>   |
| <span data-ttu-id="484b8-234">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="484b8-234">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="484b8-235">Angulaire</span><span class="sxs-lookup"><span data-stu-id="484b8-235">angular</span></span>](#spa)                 | <span data-ttu-id="484b8-236">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-236">[C#]</span></span>         | <span data-ttu-id="484b8-237">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="484b8-237">Web/MVC/SPA</span></span>                           | <span data-ttu-id="484b8-238">2.0</span><span class="sxs-lookup"><span data-stu-id="484b8-238">2.0</span></span>        |
| <span data-ttu-id="484b8-239">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="484b8-239">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="484b8-240">Réagir</span><span class="sxs-lookup"><span data-stu-id="484b8-240">react</span></span>](#spa)                   | <span data-ttu-id="484b8-241">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-241">[C#]</span></span>         | <span data-ttu-id="484b8-242">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="484b8-242">Web/MVC/SPA</span></span>                           | <span data-ttu-id="484b8-243">2.0</span><span class="sxs-lookup"><span data-stu-id="484b8-243">2.0</span></span>        |
| <span data-ttu-id="484b8-244">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="484b8-244">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="484b8-245">reactredux</span><span class="sxs-lookup"><span data-stu-id="484b8-245">reactredux</span></span>](#reactredux)       | <span data-ttu-id="484b8-246">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-246">[C#]</span></span>         | <span data-ttu-id="484b8-247">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="484b8-247">Web/MVC/SPA</span></span>                           | <span data-ttu-id="484b8-248">2.0</span><span class="sxs-lookup"><span data-stu-id="484b8-248">2.0</span></span>        |
| <span data-ttu-id="484b8-249">Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="484b8-249">Razor Class Library</span></span>                          | [<span data-ttu-id="484b8-250">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="484b8-250">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="484b8-251">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-251">[C#]</span></span>         | <span data-ttu-id="484b8-252">Web/Razor/Library/Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="484b8-252">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="484b8-253">2.1</span><span class="sxs-lookup"><span data-stu-id="484b8-253">2.1</span></span>        |
| <span data-ttu-id="484b8-254">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="484b8-254">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="484b8-255">webapi webapi</span><span class="sxs-lookup"><span data-stu-id="484b8-255">webapi</span></span>](#webapi)               | <span data-ttu-id="484b8-256">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="484b8-256">[C#], F#</span></span>     | <span data-ttu-id="484b8-257">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="484b8-257">Web/WebAPI</span></span>                            | <span data-ttu-id="484b8-258">1.0</span><span class="sxs-lookup"><span data-stu-id="484b8-258">1.0</span></span>        |
| <span data-ttu-id="484b8-259">ASP.NET Core gRPC Service</span><span class="sxs-lookup"><span data-stu-id="484b8-259">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="484b8-260">grpc grpc</span><span class="sxs-lookup"><span data-stu-id="484b8-260">grpc</span></span>](#web-others)             | <span data-ttu-id="484b8-261">[C#]</span><span class="sxs-lookup"><span data-stu-id="484b8-261">[C#]</span></span>         | <span data-ttu-id="484b8-262">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="484b8-262">Web/gRPC</span></span>                              | <span data-ttu-id="484b8-263">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-263">3.0</span></span>        |
| <span data-ttu-id="484b8-264">Fichier tampon de protocole</span><span class="sxs-lookup"><span data-stu-id="484b8-264">Protocol Buffer File</span></span>                         | [<span data-ttu-id="484b8-265">Proto</span><span class="sxs-lookup"><span data-stu-id="484b8-265">proto</span></span>](#namespace)             |              | <span data-ttu-id="484b8-266">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="484b8-266">Web/gRPC</span></span>                              | <span data-ttu-id="484b8-267">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-267">3.0</span></span>        |
| <span data-ttu-id="484b8-268">fichier gitignore dotnet</span><span class="sxs-lookup"><span data-stu-id="484b8-268">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="484b8-269">Config</span><span class="sxs-lookup"><span data-stu-id="484b8-269">Config</span></span>                                | <span data-ttu-id="484b8-270">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-270">3.0</span></span>        |
| <span data-ttu-id="484b8-271">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="484b8-271">global.json file</span></span>                             | [<span data-ttu-id="484b8-272">globaljson (globaljson)</span><span class="sxs-lookup"><span data-stu-id="484b8-272">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="484b8-273">Config</span><span class="sxs-lookup"><span data-stu-id="484b8-273">Config</span></span>                                | <span data-ttu-id="484b8-274">2.0</span><span class="sxs-lookup"><span data-stu-id="484b8-274">2.0</span></span>        |
| <span data-ttu-id="484b8-275">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="484b8-275">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="484b8-276">Config</span><span class="sxs-lookup"><span data-stu-id="484b8-276">Config</span></span>                                | <span data-ttu-id="484b8-277">1.0</span><span class="sxs-lookup"><span data-stu-id="484b8-277">1.0</span></span>        |
| <span data-ttu-id="484b8-278">dotnet local outil manifeste fichier</span><span class="sxs-lookup"><span data-stu-id="484b8-278">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="484b8-279">Config</span><span class="sxs-lookup"><span data-stu-id="484b8-279">Config</span></span>                                | <span data-ttu-id="484b8-280">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-280">3.0</span></span>        |
| <span data-ttu-id="484b8-281">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="484b8-281">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="484b8-282">Config</span><span class="sxs-lookup"><span data-stu-id="484b8-282">Config</span></span>                                | <span data-ttu-id="484b8-283">1.0</span><span class="sxs-lookup"><span data-stu-id="484b8-283">1.0</span></span>        |
| <span data-ttu-id="484b8-284">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="484b8-284">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="484b8-285">Solution</span><span class="sxs-lookup"><span data-stu-id="484b8-285">Solution</span></span>                              | <span data-ttu-id="484b8-286">1.0</span><span class="sxs-lookup"><span data-stu-id="484b8-286">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="484b8-287">Options</span><span class="sxs-lookup"><span data-stu-id="484b8-287">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="484b8-288">Affiche un résumé de ce qui se passerait si la commande donnée était exécutée.</span><span class="sxs-lookup"><span data-stu-id="484b8-288">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="484b8-289">Disponible depuis .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-289">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="484b8-290">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="484b8-290">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="484b8-291">Cela est nécessaire lorsque le modèle choisi remplacerait les fichiers existants dans l’annuaire de sortie.</span><span class="sxs-lookup"><span data-stu-id="484b8-291">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="484b8-292">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="484b8-292">Prints out help for the command.</span></span> <span data-ttu-id="484b8-293">Il peut être invoqué `dotnet new` pour la commande elle-même ou pour n’importe quel modèle.</span><span class="sxs-lookup"><span data-stu-id="484b8-293">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="484b8-294">Par exemple : `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="484b8-294">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="484b8-295">Installe un pack de `PATH` `NUGET_ID` gabarit à partir de la ou fournie.</span><span class="sxs-lookup"><span data-stu-id="484b8-295">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="484b8-296">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="484b8-296">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="484b8-297">Par `dotnet new` défaut, \* passe pour la version, qui représente la dernière version de paquet stable.</span><span class="sxs-lookup"><span data-stu-id="484b8-297">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="484b8-298">Voir un exemple dans la section [Exemples.](#examples)</span><span class="sxs-lookup"><span data-stu-id="484b8-298">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="484b8-299">Si une version du modèle a déjà été installée lorsque vous exécutez cette commande, le modèle sera mis à jour à la version spécifiée, ou à la dernière version stable si aucune version n’a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="484b8-299">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="484b8-300">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="484b8-300">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="484b8-301">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="484b8-301">Lists templates containing the specified name.</span></span> <span data-ttu-id="484b8-302">Si aucun nom n’est spécifié, répertorie tous les modèles.</span><span class="sxs-lookup"><span data-stu-id="484b8-302">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="484b8-303">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="484b8-303">The language of the template to create.</span></span> <span data-ttu-id="484b8-304">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="484b8-304">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="484b8-305">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="484b8-305">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="484b8-306">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="484b8-306">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="484b8-307">Dans ces cas, joindre la valeur du paramètre linguistique dans les guillemets.</span><span class="sxs-lookup"><span data-stu-id="484b8-307">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="484b8-308">Par exemple : `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="484b8-308">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="484b8-309">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="484b8-309">The name for the created output.</span></span> <span data-ttu-id="484b8-310">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="484b8-310">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="484b8-311">Spécifie une source NuGet à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="484b8-311">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="484b8-312">Disponible depuis .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-312">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="484b8-313">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="484b8-313">Location to place the generated output.</span></span> <span data-ttu-id="484b8-314">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="484b8-314">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="484b8-315">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="484b8-315">Filters templates based on available types.</span></span> <span data-ttu-id="484b8-316">Les valeurs prédéfinies sont, `project` `item`, ou `other`.</span><span class="sxs-lookup"><span data-stu-id="484b8-316">Predefined values are `project`, `item`, or `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="484b8-317">Désinstallez un pack `PATH` de `NUGET_ID` gabarit ou fourni.</span><span class="sxs-lookup"><span data-stu-id="484b8-317">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="484b8-318">Lorsque `<PATH|NUGET_ID>` la valeur n’est pas spécifiée, tous les packs de modèles actuellement installés et leurs modèles associés sont affichés.</span><span class="sxs-lookup"><span data-stu-id="484b8-318">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="484b8-319">Lorsque vous `NUGET_ID`spécifiez, n’incluez pas le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="484b8-319">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="484b8-320">Si vous ne spécifiez pas un paramètre à cette option, la commande répertorie les modèles installés et les détails à leur sujet.</span><span class="sxs-lookup"><span data-stu-id="484b8-320">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="484b8-321">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="484b8-321">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="484b8-322">Par exemple, *\<C:/Users/ USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionnera, mais *./GarciaSoftware.ConsoleTemplate.CSharp* du dossier contenant ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="484b8-322">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="484b8-323">N’incluez pas une dernière barre oblique de terminat sur votre trajectoire de modèle.</span><span class="sxs-lookup"><span data-stu-id="484b8-323">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="484b8-324">Vérifie s’il existe des mises à jour disponibles pour les packs de modèles qui sont actuellement installés et les installe.</span><span class="sxs-lookup"><span data-stu-id="484b8-324">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="484b8-325">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="484b8-325">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="484b8-326">Vérifie s’il existe des mises à jour disponibles pour les packs de modèles qui sont actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="484b8-326">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="484b8-327">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="484b8-327">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="484b8-328">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="484b8-328">Template options</span></span>

<span data-ttu-id="484b8-329">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="484b8-329">Each project template may have additional options available.</span></span> <span data-ttu-id="484b8-330">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="484b8-330">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="484b8-331">console</span><span class="sxs-lookup"><span data-stu-id="484b8-331">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="484b8-332">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="484b8-332">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="484b8-333">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="484b8-333">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="484b8-334">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="484b8-334">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="484b8-335">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="484b8-335">SDK version</span></span> | <span data-ttu-id="484b8-336">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="484b8-336">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="484b8-337">3.1</span><span class="sxs-lookup"><span data-stu-id="484b8-337">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="484b8-338">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-338">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="484b8-339">Définit `LangVersion` la propriété dans le fichier de projet créé.</span><span class="sxs-lookup"><span data-stu-id="484b8-339">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="484b8-340">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="484b8-340">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="484b8-341">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="484b8-341">Not supported for F#.</span></span> <span data-ttu-id="484b8-342">Disponible depuis .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-342">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="484b8-343">Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="484b8-343">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="484b8-344">Si spécifié, n’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-344">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="484b8-345">Disponible depuis .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-345">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="484b8-346">classlib</span><span class="sxs-lookup"><span data-stu-id="484b8-346">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="484b8-347">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="484b8-347">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="484b8-348">Valeurs : `netcoreapp<version>` pour créer une bibliothèque de classes .NET Core ou `netstandard<version>` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="484b8-348">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="484b8-349">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="484b8-349">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="484b8-350">Définit `LangVersion` la propriété dans le fichier de projet créé.</span><span class="sxs-lookup"><span data-stu-id="484b8-350">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="484b8-351">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="484b8-351">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="484b8-352">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="484b8-352">Not supported for F#.</span></span> <span data-ttu-id="484b8-353">Disponible depuis .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-353">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="484b8-354">Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="484b8-354">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="484b8-355">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-355">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="484b8-356">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="484b8-356">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="484b8-357">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="484b8-357">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="484b8-358">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="484b8-358">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="484b8-359">Disponible depuis .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-359">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="484b8-360">Définit `LangVersion` la propriété dans le fichier de projet créé.</span><span class="sxs-lookup"><span data-stu-id="484b8-360">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="484b8-361">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="484b8-361">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="484b8-362">Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="484b8-362">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="484b8-363">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-363">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="484b8-364">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="484b8-364">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="484b8-365">Définit `LangVersion` la propriété dans le fichier de projet créé.</span><span class="sxs-lookup"><span data-stu-id="484b8-365">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="484b8-366">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="484b8-366">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="484b8-367">Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="484b8-367">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="484b8-368">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-368">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="484b8-369">travailleur, grpc</span><span class="sxs-lookup"><span data-stu-id="484b8-369">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="484b8-370">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="484b8-370">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="484b8-371">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="484b8-371">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="484b8-372">Disponible depuis .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-372">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="484b8-373">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="484b8-373">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="484b8-374">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-374">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="484b8-375">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="484b8-375">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="484b8-376">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="484b8-376">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="484b8-377">Option disponible depuis .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-377">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="484b8-378">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="484b8-378">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="484b8-379">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="484b8-379">SDK version</span></span> | <span data-ttu-id="484b8-380">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="484b8-380">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="484b8-381">3.1</span><span class="sxs-lookup"><span data-stu-id="484b8-381">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="484b8-382">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-382">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="484b8-383">Permet l’emballage pour le projet à l’aide [de dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="484b8-383">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="484b8-384">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-384">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="484b8-385">Nunit</span><span class="sxs-lookup"><span data-stu-id="484b8-385">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="484b8-386">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="484b8-386">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="484b8-387">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="484b8-387">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="484b8-388">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="484b8-388">SDK version</span></span> | <span data-ttu-id="484b8-389">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="484b8-389">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="484b8-390">3.1</span><span class="sxs-lookup"><span data-stu-id="484b8-390">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="484b8-391">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-391">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="484b8-392">2.2</span><span class="sxs-lookup"><span data-stu-id="484b8-392">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="484b8-393">2.1</span><span class="sxs-lookup"><span data-stu-id="484b8-393">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="484b8-394">Permet l’emballage pour le projet à l’aide [de dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="484b8-394">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="484b8-395">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-395">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="484b8-396">page</span><span class="sxs-lookup"><span data-stu-id="484b8-396">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="484b8-397">Espace nom pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="484b8-397">Namespace for the generated code.</span></span> <span data-ttu-id="484b8-398">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="484b8-398">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="484b8-399">Crée la page sans PageModel.</span><span class="sxs-lookup"><span data-stu-id="484b8-399">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="484b8-400">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="484b8-400">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="484b8-401">Espace nom pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="484b8-401">Namespace for the generated code.</span></span> <span data-ttu-id="484b8-402">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="484b8-402">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="484b8-403">blazorserver</span><span class="sxs-lookup"><span data-stu-id="484b8-403">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="484b8-404">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="484b8-404">The type of authentication to use.</span></span> <span data-ttu-id="484b8-405">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="484b8-405">The possible values are:</span></span>

  - <span data-ttu-id="484b8-406">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="484b8-406">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="484b8-407">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="484b8-407">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="484b8-408">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="484b8-408">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="484b8-409">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="484b8-409">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="484b8-410">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="484b8-410">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="484b8-411">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="484b8-411">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="484b8-412">L’instance Azure Active Directory B2C à connecter.</span><span class="sxs-lookup"><span data-stu-id="484b8-412">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="484b8-413">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-413">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="484b8-414">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="484b8-414">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="484b8-415">L’id de la stratégie d’inscription et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-415">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="484b8-416">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-416">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="484b8-417">L’ID de stratégie de mot de passe de réinitialisation pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-417">The reset password policy ID for this project.</span></span> <span data-ttu-id="484b8-418">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-418">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="484b8-419">L’ID de la stratégie de profil d’édition pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-419">The edit profile policy ID for this project.</span></span> <span data-ttu-id="484b8-420">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-420">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="484b8-421">L’instance Azure Active Directory à connecter.</span><span class="sxs-lookup"><span data-stu-id="484b8-421">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="484b8-422">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-422">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="484b8-423">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="484b8-423">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="484b8-424">L’ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-424">The Client ID for this project.</span></span> <span data-ttu-id="484b8-425">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-425">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="484b8-426">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="484b8-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="484b8-427">Le domaine pour le locataire de l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="484b8-427">The domain for the directory tenant.</span></span> <span data-ttu-id="484b8-428">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="484b8-429">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="484b8-429">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="484b8-430">L’ID TenantId de l’annuaire pour se connecter à.</span><span class="sxs-lookup"><span data-stu-id="484b8-430">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="484b8-431">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="484b8-432">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="484b8-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="484b8-433">Le chemin de demande dans le chemin de base de l’application de l’URI rediriger.</span><span class="sxs-lookup"><span data-stu-id="484b8-433">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="484b8-434">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-434">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="484b8-435">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="484b8-435">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="484b8-436">Permet à cette application de lire l’accès à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="484b8-436">Allows this application read-access to the directory.</span></span> <span data-ttu-id="484b8-437">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-437">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="484b8-438">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="484b8-438">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="484b8-439">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="484b8-439">Turns off HTTPS.</span></span> <span data-ttu-id="484b8-440">Cette option ne `Individual` `IndividualB2C`s’applique `MultiOrg` que si, `--auth`, `SingleOrg`, ou ne sont pas utilisés pour .</span><span class="sxs-lookup"><span data-stu-id="484b8-440">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="484b8-441">Spécifie LocalDB devrait être utilisé au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="484b8-441">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="484b8-442">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-442">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="484b8-443">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-443">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="484b8-444">web</span><span class="sxs-lookup"><span data-stu-id="484b8-444">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="484b8-445">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="484b8-445">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="484b8-446">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="484b8-446">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="484b8-447">Option non disponible en .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-447">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="484b8-448">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="484b8-448">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="484b8-449">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="484b8-449">SDK version</span></span> | <span data-ttu-id="484b8-450">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="484b8-450">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="484b8-451">3.1</span><span class="sxs-lookup"><span data-stu-id="484b8-451">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="484b8-452">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-452">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="484b8-453">2.1</span><span class="sxs-lookup"><span data-stu-id="484b8-453">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="484b8-454">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-454">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="484b8-455">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="484b8-455">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="484b8-456">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="484b8-456">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="484b8-457">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="484b8-457">The type of authentication to use.</span></span> <span data-ttu-id="484b8-458">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="484b8-458">The possible values are:</span></span>

  - <span data-ttu-id="484b8-459">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="484b8-459">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="484b8-460">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="484b8-460">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="484b8-461">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="484b8-461">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="484b8-462">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="484b8-462">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="484b8-463">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="484b8-463">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="484b8-464">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="484b8-464">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="484b8-465">L’instance Azure Active Directory B2C à connecter.</span><span class="sxs-lookup"><span data-stu-id="484b8-465">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="484b8-466">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-466">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="484b8-467">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="484b8-467">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="484b8-468">L’id de la stratégie d’inscription et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-468">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="484b8-469">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-469">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="484b8-470">L’ID de stratégie de mot de passe de réinitialisation pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-470">The reset password policy ID for this project.</span></span> <span data-ttu-id="484b8-471">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-471">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="484b8-472">L’ID de la stratégie de profil d’édition pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-472">The edit profile policy ID for this project.</span></span> <span data-ttu-id="484b8-473">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-473">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="484b8-474">L’instance Azure Active Directory à connecter.</span><span class="sxs-lookup"><span data-stu-id="484b8-474">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="484b8-475">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-475">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="484b8-476">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="484b8-476">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="484b8-477">L’ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-477">The Client ID for this project.</span></span> <span data-ttu-id="484b8-478">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-478">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="484b8-479">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="484b8-479">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="484b8-480">Le domaine pour le locataire de l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="484b8-480">The domain for the directory tenant.</span></span> <span data-ttu-id="484b8-481">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-481">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="484b8-482">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="484b8-482">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="484b8-483">L’ID TenantId de l’annuaire pour se connecter à.</span><span class="sxs-lookup"><span data-stu-id="484b8-483">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="484b8-484">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-484">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="484b8-485">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="484b8-485">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="484b8-486">Le chemin de demande dans le chemin de base de l’application de l’URI rediriger.</span><span class="sxs-lookup"><span data-stu-id="484b8-486">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="484b8-487">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-487">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="484b8-488">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="484b8-488">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="484b8-489">Permet à cette application de lire l’accès à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="484b8-489">Allows this application read-access to the directory.</span></span> <span data-ttu-id="484b8-490">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-490">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="484b8-491">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="484b8-491">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="484b8-492">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="484b8-492">Turns off HTTPS.</span></span> <span data-ttu-id="484b8-493">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="484b8-493">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="484b8-494">Spécifie LocalDB devrait être utilisé au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="484b8-494">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="484b8-495">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-495">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="484b8-496">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="484b8-496">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="484b8-497">Option disponible depuis .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-497">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="484b8-498">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="484b8-498">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="484b8-499">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="484b8-499">SDK version</span></span> | <span data-ttu-id="484b8-500">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="484b8-500">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="484b8-501">3.1</span><span class="sxs-lookup"><span data-stu-id="484b8-501">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="484b8-502">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-502">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="484b8-503">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-503">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="484b8-504">Inclut BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-504">Includes BrowserLink in the project.</span></span> <span data-ttu-id="484b8-505">Option non disponible en .NET Core 2.2 et 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-505">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="484b8-506">Détermine si le projet est configuré pour utiliser [la compilation Razor runtime](/aspnet/core/mvc/views/view-compilation#runtime-compilation) dans les versions Debug.</span><span class="sxs-lookup"><span data-stu-id="484b8-506">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="484b8-507">Option disponible depuis .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-507">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="484b8-508">angulaire, réagir</span><span class="sxs-lookup"><span data-stu-id="484b8-508">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="484b8-509">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="484b8-509">The type of authentication to use.</span></span> <span data-ttu-id="484b8-510">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="484b8-510">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="484b8-511">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="484b8-511">The possible values are:</span></span>

  - <span data-ttu-id="484b8-512">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="484b8-512">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="484b8-513">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="484b8-513">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="484b8-514">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="484b8-514">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="484b8-515">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-515">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="484b8-516">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="484b8-516">Turns off HTTPS.</span></span> <span data-ttu-id="484b8-517">Cette option ne s’applique que si l’authentification est `None`.</span><span class="sxs-lookup"><span data-stu-id="484b8-517">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="484b8-518">Spécifie LocalDB devrait être utilisé au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="484b8-518">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="484b8-519">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-519">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="484b8-520">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="484b8-520">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="484b8-521">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="484b8-521">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="484b8-522">Option non disponible en .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-522">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="484b8-523">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="484b8-523">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="484b8-524">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="484b8-524">SDK version</span></span> | <span data-ttu-id="484b8-525">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="484b8-525">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="484b8-526">3.1</span><span class="sxs-lookup"><span data-stu-id="484b8-526">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="484b8-527">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-527">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="484b8-528">2.1</span><span class="sxs-lookup"><span data-stu-id="484b8-528">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="484b8-529">reactredux</span><span class="sxs-lookup"><span data-stu-id="484b8-529">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="484b8-530">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="484b8-530">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="484b8-531">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="484b8-531">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="484b8-532">Option non disponible en .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-532">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="484b8-533">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="484b8-533">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="484b8-534">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="484b8-534">SDK version</span></span> | <span data-ttu-id="484b8-535">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="484b8-535">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="484b8-536">3.1</span><span class="sxs-lookup"><span data-stu-id="484b8-536">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="484b8-537">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-537">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="484b8-538">2.1</span><span class="sxs-lookup"><span data-stu-id="484b8-538">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="484b8-539">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="484b8-540">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="484b8-540">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="484b8-541">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="484b8-541">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="484b8-542">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-542">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="484b8-543">Prend en charge l’ajout de pages et de vues traditionnelles razor en plus des composants de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="484b8-543">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="484b8-544">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="484b8-544">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="484b8-545">webapi</span><span class="sxs-lookup"><span data-stu-id="484b8-545">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="484b8-546">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="484b8-546">The type of authentication to use.</span></span> <span data-ttu-id="484b8-547">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="484b8-547">The possible values are:</span></span>

  - <span data-ttu-id="484b8-548">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="484b8-548">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="484b8-549">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="484b8-549">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="484b8-550">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="484b8-550">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="484b8-551">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="484b8-551">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="484b8-552">L’instance Azure Active Directory B2C à connecter.</span><span class="sxs-lookup"><span data-stu-id="484b8-552">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="484b8-553">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-553">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="484b8-554">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="484b8-554">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="484b8-555">L’id de la stratégie d’inscription et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-555">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="484b8-556">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="484b8-556">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="484b8-557">L’instance Azure Active Directory à connecter.</span><span class="sxs-lookup"><span data-stu-id="484b8-557">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="484b8-558">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="484b8-559">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="484b8-559">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="484b8-560">L’ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-560">The Client ID for this project.</span></span> <span data-ttu-id="484b8-561">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="484b8-562">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="484b8-562">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="484b8-563">Le domaine pour le locataire de l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="484b8-563">The domain for the directory tenant.</span></span> <span data-ttu-id="484b8-564">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-564">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="484b8-565">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="484b8-565">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="484b8-566">L’ID TenantId de l’annuaire pour se connecter à.</span><span class="sxs-lookup"><span data-stu-id="484b8-566">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="484b8-567">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="484b8-567">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="484b8-568">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="484b8-568">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="484b8-569">Permet à cette application de lire l’accès à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="484b8-569">Allows this application read-access to the directory.</span></span> <span data-ttu-id="484b8-570">Ne s’applique qu’à l’authentification. `SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="484b8-570">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="484b8-571">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="484b8-571">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="484b8-572">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="484b8-572">Turns off HTTPS.</span></span> <span data-ttu-id="484b8-573">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="484b8-573">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="484b8-574">Cette option ne `IndividualB2C` `SingleOrg` s’applique que si l’authentification est utilisée ou non.</span><span class="sxs-lookup"><span data-stu-id="484b8-574">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="484b8-575">Spécifie LocalDB devrait être utilisé au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="484b8-575">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="484b8-576">Ne s’applique qu’à l’authentification. `IndividualB2C`</span><span class="sxs-lookup"><span data-stu-id="484b8-576">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="484b8-577">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="484b8-577">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="484b8-578">Option non disponible en .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="484b8-578">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="484b8-579">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="484b8-579">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="484b8-580">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="484b8-580">SDK version</span></span> | <span data-ttu-id="484b8-581">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="484b8-581">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="484b8-582">3.1</span><span class="sxs-lookup"><span data-stu-id="484b8-582">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="484b8-583">3.0</span><span class="sxs-lookup"><span data-stu-id="484b8-583">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="484b8-584">2.1</span><span class="sxs-lookup"><span data-stu-id="484b8-584">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="484b8-585">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="484b8-585">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="484b8-586">globaljson</span><span class="sxs-lookup"><span data-stu-id="484b8-586">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="484b8-587">Spécifie la version du .NET Core SDK à utiliser dans le fichier *global.json.*</span><span class="sxs-lookup"><span data-stu-id="484b8-587">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="484b8-588">Exemples</span><span class="sxs-lookup"><span data-stu-id="484b8-588">Examples</span></span>

- <span data-ttu-id="484b8-589">Créez un projet d’application console C# en spécifiant le nom du modèle :</span><span class="sxs-lookup"><span data-stu-id="484b8-589">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="484b8-590">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="484b8-590">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="484b8-591">Créez un projet de bibliothèque de classe Standard .NET dans l’annuaire spécifié :</span><span class="sxs-lookup"><span data-stu-id="484b8-591">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="484b8-592">Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :</span><span class="sxs-lookup"><span data-stu-id="484b8-592">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="484b8-593">Créez un projet xUnit :</span><span class="sxs-lookup"><span data-stu-id="484b8-593">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="484b8-594">Énumérez tous les modèles disponibles pour les modèles d’application d’une page unique (SPA) :</span><span class="sxs-lookup"><span data-stu-id="484b8-594">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="484b8-595">Liste de tous les modèles correspondant à la sous-chaîne *we*.</span><span class="sxs-lookup"><span data-stu-id="484b8-595">List all templates matching the *we* substring.</span></span> <span data-ttu-id="484b8-596">Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.</span><span class="sxs-lookup"><span data-stu-id="484b8-596">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="484b8-597">Tentative d’appel du modèle correspondant à *ng*.</span><span class="sxs-lookup"><span data-stu-id="484b8-597">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="484b8-598">Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.</span><span class="sxs-lookup"><span data-stu-id="484b8-598">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="484b8-599">Installer la version 2.0 des modèles SPA pour ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="484b8-599">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="484b8-600">Énumérez les modèles et les détails installés à leur sujet, y compris la façon de les désinstaller :</span><span class="sxs-lookup"><span data-stu-id="484b8-600">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="484b8-601">Créez un *global.json* dans l’annuaire actuel définissant la version SDK à 3.1.101 :</span><span class="sxs-lookup"><span data-stu-id="484b8-601">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="484b8-602">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="484b8-602">See also</span></span>

- [<span data-ttu-id="484b8-603">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="484b8-603">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="484b8-604">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="484b8-604">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="484b8-605">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="484b8-605">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="484b8-606">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="484b8-606">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
