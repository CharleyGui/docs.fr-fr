---
title: .NET Outils de base
description: Comment installer, utiliser, mettre à jour et supprimer les outils .NET Core. Couvre les outils globaux, les outils de chemin à outils et les outils locaux.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 2f0101c6385c41eda49bcb2458428c1f14552617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847783"
---
# <a name="how-to-manage-net-core-tools"></a><span data-ttu-id="d570b-104">Comment gérer les outils de base .NET</span><span class="sxs-lookup"><span data-stu-id="d570b-104">How to manage .NET Core tools</span></span>

<span data-ttu-id="d570b-105">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="d570b-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="d570b-106">Un outil .NET Core est un forfait NuGet spécial qui contient une application de console.</span><span class="sxs-lookup"><span data-stu-id="d570b-106">A .NET Core tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="d570b-107">Un outil peut être installé sur votre machine de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="d570b-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="d570b-108">En tant qu’outil global.</span><span class="sxs-lookup"><span data-stu-id="d570b-108">As a global tool.</span></span>

  <span data-ttu-id="d570b-109">Les binaires d’outils sont installés dans un répertoire par défaut qui est ajouté à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="d570b-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="d570b-110">Vous pouvez invoquer l’outil à partir de n’importe quel répertoire sur la machine sans spécifier son emplacement.</span><span class="sxs-lookup"><span data-stu-id="d570b-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="d570b-111">Une version d’un outil est utilisée pour tous les répertoires de la machine.</span><span class="sxs-lookup"><span data-stu-id="d570b-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="d570b-112">En tant qu’outil global dans un emplacement personnalisé (également connu sous le nom d’outil-chemin).</span><span class="sxs-lookup"><span data-stu-id="d570b-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="d570b-113">Les binaires d’outils sont installés dans un endroit que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="d570b-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="d570b-114">Vous pouvez invoquer l’outil à partir du répertoire d’installation ou en fournissant le répertoire avec le nom de commande ou en ajoutant l’annuaire à la variable de l’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="d570b-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="d570b-115">Une version d’un outil est utilisée pour tous les répertoires de la machine.</span><span class="sxs-lookup"><span data-stu-id="d570b-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="d570b-116">En tant qu’outil local (s’applique à .NET Core SDK 3.0 et plus tard).</span><span class="sxs-lookup"><span data-stu-id="d570b-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="d570b-117">Les binaires d’outils sont installés dans un répertoire par défaut.</span><span class="sxs-lookup"><span data-stu-id="d570b-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="d570b-118">Vous invoquez l’outil du répertoire d’installation ou de l’un de ses sous-directeurs.</span><span class="sxs-lookup"><span data-stu-id="d570b-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="d570b-119">Différents répertoires peuvent utiliser différentes versions d’un même outil.</span><span class="sxs-lookup"><span data-stu-id="d570b-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="d570b-120">Le CLI .NET utilise des fichiers manifestes pour garder une trace des outils qui sont installés comme locaux à un répertoire.</span><span class="sxs-lookup"><span data-stu-id="d570b-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="d570b-121">Lorsque le fichier manifeste est enregistré dans l’annuaire root d’un référentiel de code source, un contributeur peut cloner le référentiel et invoquer une seule commande CLI de base .NET qui installe tous les outils énumérés dans les fichiers manifestes.</span><span class="sxs-lookup"><span data-stu-id="d570b-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET Core CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d570b-122">.NET Outils de base fonctionnent en pleine confiance.</span><span class="sxs-lookup"><span data-stu-id="d570b-122">.NET Core tools run in full trust.</span></span> <span data-ttu-id="d570b-123">N’installez pas un outil .NET Core sauf si vous faites confiance à l’auteur.</span><span class="sxs-lookup"><span data-stu-id="d570b-123">Do not install a .NET Core tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="d570b-124">Trouver un outil</span><span class="sxs-lookup"><span data-stu-id="d570b-124">Find a tool</span></span>

<span data-ttu-id="d570b-125">Actuellement, .NET Core n’a pas de fonctionnalité de recherche d’outils.</span><span class="sxs-lookup"><span data-stu-id="d570b-125">Currently, .NET Core doesn't have a tool search feature.</span></span> <span data-ttu-id="d570b-126">Voici quelques façons de trouver des outils :</span><span class="sxs-lookup"><span data-stu-id="d570b-126">Here are some ways to find tools:</span></span>

* <span data-ttu-id="d570b-127">Voir la liste des outils dans le référentiel GitHub [natemcmaster/dotnet-tools.](https://github.com/natemcmaster/dotnet-tools)</span><span class="sxs-lookup"><span data-stu-id="d570b-127">See the list of tools in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="d570b-128">Utilisez [ToolGet](https://www.toolget.net/) pour rechercher des outils .NET.</span><span class="sxs-lookup"><span data-stu-id="d570b-128">Use [ToolGet](https://www.toolget.net/) to search for .NET tools.</span></span>
* <span data-ttu-id="d570b-129">Voir le code source pour les outils créés par l’équipe ASP.NET Core dans le [répertoire Tools du référentiel GitHub dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span><span class="sxs-lookup"><span data-stu-id="d570b-129">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span></span>
* <span data-ttu-id="d570b-130">En savoir plus sur les outils de diagnostic à [.NET Core dotnet outils de diagnostic](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span><span class="sxs-lookup"><span data-stu-id="d570b-130">Learn about diagnostic tools at [.NET Core dotnet diagnostic tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span></span>
* <span data-ttu-id="d570b-131">Recherchez le site [Web de NuGet.](https://www.nuget.org)</span><span class="sxs-lookup"><span data-stu-id="d570b-131">Search the [NuGet](https://www.nuget.org) website.</span></span> <span data-ttu-id="d570b-132">Cependant, le site NuGet n’a pas encore de fonctionnalité qui vous permet de rechercher uniquement des paquets d’outils.</span><span class="sxs-lookup"><span data-stu-id="d570b-132">However, the NuGet site doesn't yet have a feature that lets you search only for tool packages.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="d570b-133">Vérifier l’auteur et les statistiques</span><span class="sxs-lookup"><span data-stu-id="d570b-133">Check the author and statistics</span></span>

<span data-ttu-id="d570b-134">Étant donné que les outils .NET Core fonctionnent en pleine confiance et que des outils globaux sont ajoutés à la variable de l’environnement PATH, ils peuvent être très puissants.</span><span class="sxs-lookup"><span data-stu-id="d570b-134">Since .NET Core tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="d570b-135">Par conséquent, ne téléchargez pas d’outils provenant de personnes en qui vous n’avez pas confiance.</span><span class="sxs-lookup"><span data-stu-id="d570b-135">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="d570b-136">Si l’outil est hébergé sur NuGet, vous pouvez vérifier l’auteur et les statistiques en recherchant l’outil.</span><span class="sxs-lookup"><span data-stu-id="d570b-136">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="d570b-137">Installer un outil global</span><span class="sxs-lookup"><span data-stu-id="d570b-137">Install a global tool</span></span>

<span data-ttu-id="d570b-138">Pour installer un outil comme outil `-g` `--global` global, utilisez l’installation ou l’option de [l’installation d’outils dotnet,](dotnet-tool-install.md)comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d570b-138">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="d570b-139">La sortie montre la commande utilisée pour invoquer l’outil et la version installée, semblable à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d570b-139">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="d570b-140">L’emplacement par défaut des binaires d’un outil dépend du système d’exploitation :</span><span class="sxs-lookup"><span data-stu-id="d570b-140">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="d570b-141">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="d570b-141">OS</span></span>          | <span data-ttu-id="d570b-142">Path</span><span class="sxs-lookup"><span data-stu-id="d570b-142">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="d570b-143">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="d570b-143">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="d570b-144"> Windows</span><span class="sxs-lookup"><span data-stu-id="d570b-144">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="d570b-145">Cet emplacement est ajouté au chemin de l’utilisateur lorsque le SDK est géré pour la première fois, de sorte que les outils globaux peuvent être invoqués à partir de n’importe quel répertoire sans spécifier l’emplacement de l’outil.</span><span class="sxs-lookup"><span data-stu-id="d570b-145">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="d570b-146">L’accès à l’outil est spécifique à l’utilisateur, et non à la machine mondiale.</span><span class="sxs-lookup"><span data-stu-id="d570b-146">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="d570b-147">Un outil global n’est disponible que pour l’utilisateur qui a installé l’outil.</span><span class="sxs-lookup"><span data-stu-id="d570b-147">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="d570b-148">Installer un outil global dans un emplacement personnalisé</span><span class="sxs-lookup"><span data-stu-id="d570b-148">Install a global tool in a custom location</span></span>

<span data-ttu-id="d570b-149">Pour installer un outil comme outil global dans `--tool-path` un emplacement personnalisé, utilisez l’option d’installation d’outils [dotnet,](dotnet-tool-install.md)comme le montrent les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="d570b-149">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="d570b-150">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="d570b-150">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="d570b-151">Sur Linux ou macOS :</span><span class="sxs-lookup"><span data-stu-id="d570b-151">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="d570b-152">Le SDK core .NET n’ajoute pas automatiquement cet emplacement à la variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="d570b-152">The .NET Core SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="d570b-153">Pour [invoquer un outil de chemin d’outil,](#invoke-a-tool-path-tool)vous devez vous assurer que la commande est disponible en utilisant l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="d570b-153">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="d570b-154">Ajouter le répertoire d’installation à la variable de l’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="d570b-154">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="d570b-155">Spécifier le chemin complet vers l’outil lorsque vous l’invoquez.</span><span class="sxs-lookup"><span data-stu-id="d570b-155">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="d570b-156">Invoquez l’outil à partir de l’annuaire d’installation.</span><span class="sxs-lookup"><span data-stu-id="d570b-156">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="d570b-157">Installer un outil local</span><span class="sxs-lookup"><span data-stu-id="d570b-157">Install a local tool</span></span>

<span data-ttu-id="d570b-158">**S’applique à .NET Core 3.0 SDK et plus tard.**</span><span class="sxs-lookup"><span data-stu-id="d570b-158">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="d570b-159">Pour installer un outil d’accès local uniquement (pour l’annuaire actuel et les sous-directeurs), il doit être ajouté à un fichier manifeste d’outil.</span><span class="sxs-lookup"><span data-stu-id="d570b-159">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="d570b-160">Pour créer un fichier manifeste `dotnet new tool-manifest` d’outil, exécutez la commande :</span><span class="sxs-lookup"><span data-stu-id="d570b-160">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="d570b-161">Cette commande crée un fichier manifeste nommé *dotnet-tools.json* sous l’annuaire *.config.*</span><span class="sxs-lookup"><span data-stu-id="d570b-161">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="d570b-162">Pour ajouter un outil local au fichier manifeste, utilisez l’outil `--tool-path` [dotnet installer](dotnet-tool-install.md) la commande et **omettre** les options et les `--global` options, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d570b-162">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="d570b-163">La sortie de commande indique dans quel fichier manifeste l’outil nouvellement installé est, semblable à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d570b-163">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="d570b-164">L’exemple suivant montre un fichier manifeste avec deux outils locaux installés :</span><span class="sxs-lookup"><span data-stu-id="d570b-164">The following example shows a manifest file with two local tools installed:</span></span>

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

<span data-ttu-id="d570b-165">Vous ajoutez généralement un outil local à l’annuaire racine du référentiel.</span><span class="sxs-lookup"><span data-stu-id="d570b-165">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="d570b-166">Après avoir vérifié le fichier manifeste au référentiel, les développeurs qui vérifient le code du référentiel obtiennent le dernier fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="d570b-166">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="d570b-167">Pour installer tous les outils énumérés dans `dotnet tool restore` le fichier manifeste, ils exécutent la commande :</span><span class="sxs-lookup"><span data-stu-id="d570b-167">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="d570b-168">La sortie indique quels outils ont été restaurés :</span><span class="sxs-lookup"><span data-stu-id="d570b-168">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="d570b-169">Installer une version outil spécifique</span><span class="sxs-lookup"><span data-stu-id="d570b-169">Install a specific tool version</span></span>

<span data-ttu-id="d570b-170">Pour installer une version pré-version ou une version spécifique d’un outil, spécifiez le numéro de version en utilisant l’option, `--version` comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d570b-170">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="d570b-171">Utiliser un outil</span><span class="sxs-lookup"><span data-stu-id="d570b-171">Use a tool</span></span>

<span data-ttu-id="d570b-172">La commande que vous utilisez pour invoquer un outil peut être différente du nom du paquet que vous installez.</span><span class="sxs-lookup"><span data-stu-id="d570b-172">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="d570b-173">Pour afficher tous les outils actuellement installés sur la machine pour l’utilisateur actuel, utilisez la commande [de liste d’outils dotnet](dotnet-tool-list.md) :</span><span class="sxs-lookup"><span data-stu-id="d570b-173">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="d570b-174">La sortie affiche la version et la commande de chaque outil, semblables à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d570b-174">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="d570b-175">Comme le montre cet exemple, la liste montre les outils locaux.</span><span class="sxs-lookup"><span data-stu-id="d570b-175">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="d570b-176">Pour voir les outils `--global` globaux, utiliser l’option et `--tool-path` voir les outils de voie d’outils, utilisez l’option.</span><span class="sxs-lookup"><span data-stu-id="d570b-176">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="d570b-177">Invoquer un outil global</span><span class="sxs-lookup"><span data-stu-id="d570b-177">Invoke a global tool</span></span>

<span data-ttu-id="d570b-178">Pour les outils globaux, utilisez la commande d’outils par lui-même.</span><span class="sxs-lookup"><span data-stu-id="d570b-178">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="d570b-179">Par exemple, si `dotnetsay` la `dotnet-doc`commande est ou , c’est ce que vous utilisez pour invoquer la commande:</span><span class="sxs-lookup"><span data-stu-id="d570b-179">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="d570b-180">Si la commande commence `dotnet-`par le préfixe, une autre `dotnet` façon d’invoquer l’outil est d’utiliser la commande et d’omettre le préfixe de commande de l’outil.</span><span class="sxs-lookup"><span data-stu-id="d570b-180">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="d570b-181">Par exemple, si `dotnet-doc`la commande est, la commande suivante invoque l’outil :</span><span class="sxs-lookup"><span data-stu-id="d570b-181">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="d570b-182">Toutefois, dans le scénario suivant, `dotnet` vous ne pouvez pas utiliser la commande pour invoquer un outil global :</span><span class="sxs-lookup"><span data-stu-id="d570b-182">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="d570b-183">Un outil global et un outil local ont `dotnet-`la même commande préfixée par .</span><span class="sxs-lookup"><span data-stu-id="d570b-183">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="d570b-184">Vous souhaitez invoquer l’outil global à partir d’un répertoire qui est en portée pour l’outil local.</span><span class="sxs-lookup"><span data-stu-id="d570b-184">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="d570b-185">Dans ce `dotnet doc` scénario, et `dotnet dotnet-doc` invoquer l’outil local.</span><span class="sxs-lookup"><span data-stu-id="d570b-185">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="d570b-186">Pour invoquer l’outil global, utilisez la commande par lui-même :</span><span class="sxs-lookup"><span data-stu-id="d570b-186">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="d570b-187">Invoquer un outil de chemin d’outil</span><span class="sxs-lookup"><span data-stu-id="d570b-187">Invoke a tool-path tool</span></span>

<span data-ttu-id="d570b-188">Pour invoquer un outil global `tool-path` qui est installé en utilisant l’option, assurez-vous que la commande est disponible, comme expliqué [plus tôt dans cet article](#install-a-global-tool-in-a-custom-location).</span><span class="sxs-lookup"><span data-stu-id="d570b-188">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="d570b-189">Invoquer un outil local</span><span class="sxs-lookup"><span data-stu-id="d570b-189">Invoke a local tool</span></span>

<span data-ttu-id="d570b-190">Pour invoquer un outil local, vous devez utiliser la `dotnet` commande à partir de l’annuaire d’installation.</span><span class="sxs-lookup"><span data-stu-id="d570b-190">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="d570b-191">Vous pouvez utiliser la`dotnet tool run <COMMAND_NAME>`forme longue (`dotnet <COMMAND_NAME>`) ou la forme courte ( ), comme indiqué dans les exemples suivants:</span><span class="sxs-lookup"><span data-stu-id="d570b-191">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="d570b-192">Si la commande est `dotnet-`préfixée par , vous pouvez inclure ou omettre le préfixe lorsque vous invoquez l’outil.</span><span class="sxs-lookup"><span data-stu-id="d570b-192">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="d570b-193">Par exemple, si `dotnet-doc`la commande est, l’un des exemples suivants invoque l’outil local :</span><span class="sxs-lookup"><span data-stu-id="d570b-193">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="d570b-194">Mettre à jour un outil</span><span class="sxs-lookup"><span data-stu-id="d570b-194">Update a tool</span></span>

<span data-ttu-id="d570b-195">La mise à jour d’un outil implique de le désinstaller et de le réinstaller avec la dernière version stable.</span><span class="sxs-lookup"><span data-stu-id="d570b-195">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="d570b-196">Pour mettre à jour un outil, utilisez la commande [de mise à jour de l’outil dotnet](dotnet-tool-update.md) avec la même option que vous avez utilisée pour installer l’outil :</span><span class="sxs-lookup"><span data-stu-id="d570b-196">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="d570b-197">Pour un outil local, le SDK trouve le premier fichier manifeste qui contient l’ID du paquet en regardant dans l’annuaire actuel et les répertoires parent.</span><span class="sxs-lookup"><span data-stu-id="d570b-197">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="d570b-198">S’il n’y a pas d’id de paquet dans un fichier manifeste, le SDK ajoute une nouvelle entrée au fichier manifeste le plus proche.</span><span class="sxs-lookup"><span data-stu-id="d570b-198">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="d570b-199">Désinstaller un outil</span><span class="sxs-lookup"><span data-stu-id="d570b-199">Uninstall a tool</span></span>

<span data-ttu-id="d570b-200">Retirez un outil en utilisant [l’outil dotnet désinstaller](dotnet-tool-uninstall.md) la commande avec la même option que vous avez utilisé pour installer l’outil:</span><span class="sxs-lookup"><span data-stu-id="d570b-200">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="d570b-201">Pour un outil local, le SDK trouve le premier fichier manifeste qui contient l’ID du paquet en regardant dans l’annuaire actuel et les répertoires parent.</span><span class="sxs-lookup"><span data-stu-id="d570b-201">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="d570b-202">Obtenez de l’aide et dépannez</span><span class="sxs-lookup"><span data-stu-id="d570b-202">Get help and troubleshoot</span></span>

<span data-ttu-id="d570b-203">Pour obtenir une `dotnet tool` liste de commandes disponibles, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d570b-203">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="d570b-204">Pour obtenir des instructions d’utilisation de l’outil, saisissez l’une des commandes suivantes ou consultez le site Web de l’outil :</span><span class="sxs-lookup"><span data-stu-id="d570b-204">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="d570b-205">Si un outil ne parvient pas à installer ou à exécuter, voir [Troubleshoot .NET Core problèmes d’utilisation de l’outil](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="d570b-205">If a tool fails to install or run, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d570b-206">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d570b-206">See also</span></span>

- [<span data-ttu-id="d570b-207">Tutorial: Créer un outil .NET Core en utilisant le CLI de base .NET</span><span class="sxs-lookup"><span data-stu-id="d570b-207">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>](global-tools-how-to-create.md)
- [<span data-ttu-id="d570b-208">Tutorial: Installer et utiliser un outil mondial .NET Core en utilisant le CLI CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="d570b-208">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="d570b-209">Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="d570b-209">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
