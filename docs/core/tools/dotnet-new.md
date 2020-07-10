---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
no-loc:
- Blazor
- WebAssembly
ms.date: 04/10/2020
ms.openlocfilehash: ec41b3b79ed5eded7c9124d3e4d95c658ee39580
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173118"
---
# <a name="dotnet-new"></a><span data-ttu-id="f5cd7-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="f5cd7-103">dotnet new</span></span>

<span data-ttu-id="f5cd7-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="f5cd7-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f5cd7-105">Nom</span><span class="sxs-lookup"><span data-stu-id="f5cd7-105">Name</span></span>

<span data-ttu-id="f5cd7-106">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f5cd7-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="f5cd7-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="f5cd7-108">Description</span><span class="sxs-lookup"><span data-stu-id="f5cd7-108">Description</span></span>

<span data-ttu-id="f5cd7-109">La `dotnet new` commande crée un projet .net Core ou d’autres artefacts basés sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="f5cd7-110">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="f5cd7-111">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="f5cd7-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="f5cd7-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="f5cd7-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="f5cd7-113">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="f5cd7-114">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="f5cd7-115">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="f5cd7-116">Vous pouvez exécuter `dotnet new --list` ou `dotnet new -l` pour afficher la liste de tous les modèles installés.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="f5cd7-117">Si la `TEMPLATE` valeur ne correspond pas exactement au texte de la colonne **Templates** ou **Short Name** de la table retournée, une correspondance de sous-chaînes est effectuée sur ces deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="f5cd7-118">À compter du kit de développement logiciel (SDK) .NET Core 3,0, l’interface CLI recherche des modèles dans NuGet.org quand vous appelez la `dotnet new` commande dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="f5cd7-119">Si l’interface CLI ne peut pas trouver de correspondance de modèle lors de l’appel `dotnet new` de, pas encore partiel.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="f5cd7-120">Si une version plus récente du modèle est disponible.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="f5cd7-121">Dans ce cas, le projet ou l’artefact est créé, mais l’interface CLI vous avertit d’une version mise à jour du modèle.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="f5cd7-122">Le tableau suivant répertorie les modèles qui sont préinstallés avec le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="f5cd7-123">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="f5cd7-124">Cliquez sur le lien nom abrégé pour afficher les options de modèle spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="f5cd7-125">Modèles</span><span class="sxs-lookup"><span data-stu-id="f5cd7-125">Templates</span></span>                                    | <span data-ttu-id="f5cd7-126">Nom court</span><span class="sxs-lookup"><span data-stu-id="f5cd7-126">Short name</span></span>                      | <span data-ttu-id="f5cd7-127">Langage</span><span class="sxs-lookup"><span data-stu-id="f5cd7-127">Language</span></span>     | <span data-ttu-id="f5cd7-128">Balises</span><span class="sxs-lookup"><span data-stu-id="f5cd7-128">Tags</span></span>                                  | <span data-ttu-id="f5cd7-129">Présent</span><span class="sxs-lookup"><span data-stu-id="f5cd7-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="f5cd7-130">Application console</span><span class="sxs-lookup"><span data-stu-id="f5cd7-130">Console Application</span></span>                          | [<span data-ttu-id="f5cd7-131">console</span><span class="sxs-lookup"><span data-stu-id="f5cd7-131">console</span></span>](#console)             | <span data-ttu-id="f5cd7-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f5cd7-132">[C#], F#, VB</span></span> | <span data-ttu-id="f5cd7-133">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="f5cd7-133">Common/Console</span></span>                        | <span data-ttu-id="f5cd7-134">1.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-134">1.0</span></span>        |
| <span data-ttu-id="f5cd7-135">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="f5cd7-135">Class library</span></span>                                | [<span data-ttu-id="f5cd7-136">classlib</span><span class="sxs-lookup"><span data-stu-id="f5cd7-136">classlib</span></span>](#classlib)           | <span data-ttu-id="f5cd7-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f5cd7-137">[C#], F#, VB</span></span> | <span data-ttu-id="f5cd7-138">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="f5cd7-138">Common/Library</span></span>                        | <span data-ttu-id="f5cd7-139">1.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-139">1.0</span></span>        |
| <span data-ttu-id="f5cd7-140">Application WPF</span><span class="sxs-lookup"><span data-stu-id="f5cd7-140">WPF Application</span></span>                              | [<span data-ttu-id="f5cd7-141">WPF</span><span class="sxs-lookup"><span data-stu-id="f5cd7-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="f5cd7-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-142">[C#]</span></span>         | <span data-ttu-id="f5cd7-143">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="f5cd7-143">Common/WPF</span></span>                            | <span data-ttu-id="f5cd7-144">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-144">3.0</span></span>        |
| <span data-ttu-id="f5cd7-145">Bibliothèque de classes WPF</span><span class="sxs-lookup"><span data-stu-id="f5cd7-145">WPF Class library</span></span>                            | [<span data-ttu-id="f5cd7-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="f5cd7-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="f5cd7-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-147">[C#]</span></span>         | <span data-ttu-id="f5cd7-148">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="f5cd7-148">Common/WPF</span></span>                            | <span data-ttu-id="f5cd7-149">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-149">3.0</span></span>        |
| <span data-ttu-id="f5cd7-150">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="f5cd7-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="f5cd7-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="f5cd7-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="f5cd7-152">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-152">[C#]</span></span>         | <span data-ttu-id="f5cd7-153">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="f5cd7-153">Common/WPF</span></span>                            | <span data-ttu-id="f5cd7-154">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-154">3.0</span></span>        |
| <span data-ttu-id="f5cd7-155">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="f5cd7-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="f5cd7-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="f5cd7-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="f5cd7-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-157">[C#]</span></span>         | <span data-ttu-id="f5cd7-158">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="f5cd7-158">Common/WPF</span></span>                            | <span data-ttu-id="f5cd7-159">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-159">3.0</span></span>        |
| <span data-ttu-id="f5cd7-160">Application Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="f5cd7-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="f5cd7-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="f5cd7-161">winforms</span></span>](#winforms)           | <span data-ttu-id="f5cd7-162">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-162">[C#]</span></span>         | <span data-ttu-id="f5cd7-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="f5cd7-163">Common/WinForms</span></span>                       | <span data-ttu-id="f5cd7-164">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-164">3.0</span></span>        |
| <span data-ttu-id="f5cd7-165">Bibliothèque de classes Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="f5cd7-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="f5cd7-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="f5cd7-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="f5cd7-167">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-167">[C#]</span></span>         | <span data-ttu-id="f5cd7-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="f5cd7-168">Common/WinForms</span></span>                       | <span data-ttu-id="f5cd7-169">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-169">3.0</span></span>        |
| <span data-ttu-id="f5cd7-170">Service Worker</span><span class="sxs-lookup"><span data-stu-id="f5cd7-170">Worker Service</span></span>                               | [<span data-ttu-id="f5cd7-171">collabor</span><span class="sxs-lookup"><span data-stu-id="f5cd7-171">worker</span></span>](#web-others)           | <span data-ttu-id="f5cd7-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-172">[C#]</span></span>         | <span data-ttu-id="f5cd7-173">Commun/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="f5cd7-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="f5cd7-174">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-174">3.0</span></span>        |
| <span data-ttu-id="f5cd7-175">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="f5cd7-175">Unit Test Project</span></span>                            | [<span data-ttu-id="f5cd7-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="f5cd7-176">mstest</span></span>](#test)                 | <span data-ttu-id="f5cd7-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f5cd7-177">[C#], F#, VB</span></span> | <span data-ttu-id="f5cd7-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="f5cd7-178">Test/MSTest</span></span>                           | <span data-ttu-id="f5cd7-179">1.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-179">1.0</span></span>        |
| <span data-ttu-id="f5cd7-180">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="f5cd7-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="f5cd7-181">nunit</span><span class="sxs-lookup"><span data-stu-id="f5cd7-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="f5cd7-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f5cd7-182">[C#], F#, VB</span></span> | <span data-ttu-id="f5cd7-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="f5cd7-183">Test/NUnit</span></span>                            | <span data-ttu-id="f5cd7-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="f5cd7-184">2.1.400</span></span>    |
| <span data-ttu-id="f5cd7-185">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="f5cd7-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="f5cd7-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f5cd7-186">[C#], F#, VB</span></span> | <span data-ttu-id="f5cd7-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="f5cd7-187">Test/NUnit</span></span>                            | <span data-ttu-id="f5cd7-188">2.2</span><span class="sxs-lookup"><span data-stu-id="f5cd7-188">2.2</span></span>        |
| <span data-ttu-id="f5cd7-189">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="f5cd7-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="f5cd7-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="f5cd7-190">xunit</span></span>](#test)                  | <span data-ttu-id="f5cd7-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f5cd7-191">[C#], F#, VB</span></span> | <span data-ttu-id="f5cd7-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="f5cd7-192">Test/xUnit</span></span>                            | <span data-ttu-id="f5cd7-193">1.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-193">1.0</span></span>        |
| <span data-ttu-id="f5cd7-194">Composant Razor</span><span class="sxs-lookup"><span data-stu-id="f5cd7-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="f5cd7-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-195">[C#]</span></span>         | <span data-ttu-id="f5cd7-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f5cd7-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="f5cd7-197">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-197">3.0</span></span>        |
| <span data-ttu-id="f5cd7-198">Page Razor</span><span class="sxs-lookup"><span data-stu-id="f5cd7-198">Razor Page</span></span>                                   | [<span data-ttu-id="f5cd7-199">pagination</span><span class="sxs-lookup"><span data-stu-id="f5cd7-199">page</span></span>](#page)                   | <span data-ttu-id="f5cd7-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-200">[C#]</span></span>         | <span data-ttu-id="f5cd7-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f5cd7-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="f5cd7-202">2.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-202">2.0</span></span>        |
| <span data-ttu-id="f5cd7-203">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="f5cd7-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="f5cd7-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="f5cd7-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="f5cd7-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-205">[C#]</span></span>         | <span data-ttu-id="f5cd7-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f5cd7-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="f5cd7-207">2.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-207">2.0</span></span>        |
| <span data-ttu-id="f5cd7-208">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="f5cd7-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="f5cd7-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-209">[C#]</span></span>         | <span data-ttu-id="f5cd7-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f5cd7-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="f5cd7-211">2.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-211">2.0</span></span>        |
| Blazor<span data-ttu-id="f5cd7-212">Application serveur</span><span class="sxs-lookup"><span data-stu-id="f5cd7-212"> Server App</span></span>                            | [<span data-ttu-id="f5cd7-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="f5cd7-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="f5cd7-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-214">[C#]</span></span>         | <span data-ttu-id="f5cd7-215">InternetBlazor</span><span class="sxs-lookup"><span data-stu-id="f5cd7-215">Web/Blazor</span></span>                            | <span data-ttu-id="f5cd7-216">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-216">3.0</span></span>        |
| Blazor<span data-ttu-id="f5cd7-217">WebAssemblyApplication</span><span class="sxs-lookup"><span data-stu-id="f5cd7-217"> WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="f5cd7-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-218">[C#]</span></span>         | <span data-ttu-id="f5cd7-219">InternetBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="f5cd7-219">Web/Blazor/WebAssembly</span></span>                            | <span data-ttu-id="f5cd7-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="f5cd7-220">3.1.300</span></span>    |
| <span data-ttu-id="f5cd7-221">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="f5cd7-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="f5cd7-222">Internet</span><span class="sxs-lookup"><span data-stu-id="f5cd7-222">web</span></span>](#web)                     | <span data-ttu-id="f5cd7-223">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f5cd7-223">[C#], F#</span></span>     | <span data-ttu-id="f5cd7-224">Web/vides</span><span class="sxs-lookup"><span data-stu-id="f5cd7-224">Web/Empty</span></span>                             | <span data-ttu-id="f5cd7-225">1.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-225">1.0</span></span>        |
| <span data-ttu-id="f5cd7-226">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="f5cd7-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="f5cd7-227">MVC</span><span class="sxs-lookup"><span data-stu-id="f5cd7-227">mvc</span></span>](#web-options)             | <span data-ttu-id="f5cd7-228">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f5cd7-228">[C#], F#</span></span>     | <span data-ttu-id="f5cd7-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="f5cd7-229">Web/MVC</span></span>                               | <span data-ttu-id="f5cd7-230">1.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-230">1.0</span></span>        |
| <span data-ttu-id="f5cd7-231">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f5cd7-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="f5cd7-232">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="f5cd7-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="f5cd7-233">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-233">[C#]</span></span>         | <span data-ttu-id="f5cd7-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="f5cd7-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="f5cd7-235">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="f5cd7-236">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="f5cd7-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="f5cd7-237">oblique</span><span class="sxs-lookup"><span data-stu-id="f5cd7-237">angular</span></span>](#spa)                 | <span data-ttu-id="f5cd7-238">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-238">[C#]</span></span>         | <span data-ttu-id="f5cd7-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f5cd7-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f5cd7-240">2.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-240">2.0</span></span>        |
| <span data-ttu-id="f5cd7-241">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="f5cd7-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="f5cd7-242">réagir</span><span class="sxs-lookup"><span data-stu-id="f5cd7-242">react</span></span>](#spa)                   | <span data-ttu-id="f5cd7-243">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-243">[C#]</span></span>         | <span data-ttu-id="f5cd7-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f5cd7-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f5cd7-245">2.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-245">2.0</span></span>        |
| <span data-ttu-id="f5cd7-246">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="f5cd7-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="f5cd7-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="f5cd7-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="f5cd7-248">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-248">[C#]</span></span>         | <span data-ttu-id="f5cd7-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f5cd7-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f5cd7-250">2.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-250">2.0</span></span>        |
| <span data-ttu-id="f5cd7-251">Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="f5cd7-251">Razor Class Library</span></span>                          | [<span data-ttu-id="f5cd7-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="f5cd7-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="f5cd7-253">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-253">[C#]</span></span>         | <span data-ttu-id="f5cd7-254">Web/Razor/Library/Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="f5cd7-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="f5cd7-255">2.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-255">2.1</span></span>        |
| <span data-ttu-id="f5cd7-256">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f5cd7-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="f5cd7-257">WebAPI</span><span class="sxs-lookup"><span data-stu-id="f5cd7-257">webapi</span></span>](#webapi)               | <span data-ttu-id="f5cd7-258">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f5cd7-258">[C#], F#</span></span>     | <span data-ttu-id="f5cd7-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="f5cd7-259">Web/WebAPI</span></span>                            | <span data-ttu-id="f5cd7-260">1.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-260">1.0</span></span>        |
| <span data-ttu-id="f5cd7-261">ASP.NET Core Service gRPC</span><span class="sxs-lookup"><span data-stu-id="f5cd7-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="f5cd7-262">GRPC</span><span class="sxs-lookup"><span data-stu-id="f5cd7-262">grpc</span></span>](#web-others)             | <span data-ttu-id="f5cd7-263">[C#]</span><span class="sxs-lookup"><span data-stu-id="f5cd7-263">[C#]</span></span>         | <span data-ttu-id="f5cd7-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="f5cd7-264">Web/gRPC</span></span>                              | <span data-ttu-id="f5cd7-265">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-265">3.0</span></span>        |
| <span data-ttu-id="f5cd7-266">fichier gitignore dotnet</span><span class="sxs-lookup"><span data-stu-id="f5cd7-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="f5cd7-267">Config</span><span class="sxs-lookup"><span data-stu-id="f5cd7-267">Config</span></span>                                | <span data-ttu-id="f5cd7-268">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-268">3.0</span></span>        |
| <span data-ttu-id="f5cd7-269">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="f5cd7-269">global.json file</span></span>                             | [<span data-ttu-id="f5cd7-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="f5cd7-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="f5cd7-271">Config</span><span class="sxs-lookup"><span data-stu-id="f5cd7-271">Config</span></span>                                | <span data-ttu-id="f5cd7-272">2.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-272">2.0</span></span>        |
| <span data-ttu-id="f5cd7-273">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="f5cd7-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="f5cd7-274">Config</span><span class="sxs-lookup"><span data-stu-id="f5cd7-274">Config</span></span>                                | <span data-ttu-id="f5cd7-275">1.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-275">1.0</span></span>        |
| <span data-ttu-id="f5cd7-276">Fichier manifeste de l’outil local dotnet</span><span class="sxs-lookup"><span data-stu-id="f5cd7-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="f5cd7-277">Config</span><span class="sxs-lookup"><span data-stu-id="f5cd7-277">Config</span></span>                                | <span data-ttu-id="f5cd7-278">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-278">3.0</span></span>        |
| <span data-ttu-id="f5cd7-279">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="f5cd7-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="f5cd7-280">Config</span><span class="sxs-lookup"><span data-stu-id="f5cd7-280">Config</span></span>                                | <span data-ttu-id="f5cd7-281">1.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-281">1.0</span></span>        |
| <span data-ttu-id="f5cd7-282">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="f5cd7-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="f5cd7-283">Solution</span><span class="sxs-lookup"><span data-stu-id="f5cd7-283">Solution</span></span>                              | <span data-ttu-id="f5cd7-284">1.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-284">1.0</span></span>        |
| <span data-ttu-id="f5cd7-285">Fichier de mémoire tampon de protocole</span><span class="sxs-lookup"><span data-stu-id="f5cd7-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="f5cd7-286">proto</span><span class="sxs-lookup"><span data-stu-id="f5cd7-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="f5cd7-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="f5cd7-287">Web/gRPC</span></span>                              | <span data-ttu-id="f5cd7-288">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="f5cd7-289">Options</span><span class="sxs-lookup"><span data-stu-id="f5cd7-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="f5cd7-290">Affiche un récapitulatif de ce qui se passerait si la commande donnée était exécutée (si cela donnerait lieu à la création d’un modèle).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="f5cd7-291">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="f5cd7-292">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="f5cd7-293">Cela est obligatoire lorsque le modèle choisi remplace les fichiers existants dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f5cd7-294">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-294">Prints out help for the command.</span></span> <span data-ttu-id="f5cd7-295">Elle peut être appelée pour la `dotnet new` commande elle-même ou pour n’importe quel modèle.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="f5cd7-296">Par exemple, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="f5cd7-297">Installe un pack de modèles à partir du `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f5cd7-298">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="f5cd7-299">Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="f5cd7-300">Consultez un exemple dans la section [exemples](#examples) .</span><span class="sxs-lookup"><span data-stu-id="f5cd7-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="f5cd7-301">Si une version du modèle a déjà été installée lorsque vous exécutez cette commande, le modèle sera mis à jour vers la version spécifiée, ou vers la version stable la plus récente si aucune version n’a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="f5cd7-302">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="f5cd7-303">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="f5cd7-304">Si aucun nom n’est spécifié, répertorie tous les modèles.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="f5cd7-305">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-305">The language of the template to create.</span></span> <span data-ttu-id="f5cd7-306">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f5cd7-307">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f5cd7-308">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="f5cd7-309">Dans ce cas, mettez la valeur du paramètre de langue entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="f5cd7-310">Par exemple, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="f5cd7-311">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-311">The name for the created output.</span></span> <span data-ttu-id="f5cd7-312">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="f5cd7-313">Spécifie une source NuGet à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="f5cd7-314">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f5cd7-315">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-315">Location to place the generated output.</span></span> <span data-ttu-id="f5cd7-316">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="f5cd7-317">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-317">Filters templates based on available types.</span></span> <span data-ttu-id="f5cd7-318">Les valeurs prédéfinies sont `project` , `item` et `other` .</span><span class="sxs-lookup"><span data-stu-id="f5cd7-318">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="f5cd7-319">Désinstalle un pack de modèles au niveau de `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f5cd7-320">Lorsque la `<PATH|NUGET_ID>` valeur n’est pas spécifiée, tous les packs de modèles actuellement installés et leurs modèles associés sont affichés.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="f5cd7-321">Lorsque vous spécifiez `NUGET_ID` , n’incluez pas le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="f5cd7-322">Si vous ne spécifiez pas de paramètre pour cette option, la commande répertorie les modèles installés et fournit des détails à leur sujet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f5cd7-323">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="f5cd7-324">Par exemple, *C:/Users/ \<USER> /documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionnera, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne le sera pas.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="f5cd7-325">N’incluez pas de barre oblique finale de répertoire finale dans le chemin d’accès de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="f5cd7-326">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés et les installe.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="f5cd7-327">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="f5cd7-328">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="f5cd7-329">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="f5cd7-330">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="f5cd7-330">Template options</span></span>

<span data-ttu-id="f5cd7-331">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-331">Each project template may have additional options available.</span></span> <span data-ttu-id="f5cd7-332">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="f5cd7-333">console</span><span class="sxs-lookup"><span data-stu-id="f5cd7-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5cd7-334">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f5cd7-335">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f5cd7-336">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f5cd7-337">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f5cd7-337">SDK version</span></span> | <span data-ttu-id="f5cd7-338">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f5cd7-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f5cd7-339">3.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f5cd7-340">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f5cd7-341">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f5cd7-342">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="f5cd7-343">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-343">Not supported for F#.</span></span> <span data-ttu-id="f5cd7-344">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f5cd7-345">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f5cd7-346">S’il est spécifié, n’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="f5cd7-347">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-347">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="f5cd7-348">classlib</span><span class="sxs-lookup"><span data-stu-id="f5cd7-348">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5cd7-349">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-349">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f5cd7-350">Valeurs : `netcoreapp<version>` pour créer une bibliothèque de classes .NET Core ou `netstandard<version>` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-350">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="f5cd7-351">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-351">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f5cd7-352">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-352">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f5cd7-353">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-353">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="f5cd7-354">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-354">Not supported for F#.</span></span> <span data-ttu-id="f5cd7-355">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-355">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f5cd7-356">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-356">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f5cd7-357">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-357">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="f5cd7-358">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="f5cd7-358">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5cd7-359">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-359">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f5cd7-360">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-360">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="f5cd7-361">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-361">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f5cd7-362">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-362">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f5cd7-363">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-363">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="f5cd7-364">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-364">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f5cd7-365">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-365">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="f5cd7-366">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="f5cd7-366">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f5cd7-367">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f5cd7-368">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="f5cd7-369">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f5cd7-370">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="f5cd7-371">Worker, GRPC</span><span class="sxs-lookup"><span data-stu-id="f5cd7-371">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5cd7-372">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-372">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f5cd7-373">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-373">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="f5cd7-374">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-374">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f5cd7-375">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-375">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f5cd7-376">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-376">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="f5cd7-377">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="f5cd7-377">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5cd7-378">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-378">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f5cd7-379">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-379">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f5cd7-380">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-380">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f5cd7-381">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f5cd7-381">SDK version</span></span> | <span data-ttu-id="f5cd7-382">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f5cd7-382">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f5cd7-383">3.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-383">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f5cd7-384">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-384">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="f5cd7-385">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-385">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f5cd7-386">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-386">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="f5cd7-387">nunit</span><span class="sxs-lookup"><span data-stu-id="f5cd7-387">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5cd7-388">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="f5cd7-389">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-389">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f5cd7-390">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f5cd7-390">SDK version</span></span> | <span data-ttu-id="f5cd7-391">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f5cd7-391">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f5cd7-392">3.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-392">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f5cd7-393">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-393">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f5cd7-394">2.2</span><span class="sxs-lookup"><span data-stu-id="f5cd7-394">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="f5cd7-395">2.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-395">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="f5cd7-396">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f5cd7-397">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-397">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="f5cd7-398">page</span><span class="sxs-lookup"><span data-stu-id="f5cd7-398">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="f5cd7-399">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-399">Namespace for the generated code.</span></span> <span data-ttu-id="f5cd7-400">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-400">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="f5cd7-401">Crée la page sans PageModel.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-401">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="f5cd7-402">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="f5cd7-402">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="f5cd7-403">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-403">Namespace for the generated code.</span></span> <span data-ttu-id="f5cd7-404">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-404">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="f5cd7-405">blazorserver</span><span class="sxs-lookup"><span data-stu-id="f5cd7-405">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f5cd7-406">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-406">The type of authentication to use.</span></span> <span data-ttu-id="f5cd7-407">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-407">The possible values are:</span></span>

  - <span data-ttu-id="f5cd7-408">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-408">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f5cd7-409">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-409">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="f5cd7-410">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-410">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f5cd7-411">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-411">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f5cd7-412">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-412">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="f5cd7-413">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-413">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f5cd7-414">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-414">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f5cd7-415">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-415">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f5cd7-416">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-416">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f5cd7-417">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-417">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f5cd7-418">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-418">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="f5cd7-419">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-419">The reset password policy ID for this project.</span></span> <span data-ttu-id="f5cd7-420">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-420">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="f5cd7-421">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-421">The edit profile policy ID for this project.</span></span> <span data-ttu-id="f5cd7-422">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-422">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f5cd7-423">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-423">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f5cd7-424">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-424">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f5cd7-425">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-425">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f5cd7-426">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-426">The Client ID for this project.</span></span> <span data-ttu-id="f5cd7-427">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-427">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f5cd7-428">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-428">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f5cd7-429">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-429">The domain for the directory tenant.</span></span> <span data-ttu-id="f5cd7-430">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-430">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f5cd7-431">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-431">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f5cd7-432">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-432">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f5cd7-433">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-433">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f5cd7-434">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-434">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="f5cd7-435">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-435">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f5cd7-436">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f5cd7-437">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-437">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f5cd7-438">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-438">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f5cd7-439">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-439">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f5cd7-440">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-440">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f5cd7-441">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-441">Turns off HTTPS.</span></span> <span data-ttu-id="f5cd7-442">Cette option s’applique uniquement si `Individual` , `IndividualB2C` , `SingleOrg` ou `MultiOrg` ne sont pas utilisés pour `--auth` .</span><span class="sxs-lookup"><span data-stu-id="f5cd7-442">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f5cd7-443">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-443">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f5cd7-444">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-444">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f5cd7-445">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-445">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="f5cd7-446">web</span><span class="sxs-lookup"><span data-stu-id="f5cd7-446">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f5cd7-447">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-447">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5cd7-448">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-448">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f5cd7-449">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-449">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f5cd7-450">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-450">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f5cd7-451">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f5cd7-451">SDK version</span></span> | <span data-ttu-id="f5cd7-452">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f5cd7-452">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f5cd7-453">3.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-453">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f5cd7-454">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-454">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f5cd7-455">2.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-455">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="f5cd7-456">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-456">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f5cd7-457">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-457">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="f5cd7-458">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="f5cd7-458">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f5cd7-459">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-459">The type of authentication to use.</span></span> <span data-ttu-id="f5cd7-460">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-460">The possible values are:</span></span>

  - <span data-ttu-id="f5cd7-461">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-461">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f5cd7-462">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-462">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="f5cd7-463">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-463">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f5cd7-464">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-464">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f5cd7-465">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-465">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="f5cd7-466">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-466">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f5cd7-467">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-467">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f5cd7-468">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-468">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f5cd7-469">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-469">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f5cd7-470">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-470">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f5cd7-471">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-471">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="f5cd7-472">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-472">The reset password policy ID for this project.</span></span> <span data-ttu-id="f5cd7-473">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-473">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="f5cd7-474">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-474">The edit profile policy ID for this project.</span></span> <span data-ttu-id="f5cd7-475">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-475">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f5cd7-476">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-476">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f5cd7-477">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-477">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f5cd7-478">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-478">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f5cd7-479">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-479">The Client ID for this project.</span></span> <span data-ttu-id="f5cd7-480">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-480">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f5cd7-481">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-481">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f5cd7-482">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-482">The domain for the directory tenant.</span></span> <span data-ttu-id="f5cd7-483">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-483">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f5cd7-484">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-484">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f5cd7-485">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-485">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f5cd7-486">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-486">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f5cd7-487">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-487">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="f5cd7-488">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-488">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f5cd7-489">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-489">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f5cd7-490">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-490">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f5cd7-491">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-491">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f5cd7-492">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-492">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f5cd7-493">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-493">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f5cd7-494">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-494">Turns off HTTPS.</span></span> <span data-ttu-id="f5cd7-495">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-495">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f5cd7-496">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-496">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f5cd7-497">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-497">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5cd7-498">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-498">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f5cd7-499">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-499">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f5cd7-500">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-500">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f5cd7-501">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f5cd7-501">SDK version</span></span> | <span data-ttu-id="f5cd7-502">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f5cd7-502">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f5cd7-503">3.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-503">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f5cd7-504">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-504">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="f5cd7-505">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-505">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="f5cd7-506">Comprend BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-506">Includes BrowserLink in the project.</span></span> <span data-ttu-id="f5cd7-507">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2 et 3,1.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-507">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="f5cd7-508">Détermine si le projet est configuré pour utiliser la [compilation du runtime Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) dans les versions Debug.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-508">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="f5cd7-509">Option disponible depuis le kit de développement logiciel (SDK) 3.1.201 .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-509">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="f5cd7-510">angulaire, réaction</span><span class="sxs-lookup"><span data-stu-id="f5cd7-510">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f5cd7-511">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-511">The type of authentication to use.</span></span> <span data-ttu-id="f5cd7-512">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-512">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="f5cd7-513">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-513">The possible values are:</span></span>

  - <span data-ttu-id="f5cd7-514">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-514">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f5cd7-515">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-515">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f5cd7-516">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-516">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f5cd7-517">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-517">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f5cd7-518">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-518">Turns off HTTPS.</span></span> <span data-ttu-id="f5cd7-519">Cette option s’applique uniquement si l’authentification est `None` .</span><span class="sxs-lookup"><span data-stu-id="f5cd7-519">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f5cd7-520">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-520">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f5cd7-521">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-521">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f5cd7-522">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-522">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5cd7-523">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-523">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f5cd7-524">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-524">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f5cd7-525">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-525">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f5cd7-526">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f5cd7-526">SDK version</span></span> | <span data-ttu-id="f5cd7-527">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f5cd7-527">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f5cd7-528">3.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-528">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f5cd7-529">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-529">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f5cd7-530">2.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-530">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="f5cd7-531">reactredux</span><span class="sxs-lookup"><span data-stu-id="f5cd7-531">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f5cd7-532">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5cd7-533">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f5cd7-534">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f5cd7-535">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f5cd7-536">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f5cd7-536">SDK version</span></span> | <span data-ttu-id="f5cd7-537">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f5cd7-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f5cd7-538">3.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-538">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f5cd7-539">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-539">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f5cd7-540">2.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-540">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="f5cd7-541">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f5cd7-542">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-542">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="f5cd7-543">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="f5cd7-543">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="f5cd7-544">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-544">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="f5cd7-545">Prend en charge l’ajout de pages et de vues Razor traditionnelles en plus des composants de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-545">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="f5cd7-546">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-546">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="f5cd7-547">webapi</span><span class="sxs-lookup"><span data-stu-id="f5cd7-547">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f5cd7-548">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-548">The type of authentication to use.</span></span> <span data-ttu-id="f5cd7-549">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-549">The possible values are:</span></span>

  - <span data-ttu-id="f5cd7-550">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="f5cd7-550">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f5cd7-551">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f5cd7-552">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f5cd7-553">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-553">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f5cd7-554">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-554">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f5cd7-555">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-555">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f5cd7-556">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-556">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f5cd7-557">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-557">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f5cd7-558">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-558">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f5cd7-559">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-559">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f5cd7-560">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-560">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f5cd7-561">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-561">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f5cd7-562">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-562">The Client ID for this project.</span></span> <span data-ttu-id="f5cd7-563">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f5cd7-564">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-564">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f5cd7-565">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-565">The domain for the directory tenant.</span></span> <span data-ttu-id="f5cd7-566">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-566">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f5cd7-567">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-567">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f5cd7-568">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-568">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f5cd7-569">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-569">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f5cd7-570">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-570">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f5cd7-571">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-571">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f5cd7-572">S’applique uniquement à `SingleOrg` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-572">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f5cd7-573">Exclut *launchSettings.js* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-573">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f5cd7-574">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-574">Turns off HTTPS.</span></span> <span data-ttu-id="f5cd7-575">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-575">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="f5cd7-576">Cette option s’applique uniquement si `IndividualB2C` ou `SingleOrg` ne sont pas utilisés pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-576">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f5cd7-577">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-577">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f5cd7-578">S’applique uniquement à `IndividualB2C` l’authentification.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-578">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5cd7-579">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-579">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f5cd7-580">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-580">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f5cd7-581">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-581">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f5cd7-582">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f5cd7-582">SDK version</span></span> | <span data-ttu-id="f5cd7-583">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f5cd7-583">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f5cd7-584">3.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-584">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f5cd7-585">3.0</span><span class="sxs-lookup"><span data-stu-id="f5cd7-585">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f5cd7-586">2.1</span><span class="sxs-lookup"><span data-stu-id="f5cd7-586">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="f5cd7-587">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-587">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="f5cd7-588">globaljson</span><span class="sxs-lookup"><span data-stu-id="f5cd7-588">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="f5cd7-589">Spécifie la version de la kit SDK .NET Core à utiliser dans le fichier *global.js* .</span><span class="sxs-lookup"><span data-stu-id="f5cd7-589">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="f5cd7-590">Exemples</span><span class="sxs-lookup"><span data-stu-id="f5cd7-590">Examples</span></span>

- <span data-ttu-id="f5cd7-591">Créez un projet d’application console C# en spécifiant le nom du modèle :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-591">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="f5cd7-592">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-592">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="f5cd7-593">Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-593">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="f5cd7-594">Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-594">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="f5cd7-595">Créez un projet xUnit :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-595">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="f5cd7-596">Répertorier tous les modèles disponibles pour les modèles d’application à page unique (SPA) :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-596">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="f5cd7-597">Liste de tous les modèles correspondant à la sous-chaîne *we*.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-597">List all templates matching the *we* substring.</span></span> <span data-ttu-id="f5cd7-598">Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-598">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="f5cd7-599">Tentative d’appel du modèle correspondant à *ng*.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-599">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="f5cd7-600">Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.</span><span class="sxs-lookup"><span data-stu-id="f5cd7-600">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="f5cd7-601">Installez la version 2,0 des modèles SPA pour ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-601">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="f5cd7-602">Répertoriez les modèles installés et les détails les concernant, notamment comment les désinstaller :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-602">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="f5cd7-603">Créez un *global.js* dans le répertoire actif en définissant la version du kit de développement logiciel (SDK) sur 3.1.101 :</span><span class="sxs-lookup"><span data-stu-id="f5cd7-603">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="f5cd7-604">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5cd7-604">See also</span></span>

- [<span data-ttu-id="f5cd7-605">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="f5cd7-605">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="f5cd7-606">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="f5cd7-606">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="f5cd7-607">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="f5cd7-607">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="f5cd7-608">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="f5cd7-608">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
