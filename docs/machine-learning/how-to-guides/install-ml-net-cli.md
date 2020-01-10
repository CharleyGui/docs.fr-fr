---
title: Guide pratique pour installer l’outil CLI ML.NET
description: Découvrez comment installer, mettre à niveau, rétrograder et désinstaller l’outil d’interface de ligne de commande (CLI) ML.NET.
ms.date: 12/18/2019
ms.openlocfilehash: 350122f2d2d2f03484ab6e272b482adf2094495c
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739963"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="8cf90-103">Guide pratique pour installer l’outil CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="8cf90-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="8cf90-104">Découvrez comment installer l’interface de ligne de commande (CLI) ML.NET sur Windows, Mac ou Linux.</span><span class="sxs-lookup"><span data-stu-id="8cf90-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="8cf90-105">L’interface CLI ML.NET génère des modèles de ML.NET de qualité et du code source corrects à l’aide d’une Machine Learning automatisée (AutoML) et d’un jeu de données d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="8cf90-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="8cf90-106">Cette rubrique fait référence à l’interface CLI ML.NET et au moteur AutoML ML.NET, actuellement en préversion. Les ressources sont donc susceptibles d’être changées.</span><span class="sxs-lookup"><span data-stu-id="8cf90-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="8cf90-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8cf90-107">Pre-requisites</span></span>

- [<span data-ttu-id="8cf90-108">SDK .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="8cf90-108">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="8cf90-109">(Facultatif) [Visual Studio 2017 ou 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="8cf90-109">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="8cf90-110">Vous pouvez exécuter les projets C# de code générés avec Visual Studio en appuyant sur la touche `F5` ou `dotnet run` (CLI .net Core).</span><span class="sxs-lookup"><span data-stu-id="8cf90-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="8cf90-111">Remarque : si, après l’installation du [Kit de développement logiciel (SDK) .net Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) , la commande `dotnet tool` ne fonctionne pas, déconnectez-vous de Windows, puis reconnectez-vous.</span><span class="sxs-lookup"><span data-stu-id="8cf90-111">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="8cf90-112">Installez .</span><span class="sxs-lookup"><span data-stu-id="8cf90-112">Install</span></span>

<span data-ttu-id="8cf90-113">L’interface CLI ML.NET est installée comme tout autre outil global dotnet.</span><span class="sxs-lookup"><span data-stu-id="8cf90-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="8cf90-114">Vous utilisez la commande CLI .NET Core `dotnet tool install`.</span><span class="sxs-lookup"><span data-stu-id="8cf90-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="8cf90-115">L’exemple suivant montre comment installer la CLI ML.NET à l’emplacement du flux NuGet par défaut :</span><span class="sxs-lookup"><span data-stu-id="8cf90-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="8cf90-116">Si l’outil ne peut pas être installé (autrement dit, s’il n’est pas disponible dans le flux NuGet par défaut), des messages d’erreur sont affichés.</span><span class="sxs-lookup"><span data-stu-id="8cf90-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="8cf90-117">Assurez-vous que les flux attendus sont vérifiés.</span><span class="sxs-lookup"><span data-stu-id="8cf90-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="8cf90-118">Si l’installation réussit, un message s’affiche indiquant la commande utilisée pour appeler l’outil et la version installée, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8cf90-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="8cf90-119">Vous pouvez vérifier que l’installation a réussi en tapant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8cf90-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="8cf90-120">Vous devez voir l’aide des commandes disponibles pour l’outil mlnet, telles que la commande « auto-train ».</span><span class="sxs-lookup"><span data-stu-id="8cf90-120">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="8cf90-121">Installer une version spécifique</span><span class="sxs-lookup"><span data-stu-id="8cf90-121">Install a specific release version</span></span>

<span data-ttu-id="8cf90-122">Si vous essayez d’installer une version préliminaire ou une version spécifique de l’outil, vous pouvez spécifier [l’infrastructure](../../standard/frameworks.md) au format suivant :</span><span class="sxs-lookup"><span data-stu-id="8cf90-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="8cf90-123">Vous pouvez également vérifier si le package est correctement installé en tapant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8cf90-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="8cf90-124">Désinstaller le package de la CLI</span><span class="sxs-lookup"><span data-stu-id="8cf90-124">Uninstall the CLI package</span></span>

<span data-ttu-id="8cf90-125">Tapez la commande suivante pour désinstaller le package de votre ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="8cf90-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="8cf90-126">Mettre à jour le package de la CLI</span><span class="sxs-lookup"><span data-stu-id="8cf90-126">Update the CLI package</span></span>

<span data-ttu-id="8cf90-127">Tapez la commande suivante pour mettre à jour le package sur votre ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="8cf90-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="8cf90-128">Configurer des suggestions pour la CLI (autocomplétion avec la touche Tab)</span><span class="sxs-lookup"><span data-stu-id="8cf90-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="8cf90-129">Étant donné que l’interface CLI ML.NET repose sur `System.CommandLine`, elle prend en charge l’autocomplétion à l’aide de la touche Tab.</span><span class="sxs-lookup"><span data-stu-id="8cf90-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="8cf90-130">L’animation suivante illustre le fonctionnement de l’autocomplétion à l’aide de la touche Tab :</span><span class="sxs-lookup"><span data-stu-id="8cf90-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![image](./media/cli-tab-completion.gif)

<span data-ttu-id="8cf90-132">L’autocomplétion à l’aide de la touche Tab (suggestions de paramètre) fonctionne sur *Windows PowerShell* et *macOS/Linux bash*, mais pas sur *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="8cf90-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="8cf90-133">Pour l’activer, dans la préversion actuelle, l’utilisateur final doit effectuer quelques étapes une fois par interpréteur de commandes, décrites ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="8cf90-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="8cf90-134">Une fois ces étapes effectuées, les complétions fonctionnent pour toutes les applications écrites à l’aide de `System.CommandLine` telles que l’interface CLI ML.NET.</span><span class="sxs-lookup"><span data-stu-id="8cf90-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="8cf90-135">Sur la machine où vous souhaitez activer la complétion, vous devez faire deux choses.</span><span class="sxs-lookup"><span data-stu-id="8cf90-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="8cf90-136">Installez l’outil global `dotnet-suggest` en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8cf90-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="8cf90-137">Ajoutez le script shim approprié au profil de votre interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="8cf90-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="8cf90-138">Vous devrez peut-être créer un fichier de profil d’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="8cf90-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="8cf90-139">Le script shim transfère les demandes de complétion depuis votre interpréteur de commandes vers l’outil `dotnet-suggest`, qui délègue à l’application basée sur `System.CommandLine` appropriée.</span><span class="sxs-lookup"><span data-stu-id="8cf90-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="8cf90-140">Pour bash, ajoutez le contenu de [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) à `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="8cf90-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="8cf90-141">Pour PowerShell, ajoutez le contenu de [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8cf90-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="8cf90-142">Vous pouvez trouver le chemin attendu de votre profil PowerShell en exécutant la commande suivante dans votre console :</span><span class="sxs-lookup"><span data-stu-id="8cf90-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="8cf90-143">(Pour les autres interpréteurs de commandes, [recherchez](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) ou ouvrez un [problème](https://github.com/dotnet/System.CommandLine/issues).)</span><span class="sxs-lookup"><span data-stu-id="8cf90-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="8cf90-144">Répertoire d'installation</span><span class="sxs-lookup"><span data-stu-id="8cf90-144">Installation directory</span></span>

<span data-ttu-id="8cf90-145">Il est possible d’installer la CLI ML.NET dans le répertoire par défaut ou à un emplacement spécifique.</span><span class="sxs-lookup"><span data-stu-id="8cf90-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="8cf90-146">Les répertoires par défaut sont :</span><span class="sxs-lookup"><span data-stu-id="8cf90-146">The default directories are:</span></span>

| <span data-ttu-id="8cf90-147">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="8cf90-147">OS</span></span>          | <span data-ttu-id="8cf90-148">Path</span><span class="sxs-lookup"><span data-stu-id="8cf90-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="8cf90-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="8cf90-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="8cf90-150">Portail</span><span class="sxs-lookup"><span data-stu-id="8cf90-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="8cf90-151">Ces emplacements sont ajoutés au chemin de l’utilisateur lors de la première exécution du SDK, si bien que les outils globaux qui y sont installés peuvent être appelées directement.</span><span class="sxs-lookup"><span data-stu-id="8cf90-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="8cf90-152">Remarque : Les outils globaux sont propres à l’utilisateur, et non globaux pour la machine.</span><span class="sxs-lookup"><span data-stu-id="8cf90-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="8cf90-153">Le fait d’être propre à l’utilisateur signifie que vous ne pouvez pas installer un outil global disponible pour tous les utilisateurs de la machine.</span><span class="sxs-lookup"><span data-stu-id="8cf90-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="8cf90-154">L’outil est uniquement disponible pour chaque profil utilisateur dans lequel l’outil a été installé.</span><span class="sxs-lookup"><span data-stu-id="8cf90-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="8cf90-155">Les outils globaux peuvent également être installés dans un répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="8cf90-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="8cf90-156">Lors d’une installation dans un répertoire spécifique, l’utilisateur doit vérifier que la commande est disponible, en incluant ce répertoire dans le chemin, en appelant la commande avec le répertoire spécifié, ou en appelant l’outil à partir du répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="8cf90-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="8cf90-157">Dans ce cas, CLI .NET Core n’ajoute pas automatiquement cet emplacement à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="8cf90-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cf90-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cf90-158">See also</span></span>

- [<span data-ttu-id="8cf90-159">Vue d’ensemble de l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="8cf90-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="8cf90-160">Didacticiel : analyser le sentiment avec l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="8cf90-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="8cf90-161">Informations de référence sur la commande auto-train de la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="8cf90-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="8cf90-162">Télémétrie dans la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="8cf90-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
