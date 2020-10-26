---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
no-loc:
- Blazor
- WebAssembly
ms.date: 09/01/2020
ms.openlocfilehash: 4a4c8e2806fee663b5f6aa255a6f24250a072a85
ms.sourcegitcommit: 532b03d5bbab764d63356193b04cd2281bc01239
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2020
ms.locfileid: "92526618"
---
# <a name="dotnet-new"></a><span data-ttu-id="8472f-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8472f-103">dotnet new</span></span>

<span data-ttu-id="8472f-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="8472f-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8472f-105">Nom</span><span class="sxs-lookup"><span data-stu-id="8472f-105">Name</span></span>

<span data-ttu-id="8472f-106">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="8472f-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8472f-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8472f-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="8472f-108">Description</span><span class="sxs-lookup"><span data-stu-id="8472f-108">Description</span></span>

<span data-ttu-id="8472f-109">La `dotnet new` commande crée un projet .net Core ou d’autres artefacts basés sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="8472f-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="8472f-110">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8472f-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="8472f-111">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="8472f-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="8472f-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="8472f-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="8472f-113">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="8472f-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="8472f-114">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="8472f-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="8472f-115">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="8472f-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="8472f-116">Vous pouvez exécuter `dotnet new --list` ou `dotnet new -l` pour afficher la liste de tous les modèles installés.</span><span class="sxs-lookup"><span data-stu-id="8472f-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="8472f-117">Si la `TEMPLATE` valeur ne correspond pas exactement au texte de la colonne **Templates** ou **Short Name** de la table retournée, une correspondance de sous-chaînes est effectuée sur ces deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="8472f-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="8472f-118">À compter du kit de développement logiciel (SDK) .NET Core 3,0, l’interface CLI recherche des modèles dans NuGet.org quand vous appelez la `dotnet new` commande dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="8472f-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="8472f-119">Si l’interface CLI ne peut pas trouver de correspondance de modèle lors de l’appel `dotnet new` de, pas encore partiel.</span><span class="sxs-lookup"><span data-stu-id="8472f-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="8472f-120">Si une version plus récente du modèle est disponible.</span><span class="sxs-lookup"><span data-stu-id="8472f-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="8472f-121">Dans ce cas, le projet ou l’artefact est créé, mais l’interface CLI vous avertit d’une version mise à jour du modèle.</span><span class="sxs-lookup"><span data-stu-id="8472f-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="8472f-122">Le tableau suivant répertorie les modèles qui sont préinstallés avec le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8472f-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="8472f-123">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="8472f-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="8472f-124">Cliquez sur le lien nom abrégé pour afficher les options de modèle spécifiques.</span><span class="sxs-lookup"><span data-stu-id="8472f-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="8472f-125">Modèles</span><span class="sxs-lookup"><span data-stu-id="8472f-125">Templates</span></span>                                    | <span data-ttu-id="8472f-126">Nom court</span><span class="sxs-lookup"><span data-stu-id="8472f-126">Short name</span></span>                      | <span data-ttu-id="8472f-127">Langage</span><span class="sxs-lookup"><span data-stu-id="8472f-127">Language</span></span>     | <span data-ttu-id="8472f-128">Étiquettes</span><span class="sxs-lookup"><span data-stu-id="8472f-128">Tags</span></span>                                  | <span data-ttu-id="8472f-129">Introduit</span><span class="sxs-lookup"><span data-stu-id="8472f-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="8472f-130">Application console</span><span class="sxs-lookup"><span data-stu-id="8472f-130">Console Application</span></span>                          | [<span data-ttu-id="8472f-131">console</span><span class="sxs-lookup"><span data-stu-id="8472f-131">console</span></span>](#console)             | <span data-ttu-id="8472f-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8472f-132">[C#], F#, VB</span></span> | <span data-ttu-id="8472f-133">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="8472f-133">Common/Console</span></span>                        | <span data-ttu-id="8472f-134">1.0</span><span class="sxs-lookup"><span data-stu-id="8472f-134">1.0</span></span>        |
| <span data-ttu-id="8472f-135">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="8472f-135">Class library</span></span>                                | [<span data-ttu-id="8472f-136">classlib</span><span class="sxs-lookup"><span data-stu-id="8472f-136">classlib</span></span>](#classlib)           | <span data-ttu-id="8472f-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8472f-137">[C#], F#, VB</span></span> | <span data-ttu-id="8472f-138">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="8472f-138">Common/Library</span></span>                        | <span data-ttu-id="8472f-139">1.0</span><span class="sxs-lookup"><span data-stu-id="8472f-139">1.0</span></span>        |
| <span data-ttu-id="8472f-140">Application WPF</span><span class="sxs-lookup"><span data-stu-id="8472f-140">WPF Application</span></span>                              | [<span data-ttu-id="8472f-141">WPF</span><span class="sxs-lookup"><span data-stu-id="8472f-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="8472f-142">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="8472f-142">[C#], VB</span></span>     | <span data-ttu-id="8472f-143">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="8472f-143">Common/WPF</span></span>                            | <span data-ttu-id="8472f-144">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="8472f-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8472f-145">Bibliothèque de classes WPF</span><span class="sxs-lookup"><span data-stu-id="8472f-145">WPF Class library</span></span>                            | [<span data-ttu-id="8472f-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="8472f-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="8472f-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="8472f-147">[C#], VB</span></span>     | <span data-ttu-id="8472f-148">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="8472f-148">Common/WPF</span></span>                            | <span data-ttu-id="8472f-149">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="8472f-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8472f-150">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="8472f-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="8472f-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="8472f-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="8472f-152">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="8472f-152">[C#], VB</span></span>     | <span data-ttu-id="8472f-153">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="8472f-153">Common/WPF</span></span>                            | <span data-ttu-id="8472f-154">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="8472f-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8472f-155">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="8472f-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="8472f-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="8472f-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="8472f-157">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="8472f-157">[C#], VB</span></span>     | <span data-ttu-id="8472f-158">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="8472f-158">Common/WPF</span></span>                            | <span data-ttu-id="8472f-159">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="8472f-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8472f-160">Application Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="8472f-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="8472f-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="8472f-161">winforms</span></span>](#winforms)           | <span data-ttu-id="8472f-162">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="8472f-162">[C#], VB</span></span>     | <span data-ttu-id="8472f-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="8472f-163">Common/WinForms</span></span>                       | <span data-ttu-id="8472f-164">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="8472f-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8472f-165">Bibliothèque de classes Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="8472f-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="8472f-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="8472f-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="8472f-167">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="8472f-167">[C#], VB</span></span>     | <span data-ttu-id="8472f-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="8472f-168">Common/WinForms</span></span>                       | <span data-ttu-id="8472f-169">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="8472f-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="8472f-170">Service Worker</span><span class="sxs-lookup"><span data-stu-id="8472f-170">Worker Service</span></span>                               | [<span data-ttu-id="8472f-171">collabor</span><span class="sxs-lookup"><span data-stu-id="8472f-171">worker</span></span>](#web-others)           | <span data-ttu-id="8472f-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-172">[C#]</span></span>         | <span data-ttu-id="8472f-173">Commun/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="8472f-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="8472f-174">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-174">3.0</span></span>        |
| <span data-ttu-id="8472f-175">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="8472f-175">Unit Test Project</span></span>                            | [<span data-ttu-id="8472f-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="8472f-176">mstest</span></span>](#test)                 | <span data-ttu-id="8472f-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8472f-177">[C#], F#, VB</span></span> | <span data-ttu-id="8472f-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="8472f-178">Test/MSTest</span></span>                           | <span data-ttu-id="8472f-179">1.0</span><span class="sxs-lookup"><span data-stu-id="8472f-179">1.0</span></span>        |
| <span data-ttu-id="8472f-180">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="8472f-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="8472f-181">nunit</span><span class="sxs-lookup"><span data-stu-id="8472f-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="8472f-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8472f-182">[C#], F#, VB</span></span> | <span data-ttu-id="8472f-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="8472f-183">Test/NUnit</span></span>                            | <span data-ttu-id="8472f-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="8472f-184">2.1.400</span></span>    |
| <span data-ttu-id="8472f-185">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="8472f-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="8472f-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8472f-186">[C#], F#, VB</span></span> | <span data-ttu-id="8472f-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="8472f-187">Test/NUnit</span></span>                            | <span data-ttu-id="8472f-188">2.2</span><span class="sxs-lookup"><span data-stu-id="8472f-188">2.2</span></span>        |
| <span data-ttu-id="8472f-189">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="8472f-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="8472f-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="8472f-190">xunit</span></span>](#test)                  | <span data-ttu-id="8472f-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8472f-191">[C#], F#, VB</span></span> | <span data-ttu-id="8472f-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="8472f-192">Test/xUnit</span></span>                            | <span data-ttu-id="8472f-193">1.0</span><span class="sxs-lookup"><span data-stu-id="8472f-193">1.0</span></span>        |
| <span data-ttu-id="8472f-194">Composant Razor</span><span class="sxs-lookup"><span data-stu-id="8472f-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="8472f-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-195">[C#]</span></span>         | <span data-ttu-id="8472f-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8472f-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="8472f-197">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-197">3.0</span></span>        |
| <span data-ttu-id="8472f-198">Page Razor</span><span class="sxs-lookup"><span data-stu-id="8472f-198">Razor Page</span></span>                                   | [<span data-ttu-id="8472f-199">page</span><span class="sxs-lookup"><span data-stu-id="8472f-199">page</span></span>](#page)                   | <span data-ttu-id="8472f-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-200">[C#]</span></span>         | <span data-ttu-id="8472f-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8472f-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="8472f-202">2.0</span><span class="sxs-lookup"><span data-stu-id="8472f-202">2.0</span></span>        |
| <span data-ttu-id="8472f-203">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="8472f-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="8472f-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="8472f-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="8472f-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-205">[C#]</span></span>         | <span data-ttu-id="8472f-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8472f-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="8472f-207">2.0</span><span class="sxs-lookup"><span data-stu-id="8472f-207">2.0</span></span>        |
| <span data-ttu-id="8472f-208">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="8472f-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="8472f-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-209">[C#]</span></span>         | <span data-ttu-id="8472f-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8472f-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="8472f-211">2.0</span><span class="sxs-lookup"><span data-stu-id="8472f-211">2.0</span></span>        |
| <span data-ttu-id="8472f-212">Blazor Application serveur</span><span class="sxs-lookup"><span data-stu-id="8472f-212">Blazor Server App</span></span>                            | [<span data-ttu-id="8472f-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="8472f-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="8472f-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-214">[C#]</span></span>         | <span data-ttu-id="8472f-215">InternetBlazor</span><span class="sxs-lookup"><span data-stu-id="8472f-215">Web/Blazor</span></span>                            | <span data-ttu-id="8472f-216">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-216">3.0</span></span>        |
| <span data-ttu-id="8472f-217">BlazorWebAssemblyApplication</span><span class="sxs-lookup"><span data-stu-id="8472f-217">Blazor WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="8472f-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-218">[C#]</span></span>         | <span data-ttu-id="8472f-219">InternetBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="8472f-219">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="8472f-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="8472f-220">3.1.300</span></span>    |
| <span data-ttu-id="8472f-221">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="8472f-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="8472f-222">web</span><span class="sxs-lookup"><span data-stu-id="8472f-222">web</span></span>](#web)                     | <span data-ttu-id="8472f-223">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8472f-223">[C#], F#</span></span>     | <span data-ttu-id="8472f-224">Web/vides</span><span class="sxs-lookup"><span data-stu-id="8472f-224">Web/Empty</span></span>                             | <span data-ttu-id="8472f-225">1.0</span><span class="sxs-lookup"><span data-stu-id="8472f-225">1.0</span></span>        |
| <span data-ttu-id="8472f-226">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="8472f-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="8472f-227">MVC</span><span class="sxs-lookup"><span data-stu-id="8472f-227">mvc</span></span>](#web-options)             | <span data-ttu-id="8472f-228">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8472f-228">[C#], F#</span></span>     | <span data-ttu-id="8472f-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="8472f-229">Web/MVC</span></span>                               | <span data-ttu-id="8472f-230">1.0</span><span class="sxs-lookup"><span data-stu-id="8472f-230">1.0</span></span>        |
| <span data-ttu-id="8472f-231">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8472f-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="8472f-232">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="8472f-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="8472f-233">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-233">[C#]</span></span>         | <span data-ttu-id="8472f-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="8472f-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="8472f-235">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="8472f-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="8472f-236">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="8472f-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="8472f-237">oblique</span><span class="sxs-lookup"><span data-stu-id="8472f-237">angular</span></span>](#spa)                 | <span data-ttu-id="8472f-238">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-238">[C#]</span></span>         | <span data-ttu-id="8472f-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="8472f-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="8472f-240">2.0</span><span class="sxs-lookup"><span data-stu-id="8472f-240">2.0</span></span>        |
| <span data-ttu-id="8472f-241">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="8472f-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="8472f-242">réagir</span><span class="sxs-lookup"><span data-stu-id="8472f-242">react</span></span>](#spa)                   | <span data-ttu-id="8472f-243">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-243">[C#]</span></span>         | <span data-ttu-id="8472f-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="8472f-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="8472f-245">2.0</span><span class="sxs-lookup"><span data-stu-id="8472f-245">2.0</span></span>        |
| <span data-ttu-id="8472f-246">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="8472f-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="8472f-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="8472f-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="8472f-248">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-248">[C#]</span></span>         | <span data-ttu-id="8472f-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="8472f-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="8472f-250">2.0</span><span class="sxs-lookup"><span data-stu-id="8472f-250">2.0</span></span>        |
| <span data-ttu-id="8472f-251">Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="8472f-251">Razor Class Library</span></span>                          | [<span data-ttu-id="8472f-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="8472f-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="8472f-253">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-253">[C#]</span></span>         | <span data-ttu-id="8472f-254">Web/Razor/Library/Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="8472f-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="8472f-255">2.1</span><span class="sxs-lookup"><span data-stu-id="8472f-255">2.1</span></span>        |
| <span data-ttu-id="8472f-256">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8472f-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="8472f-257">WebAPI</span><span class="sxs-lookup"><span data-stu-id="8472f-257">webapi</span></span>](#webapi)               | <span data-ttu-id="8472f-258">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8472f-258">[C#], F#</span></span>     | <span data-ttu-id="8472f-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="8472f-259">Web/WebAPI</span></span>                            | <span data-ttu-id="8472f-260">1.0</span><span class="sxs-lookup"><span data-stu-id="8472f-260">1.0</span></span>        |
| <span data-ttu-id="8472f-261">ASP.NET Core Service gRPC</span><span class="sxs-lookup"><span data-stu-id="8472f-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="8472f-262">GRPC</span><span class="sxs-lookup"><span data-stu-id="8472f-262">grpc</span></span>](#web-others)             | <span data-ttu-id="8472f-263">[C#]</span><span class="sxs-lookup"><span data-stu-id="8472f-263">[C#]</span></span>         | <span data-ttu-id="8472f-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="8472f-264">Web/gRPC</span></span>                              | <span data-ttu-id="8472f-265">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-265">3.0</span></span>        |
| <span data-ttu-id="8472f-266">fichier gitignore dotnet</span><span class="sxs-lookup"><span data-stu-id="8472f-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="8472f-267">Config</span><span class="sxs-lookup"><span data-stu-id="8472f-267">Config</span></span>                                | <span data-ttu-id="8472f-268">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-268">3.0</span></span>        |
| <span data-ttu-id="8472f-269">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="8472f-269">global.json file</span></span>                             | [<span data-ttu-id="8472f-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="8472f-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="8472f-271">Config</span><span class="sxs-lookup"><span data-stu-id="8472f-271">Config</span></span>                                | <span data-ttu-id="8472f-272">2.0</span><span class="sxs-lookup"><span data-stu-id="8472f-272">2.0</span></span>        |
| <span data-ttu-id="8472f-273">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="8472f-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="8472f-274">Config</span><span class="sxs-lookup"><span data-stu-id="8472f-274">Config</span></span>                                | <span data-ttu-id="8472f-275">1.0</span><span class="sxs-lookup"><span data-stu-id="8472f-275">1.0</span></span>        |
| <span data-ttu-id="8472f-276">Fichier manifeste de l’outil local dotnet</span><span class="sxs-lookup"><span data-stu-id="8472f-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="8472f-277">Config</span><span class="sxs-lookup"><span data-stu-id="8472f-277">Config</span></span>                                | <span data-ttu-id="8472f-278">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-278">3.0</span></span>        |
| <span data-ttu-id="8472f-279">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="8472f-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="8472f-280">Config</span><span class="sxs-lookup"><span data-stu-id="8472f-280">Config</span></span>                                | <span data-ttu-id="8472f-281">1.0</span><span class="sxs-lookup"><span data-stu-id="8472f-281">1.0</span></span>        |
| <span data-ttu-id="8472f-282">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="8472f-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="8472f-283">Solution</span><span class="sxs-lookup"><span data-stu-id="8472f-283">Solution</span></span>                              | <span data-ttu-id="8472f-284">1.0</span><span class="sxs-lookup"><span data-stu-id="8472f-284">1.0</span></span>        |
| <span data-ttu-id="8472f-285">Fichier de mémoire tampon de protocole</span><span class="sxs-lookup"><span data-stu-id="8472f-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="8472f-286">proto</span><span class="sxs-lookup"><span data-stu-id="8472f-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="8472f-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="8472f-287">Web/gRPC</span></span>                              | <span data-ttu-id="8472f-288">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="8472f-289">Options</span><span class="sxs-lookup"><span data-stu-id="8472f-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="8472f-290">Affiche un récapitulatif de ce qui se passerait si la commande donnée était exécutée (si cela donnerait lieu à la création d’un modèle).</span><span class="sxs-lookup"><span data-stu-id="8472f-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="8472f-291">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="8472f-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="8472f-292">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="8472f-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="8472f-293">Cela est obligatoire lorsque le modèle choisi remplace les fichiers existants dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="8472f-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="8472f-294">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="8472f-294">Prints out help for the command.</span></span> <span data-ttu-id="8472f-295">Elle peut être appelée pour la `dotnet new` commande elle-même ou pour n’importe quel modèle.</span><span class="sxs-lookup"><span data-stu-id="8472f-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="8472f-296">Par exemple : `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="8472f-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="8472f-297">Installe un pack de modèles à partir du `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="8472f-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="8472f-298">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="8472f-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="8472f-299">Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package.</span><span class="sxs-lookup"><span data-stu-id="8472f-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="8472f-300">Consultez un exemple dans la section [exemples](#examples) .</span><span class="sxs-lookup"><span data-stu-id="8472f-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="8472f-301">Si une version du modèle a déjà été installée lorsque vous exécutez cette commande, le modèle sera mis à jour vers la version spécifiée, ou vers la version stable la plus récente si aucune version n’a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8472f-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="8472f-302">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="8472f-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="8472f-303">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="8472f-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="8472f-304">Si aucun nom n’est spécifié, répertorie tous les modèles.</span><span class="sxs-lookup"><span data-stu-id="8472f-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="8472f-305">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="8472f-305">The language of the template to create.</span></span> <span data-ttu-id="8472f-306">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="8472f-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8472f-307">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="8472f-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="8472f-308">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="8472f-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="8472f-309">Dans ce cas, mettez la valeur du paramètre de langue entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="8472f-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="8472f-310">Par exemple : `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="8472f-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="8472f-311">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="8472f-311">The name for the created output.</span></span> <span data-ttu-id="8472f-312">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8472f-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="8472f-313">Spécifie une source NuGet à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="8472f-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="8472f-314">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="8472f-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="8472f-315">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="8472f-315">Location to place the generated output.</span></span> <span data-ttu-id="8472f-316">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="8472f-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="8472f-317">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="8472f-317">Filters templates based on available types.</span></span> <span data-ttu-id="8472f-318">Les valeurs prédéfinies sont `project` et `item` .</span><span class="sxs-lookup"><span data-stu-id="8472f-318">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="8472f-319">Désinstalle un pack de modèles au niveau de `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="8472f-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="8472f-320">Lorsque la `<PATH|NUGET_ID>` valeur n’est pas spécifiée, tous les packs de modèles actuellement installés et leurs modèles associés sont affichés.</span><span class="sxs-lookup"><span data-stu-id="8472f-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="8472f-321">Lorsque vous spécifiez `NUGET_ID` , n’incluez pas le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="8472f-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="8472f-322">Si vous ne spécifiez pas de paramètre pour cette option, la commande répertorie les modèles installés et fournit des détails à leur sujet.</span><span class="sxs-lookup"><span data-stu-id="8472f-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="8472f-323">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="8472f-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="8472f-324">Par exemple, *C:/Users/ \<USER> /documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionnera, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne le sera pas.</span><span class="sxs-lookup"><span data-stu-id="8472f-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="8472f-325">N’incluez pas de barre oblique finale de répertoire finale dans le chemin d’accès de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="8472f-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="8472f-326">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés et les installe.</span><span class="sxs-lookup"><span data-stu-id="8472f-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="8472f-327">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8472f-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="8472f-328">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="8472f-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="8472f-329">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8472f-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="8472f-330">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="8472f-330">Template options</span></span>

<span data-ttu-id="8472f-331">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="8472f-331">Each project template may have additional options available.</span></span> <span data-ttu-id="8472f-332">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="8472f-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="8472f-333">console</span><span class="sxs-lookup"><span data-stu-id="8472f-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8472f-334">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="8472f-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8472f-335">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8472f-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="8472f-336">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="8472f-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8472f-337">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="8472f-337">SDK version</span></span> | <span data-ttu-id="8472f-338">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8472f-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8472f-339">3.1</span><span class="sxs-lookup"><span data-stu-id="8472f-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8472f-340">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="8472f-341">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="8472f-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="8472f-342">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="8472f-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="8472f-343">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="8472f-343">Not supported for F#.</span></span> <span data-ttu-id="8472f-344">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="8472f-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8472f-345">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="8472f-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8472f-346">S’il est spécifié, n’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="8472f-347">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="8472f-347">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="8472f-348">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-348">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="8472f-349">classlib</span><span class="sxs-lookup"><span data-stu-id="8472f-349">classlib</span></span>

- <span data-ttu-id="8472f-350">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-350">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="8472f-351">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="8472f-351">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8472f-352">Valeurs : `netcoreapp<version>` pour créer une bibliothèque de classes .NET Core ou `netstandard<version>` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="8472f-352">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="8472f-353">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="8472f-353">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="8472f-354">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="8472f-354">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="8472f-355">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="8472f-355">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="8472f-356">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="8472f-356">Not supported for F#.</span></span> <span data-ttu-id="8472f-357">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="8472f-357">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8472f-358">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="8472f-358">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8472f-359">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-359">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8472f-360">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-360">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="8472f-361">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="8472f-361">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="8472f-362">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-362">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="8472f-363">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="8472f-363">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8472f-364">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="8472f-364">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="8472f-365">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="8472f-365">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="8472f-366">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="8472f-366">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="8472f-367">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="8472f-367">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="8472f-368">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="8472f-368">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8472f-369">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-369">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8472f-370">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-370">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="8472f-371">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="8472f-371">winforms, winformslib</span></span>

- <span data-ttu-id="8472f-372">_*`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-372">_*`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="8472f-373">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="8472f-373">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="8472f-374">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="8472f-374">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="8472f-375">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="8472f-375">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8472f-376">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-376">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8472f-377">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-377">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="8472f-378">Worker, GRPC</span><span class="sxs-lookup"><span data-stu-id="8472f-378">worker, grpc</span></span>

- <span data-ttu-id="8472f-379">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-379">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="8472f-380">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="8472f-380">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8472f-381">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="8472f-381">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="8472f-382">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="8472f-382">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="8472f-383">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="8472f-383">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="8472f-384">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-384">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8472f-385">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-385">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="8472f-386">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="8472f-386">mstest, xunit</span></span>

- <span data-ttu-id="8472f-387">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-387">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="8472f-388">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="8472f-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8472f-389">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="8472f-389">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="8472f-390">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="8472f-390">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8472f-391">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="8472f-391">SDK version</span></span> | <span data-ttu-id="8472f-392">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8472f-392">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8472f-393">3.1</span><span class="sxs-lookup"><span data-stu-id="8472f-393">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8472f-394">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-394">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="8472f-395">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="8472f-395">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8472f-396">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-396">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8472f-397">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-397">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="8472f-398">nunit</span><span class="sxs-lookup"><span data-stu-id="8472f-398">nunit</span></span>

- <span data-ttu-id="8472f-399">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-399">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="8472f-400">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="8472f-400">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="8472f-401">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="8472f-401">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8472f-402">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="8472f-402">SDK version</span></span> | <span data-ttu-id="8472f-403">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8472f-403">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8472f-404">3.1</span><span class="sxs-lookup"><span data-stu-id="8472f-404">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8472f-405">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-405">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="8472f-406">2.2</span><span class="sxs-lookup"><span data-stu-id="8472f-406">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="8472f-407">2.1</span><span class="sxs-lookup"><span data-stu-id="8472f-407">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="8472f-408">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="8472f-408">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="8472f-409">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-409">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8472f-410">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-410">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="8472f-411">page</span><span class="sxs-lookup"><span data-stu-id="8472f-411">page</span></span>

- <span data-ttu-id="8472f-412">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-412">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="8472f-413">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="8472f-413">Namespace for the generated code.</span></span> <span data-ttu-id="8472f-414">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="8472f-414">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="8472f-415">Crée la page sans PageModel.</span><span class="sxs-lookup"><span data-stu-id="8472f-415">Creates the page without a PageModel.</span></span>

<span data-ttu-id="8472f-416">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-416">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="8472f-417">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="8472f-417">viewimports, proto</span></span>

- <span data-ttu-id="8472f-418">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-418">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="8472f-419">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="8472f-419">Namespace for the generated code.</span></span> <span data-ttu-id="8472f-420">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="8472f-420">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="8472f-421">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-421">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="8472f-422">blazorserver</span><span class="sxs-lookup"><span data-stu-id="8472f-422">blazorserver</span></span>

- <span data-ttu-id="8472f-423">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-423">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="8472f-424">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8472f-424">The type of authentication to use.</span></span> <span data-ttu-id="8472f-425">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8472f-425">The possible values are:</span></span>

  - <span data-ttu-id="8472f-426">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="8472f-426">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="8472f-427">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="8472f-427">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="8472f-428">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="8472f-428">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="8472f-429">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="8472f-429">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="8472f-430">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="8472f-430">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="8472f-431">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="8472f-431">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="8472f-432">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="8472f-432">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8472f-433">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-433">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8472f-434">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="8472f-434">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="8472f-435">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-435">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8472f-436">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-436">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="8472f-437">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-437">The reset password policy ID for this project.</span></span> <span data-ttu-id="8472f-438">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-438">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="8472f-439">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-439">The edit profile policy ID for this project.</span></span> <span data-ttu-id="8472f-440">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-440">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="8472f-441">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="8472f-441">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8472f-442">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-442">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="8472f-443">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="8472f-443">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="8472f-444">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-444">The Client ID for this project.</span></span> <span data-ttu-id="8472f-445">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-445">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="8472f-446">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="8472f-446">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="8472f-447">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="8472f-447">The domain for the directory tenant.</span></span> <span data-ttu-id="8472f-448">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-448">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8472f-449">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="8472f-449">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="8472f-450">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="8472f-450">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8472f-451">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-451">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8472f-452">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="8472f-452">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="8472f-453">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="8472f-453">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="8472f-454">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-454">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8472f-455">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="8472f-455">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="8472f-456">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="8472f-456">Allows this application read-access to the directory.</span></span> <span data-ttu-id="8472f-457">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-457">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="8472f-458">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="8472f-458">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="8472f-459">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="8472f-459">Turns off HTTPS.</span></span> <span data-ttu-id="8472f-460">Cette option s’applique uniquement si `Individual` , `IndividualB2C` , `SingleOrg` ou `MultiOrg` ne sont pas utilisés pour `--auth` .</span><span class="sxs-lookup"><span data-stu-id="8472f-460">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="8472f-461">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8472f-461">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8472f-462">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-462">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="8472f-463">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-463">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8472f-464">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-464">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="8472f-465">web</span><span class="sxs-lookup"><span data-stu-id="8472f-465">web</span></span>

- <span data-ttu-id="8472f-466">_*`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-466">_*`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="8472f-467">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="8472f-467">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8472f-468">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="8472f-468">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8472f-469">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="8472f-469">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8472f-470">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="8472f-470">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8472f-471">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="8472f-471">SDK version</span></span> | <span data-ttu-id="8472f-472">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8472f-472">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8472f-473">3.1</span><span class="sxs-lookup"><span data-stu-id="8472f-473">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8472f-474">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-474">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="8472f-475">2.1</span><span class="sxs-lookup"><span data-stu-id="8472f-475">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="8472f-476">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-476">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="8472f-477">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="8472f-477">Turns off HTTPS.</span></span>

<span data-ttu-id="8472f-478">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-478">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="8472f-479">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="8472f-479">mvc, webapp</span></span>

- <span data-ttu-id="8472f-480">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-480">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="8472f-481">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8472f-481">The type of authentication to use.</span></span> <span data-ttu-id="8472f-482">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8472f-482">The possible values are:</span></span>

  - <span data-ttu-id="8472f-483">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="8472f-483">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="8472f-484">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="8472f-484">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="8472f-485">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="8472f-485">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="8472f-486">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="8472f-486">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="8472f-487">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="8472f-487">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="8472f-488">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="8472f-488">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="8472f-489">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="8472f-489">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8472f-490">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-490">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8472f-491">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="8472f-491">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="8472f-492">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-492">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8472f-493">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-493">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="8472f-494">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-494">The reset password policy ID for this project.</span></span> <span data-ttu-id="8472f-495">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-495">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="8472f-496">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-496">The edit profile policy ID for this project.</span></span> <span data-ttu-id="8472f-497">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-497">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="8472f-498">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="8472f-498">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8472f-499">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-499">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="8472f-500">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="8472f-500">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="8472f-501">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-501">The Client ID for this project.</span></span> <span data-ttu-id="8472f-502">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-502">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="8472f-503">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="8472f-503">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="8472f-504">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="8472f-504">The domain for the directory tenant.</span></span> <span data-ttu-id="8472f-505">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-505">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8472f-506">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="8472f-506">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="8472f-507">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="8472f-507">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8472f-508">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-508">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8472f-509">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="8472f-509">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="8472f-510">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="8472f-510">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="8472f-511">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-511">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8472f-512">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="8472f-512">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="8472f-513">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="8472f-513">Allows this application read-access to the directory.</span></span> <span data-ttu-id="8472f-514">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-514">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="8472f-515">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="8472f-515">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="8472f-516">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="8472f-516">Turns off HTTPS.</span></span> <span data-ttu-id="8472f-517">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="8472f-517">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="8472f-518">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8472f-518">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8472f-519">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-519">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8472f-520">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="8472f-520">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8472f-521">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="8472f-521">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="8472f-522">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="8472f-522">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8472f-523">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="8472f-523">SDK version</span></span> | <span data-ttu-id="8472f-524">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8472f-524">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8472f-525">3.1</span><span class="sxs-lookup"><span data-stu-id="8472f-525">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8472f-526">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-526">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="8472f-527">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-527">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="8472f-528">Comprend BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-528">Includes BrowserLink in the project.</span></span> <span data-ttu-id="8472f-529">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2 et 3,1.</span><span class="sxs-lookup"><span data-stu-id="8472f-529">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="8472f-530">Détermine si le projet est configuré pour utiliser la [compilation du runtime Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) dans les versions Debug.</span><span class="sxs-lookup"><span data-stu-id="8472f-530">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="8472f-531">Option disponible depuis le kit de développement logiciel (SDK) 3.1.201 .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8472f-531">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="8472f-532">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-532">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="8472f-533">angulaire, réaction</span><span class="sxs-lookup"><span data-stu-id="8472f-533">angular, react</span></span>

- <span data-ttu-id="8472f-534">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-534">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="8472f-535">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8472f-535">The type of authentication to use.</span></span> <span data-ttu-id="8472f-536">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8472f-536">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="8472f-537">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8472f-537">The possible values are:</span></span>

  - <span data-ttu-id="8472f-538">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="8472f-538">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="8472f-539">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="8472f-539">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="8472f-540">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="8472f-540">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="8472f-541">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="8472f-542">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="8472f-542">Turns off HTTPS.</span></span> <span data-ttu-id="8472f-543">Cette option s’applique uniquement si l’authentification est `None` .</span><span class="sxs-lookup"><span data-stu-id="8472f-543">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="8472f-544">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8472f-544">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8472f-545">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-545">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8472f-546">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8472f-546">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8472f-547">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="8472f-547">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8472f-548">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="8472f-548">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8472f-549">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="8472f-549">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8472f-550">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="8472f-550">SDK version</span></span> | <span data-ttu-id="8472f-551">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8472f-551">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8472f-552">3.1</span><span class="sxs-lookup"><span data-stu-id="8472f-552">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8472f-553">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-553">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="8472f-554">2.1</span><span class="sxs-lookup"><span data-stu-id="8472f-554">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="8472f-555">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-555">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="8472f-556">reactredux</span><span class="sxs-lookup"><span data-stu-id="8472f-556">reactredux</span></span>

- <span data-ttu-id="8472f-557">_*`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-557">_*`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="8472f-558">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="8472f-558">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8472f-559">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="8472f-559">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8472f-560">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="8472f-560">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8472f-561">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="8472f-561">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8472f-562">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="8472f-562">SDK version</span></span> | <span data-ttu-id="8472f-563">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8472f-563">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8472f-564">3.1</span><span class="sxs-lookup"><span data-stu-id="8472f-564">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8472f-565">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-565">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="8472f-566">2.1</span><span class="sxs-lookup"><span data-stu-id="8472f-566">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="8472f-567">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-567">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="8472f-568">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="8472f-568">Turns off HTTPS.</span></span>

<span data-ttu-id="8472f-569">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-569">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="8472f-570">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="8472f-570">razorclasslib</span></span>

- <span data-ttu-id="8472f-571">_*`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-571">_*`--no-restore`*\*</span></span>

  <span data-ttu-id="8472f-572">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-572">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="8472f-573">Prend en charge l’ajout de pages et de vues Razor traditionnelles en plus des composants de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="8472f-573">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="8472f-574">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8472f-574">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="8472f-575">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-575">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="8472f-576">webapi</span><span class="sxs-lookup"><span data-stu-id="8472f-576">webapi</span></span>

- <span data-ttu-id="8472f-577">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-577">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="8472f-578">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8472f-578">The type of authentication to use.</span></span> <span data-ttu-id="8472f-579">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8472f-579">The possible values are:</span></span>

  - <span data-ttu-id="8472f-580">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="8472f-580">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="8472f-581">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="8472f-581">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="8472f-582">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="8472f-582">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="8472f-583">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="8472f-583">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="8472f-584">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="8472f-584">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8472f-585">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-585">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8472f-586">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="8472f-586">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="8472f-587">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-587">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8472f-588">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8472f-588">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="8472f-589">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="8472f-589">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8472f-590">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-590">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8472f-591">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="8472f-591">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="8472f-592">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-592">The Client ID for this project.</span></span> <span data-ttu-id="8472f-593">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-593">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="8472f-594">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="8472f-594">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="8472f-595">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="8472f-595">The domain for the directory tenant.</span></span> <span data-ttu-id="8472f-596">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-596">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="8472f-597">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="8472f-597">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="8472f-598">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="8472f-598">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8472f-599">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8472f-599">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8472f-600">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="8472f-600">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="8472f-601">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="8472f-601">Allows this application read-access to the directory.</span></span> <span data-ttu-id="8472f-602">S’applique uniquement à `SingleOrg` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="8472f-602">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="8472f-603">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="8472f-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="8472f-604">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="8472f-604">Turns off HTTPS.</span></span> <span data-ttu-id="8472f-605">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="8472f-605">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="8472f-606">Cette option s’applique uniquement si `IndividualB2C` ou `SingleOrg` ne sont pas utilisés pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="8472f-606">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="8472f-607">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8472f-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8472f-608">S’applique uniquement à `IndividualB2C` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="8472f-608">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8472f-609">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="8472f-609">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8472f-610">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="8472f-610">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="8472f-611">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="8472f-611">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="8472f-612">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="8472f-612">SDK version</span></span> | <span data-ttu-id="8472f-613">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8472f-613">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="8472f-614">3.1</span><span class="sxs-lookup"><span data-stu-id="8472f-614">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="8472f-615">3.0</span><span class="sxs-lookup"><span data-stu-id="8472f-615">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="8472f-616">2.1</span><span class="sxs-lookup"><span data-stu-id="8472f-616">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="8472f-617">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="8472f-617">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8472f-618">\*\*_</span><span class="sxs-lookup"><span data-stu-id="8472f-618">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="8472f-619">globaljson</span><span class="sxs-lookup"><span data-stu-id="8472f-619">globaljson</span></span>

- <span data-ttu-id="8472f-620">_*`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="8472f-620">_*`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="8472f-621">Spécifie la version de la kit SDK .NET Core à utiliser dans le fichier *global.js* .</span><span class="sxs-lookup"><span data-stu-id="8472f-621">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="8472f-622">Exemples</span><span class="sxs-lookup"><span data-stu-id="8472f-622">Examples</span></span>

- <span data-ttu-id="8472f-623">Créez un projet d’application console C# en spécifiant le nom du modèle :</span><span class="sxs-lookup"><span data-stu-id="8472f-623">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="8472f-624">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="8472f-624">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="8472f-625">Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié :</span><span class="sxs-lookup"><span data-stu-id="8472f-625">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="8472f-626">Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :</span><span class="sxs-lookup"><span data-stu-id="8472f-626">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="8472f-627">Créez un projet xUnit :</span><span class="sxs-lookup"><span data-stu-id="8472f-627">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="8472f-628">Répertorier tous les modèles disponibles pour les modèles d’application à page unique (SPA) :</span><span class="sxs-lookup"><span data-stu-id="8472f-628">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="8472f-629">Liste de tous les modèles correspondant à la sous-chaîne *we*.</span><span class="sxs-lookup"><span data-stu-id="8472f-629">List all templates matching the *we* substring.</span></span> <span data-ttu-id="8472f-630">Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.</span><span class="sxs-lookup"><span data-stu-id="8472f-630">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="8472f-631">Tentative d’appel du modèle correspondant à *ng*.</span><span class="sxs-lookup"><span data-stu-id="8472f-631">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="8472f-632">Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.</span><span class="sxs-lookup"><span data-stu-id="8472f-632">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="8472f-633">Installez la version 2,0 des modèles SPA pour ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="8472f-633">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="8472f-634">Répertoriez les modèles installés et les détails les concernant, notamment comment les désinstaller :</span><span class="sxs-lookup"><span data-stu-id="8472f-634">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="8472f-635">Créez un *global.js* dans le répertoire actif en définissant la version du kit de développement logiciel (SDK) sur 3.1.101 :</span><span class="sxs-lookup"><span data-stu-id="8472f-635">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="8472f-636">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8472f-636">See also</span></span>

- [<span data-ttu-id="8472f-637">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="8472f-637">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="8472f-638">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="8472f-638">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="8472f-639">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="8472f-639">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="8472f-640">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="8472f-640">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
