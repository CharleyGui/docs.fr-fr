---
title: Commande dotnet new
description: La commande dotnet New crée de nouveaux projets .NET basés sur le modèle spécifié.
no-loc:
- 'Blazor'
- 'WebAssembly'
ms.date: 09/04/2020
ms.openlocfilehash: 3ee644f05ea5929ffc7b11054ef1d974b811f418
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634453"
---
# <a name="dotnet-new"></a><span data-ttu-id="e061c-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="e061c-103">dotnet new</span></span>

<span data-ttu-id="e061c-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="e061c-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e061c-105">Name</span><span class="sxs-lookup"><span data-stu-id="e061c-105">Name</span></span>

<span data-ttu-id="e061c-106">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="e061c-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e061c-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="e061c-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="e061c-108">Description</span><span class="sxs-lookup"><span data-stu-id="e061c-108">Description</span></span>

<span data-ttu-id="e061c-109">La `dotnet new` commande crée un projet .net ou d’autres artefacts basés sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="e061c-109">The `dotnet new` command creates a .NET project or other artifacts based on a template.</span></span>

<span data-ttu-id="e061c-110">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="e061c-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="e061c-111">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="e061c-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="e061c-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="e061c-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="e061c-113">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="e061c-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="e061c-114">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="e061c-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="e061c-115">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="e061c-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="e061c-116">Vous pouvez exécuter `dotnet new --list` ou `dotnet new -l` pour afficher la liste de tous les modèles installés.</span><span class="sxs-lookup"><span data-stu-id="e061c-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="e061c-117">Si la `TEMPLATE` valeur ne correspond pas exactement au texte de la colonne **Templates** ou **Short Name** de la table retournée, une correspondance de sous-chaînes est effectuée sur ces deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="e061c-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="e061c-118">À compter du kit de développement logiciel (SDK) .NET Core 3,0, l’interface CLI recherche des modèles dans NuGet.org quand vous appelez la `dotnet new` commande dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e061c-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="e061c-119">Si l’interface CLI ne peut pas trouver de correspondance de modèle lors de l’appel `dotnet new` de, pas encore partiel.</span><span class="sxs-lookup"><span data-stu-id="e061c-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="e061c-120">Si une version plus récente du modèle est disponible.</span><span class="sxs-lookup"><span data-stu-id="e061c-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="e061c-121">Dans ce cas, le projet ou l’artefact est créé, mais l’interface CLI vous avertit d’une version mise à jour du modèle.</span><span class="sxs-lookup"><span data-stu-id="e061c-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="e061c-122">Le tableau suivant présente les modèles qui sont préinstallés avec le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="e061c-122">The following table shows the templates that come pre-installed with the .NET SDK.</span></span> <span data-ttu-id="e061c-123">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="e061c-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="e061c-124">Cliquez sur le lien nom abrégé pour afficher les options de modèle spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e061c-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="e061c-125">Modèles</span><span class="sxs-lookup"><span data-stu-id="e061c-125">Templates</span></span>                                    | <span data-ttu-id="e061c-126">Nom court</span><span class="sxs-lookup"><span data-stu-id="e061c-126">Short name</span></span>                      | <span data-ttu-id="e061c-127">Langage</span><span class="sxs-lookup"><span data-stu-id="e061c-127">Language</span></span>     | <span data-ttu-id="e061c-128">Étiquettes</span><span class="sxs-lookup"><span data-stu-id="e061c-128">Tags</span></span>                                  | <span data-ttu-id="e061c-129">Introduit</span><span class="sxs-lookup"><span data-stu-id="e061c-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="e061c-130">Application console</span><span class="sxs-lookup"><span data-stu-id="e061c-130">Console Application</span></span>                          | [<span data-ttu-id="e061c-131">console</span><span class="sxs-lookup"><span data-stu-id="e061c-131">console</span></span>](#console)             | <span data-ttu-id="e061c-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e061c-132">[C#], F#, VB</span></span> | <span data-ttu-id="e061c-133">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="e061c-133">Common/Console</span></span>                        | <span data-ttu-id="e061c-134">1.0</span><span class="sxs-lookup"><span data-stu-id="e061c-134">1.0</span></span>        |
| <span data-ttu-id="e061c-135">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="e061c-135">Class library</span></span>                                | [<span data-ttu-id="e061c-136">classlib</span><span class="sxs-lookup"><span data-stu-id="e061c-136">classlib</span></span>](#classlib)           | <span data-ttu-id="e061c-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e061c-137">[C#], F#, VB</span></span> | <span data-ttu-id="e061c-138">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="e061c-138">Common/Library</span></span>                        | <span data-ttu-id="e061c-139">1.0</span><span class="sxs-lookup"><span data-stu-id="e061c-139">1.0</span></span>        |
| <span data-ttu-id="e061c-140">Application WPF</span><span class="sxs-lookup"><span data-stu-id="e061c-140">WPF Application</span></span>                              | [<span data-ttu-id="e061c-141">WPF</span><span class="sxs-lookup"><span data-stu-id="e061c-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="e061c-142">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e061c-142">[C#], VB</span></span>     | <span data-ttu-id="e061c-143">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="e061c-143">Common/WPF</span></span>                            | <span data-ttu-id="e061c-144">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e061c-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e061c-145">Bibliothèque de classes WPF</span><span class="sxs-lookup"><span data-stu-id="e061c-145">WPF Class library</span></span>                            | [<span data-ttu-id="e061c-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="e061c-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="e061c-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e061c-147">[C#], VB</span></span>     | <span data-ttu-id="e061c-148">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="e061c-148">Common/WPF</span></span>                            | <span data-ttu-id="e061c-149">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e061c-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e061c-150">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="e061c-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="e061c-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="e061c-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="e061c-152">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e061c-152">[C#], VB</span></span>     | <span data-ttu-id="e061c-153">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="e061c-153">Common/WPF</span></span>                            | <span data-ttu-id="e061c-154">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e061c-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e061c-155">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="e061c-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="e061c-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="e061c-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="e061c-157">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e061c-157">[C#], VB</span></span>     | <span data-ttu-id="e061c-158">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="e061c-158">Common/WPF</span></span>                            | <span data-ttu-id="e061c-159">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e061c-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e061c-160">Application Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e061c-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="e061c-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="e061c-161">winforms</span></span>](#winforms)           | <span data-ttu-id="e061c-162">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e061c-162">[C#], VB</span></span>     | <span data-ttu-id="e061c-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="e061c-163">Common/WinForms</span></span>                       | <span data-ttu-id="e061c-164">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e061c-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e061c-165">Bibliothèque de classes Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e061c-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="e061c-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="e061c-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="e061c-167">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e061c-167">[C#], VB</span></span>     | <span data-ttu-id="e061c-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="e061c-168">Common/WinForms</span></span>                       | <span data-ttu-id="e061c-169">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e061c-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e061c-170">Service Worker</span><span class="sxs-lookup"><span data-stu-id="e061c-170">Worker Service</span></span>                               | [<span data-ttu-id="e061c-171">collabor</span><span class="sxs-lookup"><span data-stu-id="e061c-171">worker</span></span>](#web-others)           | <span data-ttu-id="e061c-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-172">[C#]</span></span>         | <span data-ttu-id="e061c-173">Commun/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="e061c-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="e061c-174">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-174">3.0</span></span>        |
| <span data-ttu-id="e061c-175">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="e061c-175">Unit Test Project</span></span>                            | [<span data-ttu-id="e061c-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="e061c-176">mstest</span></span>](#test)                 | <span data-ttu-id="e061c-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e061c-177">[C#], F#, VB</span></span> | <span data-ttu-id="e061c-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="e061c-178">Test/MSTest</span></span>                           | <span data-ttu-id="e061c-179">1.0</span><span class="sxs-lookup"><span data-stu-id="e061c-179">1.0</span></span>        |
| <span data-ttu-id="e061c-180">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="e061c-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="e061c-181">nunit</span><span class="sxs-lookup"><span data-stu-id="e061c-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="e061c-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e061c-182">[C#], F#, VB</span></span> | <span data-ttu-id="e061c-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="e061c-183">Test/NUnit</span></span>                            | <span data-ttu-id="e061c-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="e061c-184">2.1.400</span></span>    |
| <span data-ttu-id="e061c-185">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="e061c-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="e061c-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e061c-186">[C#], F#, VB</span></span> | <span data-ttu-id="e061c-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="e061c-187">Test/NUnit</span></span>                            | <span data-ttu-id="e061c-188">2.2</span><span class="sxs-lookup"><span data-stu-id="e061c-188">2.2</span></span>        |
| <span data-ttu-id="e061c-189">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="e061c-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="e061c-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="e061c-190">xunit</span></span>](#test)                  | <span data-ttu-id="e061c-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e061c-191">[C#], F#, VB</span></span> | <span data-ttu-id="e061c-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="e061c-192">Test/xUnit</span></span>                            | <span data-ttu-id="e061c-193">1.0</span><span class="sxs-lookup"><span data-stu-id="e061c-193">1.0</span></span>        |
| <span data-ttu-id="e061c-194">Composant Razor</span><span class="sxs-lookup"><span data-stu-id="e061c-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="e061c-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-195">[C#]</span></span>         | <span data-ttu-id="e061c-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e061c-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="e061c-197">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-197">3.0</span></span>        |
| <span data-ttu-id="e061c-198">Page Razor</span><span class="sxs-lookup"><span data-stu-id="e061c-198">Razor Page</span></span>                                   | [<span data-ttu-id="e061c-199">page</span><span class="sxs-lookup"><span data-stu-id="e061c-199">page</span></span>](#page)                   | <span data-ttu-id="e061c-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-200">[C#]</span></span>         | <span data-ttu-id="e061c-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e061c-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="e061c-202">2.0</span><span class="sxs-lookup"><span data-stu-id="e061c-202">2.0</span></span>        |
| <span data-ttu-id="e061c-203">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="e061c-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="e061c-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="e061c-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="e061c-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-205">[C#]</span></span>         | <span data-ttu-id="e061c-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e061c-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="e061c-207">2.0</span><span class="sxs-lookup"><span data-stu-id="e061c-207">2.0</span></span>        |
| <span data-ttu-id="e061c-208">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="e061c-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="e061c-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-209">[C#]</span></span>         | <span data-ttu-id="e061c-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e061c-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="e061c-211">2.0</span><span class="sxs-lookup"><span data-stu-id="e061c-211">2.0</span></span>        |
| <span data-ttu-id="e061c-212">Blazor Application serveur</span><span class="sxs-lookup"><span data-stu-id="e061c-212">Blazor Server App</span></span>                            | [<span data-ttu-id="e061c-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="e061c-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="e061c-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-214">[C#]</span></span>         | <span data-ttu-id="e061c-215">InternetBlazor</span><span class="sxs-lookup"><span data-stu-id="e061c-215">Web/Blazor</span></span>                            | <span data-ttu-id="e061c-216">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-216">3.0</span></span>        |
| <span data-ttu-id="e061c-217">BlazorWebAssemblyApplication</span><span class="sxs-lookup"><span data-stu-id="e061c-217">Blazor WebAssembly App</span></span>                       | [<span data-ttu-id="e061c-218">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="e061c-218">blazorwasm</span></span>](#blazorwasm)       | <span data-ttu-id="e061c-219">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-219">[C#]</span></span>         | <span data-ttu-id="e061c-220">InternetBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="e061c-220">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="e061c-221">3.1.300</span><span class="sxs-lookup"><span data-stu-id="e061c-221">3.1.300</span></span>    |
| <span data-ttu-id="e061c-222">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="e061c-222">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="e061c-223">web</span><span class="sxs-lookup"><span data-stu-id="e061c-223">web</span></span>](#web)                     | <span data-ttu-id="e061c-224">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e061c-224">[C#], F#</span></span>     | <span data-ttu-id="e061c-225">Web/vides</span><span class="sxs-lookup"><span data-stu-id="e061c-225">Web/Empty</span></span>                             | <span data-ttu-id="e061c-226">1.0</span><span class="sxs-lookup"><span data-stu-id="e061c-226">1.0</span></span>        |
| <span data-ttu-id="e061c-227">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="e061c-227">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="e061c-228">MVC</span><span class="sxs-lookup"><span data-stu-id="e061c-228">mvc</span></span>](#web-options)             | <span data-ttu-id="e061c-229">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e061c-229">[C#], F#</span></span>     | <span data-ttu-id="e061c-230">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="e061c-230">Web/MVC</span></span>                               | <span data-ttu-id="e061c-231">1.0</span><span class="sxs-lookup"><span data-stu-id="e061c-231">1.0</span></span>        |
| <span data-ttu-id="e061c-232">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e061c-232">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="e061c-233">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="e061c-233">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="e061c-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-234">[C#]</span></span>         | <span data-ttu-id="e061c-235">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="e061c-235">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="e061c-236">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="e061c-236">2.2, 2.0</span></span>   |
| <span data-ttu-id="e061c-237">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="e061c-237">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="e061c-238">oblique</span><span class="sxs-lookup"><span data-stu-id="e061c-238">angular</span></span>](#spa)                 | <span data-ttu-id="e061c-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-239">[C#]</span></span>         | <span data-ttu-id="e061c-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="e061c-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e061c-241">2.0</span><span class="sxs-lookup"><span data-stu-id="e061c-241">2.0</span></span>        |
| <span data-ttu-id="e061c-242">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="e061c-242">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="e061c-243">réagir</span><span class="sxs-lookup"><span data-stu-id="e061c-243">react</span></span>](#spa)                   | <span data-ttu-id="e061c-244">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-244">[C#]</span></span>         | <span data-ttu-id="e061c-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="e061c-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e061c-246">2.0</span><span class="sxs-lookup"><span data-stu-id="e061c-246">2.0</span></span>        |
| <span data-ttu-id="e061c-247">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="e061c-247">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="e061c-248">reactredux</span><span class="sxs-lookup"><span data-stu-id="e061c-248">reactredux</span></span>](#reactredux)       | <span data-ttu-id="e061c-249">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-249">[C#]</span></span>         | <span data-ttu-id="e061c-250">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="e061c-250">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e061c-251">2.0</span><span class="sxs-lookup"><span data-stu-id="e061c-251">2.0</span></span>        |
| <span data-ttu-id="e061c-252">Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="e061c-252">Razor Class Library</span></span>                          | [<span data-ttu-id="e061c-253">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="e061c-253">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="e061c-254">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-254">[C#]</span></span>         | <span data-ttu-id="e061c-255">Web/Razor/Library/Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="e061c-255">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="e061c-256">2.1</span><span class="sxs-lookup"><span data-stu-id="e061c-256">2.1</span></span>        |
| <span data-ttu-id="e061c-257">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e061c-257">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="e061c-258">WebAPI</span><span class="sxs-lookup"><span data-stu-id="e061c-258">webapi</span></span>](#webapi)               | <span data-ttu-id="e061c-259">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e061c-259">[C#], F#</span></span>     | <span data-ttu-id="e061c-260">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="e061c-260">Web/WebAPI</span></span>                            | <span data-ttu-id="e061c-261">1.0</span><span class="sxs-lookup"><span data-stu-id="e061c-261">1.0</span></span>        |
| <span data-ttu-id="e061c-262">ASP.NET Core Service gRPC</span><span class="sxs-lookup"><span data-stu-id="e061c-262">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="e061c-263">GRPC</span><span class="sxs-lookup"><span data-stu-id="e061c-263">grpc</span></span>](#web-others)             | <span data-ttu-id="e061c-264">[C#]</span><span class="sxs-lookup"><span data-stu-id="e061c-264">[C#]</span></span>         | <span data-ttu-id="e061c-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="e061c-265">Web/gRPC</span></span>                              | <span data-ttu-id="e061c-266">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-266">3.0</span></span>        |
| <span data-ttu-id="e061c-267">fichier gitignore dotnet</span><span class="sxs-lookup"><span data-stu-id="e061c-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="e061c-268">Config</span><span class="sxs-lookup"><span data-stu-id="e061c-268">Config</span></span>                                | <span data-ttu-id="e061c-269">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-269">3.0</span></span>        |
| <span data-ttu-id="e061c-270">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="e061c-270">global.json file</span></span>                             | [<span data-ttu-id="e061c-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="e061c-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="e061c-272">Config</span><span class="sxs-lookup"><span data-stu-id="e061c-272">Config</span></span>                                | <span data-ttu-id="e061c-273">2.0</span><span class="sxs-lookup"><span data-stu-id="e061c-273">2.0</span></span>        |
| <span data-ttu-id="e061c-274">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="e061c-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="e061c-275">Config</span><span class="sxs-lookup"><span data-stu-id="e061c-275">Config</span></span>                                | <span data-ttu-id="e061c-276">1.0</span><span class="sxs-lookup"><span data-stu-id="e061c-276">1.0</span></span>        |
| <span data-ttu-id="e061c-277">Fichier manifeste de l’outil local dotnet</span><span class="sxs-lookup"><span data-stu-id="e061c-277">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="e061c-278">Config</span><span class="sxs-lookup"><span data-stu-id="e061c-278">Config</span></span>                                | <span data-ttu-id="e061c-279">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-279">3.0</span></span>        |
| <span data-ttu-id="e061c-280">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="e061c-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="e061c-281">Config</span><span class="sxs-lookup"><span data-stu-id="e061c-281">Config</span></span>                                | <span data-ttu-id="e061c-282">1.0</span><span class="sxs-lookup"><span data-stu-id="e061c-282">1.0</span></span>        |
| <span data-ttu-id="e061c-283">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="e061c-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="e061c-284">Solution</span><span class="sxs-lookup"><span data-stu-id="e061c-284">Solution</span></span>                              | <span data-ttu-id="e061c-285">1.0</span><span class="sxs-lookup"><span data-stu-id="e061c-285">1.0</span></span>        |
| <span data-ttu-id="e061c-286">Fichier de mémoire tampon de protocole</span><span class="sxs-lookup"><span data-stu-id="e061c-286">Protocol Buffer File</span></span>                         | [<span data-ttu-id="e061c-287">proto</span><span class="sxs-lookup"><span data-stu-id="e061c-287">proto</span></span>](#namespace)             |              | <span data-ttu-id="e061c-288">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="e061c-288">Web/gRPC</span></span>                              | <span data-ttu-id="e061c-289">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-289">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="e061c-290">Options</span><span class="sxs-lookup"><span data-stu-id="e061c-290">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="e061c-291">Affiche un récapitulatif de ce qui se passerait si la commande donnée était exécutée (si cela donnerait lieu à la création d’un modèle).</span><span class="sxs-lookup"><span data-stu-id="e061c-291">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="e061c-292">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e061c-292">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="e061c-293">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="e061c-293">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="e061c-294">Cela est obligatoire lorsque le modèle choisi remplace les fichiers existants dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="e061c-294">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e061c-295">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="e061c-295">Prints out help for the command.</span></span> <span data-ttu-id="e061c-296">Elle peut être appelée pour la `dotnet new` commande elle-même ou pour n’importe quel modèle.</span><span class="sxs-lookup"><span data-stu-id="e061c-296">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="e061c-297">Par exemple : `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="e061c-297">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="e061c-298">Installe un pack de modèles à partir du `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="e061c-298">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="e061c-299">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="e061c-299">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="e061c-300">Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package.</span><span class="sxs-lookup"><span data-stu-id="e061c-300">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="e061c-301">Consultez un exemple dans la section [exemples](#examples) .</span><span class="sxs-lookup"><span data-stu-id="e061c-301">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="e061c-302">Si une version du modèle a déjà été installée lorsque vous exécutez cette commande, le modèle sera mis à jour vers la version spécifiée, ou vers la version stable la plus récente si aucune version n’a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e061c-302">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="e061c-303">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="e061c-303">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="e061c-304">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="e061c-304">Lists templates containing the specified name.</span></span> <span data-ttu-id="e061c-305">Si aucun nom n’est spécifié, répertorie tous les modèles.</span><span class="sxs-lookup"><span data-stu-id="e061c-305">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="e061c-306">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="e061c-306">The language of the template to create.</span></span> <span data-ttu-id="e061c-307">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="e061c-307">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="e061c-308">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="e061c-308">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e061c-309">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="e061c-309">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="e061c-310">Dans ce cas, mettez la valeur du paramètre de langue entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="e061c-310">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="e061c-311">Par exemple : `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="e061c-311">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="e061c-312">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="e061c-312">The name for the created output.</span></span> <span data-ttu-id="e061c-313">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e061c-313">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="e061c-314">Spécifie une source NuGet à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="e061c-314">Specifies a NuGet source to use during install.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e061c-315">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="e061c-315">Location to place the generated output.</span></span> <span data-ttu-id="e061c-316">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="e061c-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="e061c-317">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="e061c-317">Filters templates based on available types.</span></span> <span data-ttu-id="e061c-318">Les valeurs prédéfinies sont `project` et `item` .</span><span class="sxs-lookup"><span data-stu-id="e061c-318">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="e061c-319">Désinstalle un pack de modèles au niveau de `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="e061c-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="e061c-320">Lorsque la `<PATH|NUGET_ID>` valeur n’est pas spécifiée, tous les packs de modèles actuellement installés et leurs modèles associés sont affichés.</span><span class="sxs-lookup"><span data-stu-id="e061c-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="e061c-321">Lorsque vous spécifiez `NUGET_ID` , n’incluez pas le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="e061c-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="e061c-322">Si vous ne spécifiez pas de paramètre pour cette option, la commande répertorie les modèles installés et fournit des détails à leur sujet.</span><span class="sxs-lookup"><span data-stu-id="e061c-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e061c-323">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="e061c-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="e061c-324">Par exemple, *C:/Users/ \<USER> /documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionnera, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne le sera pas.</span><span class="sxs-lookup"><span data-stu-id="e061c-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="e061c-325">N’incluez pas de barre oblique finale de répertoire finale dans le chemin d’accès de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="e061c-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="e061c-326">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés et les installe.</span><span class="sxs-lookup"><span data-stu-id="e061c-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="e061c-327">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e061c-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="e061c-328">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="e061c-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="e061c-329">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e061c-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="e061c-330">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="e061c-330">Template options</span></span>

<span data-ttu-id="e061c-331">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="e061c-331">Each project template may have additional options available.</span></span> <span data-ttu-id="e061c-332">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="e061c-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="e061c-333">console</span><span class="sxs-lookup"><span data-stu-id="e061c-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e061c-334">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e061c-335">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e061c-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e061c-336">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e061c-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e061c-337">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e061c-337">SDK version</span></span> | <span data-ttu-id="e061c-338">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e061c-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e061c-339">5.0</span><span class="sxs-lookup"><span data-stu-id="e061c-339">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e061c-340">3.1</span><span class="sxs-lookup"><span data-stu-id="e061c-340">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e061c-341">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-341">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e061c-342">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="e061c-342">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e061c-343">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e061c-343">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="e061c-344">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="e061c-344">Not supported for F#.</span></span> <span data-ttu-id="e061c-345">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e061c-345">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e061c-346">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e061c-346">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e061c-347">S’il est spécifié, n’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-347">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="e061c-348">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e061c-348">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="e061c-349">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-349">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="e061c-350">classlib</span><span class="sxs-lookup"><span data-stu-id="e061c-350">classlib</span></span>

- <span data-ttu-id="e061c-351">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-351">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e061c-352">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-352">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e061c-353">Valeurs : `net5.0` ou `netcoreapp<version>` pour créer une bibliothèque de classes .net ou `netstandard<version>` pour créer une bibliothèque de classes .NET standard.</span><span class="sxs-lookup"><span data-stu-id="e061c-353">Values: `net5.0` or `netcoreapp<version>` to create a .NET Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="e061c-354">La valeur par défaut pour le kit de développement logiciel (SDK) .NET 5,0 est `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="e061c-354">The default value for .NET 5.0 SDK is `net5.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e061c-355">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="e061c-355">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e061c-356">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e061c-356">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="e061c-357">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="e061c-357">Not supported for F#.</span></span> <span data-ttu-id="e061c-358">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e061c-358">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e061c-359">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e061c-359">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e061c-360">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-360">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e061c-361">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-361">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="e061c-362">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="e061c-362">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="e061c-363">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-363">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e061c-364">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-364">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e061c-365">La valeur par défaut est `net5.0`.</span><span class="sxs-lookup"><span data-stu-id="e061c-365">The default value is `net5.0`.</span></span> <span data-ttu-id="e061c-366">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="e061c-366">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e061c-367">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="e061c-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e061c-368">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e061c-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="e061c-369">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e061c-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e061c-370">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-370">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e061c-371">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-371">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="e061c-372">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="e061c-372">winforms, winformslib</span></span>

- <span data-ttu-id="e061c-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="e061c-374">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="e061c-374">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e061c-375">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e061c-375">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="e061c-376">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e061c-376">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e061c-377">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-377">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e061c-378">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-378">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="e061c-379">Worker, GRPC</span><span class="sxs-lookup"><span data-stu-id="e061c-379">worker, grpc</span></span>

- <span data-ttu-id="e061c-380">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-380">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e061c-381">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-381">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e061c-382">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="e061c-382">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="e061c-383">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="e061c-383">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e061c-384">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e061c-384">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e061c-385">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-385">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e061c-386">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-386">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="e061c-387">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="e061c-387">mstest, xunit</span></span>

- <span data-ttu-id="e061c-388">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-388">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e061c-389">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-389">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e061c-390">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e061c-390">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e061c-391">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e061c-391">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e061c-392">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e061c-392">SDK version</span></span> | <span data-ttu-id="e061c-393">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e061c-393">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e061c-394">5.0</span><span class="sxs-lookup"><span data-stu-id="e061c-394">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e061c-395">3.1</span><span class="sxs-lookup"><span data-stu-id="e061c-395">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e061c-396">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-396">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="e061c-397">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="e061c-397">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e061c-398">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-398">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e061c-399">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-399">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="e061c-400">nunit</span><span class="sxs-lookup"><span data-stu-id="e061c-400">nunit</span></span>

- <span data-ttu-id="e061c-401">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-401">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e061c-402">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-402">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="e061c-403">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e061c-403">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e061c-404">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e061c-404">SDK version</span></span> | <span data-ttu-id="e061c-405">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e061c-405">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e061c-406">5.0</span><span class="sxs-lookup"><span data-stu-id="e061c-406">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e061c-407">3.1</span><span class="sxs-lookup"><span data-stu-id="e061c-407">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e061c-408">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-408">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e061c-409">2.2</span><span class="sxs-lookup"><span data-stu-id="e061c-409">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="e061c-410">2.1</span><span class="sxs-lookup"><span data-stu-id="e061c-410">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="e061c-411">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="e061c-411">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e061c-412">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-412">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e061c-413">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-413">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="e061c-414">page</span><span class="sxs-lookup"><span data-stu-id="e061c-414">page</span></span>

- <span data-ttu-id="e061c-415">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-415">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="e061c-416">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="e061c-416">Namespace for the generated code.</span></span> <span data-ttu-id="e061c-417">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="e061c-417">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="e061c-418">Crée la page sans PageModel.</span><span class="sxs-lookup"><span data-stu-id="e061c-418">Creates the page without a PageModel.</span></span>

<span data-ttu-id="e061c-419">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-419">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="e061c-420">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="e061c-420">viewimports, proto</span></span>

- <span data-ttu-id="e061c-421">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-421">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="e061c-422">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="e061c-422">Namespace for the generated code.</span></span> <span data-ttu-id="e061c-423">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="e061c-423">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="e061c-424">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-424">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="e061c-425">blazorserver</span><span class="sxs-lookup"><span data-stu-id="e061c-425">blazorserver</span></span>

- <span data-ttu-id="e061c-426">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-426">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e061c-427">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e061c-427">The type of authentication to use.</span></span> <span data-ttu-id="e061c-428">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e061c-428">The possible values are:</span></span>

  - <span data-ttu-id="e061c-429">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="e061c-429">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e061c-430">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="e061c-430">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e061c-431">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e061c-431">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e061c-432">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="e061c-432">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e061c-433">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="e061c-433">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="e061c-434">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="e061c-434">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e061c-435">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-435">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e061c-436">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-436">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-437">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="e061c-437">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e061c-438">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-438">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e061c-439">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-439">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="e061c-440">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-440">The reset password policy ID for this project.</span></span> <span data-ttu-id="e061c-441">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-441">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="e061c-442">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-442">The edit profile policy ID for this project.</span></span> <span data-ttu-id="e061c-443">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-443">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e061c-444">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-444">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e061c-445">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-445">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="e061c-446">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e061c-446">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e061c-447">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-447">The Client ID for this project.</span></span> <span data-ttu-id="e061c-448">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-448">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="e061c-449">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e061c-449">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e061c-450">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e061c-450">The domain for the directory tenant.</span></span> <span data-ttu-id="e061c-451">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-451">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-452">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e061c-452">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e061c-453">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-453">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e061c-454">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-454">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e061c-455">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e061c-455">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="e061c-456">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="e061c-456">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="e061c-457">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-457">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-458">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="e061c-458">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e061c-459">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e061c-459">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e061c-460">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-460">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e061c-461">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e061c-461">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e061c-462">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e061c-462">Turns off HTTPS.</span></span> <span data-ttu-id="e061c-463">Cette option s’applique uniquement si `Individual` , `IndividualB2C` , `SingleOrg` ou `MultiOrg` ne sont pas utilisés pour `--auth` .</span><span class="sxs-lookup"><span data-stu-id="e061c-463">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e061c-464">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="e061c-464">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e061c-465">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-465">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e061c-466">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-466">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e061c-467">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-467">\*\*_</span></span>

### <a name="blazorwasm"></a><span data-ttu-id="e061c-468">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="e061c-468">blazorwasm</span></span>

- <span data-ttu-id="e061c-469">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-469">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e061c-470">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-470">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="e061c-471">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e061c-471">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e061c-472">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e061c-472">SDK version</span></span> | <span data-ttu-id="e061c-473">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e061c-473">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e061c-474">5.0</span><span class="sxs-lookup"><span data-stu-id="e061c-474">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e061c-475">3.1</span><span class="sxs-lookup"><span data-stu-id="e061c-475">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="e061c-476">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-476">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="e061c-477">Comprend un hôte de ASP.NET Core pour l' Blazor WebAssembly application.</span><span class="sxs-lookup"><span data-stu-id="e061c-477">Includes an ASP.NET Core host for the Blazor WebAssembly app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="e061c-478">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e061c-478">The type of authentication to use.</span></span> <span data-ttu-id="e061c-479">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e061c-479">The possible values are:</span></span>

  - <span data-ttu-id="e061c-480">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="e061c-480">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e061c-481">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="e061c-481">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e061c-482">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e061c-482">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e061c-483">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="e061c-483">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="e061c-484">Autorité du fournisseur OIDC.</span><span class="sxs-lookup"><span data-stu-id="e061c-484">The authority of the OIDC provider.</span></span> <span data-ttu-id="e061c-485">À utiliser avec l’authentification `Individual`.</span><span class="sxs-lookup"><span data-stu-id="e061c-485">Use with `Individual` authentication.</span></span> <span data-ttu-id="e061c-486">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e061c-486">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e061c-487">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-487">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e061c-488">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-488">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-489">La valeur par défaut est `https://aadB2CInstance.b2clogin.com/`.</span><span class="sxs-lookup"><span data-stu-id="e061c-489">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e061c-490">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-490">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e061c-491">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-491">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e061c-492">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-492">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e061c-493">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-493">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e061c-494">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e061c-494">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e061c-495">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-495">The Client ID for this project.</span></span> <span data-ttu-id="e061c-496">Utilisez avec `IndividualB2C` `SingleOrg` `Individual` l’authentification, ou dans des scénarios autonomes.</span><span class="sxs-lookup"><span data-stu-id="e061c-496">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="e061c-497">La valeur par défaut est `33333333-3333-3333-33333333333333333`.</span><span class="sxs-lookup"><span data-stu-id="e061c-497">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e061c-498">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e061c-498">The domain for the directory tenant.</span></span> <span data-ttu-id="e061c-499">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-499">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-500">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e061c-500">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="e061c-501">URI ID d’application de l’API serveur que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="e061c-501">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="e061c-502">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-502">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-503">La valeur par défaut est `api.id.uri`.</span><span class="sxs-lookup"><span data-stu-id="e061c-503">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="e061c-504">ID client de l’API que le serveur héberge.</span><span class="sxs-lookup"><span data-stu-id="e061c-504">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="e061c-505">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-505">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-506">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e061c-506">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="e061c-507">Étendue de l’API que le client doit demander pour approvisionner un jeton d’accès.</span><span class="sxs-lookup"><span data-stu-id="e061c-507">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="e061c-508">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-508">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-509">La valeur par défaut est `user_impersonation`.</span><span class="sxs-lookup"><span data-stu-id="e061c-509">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e061c-510">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-510">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e061c-511">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-511">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e061c-512">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e061c-512">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e061c-513">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e061c-513">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e061c-514">S’applique uniquement à `SingleOrg` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="e061c-514">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e061c-515">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e061c-515">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="e061c-516">produit une application Web progressive (PWA) qui prend en charge l’installation et l’utilisation hors connexion.</span><span class="sxs-lookup"><span data-stu-id="e061c-516">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="e061c-517">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e061c-517">Turns off HTTPS.</span></span> <span data-ttu-id="e061c-518">Cette option s’applique uniquement si `Individual` , `IndividualB2C` ou `SingleOrg` ne sont pas utilisés pour `--auth` .</span><span class="sxs-lookup"><span data-stu-id="e061c-518">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e061c-519">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="e061c-519">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e061c-520">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-520">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="e061c-521">URL de l’API à appeler à partir de l’application Web.</span><span class="sxs-lookup"><span data-stu-id="e061c-521">URL of the API to call from the web app.</span></span> <span data-ttu-id="e061c-522">S’applique uniquement à `SingleOrg` ou à `IndividualB2C` l’authentification sans ASP.net Core hôte spécifié.</span><span class="sxs-lookup"><span data-stu-id="e061c-522">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="e061c-523">La valeur par défaut est `https://graph.microsoft.com/v1.0/me`.</span><span class="sxs-lookup"><span data-stu-id="e061c-523">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="e061c-524">Spécifie si l’application Web appelle Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="e061c-524">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="e061c-525">S’applique uniquement à `SingleOrg` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="e061c-525">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="e061c-526">Étendues à demander pour appeler l’API à partir de l’application Web.</span><span class="sxs-lookup"><span data-stu-id="e061c-526">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="e061c-527">S’applique uniquement à `SingleOrg` ou à `IndividualB2C` l’authentification sans ASP.net Core hôte spécifié.</span><span class="sxs-lookup"><span data-stu-id="e061c-527">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="e061c-528">La valeur par défaut est `user.read`.</span><span class="sxs-lookup"><span data-stu-id="e061c-528">The default is `user.read`.</span></span>

<span data-ttu-id="e061c-529">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-529">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="e061c-530">web</span><span class="sxs-lookup"><span data-stu-id="e061c-530">web</span></span>

- <span data-ttu-id="e061c-531">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-531">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="e061c-532">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e061c-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e061c-533">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e061c-534">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e061c-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e061c-535">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e061c-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e061c-536">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e061c-536">SDK version</span></span> | <span data-ttu-id="e061c-537">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e061c-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e061c-538">5.0</span><span class="sxs-lookup"><span data-stu-id="e061c-538">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e061c-539">3.1</span><span class="sxs-lookup"><span data-stu-id="e061c-539">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e061c-540">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-540">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e061c-541">2.1</span><span class="sxs-lookup"><span data-stu-id="e061c-541">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="e061c-542">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-542">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e061c-543">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e061c-543">Turns off HTTPS.</span></span>

<span data-ttu-id="e061c-544">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-544">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="e061c-545">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="e061c-545">mvc, webapp</span></span>

- <span data-ttu-id="e061c-546">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-546">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e061c-547">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e061c-547">The type of authentication to use.</span></span> <span data-ttu-id="e061c-548">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e061c-548">The possible values are:</span></span>

  - <span data-ttu-id="e061c-549">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="e061c-549">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e061c-550">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="e061c-550">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e061c-551">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e061c-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e061c-552">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="e061c-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e061c-553">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="e061c-553">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="e061c-554">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="e061c-554">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e061c-555">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-555">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e061c-556">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-556">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-557">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="e061c-557">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e061c-558">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-558">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e061c-559">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-559">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="e061c-560">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-560">The reset password policy ID for this project.</span></span> <span data-ttu-id="e061c-561">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-561">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="e061c-562">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-562">The edit profile policy ID for this project.</span></span> <span data-ttu-id="e061c-563">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-563">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e061c-564">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-564">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e061c-565">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-565">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="e061c-566">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e061c-566">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e061c-567">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-567">The Client ID for this project.</span></span> <span data-ttu-id="e061c-568">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-568">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="e061c-569">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e061c-569">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e061c-570">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e061c-570">The domain for the directory tenant.</span></span> <span data-ttu-id="e061c-571">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-571">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-572">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e061c-572">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e061c-573">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-573">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e061c-574">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-574">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e061c-575">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e061c-575">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="e061c-576">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="e061c-576">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="e061c-577">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-577">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-578">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="e061c-578">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e061c-579">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e061c-579">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e061c-580">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-580">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e061c-581">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e061c-581">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e061c-582">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e061c-582">Turns off HTTPS.</span></span> <span data-ttu-id="e061c-583">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="e061c-583">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e061c-584">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="e061c-584">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e061c-585">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-585">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e061c-586">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-586">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e061c-587">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e061c-587">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e061c-588">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e061c-588">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e061c-589">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e061c-589">SDK version</span></span> | <span data-ttu-id="e061c-590">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e061c-590">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e061c-591">5.0</span><span class="sxs-lookup"><span data-stu-id="e061c-591">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e061c-592">3.1</span><span class="sxs-lookup"><span data-stu-id="e061c-592">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e061c-593">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-593">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="e061c-594">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-594">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="e061c-595">Comprend BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-595">Includes BrowserLink in the project.</span></span> <span data-ttu-id="e061c-596">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2 et 3,1.</span><span class="sxs-lookup"><span data-stu-id="e061c-596">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="e061c-597">Détermine si le projet est configuré pour utiliser la [compilation du runtime Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) dans les versions Debug.</span><span class="sxs-lookup"><span data-stu-id="e061c-597">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="e061c-598">Option disponible depuis le kit de développement logiciel (SDK) 3.1.201 .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e061c-598">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="e061c-599">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-599">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="e061c-600">angulaire, réaction</span><span class="sxs-lookup"><span data-stu-id="e061c-600">angular, react</span></span>

- <span data-ttu-id="e061c-601">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-601">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e061c-602">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e061c-602">The type of authentication to use.</span></span> <span data-ttu-id="e061c-603">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e061c-603">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="e061c-604">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e061c-604">The possible values are:</span></span>

  - <span data-ttu-id="e061c-605">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="e061c-605">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e061c-606">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="e061c-606">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e061c-607">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e061c-607">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e061c-608">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-608">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e061c-609">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e061c-609">Turns off HTTPS.</span></span> <span data-ttu-id="e061c-610">Cette option s’applique uniquement si l’authentification est `None` .</span><span class="sxs-lookup"><span data-stu-id="e061c-610">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e061c-611">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="e061c-611">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e061c-612">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-612">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-613">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e061c-613">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e061c-614">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-614">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e061c-615">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e061c-615">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e061c-616">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e061c-616">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e061c-617">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e061c-617">SDK version</span></span> | <span data-ttu-id="e061c-618">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e061c-618">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e061c-619">5.0</span><span class="sxs-lookup"><span data-stu-id="e061c-619">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e061c-620">3.1</span><span class="sxs-lookup"><span data-stu-id="e061c-620">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e061c-621">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-621">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e061c-622">2.1</span><span class="sxs-lookup"><span data-stu-id="e061c-622">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="e061c-623">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-623">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="e061c-624">reactredux</span><span class="sxs-lookup"><span data-stu-id="e061c-624">reactredux</span></span>

- <span data-ttu-id="e061c-625">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-625">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="e061c-626">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e061c-626">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e061c-627">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-627">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e061c-628">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e061c-628">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e061c-629">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e061c-629">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e061c-630">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e061c-630">SDK version</span></span> | <span data-ttu-id="e061c-631">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e061c-631">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e061c-632">5.0</span><span class="sxs-lookup"><span data-stu-id="e061c-632">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e061c-633">3.1</span><span class="sxs-lookup"><span data-stu-id="e061c-633">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e061c-634">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-634">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e061c-635">2.1</span><span class="sxs-lookup"><span data-stu-id="e061c-635">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="e061c-636">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-636">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e061c-637">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e061c-637">Turns off HTTPS.</span></span>

<span data-ttu-id="e061c-638">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-638">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="e061c-639">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="e061c-639">razorclasslib</span></span>

- <span data-ttu-id="e061c-640">_ *`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-640">_ *`--no-restore`*\*</span></span>

  <span data-ttu-id="e061c-641">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-641">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="e061c-642">Prend en charge l’ajout de pages et de vues Razor traditionnelles en plus des composants de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="e061c-642">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="e061c-643">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e061c-643">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="e061c-644">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-644">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="e061c-645">webapi</span><span class="sxs-lookup"><span data-stu-id="e061c-645">webapi</span></span>

- <span data-ttu-id="e061c-646">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-646">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e061c-647">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e061c-647">The type of authentication to use.</span></span> <span data-ttu-id="e061c-648">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e061c-648">The possible values are:</span></span>

  - <span data-ttu-id="e061c-649">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="e061c-649">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e061c-650">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e061c-650">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e061c-651">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="e061c-651">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e061c-652">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="e061c-652">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e061c-653">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-653">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e061c-654">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-654">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e061c-655">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="e061c-655">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e061c-656">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-656">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e061c-657">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e061c-657">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e061c-658">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-658">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e061c-659">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-659">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e061c-660">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e061c-660">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e061c-661">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-661">The Client ID for this project.</span></span> <span data-ttu-id="e061c-662">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-662">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="e061c-663">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e061c-663">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e061c-664">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e061c-664">The domain for the directory tenant.</span></span> <span data-ttu-id="e061c-665">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-665">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="e061c-666">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e061c-666">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e061c-667">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="e061c-667">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e061c-668">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e061c-668">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e061c-669">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e061c-669">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e061c-670">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e061c-670">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e061c-671">S’applique uniquement à `SingleOrg` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="e061c-671">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e061c-672">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e061c-672">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e061c-673">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e061c-673">Turns off HTTPS.</span></span> <span data-ttu-id="e061c-674">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="e061c-674">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="e061c-675">Cette option s’applique uniquement si `IndividualB2C` ou `SingleOrg` ne sont pas utilisés pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="e061c-675">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e061c-676">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="e061c-676">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e061c-677">S’applique uniquement à `IndividualB2C` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="e061c-677">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e061c-678">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e061c-678">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e061c-679">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e061c-679">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e061c-680">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e061c-680">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e061c-681">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e061c-681">SDK version</span></span> | <span data-ttu-id="e061c-682">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e061c-682">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e061c-683">5.0</span><span class="sxs-lookup"><span data-stu-id="e061c-683">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e061c-684">3.1</span><span class="sxs-lookup"><span data-stu-id="e061c-684">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e061c-685">3.0</span><span class="sxs-lookup"><span data-stu-id="e061c-685">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e061c-686">2.1</span><span class="sxs-lookup"><span data-stu-id="e061c-686">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="e061c-687">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e061c-687">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e061c-688">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e061c-688">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="e061c-689">globaljson</span><span class="sxs-lookup"><span data-stu-id="e061c-689">globaljson</span></span>

- <span data-ttu-id="e061c-690">_ *`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="e061c-690">_ *`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="e061c-691">Spécifie la version du kit de développement logiciel (SDK) .NET à utiliser dans le fichier *global.js* .</span><span class="sxs-lookup"><span data-stu-id="e061c-691">Specifies the version of the .NET SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="e061c-692">Exemples</span><span class="sxs-lookup"><span data-stu-id="e061c-692">Examples</span></span>

- <span data-ttu-id="e061c-693">Créez un projet d’application console C# en spécifiant le nom du modèle :</span><span class="sxs-lookup"><span data-stu-id="e061c-693">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="e061c-694">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="e061c-694">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="e061c-695">Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié :</span><span class="sxs-lookup"><span data-stu-id="e061c-695">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="e061c-696">Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :</span><span class="sxs-lookup"><span data-stu-id="e061c-696">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="e061c-697">Créez un projet xUnit :</span><span class="sxs-lookup"><span data-stu-id="e061c-697">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="e061c-698">Répertorier tous les modèles disponibles pour les modèles d’application à page unique (SPA) :</span><span class="sxs-lookup"><span data-stu-id="e061c-698">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="e061c-699">Liste de tous les modèles correspondant à la sous-chaîne *we*.</span><span class="sxs-lookup"><span data-stu-id="e061c-699">List all templates matching the *we* substring.</span></span> <span data-ttu-id="e061c-700">Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.</span><span class="sxs-lookup"><span data-stu-id="e061c-700">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="e061c-701">Tentative d’appel du modèle correspondant à *ng*.</span><span class="sxs-lookup"><span data-stu-id="e061c-701">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="e061c-702">Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.</span><span class="sxs-lookup"><span data-stu-id="e061c-702">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="e061c-703">Installez la version 2,0 des modèles SPA pour ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="e061c-703">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="e061c-704">Répertoriez les modèles installés et les détails les concernant, notamment comment les désinstaller :</span><span class="sxs-lookup"><span data-stu-id="e061c-704">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="e061c-705">Créez un *global.js* dans le répertoire actif en définissant la version du kit de développement logiciel (SDK) sur 3.1.101 :</span><span class="sxs-lookup"><span data-stu-id="e061c-705">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="e061c-706">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e061c-706">See also</span></span>

- [<span data-ttu-id="e061c-707">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="e061c-707">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="e061c-708">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="e061c-708">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="e061c-709">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="e061c-709">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="e061c-710">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="e061c-710">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
