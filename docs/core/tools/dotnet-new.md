---
title: Commande dotnet new
description: La commande dotnet new crée des projets .NET Core basés sur le modèle spécifié.
ms.date: 05/06/2019
ms.openlocfilehash: f8bc8cb59ae6e421f4e9bd05925376399939056d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878314"
---
# <a name="dotnet-new"></a><span data-ttu-id="4a67d-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="4a67d-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4a67d-104">Name</span><span class="sxs-lookup"><span data-stu-id="4a67d-104">Name</span></span>

<span data-ttu-id="4a67d-105">`dotnet new` : crée un projet, un fichier de configuration ou une solution en fonction du modèle spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a67d-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4a67d-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="4a67d-106">Synopsis</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="4a67d-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="4a67d-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4a67d-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4a67d-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4a67d-109">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4a67d-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4a67d-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4a67d-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="4a67d-111">Description</span><span class="sxs-lookup"><span data-stu-id="4a67d-111">Description</span></span>

<span data-ttu-id="4a67d-112">La commande `dotnet new` offre un moyen pratique d’initialiser un projet .NET Core valide.</span><span class="sxs-lookup"><span data-stu-id="4a67d-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="4a67d-113">La commande appelle le [moteur de modèles](https://github.com/dotnet/templating) pour créer les artefacts sur le disque en fonction du modèle et des options spécifiés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="4a67d-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a67d-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="4a67d-115">Modèle à instancier quand la commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="4a67d-116">Vous pouvez passer des options spécifiques pour chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="4a67d-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="4a67d-117">Pour plus d'informations, consultez [Options de modèle](#template-options).</span><span class="sxs-lookup"><span data-stu-id="4a67d-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="4a67d-118">Si la valeur `TEMPLATE` ne correspond pas exactement au texte des colonnes **Modèles** ou **Nom court**, une comparaison de sous-chaîne est exécutée sur ces deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="4a67d-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="4a67d-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="4a67d-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="4a67d-120">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-120">The command contains a default list of templates.</span></span> <span data-ttu-id="4a67d-121">Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="4a67d-122">Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="4a67d-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="4a67d-123">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="4a67d-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="4a67d-124">Modèles</span><span class="sxs-lookup"><span data-stu-id="4a67d-124">Templates</span></span>                                    | <span data-ttu-id="4a67d-125">Nom court</span><span class="sxs-lookup"><span data-stu-id="4a67d-125">Short Name</span></span>        | <span data-ttu-id="4a67d-126">Langue</span><span class="sxs-lookup"><span data-stu-id="4a67d-126">Language</span></span>     | <span data-ttu-id="4a67d-127">Balises</span><span class="sxs-lookup"><span data-stu-id="4a67d-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="4a67d-128">Application console</span><span class="sxs-lookup"><span data-stu-id="4a67d-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="4a67d-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-129">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-130">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="4a67d-130">Common/Console</span></span>                        |
| <span data-ttu-id="4a67d-131">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="4a67d-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="4a67d-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-132">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-133">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="4a67d-133">Common/Library</span></span>                        |
| <span data-ttu-id="4a67d-134">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="4a67d-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="4a67d-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-135">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="4a67d-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="4a67d-137">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="4a67d-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="4a67d-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-138">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="4a67d-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="4a67d-140">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="4a67d-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="4a67d-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-141">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="4a67d-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="4a67d-143">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="4a67d-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="4a67d-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-144">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="4a67d-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="4a67d-146">Page Razor</span><span class="sxs-lookup"><span data-stu-id="4a67d-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="4a67d-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-147">[C#]</span></span>         | <span data-ttu-id="4a67d-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4a67d-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a67d-149">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="4a67d-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="4a67d-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-150">[C#]</span></span>         | <span data-ttu-id="4a67d-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4a67d-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a67d-152">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="4a67d-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="4a67d-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-153">[C#]</span></span>         | <span data-ttu-id="4a67d-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4a67d-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a67d-155">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="4a67d-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="4a67d-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-156">[C#], F#</span></span>     | <span data-ttu-id="4a67d-157">Web/vides</span><span class="sxs-lookup"><span data-stu-id="4a67d-157">Web/Empty</span></span>                             |
| <span data-ttu-id="4a67d-158">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="4a67d-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="4a67d-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-159">[C#], F#</span></span>     | <span data-ttu-id="4a67d-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="4a67d-160">Web/MVC</span></span>                               |
| <span data-ttu-id="4a67d-161">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a67d-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="4a67d-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="4a67d-162">`webapp`, `razor`</span></span> | <span data-ttu-id="4a67d-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-163">[C#]</span></span>         | <span data-ttu-id="4a67d-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="4a67d-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="4a67d-165">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="4a67d-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="4a67d-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-166">[C#]</span></span>         | <span data-ttu-id="4a67d-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a67d-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="4a67d-168">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="4a67d-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="4a67d-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-169">[C#]</span></span>         | <span data-ttu-id="4a67d-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a67d-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="4a67d-171">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="4a67d-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="4a67d-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-172">[C#]</span></span>         | <span data-ttu-id="4a67d-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a67d-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="4a67d-174">Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="4a67d-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="4a67d-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-175">[C#]</span></span>         | <span data-ttu-id="4a67d-176">Web/Razor/Library/Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="4a67d-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="4a67d-177">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a67d-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="4a67d-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-178">[C#], F#</span></span>     | <span data-ttu-id="4a67d-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="4a67d-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="4a67d-180">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="4a67d-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="4a67d-181">Config</span><span class="sxs-lookup"><span data-stu-id="4a67d-181">Config</span></span>                                |
| <span data-ttu-id="4a67d-182">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="4a67d-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="4a67d-183">Config</span><span class="sxs-lookup"><span data-stu-id="4a67d-183">Config</span></span>                                |
| <span data-ttu-id="4a67d-184">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="4a67d-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="4a67d-185">Config</span><span class="sxs-lookup"><span data-stu-id="4a67d-185">Config</span></span>                                |
| <span data-ttu-id="4a67d-186">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="4a67d-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="4a67d-187">Solution</span><span class="sxs-lookup"><span data-stu-id="4a67d-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4a67d-188">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4a67d-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="4a67d-189">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-189">The command contains a default list of templates.</span></span> <span data-ttu-id="4a67d-190">Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="4a67d-191">Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="4a67d-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="4a67d-192">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="4a67d-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="4a67d-193">Modèles</span><span class="sxs-lookup"><span data-stu-id="4a67d-193">Templates</span></span>                                    | <span data-ttu-id="4a67d-194">Nom court</span><span class="sxs-lookup"><span data-stu-id="4a67d-194">Short Name</span></span>      | <span data-ttu-id="4a67d-195">Langue</span><span class="sxs-lookup"><span data-stu-id="4a67d-195">Language</span></span>     | <span data-ttu-id="4a67d-196">Balises</span><span class="sxs-lookup"><span data-stu-id="4a67d-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="4a67d-197">Application console</span><span class="sxs-lookup"><span data-stu-id="4a67d-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="4a67d-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-198">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-199">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="4a67d-199">Common/Console</span></span>                        |
| <span data-ttu-id="4a67d-200">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="4a67d-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="4a67d-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-201">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-202">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="4a67d-202">Common/Library</span></span>                        |
| <span data-ttu-id="4a67d-203">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="4a67d-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="4a67d-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-204">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="4a67d-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="4a67d-206">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="4a67d-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="4a67d-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-207">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="4a67d-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="4a67d-209">Page Razor</span><span class="sxs-lookup"><span data-stu-id="4a67d-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="4a67d-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-210">[C#]</span></span>         | <span data-ttu-id="4a67d-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4a67d-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a67d-212">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="4a67d-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="4a67d-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-213">[C#]</span></span>         | <span data-ttu-id="4a67d-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4a67d-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a67d-215">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="4a67d-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="4a67d-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-216">[C#]</span></span>         | <span data-ttu-id="4a67d-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4a67d-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a67d-218">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="4a67d-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="4a67d-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-219">[C#], F#</span></span>     | <span data-ttu-id="4a67d-220">Web/vides</span><span class="sxs-lookup"><span data-stu-id="4a67d-220">Web/Empty</span></span>                             |
| <span data-ttu-id="4a67d-221">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="4a67d-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="4a67d-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-222">[C#], F#</span></span>     | <span data-ttu-id="4a67d-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="4a67d-223">Web/MVC</span></span>                               |
| <span data-ttu-id="4a67d-224">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a67d-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="4a67d-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-225">[C#]</span></span>         | <span data-ttu-id="4a67d-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="4a67d-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="4a67d-227">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="4a67d-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="4a67d-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-228">[C#]</span></span>         | <span data-ttu-id="4a67d-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a67d-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="4a67d-230">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="4a67d-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="4a67d-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-231">[C#]</span></span>         | <span data-ttu-id="4a67d-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a67d-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="4a67d-233">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="4a67d-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="4a67d-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-234">[C#]</span></span>         | <span data-ttu-id="4a67d-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a67d-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="4a67d-236">Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="4a67d-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="4a67d-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-237">[C#]</span></span>         | <span data-ttu-id="4a67d-238">Web/Razor/Library/Bibliothèque de classes Razor</span><span class="sxs-lookup"><span data-stu-id="4a67d-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="4a67d-239">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a67d-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="4a67d-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-240">[C#], F#</span></span>     | <span data-ttu-id="4a67d-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="4a67d-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="4a67d-242">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="4a67d-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="4a67d-243">Config</span><span class="sxs-lookup"><span data-stu-id="4a67d-243">Config</span></span>                                |
| <span data-ttu-id="4a67d-244">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="4a67d-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="4a67d-245">Config</span><span class="sxs-lookup"><span data-stu-id="4a67d-245">Config</span></span>                                |
| <span data-ttu-id="4a67d-246">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="4a67d-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="4a67d-247">Config</span><span class="sxs-lookup"><span data-stu-id="4a67d-247">Config</span></span>                                |
| <span data-ttu-id="4a67d-248">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="4a67d-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="4a67d-249">Solution</span><span class="sxs-lookup"><span data-stu-id="4a67d-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4a67d-250">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4a67d-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="4a67d-251">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-251">The command contains a default list of templates.</span></span> <span data-ttu-id="4a67d-252">Utilisez `dotnet new -l` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="4a67d-253">Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="4a67d-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="4a67d-254">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="4a67d-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="4a67d-255">Modèles</span><span class="sxs-lookup"><span data-stu-id="4a67d-255">Templates</span></span>                                    | <span data-ttu-id="4a67d-256">Nom court</span><span class="sxs-lookup"><span data-stu-id="4a67d-256">Short Name</span></span>    | <span data-ttu-id="4a67d-257">Langue</span><span class="sxs-lookup"><span data-stu-id="4a67d-257">Language</span></span>     | <span data-ttu-id="4a67d-258">Balises</span><span class="sxs-lookup"><span data-stu-id="4a67d-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="4a67d-259">Application console</span><span class="sxs-lookup"><span data-stu-id="4a67d-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="4a67d-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-260">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-261">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="4a67d-261">Common/Console</span></span>      |
| <span data-ttu-id="4a67d-262">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="4a67d-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="4a67d-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-263">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-264">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="4a67d-264">Common/Library</span></span>      |
| <span data-ttu-id="4a67d-265">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="4a67d-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="4a67d-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-266">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="4a67d-267">Test/MSTest</span></span>         |
| <span data-ttu-id="4a67d-268">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="4a67d-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="4a67d-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4a67d-269">[C#], F#, VB</span></span> | <span data-ttu-id="4a67d-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="4a67d-270">Test/xUnit</span></span>          |
| <span data-ttu-id="4a67d-271">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="4a67d-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="4a67d-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-272">[C#], F#</span></span>     | <span data-ttu-id="4a67d-273">Web/vides</span><span class="sxs-lookup"><span data-stu-id="4a67d-273">Web/Empty</span></span>           |
| <span data-ttu-id="4a67d-274">Application web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="4a67d-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="4a67d-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-275">[C#], F#</span></span>     | <span data-ttu-id="4a67d-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="4a67d-276">Web/MVC</span></span>             |
| <span data-ttu-id="4a67d-277">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a67d-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="4a67d-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-278">[C#]</span></span>         | <span data-ttu-id="4a67d-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="4a67d-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="4a67d-280">ASP.NET Core avec Angular</span><span class="sxs-lookup"><span data-stu-id="4a67d-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="4a67d-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-281">[C#]</span></span>         | <span data-ttu-id="4a67d-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a67d-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="4a67d-283">ASP.NET Core avec React.js</span><span class="sxs-lookup"><span data-stu-id="4a67d-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="4a67d-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-284">[C#]</span></span>         | <span data-ttu-id="4a67d-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a67d-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="4a67d-286">ASP.NET Core avec React.js et Redux</span><span class="sxs-lookup"><span data-stu-id="4a67d-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="4a67d-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-287">[C#]</span></span>         | <span data-ttu-id="4a67d-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a67d-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="4a67d-289">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a67d-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="4a67d-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-290">[C#], F#</span></span>     | <span data-ttu-id="4a67d-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="4a67d-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="4a67d-292">fichier global.json</span><span class="sxs-lookup"><span data-stu-id="4a67d-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="4a67d-293">Config</span><span class="sxs-lookup"><span data-stu-id="4a67d-293">Config</span></span>              |
| <span data-ttu-id="4a67d-294">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="4a67d-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="4a67d-295">Config</span><span class="sxs-lookup"><span data-stu-id="4a67d-295">Config</span></span>              |
| <span data-ttu-id="4a67d-296">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="4a67d-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="4a67d-297">Config</span><span class="sxs-lookup"><span data-stu-id="4a67d-297">Config</span></span>              |
| <span data-ttu-id="4a67d-298">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="4a67d-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="4a67d-299">Solution</span><span class="sxs-lookup"><span data-stu-id="4a67d-299">Solution</span></span>            |
| <span data-ttu-id="4a67d-300">Page Razor</span><span class="sxs-lookup"><span data-stu-id="4a67d-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="4a67d-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4a67d-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="4a67d-302">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="4a67d-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="4a67d-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4a67d-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="4a67d-304">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="4a67d-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="4a67d-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4a67d-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4a67d-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4a67d-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="4a67d-307">La commande contient une liste par défaut de modèles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-307">The command contains a default list of templates.</span></span> <span data-ttu-id="4a67d-308">Utilisez `dotnet new -all` pour obtenir une liste des modèles disponibles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="4a67d-309">Le tableau suivant présente les modèles préinstallés avec le SDK .NET Core 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="4a67d-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="4a67d-310">Le langage par défaut pour le modèle est indiqué entre crochets.</span><span class="sxs-lookup"><span data-stu-id="4a67d-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="4a67d-311">Modèles</span><span class="sxs-lookup"><span data-stu-id="4a67d-311">Templates</span></span>            | <span data-ttu-id="4a67d-312">Nom court</span><span class="sxs-lookup"><span data-stu-id="4a67d-312">Short Name</span></span>    | <span data-ttu-id="4a67d-313">Langue</span><span class="sxs-lookup"><span data-stu-id="4a67d-313">Language</span></span> | <span data-ttu-id="4a67d-314">Balises</span><span class="sxs-lookup"><span data-stu-id="4a67d-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="4a67d-315">Application console</span><span class="sxs-lookup"><span data-stu-id="4a67d-315">Console Application</span></span>  | `console`     | <span data-ttu-id="4a67d-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-316">[C#], F#</span></span> | <span data-ttu-id="4a67d-317">Communes/Console</span><span class="sxs-lookup"><span data-stu-id="4a67d-317">Common/Console</span></span> |
| <span data-ttu-id="4a67d-318">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="4a67d-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="4a67d-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-319">[C#], F#</span></span> | <span data-ttu-id="4a67d-320">Communes/Bibliothèque</span><span class="sxs-lookup"><span data-stu-id="4a67d-320">Common/Library</span></span> |
| <span data-ttu-id="4a67d-321">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="4a67d-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="4a67d-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-322">[C#], F#</span></span> | <span data-ttu-id="4a67d-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="4a67d-323">Test/MSTest</span></span>    |
| <span data-ttu-id="4a67d-324">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="4a67d-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="4a67d-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-325">[C#], F#</span></span> | <span data-ttu-id="4a67d-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="4a67d-326">Test/xUnit</span></span>     |
| <span data-ttu-id="4a67d-327">ASP.NET Core vide</span><span class="sxs-lookup"><span data-stu-id="4a67d-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="4a67d-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-328">[C#]</span></span>     | <span data-ttu-id="4a67d-329">Web/vides</span><span class="sxs-lookup"><span data-stu-id="4a67d-329">Web/Empty</span></span>      |
| <span data-ttu-id="4a67d-330">Application web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a67d-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="4a67d-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4a67d-331">[C#], F#</span></span> | <span data-ttu-id="4a67d-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="4a67d-332">Web/MVC</span></span>        |
| <span data-ttu-id="4a67d-333">API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a67d-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="4a67d-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a67d-334">[C#]</span></span>     | <span data-ttu-id="4a67d-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="4a67d-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="4a67d-336">Configuration NuGet</span><span class="sxs-lookup"><span data-stu-id="4a67d-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="4a67d-337">Config</span><span class="sxs-lookup"><span data-stu-id="4a67d-337">Config</span></span>         |
| <span data-ttu-id="4a67d-338">Configuration Web</span><span class="sxs-lookup"><span data-stu-id="4a67d-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="4a67d-339">Config</span><span class="sxs-lookup"><span data-stu-id="4a67d-339">Config</span></span>         |
| <span data-ttu-id="4a67d-340">Fichier solution</span><span class="sxs-lookup"><span data-stu-id="4a67d-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="4a67d-341">Solution</span><span class="sxs-lookup"><span data-stu-id="4a67d-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="4a67d-342">Options</span><span class="sxs-lookup"><span data-stu-id="4a67d-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="4a67d-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="4a67d-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="4a67d-344">Affiche un récapitulatif de ce qui se passerait si la commande donnée était exécutée (si cela donnerait lieu à la création d’un modèle).</span><span class="sxs-lookup"><span data-stu-id="4a67d-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="4a67d-345">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="4a67d-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="4a67d-346">Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4a67d-347">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="4a67d-347">Prints out help for the command.</span></span> <span data-ttu-id="4a67d-348">Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="4a67d-349">Installe un pack source ou de modèle à partir du `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="4a67d-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4a67d-350">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="4a67d-351">Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package.</span><span class="sxs-lookup"><span data-stu-id="4a67d-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="4a67d-352">Consultez un exemple dans la section [Exemples](#examples).</span><span class="sxs-lookup"><span data-stu-id="4a67d-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="4a67d-353">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4a67d-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="4a67d-354">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a67d-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="4a67d-355">Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné.</span><span class="sxs-lookup"><span data-stu-id="4a67d-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4a67d-356">Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="4a67d-357">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="4a67d-357">The language of the template to create.</span></span> <span data-ttu-id="4a67d-358">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="4a67d-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4a67d-359">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="4a67d-360">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="4a67d-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4a67d-361">Dans ce cas, vous devez placer la valeur de paramètre de langage entre guillemets doubles, par exemple `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4a67d-362">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-362">The name for the created output.</span></span> <span data-ttu-id="4a67d-363">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4a67d-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="4a67d-364">Spécifie une source NuGet à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="4a67d-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4a67d-365">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-365">Location to place the generated output.</span></span> <span data-ttu-id="4a67d-366">La valeur par défaut correspond au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="4a67d-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="4a67d-367">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-367">Filters templates based on available types.</span></span> <span data-ttu-id="4a67d-368">Les valeurs prédéfinies sont « project », « item » ou « other ».</span><span class="sxs-lookup"><span data-stu-id="4a67d-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="4a67d-369">Désinstalle un pack source ou de modèle au `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="4a67d-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4a67d-370">Quand vous excluez la valeur `<PATH|NUGET_ID>`, tous les packs de modèles actuellement installés sont affichés, ainsi que les modèles qui leur sont associés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="4a67d-371">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="4a67d-372">Par exemple, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionne, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="4a67d-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="4a67d-373">En outre, n’incluez pas de barre oblique finale après le répertoire dans votre chemin d’accès au modèle.</span><span class="sxs-lookup"><span data-stu-id="4a67d-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4a67d-374">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4a67d-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="4a67d-375">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="4a67d-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="4a67d-376">Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4a67d-377">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="4a67d-377">Prints out help for the command.</span></span> <span data-ttu-id="4a67d-378">Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="4a67d-379">Installe un pack source ou de modèle à partir du `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="4a67d-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4a67d-380">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="4a67d-381">Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package.</span><span class="sxs-lookup"><span data-stu-id="4a67d-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="4a67d-382">Consultez un exemple dans la section [Exemples](#examples).</span><span class="sxs-lookup"><span data-stu-id="4a67d-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="4a67d-383">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4a67d-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="4a67d-384">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a67d-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="4a67d-385">Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné.</span><span class="sxs-lookup"><span data-stu-id="4a67d-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4a67d-386">Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="4a67d-387">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="4a67d-387">The language of the template to create.</span></span> <span data-ttu-id="4a67d-388">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="4a67d-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4a67d-389">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="4a67d-390">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="4a67d-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4a67d-391">Dans ce cas, vous devez placer la valeur de paramètre de langage entre guillemets doubles, par exemple `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4a67d-392">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-392">The name for the created output.</span></span> <span data-ttu-id="4a67d-393">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4a67d-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="4a67d-394">Spécifie une source NuGet à utiliser pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="4a67d-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4a67d-395">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-395">Location to place the generated output.</span></span> <span data-ttu-id="4a67d-396">La valeur par défaut correspond au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="4a67d-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="4a67d-397">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-397">Filters templates based on available types.</span></span> <span data-ttu-id="4a67d-398">Les valeurs prédéfinies sont « project », « item » ou « other ».</span><span class="sxs-lookup"><span data-stu-id="4a67d-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="4a67d-399">Désinstalle un pack source ou de modèle au `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="4a67d-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="4a67d-400">Pour désinstaller un modèle à l’aide de `PATH`, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="4a67d-401">Par exemple, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionne, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="4a67d-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="4a67d-402">En outre, n’incluez pas de barre oblique finale après le répertoire dans votre chemin d’accès au modèle.</span><span class="sxs-lookup"><span data-stu-id="4a67d-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4a67d-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4a67d-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="4a67d-404">Force le contenu à être généré même s’il change les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="4a67d-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="4a67d-405">Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4a67d-406">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="4a67d-406">Prints out help for the command.</span></span> <span data-ttu-id="4a67d-407">Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="4a67d-408">Installe un pack source ou de modèle à partir du `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="4a67d-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4a67d-409">Si vous souhaitez installer une préversion d’un package de modèle, vous devez spécifier la version au format `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="4a67d-410">Par défaut, `dotnet new` passe \* pour la version, qui représente la dernière version stable du package.</span><span class="sxs-lookup"><span data-stu-id="4a67d-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="4a67d-411">Consultez un exemple dans la section [Exemples](#examples).</span><span class="sxs-lookup"><span data-stu-id="4a67d-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="4a67d-412">Pour plus d’informations sur la création de modèles personnalisés, consultez [Modèles personnalisés pour dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4a67d-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="4a67d-413">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a67d-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="4a67d-414">Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné.</span><span class="sxs-lookup"><span data-stu-id="4a67d-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4a67d-415">Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="4a67d-416">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="4a67d-416">The language of the template to create.</span></span> <span data-ttu-id="4a67d-417">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="4a67d-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4a67d-418">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="4a67d-419">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="4a67d-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4a67d-420">Dans ce cas, vous devez placer la valeur de paramètre de langage entre guillemets doubles, par exemple `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4a67d-421">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-421">The name for the created output.</span></span> <span data-ttu-id="4a67d-422">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4a67d-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4a67d-423">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-423">Location to place the generated output.</span></span> <span data-ttu-id="4a67d-424">La valeur par défaut correspond au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="4a67d-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="4a67d-425">Filtre les modèles en fonction des types disponibles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-425">Filters templates based on available types.</span></span> <span data-ttu-id="4a67d-426">Les valeurs prédéfinies sont « project », « item » ou « other ».</span><span class="sxs-lookup"><span data-stu-id="4a67d-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="4a67d-427">Désinstalle un pack source ou de modèle au `PATH` ou `NUGET_ID` fourni.</span><span class="sxs-lookup"><span data-stu-id="4a67d-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="4a67d-428">Pour désinstaller un modèle à l’aide de `PATH` source, vous devez qualifier le chemin d’accès avec un nom complet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="4a67d-429">Par exemple, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* fonctionne, mais *./GarciaSoftware.ConsoleTemplate.CSharp* à partir du dossier conteneur ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="4a67d-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="4a67d-430">En outre, n’incluez pas de barre oblique finale après le répertoire dans votre chemin d’accès au modèle.</span><span class="sxs-lookup"><span data-stu-id="4a67d-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="4a67d-431">Si vous ne parvenez pas à déterminer l’argument `PATH` ou `NUGET_ID` nécessaire pour désinstaller un modèle, l’exécution de `dotnet new --uninstall` sans argument répertorie tous les modèles installés et l’argument requis pour les désinstaller.</span><span class="sxs-lookup"><span data-stu-id="4a67d-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4a67d-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4a67d-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="4a67d-433">Affiche tous les modèles pour un type de projet spécifique lors de l’exécution dans le contexte de la commande `dotnet new` seule.</span><span class="sxs-lookup"><span data-stu-id="4a67d-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="4a67d-434">Lors de l’exécution dans le contexte d’un modèle spécifique, comme `dotnet new web -all`, `-all` est interprété comme un indicateur de création forcée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="4a67d-435">Ceci est nécessaire quand le répertoire de sortie contient déjà un projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4a67d-436">Affiche l’aide pour la commande.</span><span class="sxs-lookup"><span data-stu-id="4a67d-436">Prints out help for the command.</span></span> <span data-ttu-id="4a67d-437">Elle peut être appelée pour la commande `dotnet new` elle-même ou pour n’importe quel modèle, par exemple, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="4a67d-438">Liste les modèles contenant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a67d-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="4a67d-439">Si elle est appelée pour la commande `dotnet new`, elle liste les modèles disponibles dans le répertoire donné.</span><span class="sxs-lookup"><span data-stu-id="4a67d-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4a67d-440">Par exemple, si le répertoire contient déjà un projet, elle ne liste pas tous les modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="4a67d-441">Langage du modèle à créer.</span><span class="sxs-lookup"><span data-stu-id="4a67d-441">The language of the template to create.</span></span> <span data-ttu-id="4a67d-442">Le langage accepté diffère selon le modèle (voir les valeurs par défaut dans la section [arguments](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="4a67d-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4a67d-443">Non valide pour certains modèles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="4a67d-444">Certains interpréteurs interprètent la commande `#` comme un caractère spécial.</span><span class="sxs-lookup"><span data-stu-id="4a67d-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4a67d-445">Dans ce cas, vous devez placer la valeur de paramètre de langage entre guillemets doubles, par exemple `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4a67d-446">Le nom de la sortie créée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-446">The name for the created output.</span></span> <span data-ttu-id="4a67d-447">Si aucun nom n’est spécifié, le nom du répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4a67d-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4a67d-448">Emplacement où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-448">Location to place the generated output.</span></span> <span data-ttu-id="4a67d-449">La valeur par défaut correspond au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="4a67d-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="4a67d-450">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="4a67d-450">Template options</span></span>

<span data-ttu-id="4a67d-451">Chaque modèle de projet peut présenter d’autres options disponibles.</span><span class="sxs-lookup"><span data-stu-id="4a67d-451">Each project template may have additional options available.</span></span> <span data-ttu-id="4a67d-452">Les modèles de base ont les options supplémentaires suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a67d-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="4a67d-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="4a67d-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="4a67d-454">**console**</span><span class="sxs-lookup"><span data-stu-id="4a67d-454">**console**</span></span>

<span data-ttu-id="4a67d-455">`--langVersion <VERSION_NUMBER>` - Définit la propriété `LangVersion` dans le fichier de projet créé.</span><span class="sxs-lookup"><span data-stu-id="4a67d-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="4a67d-456">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="4a67d-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="4a67d-457">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="4a67d-457">Not supported for F#.</span></span>

<span data-ttu-id="4a67d-458">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-459">**angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="4a67d-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="4a67d-460">`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a67d-461">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-462">`--no-https` - Le projet ne nécessite pas le protocole HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a67d-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a67d-463">Cette option s’applique uniquement si `IndividualAuth` ou `OrganizationalAuth` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="4a67d-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="4a67d-464">**razorclasslib**</span></span>

<span data-ttu-id="4a67d-465">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="4a67d-466">**classlib**</span></span>

<span data-ttu-id="4a67d-467">`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="4a67d-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a67d-468">Valeurs : `netcoreapp2.2` pour créer une bibliothèque de classes .NET Core ou `netstandard2.0` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4a67d-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="4a67d-469">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="4a67d-470">`--langVersion <VERSION_NUMBER>` - Définit la propriété `LangVersion` dans le fichier de projet créé.</span><span class="sxs-lookup"><span data-stu-id="4a67d-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="4a67d-471">Par exemple, choisissez `--langVersion 7.3` pour utiliser C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="4a67d-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="4a67d-472">Non pris en charge pour F#.</span><span class="sxs-lookup"><span data-stu-id="4a67d-472">Not supported for F#.</span></span>

<span data-ttu-id="4a67d-473">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-474">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="4a67d-474">**mstest, xunit**</span></span>

<span data-ttu-id="4a67d-475">`-p|--enable-pack` : permet l’empaquetage pour le projet à l’aide de [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="4a67d-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="4a67d-476">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="4a67d-477">**nunit**</span></span>

<span data-ttu-id="4a67d-478">`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="4a67d-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a67d-479">La valeur par défaut est `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="4a67d-480">`-p|--enable-pack` : permet l’empaquetage pour le projet à l’aide de [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="4a67d-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="4a67d-481">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-482">**page**</span><span class="sxs-lookup"><span data-stu-id="4a67d-482">**page**</span></span>

<span data-ttu-id="4a67d-483">`-na|--namespace <NAMESPACE_NAME>` - Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="4a67d-484">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="4a67d-485">`-np|--no-pagemodel` : crée la page sans modèle de page.</span><span class="sxs-lookup"><span data-stu-id="4a67d-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="4a67d-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="4a67d-486">**viewimports**</span></span>

<span data-ttu-id="4a67d-487">`-na|--namespace <NAMESPACE_NAME>` - Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="4a67d-488">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="4a67d-489">**web**</span><span class="sxs-lookup"><span data-stu-id="4a67d-489">**web**</span></span>

<span data-ttu-id="4a67d-490">`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a67d-491">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-492">`--no-https` - Le projet ne nécessite pas le protocole HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a67d-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a67d-493">Cette option s’applique uniquement si `IndividualAuth` ou `OrganizationalAuth` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="4a67d-494">**mvc, webapp**</span><span class="sxs-lookup"><span data-stu-id="4a67d-494">**mvc, webapp**</span></span>

<span data-ttu-id="4a67d-495">`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4a67d-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a67d-496">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="4a67d-496">The possible values are:</span></span>

- <span data-ttu-id="4a67d-497">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="4a67d-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a67d-498">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="4a67d-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="4a67d-499">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a67d-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a67d-500">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="4a67d-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a67d-501">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="4a67d-502">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="4a67d-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a67d-503">`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a67d-504">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-505">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a67d-506">`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a67d-507">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-508">`-rp|--reset-password-policy-id <ID>` : ID de stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="4a67d-509">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-510">`-ep|--edit-profile-policy-id <ID>` : ID de stratégie de modification du profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="4a67d-511">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-512">`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a67d-513">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a67d-514">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a67d-515">`--client-id <ID>` : ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a67d-516">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a67d-517">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a67d-518">`--domain <DOMAIN>` : domaine de l’abonné d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a67d-519">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-520">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a67d-521">`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a67d-522">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-523">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a67d-524">`--callback-path <PATH>` : chemin de demande dans le chemin de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="4a67d-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="4a67d-525">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-526">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="4a67d-527">`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a67d-528">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a67d-529">`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a67d-530">`--no-https` - Le projet ne nécessite pas le protocole HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a67d-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a67d-531">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="4a67d-532">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="4a67d-533">`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="4a67d-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a67d-534">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-535">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-536">**webapi**</span><span class="sxs-lookup"><span data-stu-id="4a67d-536">**webapi**</span></span>

<span data-ttu-id="4a67d-537">`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4a67d-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a67d-538">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="4a67d-538">The possible values are:</span></span>

- <span data-ttu-id="4a67d-539">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="4a67d-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a67d-540">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a67d-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a67d-541">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="4a67d-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a67d-542">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="4a67d-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a67d-543">`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a67d-544">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-545">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a67d-546">`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a67d-547">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-548">`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a67d-549">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-550">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a67d-551">`--client-id <ID>` : ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a67d-552">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-553">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a67d-554">`--domain <DOMAIN>` : domaine de l’abonné d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a67d-555">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-556">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a67d-557">`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a67d-558">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-559">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a67d-560">`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a67d-561">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a67d-562">`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a67d-563">`--no-https` - Le projet ne nécessite pas le protocole HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a67d-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a67d-564">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="4a67d-565">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="4a67d-566">`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="4a67d-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a67d-567">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-568">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="4a67d-569">**globaljson**</span></span>

<span data-ttu-id="4a67d-570">`--sdk-version <VERSION_NUMBER>` : spécifie la version du SDK .NET Core à utiliser dans le fichier *global.json*.</span><span class="sxs-lookup"><span data-stu-id="4a67d-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4a67d-571">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4a67d-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="4a67d-572">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="4a67d-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="4a67d-573">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="4a67d-574">**classlib**</span></span>

<span data-ttu-id="4a67d-575">`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="4a67d-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a67d-576">Valeurs : `netcoreapp2.1` pour créer une bibliothèque de classes .NET Core ou `netstandard2.0` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4a67d-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="4a67d-577">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="4a67d-578">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-579">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="4a67d-579">**mstest, xunit**</span></span>

<span data-ttu-id="4a67d-580">`-p|--enable-pack` : permet l’empaquetage pour le projet à l’aide de [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="4a67d-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="4a67d-581">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="4a67d-582">**globaljson**</span></span>

<span data-ttu-id="4a67d-583">`--sdk-version <VERSION_NUMBER>` : spécifie la version du SDK .NET Core à utiliser dans le fichier *global.json*.</span><span class="sxs-lookup"><span data-stu-id="4a67d-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="4a67d-584">**web**</span><span class="sxs-lookup"><span data-stu-id="4a67d-584">**web**</span></span>

<span data-ttu-id="4a67d-585">`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a67d-586">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-587">`--no-https` - Le projet ne nécessite pas le protocole HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a67d-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a67d-588">Cette option s’applique uniquement si `IndividualAuth` ou `OrganizationalAuth` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="4a67d-589">**webapi**</span><span class="sxs-lookup"><span data-stu-id="4a67d-589">**webapi**</span></span>

<span data-ttu-id="4a67d-590">`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4a67d-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a67d-591">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="4a67d-591">The possible values are:</span></span>

- <span data-ttu-id="4a67d-592">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="4a67d-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a67d-593">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a67d-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a67d-594">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="4a67d-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a67d-595">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="4a67d-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a67d-596">`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a67d-597">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-598">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a67d-599">`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a67d-600">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-601">`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a67d-602">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-603">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a67d-604">`--client-id <ID>` : ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a67d-605">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-606">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a67d-607">`--domain <DOMAIN>` : domaine de l’abonné d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a67d-608">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-609">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a67d-610">`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a67d-611">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-612">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a67d-613">`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a67d-614">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a67d-615">`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a67d-616">`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="4a67d-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a67d-617">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-618">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-619">`--no-https` - Le projet ne nécessite pas le protocole HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a67d-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a67d-620">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="4a67d-621">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="4a67d-622">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="4a67d-622">**mvc, razor**</span></span>

<span data-ttu-id="4a67d-623">`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4a67d-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a67d-624">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="4a67d-624">The possible values are:</span></span>

- <span data-ttu-id="4a67d-625">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="4a67d-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a67d-626">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="4a67d-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="4a67d-627">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a67d-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a67d-628">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="4a67d-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a67d-629">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="4a67d-630">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="4a67d-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a67d-631">`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a67d-632">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-633">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a67d-634">`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a67d-635">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-636">`-rp|--reset-password-policy-id <ID>` : ID de stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="4a67d-637">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-638">`-ep|--edit-profile-policy-id <ID>` : ID de stratégie de modification du profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="4a67d-639">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-640">`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a67d-641">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a67d-642">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a67d-643">`--client-id <ID>` : ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a67d-644">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a67d-645">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a67d-646">`--domain <DOMAIN>` : domaine de l’abonné d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a67d-647">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-648">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a67d-649">`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a67d-650">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-651">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a67d-652">`--callback-path <PATH>` : chemin de demande dans le chemin de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="4a67d-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="4a67d-653">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-654">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="4a67d-655">`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a67d-656">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a67d-657">`--exclude-launch-settings` - Exclure *launchSettings.json* du modèle généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a67d-658">`--use-browserlink` : inclut BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="4a67d-659">`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="4a67d-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a67d-660">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-661">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-662">`--no-https` - Le projet ne nécessite pas le protocole HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a67d-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a67d-663">`app.UseHsts` et `app.UseHttpsRedirection` ne sont pas ajoutés à `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="4a67d-664">Cette option s’applique uniquement si `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="4a67d-665">**page**</span><span class="sxs-lookup"><span data-stu-id="4a67d-665">**page**</span></span>

<span data-ttu-id="4a67d-666">`-na|--namespace <NAMESPACE_NAME>` - Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="4a67d-667">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="4a67d-668">`-np|--no-pagemodel` : crée la page sans modèle de page.</span><span class="sxs-lookup"><span data-stu-id="4a67d-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="4a67d-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="4a67d-669">**viewimports**</span></span>

<span data-ttu-id="4a67d-670">`-na|--namespace <NAMESPACE_NAME>` - Espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="4a67d-671">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4a67d-672">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4a67d-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="4a67d-673">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="4a67d-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="4a67d-674">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="4a67d-675">**classlib**</span></span>

<span data-ttu-id="4a67d-676">`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="4a67d-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a67d-677">Valeurs : `netcoreapp2.0` pour créer une bibliothèque de classes .NET Core ou `netstandard2.0` pour créer une bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4a67d-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="4a67d-678">La valeur par défaut est `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="4a67d-679">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-680">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="4a67d-680">**mstest, xunit**</span></span>

<span data-ttu-id="4a67d-681">`-p|--enable-pack` : permet l’empaquetage pour le projet à l’aide de [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="4a67d-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="4a67d-682">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="4a67d-683">**globaljson**</span></span>

<span data-ttu-id="4a67d-684">`--sdk-version <VERSION_NUMBER>` : spécifie la version du SDK .NET Core à utiliser dans le fichier *global.json*.</span><span class="sxs-lookup"><span data-stu-id="4a67d-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="4a67d-685">**web**</span><span class="sxs-lookup"><span data-stu-id="4a67d-685">**web**</span></span>

<span data-ttu-id="4a67d-686">`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4a67d-687">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-688">**webapi**</span><span class="sxs-lookup"><span data-stu-id="4a67d-688">**webapi**</span></span>

<span data-ttu-id="4a67d-689">`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4a67d-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a67d-690">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="4a67d-690">The possible values are:</span></span>

- <span data-ttu-id="4a67d-691">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="4a67d-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a67d-692">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a67d-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a67d-693">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="4a67d-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a67d-694">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="4a67d-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a67d-695">`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a67d-696">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-697">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a67d-698">`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a67d-699">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-700">`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a67d-701">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-702">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a67d-703">`--client-id <ID>` : ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a67d-704">À utiliser avec l’authentification `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-705">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a67d-706">`--domain <DOMAIN>` : domaine de l’abonné d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a67d-707">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-708">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a67d-709">`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a67d-710">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-711">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a67d-712">`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a67d-713">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a67d-714">`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4a67d-715">`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="4a67d-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a67d-716">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-717">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-718">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="4a67d-718">**mvc, razor**</span></span>

<span data-ttu-id="4a67d-719">`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4a67d-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a67d-720">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="4a67d-720">The possible values are:</span></span>

- <span data-ttu-id="4a67d-721">`None` : aucune authentification (configuration par défaut).</span><span class="sxs-lookup"><span data-stu-id="4a67d-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a67d-722">`Individual` : authentification individuelle.</span><span class="sxs-lookup"><span data-stu-id="4a67d-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="4a67d-723">`IndividualB2C` : authentification individuelle avec Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a67d-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a67d-724">`SingleOrg` : authentification d’organisation pour un seul abonné.</span><span class="sxs-lookup"><span data-stu-id="4a67d-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a67d-725">`MultiOrg` : authentification d’organisation pour plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="4a67d-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="4a67d-726">`Windows` : authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="4a67d-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a67d-727">`--aad-b2c-instance <INSTANCE>` : instance d’Azure Active Directory B2C à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a67d-728">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-729">La valeur par défaut est `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a67d-730">`-ssp|--susi-policy-id <ID>` : ID de la stratégie de connexion et d’inscription pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a67d-731">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-732">`-rp|--reset-password-policy-id <ID>` : ID de stratégie de réinitialisation du mot de passe pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="4a67d-733">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-734">`-ep|--edit-profile-policy-id <ID>` : ID de stratégie de modification du profil pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="4a67d-735">À utiliser avec l’authentification `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-736">`--aad-instance <INSTANCE>` : instance d’Azure Active Directory à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a67d-737">À utiliser avec l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a67d-738">La valeur par défaut est `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a67d-739">`--client-id <ID>` : ID client pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a67d-740">À utiliser avec l’authentification `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a67d-741">La valeur par défaut est `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a67d-742">`--domain <DOMAIN>` : domaine de l’abonné d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a67d-743">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-744">La valeur par défaut est `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a67d-745">`--tenant-id <ID>` : ID d’abonné de l’annuaire auquel se connecter.</span><span class="sxs-lookup"><span data-stu-id="4a67d-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a67d-746">À utiliser avec l’authentification `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a67d-747">La valeur par défaut est `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a67d-748">`--callback-path <PATH>` : chemin de demande dans le chemin de base de l’application de l’URI de redirection.</span><span class="sxs-lookup"><span data-stu-id="4a67d-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="4a67d-749">À utiliser avec l’authentification `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a67d-750">La valeur par défaut est `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="4a67d-751">`-r|--org-read-access` : accorde à cette application un accès en lecture au répertoire.</span><span class="sxs-lookup"><span data-stu-id="4a67d-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a67d-752">S’applique uniquement à l’authentification `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a67d-753">`--use-launch-settings` : inclut *launchSettings.json* dans la sortie de modèle générée.</span><span class="sxs-lookup"><span data-stu-id="4a67d-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4a67d-754">`--use-browserlink` : inclut BrowserLink dans le projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="4a67d-755">`-uld|--use-local-db` : spécifie que la base de données locale doit être utilisée à la place de SQLite.</span><span class="sxs-lookup"><span data-stu-id="4a67d-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a67d-756">S’applique uniquement à l’authentification `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a67d-757">`--no-restore` - N’exécute aucune restauration implicite pendant la création du projet.</span><span class="sxs-lookup"><span data-stu-id="4a67d-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a67d-758">**page**</span><span class="sxs-lookup"><span data-stu-id="4a67d-758">**page**</span></span>

<span data-ttu-id="4a67d-759">`-na|--namespace <NAMESPACE_NAME>` : espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="4a67d-760">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="4a67d-761">`-np|--no-pagemodel` : crée la page sans modèle de page.</span><span class="sxs-lookup"><span data-stu-id="4a67d-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="4a67d-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="4a67d-762">**viewimports**</span></span>

<span data-ttu-id="4a67d-763">`-na|--namespace <NAMESPACE_NAME>` : espace de noms pour le code généré.</span><span class="sxs-lookup"><span data-stu-id="4a67d-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="4a67d-764">La valeur par défaut est `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4a67d-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4a67d-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="4a67d-766">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="4a67d-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="4a67d-767">`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="4a67d-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a67d-768">Valeurs : `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="4a67d-769">La valeur par défaut est `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="4a67d-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="4a67d-770">**classlib**</span></span>

<span data-ttu-id="4a67d-771">`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="4a67d-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a67d-772">Valeurs : `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` à `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="4a67d-773">La valeur par défaut est `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="4a67d-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="4a67d-774">**mvc**</span></span>

<span data-ttu-id="4a67d-775">`-f|--framework <FRAMEWORK>` : spécifie le [framework](../../standard/frameworks.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="4a67d-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a67d-776">Valeurs : `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="4a67d-777">La valeur par défaut est `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="4a67d-778">`-au|--auth <AUTHENTICATION_TYPE>` : type d’authentification à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4a67d-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a67d-779">Valeurs : `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="4a67d-780">La valeur par défaut est `None`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-780">The default value is `None`.</span></span>

<span data-ttu-id="4a67d-781">`-uld|--use-local-db` : spécifie s’il convient ou non d’utiliser LocalDB au lieu de SQLite.</span><span class="sxs-lookup"><span data-stu-id="4a67d-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="4a67d-782">Valeurs : `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-782">Values: `true` or `false`.</span></span> <span data-ttu-id="4a67d-783">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="4a67d-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="4a67d-784">Exemples</span><span class="sxs-lookup"><span data-stu-id="4a67d-784">Examples</span></span>

<span data-ttu-id="4a67d-785">Créez un projet d’application console C# en spécifiant le nom du modèle :</span><span class="sxs-lookup"><span data-stu-id="4a67d-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="4a67d-786">Créez un projet d’application console F# dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="4a67d-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="4a67d-787">Créez un projet de bibliothèque de classes .NET Standard dans le répertoire spécifié (disponible uniquement avec le SDK .NET Core 2.0 ou ultérieur) :</span><span class="sxs-lookup"><span data-stu-id="4a67d-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="4a67d-788">Créez un projet ASP.NET Core C# MVC dans le répertoire actif sans authentification :</span><span class="sxs-lookup"><span data-stu-id="4a67d-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="4a67d-789">Créez un projet xUnit :</span><span class="sxs-lookup"><span data-stu-id="4a67d-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="4a67d-790">Répertoriez tous les modèles disponibles pour MVC :</span><span class="sxs-lookup"><span data-stu-id="4a67d-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="4a67d-791">Liste de tous les modèles correspondant à la sous-chaîne *we*.</span><span class="sxs-lookup"><span data-stu-id="4a67d-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="4a67d-792">Aucune correspondance exacte n’a été trouvée, donc la recherche de sous-chaîne est exécutée sur les colonnes Nom court et Nom.</span><span class="sxs-lookup"><span data-stu-id="4a67d-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="4a67d-793">Tentative d’appel du modèle correspondant à *ng*.</span><span class="sxs-lookup"><span data-stu-id="4a67d-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="4a67d-794">Si aucune correspondance exacte n’est trouvée, listez les modèles qui correspondent partiellement.</span><span class="sxs-lookup"><span data-stu-id="4a67d-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="4a67d-795">Installez la version 2.0 des modèles d’application monopage pour ASP.NET Core (option de commande disponible pour .NET Core  SDK 1.1 et versions ultérieures uniquement) :</span><span class="sxs-lookup"><span data-stu-id="4a67d-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="4a67d-796">Créez un fichier *global.json* dans le répertoire actif en définissant la version du SDK sur 2.0.0 (disponible uniquement avec le SDK .NET Core 2.0 ou ultérieure) :</span><span class="sxs-lookup"><span data-stu-id="4a67d-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="4a67d-797">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a67d-797">See also</span></span>

- [<span data-ttu-id="4a67d-798">Modèles personnalisés pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="4a67d-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="4a67d-799">Créer un modèle personnalisé pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="4a67d-799">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)
- [<span data-ttu-id="4a67d-800">Dépôt GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="4a67d-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="4a67d-801">Modèles disponibles pour dotnet new</span><span class="sxs-lookup"><span data-stu-id="4a67d-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
