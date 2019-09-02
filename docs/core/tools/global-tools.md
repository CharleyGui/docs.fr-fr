---
title: Outils globaux .NET Core
description: Vue d’ensemble des outils globaux .NET Core et des commandes CLI .NET Core disponibles pour eux.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 9ff7e33a50eb0c5fb649b44dda6d72412a134584
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202590"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="a9a65-103">Vue d’ensemble des outils globaux .NET Core</span><span class="sxs-lookup"><span data-stu-id="a9a65-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="a9a65-104">Un outil global .NET Core est un package NuGet spécial qui contient une application console.</span><span class="sxs-lookup"><span data-stu-id="a9a65-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="a9a65-105">Vous pouvez installer un outil global sur votre machine à un emplacement par défaut inclus dans la variable d’environnement PATH ou à un emplacement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a9a65-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="a9a65-106">Pour utiliser un outil global .NET Core :</span><span class="sxs-lookup"><span data-stu-id="a9a65-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="a9a65-107">Recherchez des informations sur l’outil (généralement un site web ou une page GitHub).</span><span class="sxs-lookup"><span data-stu-id="a9a65-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="a9a65-108">Vérifiez l’auteur et les statistiques dans la page d’accueil du flux (généralement NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="a9a65-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="a9a65-109">Installez l’outil.</span><span class="sxs-lookup"><span data-stu-id="a9a65-109">Install the tool.</span></span>
* <span data-ttu-id="a9a65-110">Appelez l’outil.</span><span class="sxs-lookup"><span data-stu-id="a9a65-110">Call the tool.</span></span>
* <span data-ttu-id="a9a65-111">Mettez à jour l’outil.</span><span class="sxs-lookup"><span data-stu-id="a9a65-111">Update the tool.</span></span>
* <span data-ttu-id="a9a65-112">Désinstallez l’outil.</span><span class="sxs-lookup"><span data-stu-id="a9a65-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9a65-113">Les outils globaux .NET Core apparaissent dans votre chemin et s’exécutent en mode de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="a9a65-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="a9a65-114">N’installez pas les outils globaux .NET Core si vous ne faites pas confiance à l’auteur.</span><span class="sxs-lookup"><span data-stu-id="a9a65-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="a9a65-115">Rechercher un outil global .NET Core</span><span class="sxs-lookup"><span data-stu-id="a9a65-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="a9a65-116">Actuellement, l’interface de ligne de commande (CLI) .NET Core ne comprend pas de fonctionnalité de recherche d’outil global.</span><span class="sxs-lookup"><span data-stu-id="a9a65-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="a9a65-117">Vous trouverez des outils globaux .NET Core sur [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="a9a65-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="a9a65-118">Toutefois, NuGet ne vous permet pas encore de rechercher spécifiquement des outils globaux .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9a65-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="a9a65-119">Vous pouvez également trouver des suggestions d’outils dans les billets de blog ou dans le dépôt GitHub [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools).</span><span class="sxs-lookup"><span data-stu-id="a9a65-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="a9a65-120">Vous pouvez également voir le code source des outils globaux créés par l’équipe ASP.NET dans le dépôt GitHub [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/).</span><span class="sxs-lookup"><span data-stu-id="a9a65-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="a9a65-121">Vérifier l’auteur et les statistiques</span><span class="sxs-lookup"><span data-stu-id="a9a65-121">Check the author and statistics</span></span>

<span data-ttu-id="a9a65-122">Étant donné que les outils globaux .NET Core s’exécutent en mode de confiance totale et qu’ils sont généralement installés dans votre chemin, ils peuvent être très puissants.</span><span class="sxs-lookup"><span data-stu-id="a9a65-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="a9a65-123">Par conséquent, ne téléchargez pas d’outils provenant de personnes en qui vous n’avez pas confiance.</span><span class="sxs-lookup"><span data-stu-id="a9a65-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="a9a65-124">Si l’outil est hébergé sur NuGet, vous pouvez vérifier l’auteur et les statistiques en recherchant l’outil.</span><span class="sxs-lookup"><span data-stu-id="a9a65-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="a9a65-125">Installer un outil global</span><span class="sxs-lookup"><span data-stu-id="a9a65-125">Install a Global Tool</span></span>

<span data-ttu-id="a9a65-126">Pour installer un outil global, utilisez la commande CLI .NET Core [dotnet tool install](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="a9a65-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="a9a65-127">L’exemple suivant montre comment installer un outil global à l’emplacement par défaut :</span><span class="sxs-lookup"><span data-stu-id="a9a65-127">The following example shows how to install a Global Tool in the default location:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="a9a65-128">Si l’outil ne peut pas être installé, des messages d’erreur s’affichent.</span><span class="sxs-lookup"><span data-stu-id="a9a65-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="a9a65-129">Assurez-vous que les flux attendus sont vérifiés.</span><span class="sxs-lookup"><span data-stu-id="a9a65-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="a9a65-130">Si vous essayez d’installer une préversion ou une version spécifique de l’outil, vous pouvez spécifier le numéro de version au format suivant :</span><span class="sxs-lookup"><span data-stu-id="a9a65-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="a9a65-131">Si l’installation réussit, un message s’affiche indiquant la commande utilisée pour appeler l’outil et la version installée, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a9a65-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="a9a65-132">Il est possible d’installer des outils globaux dans le répertoire par défaut ou à un emplacement spécifique.</span><span class="sxs-lookup"><span data-stu-id="a9a65-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="a9a65-133">Les répertoires par défaut sont :</span><span class="sxs-lookup"><span data-stu-id="a9a65-133">The default directories are:</span></span>

| <span data-ttu-id="a9a65-134">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="a9a65-134">OS</span></span>          | <span data-ttu-id="a9a65-135">Chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="a9a65-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="a9a65-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="a9a65-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="a9a65-137">Windows</span><span class="sxs-lookup"><span data-stu-id="a9a65-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="a9a65-138">Ces emplacements sont ajoutés au chemin de l’utilisateur lors de la première exécution du SDK, si bien que les outils globaux qui y sont installés peuvent être appelées directement.</span><span class="sxs-lookup"><span data-stu-id="a9a65-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="a9a65-139">Notez que les outils globaux sont propres à l’utilisateur, et non globaux pour la machine.</span><span class="sxs-lookup"><span data-stu-id="a9a65-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="a9a65-140">Le fait d’être propre à l’utilisateur signifie que vous ne pouvez pas installer un outil global disponible pour tous les utilisateurs de la machine.</span><span class="sxs-lookup"><span data-stu-id="a9a65-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="a9a65-141">L’outil est uniquement disponible pour chaque profil utilisateur dans lequel l’outil a été installé.</span><span class="sxs-lookup"><span data-stu-id="a9a65-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="a9a65-142">Les outils globaux peuvent également être installés dans un répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="a9a65-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="a9a65-143">Lors d’une installation dans un répertoire spécifique, l’utilisateur doit vérifier que la commande est disponible, en incluant ce répertoire dans le chemin, en appelant la commande avec le répertoire spécifié, ou en appelant l’outil à partir du répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="a9a65-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="a9a65-144">Dans ce cas, CLI .NET Core n’ajoute pas automatiquement cet emplacement à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="a9a65-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="a9a65-145">Utiliser l’outil</span><span class="sxs-lookup"><span data-stu-id="a9a65-145">Use the tool</span></span>

<span data-ttu-id="a9a65-146">Une fois que l’outil est installé, vous pouvez l’appeler à l’aide de sa commande.</span><span class="sxs-lookup"><span data-stu-id="a9a65-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="a9a65-147">Notez que la commande peut ne pas être identique au nom du package.</span><span class="sxs-lookup"><span data-stu-id="a9a65-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="a9a65-148">Si la commande est `dotnetsay`, vous l’appelez avec :</span><span class="sxs-lookup"><span data-stu-id="a9a65-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="a9a65-149">Si l’auteur de l’outil voulait que l’outil apparaisse dans le contexte de l’invite `dotnet`, il peut l’avoir écrit de façon à ce que vous l’appeliez en utilisant `dotnet <command>`, par exemple :</span><span class="sxs-lookup"><span data-stu-id="a9a65-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```console
dotnet doc
```

<span data-ttu-id="a9a65-150">Vous pouvez déterminer quels outils sont inclus dans un package d’outils globaux installé en répertoriant les packages installés à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="a9a65-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="a9a65-151">Vous pouvez également rechercher des instructions d’utilisation sur le site web de l’outil ou en tapant l’une des commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a9a65-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="a9a65-152">Problèmes potentiels</span><span class="sxs-lookup"><span data-stu-id="a9a65-152">What could go wrong</span></span>

<span data-ttu-id="a9a65-153">Les outils globaux sont des [applications dépendant du framework](../deploying/index.md#framework-dependent-deployments-fdd), ce qui signifie qu’ils reposent sur un runtime .NET Core installé sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="a9a65-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="a9a65-154">Si le runtime attendu est introuvable, ils suivent les règles normales de restauration par progression du runtime .NET Core, à savoir :</span><span class="sxs-lookup"><span data-stu-id="a9a65-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="a9a65-155">Une application restaure par progression le correctif le plus élevé de la version principale et secondaire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a9a65-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="a9a65-156">En l’absence de runtime correspondant à un numéro de version principale et secondaire, la version secondaire supérieure suivante est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a9a65-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="a9a65-157">Une restauration par progression ne se produit pas entre des préversions du runtime ou entre des préversions et des versions finales.</span><span class="sxs-lookup"><span data-stu-id="a9a65-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="a9a65-158">C’est pourquoi les outils globaux créés à l’aide de préversions doivent être regénérés et republiés par l’auteur, puis réinstallés.</span><span class="sxs-lookup"><span data-stu-id="a9a65-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="a9a65-159">D’autres problèmes peuvent se produire avec les outils globaux créés dans .NET Core 2.1 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="a9a65-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="a9a65-160">Pour plus d’informations, consultez [Problèmes connus de .NET Core 2.1 Preview 2](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="a9a65-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="a9a65-161">Si une application ne trouve pas un runtime approprié, elle ne parvient pas à s’exécuter et signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="a9a65-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="a9a65-162">Un autre problème susceptible de se produire vient du fait qu’un outil global créé pendant une préversion antérieure risque de ne pas s’exécuter avec vos runtimes .NET Core actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="a9a65-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="a9a65-163">Vous pouvez voir quels runtimes sont installés sur votre machine à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a9a65-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```console
dotnet --list-runtimes
```

<span data-ttu-id="a9a65-164">Contactez l’auteur de l’outil global pour voir s’il peut recompiler et republier son package d’outils sur NuGet avec un numéro de version mis à jour.</span><span class="sxs-lookup"><span data-stu-id="a9a65-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="a9a65-165">Une fois la mise à jour du package effectuée sur NuGet, vous pouvez mettre à jour votre copie.</span><span class="sxs-lookup"><span data-stu-id="a9a65-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="a9a65-166">CLI .NET Core essaie d’ajouter les emplacements par défaut à la variable d’environnement PATH lors de sa première utilisation.</span><span class="sxs-lookup"><span data-stu-id="a9a65-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="a9a65-167">Toutefois, dans certains cas, il n’est pas possible d’ajouter automatiquement l’emplacement à PATH, notamment :</span><span class="sxs-lookup"><span data-stu-id="a9a65-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="a9a65-168">Si vous avez défini la variable d’environnement `DOTNET_SKIP_FIRST_TIME_EXPERIENCE`.</span><span class="sxs-lookup"><span data-stu-id="a9a65-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="a9a65-169">Sur macOS, si vous avez installé le SDK .NET Core à l’aide de fichiers *.tar.gz* et non *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="a9a65-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="a9a65-170">Sur Linux, vous devez modifier le fichier d’environnement d’interpréteur de commandes pour configurer PATH.</span><span class="sxs-lookup"><span data-stu-id="a9a65-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="a9a65-171">Autres commandes CLI</span><span class="sxs-lookup"><span data-stu-id="a9a65-171">Other CLI commands</span></span>

<span data-ttu-id="a9a65-172">Le SDK .NET Core contient d’autres commandes qui prennent en charge des outils globaux .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9a65-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="a9a65-173">Utilisez l’une des commandes `dotnet tool` avec l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="a9a65-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="a9a65-174">`--global` ou `-g` spécifient que la commande s’applique aux outils globaux à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a9a65-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="a9a65-175">`--tool-path` spécifie un emplacement personnalisé pour les outils globaux.</span><span class="sxs-lookup"><span data-stu-id="a9a65-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="a9a65-176">Pour déterminer les commandes disponibles pour les outils globaux :</span><span class="sxs-lookup"><span data-stu-id="a9a65-176">To find out which commands are available for Global Tools:</span></span>

```console
dotnet tool --help
```

<span data-ttu-id="a9a65-177">La mise à jour d’un outil global implique de le désinstaller puis de le réinstaller avec la dernière version stable.</span><span class="sxs-lookup"><span data-stu-id="a9a65-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="a9a65-178">Pour mettre à jour un outil global, utilisez la commande [dotnet tool update](dotnet-tool-update.md) :</span><span class="sxs-lookup"><span data-stu-id="a9a65-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```console
dotnet tool update -g <packagename>
```

<span data-ttu-id="a9a65-179">Supprimez un outil global avec [dotnet tool uninstall](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="a9a65-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```console
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="a9a65-180">Pour afficher tous les outils globaux actuellement installés sur la machine, ainsi que leur version et leurs commandes, utilisez la commande [dotnet tool list](dotnet-tool-list.md) :</span><span class="sxs-lookup"><span data-stu-id="a9a65-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```console
dotnet tool list -g
```
