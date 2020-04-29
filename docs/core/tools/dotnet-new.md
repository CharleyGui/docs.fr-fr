---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
ms.date: 04/10/2020
ms.openlocfilehash: 9a68baafa7ac3e6ad2fdc8f1c6e8621d6e15f1ff
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506855"
---
# <a name="dotnet-new"></a><span data-ttu-id="bdfd1-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="bdfd1-103">dotnet new</span></span>

<span data-ttu-id="bdfd1-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bdfd1-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bdfd1-105">Nom</span><span class="sxs-lookup"><span data-stu-id="bdfd1-105">Name</span></span>

<span data-ttu-id="bdfd1-106">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bdfd1-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="bdfd1-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="bdfd1-108">Description</span><span class="sxs-lookup"><span data-stu-id="bdfd1-108">Description</span></span>

<span data-ttu-id="bdfd1-109">La `dotnet new` commande crée un projet .net Core ou d’autres artefacts basés sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="bdfd1-110">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="bdfd1-111">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="bdfd1-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="bdfd1-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="bdfd1-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="bdfd1-113">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="bdfd1-114">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="bdfd1-115">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="bdfd1-116">Vous pouvez exécuter `dotnet new --list` ou `dotnet new -l` pour afficher la liste de tous les modèles installés.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="bdfd1-117">Si la `TEMPLATE` valeur ne correspond pas exactement au texte de la colonne **Templates** ou **Short Name** de la table retournée, une correspondance de sous-chaînes est effectuée sur ces deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="bdfd1-118">À compter du kit de développement logiciel (SDK) .NET Core 3,0, l’interface CLI recherche `dotnet new` des modèles dans NuGet.org quand vous appelez la commande dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="bdfd1-119">Si l’interface CLI ne peut pas trouver de correspondance de `dotnet new`modèle lors de l’appel de, pas encore partiel.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="bdfd1-120">Si une version plus récente du modèle est disponible.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="bdfd1-121">Dans ce cas, le projet ou l’artefact est créé, mais l’interface CLI vous avertit d’une version mise à jour du modèle.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="bdfd1-122">Le tableau suivant répertorie les modèles qui sont préinstallés avec le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="bdfd1-123">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="bdfd1-124">Cliquez sur le lien nom abrégé pour afficher les options de modèle spécifiques.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="bdfd1-125">Modèles</span><span class="sxs-lookup"><span data-stu-id="bdfd1-125">Templates</span></span>                                    | <span data-ttu-id="bdfd1-126">Nom court</span><span class="sxs-lookup"><span data-stu-id="bdfd1-126">Short name</span></span>                      | <span data-ttu-id="bdfd1-127">Langage</span><span class="sxs-lookup"><span data-stu-id="bdfd1-127">Language</span></span>     | <span data-ttu-id="bdfd1-128">Balises</span><span class="sxs-lookup"><span data-stu-id="bdfd1-128">Tags</span></span>                                  | <span data-ttu-id="bdfd1-129">Présent</span><span class="sxs-lookup"><span data-stu-id="bdfd1-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="bdfd1-130">Application console</span><span class="sxs-lookup"><span data-stu-id="bdfd1-130">Console Application</span></span>                          | [<span data-ttu-id="bdfd1-131">Console</span><span class="sxs-lookup"><span data-stu-id="bdfd1-131">console</span></span>](#console)             | <span data-ttu-id="bdfd1-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="bdfd1-132">[C#], F#, VB</span></span> | <span data-ttu-id="bdfd1-133">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="bdfd1-133">Common/Console</span></span>                        | <span data-ttu-id="bdfd1-134">1.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-134">1.0</span></span>        |
| <span data-ttu-id="bdfd1-135">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="bdfd1-135">Class library</span></span>                                | [<span data-ttu-id="bdfd1-136">classlib</span><span class="sxs-lookup"><span data-stu-id="bdfd1-136">classlib</span></span>](#classlib)           | <span data-ttu-id="bdfd1-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="bdfd1-137">[C#], F#, VB</span></span> | <span data-ttu-id="bdfd1-138">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="bdfd1-138">Common/Library</span></span>                        | <span data-ttu-id="bdfd1-139">1.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-139">1.0</span></span>        |
| <span data-ttu-id="bdfd1-140">Application WPF</span><span class="sxs-lookup"><span data-stu-id="bdfd1-140">WPF Application</span></span>                              | [<span data-ttu-id="bdfd1-141">WPF</span><span class="sxs-lookup"><span data-stu-id="bdfd1-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="bdfd1-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-142">[C#]</span></span>         | <span data-ttu-id="bdfd1-143">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="bdfd1-143">Common/WPF</span></span>                            | <span data-ttu-id="bdfd1-144">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-144">3.0</span></span>        |
| <span data-ttu-id="bdfd1-145">Bibliothèque de classes WPF</span><span class="sxs-lookup"><span data-stu-id="bdfd1-145">WPF Class library</span></span>                            | [<span data-ttu-id="bdfd1-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="bdfd1-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="bdfd1-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-147">[C#]</span></span>         | <span data-ttu-id="bdfd1-148">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="bdfd1-148">Common/WPF</span></span>                            | <span data-ttu-id="bdfd1-149">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-149">3.0</span></span>        |
| <span data-ttu-id="bdfd1-150">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="bdfd1-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="bdfd1-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="bdfd1-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="bdfd1-152">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-152">[C#]</span></span>         | <span data-ttu-id="bdfd1-153">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="bdfd1-153">Common/WPF</span></span>                            | <span data-ttu-id="bdfd1-154">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-154">3.0</span></span>        |
| <span data-ttu-id="bdfd1-155">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="bdfd1-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="bdfd1-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="bdfd1-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="bdfd1-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-157">[C#]</span></span>         | <span data-ttu-id="bdfd1-158">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="bdfd1-158">Common/WPF</span></span>                            | <span data-ttu-id="bdfd1-159">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-159">3.0</span></span>        |
| <span data-ttu-id="bdfd1-160">Application Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="bdfd1-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="bdfd1-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="bdfd1-161">winforms</span></span>](#winforms)           | <span data-ttu-id="bdfd1-162">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-162">[C#]</span></span>         | <span data-ttu-id="bdfd1-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="bdfd1-163">Common/WinForms</span></span>                       | <span data-ttu-id="bdfd1-164">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-164">3.0</span></span>        |
| <span data-ttu-id="bdfd1-165">Bibliothèque de classes Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="bdfd1-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="bdfd1-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="bdfd1-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="bdfd1-167">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-167">[C#]</span></span>         | <span data-ttu-id="bdfd1-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="bdfd1-168">Common/WinForms</span></span>                       | <span data-ttu-id="bdfd1-169">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-169">3.0</span></span>        |
| <span data-ttu-id="bdfd1-170">Service Worker</span><span class="sxs-lookup"><span data-stu-id="bdfd1-170">Worker Service</span></span>                               | [<span data-ttu-id="bdfd1-171">collabor</span><span class="sxs-lookup"><span data-stu-id="bdfd1-171">worker</span></span>](#web-others)           | <span data-ttu-id="bdfd1-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-172">[C#]</span></span>         | <span data-ttu-id="bdfd1-173">Commun/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="bdfd1-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="bdfd1-174">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-174">3.0</span></span>        |
| <span data-ttu-id="bdfd1-175">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="bdfd1-175">Unit Test Project</span></span>                            | [<span data-ttu-id="bdfd1-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="bdfd1-176">mstest</span></span>](#test)                 | <span data-ttu-id="bdfd1-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="bdfd1-177">[C#], F#, VB</span></span> | <span data-ttu-id="bdfd1-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="bdfd1-178">Test/MSTest</span></span>                           | <span data-ttu-id="bdfd1-179">1.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-179">1.0</span></span>        |
| <span data-ttu-id="bdfd1-180">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="bdfd1-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="bdfd1-181">nunit</span><span class="sxs-lookup"><span data-stu-id="bdfd1-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="bdfd1-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="bdfd1-182">[C#], F#, VB</span></span> | <span data-ttu-id="bdfd1-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="bdfd1-183">Test/NUnit</span></span>                            | <span data-ttu-id="bdfd1-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="bdfd1-184">2.1.400</span></span>    |
| <span data-ttu-id="bdfd1-185">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="bdfd1-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="bdfd1-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="bdfd1-186">[C#], F#, VB</span></span> | <span data-ttu-id="bdfd1-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="bdfd1-187">Test/NUnit</span></span>                            | <span data-ttu-id="bdfd1-188">2.2</span><span class="sxs-lookup"><span data-stu-id="bdfd1-188">2.2</span></span>        |
| <span data-ttu-id="bdfd1-189">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="bdfd1-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="bdfd1-190">xunit</span><span class="sxs-lookup"><span data-stu-id="bdfd1-190">xunit</span></span>](#test)                  | <span data-ttu-id="bdfd1-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="bdfd1-191">[C#], F#, VB</span></span> | <span data-ttu-id="bdfd1-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="bdfd1-192">Test/xUnit</span></span>                            | <span data-ttu-id="bdfd1-193">1.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-193">1.0</span></span>        |
| <span data-ttu-id="bdfd1-194">Composant Razor</span><span class="sxs-lookup"><span data-stu-id="bdfd1-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="bdfd1-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-195">[C#]</span></span>         | <span data-ttu-id="bdfd1-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bdfd1-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="bdfd1-197">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-197">3.0</span></span>        |
| <span data-ttu-id="bdfd1-198">Page Razor</span><span class="sxs-lookup"><span data-stu-id="bdfd1-198">Razor Page</span></span>                                   | [<span data-ttu-id="bdfd1-199">pagination</span><span class="sxs-lookup"><span data-stu-id="bdfd1-199">page</span></span>](#page)                   | <span data-ttu-id="bdfd1-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-200">[C#]</span></span>         | <span data-ttu-id="bdfd1-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bdfd1-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="bdfd1-202">2.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-202">2.0</span></span>        |
| <span data-ttu-id="bdfd1-203">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="bdfd1-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="bdfd1-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="bdfd1-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="bdfd1-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-205">[C#]</span></span>         | <span data-ttu-id="bdfd1-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bdfd1-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="bdfd1-207">2.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-207">2.0</span></span>        |
| <span data-ttu-id="bdfd1-208">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="bdfd1-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="bdfd1-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-209">[C#]</span></span>         | <span data-ttu-id="bdfd1-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bdfd1-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="bdfd1-211">2.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-211">2.0</span></span>        |
| <span data-ttu-id="bdfd1-212">Application de serveur éblouissante</span><span class="sxs-lookup"><span data-stu-id="bdfd1-212">Blazor Server App</span></span>                            | [<span data-ttu-id="bdfd1-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="bdfd1-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="bdfd1-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-214">[C#]</span></span>         | <span data-ttu-id="bdfd1-215">Web/éblouissant</span><span class="sxs-lookup"><span data-stu-id="bdfd1-215">Web/Blazor</span></span>                            | <span data-ttu-id="bdfd1-216">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-216">3.0</span></span>        |
| <span data-ttu-id="bdfd1-217">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="bdfd1-217">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="bdfd1-218">Internet</span><span class="sxs-lookup"><span data-stu-id="bdfd1-218">web</span></span>](#web)                     | <span data-ttu-id="bdfd1-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="bdfd1-219">[C#], F#</span></span>     | <span data-ttu-id="bdfd1-220">Web/vides</span><span class="sxs-lookup"><span data-stu-id="bdfd1-220">Web/Empty</span></span>                             | <span data-ttu-id="bdfd1-221">1.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-221">1.0</span></span>        |
| <span data-ttu-id="bdfd1-222">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="bdfd1-222">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="bdfd1-223">MVC</span><span class="sxs-lookup"><span data-stu-id="bdfd1-223">mvc</span></span>](#web-options)             | <span data-ttu-id="bdfd1-224">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="bdfd1-224">[C#], F#</span></span>     | <span data-ttu-id="bdfd1-225">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="bdfd1-225">Web/MVC</span></span>                               | <span data-ttu-id="bdfd1-226">1.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-226">1.0</span></span>        |
| <span data-ttu-id="bdfd1-227">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bdfd1-227">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="bdfd1-228">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="bdfd1-228">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="bdfd1-229">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-229">[C#]</span></span>         | <span data-ttu-id="bdfd1-230">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="bdfd1-230">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="bdfd1-231">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-231">2.2, 2.0</span></span>   |
| <span data-ttu-id="bdfd1-232">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="bdfd1-232">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="bdfd1-233">oblique</span><span class="sxs-lookup"><span data-stu-id="bdfd1-233">angular</span></span>](#spa)                 | <span data-ttu-id="bdfd1-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-234">[C#]</span></span>         | <span data-ttu-id="bdfd1-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="bdfd1-235">Web/MVC/SPA</span></span>                           | <span data-ttu-id="bdfd1-236">2.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-236">2.0</span></span>        |
| <span data-ttu-id="bdfd1-237">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="bdfd1-237">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="bdfd1-238">réagir</span><span class="sxs-lookup"><span data-stu-id="bdfd1-238">react</span></span>](#spa)                   | <span data-ttu-id="bdfd1-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-239">[C#]</span></span>         | <span data-ttu-id="bdfd1-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="bdfd1-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="bdfd1-241">2.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-241">2.0</span></span>        |
| <span data-ttu-id="bdfd1-242">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="bdfd1-242">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="bdfd1-243">reactredux</span><span class="sxs-lookup"><span data-stu-id="bdfd1-243">reactredux</span></span>](#reactredux)       | <span data-ttu-id="bdfd1-244">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-244">[C#]</span></span>         | <span data-ttu-id="bdfd1-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="bdfd1-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="bdfd1-246">2.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-246">2.0</span></span>        |
| <span data-ttu-id="bdfd1-247">Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="bdfd1-247">Razor Class Library</span></span>                          | [<span data-ttu-id="bdfd1-248">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="bdfd1-248">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="bdfd1-249">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-249">[C#]</span></span>         | <span data-ttu-id="bdfd1-250">Web/Razor/Library/Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="bdfd1-250">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="bdfd1-251">2.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-251">2.1</span></span>        |
| <span data-ttu-id="bdfd1-252">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bdfd1-252">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="bdfd1-253">WebAPI</span><span class="sxs-lookup"><span data-stu-id="bdfd1-253">webapi</span></span>](#webapi)               | <span data-ttu-id="bdfd1-254">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="bdfd1-254">[C#], F#</span></span>     | <span data-ttu-id="bdfd1-255">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="bdfd1-255">Web/WebAPI</span></span>                            | <span data-ttu-id="bdfd1-256">1.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-256">1.0</span></span>        |
| <span data-ttu-id="bdfd1-257">ASP.NET Core Service gRPC</span><span class="sxs-lookup"><span data-stu-id="bdfd1-257">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="bdfd1-258">GRPC</span><span class="sxs-lookup"><span data-stu-id="bdfd1-258">grpc</span></span>](#web-others)             | <span data-ttu-id="bdfd1-259">[C#]</span><span class="sxs-lookup"><span data-stu-id="bdfd1-259">[C#]</span></span>         | <span data-ttu-id="bdfd1-260">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="bdfd1-260">Web/gRPC</span></span>                              | <span data-ttu-id="bdfd1-261">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-261">3.0</span></span>        |
| <span data-ttu-id="bdfd1-262">fichier gitignore dotnet</span><span class="sxs-lookup"><span data-stu-id="bdfd1-262">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="bdfd1-263">Config</span><span class="sxs-lookup"><span data-stu-id="bdfd1-263">Config</span></span>                                | <span data-ttu-id="bdfd1-264">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-264">3.0</span></span>        |
| <span data-ttu-id="bdfd1-265">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="bdfd1-265">global.json file</span></span>                             | [<span data-ttu-id="bdfd1-266">globaljson</span><span class="sxs-lookup"><span data-stu-id="bdfd1-266">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="bdfd1-267">Config</span><span class="sxs-lookup"><span data-stu-id="bdfd1-267">Config</span></span>                                | <span data-ttu-id="bdfd1-268">2.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-268">2.0</span></span>        |
| <span data-ttu-id="bdfd1-269">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="bdfd1-269">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="bdfd1-270">Config</span><span class="sxs-lookup"><span data-stu-id="bdfd1-270">Config</span></span>                                | <span data-ttu-id="bdfd1-271">1.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-271">1.0</span></span>        |
| <span data-ttu-id="bdfd1-272">Fichier manifeste de l’outil local dotnet</span><span class="sxs-lookup"><span data-stu-id="bdfd1-272">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="bdfd1-273">Config</span><span class="sxs-lookup"><span data-stu-id="bdfd1-273">Config</span></span>                                | <span data-ttu-id="bdfd1-274">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-274">3.0</span></span>        |
| <span data-ttu-id="bdfd1-275">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="bdfd1-275">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="bdfd1-276">Config</span><span class="sxs-lookup"><span data-stu-id="bdfd1-276">Config</span></span>                                | <span data-ttu-id="bdfd1-277">1.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-277">1.0</span></span>        |
| <span data-ttu-id="bdfd1-278">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="bdfd1-278">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="bdfd1-279">Solution</span><span class="sxs-lookup"><span data-stu-id="bdfd1-279">Solution</span></span>                              | <span data-ttu-id="bdfd1-280">1.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-280">1.0</span></span>        |
| <span data-ttu-id="bdfd1-281">Fichier de mémoire tampon de protocole</span><span class="sxs-lookup"><span data-stu-id="bdfd1-281">Protocol Buffer File</span></span>                         | [<span data-ttu-id="bdfd1-282">proto</span><span class="sxs-lookup"><span data-stu-id="bdfd1-282">proto</span></span>](#namespace)             |              | <span data-ttu-id="bdfd1-283">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="bdfd1-283">Web/gRPC</span></span>                              | <span data-ttu-id="bdfd1-284">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-284">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="bdfd1-285">Options</span><span class="sxs-lookup"><span data-stu-id="bdfd1-285">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="bdfd1-286">Affiche un récapitulatif de ce qui se passerait si la commande donnée était exécutée (si cela donnerait lieu à la création d’un modèle).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-286">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="bdfd1-287">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-287">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="bdfd1-288">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-288">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="bdfd1-289">Cela est obligatoire lorsque le modèle choisi remplace les fichiers existants dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-289">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="bdfd1-290">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-290">Prints out help for the command.</span></span> <span data-ttu-id="bdfd1-291">Elle peut être appelée pour la `dotnet new` commande elle-même ou pour n’importe quel modèle.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-291">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="bdfd1-292">Par exemple : `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-292">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="bdfd1-293">Installe un pack de modèles à `PATH` partir `NUGET_ID` du ou fourni.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-293">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="bdfd1-294">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-294">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="bdfd1-295">Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-295">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="bdfd1-296">Consultez un exemple dans la section [exemples](#examples) .</span><span class="sxs-lookup"><span data-stu-id="bdfd1-296">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="bdfd1-297">Si une version du modèle a déjà été installée lorsque vous exécutez cette commande, le modèle sera mis à jour vers la version spécifiée, ou vers la version stable la plus récente si aucune version n’a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-297">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="bdfd1-298">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-298">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="bdfd1-299">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-299">Lists templates containing the specified name.</span></span> <span data-ttu-id="bdfd1-300">Si aucun nom n’est spécifié, répertorie tous les modèles.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-300">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="bdfd1-301">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-301">The language of the template to create.</span></span> <span data-ttu-id="bdfd1-302">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-302">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="bdfd1-303">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-303">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="bdfd1-304">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-304">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="bdfd1-305">Dans ce cas, mettez la valeur du paramètre de langue entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-305">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="bdfd1-306">Par exemple : `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-306">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="bdfd1-307">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-307">The name for the created output.</span></span> <span data-ttu-id="bdfd1-308">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-308">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="bdfd1-309">Spécifie une source NuGet à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-309">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="bdfd1-310">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-310">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="bdfd1-311">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-311">Location to place the generated output.</span></span> <span data-ttu-id="bdfd1-312">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-312">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="bdfd1-313">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-313">Filters templates based on available types.</span></span> <span data-ttu-id="bdfd1-314">Les valeurs prédéfinies `project`sont `item`, et `other`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-314">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="bdfd1-315">Désinstalle un pack de modèles au niveau de `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-315">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="bdfd1-316">Lorsque la `<PATH|NUGET_ID>` valeur n’est pas spécifiée, tous les packs de modèles actuellement installés et leurs modèles associés sont affichés.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-316">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="bdfd1-317">Lorsque vous `NUGET_ID`spécifiez, n’incluez pas le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-317">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="bdfd1-318">Si vous ne spécifiez pas de paramètre pour cette option, la commande répertorie les modèles installés et fournit des détails à leur sujet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-318">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="bdfd1-319">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-319">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="bdfd1-320">Par exemple, *C:/Users\</User>/documents/templates/garciasoftware.consoletemplate.CSharp* fonctionnera, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne le sera pas.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-320">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="bdfd1-321">N’incluez pas de barre oblique finale de répertoire finale dans le chemin d’accès de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-321">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="bdfd1-322">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés et les installe.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-322">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="bdfd1-323">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-323">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="bdfd1-324">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-324">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="bdfd1-325">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-325">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="bdfd1-326">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="bdfd1-326">Template options</span></span>

<span data-ttu-id="bdfd1-327">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-327">Each project template may have additional options available.</span></span> <span data-ttu-id="bdfd1-328">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-328">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="bdfd1-329">console</span><span class="sxs-lookup"><span data-stu-id="bdfd1-329">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bdfd1-330">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-330">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bdfd1-331">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-331">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="bdfd1-332">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-332">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bdfd1-333">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="bdfd1-333">SDK version</span></span> | <span data-ttu-id="bdfd1-334">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="bdfd1-334">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bdfd1-335">3.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-335">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bdfd1-336">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-336">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="bdfd1-337">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-337">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="bdfd1-338">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-338">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="bdfd1-339">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-339">Not supported for F#.</span></span> <span data-ttu-id="bdfd1-340">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-340">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bdfd1-341">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-341">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bdfd1-342">S’il est spécifié, n’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-342">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="bdfd1-343">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-343">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="bdfd1-344">classlib</span><span class="sxs-lookup"><span data-stu-id="bdfd1-344">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bdfd1-345">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-345">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bdfd1-346">Valeurs : `netcoreapp<version>` pour créer une bibliothèque de classes .NET Core ou `netstandard<version>` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-346">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="bdfd1-347">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-347">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="bdfd1-348">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-348">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="bdfd1-349">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-349">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="bdfd1-350">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-350">Not supported for F#.</span></span> <span data-ttu-id="bdfd1-351">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-351">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bdfd1-352">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-352">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bdfd1-353">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-353">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="bdfd1-354">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="bdfd1-354">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bdfd1-355">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-355">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bdfd1-356">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-356">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="bdfd1-357">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-357">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="bdfd1-358">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-358">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="bdfd1-359">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-359">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="bdfd1-360">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-360">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bdfd1-361">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-361">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="bdfd1-362">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="bdfd1-362">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="bdfd1-363">Définit la `LangVersion` propriété dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-363">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="bdfd1-364">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-364">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="bdfd1-365">Pour obtenir la liste des versions C# par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-365">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bdfd1-366">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-366">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="bdfd1-367">Worker, GRPC</span><span class="sxs-lookup"><span data-stu-id="bdfd1-367">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bdfd1-368">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-368">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bdfd1-369">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-369">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="bdfd1-370">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-370">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bdfd1-371">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-371">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="bdfd1-372">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-372">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="bdfd1-373">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="bdfd1-373">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bdfd1-374">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-374">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bdfd1-375">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-375">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="bdfd1-376">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-376">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bdfd1-377">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="bdfd1-377">SDK version</span></span> | <span data-ttu-id="bdfd1-378">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="bdfd1-378">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bdfd1-379">3.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-379">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bdfd1-380">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-380">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="bdfd1-381">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-381">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bdfd1-382">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-382">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="bdfd1-383">nunit</span><span class="sxs-lookup"><span data-stu-id="bdfd1-383">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bdfd1-384">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-384">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="bdfd1-385">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-385">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bdfd1-386">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="bdfd1-386">SDK version</span></span> | <span data-ttu-id="bdfd1-387">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="bdfd1-387">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bdfd1-388">3.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-388">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bdfd1-389">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-389">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="bdfd1-390">2.2</span><span class="sxs-lookup"><span data-stu-id="bdfd1-390">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="bdfd1-391">2.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-391">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="bdfd1-392">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-392">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bdfd1-393">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-393">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="bdfd1-394">page</span><span class="sxs-lookup"><span data-stu-id="bdfd1-394">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="bdfd1-395">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-395">Namespace for the generated code.</span></span> <span data-ttu-id="bdfd1-396">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-396">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="bdfd1-397">Crée la page sans PageModel.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-397">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="bdfd1-398">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="bdfd1-398">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="bdfd1-399">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-399">Namespace for the generated code.</span></span> <span data-ttu-id="bdfd1-400">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-400">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="bdfd1-401">blazorserver</span><span class="sxs-lookup"><span data-stu-id="bdfd1-401">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="bdfd1-402">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-402">The type of authentication to use.</span></span> <span data-ttu-id="bdfd1-403">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-403">The possible values are:</span></span>

  - <span data-ttu-id="bdfd1-404">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-404">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="bdfd1-405">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-405">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="bdfd1-406">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-406">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="bdfd1-407">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-407">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="bdfd1-408">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-408">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="bdfd1-409">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-409">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="bdfd1-410">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-410">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="bdfd1-411">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="bdfd1-412">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="bdfd1-413">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-413">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="bdfd1-414">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-414">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="bdfd1-415">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-415">The reset password policy ID for this project.</span></span> <span data-ttu-id="bdfd1-416">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-416">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="bdfd1-417">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-417">The edit profile policy ID for this project.</span></span> <span data-ttu-id="bdfd1-418">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-418">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="bdfd1-419">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-419">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="bdfd1-420">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-420">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="bdfd1-421">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-421">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="bdfd1-422">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-422">The Client ID for this project.</span></span> <span data-ttu-id="bdfd1-423">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-423">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="bdfd1-424">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-424">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="bdfd1-425">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-425">The domain for the directory tenant.</span></span> <span data-ttu-id="bdfd1-426">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-426">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="bdfd1-427">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-427">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="bdfd1-428">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-428">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="bdfd1-429">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-429">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="bdfd1-430">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-430">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="bdfd1-431">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-431">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="bdfd1-432">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-432">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="bdfd1-433">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-433">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="bdfd1-434">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-434">Allows this application read-access to the directory.</span></span> <span data-ttu-id="bdfd1-435">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-435">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bdfd1-436">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-436">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="bdfd1-437">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-437">Turns off HTTPS.</span></span> <span data-ttu-id="bdfd1-438">Cette option s’applique uniquement `Individual`si `IndividualB2C`, `SingleOrg`, ou `MultiOrg` ne sont pas utilisés `--auth`pour.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-438">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="bdfd1-439">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-439">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="bdfd1-440">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-440">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="bdfd1-441">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-441">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="bdfd1-442">web</span><span class="sxs-lookup"><span data-stu-id="bdfd1-442">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bdfd1-443">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-443">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bdfd1-444">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-444">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bdfd1-445">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-445">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bdfd1-446">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-446">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bdfd1-447">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="bdfd1-447">SDK version</span></span> | <span data-ttu-id="bdfd1-448">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="bdfd1-448">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bdfd1-449">3.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-449">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bdfd1-450">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-450">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="bdfd1-451">2.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-451">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="bdfd1-452">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-452">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="bdfd1-453">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-453">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="bdfd1-454">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="bdfd1-454">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="bdfd1-455">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-455">The type of authentication to use.</span></span> <span data-ttu-id="bdfd1-456">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-456">The possible values are:</span></span>

  - <span data-ttu-id="bdfd1-457">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-457">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="bdfd1-458">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-458">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="bdfd1-459">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-459">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="bdfd1-460">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-460">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="bdfd1-461">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-461">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="bdfd1-462">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-462">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="bdfd1-463">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-463">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="bdfd1-464">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-464">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="bdfd1-465">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-465">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="bdfd1-466">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-466">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="bdfd1-467">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-467">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="bdfd1-468">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-468">The reset password policy ID for this project.</span></span> <span data-ttu-id="bdfd1-469">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-469">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="bdfd1-470">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-470">The edit profile policy ID for this project.</span></span> <span data-ttu-id="bdfd1-471">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-471">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="bdfd1-472">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-472">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="bdfd1-473">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-473">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="bdfd1-474">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-474">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="bdfd1-475">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-475">The Client ID for this project.</span></span> <span data-ttu-id="bdfd1-476">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-476">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="bdfd1-477">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-477">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="bdfd1-478">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-478">The domain for the directory tenant.</span></span> <span data-ttu-id="bdfd1-479">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="bdfd1-480">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-480">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="bdfd1-481">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-481">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="bdfd1-482">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-482">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="bdfd1-483">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-483">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="bdfd1-484">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-484">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="bdfd1-485">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-485">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="bdfd1-486">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-486">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="bdfd1-487">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-487">Allows this application read-access to the directory.</span></span> <span data-ttu-id="bdfd1-488">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-488">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bdfd1-489">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-489">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="bdfd1-490">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-490">Turns off HTTPS.</span></span> <span data-ttu-id="bdfd1-491">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-491">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="bdfd1-492">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-492">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="bdfd1-493">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-493">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bdfd1-494">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-494">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bdfd1-495">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-495">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="bdfd1-496">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-496">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bdfd1-497">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="bdfd1-497">SDK version</span></span> | <span data-ttu-id="bdfd1-498">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="bdfd1-498">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bdfd1-499">3.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-499">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bdfd1-500">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-500">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="bdfd1-501">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-501">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="bdfd1-502">Comprend BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-502">Includes BrowserLink in the project.</span></span> <span data-ttu-id="bdfd1-503">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2 et 3,1.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-503">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="bdfd1-504">Détermine si le projet est configuré pour utiliser la [compilation du runtime Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) dans les versions Debug.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-504">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="bdfd1-505">Option disponible depuis le kit de développement logiciel (SDK) 3.1.201 .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-505">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="bdfd1-506">angulaire, réaction</span><span class="sxs-lookup"><span data-stu-id="bdfd1-506">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="bdfd1-507">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-507">The type of authentication to use.</span></span> <span data-ttu-id="bdfd1-508">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-508">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="bdfd1-509">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-509">The possible values are:</span></span>

  - <span data-ttu-id="bdfd1-510">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-510">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="bdfd1-511">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-511">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bdfd1-512">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-512">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="bdfd1-513">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-513">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="bdfd1-514">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-514">Turns off HTTPS.</span></span> <span data-ttu-id="bdfd1-515">Cette option s’applique uniquement si l' `None`authentification est.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-515">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="bdfd1-516">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-516">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="bdfd1-517">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-517">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="bdfd1-518">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-518">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bdfd1-519">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-519">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bdfd1-520">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-520">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bdfd1-521">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-521">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bdfd1-522">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="bdfd1-522">SDK version</span></span> | <span data-ttu-id="bdfd1-523">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="bdfd1-523">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bdfd1-524">3.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-524">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bdfd1-525">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-525">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="bdfd1-526">2.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-526">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="bdfd1-527">reactredux</span><span class="sxs-lookup"><span data-stu-id="bdfd1-527">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bdfd1-528">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-528">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bdfd1-529">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-529">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bdfd1-530">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-530">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bdfd1-531">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-531">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bdfd1-532">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="bdfd1-532">SDK version</span></span> | <span data-ttu-id="bdfd1-533">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="bdfd1-533">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bdfd1-534">3.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-534">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bdfd1-535">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-535">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="bdfd1-536">2.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-536">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="bdfd1-537">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-537">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="bdfd1-538">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-538">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="bdfd1-539">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="bdfd1-539">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="bdfd1-540">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-540">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="bdfd1-541">Prend en charge l’ajout de pages et de vues Razor traditionnelles en plus des composants de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-541">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="bdfd1-542">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-542">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="bdfd1-543">webapi</span><span class="sxs-lookup"><span data-stu-id="bdfd1-543">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="bdfd1-544">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-544">The type of authentication to use.</span></span> <span data-ttu-id="bdfd1-545">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-545">The possible values are:</span></span>

  - <span data-ttu-id="bdfd1-546">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="bdfd1-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="bdfd1-547">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-547">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="bdfd1-548">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-548">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="bdfd1-549">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-549">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="bdfd1-550">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-550">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="bdfd1-551">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-551">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="bdfd1-552">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-552">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="bdfd1-553">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-553">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="bdfd1-554">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-554">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="bdfd1-555">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-555">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="bdfd1-556">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-556">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="bdfd1-557">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-557">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="bdfd1-558">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-558">The Client ID for this project.</span></span> <span data-ttu-id="bdfd1-559">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-559">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="bdfd1-560">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-560">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="bdfd1-561">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-561">The domain for the directory tenant.</span></span> <span data-ttu-id="bdfd1-562">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-562">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="bdfd1-563">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-563">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="bdfd1-564">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-564">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="bdfd1-565">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-565">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="bdfd1-566">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-566">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="bdfd1-567">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-567">Allows this application read-access to the directory.</span></span> <span data-ttu-id="bdfd1-568">S’applique uniquement `SingleOrg` à l’authentification.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-568">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bdfd1-569">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-569">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="bdfd1-570">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-570">Turns off HTTPS.</span></span> <span data-ttu-id="bdfd1-571">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-571">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="bdfd1-572">Cette option s’applique uniquement `IndividualB2C` si `SingleOrg` ou ne sont pas utilisés pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-572">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="bdfd1-573">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-573">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="bdfd1-574">S’applique uniquement `IndividualB2C` à l’authentification.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-574">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bdfd1-575">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-575">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bdfd1-576">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-576">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bdfd1-577">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-577">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bdfd1-578">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="bdfd1-578">SDK version</span></span> | <span data-ttu-id="bdfd1-579">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="bdfd1-579">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bdfd1-580">3.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-580">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bdfd1-581">3.0</span><span class="sxs-lookup"><span data-stu-id="bdfd1-581">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="bdfd1-582">2.1</span><span class="sxs-lookup"><span data-stu-id="bdfd1-582">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="bdfd1-583">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-583">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="bdfd1-584">globaljson</span><span class="sxs-lookup"><span data-stu-id="bdfd1-584">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="bdfd1-585">Spécifie la version de la kit SDK .NET Core à utiliser dans le fichier *global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bdfd1-585">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="bdfd1-586">Exemples</span><span class="sxs-lookup"><span data-stu-id="bdfd1-586">Examples</span></span>

- <span data-ttu-id="bdfd1-587">Créez un projet d’application console C# en spécifiant le nom du modèle :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-587">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="bdfd1-588">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-588">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="bdfd1-589">Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-589">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="bdfd1-590">Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-590">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="bdfd1-591">Créez un projet xUnit :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-591">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="bdfd1-592">Répertorier tous les modèles disponibles pour les modèles d’application à page unique (SPA) :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-592">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="bdfd1-593">Liste de tous les modèles correspondant à la sous-chaîne *we*.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-593">List all templates matching the *we* substring.</span></span> <span data-ttu-id="bdfd1-594">Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-594">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="bdfd1-595">Tentative d’appel du modèle correspondant à *ng*.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-595">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="bdfd1-596">Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.</span><span class="sxs-lookup"><span data-stu-id="bdfd1-596">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="bdfd1-597">Installez la version 2,0 des modèles SPA pour ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-597">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="bdfd1-598">Répertoriez les modèles installés et les détails les concernant, notamment comment les désinstaller :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-598">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="bdfd1-599">Créez un *global. JSON* dans le répertoire actif en définissant la version du kit de développement logiciel (SDK) sur 3.1.101 :</span><span class="sxs-lookup"><span data-stu-id="bdfd1-599">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="bdfd1-600">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdfd1-600">See also</span></span>

- [<span data-ttu-id="bdfd1-601">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="bdfd1-601">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="bdfd1-602">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="bdfd1-602">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="bdfd1-603">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="bdfd1-603">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="bdfd1-604">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="bdfd1-604">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
