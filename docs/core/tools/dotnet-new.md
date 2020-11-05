---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
no-loc:
- ':::no-loc(Blazor):::'
- ':::no-loc(WebAssembly):::'
ms.date: 09/04/2020
ms.openlocfilehash: 2ee06c37cd950f3b9771db2f30fe353435641d67
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400589"
---
# <a name="dotnet-new"></a><span data-ttu-id="e5617-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="e5617-103">dotnet new</span></span>

<span data-ttu-id="e5617-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="e5617-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e5617-105">Nom</span><span class="sxs-lookup"><span data-stu-id="e5617-105">Name</span></span>

<span data-ttu-id="e5617-106">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="e5617-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e5617-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="e5617-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="e5617-108">Description</span><span class="sxs-lookup"><span data-stu-id="e5617-108">Description</span></span>

<span data-ttu-id="e5617-109">La `dotnet new` commande crée un projet .net Core ou d’autres artefacts basés sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="e5617-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="e5617-110">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="e5617-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="e5617-111">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="e5617-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="e5617-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="e5617-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="e5617-113">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="e5617-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="e5617-114">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="e5617-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="e5617-115">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="e5617-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="e5617-116">Vous pouvez exécuter `dotnet new --list` ou `dotnet new -l` pour afficher la liste de tous les modèles installés.</span><span class="sxs-lookup"><span data-stu-id="e5617-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="e5617-117">Si la `TEMPLATE` valeur ne correspond pas exactement au texte de la colonne **Templates** ou **Short Name** de la table retournée, une correspondance de sous-chaînes est effectuée sur ces deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="e5617-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="e5617-118">À compter du kit de développement logiciel (SDK) .NET Core 3,0, l’interface CLI recherche des modèles dans NuGet.org quand vous appelez la `dotnet new` commande dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5617-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="e5617-119">Si l’interface CLI ne peut pas trouver de correspondance de modèle lors de l’appel `dotnet new` de, pas encore partiel.</span><span class="sxs-lookup"><span data-stu-id="e5617-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="e5617-120">Si une version plus récente du modèle est disponible.</span><span class="sxs-lookup"><span data-stu-id="e5617-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="e5617-121">Dans ce cas, le projet ou l’artefact est créé, mais l’interface CLI vous avertit d’une version mise à jour du modèle.</span><span class="sxs-lookup"><span data-stu-id="e5617-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="e5617-122">Le tableau suivant répertorie les modèles qui sont préinstallés avec le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5617-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="e5617-123">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="e5617-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="e5617-124">Cliquez sur le lien nom abrégé pour afficher les options de modèle spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e5617-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="e5617-125">Modèles</span><span class="sxs-lookup"><span data-stu-id="e5617-125">Templates</span></span>                                    | <span data-ttu-id="e5617-126">Nom court</span><span class="sxs-lookup"><span data-stu-id="e5617-126">Short name</span></span>                      | <span data-ttu-id="e5617-127">Language</span><span class="sxs-lookup"><span data-stu-id="e5617-127">Language</span></span>     | <span data-ttu-id="e5617-128">Étiquettes</span><span class="sxs-lookup"><span data-stu-id="e5617-128">Tags</span></span>                                  | <span data-ttu-id="e5617-129">Introduit</span><span class="sxs-lookup"><span data-stu-id="e5617-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="e5617-130">Application console</span><span class="sxs-lookup"><span data-stu-id="e5617-130">Console Application</span></span>                          | [<span data-ttu-id="e5617-131">console</span><span class="sxs-lookup"><span data-stu-id="e5617-131">console</span></span>](#console)             | <span data-ttu-id="e5617-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e5617-132">[C#], F#, VB</span></span> | <span data-ttu-id="e5617-133">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="e5617-133">Common/Console</span></span>                        | <span data-ttu-id="e5617-134">1.0</span><span class="sxs-lookup"><span data-stu-id="e5617-134">1.0</span></span>        |
| <span data-ttu-id="e5617-135">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="e5617-135">Class library</span></span>                                | [<span data-ttu-id="e5617-136">classlib</span><span class="sxs-lookup"><span data-stu-id="e5617-136">classlib</span></span>](#classlib)           | <span data-ttu-id="e5617-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e5617-137">[C#], F#, VB</span></span> | <span data-ttu-id="e5617-138">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="e5617-138">Common/Library</span></span>                        | <span data-ttu-id="e5617-139">1.0</span><span class="sxs-lookup"><span data-stu-id="e5617-139">1.0</span></span>        |
| <span data-ttu-id="e5617-140">Application WPF</span><span class="sxs-lookup"><span data-stu-id="e5617-140">WPF Application</span></span>                              | [<span data-ttu-id="e5617-141">WPF</span><span class="sxs-lookup"><span data-stu-id="e5617-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="e5617-142">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e5617-142">[C#], VB</span></span>     | <span data-ttu-id="e5617-143">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="e5617-143">Common/WPF</span></span>                            | <span data-ttu-id="e5617-144">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e5617-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e5617-145">Bibliothèque de classes WPF</span><span class="sxs-lookup"><span data-stu-id="e5617-145">WPF Class library</span></span>                            | [<span data-ttu-id="e5617-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="e5617-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="e5617-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e5617-147">[C#], VB</span></span>     | <span data-ttu-id="e5617-148">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="e5617-148">Common/WPF</span></span>                            | <span data-ttu-id="e5617-149">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e5617-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e5617-150">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="e5617-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="e5617-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="e5617-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="e5617-152">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e5617-152">[C#], VB</span></span>     | <span data-ttu-id="e5617-153">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="e5617-153">Common/WPF</span></span>                            | <span data-ttu-id="e5617-154">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e5617-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e5617-155">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="e5617-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="e5617-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="e5617-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="e5617-157">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e5617-157">[C#], VB</span></span>     | <span data-ttu-id="e5617-158">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="e5617-158">Common/WPF</span></span>                            | <span data-ttu-id="e5617-159">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e5617-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e5617-160">Application Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e5617-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="e5617-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="e5617-161">winforms</span></span>](#winforms)           | <span data-ttu-id="e5617-162">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e5617-162">[C#], VB</span></span>     | <span data-ttu-id="e5617-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="e5617-163">Common/WinForms</span></span>                       | <span data-ttu-id="e5617-164">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e5617-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e5617-165">Bibliothèque de classes Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e5617-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="e5617-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="e5617-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="e5617-167">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="e5617-167">[C#], VB</span></span>     | <span data-ttu-id="e5617-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="e5617-168">Common/WinForms</span></span>                       | <span data-ttu-id="e5617-169">3,0 (5,0 pour VB)</span><span class="sxs-lookup"><span data-stu-id="e5617-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="e5617-170">Service Worker</span><span class="sxs-lookup"><span data-stu-id="e5617-170">Worker Service</span></span>                               | [<span data-ttu-id="e5617-171">collabor</span><span class="sxs-lookup"><span data-stu-id="e5617-171">worker</span></span>](#web-others)           | <span data-ttu-id="e5617-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-172">[C#]</span></span>         | <span data-ttu-id="e5617-173">Commun/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="e5617-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="e5617-174">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-174">3.0</span></span>        |
| <span data-ttu-id="e5617-175">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="e5617-175">Unit Test Project</span></span>                            | [<span data-ttu-id="e5617-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="e5617-176">mstest</span></span>](#test)                 | <span data-ttu-id="e5617-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e5617-177">[C#], F#, VB</span></span> | <span data-ttu-id="e5617-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="e5617-178">Test/MSTest</span></span>                           | <span data-ttu-id="e5617-179">1.0</span><span class="sxs-lookup"><span data-stu-id="e5617-179">1.0</span></span>        |
| <span data-ttu-id="e5617-180">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="e5617-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="e5617-181">nunit</span><span class="sxs-lookup"><span data-stu-id="e5617-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="e5617-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e5617-182">[C#], F#, VB</span></span> | <span data-ttu-id="e5617-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="e5617-183">Test/NUnit</span></span>                            | <span data-ttu-id="e5617-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="e5617-184">2.1.400</span></span>    |
| <span data-ttu-id="e5617-185">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="e5617-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="e5617-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e5617-186">[C#], F#, VB</span></span> | <span data-ttu-id="e5617-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="e5617-187">Test/NUnit</span></span>                            | <span data-ttu-id="e5617-188">2.2</span><span class="sxs-lookup"><span data-stu-id="e5617-188">2.2</span></span>        |
| <span data-ttu-id="e5617-189">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="e5617-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="e5617-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="e5617-190">xunit</span></span>](#test)                  | <span data-ttu-id="e5617-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e5617-191">[C#], F#, VB</span></span> | <span data-ttu-id="e5617-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="e5617-192">Test/xUnit</span></span>                            | <span data-ttu-id="e5617-193">1.0</span><span class="sxs-lookup"><span data-stu-id="e5617-193">1.0</span></span>        |
| <span data-ttu-id="e5617-194">Composant Razor</span><span class="sxs-lookup"><span data-stu-id="e5617-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="e5617-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-195">[C#]</span></span>         | <span data-ttu-id="e5617-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e5617-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="e5617-197">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-197">3.0</span></span>        |
| <span data-ttu-id="e5617-198">Page Razor</span><span class="sxs-lookup"><span data-stu-id="e5617-198">Razor Page</span></span>                                   | [<span data-ttu-id="e5617-199">page</span><span class="sxs-lookup"><span data-stu-id="e5617-199">page</span></span>](#page)                   | <span data-ttu-id="e5617-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-200">[C#]</span></span>         | <span data-ttu-id="e5617-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e5617-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="e5617-202">2.0</span><span class="sxs-lookup"><span data-stu-id="e5617-202">2.0</span></span>        |
| <span data-ttu-id="e5617-203">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="e5617-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="e5617-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="e5617-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="e5617-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-205">[C#]</span></span>         | <span data-ttu-id="e5617-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e5617-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="e5617-207">2.0</span><span class="sxs-lookup"><span data-stu-id="e5617-207">2.0</span></span>        |
| <span data-ttu-id="e5617-208">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="e5617-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="e5617-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-209">[C#]</span></span>         | <span data-ttu-id="e5617-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e5617-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="e5617-211">2.0</span><span class="sxs-lookup"><span data-stu-id="e5617-211">2.0</span></span>        |
| <span data-ttu-id="e5617-212">:::no-loc(Blazor)::: Application serveur</span><span class="sxs-lookup"><span data-stu-id="e5617-212">:::no-loc(Blazor)::: Server App</span></span>                            | [<span data-ttu-id="e5617-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="e5617-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="e5617-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-214">[C#]</span></span>         | <span data-ttu-id="e5617-215">Internet:::no-loc(Blazor):::</span><span class="sxs-lookup"><span data-stu-id="e5617-215">Web/:::no-loc(Blazor):::</span></span>                            | <span data-ttu-id="e5617-216">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-216">3.0</span></span>        |
| <span data-ttu-id="e5617-217">:::no-loc(Blazor)::::::no-loc(WebAssembly):::Application</span><span class="sxs-lookup"><span data-stu-id="e5617-217">:::no-loc(Blazor)::: :::no-loc(WebAssembly)::: App</span></span>                       | [<span data-ttu-id="e5617-218">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="e5617-218">blazorwasm</span></span>](#blazorwasm)       | <span data-ttu-id="e5617-219">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-219">[C#]</span></span>         | <span data-ttu-id="e5617-220">Internet:::no-loc(Blazor):::/:::no-loc(WebAssembly):::</span><span class="sxs-lookup"><span data-stu-id="e5617-220">Web/:::no-loc(Blazor):::/:::no-loc(WebAssembly):::</span></span>                | <span data-ttu-id="e5617-221">3.1.300</span><span class="sxs-lookup"><span data-stu-id="e5617-221">3.1.300</span></span>    |
| <span data-ttu-id="e5617-222">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="e5617-222">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="e5617-223">web</span><span class="sxs-lookup"><span data-stu-id="e5617-223">web</span></span>](#web)                     | <span data-ttu-id="e5617-224">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e5617-224">[C#], F#</span></span>     | <span data-ttu-id="e5617-225">Web/vides</span><span class="sxs-lookup"><span data-stu-id="e5617-225">Web/Empty</span></span>                             | <span data-ttu-id="e5617-226">1.0</span><span class="sxs-lookup"><span data-stu-id="e5617-226">1.0</span></span>        |
| <span data-ttu-id="e5617-227">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="e5617-227">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="e5617-228">MVC</span><span class="sxs-lookup"><span data-stu-id="e5617-228">mvc</span></span>](#web-options)             | <span data-ttu-id="e5617-229">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e5617-229">[C#], F#</span></span>     | <span data-ttu-id="e5617-230">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="e5617-230">Web/MVC</span></span>                               | <span data-ttu-id="e5617-231">1.0</span><span class="sxs-lookup"><span data-stu-id="e5617-231">1.0</span></span>        |
| <span data-ttu-id="e5617-232">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e5617-232">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="e5617-233">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="e5617-233">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="e5617-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-234">[C#]</span></span>         | <span data-ttu-id="e5617-235">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="e5617-235">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="e5617-236">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="e5617-236">2.2, 2.0</span></span>   |
| <span data-ttu-id="e5617-237">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="e5617-237">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="e5617-238">oblique</span><span class="sxs-lookup"><span data-stu-id="e5617-238">angular</span></span>](#spa)                 | <span data-ttu-id="e5617-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-239">[C#]</span></span>         | <span data-ttu-id="e5617-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="e5617-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e5617-241">2.0</span><span class="sxs-lookup"><span data-stu-id="e5617-241">2.0</span></span>        |
| <span data-ttu-id="e5617-242">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="e5617-242">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="e5617-243">réagir</span><span class="sxs-lookup"><span data-stu-id="e5617-243">react</span></span>](#spa)                   | <span data-ttu-id="e5617-244">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-244">[C#]</span></span>         | <span data-ttu-id="e5617-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="e5617-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e5617-246">2.0</span><span class="sxs-lookup"><span data-stu-id="e5617-246">2.0</span></span>        |
| <span data-ttu-id="e5617-247">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="e5617-247">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="e5617-248">reactredux</span><span class="sxs-lookup"><span data-stu-id="e5617-248">reactredux</span></span>](#reactredux)       | <span data-ttu-id="e5617-249">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-249">[C#]</span></span>         | <span data-ttu-id="e5617-250">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="e5617-250">Web/MVC/SPA</span></span>                           | <span data-ttu-id="e5617-251">2.0</span><span class="sxs-lookup"><span data-stu-id="e5617-251">2.0</span></span>        |
| <span data-ttu-id="e5617-252">Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="e5617-252">Razor Class Library</span></span>                          | [<span data-ttu-id="e5617-253">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="e5617-253">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="e5617-254">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-254">[C#]</span></span>         | <span data-ttu-id="e5617-255">Web/Razor/Library/Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="e5617-255">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="e5617-256">2.1</span><span class="sxs-lookup"><span data-stu-id="e5617-256">2.1</span></span>        |
| <span data-ttu-id="e5617-257">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e5617-257">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="e5617-258">WebAPI</span><span class="sxs-lookup"><span data-stu-id="e5617-258">webapi</span></span>](#webapi)               | <span data-ttu-id="e5617-259">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="e5617-259">[C#], F#</span></span>     | <span data-ttu-id="e5617-260">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="e5617-260">Web/WebAPI</span></span>                            | <span data-ttu-id="e5617-261">1.0</span><span class="sxs-lookup"><span data-stu-id="e5617-261">1.0</span></span>        |
| <span data-ttu-id="e5617-262">ASP.NET Core Service gRPC</span><span class="sxs-lookup"><span data-stu-id="e5617-262">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="e5617-263">GRPC</span><span class="sxs-lookup"><span data-stu-id="e5617-263">grpc</span></span>](#web-others)             | <span data-ttu-id="e5617-264">[C#]</span><span class="sxs-lookup"><span data-stu-id="e5617-264">[C#]</span></span>         | <span data-ttu-id="e5617-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="e5617-265">Web/gRPC</span></span>                              | <span data-ttu-id="e5617-266">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-266">3.0</span></span>        |
| <span data-ttu-id="e5617-267">fichier gitignore dotnet</span><span class="sxs-lookup"><span data-stu-id="e5617-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="e5617-268">Config</span><span class="sxs-lookup"><span data-stu-id="e5617-268">Config</span></span>                                | <span data-ttu-id="e5617-269">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-269">3.0</span></span>        |
| <span data-ttu-id="e5617-270">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="e5617-270">global.json file</span></span>                             | [<span data-ttu-id="e5617-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="e5617-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="e5617-272">Config</span><span class="sxs-lookup"><span data-stu-id="e5617-272">Config</span></span>                                | <span data-ttu-id="e5617-273">2.0</span><span class="sxs-lookup"><span data-stu-id="e5617-273">2.0</span></span>        |
| <span data-ttu-id="e5617-274">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="e5617-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="e5617-275">Config</span><span class="sxs-lookup"><span data-stu-id="e5617-275">Config</span></span>                                | <span data-ttu-id="e5617-276">1.0</span><span class="sxs-lookup"><span data-stu-id="e5617-276">1.0</span></span>        |
| <span data-ttu-id="e5617-277">Fichier manifeste de l’outil local dotnet</span><span class="sxs-lookup"><span data-stu-id="e5617-277">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="e5617-278">Config</span><span class="sxs-lookup"><span data-stu-id="e5617-278">Config</span></span>                                | <span data-ttu-id="e5617-279">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-279">3.0</span></span>        |
| <span data-ttu-id="e5617-280">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="e5617-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="e5617-281">Config</span><span class="sxs-lookup"><span data-stu-id="e5617-281">Config</span></span>                                | <span data-ttu-id="e5617-282">1.0</span><span class="sxs-lookup"><span data-stu-id="e5617-282">1.0</span></span>        |
| <span data-ttu-id="e5617-283">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="e5617-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="e5617-284">Solution</span><span class="sxs-lookup"><span data-stu-id="e5617-284">Solution</span></span>                              | <span data-ttu-id="e5617-285">1.0</span><span class="sxs-lookup"><span data-stu-id="e5617-285">1.0</span></span>        |
| <span data-ttu-id="e5617-286">Fichier de mémoire tampon de protocole</span><span class="sxs-lookup"><span data-stu-id="e5617-286">Protocol Buffer File</span></span>                         | [<span data-ttu-id="e5617-287">proto</span><span class="sxs-lookup"><span data-stu-id="e5617-287">proto</span></span>](#namespace)             |              | <span data-ttu-id="e5617-288">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="e5617-288">Web/gRPC</span></span>                              | <span data-ttu-id="e5617-289">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-289">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="e5617-290">Options</span><span class="sxs-lookup"><span data-stu-id="e5617-290">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="e5617-291">Affiche un récapitulatif de ce qui se passerait si la commande donnée était exécutée (si cela donnerait lieu à la création d’un modèle).</span><span class="sxs-lookup"><span data-stu-id="e5617-291">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="e5617-292">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e5617-292">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="e5617-293">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="e5617-293">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="e5617-294">Cela est obligatoire lorsque le modèle choisi remplace les fichiers existants dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="e5617-294">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e5617-295">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="e5617-295">Prints out help for the command.</span></span> <span data-ttu-id="e5617-296">Elle peut être appelée pour la `dotnet new` commande elle-même ou pour n’importe quel modèle.</span><span class="sxs-lookup"><span data-stu-id="e5617-296">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="e5617-297">Par exemple, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="e5617-297">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="e5617-298">Installe un pack de modèles à partir du `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="e5617-298">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="e5617-299">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="e5617-299">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="e5617-300">Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package.</span><span class="sxs-lookup"><span data-stu-id="e5617-300">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="e5617-301">Consultez un exemple dans la section [exemples](#examples) .</span><span class="sxs-lookup"><span data-stu-id="e5617-301">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="e5617-302">Si une version du modèle a déjà été installée lorsque vous exécutez cette commande, le modèle sera mis à jour vers la version spécifiée, ou vers la version stable la plus récente si aucune version n’a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e5617-302">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="e5617-303">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="e5617-303">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="e5617-304">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="e5617-304">Lists templates containing the specified name.</span></span> <span data-ttu-id="e5617-305">Si aucun nom n’est spécifié, répertorie tous les modèles.</span><span class="sxs-lookup"><span data-stu-id="e5617-305">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="e5617-306">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="e5617-306">The language of the template to create.</span></span> <span data-ttu-id="e5617-307">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="e5617-307">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="e5617-308">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="e5617-308">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e5617-309">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="e5617-309">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="e5617-310">Dans ce cas, mettez la valeur du paramètre de langue entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="e5617-310">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="e5617-311">Par exemple, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="e5617-311">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="e5617-312">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="e5617-312">The name for the created output.</span></span> <span data-ttu-id="e5617-313">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e5617-313">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="e5617-314">Spécifie une source NuGet à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="e5617-314">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="e5617-315">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="e5617-315">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e5617-316">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="e5617-316">Location to place the generated output.</span></span> <span data-ttu-id="e5617-317">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="e5617-317">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="e5617-318">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="e5617-318">Filters templates based on available types.</span></span> <span data-ttu-id="e5617-319">Les valeurs prédéfinies sont `project` et `item` .</span><span class="sxs-lookup"><span data-stu-id="e5617-319">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="e5617-320">Désinstalle un pack de modèles au niveau de `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="e5617-320">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="e5617-321">Lorsque la `<PATH|NUGET_ID>` valeur n’est pas spécifiée, tous les packs de modèles actuellement installés et leurs modèles associés sont affichés.</span><span class="sxs-lookup"><span data-stu-id="e5617-321">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="e5617-322">Lorsque vous spécifiez `NUGET_ID` , n’incluez pas le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="e5617-322">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="e5617-323">Si vous ne spécifiez pas de paramètre pour cette option, la commande répertorie les modèles installés et fournit des détails à leur sujet.</span><span class="sxs-lookup"><span data-stu-id="e5617-323">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e5617-324">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="e5617-324">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="e5617-325">Par exemple, *C:/Users/ \<USER> /documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionnera, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne le sera pas.</span><span class="sxs-lookup"><span data-stu-id="e5617-325">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="e5617-326">N’incluez pas de barre oblique finale de répertoire finale dans le chemin d’accès de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="e5617-326">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="e5617-327">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés et les installe.</span><span class="sxs-lookup"><span data-stu-id="e5617-327">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="e5617-328">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e5617-328">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="e5617-329">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="e5617-329">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="e5617-330">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e5617-330">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="e5617-331">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="e5617-331">Template options</span></span>

<span data-ttu-id="e5617-332">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="e5617-332">Each project template may have additional options available.</span></span> <span data-ttu-id="e5617-333">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5617-333">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="e5617-334">console</span><span class="sxs-lookup"><span data-stu-id="e5617-334">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e5617-335">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-335">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e5617-336">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e5617-336">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e5617-337">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e5617-337">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e5617-338">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e5617-338">SDK version</span></span> | <span data-ttu-id="e5617-339">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e5617-339">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e5617-340">3.1</span><span class="sxs-lookup"><span data-stu-id="e5617-340">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e5617-341">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-341">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e5617-342">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="e5617-342">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e5617-343">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e5617-343">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="e5617-344">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="e5617-344">Not supported for F#.</span></span> <span data-ttu-id="e5617-345">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e5617-345">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e5617-346">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e5617-346">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e5617-347">S’il est spécifié, n’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-347">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="e5617-348">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e5617-348">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="e5617-349">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-349">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="e5617-350">classlib</span><span class="sxs-lookup"><span data-stu-id="e5617-350">classlib</span></span>

- <span data-ttu-id="e5617-351">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-351">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e5617-352">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-352">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e5617-353">Valeurs : `netcoreapp<version>` pour créer une bibliothèque de classes .NET Core ou `netstandard<version>` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e5617-353">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="e5617-354">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="e5617-354">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e5617-355">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="e5617-355">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e5617-356">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e5617-356">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="e5617-357">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="e5617-357">Not supported for F#.</span></span> <span data-ttu-id="e5617-358">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e5617-358">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e5617-359">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e5617-359">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e5617-360">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-360">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e5617-361">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-361">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="e5617-362">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="e5617-362">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="e5617-363">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-363">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e5617-364">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-364">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e5617-365">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="e5617-365">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="e5617-366">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="e5617-366">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="e5617-367">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="e5617-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e5617-368">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e5617-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="e5617-369">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e5617-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e5617-370">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-370">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e5617-371">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-371">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="e5617-372">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="e5617-372">winforms, winformslib</span></span>

- <span data-ttu-id="e5617-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="e5617-374">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="e5617-374">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="e5617-375">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="e5617-375">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="e5617-376">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="e5617-376">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e5617-377">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-377">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e5617-378">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-378">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="e5617-379">Worker, GRPC</span><span class="sxs-lookup"><span data-stu-id="e5617-379">worker, grpc</span></span>

- <span data-ttu-id="e5617-380">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-380">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e5617-381">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-381">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e5617-382">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="e5617-382">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="e5617-383">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="e5617-383">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e5617-384">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e5617-384">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e5617-385">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-385">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e5617-386">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-386">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="e5617-387">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="e5617-387">mstest, xunit</span></span>

- <span data-ttu-id="e5617-388">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-388">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e5617-389">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-389">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e5617-390">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e5617-390">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e5617-391">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e5617-391">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e5617-392">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e5617-392">SDK version</span></span> | <span data-ttu-id="e5617-393">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e5617-393">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e5617-394">3.1</span><span class="sxs-lookup"><span data-stu-id="e5617-394">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e5617-395">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-395">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="e5617-396">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="e5617-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e5617-397">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-397">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e5617-398">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-398">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="e5617-399">nunit</span><span class="sxs-lookup"><span data-stu-id="e5617-399">nunit</span></span>

- <span data-ttu-id="e5617-400">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-400">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e5617-401">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-401">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="e5617-402">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e5617-402">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e5617-403">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e5617-403">SDK version</span></span> | <span data-ttu-id="e5617-404">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e5617-404">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e5617-405">3.1</span><span class="sxs-lookup"><span data-stu-id="e5617-405">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e5617-406">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-406">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e5617-407">2.2</span><span class="sxs-lookup"><span data-stu-id="e5617-407">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="e5617-408">2.1</span><span class="sxs-lookup"><span data-stu-id="e5617-408">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="e5617-409">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="e5617-409">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="e5617-410">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-410">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e5617-411">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-411">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="e5617-412">page</span><span class="sxs-lookup"><span data-stu-id="e5617-412">page</span></span>

- <span data-ttu-id="e5617-413">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-413">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="e5617-414">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="e5617-414">Namespace for the generated code.</span></span> <span data-ttu-id="e5617-415">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="e5617-415">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="e5617-416">Crée la page sans PageModel.</span><span class="sxs-lookup"><span data-stu-id="e5617-416">Creates the page without a PageModel.</span></span>

<span data-ttu-id="e5617-417">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-417">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="e5617-418">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="e5617-418">viewimports, proto</span></span>

- <span data-ttu-id="e5617-419">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-419">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="e5617-420">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="e5617-420">Namespace for the generated code.</span></span> <span data-ttu-id="e5617-421">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="e5617-421">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="e5617-422">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-422">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="e5617-423">blazorserver</span><span class="sxs-lookup"><span data-stu-id="e5617-423">blazorserver</span></span>

- <span data-ttu-id="e5617-424">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-424">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e5617-425">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e5617-425">The type of authentication to use.</span></span> <span data-ttu-id="e5617-426">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5617-426">The possible values are:</span></span>

  - <span data-ttu-id="e5617-427">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="e5617-427">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e5617-428">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="e5617-428">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e5617-429">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e5617-429">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e5617-430">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="e5617-430">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e5617-431">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="e5617-431">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="e5617-432">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="e5617-432">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e5617-433">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-433">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e5617-434">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-434">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-435">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="e5617-435">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e5617-436">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-436">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e5617-437">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-437">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="e5617-438">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-438">The reset password policy ID for this project.</span></span> <span data-ttu-id="e5617-439">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-439">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="e5617-440">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-440">The edit profile policy ID for this project.</span></span> <span data-ttu-id="e5617-441">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-441">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e5617-442">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-442">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e5617-443">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-443">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="e5617-444">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e5617-444">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e5617-445">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-445">The Client ID for this project.</span></span> <span data-ttu-id="e5617-446">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-446">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="e5617-447">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e5617-447">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e5617-448">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e5617-448">The domain for the directory tenant.</span></span> <span data-ttu-id="e5617-449">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-449">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-450">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e5617-450">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e5617-451">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-451">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e5617-452">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-452">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e5617-453">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e5617-453">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="e5617-454">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="e5617-454">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="e5617-455">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-455">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-456">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="e5617-456">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e5617-457">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e5617-457">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e5617-458">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-458">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e5617-459">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e5617-459">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e5617-460">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e5617-460">Turns off HTTPS.</span></span> <span data-ttu-id="e5617-461">Cette option s’applique uniquement si `Individual` , `IndividualB2C` , `SingleOrg` ou `MultiOrg` ne sont pas utilisés pour `--auth` .</span><span class="sxs-lookup"><span data-stu-id="e5617-461">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e5617-462">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="e5617-462">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e5617-463">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-463">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e5617-464">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-464">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e5617-465">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-465">\*\*_</span></span>

### <a name="blazorwasm"></a><span data-ttu-id="e5617-466">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="e5617-466">blazorwasm</span></span>

- <span data-ttu-id="e5617-467">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-467">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="e5617-468">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-468">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="e5617-469">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e5617-469">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e5617-470">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e5617-470">SDK version</span></span> | <span data-ttu-id="e5617-471">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e5617-471">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e5617-472">5.0</span><span class="sxs-lookup"><span data-stu-id="e5617-472">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="e5617-473">3.1</span><span class="sxs-lookup"><span data-stu-id="e5617-473">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="e5617-474">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-474">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="e5617-475">Comprend un hôte de ASP.NET Core pour l' :::no-loc(Blazor)::: :::no-loc(WebAssembly)::: application.</span><span class="sxs-lookup"><span data-stu-id="e5617-475">Includes an ASP.NET Core host for the :::no-loc(Blazor)::: :::no-loc(WebAssembly)::: app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="e5617-476">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e5617-476">The type of authentication to use.</span></span> <span data-ttu-id="e5617-477">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5617-477">The possible values are:</span></span>

  - <span data-ttu-id="e5617-478">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="e5617-478">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e5617-479">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="e5617-479">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e5617-480">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e5617-480">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e5617-481">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="e5617-481">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="e5617-482">Autorité du fournisseur OIDC.</span><span class="sxs-lookup"><span data-stu-id="e5617-482">The authority of the OIDC provider.</span></span> <span data-ttu-id="e5617-483">À utiliser avec l’authentification `Individual`.</span><span class="sxs-lookup"><span data-stu-id="e5617-483">Use with `Individual` authentication.</span></span> <span data-ttu-id="e5617-484">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e5617-484">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e5617-485">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-485">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e5617-486">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-486">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-487">La valeur par défaut est `https://aadB2CInstance.b2clogin.com/`.</span><span class="sxs-lookup"><span data-stu-id="e5617-487">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e5617-488">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-488">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e5617-489">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-489">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e5617-490">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-490">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e5617-491">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-491">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e5617-492">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e5617-492">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e5617-493">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-493">The Client ID for this project.</span></span> <span data-ttu-id="e5617-494">Utilisez avec `IndividualB2C` `SingleOrg` `Individual` l’authentification, ou dans des scénarios autonomes.</span><span class="sxs-lookup"><span data-stu-id="e5617-494">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="e5617-495">La valeur par défaut est `33333333-3333-3333-33333333333333333`.</span><span class="sxs-lookup"><span data-stu-id="e5617-495">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e5617-496">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e5617-496">The domain for the directory tenant.</span></span> <span data-ttu-id="e5617-497">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-497">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-498">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e5617-498">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="e5617-499">URI ID d’application de l’API serveur que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="e5617-499">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="e5617-500">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-500">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-501">La valeur par défaut est `api.id.uri`.</span><span class="sxs-lookup"><span data-stu-id="e5617-501">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="e5617-502">ID client de l’API que le serveur héberge.</span><span class="sxs-lookup"><span data-stu-id="e5617-502">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="e5617-503">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-503">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-504">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e5617-504">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="e5617-505">Étendue de l’API que le client doit demander pour approvisionner un jeton d’accès.</span><span class="sxs-lookup"><span data-stu-id="e5617-505">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="e5617-506">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-506">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-507">La valeur par défaut est `user_impersonation`.</span><span class="sxs-lookup"><span data-stu-id="e5617-507">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e5617-508">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-508">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e5617-509">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-509">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e5617-510">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e5617-510">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e5617-511">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e5617-511">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e5617-512">S’applique uniquement à `SingleOrg` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="e5617-512">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e5617-513">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e5617-513">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="e5617-514">produit une application Web progressive (PWA) qui prend en charge l’installation et l’utilisation hors connexion.</span><span class="sxs-lookup"><span data-stu-id="e5617-514">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="e5617-515">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e5617-515">Turns off HTTPS.</span></span> <span data-ttu-id="e5617-516">Cette option s’applique uniquement si `Individual` , `IndividualB2C` ou `SingleOrg` ne sont pas utilisés pour `--auth` .</span><span class="sxs-lookup"><span data-stu-id="e5617-516">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e5617-517">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="e5617-517">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e5617-518">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-518">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="e5617-519">URL de l’API à appeler à partir de l’application Web.</span><span class="sxs-lookup"><span data-stu-id="e5617-519">URL of the API to call from the web app.</span></span> <span data-ttu-id="e5617-520">S’applique uniquement à `SingleOrg` ou à `IndividualB2C` l’authentification sans ASP.net Core hôte spécifié.</span><span class="sxs-lookup"><span data-stu-id="e5617-520">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="e5617-521">La valeur par défaut est `https://graph.microsoft.com/v1.0/me`.</span><span class="sxs-lookup"><span data-stu-id="e5617-521">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="e5617-522">Spécifie si l’application Web appelle Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="e5617-522">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="e5617-523">S’applique uniquement à `SingleOrg` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="e5617-523">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="e5617-524">Étendues à demander pour appeler l’API à partir de l’application Web.</span><span class="sxs-lookup"><span data-stu-id="e5617-524">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="e5617-525">S’applique uniquement à `SingleOrg` ou à `IndividualB2C` l’authentification sans ASP.net Core hôte spécifié.</span><span class="sxs-lookup"><span data-stu-id="e5617-525">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="e5617-526">La valeur par défaut est `user.read`.</span><span class="sxs-lookup"><span data-stu-id="e5617-526">The default is `user.read`.</span></span>

<span data-ttu-id="e5617-527">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-527">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="e5617-528">web</span><span class="sxs-lookup"><span data-stu-id="e5617-528">web</span></span>

- <span data-ttu-id="e5617-529">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-529">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="e5617-530">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e5617-530">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e5617-531">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-531">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e5617-532">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e5617-532">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e5617-533">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e5617-533">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e5617-534">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e5617-534">SDK version</span></span> | <span data-ttu-id="e5617-535">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e5617-535">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e5617-536">3.1</span><span class="sxs-lookup"><span data-stu-id="e5617-536">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e5617-537">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-537">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e5617-538">2.1</span><span class="sxs-lookup"><span data-stu-id="e5617-538">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="e5617-539">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e5617-540">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e5617-540">Turns off HTTPS.</span></span>

<span data-ttu-id="e5617-541">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-541">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="e5617-542">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="e5617-542">mvc, webapp</span></span>

- <span data-ttu-id="e5617-543">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-543">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e5617-544">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e5617-544">The type of authentication to use.</span></span> <span data-ttu-id="e5617-545">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5617-545">The possible values are:</span></span>

  - <span data-ttu-id="e5617-546">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="e5617-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e5617-547">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="e5617-547">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="e5617-548">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e5617-548">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e5617-549">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="e5617-549">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e5617-550">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="e5617-550">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="e5617-551">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="e5617-551">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e5617-552">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-552">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e5617-553">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-553">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-554">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="e5617-554">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e5617-555">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-555">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e5617-556">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-556">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="e5617-557">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-557">The reset password policy ID for this project.</span></span> <span data-ttu-id="e5617-558">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-558">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="e5617-559">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-559">The edit profile policy ID for this project.</span></span> <span data-ttu-id="e5617-560">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-560">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e5617-561">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-561">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e5617-562">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-562">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="e5617-563">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e5617-563">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e5617-564">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-564">The Client ID for this project.</span></span> <span data-ttu-id="e5617-565">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-565">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="e5617-566">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e5617-566">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e5617-567">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e5617-567">The domain for the directory tenant.</span></span> <span data-ttu-id="e5617-568">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-568">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-569">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e5617-569">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e5617-570">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-570">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e5617-571">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-571">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e5617-572">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e5617-572">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="e5617-573">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="e5617-573">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="e5617-574">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-574">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-575">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="e5617-575">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e5617-576">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e5617-576">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e5617-577">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-577">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e5617-578">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e5617-578">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e5617-579">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e5617-579">Turns off HTTPS.</span></span> <span data-ttu-id="e5617-580">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="e5617-580">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e5617-581">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="e5617-581">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e5617-582">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-582">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e5617-583">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-583">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e5617-584">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e5617-584">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="e5617-585">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e5617-585">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e5617-586">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e5617-586">SDK version</span></span> | <span data-ttu-id="e5617-587">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e5617-587">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e5617-588">3.1</span><span class="sxs-lookup"><span data-stu-id="e5617-588">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e5617-589">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-589">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="e5617-590">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-590">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="e5617-591">Comprend BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-591">Includes BrowserLink in the project.</span></span> <span data-ttu-id="e5617-592">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2 et 3,1.</span><span class="sxs-lookup"><span data-stu-id="e5617-592">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="e5617-593">Détermine si le projet est configuré pour utiliser la [compilation du runtime Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) dans les versions Debug.</span><span class="sxs-lookup"><span data-stu-id="e5617-593">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="e5617-594">Option disponible depuis le kit de développement logiciel (SDK) 3.1.201 .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5617-594">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="e5617-595">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-595">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="e5617-596">angulaire, réaction</span><span class="sxs-lookup"><span data-stu-id="e5617-596">angular, react</span></span>

- <span data-ttu-id="e5617-597">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-597">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e5617-598">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e5617-598">The type of authentication to use.</span></span> <span data-ttu-id="e5617-599">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e5617-599">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="e5617-600">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5617-600">The possible values are:</span></span>

  - <span data-ttu-id="e5617-601">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="e5617-601">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e5617-602">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="e5617-602">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e5617-603">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e5617-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e5617-604">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-604">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e5617-605">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e5617-605">Turns off HTTPS.</span></span> <span data-ttu-id="e5617-606">Cette option s’applique uniquement si l’authentification est `None` .</span><span class="sxs-lookup"><span data-stu-id="e5617-606">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e5617-607">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="e5617-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e5617-608">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-608">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-609">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e5617-609">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e5617-610">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-610">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e5617-611">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e5617-611">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e5617-612">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e5617-612">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e5617-613">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e5617-613">SDK version</span></span> | <span data-ttu-id="e5617-614">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e5617-614">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e5617-615">3.1</span><span class="sxs-lookup"><span data-stu-id="e5617-615">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e5617-616">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-616">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e5617-617">2.1</span><span class="sxs-lookup"><span data-stu-id="e5617-617">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="e5617-618">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-618">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="e5617-619">reactredux</span><span class="sxs-lookup"><span data-stu-id="e5617-619">reactredux</span></span>

- <span data-ttu-id="e5617-620">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-620">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="e5617-621">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e5617-621">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e5617-622">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-622">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e5617-623">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e5617-623">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e5617-624">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e5617-624">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e5617-625">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e5617-625">SDK version</span></span> | <span data-ttu-id="e5617-626">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e5617-626">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e5617-627">3.1</span><span class="sxs-lookup"><span data-stu-id="e5617-627">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e5617-628">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-628">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e5617-629">2.1</span><span class="sxs-lookup"><span data-stu-id="e5617-629">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="e5617-630">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-630">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="e5617-631">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e5617-631">Turns off HTTPS.</span></span>

<span data-ttu-id="e5617-632">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-632">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="e5617-633">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="e5617-633">razorclasslib</span></span>

- <span data-ttu-id="e5617-634">_ *`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-634">_ *`--no-restore`*\*</span></span>

  <span data-ttu-id="e5617-635">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-635">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="e5617-636">Prend en charge l’ajout de pages et de vues Razor traditionnelles en plus des composants de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="e5617-636">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="e5617-637">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e5617-637">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="e5617-638">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-638">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="e5617-639">webapi</span><span class="sxs-lookup"><span data-stu-id="e5617-639">webapi</span></span>

- <span data-ttu-id="e5617-640">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-640">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="e5617-641">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e5617-641">The type of authentication to use.</span></span> <span data-ttu-id="e5617-642">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5617-642">The possible values are:</span></span>

  - <span data-ttu-id="e5617-643">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="e5617-643">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="e5617-644">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="e5617-644">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="e5617-645">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="e5617-645">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="e5617-646">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="e5617-646">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="e5617-647">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-647">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e5617-648">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-648">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e5617-649">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="e5617-649">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="e5617-650">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-650">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e5617-651">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="e5617-651">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="e5617-652">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-652">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e5617-653">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-653">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e5617-654">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="e5617-654">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="e5617-655">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-655">The Client ID for this project.</span></span> <span data-ttu-id="e5617-656">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-656">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="e5617-657">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="e5617-657">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="e5617-658">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e5617-658">The domain for the directory tenant.</span></span> <span data-ttu-id="e5617-659">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-659">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="e5617-660">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="e5617-660">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="e5617-661">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="e5617-661">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e5617-662">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="e5617-662">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e5617-663">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="e5617-663">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="e5617-664">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="e5617-664">Allows this application read-access to the directory.</span></span> <span data-ttu-id="e5617-665">S’applique uniquement à `SingleOrg` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="e5617-665">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="e5617-666">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e5617-666">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="e5617-667">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="e5617-667">Turns off HTTPS.</span></span> <span data-ttu-id="e5617-668">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="e5617-668">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="e5617-669">Cette option s’applique uniquement si `IndividualB2C` ou `SingleOrg` ne sont pas utilisés pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="e5617-669">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="e5617-670">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="e5617-670">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e5617-671">S’applique uniquement à `IndividualB2C` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="e5617-671">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e5617-672">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="e5617-672">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e5617-673">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e5617-673">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="e5617-674">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="e5617-674">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="e5617-675">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="e5617-675">SDK version</span></span> | <span data-ttu-id="e5617-676">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="e5617-676">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="e5617-677">3.1</span><span class="sxs-lookup"><span data-stu-id="e5617-677">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="e5617-678">3.0</span><span class="sxs-lookup"><span data-stu-id="e5617-678">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="e5617-679">2.1</span><span class="sxs-lookup"><span data-stu-id="e5617-679">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="e5617-680">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="e5617-680">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e5617-681">\*\*_</span><span class="sxs-lookup"><span data-stu-id="e5617-681">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="e5617-682">globaljson</span><span class="sxs-lookup"><span data-stu-id="e5617-682">globaljson</span></span>

- <span data-ttu-id="e5617-683">_ *`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="e5617-683">_ *`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="e5617-684">Spécifie la version de la kit SDK .NET Core à utiliser dans le fichier *global.js* .</span><span class="sxs-lookup"><span data-stu-id="e5617-684">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="e5617-685">Exemples</span><span class="sxs-lookup"><span data-stu-id="e5617-685">Examples</span></span>

- <span data-ttu-id="e5617-686">Créez un projet d’application console C# en spécifiant le nom du modèle :</span><span class="sxs-lookup"><span data-stu-id="e5617-686">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="e5617-687">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="e5617-687">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="e5617-688">Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié :</span><span class="sxs-lookup"><span data-stu-id="e5617-688">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="e5617-689">Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :</span><span class="sxs-lookup"><span data-stu-id="e5617-689">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="e5617-690">Créez un projet xUnit :</span><span class="sxs-lookup"><span data-stu-id="e5617-690">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="e5617-691">Répertorier tous les modèles disponibles pour les modèles d’application à page unique (SPA) :</span><span class="sxs-lookup"><span data-stu-id="e5617-691">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="e5617-692">Liste de tous les modèles correspondant à la sous-chaîne *we*.</span><span class="sxs-lookup"><span data-stu-id="e5617-692">List all templates matching the *we* substring.</span></span> <span data-ttu-id="e5617-693">Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.</span><span class="sxs-lookup"><span data-stu-id="e5617-693">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="e5617-694">Tentative d’appel du modèle correspondant à *ng*.</span><span class="sxs-lookup"><span data-stu-id="e5617-694">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="e5617-695">Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.</span><span class="sxs-lookup"><span data-stu-id="e5617-695">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="e5617-696">Installez la version 2,0 des modèles SPA pour ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="e5617-696">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="e5617-697">Répertoriez les modèles installés et les détails les concernant, notamment comment les désinstaller :</span><span class="sxs-lookup"><span data-stu-id="e5617-697">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="e5617-698">Créez un *global.js* dans le répertoire actif en définissant la version du kit de développement logiciel (SDK) sur 3.1.101 :</span><span class="sxs-lookup"><span data-stu-id="e5617-698">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="e5617-699">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5617-699">See also</span></span>

- [<span data-ttu-id="e5617-700">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="e5617-700">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="e5617-701">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="e5617-701">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="e5617-702">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="e5617-702">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="e5617-703">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="e5617-703">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
