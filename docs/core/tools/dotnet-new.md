---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
ms.date: 02/13/2020
ms.openlocfilehash: f11512acf5a1fdc4bde49b3d1212ccf6335dff8b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451328"
---
# <a name="dotnet-new"></a><span data-ttu-id="0d84b-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="0d84b-103">dotnet new</span></span>

<span data-ttu-id="0d84b-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="0d84b-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0d84b-105">Name</span><span class="sxs-lookup"><span data-stu-id="0d84b-105">Name</span></span>

<span data-ttu-id="0d84b-106">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d84b-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0d84b-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="0d84b-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] 
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="0d84b-108">Description</span><span class="sxs-lookup"><span data-stu-id="0d84b-108">Description</span></span>

<span data-ttu-id="0d84b-109">La commande `dotnet new` crée un projet .NET Core ou d’autres artefacts basés sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="0d84b-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="0d84b-110">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0d84b-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="0d84b-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="0d84b-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="0d84b-112">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="0d84b-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="0d84b-113">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="0d84b-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="0d84b-114">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="0d84b-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="0d84b-115">Vous pouvez exécuter `dotnet new --list` pour afficher la liste de tous les modèles installés.</span><span class="sxs-lookup"><span data-stu-id="0d84b-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="0d84b-116">Si la valeur de `TEMPLATE` ne correspond pas exactement au texte de la colonne **Templates** ou **Short Name** de la table retournée, une correspondance de sous-chaîne est effectuée sur ces deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="0d84b-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="0d84b-117">À compter du kit de développement logiciel (SDK) .NET Core 3,0, l’interface CLI recherche des modèles dans NuGet.org quand vous appelez la commande `dotnet new` dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="0d84b-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="0d84b-118">Si l’interface CLI ne trouve pas de correspondance de modèle lors de l’appel de `dotnet new`, pas encore partielle.</span><span class="sxs-lookup"><span data-stu-id="0d84b-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="0d84b-119">Si une version plus récente du modèle est disponible.</span><span class="sxs-lookup"><span data-stu-id="0d84b-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="0d84b-120">Dans ce cas, le projet ou l’artefact est créé, mais l’interface CLI vous avertit d’une version mise à jour du modèle.</span><span class="sxs-lookup"><span data-stu-id="0d84b-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="0d84b-121">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="0d84b-121">The command contains a default list of templates.</span></span> <span data-ttu-id="0d84b-122">Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="0d84b-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="0d84b-123">Le tableau suivant répertorie les modèles qui sont préinstallés avec le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0d84b-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="0d84b-124">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="0d84b-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="0d84b-125">Cliquez sur le lien nom abrégé pour afficher les options de modèle spécifiques.</span><span class="sxs-lookup"><span data-stu-id="0d84b-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="0d84b-126">Modèles</span><span class="sxs-lookup"><span data-stu-id="0d84b-126">Templates</span></span>                                    | <span data-ttu-id="0d84b-127">Nom court</span><span class="sxs-lookup"><span data-stu-id="0d84b-127">Short name</span></span>                      | <span data-ttu-id="0d84b-128">Langage</span><span class="sxs-lookup"><span data-stu-id="0d84b-128">Language</span></span>     | <span data-ttu-id="0d84b-129">Balises</span><span class="sxs-lookup"><span data-stu-id="0d84b-129">Tags</span></span>                                  | <span data-ttu-id="0d84b-130">Présent</span><span class="sxs-lookup"><span data-stu-id="0d84b-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="0d84b-131">Application console</span><span class="sxs-lookup"><span data-stu-id="0d84b-131">Console Application</span></span>                          | [<span data-ttu-id="0d84b-132">console</span><span class="sxs-lookup"><span data-stu-id="0d84b-132">console</span></span>](#console)             | <span data-ttu-id="0d84b-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0d84b-133">[C#], F#, VB</span></span> | <span data-ttu-id="0d84b-134">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="0d84b-134">Common/Console</span></span>                        | <span data-ttu-id="0d84b-135">1.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-135">1.0</span></span>        |
| <span data-ttu-id="0d84b-136">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="0d84b-136">Class library</span></span>                                | [<span data-ttu-id="0d84b-137">classlib</span><span class="sxs-lookup"><span data-stu-id="0d84b-137">classlib</span></span>](#classlib)           | <span data-ttu-id="0d84b-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0d84b-138">[C#], F#, VB</span></span> | <span data-ttu-id="0d84b-139">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="0d84b-139">Common/Library</span></span>                        | <span data-ttu-id="0d84b-140">1.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-140">1.0</span></span>        |
| <span data-ttu-id="0d84b-141">Application WPF</span><span class="sxs-lookup"><span data-stu-id="0d84b-141">WPF Application</span></span>                              | [<span data-ttu-id="0d84b-142">WPF</span><span class="sxs-lookup"><span data-stu-id="0d84b-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="0d84b-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-143">[C#]</span></span>         | <span data-ttu-id="0d84b-144">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="0d84b-144">Common/WPF</span></span>                            | <span data-ttu-id="0d84b-145">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-145">3.0</span></span>        |
| <span data-ttu-id="0d84b-146">Bibliothèque de classes WPF</span><span class="sxs-lookup"><span data-stu-id="0d84b-146">WPF Class library</span></span>                            | [<span data-ttu-id="0d84b-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="0d84b-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="0d84b-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-148">[C#]</span></span>         | <span data-ttu-id="0d84b-149">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="0d84b-149">Common/WPF</span></span>                            | <span data-ttu-id="0d84b-150">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-150">3.0</span></span>        |
| <span data-ttu-id="0d84b-151">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="0d84b-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="0d84b-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="0d84b-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="0d84b-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-153">[C#]</span></span>         | <span data-ttu-id="0d84b-154">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="0d84b-154">Common/WPF</span></span>                            | <span data-ttu-id="0d84b-155">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-155">3.0</span></span>        |
| <span data-ttu-id="0d84b-156">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="0d84b-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="0d84b-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="0d84b-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="0d84b-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-158">[C#]</span></span>         | <span data-ttu-id="0d84b-159">Commun/WPF</span><span class="sxs-lookup"><span data-stu-id="0d84b-159">Common/WPF</span></span>                            | <span data-ttu-id="0d84b-160">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-160">3.0</span></span>        |
| <span data-ttu-id="0d84b-161">Application Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="0d84b-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="0d84b-162">WinForms</span><span class="sxs-lookup"><span data-stu-id="0d84b-162">winforms</span></span>](#winforms)           | <span data-ttu-id="0d84b-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-163">[C#]</span></span>         | <span data-ttu-id="0d84b-164">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="0d84b-164">Common/WinForms</span></span>                       | <span data-ttu-id="0d84b-165">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-165">3.0</span></span>        |
| <span data-ttu-id="0d84b-166">Bibliothèque de classes Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="0d84b-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="0d84b-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="0d84b-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="0d84b-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-168">[C#]</span></span>         | <span data-ttu-id="0d84b-169">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="0d84b-169">Common/WinForms</span></span>                       | <span data-ttu-id="0d84b-170">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-170">3.0</span></span>        |
| <span data-ttu-id="0d84b-171">Service Worker</span><span class="sxs-lookup"><span data-stu-id="0d84b-171">Worker Service</span></span>                               | [<span data-ttu-id="0d84b-172">collabor</span><span class="sxs-lookup"><span data-stu-id="0d84b-172">worker</span></span>](#web-others)           | <span data-ttu-id="0d84b-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-173">[C#]</span></span>         | <span data-ttu-id="0d84b-174">Commun/Worker/Web</span><span class="sxs-lookup"><span data-stu-id="0d84b-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="0d84b-175">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-175">3.0</span></span>        |
| <span data-ttu-id="0d84b-176">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="0d84b-176">Unit Test Project</span></span>                            | [<span data-ttu-id="0d84b-177">MSTest</span><span class="sxs-lookup"><span data-stu-id="0d84b-177">mstest</span></span>](#test)                 | <span data-ttu-id="0d84b-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0d84b-178">[C#], F#, VB</span></span> | <span data-ttu-id="0d84b-179">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="0d84b-179">Test/MSTest</span></span>                           | <span data-ttu-id="0d84b-180">1.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-180">1.0</span></span>        |
| <span data-ttu-id="0d84b-181">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="0d84b-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="0d84b-182">nunit</span><span class="sxs-lookup"><span data-stu-id="0d84b-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="0d84b-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0d84b-183">[C#], F#, VB</span></span> | <span data-ttu-id="0d84b-184">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="0d84b-184">Test/NUnit</span></span>                            | <span data-ttu-id="0d84b-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="0d84b-185">2.1.400</span></span>    |
| <span data-ttu-id="0d84b-186">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="0d84b-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="0d84b-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0d84b-187">[C#], F#, VB</span></span> | <span data-ttu-id="0d84b-188">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="0d84b-188">Test/NUnit</span></span>                            | <span data-ttu-id="0d84b-189">2.2</span><span class="sxs-lookup"><span data-stu-id="0d84b-189">2.2</span></span>        |
| <span data-ttu-id="0d84b-190">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="0d84b-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="0d84b-191">xUnit</span><span class="sxs-lookup"><span data-stu-id="0d84b-191">xunit</span></span>](#test)                  | <span data-ttu-id="0d84b-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0d84b-192">[C#], F#, VB</span></span> | <span data-ttu-id="0d84b-193">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="0d84b-193">Test/xUnit</span></span>                            | <span data-ttu-id="0d84b-194">1.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-194">1.0</span></span>        |
| <span data-ttu-id="0d84b-195">Composant Razor</span><span class="sxs-lookup"><span data-stu-id="0d84b-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="0d84b-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-196">[C#]</span></span>         | <span data-ttu-id="0d84b-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0d84b-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="0d84b-198">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-198">3.0</span></span>        |
| <span data-ttu-id="0d84b-199">Page Razor</span><span class="sxs-lookup"><span data-stu-id="0d84b-199">Razor Page</span></span>                                   | [<span data-ttu-id="0d84b-200">page</span><span class="sxs-lookup"><span data-stu-id="0d84b-200">page</span></span>](#page)                   | <span data-ttu-id="0d84b-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-201">[C#]</span></span>         | <span data-ttu-id="0d84b-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0d84b-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="0d84b-203">2</span><span class="sxs-lookup"><span data-stu-id="0d84b-203">2.0</span></span>        |
| <span data-ttu-id="0d84b-204">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="0d84b-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="0d84b-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="0d84b-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="0d84b-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-206">[C#]</span></span>         | <span data-ttu-id="0d84b-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0d84b-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="0d84b-208">2</span><span class="sxs-lookup"><span data-stu-id="0d84b-208">2.0</span></span>        |
| <span data-ttu-id="0d84b-209">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="0d84b-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="0d84b-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-210">[C#]</span></span>         | <span data-ttu-id="0d84b-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0d84b-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="0d84b-212">2</span><span class="sxs-lookup"><span data-stu-id="0d84b-212">2.0</span></span>        |
| <span data-ttu-id="0d84b-213">Application de serveur éblouissante</span><span class="sxs-lookup"><span data-stu-id="0d84b-213">Blazor Server App</span></span>                            | [<span data-ttu-id="0d84b-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="0d84b-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="0d84b-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-215">[C#]</span></span>         | <span data-ttu-id="0d84b-216">Web/éblouissant</span><span class="sxs-lookup"><span data-stu-id="0d84b-216">Web/Blazor</span></span>                            | <span data-ttu-id="0d84b-217">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-217">3.0</span></span>        |
| <span data-ttu-id="0d84b-218">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="0d84b-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="0d84b-219">web</span><span class="sxs-lookup"><span data-stu-id="0d84b-219">web</span></span>](#web)                     | <span data-ttu-id="0d84b-220">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0d84b-220">[C#], F#</span></span>     | <span data-ttu-id="0d84b-221">Web/vides</span><span class="sxs-lookup"><span data-stu-id="0d84b-221">Web/Empty</span></span>                             | <span data-ttu-id="0d84b-222">1.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-222">1.0</span></span>        |
| <span data-ttu-id="0d84b-223">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="0d84b-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="0d84b-224">mvc</span><span class="sxs-lookup"><span data-stu-id="0d84b-224">mvc</span></span>](#web-options)             | <span data-ttu-id="0d84b-225">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0d84b-225">[C#], F#</span></span>     | <span data-ttu-id="0d84b-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="0d84b-226">Web/MVC</span></span>                               | <span data-ttu-id="0d84b-227">1.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-227">1.0</span></span>        |
| <span data-ttu-id="0d84b-228">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0d84b-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="0d84b-229">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="0d84b-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="0d84b-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-230">[C#]</span></span>         | <span data-ttu-id="0d84b-231">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="0d84b-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="0d84b-232">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="0d84b-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="0d84b-233">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="0d84b-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="0d84b-234">oblique</span><span class="sxs-lookup"><span data-stu-id="0d84b-234">angular</span></span>](#spa)                 | <span data-ttu-id="0d84b-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-235">[C#]</span></span>         | <span data-ttu-id="0d84b-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="0d84b-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="0d84b-237">2</span><span class="sxs-lookup"><span data-stu-id="0d84b-237">2.0</span></span>        |
| <span data-ttu-id="0d84b-238">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="0d84b-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="0d84b-239">réagir</span><span class="sxs-lookup"><span data-stu-id="0d84b-239">react</span></span>](#spa)                   | <span data-ttu-id="0d84b-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-240">[C#]</span></span>         | <span data-ttu-id="0d84b-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="0d84b-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="0d84b-242">2</span><span class="sxs-lookup"><span data-stu-id="0d84b-242">2.0</span></span>        |
| <span data-ttu-id="0d84b-243">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="0d84b-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="0d84b-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="0d84b-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="0d84b-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-245">[C#]</span></span>         | <span data-ttu-id="0d84b-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="0d84b-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="0d84b-247">2</span><span class="sxs-lookup"><span data-stu-id="0d84b-247">2.0</span></span>        |
| <span data-ttu-id="0d84b-248">Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="0d84b-248">Razor Class Library</span></span>                          | [<span data-ttu-id="0d84b-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="0d84b-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="0d84b-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-250">[C#]</span></span>         | <span data-ttu-id="0d84b-251">Web/Razor/Library/Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="0d84b-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="0d84b-252">2.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-252">2.1</span></span>        |
| <span data-ttu-id="0d84b-253">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0d84b-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="0d84b-254">webapi</span><span class="sxs-lookup"><span data-stu-id="0d84b-254">webapi</span></span>](#webapi)               | <span data-ttu-id="0d84b-255">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0d84b-255">[C#], F#</span></span>     | <span data-ttu-id="0d84b-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="0d84b-256">Web/WebAPI</span></span>                            | <span data-ttu-id="0d84b-257">1.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-257">1.0</span></span>        |
| <span data-ttu-id="0d84b-258">ASP.NET Core Service gRPC</span><span class="sxs-lookup"><span data-stu-id="0d84b-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="0d84b-259">GRPC</span><span class="sxs-lookup"><span data-stu-id="0d84b-259">grpc</span></span>](#web-others)             | <span data-ttu-id="0d84b-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="0d84b-260">[C#]</span></span>         | <span data-ttu-id="0d84b-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="0d84b-261">Web/gRPC</span></span>                              | <span data-ttu-id="0d84b-262">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-262">3.0</span></span>        |
| <span data-ttu-id="0d84b-263">Fichier de mémoire tampon de protocole</span><span class="sxs-lookup"><span data-stu-id="0d84b-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="0d84b-264">proto</span><span class="sxs-lookup"><span data-stu-id="0d84b-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="0d84b-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="0d84b-265">Web/gRPC</span></span>                              | <span data-ttu-id="0d84b-266">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-266">3.0</span></span>        |
| <span data-ttu-id="0d84b-267">fichier gitignore dotnet</span><span class="sxs-lookup"><span data-stu-id="0d84b-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="0d84b-268">Config</span><span class="sxs-lookup"><span data-stu-id="0d84b-268">Config</span></span>                                | <span data-ttu-id="0d84b-269">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-269">3.0</span></span>        |
| <span data-ttu-id="0d84b-270">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="0d84b-270">global.json file</span></span>                             | [<span data-ttu-id="0d84b-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="0d84b-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="0d84b-272">Config</span><span class="sxs-lookup"><span data-stu-id="0d84b-272">Config</span></span>                                | <span data-ttu-id="0d84b-273">2</span><span class="sxs-lookup"><span data-stu-id="0d84b-273">2.0</span></span>        |
| <span data-ttu-id="0d84b-274">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="0d84b-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="0d84b-275">Config</span><span class="sxs-lookup"><span data-stu-id="0d84b-275">Config</span></span>                                | <span data-ttu-id="0d84b-276">1.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-276">1.0</span></span>        |
| <span data-ttu-id="0d84b-277">fichier manifeste de l’outil local dotnet</span><span class="sxs-lookup"><span data-stu-id="0d84b-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="0d84b-278">Config</span><span class="sxs-lookup"><span data-stu-id="0d84b-278">Config</span></span>                                | <span data-ttu-id="0d84b-279">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-279">3.0</span></span>        |
| <span data-ttu-id="0d84b-280">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="0d84b-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="0d84b-281">Config</span><span class="sxs-lookup"><span data-stu-id="0d84b-281">Config</span></span>                                | <span data-ttu-id="0d84b-282">1.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-282">1.0</span></span>        |
| <span data-ttu-id="0d84b-283">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="0d84b-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="0d84b-284">Solution</span><span class="sxs-lookup"><span data-stu-id="0d84b-284">Solution</span></span>                              | <span data-ttu-id="0d84b-285">1.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="0d84b-286">Options</span><span class="sxs-lookup"><span data-stu-id="0d84b-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="0d84b-287">Affiche un résumé de ce qui se passerait si la commande donnée était exécutée.</span><span class="sxs-lookup"><span data-stu-id="0d84b-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="0d84b-288">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="0d84b-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="0d84b-289">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="0d84b-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="0d84b-290">Cela est obligatoire lorsque le modèle choisi remplace les fichiers existants dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="0d84b-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0d84b-291">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="0d84b-291">Prints out help for the command.</span></span> <span data-ttu-id="0d84b-292">Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle.</span><span class="sxs-lookup"><span data-stu-id="0d84b-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="0d84b-293">Par exemple : `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="0d84b-294">Installe un pack de modèles à partir du `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="0d84b-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="0d84b-295">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="0d84b-296">Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package.</span><span class="sxs-lookup"><span data-stu-id="0d84b-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="0d84b-297">Consultez un exemple dans la section [exemples](#examples) .</span><span class="sxs-lookup"><span data-stu-id="0d84b-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="0d84b-298">Si une version du modèle a déjà été installée lorsque vous exécutez cette commande, le modèle sera mis à jour vers la version spécifiée, ou vers la version stable la plus récente si aucune version n’a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0d84b-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="0d84b-299">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="0d84b-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="0d84b-300">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d84b-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="0d84b-301">Si aucun nom n’est spécifié, répertorie tous les modèles.</span><span class="sxs-lookup"><span data-stu-id="0d84b-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="0d84b-302">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="0d84b-302">The language of the template to create.</span></span> <span data-ttu-id="0d84b-303">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="0d84b-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="0d84b-304">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="0d84b-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="0d84b-305">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="0d84b-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="0d84b-306">Dans ce cas, mettez la valeur du paramètre de langue entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="0d84b-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="0d84b-307">Par exemple : `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="0d84b-308">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="0d84b-308">The name for the created output.</span></span> <span data-ttu-id="0d84b-309">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0d84b-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="0d84b-310">Spécifie une source NuGet à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="0d84b-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="0d84b-311">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="0d84b-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="0d84b-312">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="0d84b-312">Location to place the generated output.</span></span> <span data-ttu-id="0d84b-313">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="0d84b-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="0d84b-314">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="0d84b-314">Filters templates based on available types.</span></span> <span data-ttu-id="0d84b-315">Les valeurs prédéfinies sont « project », « item » ou « other ».</span><span class="sxs-lookup"><span data-stu-id="0d84b-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="0d84b-316">Désinstalle un pack de modèles au `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="0d84b-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="0d84b-317">Lorsque la valeur de `<PATH|NUGET_ID>` n’est pas spécifiée, tous les packs de modèles actuellement installés et leurs modèles associés sont affichés.</span><span class="sxs-lookup"><span data-stu-id="0d84b-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="0d84b-318">Lorsque vous spécifiez `NUGET_ID`, n’incluez pas le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="0d84b-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="0d84b-319">Si vous ne spécifiez pas de paramètre pour cette option, la commande répertorie les modèles installés et fournit des détails à leur sujet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="0d84b-320">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="0d84b-321">Par exemple, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionne, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="0d84b-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="0d84b-322">N’incluez pas de barre oblique finale de répertoire finale dans le chemin d’accès de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="0d84b-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="0d84b-323">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés et les installe.</span><span class="sxs-lookup"><span data-stu-id="0d84b-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="0d84b-324">Disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0d84b-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="0d84b-325">Vérifie si des mises à jour sont disponibles pour les packs de modèles qui sont actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="0d84b-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="0d84b-326">Disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0d84b-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="0d84b-327">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="0d84b-327">Template options</span></span>

<span data-ttu-id="0d84b-328">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="0d84b-328">Each project template may have additional options available.</span></span> <span data-ttu-id="0d84b-329">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="0d84b-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="0d84b-330">console</span><span class="sxs-lookup"><span data-stu-id="0d84b-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0d84b-331">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="0d84b-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0d84b-332">Disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0d84b-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="0d84b-333">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="0d84b-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="0d84b-334">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="0d84b-334">SDK version</span></span> | <span data-ttu-id="0d84b-335">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="0d84b-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="0d84b-336">3.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="0d84b-337">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="0d84b-338">Définit la propriété `LangVersion` dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="0d84b-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="0d84b-339">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="0d84b-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="0d84b-340">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="0d84b-340">Not supported for F#.</span></span> <span data-ttu-id="0d84b-341">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="0d84b-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="0d84b-342">Pour obtenir la liste des C# versions par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="0d84b-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`** 

  <span data-ttu-id="0d84b-343">S’il est spécifié, n’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="0d84b-344">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="0d84b-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="0d84b-345">classlib</span><span class="sxs-lookup"><span data-stu-id="0d84b-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0d84b-346">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="0d84b-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0d84b-347">Valeurs : `netcoreapp<version>` pour créer une bibliothèque de classes .NET Core ou `netstandard<version>` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0d84b-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="0d84b-348">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="0d84b-349">Définit la propriété `LangVersion` dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="0d84b-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="0d84b-350">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="0d84b-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="0d84b-351">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="0d84b-351">Not supported for F#.</span></span> <span data-ttu-id="0d84b-352">Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="0d84b-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="0d84b-353">Pour obtenir la liste des C# versions par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="0d84b-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="0d84b-354">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="0d84b-355">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="0d84b-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0d84b-356">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="0d84b-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0d84b-357">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="0d84b-358">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="0d84b-358">Available since .NET Core 3.1 SDK.</span></span> 

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="0d84b-359">Définit la propriété `LangVersion` dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="0d84b-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="0d84b-360">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="0d84b-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="0d84b-361">Pour obtenir la liste des C# versions par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="0d84b-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="0d84b-362">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="0d84b-363">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="0d84b-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="0d84b-364">Définit la propriété `LangVersion` dans le fichier projet créé.</span><span class="sxs-lookup"><span data-stu-id="0d84b-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="0d84b-365">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="0d84b-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="0d84b-366">Pour obtenir la liste des C# versions par défaut, consultez [valeurs par défaut](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="0d84b-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="0d84b-367">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="0d84b-368">Worker, GRPC</span><span class="sxs-lookup"><span data-stu-id="0d84b-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0d84b-369">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="0d84b-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0d84b-370">La valeur par défaut est `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="0d84b-371">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="0d84b-371">Available since .NET Core 3.1 SDK.</span></span> 

- **`--exclude-launch-settings`**

  <span data-ttu-id="0d84b-372">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="0d84b-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="0d84b-373">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="0d84b-374">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="0d84b-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0d84b-375">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="0d84b-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0d84b-376">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0d84b-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="0d84b-377">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="0d84b-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="0d84b-378">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="0d84b-378">SDK version</span></span> | <span data-ttu-id="0d84b-379">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="0d84b-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="0d84b-380">3.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="0d84b-381">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="0d84b-382">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="0d84b-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="0d84b-383">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="0d84b-384">nunit</span><span class="sxs-lookup"><span data-stu-id="0d84b-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0d84b-385">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="0d84b-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="0d84b-386">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="0d84b-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="0d84b-387">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="0d84b-387">SDK version</span></span> | <span data-ttu-id="0d84b-388">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="0d84b-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="0d84b-389">3.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="0d84b-390">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="0d84b-391">2.2</span><span class="sxs-lookup"><span data-stu-id="0d84b-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="0d84b-392">2.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="0d84b-393">Active l’empaquetage pour le projet à l’aide de [dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="0d84b-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="0d84b-394">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="0d84b-395">page</span><span class="sxs-lookup"><span data-stu-id="0d84b-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="0d84b-396">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="0d84b-396">Namespace for the generated code.</span></span> <span data-ttu-id="0d84b-397">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="0d84b-398">Crée la page sans PageModel.</span><span class="sxs-lookup"><span data-stu-id="0d84b-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="0d84b-399">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="0d84b-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="0d84b-400">Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="0d84b-400">Namespace for the generated code.</span></span> <span data-ttu-id="0d84b-401">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="0d84b-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="0d84b-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="0d84b-403">Type de l’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0d84b-403">The type of authentication to use.</span></span> <span data-ttu-id="0d84b-404">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0d84b-404">The possible values are:</span></span>

  - <span data-ttu-id="0d84b-405">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="0d84b-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="0d84b-406">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="0d84b-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="0d84b-407">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0d84b-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="0d84b-408">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="0d84b-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="0d84b-409">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="0d84b-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="0d84b-410">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="0d84b-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="0d84b-411">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="0d84b-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0d84b-412">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0d84b-413">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="0d84b-414">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0d84b-415">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="0d84b-416">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="0d84b-417">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="0d84b-418">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="0d84b-419">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="0d84b-420">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="0d84b-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0d84b-421">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="0d84b-422">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="0d84b-423">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-423">The Client ID for this project.</span></span> <span data-ttu-id="0d84b-424">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="0d84b-425">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="0d84b-426">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="0d84b-426">The domain for the directory tenant.</span></span> <span data-ttu-id="0d84b-427">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0d84b-428">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="0d84b-429">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="0d84b-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0d84b-430">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0d84b-431">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="0d84b-432">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="0d84b-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="0d84b-433">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0d84b-434">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="0d84b-435">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="0d84b-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="0d84b-436">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="0d84b-437">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="0d84b-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="0d84b-438">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="0d84b-438">Turns off HTTPS.</span></span> <span data-ttu-id="0d84b-439">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg`ou `MultiOrg` ne sont pas utilisés pour `--auth`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="0d84b-440">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="0d84b-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0d84b-441">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="0d84b-442">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="0d84b-443">web</span><span class="sxs-lookup"><span data-stu-id="0d84b-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="0d84b-444">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="0d84b-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0d84b-445">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="0d84b-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0d84b-446">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="0d84b-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="0d84b-447">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="0d84b-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="0d84b-448">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="0d84b-448">SDK version</span></span> | <span data-ttu-id="0d84b-449">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="0d84b-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="0d84b-450">3.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="0d84b-451">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="0d84b-452">2.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="0d84b-453">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="0d84b-454">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="0d84b-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="0d84b-455">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="0d84b-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="0d84b-456">Type de l’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0d84b-456">The type of authentication to use.</span></span> <span data-ttu-id="0d84b-457">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0d84b-457">The possible values are:</span></span>

  - <span data-ttu-id="0d84b-458">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="0d84b-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="0d84b-459">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="0d84b-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="0d84b-460">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0d84b-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="0d84b-461">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="0d84b-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="0d84b-462">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="0d84b-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="0d84b-463">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="0d84b-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="0d84b-464">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="0d84b-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0d84b-465">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0d84b-466">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="0d84b-467">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0d84b-468">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="0d84b-469">ID de la stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="0d84b-470">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="0d84b-471">ID de stratégie de modification de profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="0d84b-472">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="0d84b-473">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="0d84b-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0d84b-474">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="0d84b-475">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="0d84b-476">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-476">The Client ID for this project.</span></span> <span data-ttu-id="0d84b-477">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="0d84b-478">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="0d84b-479">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="0d84b-479">The domain for the directory tenant.</span></span> <span data-ttu-id="0d84b-480">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0d84b-481">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="0d84b-482">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="0d84b-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0d84b-483">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0d84b-484">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="0d84b-485">Chemin d’accès de la requête dans le chemin d’accès de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="0d84b-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="0d84b-486">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0d84b-487">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="0d84b-488">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="0d84b-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="0d84b-489">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="0d84b-490">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="0d84b-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="0d84b-491">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="0d84b-491">Turns off HTTPS.</span></span> <span data-ttu-id="0d84b-492">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="0d84b-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="0d84b-493">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="0d84b-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0d84b-494">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0d84b-495">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="0d84b-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0d84b-496">Option disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0d84b-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="0d84b-497">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="0d84b-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="0d84b-498">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="0d84b-498">SDK version</span></span> | <span data-ttu-id="0d84b-499">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="0d84b-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="0d84b-500">3.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="0d84b-501">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="0d84b-502">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="0d84b-503">Comprend BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="0d84b-504">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2 et 3,1.</span><span class="sxs-lookup"><span data-stu-id="0d84b-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="0d84b-505">angulaire, réaction</span><span class="sxs-lookup"><span data-stu-id="0d84b-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="0d84b-506">Type de l’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0d84b-506">The type of authentication to use.</span></span> <span data-ttu-id="0d84b-507">Disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0d84b-507">Available since .NET Core 3.0 SDK.</span></span> 
  
  <span data-ttu-id="0d84b-508">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0d84b-508">The possible values are:</span></span>

  - <span data-ttu-id="0d84b-509">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="0d84b-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="0d84b-510">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="0d84b-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="0d84b-511">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="0d84b-511">Excludes *launchSettings.json* from the generated template.</span></span> 

- **`--no-restore`**

  <span data-ttu-id="0d84b-512">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="0d84b-513">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="0d84b-513">Turns off HTTPS.</span></span> <span data-ttu-id="0d84b-514">Cette option s’applique uniquement si l’authentification est `None`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="0d84b-515">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="0d84b-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0d84b-516">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0d84b-517">Disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0d84b-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0d84b-518">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="0d84b-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0d84b-519">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="0d84b-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="0d84b-520">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="0d84b-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="0d84b-521">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="0d84b-521">SDK version</span></span> | <span data-ttu-id="0d84b-522">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="0d84b-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="0d84b-523">3.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="0d84b-524">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="0d84b-525">2.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="0d84b-526">reactredux</span><span class="sxs-lookup"><span data-stu-id="0d84b-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="0d84b-527">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="0d84b-527">Excludes *launchSettings.json* from the generated template.</span></span> 

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0d84b-528">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="0d84b-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0d84b-529">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="0d84b-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="0d84b-530">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="0d84b-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="0d84b-531">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="0d84b-531">SDK version</span></span> | <span data-ttu-id="0d84b-532">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="0d84b-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="0d84b-533">3.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="0d84b-534">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="0d84b-535">2.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="0d84b-536">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="0d84b-537">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="0d84b-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="0d84b-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="0d84b-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="0d84b-539">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="0d84b-540">Prend en charge l’ajout de pages et de vues Razor traditionnelles en plus des composants de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="0d84b-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="0d84b-541">Disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0d84b-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="0d84b-542">webapi</span><span class="sxs-lookup"><span data-stu-id="0d84b-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="0d84b-543">Type de l’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0d84b-543">The type of authentication to use.</span></span> <span data-ttu-id="0d84b-544">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0d84b-544">The possible values are:</span></span>

  - <span data-ttu-id="0d84b-545">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="0d84b-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="0d84b-546">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0d84b-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="0d84b-547">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="0d84b-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="0d84b-548">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="0d84b-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="0d84b-549">Instance Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="0d84b-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0d84b-550">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0d84b-551">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="0d84b-552">ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0d84b-553">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="0d84b-554">Instance Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="0d84b-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0d84b-555">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0d84b-556">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="0d84b-557">ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-557">The Client ID for this project.</span></span> <span data-ttu-id="0d84b-558">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="0d84b-559">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="0d84b-560">Domaine du locataire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="0d84b-560">The domain for the directory tenant.</span></span> <span data-ttu-id="0d84b-561">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="0d84b-562">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="0d84b-563">ID TenantId de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="0d84b-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0d84b-564">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0d84b-565">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="0d84b-566">Permet à cette application d’accéder en lecture à l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="0d84b-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="0d84b-567">S’applique uniquement à l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="0d84b-568">Exclut *launchSettings. JSON* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="0d84b-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="0d84b-569">Désactive le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="0d84b-569">Turns off HTTPS.</span></span> <span data-ttu-id="0d84b-570">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="0d84b-571">Cette option s’applique uniquement si `IndividualB2C` ou `SingleOrg` ne sont pas utilisés pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="0d84b-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="0d84b-572">Spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="0d84b-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0d84b-573">S’applique uniquement à l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0d84b-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0d84b-574">Spécifie le [Framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="0d84b-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0d84b-575">Option non disponible dans le kit de développement logiciel (SDK) .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="0d84b-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="0d84b-576">Le tableau suivant répertorie les valeurs par défaut en fonction du numéro de version du kit de développement logiciel (SDK) que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="0d84b-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="0d84b-577">Version du SDK</span><span class="sxs-lookup"><span data-stu-id="0d84b-577">SDK version</span></span> | <span data-ttu-id="0d84b-578">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="0d84b-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="0d84b-579">3.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="0d84b-580">3.0</span><span class="sxs-lookup"><span data-stu-id="0d84b-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="0d84b-581">2.1</span><span class="sxs-lookup"><span data-stu-id="0d84b-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="0d84b-582">N’exécute pas de restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="0d84b-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="0d84b-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="0d84b-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="0d84b-584">Spécifie la version de la kit SDK .NET Core à utiliser dans le fichier *global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="0d84b-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="0d84b-585">Exemples</span><span class="sxs-lookup"><span data-stu-id="0d84b-585">Examples</span></span>

- <span data-ttu-id="0d84b-586">Créez un projet d’application console C# en spécifiant le nom du modèle :</span><span class="sxs-lookup"><span data-stu-id="0d84b-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="0d84b-587">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="0d84b-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="0d84b-588">Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié :</span><span class="sxs-lookup"><span data-stu-id="0d84b-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="0d84b-589">Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :</span><span class="sxs-lookup"><span data-stu-id="0d84b-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="0d84b-590">Créez un projet xUnit :</span><span class="sxs-lookup"><span data-stu-id="0d84b-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="0d84b-591">Répertorier tous les modèles disponibles pour les modèles d’application à page unique (SPA) :</span><span class="sxs-lookup"><span data-stu-id="0d84b-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="0d84b-592">Liste de tous les modèles correspondant à la sous-chaîne *we*.</span><span class="sxs-lookup"><span data-stu-id="0d84b-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="0d84b-593">Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.</span><span class="sxs-lookup"><span data-stu-id="0d84b-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="0d84b-594">Tentative d’appel du modèle correspondant à *ng*.</span><span class="sxs-lookup"><span data-stu-id="0d84b-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="0d84b-595">Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.</span><span class="sxs-lookup"><span data-stu-id="0d84b-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="0d84b-596">Installez la version 2,0 des modèles SPA pour ASP.NET Core :</span><span class="sxs-lookup"><span data-stu-id="0d84b-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="0d84b-597">Répertoriez les modèles installés et les détails les concernant, notamment comment les désinstaller :</span><span class="sxs-lookup"><span data-stu-id="0d84b-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="0d84b-598">Créez un *global. JSON* dans le répertoire actif en définissant la version du kit de développement logiciel (SDK) sur 3.1.101 :</span><span class="sxs-lookup"><span data-stu-id="0d84b-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="0d84b-599">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d84b-599">See also</span></span>

- [<span data-ttu-id="0d84b-600">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="0d84b-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="0d84b-601">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="0d84b-601">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="0d84b-602">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="0d84b-602">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="0d84b-603">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="0d84b-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
