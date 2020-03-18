---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399125"
---
# <a name="dotnet-new"></a><span data-ttu-id="f70e1-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="f70e1-103">dotnet new</span></span>

<span data-ttu-id="f70e1-104">**Cet article s’applique à:** ✔️ .NET Core 2.0 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="f70e1-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f70e1-105">Nom</span><span class="sxs-lookup"><span data-stu-id="f70e1-105">Name</span></span>

<span data-ttu-id="f70e1-106">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="f70e1-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f70e1-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="f70e1-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f70e1-108">Description</span><span class="sxs-lookup"><span data-stu-id="f70e1-108">Description</span></span>

<span data-ttu-id="f70e1-109">La `dotnet new` commande crée un projet .NET Core ou d’autres artefacts basés sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="f70e1-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="f70e1-110">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f70e1-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="f70e1-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="f70e1-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="f70e1-112">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="f70e1-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="f70e1-113">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="f70e1-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="f70e1-114">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="f70e1-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="f70e1-115">Vous pouvez `dotnet new --list` courir pour voir une liste de tous les modèles installés.</span><span class="sxs-lookup"><span data-stu-id="f70e1-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="f70e1-116">Si `TEMPLATE` la valeur n’est pas une correspondance exacte sur le texte dans les **Modèles** ou la colonne **Short Name** de la table retournée, un match de sous-corde est effectué sur ces deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="f70e1-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="f70e1-117">En commençant par .NET Core 3.0 SDK, le CLI recherche des `dotnet new` modèles dans NuGet.org lorsque vous invoquez la commande dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="f70e1-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="f70e1-118">Si le CLI ne peut pas trouver `dotnet new`un modèle de correspondance lors de l’invocation , même pas partielle.</span><span class="sxs-lookup"><span data-stu-id="f70e1-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="f70e1-119">S’il y a une nouvelle version du modèle disponible.</span><span class="sxs-lookup"><span data-stu-id="f70e1-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="f70e1-120">Dans ce cas, le projet ou l’artefact est créé, mais le CLI vous avertit d’une version mise à jour du modèle.</span><span class="sxs-lookup"><span data-stu-id="f70e1-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="f70e1-121">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="f70e1-121">The command contains a default list of templates.</span></span> <span data-ttu-id="f70e1-122">Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="f70e1-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="f70e1-123">Le tableau suivant montre les modèles qui viennent pré-installé avec le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f70e1-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="f70e1-124">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="f70e1-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="f70e1-125">Cliquez sur le lien de nom court pour voir les options spécifiques de modèle.</span><span class="sxs-lookup"><span data-stu-id="f70e1-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="f70e1-126">Modèles</span><span class="sxs-lookup"><span data-stu-id="f70e1-126">Templates</span></span>                                    | <span data-ttu-id="f70e1-127">Nom court</span><span class="sxs-lookup"><span data-stu-id="f70e1-127">Short name</span></span>                      | <span data-ttu-id="f70e1-128">Langage</span><span class="sxs-lookup"><span data-stu-id="f70e1-128">Language</span></span>     | <span data-ttu-id="f70e1-129">Balises</span><span class="sxs-lookup"><span data-stu-id="f70e1-129">Tags</span></span>                                  | <span data-ttu-id="f70e1-130">Introduit</span><span class="sxs-lookup"><span data-stu-id="f70e1-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="f70e1-131">Application console</span><span class="sxs-lookup"><span data-stu-id="f70e1-131">Console Application</span></span>                          | [<span data-ttu-id="f70e1-132">Console</span><span class="sxs-lookup"><span data-stu-id="f70e1-132">console</span></span>](#console)             | <span data-ttu-id="f70e1-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f70e1-133">[C#], F#, VB</span></span> | <span data-ttu-id="f70e1-134">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="f70e1-134">Common/Console</span></span>                        | <span data-ttu-id="f70e1-135">1.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-135">1.0</span></span>        |
| <span data-ttu-id="f70e1-136">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="f70e1-136">Class library</span></span>                                | [<span data-ttu-id="f70e1-137">classlib</span><span class="sxs-lookup"><span data-stu-id="f70e1-137">classlib</span></span>](#classlib)           | <span data-ttu-id="f70e1-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f70e1-138">[C#], F#, VB</span></span> | <span data-ttu-id="f70e1-139">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="f70e1-139">Common/Library</span></span>                        | <span data-ttu-id="f70e1-140">1.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-140">1.0</span></span>        |
| <span data-ttu-id="f70e1-141">Application WPF</span><span class="sxs-lookup"><span data-stu-id="f70e1-141">WPF Application</span></span>                              | [<span data-ttu-id="f70e1-142">Wpf</span><span class="sxs-lookup"><span data-stu-id="f70e1-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="f70e1-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-143">[C#]</span></span>         | <span data-ttu-id="f70e1-144">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="f70e1-144">Common/WPF</span></span>                            | <span data-ttu-id="f70e1-145">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-145">3.0</span></span>        |
| <span data-ttu-id="f70e1-146">Bibliothèque de classe WPF</span><span class="sxs-lookup"><span data-stu-id="f70e1-146">WPF Class library</span></span>                            | [<span data-ttu-id="f70e1-147">wpflib (wpflib)</span><span class="sxs-lookup"><span data-stu-id="f70e1-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="f70e1-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-148">[C#]</span></span>         | <span data-ttu-id="f70e1-149">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="f70e1-149">Common/WPF</span></span>                            | <span data-ttu-id="f70e1-150">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-150">3.0</span></span>        |
| <span data-ttu-id="f70e1-151">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="f70e1-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="f70e1-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="f70e1-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="f70e1-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-153">[C#]</span></span>         | <span data-ttu-id="f70e1-154">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="f70e1-154">Common/WPF</span></span>                            | <span data-ttu-id="f70e1-155">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-155">3.0</span></span>        |
| <span data-ttu-id="f70e1-156">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="f70e1-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="f70e1-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="f70e1-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="f70e1-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-158">[C#]</span></span>         | <span data-ttu-id="f70e1-159">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="f70e1-159">Common/WPF</span></span>                            | <span data-ttu-id="f70e1-160">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-160">3.0</span></span>        |
| <span data-ttu-id="f70e1-161">Application des formulaires Windows (WinForms)</span><span class="sxs-lookup"><span data-stu-id="f70e1-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="f70e1-162">Winforms</span><span class="sxs-lookup"><span data-stu-id="f70e1-162">winforms</span></span>](#winforms)           | <span data-ttu-id="f70e1-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-163">[C#]</span></span>         | <span data-ttu-id="f70e1-164">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="f70e1-164">Common/WinForms</span></span>                       | <span data-ttu-id="f70e1-165">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-165">3.0</span></span>        |
| <span data-ttu-id="f70e1-166">Bibliothèque de classe Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="f70e1-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="f70e1-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="f70e1-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="f70e1-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-168">[C#]</span></span>         | <span data-ttu-id="f70e1-169">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="f70e1-169">Common/WinForms</span></span>                       | <span data-ttu-id="f70e1-170">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-170">3.0</span></span>        |
| <span data-ttu-id="f70e1-171">Service aux travailleurs</span><span class="sxs-lookup"><span data-stu-id="f70e1-171">Worker Service</span></span>                               | [<span data-ttu-id="f70e1-172">Travailleur</span><span class="sxs-lookup"><span data-stu-id="f70e1-172">worker</span></span>](#web-others)           | <span data-ttu-id="f70e1-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-173">[C#]</span></span>         | <span data-ttu-id="f70e1-174">Commun/Travailleur/Web</span><span class="sxs-lookup"><span data-stu-id="f70e1-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="f70e1-175">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-175">3.0</span></span>        |
| <span data-ttu-id="f70e1-176">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="f70e1-176">Unit Test Project</span></span>                            | [<span data-ttu-id="f70e1-177">mstest</span><span class="sxs-lookup"><span data-stu-id="f70e1-177">mstest</span></span>](#test)                 | <span data-ttu-id="f70e1-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f70e1-178">[C#], F#, VB</span></span> | <span data-ttu-id="f70e1-179">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="f70e1-179">Test/MSTest</span></span>                           | <span data-ttu-id="f70e1-180">1.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-180">1.0</span></span>        |
| <span data-ttu-id="f70e1-181">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="f70e1-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="f70e1-182">Nunit</span><span class="sxs-lookup"><span data-stu-id="f70e1-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="f70e1-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f70e1-183">[C#], F#, VB</span></span> | <span data-ttu-id="f70e1-184">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="f70e1-184">Test/NUnit</span></span>                            | <span data-ttu-id="f70e1-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="f70e1-185">2.1.400</span></span>    |
| <span data-ttu-id="f70e1-186">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="f70e1-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="f70e1-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f70e1-187">[C#], F#, VB</span></span> | <span data-ttu-id="f70e1-188">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="f70e1-188">Test/NUnit</span></span>                            | <span data-ttu-id="f70e1-189">2.2</span><span class="sxs-lookup"><span data-stu-id="f70e1-189">2.2</span></span>        |
| <span data-ttu-id="f70e1-190">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="f70e1-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="f70e1-191">xunit</span><span class="sxs-lookup"><span data-stu-id="f70e1-191">xunit</span></span>](#test)                  | <span data-ttu-id="f70e1-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f70e1-192">[C#], F#, VB</span></span> | <span data-ttu-id="f70e1-193">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="f70e1-193">Test/xUnit</span></span>                            | <span data-ttu-id="f70e1-194">1.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-194">1.0</span></span>        |
| <span data-ttu-id="f70e1-195">Composant de rasoir</span><span class="sxs-lookup"><span data-stu-id="f70e1-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="f70e1-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-196">[C#]</span></span>         | <span data-ttu-id="f70e1-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f70e1-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="f70e1-198">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-198">3.0</span></span>        |
| <span data-ttu-id="f70e1-199">Page Razor</span><span class="sxs-lookup"><span data-stu-id="f70e1-199">Razor Page</span></span>                                   | [<span data-ttu-id="f70e1-200">Page</span><span class="sxs-lookup"><span data-stu-id="f70e1-200">page</span></span>](#page)                   | <span data-ttu-id="f70e1-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-201">[C#]</span></span>         | <span data-ttu-id="f70e1-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f70e1-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="f70e1-203">2</span><span class="sxs-lookup"><span data-stu-id="f70e1-203">2.0</span></span>        |
| <span data-ttu-id="f70e1-204">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="f70e1-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="f70e1-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="f70e1-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="f70e1-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-206">[C#]</span></span>         | <span data-ttu-id="f70e1-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f70e1-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="f70e1-208">2</span><span class="sxs-lookup"><span data-stu-id="f70e1-208">2.0</span></span>        |
| <span data-ttu-id="f70e1-209">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="f70e1-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="f70e1-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-210">[C#]</span></span>         | <span data-ttu-id="f70e1-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f70e1-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="f70e1-212">2</span><span class="sxs-lookup"><span data-stu-id="f70e1-212">2.0</span></span>        |
| <span data-ttu-id="f70e1-213">Application Serveur Blazor</span><span class="sxs-lookup"><span data-stu-id="f70e1-213">Blazor Server App</span></span>                            | [<span data-ttu-id="f70e1-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="f70e1-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="f70e1-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-215">[C#]</span></span>         | <span data-ttu-id="f70e1-216">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="f70e1-216">Web/Blazor</span></span>                            | <span data-ttu-id="f70e1-217">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-217">3.0</span></span>        |
| <span data-ttu-id="f70e1-218">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="f70e1-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="f70e1-219">Web</span><span class="sxs-lookup"><span data-stu-id="f70e1-219">web</span></span>](#web)                     | <span data-ttu-id="f70e1-220">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f70e1-220">[C#], F#</span></span>     | <span data-ttu-id="f70e1-221">Web/vides</span><span class="sxs-lookup"><span data-stu-id="f70e1-221">Web/Empty</span></span>                             | <span data-ttu-id="f70e1-222">1.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-222">1.0</span></span>        |
| <span data-ttu-id="f70e1-223">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="f70e1-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="f70e1-224">Mvc</span><span class="sxs-lookup"><span data-stu-id="f70e1-224">mvc</span></span>](#web-options)             | <span data-ttu-id="f70e1-225">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f70e1-225">[C#], F#</span></span>     | <span data-ttu-id="f70e1-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="f70e1-226">Web/MVC</span></span>                               | <span data-ttu-id="f70e1-227">1.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-227">1.0</span></span>        |
| <span data-ttu-id="f70e1-228">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f70e1-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="f70e1-229">webapp, rasoir</span><span class="sxs-lookup"><span data-stu-id="f70e1-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="f70e1-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-230">[C#]</span></span>         | <span data-ttu-id="f70e1-231">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="f70e1-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="f70e1-232">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="f70e1-233">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="f70e1-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="f70e1-234">Angulaire</span><span class="sxs-lookup"><span data-stu-id="f70e1-234">angular</span></span>](#spa)                 | <span data-ttu-id="f70e1-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-235">[C#]</span></span>         | <span data-ttu-id="f70e1-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f70e1-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f70e1-237">2</span><span class="sxs-lookup"><span data-stu-id="f70e1-237">2.0</span></span>        |
| <span data-ttu-id="f70e1-238">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="f70e1-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="f70e1-239">Réagir</span><span class="sxs-lookup"><span data-stu-id="f70e1-239">react</span></span>](#spa)                   | <span data-ttu-id="f70e1-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-240">[C#]</span></span>         | <span data-ttu-id="f70e1-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f70e1-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f70e1-242">2</span><span class="sxs-lookup"><span data-stu-id="f70e1-242">2.0</span></span>        |
| <span data-ttu-id="f70e1-243">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="f70e1-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="f70e1-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="f70e1-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="f70e1-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-245">[C#]</span></span>         | <span data-ttu-id="f70e1-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="f70e1-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="f70e1-247">2</span><span class="sxs-lookup"><span data-stu-id="f70e1-247">2.0</span></span>        |
| <span data-ttu-id="f70e1-248">Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="f70e1-248">Razor Class Library</span></span>                          | [<span data-ttu-id="f70e1-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="f70e1-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="f70e1-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-250">[C#]</span></span>         | <span data-ttu-id="f70e1-251">Web/Razor/Library/Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="f70e1-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="f70e1-252">2.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-252">2.1</span></span>        |
| <span data-ttu-id="f70e1-253">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f70e1-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="f70e1-254">webapi webapi</span><span class="sxs-lookup"><span data-stu-id="f70e1-254">webapi</span></span>](#webapi)               | <span data-ttu-id="f70e1-255">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f70e1-255">[C#], F#</span></span>     | <span data-ttu-id="f70e1-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="f70e1-256">Web/WebAPI</span></span>                            | <span data-ttu-id="f70e1-257">1.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-257">1.0</span></span>        |
| <span data-ttu-id="f70e1-258">ASP.NET Core gRPC Service</span><span class="sxs-lookup"><span data-stu-id="f70e1-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="f70e1-259">grpc grpc</span><span class="sxs-lookup"><span data-stu-id="f70e1-259">grpc</span></span>](#web-others)             | <span data-ttu-id="f70e1-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="f70e1-260">[C#]</span></span>         | <span data-ttu-id="f70e1-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="f70e1-261">Web/gRPC</span></span>                              | <span data-ttu-id="f70e1-262">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-262">3.0</span></span>        |
| <span data-ttu-id="f70e1-263">Fichier tampon de protocole</span><span class="sxs-lookup"><span data-stu-id="f70e1-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="f70e1-264">Proto</span><span class="sxs-lookup"><span data-stu-id="f70e1-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="f70e1-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="f70e1-265">Web/gRPC</span></span>                              | <span data-ttu-id="f70e1-266">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-266">3.0</span></span>        |
| <span data-ttu-id="f70e1-267">fichier gitignore dotnet</span><span class="sxs-lookup"><span data-stu-id="f70e1-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="f70e1-268">Config</span><span class="sxs-lookup"><span data-stu-id="f70e1-268">Config</span></span>                                | <span data-ttu-id="f70e1-269">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-269">3.0</span></span>        |
| <span data-ttu-id="f70e1-270">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="f70e1-270">global.json file</span></span>                             | [<span data-ttu-id="f70e1-271">globaljson (globaljson)</span><span class="sxs-lookup"><span data-stu-id="f70e1-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="f70e1-272">Config</span><span class="sxs-lookup"><span data-stu-id="f70e1-272">Config</span></span>                                | <span data-ttu-id="f70e1-273">2</span><span class="sxs-lookup"><span data-stu-id="f70e1-273">2.0</span></span>        |
| <span data-ttu-id="f70e1-274">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="f70e1-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="f70e1-275">Config</span><span class="sxs-lookup"><span data-stu-id="f70e1-275">Config</span></span>                                | <span data-ttu-id="f70e1-276">1.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-276">1.0</span></span>        |
| <span data-ttu-id="f70e1-277">dotnet local outil manifeste fichier</span><span class="sxs-lookup"><span data-stu-id="f70e1-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="f70e1-278">Config</span><span class="sxs-lookup"><span data-stu-id="f70e1-278">Config</span></span>                                | <span data-ttu-id="f70e1-279">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-279">3.0</span></span>        |
| <span data-ttu-id="f70e1-280">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="f70e1-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="f70e1-281">Config</span><span class="sxs-lookup"><span data-stu-id="f70e1-281">Config</span></span>                                | <span data-ttu-id="f70e1-282">1.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-282">1.0</span></span>        |
| <span data-ttu-id="f70e1-283">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="f70e1-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="f70e1-284">Solution</span><span class="sxs-lookup"><span data-stu-id="f70e1-284">Solution</span></span>                              | <span data-ttu-id="f70e1-285">1.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="f70e1-286">Options</span><span class="sxs-lookup"><span data-stu-id="f70e1-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="f70e1-287">Affiche un résumé de ce qui se passerait si la commande donnée était exécutée.</span><span class="sxs-lookup"><span data-stu-id="f70e1-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="f70e1-288">Disponible depuis .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="f70e1-289">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="f70e1-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="f70e1-290">Cela est nécessaire lorsque le modèle choisi remplacerait les fichiers existants dans l’annuaire de sortie.</span><span class="sxs-lookup"><span data-stu-id="f70e1-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f70e1-291">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="f70e1-291">Prints out help for the command.</span></span> <span data-ttu-id="f70e1-292">Il peut être invoqué `dotnet new` pour la commande elle-même ou pour n’importe quel modèle.</span><span class="sxs-lookup"><span data-stu-id="f70e1-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="f70e1-293">Par exemple : `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="f70e1-294">Installe un pack de `PATH` `NUGET_ID` gabarit à partir de la ou fournie.</span><span class="sxs-lookup"><span data-stu-id="f70e1-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f70e1-295">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="f70e1-296">Par `dotnet new` défaut, \* passe pour la version, qui représente la dernière version de paquet stable.</span><span class="sxs-lookup"><span data-stu-id="f70e1-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="f70e1-297">Voir un exemple dans la section [Exemples.](#examples)</span><span class="sxs-lookup"><span data-stu-id="f70e1-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="f70e1-298">Si une version du modèle a déjà été installée lorsque vous exécutez cette commande, le modèle sera mis à jour à la version spécifiée, ou à la dernière version stable si aucune version n’a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f70e1-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="f70e1-299">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="f70e1-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="f70e1-300">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="f70e1-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="f70e1-301">Si aucun nom n’est spécifié, répertorie tous les modèles.</span><span class="sxs-lookup"><span data-stu-id="f70e1-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="f70e1-302">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="f70e1-302">The language of the template to create.</span></span> <span data-ttu-id="f70e1-303">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="f70e1-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f70e1-304">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="f70e1-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f70e1-305">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="f70e1-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="f70e1-306">Dans ces cas, joindre la valeur du paramètre linguistique dans les guillemets.</span><span class="sxs-lookup"><span data-stu-id="f70e1-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="f70e1-307">Par exemple : `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="f70e1-308">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="f70e1-308">The name for the created output.</span></span> <span data-ttu-id="f70e1-309">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f70e1-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="f70e1-310">Spécifie une source NuGet à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="f70e1-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="f70e1-311">Disponible depuis .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f70e1-312">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="f70e1-312">Location to place the generated output.</span></span> <span data-ttu-id="f70e1-313">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="f70e1-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="f70e1-314">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="f70e1-314">Filters templates based on available types.</span></span> <span data-ttu-id="f70e1-315">Les valeurs prédéfinies sont « project », « item » ou « other ».</span><span class="sxs-lookup"><span data-stu-id="f70e1-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="f70e1-316">Désinstallez un pack `PATH` de `NUGET_ID` gabarit ou fourni.</span><span class="sxs-lookup"><span data-stu-id="f70e1-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f70e1-317">Lorsque `<PATH|NUGET_ID>` la valeur n’est pas spécifiée, tous les packs de modèles actuellement installés et leurs modèles associés sont affichés.</span><span class="sxs-lookup"><span data-stu-id="f70e1-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="f70e1-318">Lorsque vous `NUGET_ID`spécifiez, n’incluez pas le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="f70e1-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="f70e1-319">Si vous ne spécifiez pas un paramètre à cette option, la commande répertorie les modèles installés et les détails à leur sujet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f70e1-320">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="f70e1-321">Par exemple, *\<C:/Users/ USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionnera, mais *./GarciaSoftware.ConsoleTemplate.CSharp* du dossier contenant ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="f70e1-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="f70e1-322">N’incluez pas une dernière barre oblique de terminat sur votre trajectoire de modèle.</span><span class="sxs-lookup"><span data-stu-id="f70e1-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="f70e1-323">Vérifie s’il existe des mises à jour disponibles pour les packs de modèles qui sont actuellement installés et les installe.</span><span class="sxs-lookup"><span data-stu-id="f70e1-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="f70e1-324">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f70e1-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="f70e1-325">Vérifie s’il existe des mises à jour disponibles pour les packs de modèles qui sont actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="f70e1-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="f70e1-326">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f70e1-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="f70e1-327">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="f70e1-327">Template options</span></span>

<span data-ttu-id="f70e1-328">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="f70e1-328">Each project template may have additional options available.</span></span> <span data-ttu-id="f70e1-329">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="f70e1-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="f70e1-330">console</span><span class="sxs-lookup"><span data-stu-id="f70e1-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f70e1-331">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f70e1-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f70e1-332">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f70e1-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f70e1-333">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f70e1-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f70e1-334">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f70e1-334">SDK version</span></span> | <span data-ttu-id="f70e1-335">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f70e1-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f70e1-336">3.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f70e1-337">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f70e1-338">Définit `LangVersion` la propriété dans le fichier de projet créé.</span><span class="sxs-lookup"><span data-stu-id="f70e1-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f70e1-339">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="f70e1-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="f70e1-340">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="f70e1-340">Not supported for F#.</span></span> <span data-ttu-id="f70e1-341">Disponible depuis .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f70e1-342">Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="f70e1-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f70e1-343">Si spécifié, n’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="f70e1-344">Disponible depuis .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="f70e1-345">classlib</span><span class="sxs-lookup"><span data-stu-id="f70e1-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f70e1-346">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f70e1-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f70e1-347">Valeurs : `netcoreapp<version>` pour créer une bibliothèque de classes .NET Core ou `netstandard<version>` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f70e1-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="f70e1-348">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f70e1-349">Définit `LangVersion` la propriété dans le fichier de projet créé.</span><span class="sxs-lookup"><span data-stu-id="f70e1-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f70e1-350">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="f70e1-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="f70e1-351">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="f70e1-351">Not supported for F#.</span></span> <span data-ttu-id="f70e1-352">Disponible depuis .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f70e1-353">Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="f70e1-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f70e1-354">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="f70e1-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="f70e1-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f70e1-356">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f70e1-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f70e1-357">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="f70e1-358">Disponible depuis .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f70e1-359">Définit `LangVersion` la propriété dans le fichier de projet créé.</span><span class="sxs-lookup"><span data-stu-id="f70e1-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f70e1-360">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="f70e1-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="f70e1-361">Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="f70e1-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f70e1-362">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="f70e1-363">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="f70e1-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="f70e1-364">Définit `LangVersion` la propriété dans le fichier de projet créé.</span><span class="sxs-lookup"><span data-stu-id="f70e1-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="f70e1-365">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="f70e1-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="f70e1-366">Pour une liste des versions par défaut de C, voir [Par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="f70e1-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f70e1-367">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="f70e1-368">travailleur, grpc</span><span class="sxs-lookup"><span data-stu-id="f70e1-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f70e1-369">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f70e1-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f70e1-370">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="f70e1-371">Disponible depuis .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f70e1-372">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f70e1-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f70e1-373">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="f70e1-374">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="f70e1-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f70e1-375">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f70e1-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f70e1-376">Option disponible depuis .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f70e1-377">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f70e1-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f70e1-378">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f70e1-378">SDK version</span></span> | <span data-ttu-id="f70e1-379">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f70e1-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f70e1-380">3.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f70e1-381">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="f70e1-382">Permet l’emballage pour le projet à l’aide [de dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="f70e1-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f70e1-383">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="f70e1-384">Nunit</span><span class="sxs-lookup"><span data-stu-id="f70e1-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f70e1-385">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f70e1-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="f70e1-386">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f70e1-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f70e1-387">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f70e1-387">SDK version</span></span> | <span data-ttu-id="f70e1-388">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f70e1-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f70e1-389">3.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f70e1-390">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f70e1-391">2.2</span><span class="sxs-lookup"><span data-stu-id="f70e1-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="f70e1-392">2.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="f70e1-393">Permet l’emballage pour le projet à l’aide [de dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="f70e1-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="f70e1-394">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="f70e1-395">page</span><span class="sxs-lookup"><span data-stu-id="f70e1-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="f70e1-396">Espace nom pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="f70e1-396">Namespace for the generated code.</span></span> <span data-ttu-id="f70e1-397">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="f70e1-398">Crée la page sans PageModel.</span><span class="sxs-lookup"><span data-stu-id="f70e1-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="f70e1-399">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="f70e1-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="f70e1-400">Espace nom pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="f70e1-400">Namespace for the generated code.</span></span> <span data-ttu-id="f70e1-401">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="f70e1-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="f70e1-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f70e1-403">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f70e1-403">The type of authentication to use.</span></span> <span data-ttu-id="f70e1-404">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f70e1-404">The possible values are:</span></span>

  - <span data-ttu-id="f70e1-405">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="f70e1-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f70e1-406">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="f70e1-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="f70e1-407">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="f70e1-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f70e1-408">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="f70e1-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f70e1-409">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="f70e1-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="f70e1-410">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="f70e1-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f70e1-411">L’instance Azure Active Directory B2C à connecter.</span><span class="sxs-lookup"><span data-stu-id="f70e1-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f70e1-412">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f70e1-413">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f70e1-414">L’id de la stratégie d’inscription et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f70e1-415">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="f70e1-416">L’ID de stratégie de mot de passe de réinitialisation pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="f70e1-417">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="f70e1-418">L’ID de la stratégie de profil d’édition pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="f70e1-419">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f70e1-420">L’instance Azure Active Directory à connecter.</span><span class="sxs-lookup"><span data-stu-id="f70e1-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f70e1-421">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f70e1-422">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f70e1-423">L’ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-423">The Client ID for this project.</span></span> <span data-ttu-id="f70e1-424">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f70e1-425">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f70e1-426">Le domaine pour le locataire de l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f70e1-426">The domain for the directory tenant.</span></span> <span data-ttu-id="f70e1-427">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f70e1-428">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f70e1-429">L’ID TenantId de l’annuaire pour se connecter à.</span><span class="sxs-lookup"><span data-stu-id="f70e1-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f70e1-430">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f70e1-431">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="f70e1-432">Le chemin de demande dans le chemin de base de l’application de l’URI rediriger.</span><span class="sxs-lookup"><span data-stu-id="f70e1-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f70e1-433">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f70e1-434">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f70e1-435">Permet à cette application de lire l’accès à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f70e1-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f70e1-436">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f70e1-437">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f70e1-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f70e1-438">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f70e1-438">Turns off HTTPS.</span></span> <span data-ttu-id="f70e1-439">Cette option ne `Individual` `IndividualB2C`s’applique `MultiOrg` que si, `--auth`, `SingleOrg`, ou ne sont pas utilisés pour .</span><span class="sxs-lookup"><span data-stu-id="f70e1-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f70e1-440">Spécifie LocalDB devrait être utilisé au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="f70e1-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f70e1-441">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f70e1-442">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="f70e1-443">web</span><span class="sxs-lookup"><span data-stu-id="f70e1-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f70e1-444">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f70e1-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f70e1-445">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f70e1-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f70e1-446">Option non disponible en .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f70e1-447">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f70e1-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f70e1-448">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f70e1-448">SDK version</span></span> | <span data-ttu-id="f70e1-449">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f70e1-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f70e1-450">3.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f70e1-451">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f70e1-452">2.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="f70e1-453">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f70e1-454">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f70e1-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="f70e1-455">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="f70e1-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f70e1-456">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f70e1-456">The type of authentication to use.</span></span> <span data-ttu-id="f70e1-457">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f70e1-457">The possible values are:</span></span>

  - <span data-ttu-id="f70e1-458">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="f70e1-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f70e1-459">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="f70e1-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="f70e1-460">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="f70e1-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f70e1-461">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="f70e1-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f70e1-462">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="f70e1-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="f70e1-463">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="f70e1-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f70e1-464">L’instance Azure Active Directory B2C à connecter.</span><span class="sxs-lookup"><span data-stu-id="f70e1-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f70e1-465">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f70e1-466">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f70e1-467">L’id de la stratégie d’inscription et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f70e1-468">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="f70e1-469">L’ID de stratégie de mot de passe de réinitialisation pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="f70e1-470">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="f70e1-471">L’ID de la stratégie de profil d’édition pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="f70e1-472">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f70e1-473">L’instance Azure Active Directory à connecter.</span><span class="sxs-lookup"><span data-stu-id="f70e1-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f70e1-474">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f70e1-475">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f70e1-476">L’ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-476">The Client ID for this project.</span></span> <span data-ttu-id="f70e1-477">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f70e1-478">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f70e1-479">Le domaine pour le locataire de l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f70e1-479">The domain for the directory tenant.</span></span> <span data-ttu-id="f70e1-480">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f70e1-481">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f70e1-482">L’ID TenantId de l’annuaire pour se connecter à.</span><span class="sxs-lookup"><span data-stu-id="f70e1-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f70e1-483">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f70e1-484">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="f70e1-485">Le chemin de demande dans le chemin de base de l’application de l’URI rediriger.</span><span class="sxs-lookup"><span data-stu-id="f70e1-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f70e1-486">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f70e1-487">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f70e1-488">Permet à cette application de lire l’accès à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f70e1-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f70e1-489">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f70e1-490">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f70e1-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f70e1-491">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f70e1-491">Turns off HTTPS.</span></span> <span data-ttu-id="f70e1-492">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="f70e1-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f70e1-493">Spécifie LocalDB devrait être utilisé au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="f70e1-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f70e1-494">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f70e1-495">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f70e1-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f70e1-496">Option disponible depuis .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f70e1-497">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f70e1-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f70e1-498">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f70e1-498">SDK version</span></span> | <span data-ttu-id="f70e1-499">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f70e1-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f70e1-500">3.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f70e1-501">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="f70e1-502">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="f70e1-503">Inclut BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="f70e1-504">Option non disponible en .NET Core 2.2 et 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="f70e1-505">angulaire, réagir</span><span class="sxs-lookup"><span data-stu-id="f70e1-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f70e1-506">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f70e1-506">The type of authentication to use.</span></span> <span data-ttu-id="f70e1-507">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f70e1-507">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="f70e1-508">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f70e1-508">The possible values are:</span></span>

  - <span data-ttu-id="f70e1-509">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="f70e1-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f70e1-510">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="f70e1-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f70e1-511">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f70e1-511">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f70e1-512">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f70e1-513">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f70e1-513">Turns off HTTPS.</span></span> <span data-ttu-id="f70e1-514">Cette option ne s’applique que si l’authentification est `None`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f70e1-515">Spécifie LocalDB devrait être utilisé au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="f70e1-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f70e1-516">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f70e1-517">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f70e1-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f70e1-518">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f70e1-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f70e1-519">Option non disponible en .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f70e1-520">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f70e1-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f70e1-521">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f70e1-521">SDK version</span></span> | <span data-ttu-id="f70e1-522">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f70e1-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f70e1-523">3.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f70e1-524">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f70e1-525">2.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="f70e1-526">reactredux</span><span class="sxs-lookup"><span data-stu-id="f70e1-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f70e1-527">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f70e1-527">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f70e1-528">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f70e1-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f70e1-529">Option non disponible en .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f70e1-530">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f70e1-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f70e1-531">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f70e1-531">SDK version</span></span> | <span data-ttu-id="f70e1-532">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f70e1-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f70e1-533">3.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f70e1-534">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f70e1-535">2.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="f70e1-536">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="f70e1-537">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f70e1-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="f70e1-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="f70e1-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="f70e1-539">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="f70e1-540">Prend en charge l’ajout de pages et de vues traditionnelles razor en plus des composants de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="f70e1-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="f70e1-541">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f70e1-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="f70e1-542">webapi</span><span class="sxs-lookup"><span data-stu-id="f70e1-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="f70e1-543">Type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f70e1-543">The type of authentication to use.</span></span> <span data-ttu-id="f70e1-544">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f70e1-544">The possible values are:</span></span>

  - <span data-ttu-id="f70e1-545">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="f70e1-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="f70e1-546">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="f70e1-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="f70e1-547">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="f70e1-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="f70e1-548">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="f70e1-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="f70e1-549">L’instance Azure Active Directory B2C à connecter.</span><span class="sxs-lookup"><span data-stu-id="f70e1-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f70e1-550">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f70e1-551">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="f70e1-552">L’id de la stratégie d’inscription et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f70e1-553">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="f70e1-554">L’instance Azure Active Directory à connecter.</span><span class="sxs-lookup"><span data-stu-id="f70e1-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f70e1-555">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f70e1-556">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="f70e1-557">L’ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-557">The Client ID for this project.</span></span> <span data-ttu-id="f70e1-558">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f70e1-559">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="f70e1-560">Le domaine pour le locataire de l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f70e1-560">The domain for the directory tenant.</span></span> <span data-ttu-id="f70e1-561">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f70e1-562">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="f70e1-563">L’ID TenantId de l’annuaire pour se connecter à.</span><span class="sxs-lookup"><span data-stu-id="f70e1-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f70e1-564">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f70e1-565">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="f70e1-566">Permet à cette application de lire l’accès à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="f70e1-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="f70e1-567">Ne s’applique qu’à l’authentification. `SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="f70e1-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="f70e1-568">Exclut *le lancementSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="f70e1-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="f70e1-569">Éteint HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f70e1-569">Turns off HTTPS.</span></span> <span data-ttu-id="f70e1-570">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="f70e1-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="f70e1-571">Cette option ne `IndividualB2C` `SingleOrg` s’applique que si l’authentification est utilisée ou non.</span><span class="sxs-lookup"><span data-stu-id="f70e1-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="f70e1-572">Spécifie LocalDB devrait être utilisé au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="f70e1-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f70e1-573">Ne s’applique qu’à l’authentification. `IndividualB2C`</span><span class="sxs-lookup"><span data-stu-id="f70e1-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f70e1-574">Spécifie le [cadre](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="f70e1-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f70e1-575">Option non disponible en .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f70e1-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="f70e1-576">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version SDK que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="f70e1-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="f70e1-577">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="f70e1-577">SDK version</span></span> | <span data-ttu-id="f70e1-578">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f70e1-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="f70e1-579">3.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="f70e1-580">3.0</span><span class="sxs-lookup"><span data-stu-id="f70e1-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="f70e1-581">2.1</span><span class="sxs-lookup"><span data-stu-id="f70e1-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="f70e1-582">N’exécute pas une restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="f70e1-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="f70e1-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="f70e1-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="f70e1-584">Spécifie la version du .NET Core SDK à utiliser dans le fichier *global.json.*</span><span class="sxs-lookup"><span data-stu-id="f70e1-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="f70e1-585">Exemples</span><span class="sxs-lookup"><span data-stu-id="f70e1-585">Examples</span></span>

- <span data-ttu-id="f70e1-586">Créez un projet d’application console C# en spécifiant le nom du modèle :</span><span class="sxs-lookup"><span data-stu-id="f70e1-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="f70e1-587">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="f70e1-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="f70e1-588">Créez un projet de bibliothèque de classe Standard .NET dans l’annuaire spécifié :</span><span class="sxs-lookup"><span data-stu-id="f70e1-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="f70e1-589">Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :</span><span class="sxs-lookup"><span data-stu-id="f70e1-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="f70e1-590">Créez un projet xUnit :</span><span class="sxs-lookup"><span data-stu-id="f70e1-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="f70e1-591">Énumérez tous les modèles disponibles pour les modèles d’application d’une page unique (SPA) :</span><span class="sxs-lookup"><span data-stu-id="f70e1-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="f70e1-592">Liste de tous les modèles correspondant à la sous-chaîne *we*.</span><span class="sxs-lookup"><span data-stu-id="f70e1-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="f70e1-593">Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.</span><span class="sxs-lookup"><span data-stu-id="f70e1-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="f70e1-594">Tentative d’appel du modèle correspondant à *ng*.</span><span class="sxs-lookup"><span data-stu-id="f70e1-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="f70e1-595">Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.</span><span class="sxs-lookup"><span data-stu-id="f70e1-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="f70e1-596">Installer la version 2.0 des modèles SPA pour ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="f70e1-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="f70e1-597">Énumérez les modèles et les détails installés à leur sujet, y compris la façon de les désinstaller :</span><span class="sxs-lookup"><span data-stu-id="f70e1-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="f70e1-598">Créez un *global.json* dans l’annuaire actuel définissant la version SDK à 3.1.101 :</span><span class="sxs-lookup"><span data-stu-id="f70e1-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="f70e1-599">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f70e1-599">See also</span></span>

- [<span data-ttu-id="f70e1-600">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="f70e1-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="f70e1-601">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="f70e1-601">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="f70e1-602">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="f70e1-602">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="f70e1-603">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="f70e1-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
