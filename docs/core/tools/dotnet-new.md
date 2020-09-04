---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
no-loc:
- Blazor
- WebAssembly
ms.date: 09/01/2020
ms.openlocfilehash: 8e05f4dc7a03ae8ae68acc6a57f6fa0e1c6b2ce4
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465427"
---
# <a name="dotnet-new"></a><span data-ttu-id="265af-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="265af-103">dotnet new</span></span>

<span data-ttu-id="265af-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="265af-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="265af-105">Name</span><span class="sxs-lookup"><span data-stu-id="265af-105">Name</span></span>

<span data-ttu-id="265af-106">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="265af-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="265af-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="265af-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="265af-108">Description</span><span class="sxs-lookup"><span data-stu-id="265af-108">Description</span></span>

<span data-ttu-id="265af-109">La `dotnet new` commande crée un projet .net Core ou d’autres artefacts basés sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="265af-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="265af-110">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="265af-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="265af-111">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="265af-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="265af-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="265af-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="265af-113">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="265af-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="265af-114">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="265af-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="265af-115">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="265af-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="265af-116">Vous pouvez exécuter `dotnet new --list` ou `dotnet new -l` pour afficher la liste de tous les modèles installés.</span><span class="sxs-lookup"><span data-stu-id="265af-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="265af-117">Si la `TEMPLATE` valeur ne correspond pas exactement au texte de la colonne **Templates** ou **Short Name** de la table retournée, une correspondance de sous-chaînes est effectuée sur ces deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="265af-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="265af-118">À compter du kit de développement logiciel (SDK) .NET Core 3,0, l’interface CLI recherche des modèles dans NuGet.org quand vous appelez la `dotnet new` commande dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="265af-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="265af-119">Si l’interface CLI ne peut pas trouver de correspondance de modèle lors de l’appel `dotnet new` de, pas encore partiel.</span><span class="sxs-lookup"><span data-stu-id="265af-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="265af-120">Si une version plus récente du modèle est disponible.</span><span class="sxs-lookup"><span data-stu-id="265af-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="265af-121">Dans ce cas, le projet ou l’artefact est créé, mais l’interface CLI vous avertit d’une version mise à jour du modèle.</span><span class="sxs-lookup"><span data-stu-id="265af-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="265af-122">Le tableau suivant répertorie les modèles qui sont préinstallés avec le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="265af-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="265af-123">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="265af-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="265af-124">Cliquez sur le lien nom abrégé pour afficher les options de modèle spécifiques.</span><span class="sxs-lookup"><span data-stu-id="265af-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="265af-125">Modèles</span><span class="sxs-lookup"><span data-stu-id="265af-125">Templates</span></span>                                    | <span data-ttu-id="265af-126">Nom court</span><span class="sxs-lookup"><span data-stu-id="265af-126">Short name</span></span>                      | <span data-ttu-id="265af-127">Langage</span><span class="sxs-lookup"><span data-stu-id="265af-127">Language</span></span>     | <span data-ttu-id="265af-128">Étiquettes</span><span class="sxs-lookup"><span data-stu-id="265af-128">Tags</span></span>                                  | <span data-ttu-id="265af-129">Présent</span><span class="sxs-lookup"><span data-stu-id="265af-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="265af-130">Application console</span><span class="sxs-lookup"><span data-stu-id="265af-130">Console Application</span></span>                          | [<span data-ttu-id="265af-131">console</span><span class="sxs-lookup"><span data-stu-id="265af-131">console</span></span>](#console)             | <span data-ttu-id="265af-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="265af-132">[C#], F#, VB</span></span> | <span data-ttu-id="265af-133">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="265af-133">Common/Console</span></span>                        | <span data-ttu-id="265af-134">1.0</span><span class="sxs-lookup"><span data-stu-id="265af-134">1.0</span></span>        |
| <span data-ttu-id="265af-135">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="265af-135">Class library</span></span>                                | [<span data-ttu-id="265af-136">classlib</span><span class="sxs-lookup"><span data-stu-id="265af-136">classlib</span></span>](#classlib)           | <span data-ttu-id="265af-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="265af-137">[C#], F#, VB</span></span> | <span data-ttu-id="265af-138">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="265af-138">Common/Library</span></span>                        | <span data-ttu-id="265af-139">1.0</span><span class="sxs-lookup"><span data-stu-id="265af-139">1.0</span></span>        |
| <span data-ttu-id="265af-140">Application WPF</span><span class="sxs-lookup"><span data-stu-id="265af-140">WPF Application</span></span>                              | [<span data-ttu-id="265af-141">WPF</span><span class="sxs-lookup"><span data-stu-id="265af-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="265af-142">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="265af-142">[C#], VB</span></span>     | <span data-ttu-id="265af-143">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="265af-143">Common/WPF</span></span>                            | <span data-ttu-id="265af-144">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-144">3.0</span></span>        |
| <span data-ttu-id="265af-145">Bibliothèque de classes WPF</span><span class="sxs-lookup"><span data-stu-id="265af-145">WPF Class library</span></span>                            | [<span data-ttu-id="265af-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="265af-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="265af-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="265af-147">[C#], VB</span></span>     | <span data-ttu-id="265af-148">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="265af-148">Common/WPF</span></span>                            | <span data-ttu-id="265af-149">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-149">3.0</span></span>        |
| <span data-ttu-id="265af-150">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="265af-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="265af-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="265af-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="265af-152">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="265af-152">[C#], VB</span></span>     | <span data-ttu-id="265af-153">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="265af-153">Common/WPF</span></span>                            | <span data-ttu-id="265af-154">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-154">3.0</span></span>        |
| <span data-ttu-id="265af-155">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="265af-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="265af-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="265af-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="265af-157">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="265af-157">[C#], VB</span></span>     | <span data-ttu-id="265af-158">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="265af-158">Common/WPF</span></span>                            | <span data-ttu-id="265af-159">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-159">3.0</span></span>        |
| <span data-ttu-id="265af-160">Application Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="265af-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="265af-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="265af-161">winforms</span></span>](#winforms)           | <span data-ttu-id="265af-162">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="265af-162">[C#], VB</span></span>     | <span data-ttu-id="265af-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="265af-163">Common/WinForms</span></span>                       | <span data-ttu-id="265af-164">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-164">3.0</span></span>        |
| <span data-ttu-id="265af-165">Bibliothèque de classes Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="265af-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="265af-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="265af-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="265af-167">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="265af-167">[C#], VB</span></span>     | <span data-ttu-id="265af-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="265af-168">Common/WinForms</span></span>                       | <span data-ttu-id="265af-169">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-169">3.0</span></span>        |
| <span data-ttu-id="265af-170">Service Worker</span><span class="sxs-lookup"><span data-stu-id="265af-170">Worker Service</span></span>                               | [<span data-ttu-id="265af-171">collabor</span><span class="sxs-lookup"><span data-stu-id="265af-171">worker</span></span>](#web-others)           | <span data-ttu-id="265af-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-172">[C#]</span></span>         | <span data-ttu-id="265af-173">Commun/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="265af-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="265af-174">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-174">3.0</span></span>        |
| <span data-ttu-id="265af-175">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="265af-175">Unit Test Project</span></span>                            | [<span data-ttu-id="265af-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="265af-176">mstest</span></span>](#test)                 | <span data-ttu-id="265af-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="265af-177">[C#], F#, VB</span></span> | <span data-ttu-id="265af-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="265af-178">Test/MSTest</span></span>                           | <span data-ttu-id="265af-179">1.0</span><span class="sxs-lookup"><span data-stu-id="265af-179">1.0</span></span>        |
| <span data-ttu-id="265af-180">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="265af-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="265af-181">nunit</span><span class="sxs-lookup"><span data-stu-id="265af-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="265af-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="265af-182">[C#], F#, VB</span></span> | <span data-ttu-id="265af-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="265af-183">Test/NUnit</span></span>                            | <span data-ttu-id="265af-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="265af-184">2.1.400</span></span>    |
| <span data-ttu-id="265af-185">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="265af-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="265af-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="265af-186">[C#], F#, VB</span></span> | <span data-ttu-id="265af-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="265af-187">Test/NUnit</span></span>                            | <span data-ttu-id="265af-188">2.2</span><span class="sxs-lookup"><span data-stu-id="265af-188">2.2</span></span>        |
| <span data-ttu-id="265af-189">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="265af-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="265af-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="265af-190">xunit</span></span>](#test)                  | <span data-ttu-id="265af-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="265af-191">[C#], F#, VB</span></span> | <span data-ttu-id="265af-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="265af-192">Test/xUnit</span></span>                            | <span data-ttu-id="265af-193">1.0</span><span class="sxs-lookup"><span data-stu-id="265af-193">1.0</span></span>        |
| <span data-ttu-id="265af-194">Composant Razor</span><span class="sxs-lookup"><span data-stu-id="265af-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="265af-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-195">[C#]</span></span>         | <span data-ttu-id="265af-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="265af-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="265af-197">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-197">3.0</span></span>        |
| <span data-ttu-id="265af-198">Page Razor</span><span class="sxs-lookup"><span data-stu-id="265af-198">Razor Page</span></span>                                   | [<span data-ttu-id="265af-199">page</span><span class="sxs-lookup"><span data-stu-id="265af-199">page</span></span>](#page)                   | <span data-ttu-id="265af-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-200">[C#]</span></span>         | <span data-ttu-id="265af-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="265af-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="265af-202">2,0</span><span class="sxs-lookup"><span data-stu-id="265af-202">2.0</span></span>        |
| <span data-ttu-id="265af-203">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="265af-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="265af-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="265af-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="265af-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-205">[C#]</span></span>         | <span data-ttu-id="265af-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="265af-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="265af-207">2,0</span><span class="sxs-lookup"><span data-stu-id="265af-207">2.0</span></span>        |
| <span data-ttu-id="265af-208">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="265af-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="265af-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-209">[C#]</span></span>         | <span data-ttu-id="265af-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="265af-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="265af-211">2,0</span><span class="sxs-lookup"><span data-stu-id="265af-211">2.0</span></span>        |
| <span data-ttu-id="265af-212">Blazor Application serveur</span><span class="sxs-lookup"><span data-stu-id="265af-212">Blazor Server App</span></span>                            | [<span data-ttu-id="265af-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="265af-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="265af-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-214">[C#]</span></span>         | <span data-ttu-id="265af-215">InternetBlazor</span><span class="sxs-lookup"><span data-stu-id="265af-215">Web/Blazor</span></span>                            | <span data-ttu-id="265af-216">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-216">3.0</span></span>        |
| <span data-ttu-id="265af-217">BlazorWebAssemblyApplication</span><span class="sxs-lookup"><span data-stu-id="265af-217">Blazor WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="265af-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-218">[C#]</span></span>         | <span data-ttu-id="265af-219">InternetBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="265af-219">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="265af-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="265af-220">3.1.300</span></span>    |
| <span data-ttu-id="265af-221">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="265af-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="265af-222">web</span><span class="sxs-lookup"><span data-stu-id="265af-222">web</span></span>](#web)                     | <span data-ttu-id="265af-223">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="265af-223">[C#], F#</span></span>     | <span data-ttu-id="265af-224">Web/vides</span><span class="sxs-lookup"><span data-stu-id="265af-224">Web/Empty</span></span>                             | <span data-ttu-id="265af-225">1.0</span><span class="sxs-lookup"><span data-stu-id="265af-225">1.0</span></span>        |
| <span data-ttu-id="265af-226">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="265af-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="265af-227">MVC</span><span class="sxs-lookup"><span data-stu-id="265af-227">mvc</span></span>](#web-options)             | <span data-ttu-id="265af-228">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="265af-228">[C#], F#</span></span>     | <span data-ttu-id="265af-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="265af-229">Web/MVC</span></span>                               | <span data-ttu-id="265af-230">1.0</span><span class="sxs-lookup"><span data-stu-id="265af-230">1.0</span></span>        |
| <span data-ttu-id="265af-231">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="265af-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="265af-232">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="265af-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="265af-233">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-233">[C#]</span></span>         | <span data-ttu-id="265af-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="265af-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="265af-235">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="265af-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="265af-236">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="265af-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="265af-237">oblique</span><span class="sxs-lookup"><span data-stu-id="265af-237">angular</span></span>](#spa)                 | <span data-ttu-id="265af-238">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-238">[C#]</span></span>         | <span data-ttu-id="265af-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="265af-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="265af-240">2,0</span><span class="sxs-lookup"><span data-stu-id="265af-240">2.0</span></span>        |
| <span data-ttu-id="265af-241">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="265af-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="265af-242">réagir</span><span class="sxs-lookup"><span data-stu-id="265af-242">react</span></span>](#spa)                   | <span data-ttu-id="265af-243">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-243">[C#]</span></span>         | <span data-ttu-id="265af-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="265af-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="265af-245">2,0</span><span class="sxs-lookup"><span data-stu-id="265af-245">2.0</span></span>        |
| <span data-ttu-id="265af-246">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="265af-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="265af-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="265af-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="265af-248">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-248">[C#]</span></span>         | <span data-ttu-id="265af-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="265af-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="265af-250">2,0</span><span class="sxs-lookup"><span data-stu-id="265af-250">2.0</span></span>        |
| <span data-ttu-id="265af-251">Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="265af-251">Razor Class Library</span></span>                          | [<span data-ttu-id="265af-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="265af-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="265af-253">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-253">[C#]</span></span>         | <span data-ttu-id="265af-254">Web/Razor/Library/Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="265af-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="265af-255">2.1</span><span class="sxs-lookup"><span data-stu-id="265af-255">2.1</span></span>        |
| <span data-ttu-id="265af-256">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="265af-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="265af-257">WebAPI</span><span class="sxs-lookup"><span data-stu-id="265af-257">webapi</span></span>](#webapi)               | <span data-ttu-id="265af-258">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="265af-258">[C#], F#</span></span>     | <span data-ttu-id="265af-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="265af-259">Web/WebAPI</span></span>                            | <span data-ttu-id="265af-260">1.0</span><span class="sxs-lookup"><span data-stu-id="265af-260">1.0</span></span>        |
| <span data-ttu-id="265af-261">ASP.NET Core Service gRPC</span><span class="sxs-lookup"><span data-stu-id="265af-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="265af-262">GRPC</span><span class="sxs-lookup"><span data-stu-id="265af-262">grpc</span></span>](#web-others)             | <span data-ttu-id="265af-263">[C#]</span><span class="sxs-lookup"><span data-stu-id="265af-263">[C#]</span></span>         | <span data-ttu-id="265af-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="265af-264">Web/gRPC</span></span>                              | <span data-ttu-id="265af-265">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-265">3.0</span></span>        |
| <span data-ttu-id="265af-266">fichier gitignore dotnet</span><span class="sxs-lookup"><span data-stu-id="265af-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="265af-267">Config</span><span class="sxs-lookup"><span data-stu-id="265af-267">Config</span></span>                                | <span data-ttu-id="265af-268">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-268">3.0</span></span>        |
| <span data-ttu-id="265af-269">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="265af-269">global.json file</span></span>                             | [<span data-ttu-id="265af-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="265af-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="265af-271">Config</span><span class="sxs-lookup"><span data-stu-id="265af-271">Config</span></span>                                | <span data-ttu-id="265af-272">2,0</span><span class="sxs-lookup"><span data-stu-id="265af-272">2.0</span></span>        |
| <span data-ttu-id="265af-273">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="265af-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="265af-274">Config</span><span class="sxs-lookup"><span data-stu-id="265af-274">Config</span></span>                                | <span data-ttu-id="265af-275">1.0</span><span class="sxs-lookup"><span data-stu-id="265af-275">1.0</span></span>        |
| <span data-ttu-id="265af-276">Fichier manifeste de l’outil local dotnet</span><span class="sxs-lookup"><span data-stu-id="265af-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="265af-277">Config</span><span class="sxs-lookup"><span data-stu-id="265af-277">Config</span></span>                                | <span data-ttu-id="265af-278">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-278">3.0</span></span>        |
| <span data-ttu-id="265af-279">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="265af-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="265af-280">Config</span><span class="sxs-lookup"><span data-stu-id="265af-280">Config</span></span>                                | <span data-ttu-id="265af-281">1.0</span><span class="sxs-lookup"><span data-stu-id="265af-281">1.0</span></span>        |
| <span data-ttu-id="265af-282">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="265af-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="265af-283">Solution</span><span class="sxs-lookup"><span data-stu-id="265af-283">Solution</span></span>                              | <span data-ttu-id="265af-284">1.0</span><span class="sxs-lookup"><span data-stu-id="265af-284">1.0</span></span>        |
| <span data-ttu-id="265af-285">Fichier de mémoire tampon de protocole</span><span class="sxs-lookup"><span data-stu-id="265af-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="265af-286">proto</span><span class="sxs-lookup"><span data-stu-id="265af-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="265af-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="265af-287">Web/gRPC</span></span>                              | <span data-ttu-id="265af-288">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="265af-289">Options</span><span class="sxs-lookup"><span data-stu-id="265af-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="265af-290">Affiche un récapitulatif de ce qui se passerait si la commande donnée était exécutée (si cela donnerait lieu à la création d’un modèle).</span><span class="sxs-lookup"><span data-stu-id="265af-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="265af-291">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="265af-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="265af-292">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="265af-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="265af-293">Cela est obligatoire lorsque le modèle choisi remplace les fichiers existants dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="265af-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="265af-294">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="265af-294">Prints out help for the command.</span></span> <span data-ttu-id="265af-295">Elle peut être appelée pour la `dotnet new` commande elle-même ou pour n’importe quel modèle.</span><span class="sxs-lookup"><span data-stu-id="265af-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="265af-296">Par exemple : `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="265af-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="265af-297">Installe un pack de modèles à partir du `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="265af-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="265af-298">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="265af-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="265af-299">Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package.</span><span class="sxs-lookup"><span data-stu-id="265af-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="265af-300">Consultez un exemple dans la section [exemples](#examples) .</span><span class="sxs-lookup"><span data-stu-id="265af-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="265af-301">Si une version du modèle a déjà été installée lorsque vous exécutez cette commande, le modèle sera mis à jour vers la version spécifiée, ou vers la version stable la plus récente si aucune version n’a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="265af-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="265af-302">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="265af-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="265af-303">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="265af-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="265af-304">Si aucun nom n’est spécifié, répertorie tous les modèles.</span><span class="sxs-lookup"><span data-stu-id="265af-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="265af-305">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="265af-305">The language of the template to create.</span></span> <span data-ttu-id="265af-306">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="265af-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="265af-307">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="265af-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="265af-308">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="265af-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="265af-309">Dans ce cas, mettez la valeur du paramètre de langue entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="265af-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="265af-310">Par exemple : `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="265af-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="265af-311">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="265af-311">The name for the created output.</span></span> <span data-ttu-id="265af-312">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="265af-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="265af-313">Spécifie une source NuGet à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="265af-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="265af-314">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="265af-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="265af-315">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="265af-315">Location to place the generated output.</span></span> <span data-ttu-id="265af-316">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="265af-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="265af-317">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="265af-317">Filters templates based on available types.</span></span> <span data-ttu-id="265af-318">Les valeurs prédéfinies sont `project` , `item` et `other` .</span><span class="sxs-lookup"><span data-stu-id="265af-318">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="265af-319">Désinstalle un pack de modèles au niveau de `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="265af-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="265af-320">Lorsque la `<PATH|NUGET_ID>` valeur n’est pas spécifiée, tous les packs de modèles actuellement installés et leurs modèles associés sont affichés.</span><span class="sxs-lookup"><span data-stu-id="265af-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="265af-321">Lorsque vous spécifiez `NUGET_ID` , n’incluez pas le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="265af-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="265af-322">Si vous ne spécifiez pas de paramètre pour cette option, la commande répertorie les modèles installés et fournit des détails à leur sujet.</span><span class="sxs-lookup"><span data-stu-id="265af-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="265af-323">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="265af-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="265af-324">Par exemple, *C:/Users/ \<USER> /documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionnera, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne le sera pas.</span><span class="sxs-lookup"><span data-stu-id="265af-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="265af-325">N’incluez pas de barre oblique finale de répertoire finale dans le chemin d’accès de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="265af-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="265af-326">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés et les installe.</span><span class="sxs-lookup"><span data-stu-id="265af-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="265af-327">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="265af-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="265af-328">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="265af-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="265af-329">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="265af-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="265af-330">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="265af-330">Template options</span></span>

<span data-ttu-id="265af-331">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="265af-331">Each project template may have additional options available.</span></span> <span data-ttu-id="265af-332">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="265af-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="265af-333">console</span><span class="sxs-lookup"><span data-stu-id="265af-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="265af-334">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="265af-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="265af-335">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="265af-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="265af-336">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="265af-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="265af-337">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="265af-337">SDK version</span></span> | <span data-ttu-id="265af-338">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="265af-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="265af-339">3.1</span><span class="sxs-lookup"><span data-stu-id="265af-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="265af-340">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="265af-341">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="265af-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="265af-342">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="265af-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="265af-343">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="265af-343">Not supported for F#.</span></span> <span data-ttu-id="265af-344">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="265af-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="265af-345">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="265af-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="265af-346">S’il est spécifié, n’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="265af-347">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="265af-347">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="265af-348">classlib</span><span class="sxs-lookup"><span data-stu-id="265af-348">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="265af-349">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="265af-349">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="265af-350">Valeurs : `netcoreapp<version>` pour créer une bibliothèque de classes .NET Core ou `netstandard<version>` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="265af-350">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="265af-351">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="265af-351">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="265af-352">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="265af-352">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="265af-353">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="265af-353">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="265af-354">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="265af-354">Not supported for F#.</span></span> <span data-ttu-id="265af-355">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="265af-355">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="265af-356">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="265af-356">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="265af-357">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-357">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="265af-358">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="265af-358">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="265af-359">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="265af-359">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="265af-360">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="265af-360">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="265af-361">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="265af-361">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="265af-362">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="265af-362">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="265af-363">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="265af-363">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="265af-364">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="265af-364">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="265af-365">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-365">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="265af-366">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="265af-366">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="265af-367">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="265af-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="265af-368">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="265af-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="265af-369">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="265af-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="265af-370">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="265af-371">Worker, GRPC</span><span class="sxs-lookup"><span data-stu-id="265af-371">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="265af-372">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="265af-372">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="265af-373">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="265af-373">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="265af-374">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="265af-374">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="265af-375">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="265af-375">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="265af-376">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-376">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="265af-377">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="265af-377">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="265af-378">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="265af-378">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="265af-379">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="265af-379">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="265af-380">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="265af-380">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="265af-381">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="265af-381">SDK version</span></span> | <span data-ttu-id="265af-382">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="265af-382">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="265af-383">3.1</span><span class="sxs-lookup"><span data-stu-id="265af-383">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="265af-384">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-384">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="265af-385">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="265af-385">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="265af-386">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-386">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="265af-387">nunit</span><span class="sxs-lookup"><span data-stu-id="265af-387">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="265af-388">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="265af-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="265af-389">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="265af-389">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="265af-390">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="265af-390">SDK version</span></span> | <span data-ttu-id="265af-391">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="265af-391">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="265af-392">3.1</span><span class="sxs-lookup"><span data-stu-id="265af-392">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="265af-393">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-393">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="265af-394">2.2</span><span class="sxs-lookup"><span data-stu-id="265af-394">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="265af-395">2.1</span><span class="sxs-lookup"><span data-stu-id="265af-395">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="265af-396">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="265af-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="265af-397">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-397">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="265af-398">page</span><span class="sxs-lookup"><span data-stu-id="265af-398">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="265af-399">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="265af-399">Namespace for the generated code.</span></span> <span data-ttu-id="265af-400">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="265af-400">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="265af-401">Crée la page sans PageModel.</span><span class="sxs-lookup"><span data-stu-id="265af-401">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="265af-402">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="265af-402">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="265af-403">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="265af-403">Namespace for the generated code.</span></span> <span data-ttu-id="265af-404">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="265af-404">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="265af-405">blazorserver</span><span class="sxs-lookup"><span data-stu-id="265af-405">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="265af-406">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="265af-406">The type of authentication to use.</span></span> <span data-ttu-id="265af-407">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="265af-407">The possible values are:</span></span>

  - <span data-ttu-id="265af-408">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="265af-408">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="265af-409">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="265af-409">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="265af-410">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="265af-410">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="265af-411">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="265af-411">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="265af-412">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="265af-412">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="265af-413">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="265af-413">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="265af-414">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="265af-414">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="265af-415">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-415">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="265af-416">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="265af-416">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="265af-417">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="265af-417">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="265af-418">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-418">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="265af-419">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="265af-419">The reset password policy ID for this project.</span></span> <span data-ttu-id="265af-420">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-420">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="265af-421">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="265af-421">The edit profile policy ID for this project.</span></span> <span data-ttu-id="265af-422">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-422">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="265af-423">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="265af-423">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="265af-424">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-424">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="265af-425">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="265af-425">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="265af-426">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="265af-426">The Client ID for this project.</span></span> <span data-ttu-id="265af-427">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-427">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="265af-428">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="265af-428">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="265af-429">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="265af-429">The domain for the directory tenant.</span></span> <span data-ttu-id="265af-430">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-430">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="265af-431">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="265af-431">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="265af-432">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="265af-432">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="265af-433">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-433">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="265af-434">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="265af-434">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="265af-435">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="265af-435">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="265af-436">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="265af-437">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="265af-437">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="265af-438">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="265af-438">Allows this application read-access to the directory.</span></span> <span data-ttu-id="265af-439">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-439">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="265af-440">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="265af-440">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="265af-441">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="265af-441">Turns off HTTPS.</span></span> <span data-ttu-id="265af-442">Cette option s’applique uniquement si `Individual` , `IndividualB2C` , `SingleOrg` ou `MultiOrg` ne sont pas utilisés pour `--auth` .</span><span class="sxs-lookup"><span data-stu-id="265af-442">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="265af-443">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="265af-443">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="265af-444">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-444">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="265af-445">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-445">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="265af-446">web</span><span class="sxs-lookup"><span data-stu-id="265af-446">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="265af-447">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="265af-447">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="265af-448">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="265af-448">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="265af-449">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="265af-449">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="265af-450">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="265af-450">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="265af-451">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="265af-451">SDK version</span></span> | <span data-ttu-id="265af-452">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="265af-452">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="265af-453">3.1</span><span class="sxs-lookup"><span data-stu-id="265af-453">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="265af-454">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-454">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="265af-455">2.1</span><span class="sxs-lookup"><span data-stu-id="265af-455">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="265af-456">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-456">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="265af-457">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="265af-457">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="265af-458">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="265af-458">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="265af-459">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="265af-459">The type of authentication to use.</span></span> <span data-ttu-id="265af-460">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="265af-460">The possible values are:</span></span>

  - <span data-ttu-id="265af-461">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="265af-461">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="265af-462">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="265af-462">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="265af-463">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="265af-463">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="265af-464">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="265af-464">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="265af-465">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="265af-465">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="265af-466">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="265af-466">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="265af-467">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="265af-467">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="265af-468">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-468">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="265af-469">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="265af-469">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="265af-470">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="265af-470">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="265af-471">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-471">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="265af-472">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="265af-472">The reset password policy ID for this project.</span></span> <span data-ttu-id="265af-473">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-473">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="265af-474">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="265af-474">The edit profile policy ID for this project.</span></span> <span data-ttu-id="265af-475">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-475">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="265af-476">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="265af-476">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="265af-477">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-477">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="265af-478">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="265af-478">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="265af-479">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="265af-479">The Client ID for this project.</span></span> <span data-ttu-id="265af-480">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-480">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="265af-481">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="265af-481">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="265af-482">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="265af-482">The domain for the directory tenant.</span></span> <span data-ttu-id="265af-483">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-483">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="265af-484">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="265af-484">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="265af-485">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="265af-485">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="265af-486">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-486">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="265af-487">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="265af-487">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="265af-488">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="265af-488">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="265af-489">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-489">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="265af-490">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="265af-490">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="265af-491">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="265af-491">Allows this application read-access to the directory.</span></span> <span data-ttu-id="265af-492">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-492">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="265af-493">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="265af-493">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="265af-494">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="265af-494">Turns off HTTPS.</span></span> <span data-ttu-id="265af-495">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="265af-495">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="265af-496">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="265af-496">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="265af-497">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-497">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="265af-498">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="265af-498">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="265af-499">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="265af-499">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="265af-500">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="265af-500">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="265af-501">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="265af-501">SDK version</span></span> | <span data-ttu-id="265af-502">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="265af-502">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="265af-503">3.1</span><span class="sxs-lookup"><span data-stu-id="265af-503">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="265af-504">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-504">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="265af-505">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-505">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="265af-506">Comprend BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="265af-506">Includes BrowserLink in the project.</span></span> <span data-ttu-id="265af-507">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2 et 3,1.</span><span class="sxs-lookup"><span data-stu-id="265af-507">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="265af-508">Détermine si le projet est configuré pour utiliser la [compilation du runtime Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) dans les versions Debug.</span><span class="sxs-lookup"><span data-stu-id="265af-508">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="265af-509">Option disponible depuis le kit de développement logiciel (SDK) 3.1.201 .NET Core.</span><span class="sxs-lookup"><span data-stu-id="265af-509">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="265af-510">angulaire, réaction</span><span class="sxs-lookup"><span data-stu-id="265af-510">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="265af-511">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="265af-511">The type of authentication to use.</span></span> <span data-ttu-id="265af-512">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="265af-512">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="265af-513">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="265af-513">The possible values are:</span></span>

  - <span data-ttu-id="265af-514">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="265af-514">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="265af-515">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="265af-515">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="265af-516">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="265af-516">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="265af-517">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-517">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="265af-518">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="265af-518">Turns off HTTPS.</span></span> <span data-ttu-id="265af-519">Cette option s’applique uniquement si l’authentification est `None` .</span><span class="sxs-lookup"><span data-stu-id="265af-519">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="265af-520">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="265af-520">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="265af-521">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-521">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="265af-522">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="265af-522">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="265af-523">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="265af-523">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="265af-524">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="265af-524">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="265af-525">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="265af-525">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="265af-526">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="265af-526">SDK version</span></span> | <span data-ttu-id="265af-527">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="265af-527">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="265af-528">3.1</span><span class="sxs-lookup"><span data-stu-id="265af-528">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="265af-529">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-529">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="265af-530">2.1</span><span class="sxs-lookup"><span data-stu-id="265af-530">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="265af-531">reactredux</span><span class="sxs-lookup"><span data-stu-id="265af-531">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="265af-532">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="265af-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="265af-533">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="265af-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="265af-534">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="265af-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="265af-535">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="265af-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="265af-536">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="265af-536">SDK version</span></span> | <span data-ttu-id="265af-537">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="265af-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="265af-538">3.1</span><span class="sxs-lookup"><span data-stu-id="265af-538">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="265af-539">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-539">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="265af-540">2.1</span><span class="sxs-lookup"><span data-stu-id="265af-540">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="265af-541">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="265af-542">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="265af-542">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="265af-543">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="265af-543">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="265af-544">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-544">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="265af-545">Prend en charge l’ajout de pages et de vues Razor traditionnelles en plus des composants de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="265af-545">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="265af-546">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="265af-546">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="265af-547">webapi</span><span class="sxs-lookup"><span data-stu-id="265af-547">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="265af-548">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="265af-548">The type of authentication to use.</span></span> <span data-ttu-id="265af-549">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="265af-549">The possible values are:</span></span>

  - <span data-ttu-id="265af-550">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="265af-550">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="265af-551">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="265af-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="265af-552">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="265af-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="265af-553">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="265af-553">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="265af-554">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="265af-554">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="265af-555">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-555">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="265af-556">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="265af-556">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="265af-557">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="265af-557">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="265af-558">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="265af-558">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="265af-559">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="265af-559">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="265af-560">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-560">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="265af-561">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="265af-561">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="265af-562">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="265af-562">The Client ID for this project.</span></span> <span data-ttu-id="265af-563">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="265af-564">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="265af-564">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="265af-565">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="265af-565">The domain for the directory tenant.</span></span> <span data-ttu-id="265af-566">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-566">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="265af-567">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="265af-567">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="265af-568">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="265af-568">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="265af-569">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="265af-569">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="265af-570">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="265af-570">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="265af-571">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="265af-571">Allows this application read-access to the directory.</span></span> <span data-ttu-id="265af-572">S’applique uniquement à `SingleOrg` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="265af-572">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="265af-573">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="265af-573">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="265af-574">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="265af-574">Turns off HTTPS.</span></span> <span data-ttu-id="265af-575">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="265af-575">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="265af-576">Cette option s’applique uniquement si `IndividualB2C` ou `SingleOrg` ne sont pas utilisés pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="265af-576">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="265af-577">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="265af-577">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="265af-578">S’applique uniquement à `IndividualB2C` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="265af-578">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="265af-579">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="265af-579">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="265af-580">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="265af-580">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="265af-581">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="265af-581">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="265af-582">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="265af-582">SDK version</span></span> | <span data-ttu-id="265af-583">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="265af-583">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="265af-584">3.1</span><span class="sxs-lookup"><span data-stu-id="265af-584">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="265af-585">3.0</span><span class="sxs-lookup"><span data-stu-id="265af-585">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="265af-586">2.1</span><span class="sxs-lookup"><span data-stu-id="265af-586">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="265af-587">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="265af-587">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="265af-588">globaljson</span><span class="sxs-lookup"><span data-stu-id="265af-588">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="265af-589">Spécifie la version de la kit SDK .NET Core à utiliser dans le fichier *global.js* .</span><span class="sxs-lookup"><span data-stu-id="265af-589">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="265af-590">Exemples</span><span class="sxs-lookup"><span data-stu-id="265af-590">Examples</span></span>

- <span data-ttu-id="265af-591">Créez un projet d’application console C# en spécifiant le nom du modèle :</span><span class="sxs-lookup"><span data-stu-id="265af-591">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="265af-592">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="265af-592">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="265af-593">Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié :</span><span class="sxs-lookup"><span data-stu-id="265af-593">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="265af-594">Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :</span><span class="sxs-lookup"><span data-stu-id="265af-594">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="265af-595">Créez un projet xUnit :</span><span class="sxs-lookup"><span data-stu-id="265af-595">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="265af-596">Répertorier tous les modèles disponibles pour les modèles d’application à page unique (SPA) :</span><span class="sxs-lookup"><span data-stu-id="265af-596">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="265af-597">Liste de tous les modèles correspondant à la sous-chaîne *we*.</span><span class="sxs-lookup"><span data-stu-id="265af-597">List all templates matching the *we* substring.</span></span> <span data-ttu-id="265af-598">Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.</span><span class="sxs-lookup"><span data-stu-id="265af-598">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="265af-599">Tentative d’appel du modèle correspondant à *ng*.</span><span class="sxs-lookup"><span data-stu-id="265af-599">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="265af-600">Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.</span><span class="sxs-lookup"><span data-stu-id="265af-600">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="265af-601">Installez la version 2,0 des modèles SPA pour ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="265af-601">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="265af-602">Répertoriez les modèles installés et les détails les concernant, notamment comment les désinstaller :</span><span class="sxs-lookup"><span data-stu-id="265af-602">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="265af-603">Créez un *global.js* dans le répertoire actif en définissant la version du kit de développement logiciel (SDK) sur 3.1.101 :</span><span class="sxs-lookup"><span data-stu-id="265af-603">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="265af-604">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="265af-604">See also</span></span>

- [<span data-ttu-id="265af-605">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="265af-605">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="265af-606">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="265af-606">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="265af-607">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="265af-607">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="265af-608">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="265af-608">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
