---
title: Outils .NET
description: Comment installer, utiliser, mettre à jour et supprimer des outils .NET. Décrit les outils globaux, les outils de chemin d’accès d’outil et les outils locaux.
author: KathleenDollard
ms.topic: how-to
ms.date: 02/12/2020
ms.openlocfilehash: 8839fd4fba72c9f973d906eabb72919306a847dd
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633882"
---
# <a name="how-to-manage-net-tools"></a><span data-ttu-id="15373-104">Comment gérer les outils .NET</span><span class="sxs-lookup"><span data-stu-id="15373-104">How to manage .NET tools</span></span>

<span data-ttu-id="15373-105">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="15373-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="15373-106">Un outil .NET est un package NuGet spécial qui contient une application console.</span><span class="sxs-lookup"><span data-stu-id="15373-106">A .NET tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="15373-107">Un outil peut être installé sur votre ordinateur de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="15373-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="15373-108">Comme un outil Global.</span><span class="sxs-lookup"><span data-stu-id="15373-108">As a global tool.</span></span>

  <span data-ttu-id="15373-109">Les fichiers binaires de l’outil sont installés dans un répertoire par défaut qui est ajouté à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="15373-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="15373-110">Vous pouvez appeler l’outil à partir de n’importe quel répertoire sur l’ordinateur sans spécifier son emplacement.</span><span class="sxs-lookup"><span data-stu-id="15373-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="15373-111">Une version d’un outil est utilisée pour tous les répertoires sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="15373-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="15373-112">En tant qu’outil Global dans un emplacement personnalisé (également appelé outil de chemin d’accès d’outil).</span><span class="sxs-lookup"><span data-stu-id="15373-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="15373-113">Les fichiers binaires de l’outil sont installés dans un emplacement que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="15373-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="15373-114">Vous pouvez appeler l’outil à partir du répertoire d’installation ou en fournissant le répertoire avec le nom de commande ou en ajoutant le répertoire à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="15373-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="15373-115">Une version d’un outil est utilisée pour tous les répertoires sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="15373-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="15373-116">En tant qu’outil local (s’applique à kit SDK .NET Core 3,0 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="15373-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="15373-117">Les fichiers binaires de l’outil sont installés dans un répertoire par défaut.</span><span class="sxs-lookup"><span data-stu-id="15373-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="15373-118">Vous appelez l’outil à partir du répertoire d’installation ou de l’un de ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="15373-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="15373-119">Différents répertoires peuvent utiliser différentes versions du même outil.</span><span class="sxs-lookup"><span data-stu-id="15373-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="15373-120">L’interface CLI .NET utilise des fichiers manifeste pour suivre les outils qui sont installés en tant qu’outils locaux dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="15373-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="15373-121">Lorsque le fichier manifeste est enregistré dans le répertoire racine d’un référentiel de code source, un contributeur peut cloner le référentiel et appeler une seule commande CLI .NET qui installe tous les outils listés dans les fichiers manifeste.</span><span class="sxs-lookup"><span data-stu-id="15373-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15373-122">Les outils .NET s’exécutent en mode confiance totale.</span><span class="sxs-lookup"><span data-stu-id="15373-122">.NET tools run in full trust.</span></span> <span data-ttu-id="15373-123">N’installez pas d’outil .NET, sauf si vous faites confiance à l’auteur.</span><span class="sxs-lookup"><span data-stu-id="15373-123">Do not install a .NET tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="15373-124">Rechercher un outil</span><span class="sxs-lookup"><span data-stu-id="15373-124">Find a tool</span></span>

<span data-ttu-id="15373-125">Voici quelques méthodes pour trouver des outils :</span><span class="sxs-lookup"><span data-stu-id="15373-125">Here are some ways to find tools:</span></span>

* <span data-ttu-id="15373-126">Utilisez la commande de recherche de l' [outil dotnet](dotnet-tool-search.md) pour rechercher un outil qui est publié sur NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="15373-126">Use the [dotnet tool search](dotnet-tool-search.md) command to find a tool that is published to NuGet.org.</span></span>
* <span data-ttu-id="15373-127">Recherchez le site Web [NuGet](https://www.nuget.org) à l’aide du filtre de type de package « outil .net ».</span><span class="sxs-lookup"><span data-stu-id="15373-127">Search the [NuGet](https://www.nuget.org) website by using the ".NET tool" package type filter.</span></span> <span data-ttu-id="15373-128">Pour plus d’informations, consultez [Recherche et sélection des packages](/nuget/consume-packages/finding-and-choosing-packages).</span><span class="sxs-lookup"><span data-stu-id="15373-128">For more information, see [Finding and choosing packages](/nuget/consume-packages/finding-and-choosing-packages).</span></span>
* <span data-ttu-id="15373-129">Consultez le code source des outils créés par l’équipe ASP.NET Core dans le [répertoire Tools du référentiel GitHub dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span><span class="sxs-lookup"><span data-stu-id="15373-129">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span></span>
* <span data-ttu-id="15373-130">Découvrez les outils de diagnostics dans les [outils de diagnostic .net](../diagnostics/index.md#net-core-diagnostic-global-tools).</span><span class="sxs-lookup"><span data-stu-id="15373-130">Learn about diagnostic tools at [.NET diagnostic tools](../diagnostics/index.md#net-core-diagnostic-global-tools).</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="15373-131">Vérifier l’auteur et les statistiques</span><span class="sxs-lookup"><span data-stu-id="15373-131">Check the author and statistics</span></span>

<span data-ttu-id="15373-132">Étant donné que les outils .NET s’exécutent en mode de confiance totale et que les outils globaux sont ajoutés à la variable d’environnement PATH, ils peuvent être très puissants.</span><span class="sxs-lookup"><span data-stu-id="15373-132">Since .NET tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="15373-133">Par conséquent, ne téléchargez pas d’outils provenant de personnes en qui vous n’avez pas confiance.</span><span class="sxs-lookup"><span data-stu-id="15373-133">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="15373-134">Si l’outil est hébergé sur NuGet, vous pouvez vérifier l’auteur et les statistiques en recherchant l’outil.</span><span class="sxs-lookup"><span data-stu-id="15373-134">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="15373-135">Installer un outil Global</span><span class="sxs-lookup"><span data-stu-id="15373-135">Install a global tool</span></span>

<span data-ttu-id="15373-136">Pour installer un outil comme un outil Global, utilisez l' `-g` `--global` option ou de l' [outil dotnet installer](dotnet-tool-install.md), comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="15373-136">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="15373-137">La sortie affiche la commande utilisée pour appeler l’outil et la version installée, similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="15373-137">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="15373-138">L’emplacement par défaut des binaires d’un outil dépend du système d’exploitation :</span><span class="sxs-lookup"><span data-stu-id="15373-138">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="15373-139">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="15373-139">OS</span></span>          | <span data-ttu-id="15373-140">Chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="15373-140">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="15373-141">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="15373-141">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="15373-142">Windows</span><span class="sxs-lookup"><span data-stu-id="15373-142">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="15373-143">Cet emplacement est ajouté au chemin d’accès de l’utilisateur lors de la première exécution du kit de développement logiciel (SDK), de sorte que les outils globaux peuvent être appelés à partir de n’importe quel répertoire sans spécifier l’emplacement de l’outil.</span><span class="sxs-lookup"><span data-stu-id="15373-143">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="15373-144">L’accès aux outils est spécifique à l’utilisateur, et non à l’ordinateur global.</span><span class="sxs-lookup"><span data-stu-id="15373-144">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="15373-145">Un outil Global est uniquement disponible pour l’utilisateur qui a installé l’outil.</span><span class="sxs-lookup"><span data-stu-id="15373-145">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="15373-146">Installer un outil Global dans un emplacement personnalisé</span><span class="sxs-lookup"><span data-stu-id="15373-146">Install a global tool in a custom location</span></span>

<span data-ttu-id="15373-147">Pour installer un outil comme un outil Global dans un emplacement personnalisé, utilisez l' `--tool-path` option d' [installation de l’outil dotnet](dotnet-tool-install.md), comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="15373-147">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="15373-148">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="15373-148">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="15373-149">Sur Linux ou macOS :</span><span class="sxs-lookup"><span data-stu-id="15373-149">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="15373-150">Le kit de développement logiciel (SDK) .NET n’ajoute pas cet emplacement automatiquement à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="15373-150">The .NET SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="15373-151">Pour [appeler un outil de chemin d’accès d’outil](#invoke-a-tool-path-tool), vous devez vous assurer que la commande est disponible à l’aide de l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="15373-151">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="15373-152">Ajoutez le répertoire d’installation à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="15373-152">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="15373-153">Spécifiez le chemin d’accès complet à l’outil lorsque vous l’appelez.</span><span class="sxs-lookup"><span data-stu-id="15373-153">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="15373-154">Appelez l’outil à partir du répertoire d’installation.</span><span class="sxs-lookup"><span data-stu-id="15373-154">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="15373-155">Installer un outil local</span><span class="sxs-lookup"><span data-stu-id="15373-155">Install a local tool</span></span>

<span data-ttu-id="15373-156">**S’applique au kit de développement logiciel (SDK) .NET Core 3,0 et versions ultérieures.**</span><span class="sxs-lookup"><span data-stu-id="15373-156">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="15373-157">Pour installer un outil pour un accès local uniquement (pour le répertoire et les sous-répertoires actifs), il doit être ajouté à un fichier manifeste de l’outil.</span><span class="sxs-lookup"><span data-stu-id="15373-157">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="15373-158">Pour créer un fichier de manifeste d’outil, exécutez la `dotnet new tool-manifest` commande :</span><span class="sxs-lookup"><span data-stu-id="15373-158">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="15373-159">Cette commande crée un fichier manifeste nommé *dotnet-tools.js* sous le répertoire *. config* .</span><span class="sxs-lookup"><span data-stu-id="15373-159">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="15373-160">Pour ajouter un outil local au fichier manifeste, utilisez la commande d’installation de l' [outil dotnet](dotnet-tool-install.md) et **omettez** les `--global` `--tool-path` options et, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="15373-160">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="15373-161">La sortie de la commande indique le fichier manifeste dans lequel se trouve l’outil qui vient d’être installé, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="15373-161">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="15373-162">L’exemple suivant montre un fichier manifeste avec deux outils locaux installés :</span><span class="sxs-lookup"><span data-stu-id="15373-162">The following example shows a manifest file with two local tools installed:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

<span data-ttu-id="15373-163">En général, vous ajoutez un outil local au répertoire racine du référentiel.</span><span class="sxs-lookup"><span data-stu-id="15373-163">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="15373-164">Après avoir vérifié le fichier manifeste dans le référentiel, les développeurs qui récupèrent le code à partir du référentiel obtiennent le dernier fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="15373-164">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="15373-165">Pour installer tous les outils listés dans le fichier manifeste, ils exécutent la `dotnet tool restore` commande suivante :</span><span class="sxs-lookup"><span data-stu-id="15373-165">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="15373-166">La sortie indique les outils qui ont été restaurés :</span><span class="sxs-lookup"><span data-stu-id="15373-166">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="15373-167">Installer une version d’outil spécifique</span><span class="sxs-lookup"><span data-stu-id="15373-167">Install a specific tool version</span></span>

<span data-ttu-id="15373-168">Pour installer une version préliminaire ou une version spécifique d’un outil, spécifiez le numéro de version à l’aide de l' `--version` option, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="15373-168">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="15373-169">Utiliser un outil</span><span class="sxs-lookup"><span data-stu-id="15373-169">Use a tool</span></span>

<span data-ttu-id="15373-170">La commande que vous utilisez pour appeler un outil peut être différente du nom du package que vous installez.</span><span class="sxs-lookup"><span data-stu-id="15373-170">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="15373-171">Pour afficher tous les outils actuellement installés sur l’ordinateur pour l’utilisateur actuel, utilisez la commande de [liste d’outils dotnet](dotnet-tool-list.md) :</span><span class="sxs-lookup"><span data-stu-id="15373-171">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="15373-172">La sortie affiche la version et la commande de chaque outil, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="15373-172">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="15373-173">Comme indiqué dans cet exemple, la liste affiche les outils locaux.</span><span class="sxs-lookup"><span data-stu-id="15373-173">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="15373-174">Pour afficher les outils globaux, utilisez l' `--global` option, et pour afficher les outils de chemin d’accès d’outil, utilisez l' `--tool-path` option.</span><span class="sxs-lookup"><span data-stu-id="15373-174">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="15373-175">Appeler un outil Global</span><span class="sxs-lookup"><span data-stu-id="15373-175">Invoke a global tool</span></span>

<span data-ttu-id="15373-176">Pour les outils globaux, utilisez la commande d’outil seule.</span><span class="sxs-lookup"><span data-stu-id="15373-176">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="15373-177">Par exemple, si la commande est `dotnetsay` ou `dotnet-doc` , c’est ce que vous utilisez pour appeler la commande :</span><span class="sxs-lookup"><span data-stu-id="15373-177">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="15373-178">Si la commande commence par le préfixe `dotnet-` , une autre façon d’appeler l’outil consiste à utiliser la `dotnet` commande et à omettre le préfixe de commande d’outil.</span><span class="sxs-lookup"><span data-stu-id="15373-178">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="15373-179">Par exemple, si la commande est `dotnet-doc` , la commande suivante appelle l’outil :</span><span class="sxs-lookup"><span data-stu-id="15373-179">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="15373-180">Toutefois, dans le scénario suivant, vous ne pouvez pas utiliser la `dotnet` commande pour appeler un outil Global :</span><span class="sxs-lookup"><span data-stu-id="15373-180">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="15373-181">Un outil Global et un outil local ont la même commande préfixée par `dotnet-` .</span><span class="sxs-lookup"><span data-stu-id="15373-181">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="15373-182">Vous souhaitez appeler l’outil Global à partir d’un répertoire qui se trouve dans l’étendue de l’outil local.</span><span class="sxs-lookup"><span data-stu-id="15373-182">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="15373-183">Dans ce scénario, `dotnet doc` et `dotnet dotnet-doc` appellent l’outil local.</span><span class="sxs-lookup"><span data-stu-id="15373-183">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="15373-184">Pour appeler l’outil Global, utilisez la commande seule :</span><span class="sxs-lookup"><span data-stu-id="15373-184">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="15373-185">Appeler un outil de chemin d’accès d’outil</span><span class="sxs-lookup"><span data-stu-id="15373-185">Invoke a tool-path tool</span></span>

<span data-ttu-id="15373-186">Pour appeler un outil global qui est installé à l’aide de l’option, assurez-vous que `tool-path` la commande est disponible, comme expliqué [plus haut dans cet article](#install-a-global-tool-in-a-custom-location).</span><span class="sxs-lookup"><span data-stu-id="15373-186">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="15373-187">Appeler un outil local</span><span class="sxs-lookup"><span data-stu-id="15373-187">Invoke a local tool</span></span>

<span data-ttu-id="15373-188">Pour appeler un outil local, vous devez utiliser la `dotnet` commande à partir du répertoire d’installation.</span><span class="sxs-lookup"><span data-stu-id="15373-188">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="15373-189">Vous pouvez utiliser la forme longue ( `dotnet tool run <COMMAND_NAME>` ) ou la forme abrégée ( `dotnet <COMMAND_NAME>` ), comme indiqué dans les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="15373-189">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="15373-190">Si la commande est préfixée par `dotnet-` , vous pouvez inclure ou omettre le préfixe lorsque vous appelez l’outil.</span><span class="sxs-lookup"><span data-stu-id="15373-190">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="15373-191">Par exemple, si la commande est `dotnet-doc` , l’un des exemples suivants appelle l’outil local :</span><span class="sxs-lookup"><span data-stu-id="15373-191">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="15373-192">Mettre à jour un outil</span><span class="sxs-lookup"><span data-stu-id="15373-192">Update a tool</span></span>

<span data-ttu-id="15373-193">La mise à jour d’un outil implique sa désinstallation et sa réinstallation avec la dernière version stable.</span><span class="sxs-lookup"><span data-stu-id="15373-193">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="15373-194">Pour mettre à jour un outil, utilisez la commande de [mise à jour de l’outil dotnet](dotnet-tool-update.md) avec la même option que celle utilisée pour installer l’outil :</span><span class="sxs-lookup"><span data-stu-id="15373-194">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="15373-195">Pour un outil local, le kit de développement logiciel (SDK) recherche le premier fichier manifeste qui contient l’ID de package en examinant le répertoire actif et les répertoires parents.</span><span class="sxs-lookup"><span data-stu-id="15373-195">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="15373-196">S’il n’existe aucun ID de package de ce type dans un fichier manifeste, le kit de développement logiciel (SDK) ajoute une nouvelle entrée au fichier manifeste le plus proche.</span><span class="sxs-lookup"><span data-stu-id="15373-196">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="15373-197">Désinstaller un outil</span><span class="sxs-lookup"><span data-stu-id="15373-197">Uninstall a tool</span></span>

<span data-ttu-id="15373-198">Supprimez un outil à l’aide de la commande de [désinstallation de l’outil dotnet](dotnet-tool-uninstall.md) avec la même option que celle utilisée pour installer l’outil :</span><span class="sxs-lookup"><span data-stu-id="15373-198">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path <packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="15373-199">Pour un outil local, le kit de développement logiciel (SDK) recherche le premier fichier manifeste qui contient l’ID de package en examinant le répertoire actif et les répertoires parents.</span><span class="sxs-lookup"><span data-stu-id="15373-199">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="15373-200">Obtenir de l’aide et résoudre les problèmes</span><span class="sxs-lookup"><span data-stu-id="15373-200">Get help and troubleshoot</span></span>

<span data-ttu-id="15373-201">Pour obtenir la liste des `dotnet tool` commandes disponibles, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="15373-201">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="15373-202">Pour obtenir des instructions sur l’utilisation de l’outil, entrez l’une des commandes suivantes ou consultez le site Web de l’outil :</span><span class="sxs-lookup"><span data-stu-id="15373-202">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="15373-203">En cas d’échec de l’installation ou de l’exécution d’un outil, consultez [résoudre les problèmes d’utilisation des outils .net](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="15373-203">If a tool fails to install or run, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15373-204">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15373-204">See also</span></span>

- [<span data-ttu-id="15373-205">Didacticiel : créer un outil .NET à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="15373-205">Tutorial: Create a .NET tool using the .NET CLI</span></span>](global-tools-how-to-create.md)
- [<span data-ttu-id="15373-206">Didacticiel : installer et utiliser un outil .NET global à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="15373-206">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="15373-207">Didacticiel : installer et utiliser un outil local .NET à l’aide de l’interface de commande .NET</span><span class="sxs-lookup"><span data-stu-id="15373-207">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
