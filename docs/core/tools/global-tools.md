---
title: Outils globaux .NET Core
description: Vue d’ensemble des outils globaux .NET Core et des commandes CLI .NET Core disponibles pour eux.
author: KathleenDollard
ms.date: 05/29/2018
ms.openlocfilehash: 1531df48b7ca9c816b897d06e725ec375f6cae31
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920489"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="1510f-103">Vue d’ensemble des outils globaux .NET Core</span><span class="sxs-lookup"><span data-stu-id="1510f-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="1510f-104">Un outil global .NET Core est un package NuGet spécial qui contient une application console.</span><span class="sxs-lookup"><span data-stu-id="1510f-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="1510f-105">Vous pouvez installer un outil global sur votre machine à un emplacement par défaut inclus dans la variable d’environnement PATH ou à un emplacement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1510f-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="1510f-106">Pour utiliser un outil global .NET Core :</span><span class="sxs-lookup"><span data-stu-id="1510f-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="1510f-107">Recherchez des informations sur l’outil (généralement un site web ou une page GitHub).</span><span class="sxs-lookup"><span data-stu-id="1510f-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="1510f-108">Vérifiez l’auteur et les statistiques dans la page d’accueil du flux (généralement NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="1510f-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="1510f-109">Installez l’outil.</span><span class="sxs-lookup"><span data-stu-id="1510f-109">Install the tool.</span></span>
* <span data-ttu-id="1510f-110">Appelez l’outil.</span><span class="sxs-lookup"><span data-stu-id="1510f-110">Call the tool.</span></span>
* <span data-ttu-id="1510f-111">Mettez à jour l’outil.</span><span class="sxs-lookup"><span data-stu-id="1510f-111">Update the tool.</span></span>
* <span data-ttu-id="1510f-112">Désinstallez l’outil.</span><span class="sxs-lookup"><span data-stu-id="1510f-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1510f-113">Les outils globaux .NET Core apparaissent dans votre chemin et s’exécutent en mode de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="1510f-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="1510f-114">N’installez pas les outils globaux .NET Core si vous ne faites pas confiance à l’auteur.</span><span class="sxs-lookup"><span data-stu-id="1510f-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="1510f-115">Rechercher un outil global .NET Core</span><span class="sxs-lookup"><span data-stu-id="1510f-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="1510f-116">Actuellement, il n’existe pas de fonctionnalité de recherche d’outils globale dans le CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1510f-116">Currently, there isn't a Global Tool search feature in the .NET Core CLI.</span></span> <span data-ttu-id="1510f-117">Voici quelques recommandations sur la façon de trouver des outils :</span><span class="sxs-lookup"><span data-stu-id="1510f-117">The following are some recommendations on how to find tools:</span></span>

* <span data-ttu-id="1510f-118">Vous trouverez des outils globaux .NET Core sur [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="1510f-118">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="1510f-119">Toutefois, NuGet ne vous permet pas encore de rechercher spécifiquement des outils globaux .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1510f-119">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>
* <span data-ttu-id="1510f-120">Vous pouvez trouver des recommandations d’outils dans les billets de blog ou dans le référentiel GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .</span><span class="sxs-lookup"><span data-stu-id="1510f-120">You may find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="1510f-121">Vous pouvez voir le code source des outils globaux créés par l’équipe ASP.NET dans le référentiel GitHub [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools) .</span><span class="sxs-lookup"><span data-stu-id="1510f-121">You can see the source code for the Global Tools created by the ASP.NET team at the [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools) GitHub repository.</span></span>
* <span data-ttu-id="1510f-122">Pour en savoir plus sur les outils de diagnostic, consultez [Outils globaux de diagnostic dotnet .net Core](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span><span class="sxs-lookup"><span data-stu-id="1510f-122">You can learn about diagnostic tools at [.NET Core dotnet diagnostic Global Tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="1510f-123">Vérifier l’auteur et les statistiques</span><span class="sxs-lookup"><span data-stu-id="1510f-123">Check the author and statistics</span></span>

<span data-ttu-id="1510f-124">Étant donné que les outils globaux .NET Core s’exécutent en mode de confiance totale et qu’ils sont généralement installés dans votre chemin, ils peuvent être très puissants.</span><span class="sxs-lookup"><span data-stu-id="1510f-124">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="1510f-125">Par conséquent, ne téléchargez pas d’outils provenant de personnes en qui vous n’avez pas confiance.</span><span class="sxs-lookup"><span data-stu-id="1510f-125">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="1510f-126">Si l’outil est hébergé sur NuGet, vous pouvez vérifier l’auteur et les statistiques en recherchant l’outil.</span><span class="sxs-lookup"><span data-stu-id="1510f-126">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="1510f-127">Installer un outil global</span><span class="sxs-lookup"><span data-stu-id="1510f-127">Install a Global Tool</span></span>

<span data-ttu-id="1510f-128">Pour installer un outil global, utilisez la commande CLI .NET Core [dotnet tool install](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="1510f-128">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="1510f-129">L’exemple suivant montre comment installer un outil global à l’emplacement par défaut :</span><span class="sxs-lookup"><span data-stu-id="1510f-129">The following example shows how to install a Global Tool in the default location:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="1510f-130">Si l’outil ne peut pas être installé, des messages d’erreur s’affichent.</span><span class="sxs-lookup"><span data-stu-id="1510f-130">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="1510f-131">Assurez-vous que les flux attendus sont vérifiés.</span><span class="sxs-lookup"><span data-stu-id="1510f-131">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="1510f-132">Si vous essayez d’installer une préversion ou une version spécifique de l’outil, vous pouvez spécifier le numéro de version au format suivant :</span><span class="sxs-lookup"><span data-stu-id="1510f-132">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="1510f-133">Si l’installation réussit, un message s’affiche indiquant la commande utilisée pour appeler l’outil et la version installée, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1510f-133">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="1510f-134">Il est possible d’installer des outils globaux dans le répertoire par défaut ou à un emplacement spécifique.</span><span class="sxs-lookup"><span data-stu-id="1510f-134">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="1510f-135">Les répertoires par défaut sont :</span><span class="sxs-lookup"><span data-stu-id="1510f-135">The default directories are:</span></span>

| <span data-ttu-id="1510f-136">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="1510f-136">OS</span></span>          | <span data-ttu-id="1510f-137">Path</span><span class="sxs-lookup"><span data-stu-id="1510f-137">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="1510f-138">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="1510f-138">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="1510f-139">Portail</span><span class="sxs-lookup"><span data-stu-id="1510f-139">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="1510f-140">Ces emplacements sont ajoutés au chemin de l’utilisateur lors de la première exécution du SDK, si bien que les outils globaux qui y sont installés peuvent être appelées directement.</span><span class="sxs-lookup"><span data-stu-id="1510f-140">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="1510f-141">Notez que les outils globaux sont propres à l’utilisateur, et non globaux pour la machine.</span><span class="sxs-lookup"><span data-stu-id="1510f-141">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="1510f-142">Le fait d’être propre à l’utilisateur signifie que vous ne pouvez pas installer un outil global disponible pour tous les utilisateurs de la machine.</span><span class="sxs-lookup"><span data-stu-id="1510f-142">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="1510f-143">L’outil est uniquement disponible pour chaque profil utilisateur dans lequel l’outil a été installé.</span><span class="sxs-lookup"><span data-stu-id="1510f-143">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="1510f-144">Les outils globaux peuvent également être installés dans un répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="1510f-144">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="1510f-145">Lors d’une installation dans un répertoire spécifique, l’utilisateur doit vérifier que la commande est disponible, en incluant ce répertoire dans le chemin, en appelant la commande avec le répertoire spécifié, ou en appelant l’outil à partir du répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="1510f-145">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="1510f-146">Dans ce cas, CLI .NET Core n’ajoute pas automatiquement cet emplacement à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="1510f-146">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="1510f-147">Utiliser l’outil</span><span class="sxs-lookup"><span data-stu-id="1510f-147">Use the tool</span></span>

<span data-ttu-id="1510f-148">Une fois que l’outil est installé, vous pouvez l’appeler à l’aide de sa commande.</span><span class="sxs-lookup"><span data-stu-id="1510f-148">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="1510f-149">Notez que la commande peut ne pas être identique au nom du package.</span><span class="sxs-lookup"><span data-stu-id="1510f-149">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="1510f-150">Si la commande est `dotnetsay`, vous l’appelez avec :</span><span class="sxs-lookup"><span data-stu-id="1510f-150">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="1510f-151">Si l’auteur de l’outil voulait que l’outil apparaisse dans le contexte de l’invite `dotnet`, il peut l’avoir écrit de façon à ce que vous l’appeliez en utilisant `dotnet <command>`, par exemple :</span><span class="sxs-lookup"><span data-stu-id="1510f-151">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="1510f-152">Vous pouvez déterminer quels outils sont inclus dans un package d’outils globaux installé en répertoriant les packages installés à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="1510f-152">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="1510f-153">Vous pouvez également rechercher des instructions d’utilisation sur le site web de l’outil ou en tapant l’une des commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="1510f-153">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a><span data-ttu-id="1510f-154">Autres commandes CLI</span><span class="sxs-lookup"><span data-stu-id="1510f-154">Other CLI commands</span></span>

<span data-ttu-id="1510f-155">Le SDK .NET Core contient d’autres commandes qui prennent en charge des outils globaux .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1510f-155">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="1510f-156">Utilisez l’une des commandes `dotnet tool` avec l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="1510f-156">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="1510f-157">`--global` ou `-g` spécifient que la commande s’applique aux outils globaux à l’échelle de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1510f-157">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="1510f-158">`--tool-path` spécifie un emplacement personnalisé pour les outils globaux.</span><span class="sxs-lookup"><span data-stu-id="1510f-158">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="1510f-159">Pour déterminer les commandes disponibles pour les outils globaux :</span><span class="sxs-lookup"><span data-stu-id="1510f-159">To find out which commands are available for Global Tools:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="1510f-160">La mise à jour d’un outil global implique de le désinstaller puis de le réinstaller avec la dernière version stable.</span><span class="sxs-lookup"><span data-stu-id="1510f-160">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="1510f-161">Pour mettre à jour un outil global, utilisez la commande [dotnet tool update](dotnet-tool-update.md) :</span><span class="sxs-lookup"><span data-stu-id="1510f-161">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```dotnetcli
dotnet tool update -g <packagename>
```

<span data-ttu-id="1510f-162">Supprimez un outil global avec [dotnet tool uninstall](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="1510f-162">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```dotnetcli
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="1510f-163">Pour afficher tous les outils globaux actuellement installés sur la machine, ainsi que leur version et leurs commandes, utilisez la commande [dotnet tool list](dotnet-tool-list.md) :</span><span class="sxs-lookup"><span data-stu-id="1510f-163">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a><span data-ttu-id="1510f-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1510f-164">See also</span></span>

* [<span data-ttu-id="1510f-165">Résoudre les problèmes d’utilisation de l’outil .NET Core</span><span class="sxs-lookup"><span data-stu-id="1510f-165">Troubleshoot .NET Core tool usage issues</span></span>](troubleshoot-usage-issues.md)
