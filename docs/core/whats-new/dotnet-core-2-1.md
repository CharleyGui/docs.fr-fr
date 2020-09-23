---
title: Nouveautés de .NET Core 2.1
description: Découvrez les nouvelles fonctionnalités de .NET Core 2.1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: f125a6a8d9287cb515478a10c2679c07817ae9a6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087360"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="0caa4-103">Nouveautés de .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0caa4-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="0caa4-104">.NET Core 2.1 inclut les nouvelles fonctionnalités et améliorations dans les domaines suivants :</span><span class="sxs-lookup"><span data-stu-id="0caa4-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="0caa4-105">Outillage</span><span class="sxs-lookup"><span data-stu-id="0caa4-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="0caa4-106">Restaurer par progression</span><span class="sxs-lookup"><span data-stu-id="0caa4-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="0caa4-107">Déploiement</span><span class="sxs-lookup"><span data-stu-id="0caa4-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="0caa4-108">Pack de compatibilité Windows</span><span class="sxs-lookup"><span data-stu-id="0caa4-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="0caa4-109">Améliorations de la compilation JIT</span><span class="sxs-lookup"><span data-stu-id="0caa4-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="0caa4-110">Modifications de l’API</span><span class="sxs-lookup"><span data-stu-id="0caa4-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="0caa4-111">Outillage</span><span class="sxs-lookup"><span data-stu-id="0caa4-111">Tooling</span></span>

<span data-ttu-id="0caa4-112">Le Kit SDK.NET Core 2.1 (2.1.300), les outils inclus avec .NET Core 2.1, intègrent les modifications et améliorations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0caa4-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="0caa4-113">Amélioration des performances des builds</span><span class="sxs-lookup"><span data-stu-id="0caa4-113">Build performance improvements</span></span>

<span data-ttu-id="0caa4-114">Un objectif majeur de .NET Core 2.1 est l’amélioration des performances des builds, en particulier pour les builds incrémentielles.</span><span class="sxs-lookup"><span data-stu-id="0caa4-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="0caa4-115">Ces améliorations des performances s’appliquent aux builds en ligne de commande à l’aide de `dotnet build` et aux builds dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0caa4-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="0caa4-116">Certaines zones individuelles d’amélioration incluent :</span><span class="sxs-lookup"><span data-stu-id="0caa4-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="0caa4-117">Pour la résolution de ressources de package, résolution uniquement des ressources utilisées par une build plutôt que de toutes les ressources.</span><span class="sxs-lookup"><span data-stu-id="0caa4-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="0caa4-118">Mise en cache des références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="0caa4-118">Caching of assembly references.</span></span>

- <span data-ttu-id="0caa4-119">Utilisation de serveurs de build SDK de longue durée, représentant des processus qui couvrent des appels `dotnet build` individuels.</span><span class="sxs-lookup"><span data-stu-id="0caa4-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="0caa4-120">Ils suppriment la nécessité de la compilation JIT de grands blocs de code à chaque exécution de `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="0caa4-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="0caa4-121">Les processus d’un serveur de build peuvent être automatiquement terminés avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0caa4-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="0caa4-122">Nouvelles commandes CLI</span><span class="sxs-lookup"><span data-stu-id="0caa4-122">New CLI commands</span></span>

<span data-ttu-id="0caa4-123">Un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0caa4-123">A number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="0caa4-124">Ces outils incluent :</span><span class="sxs-lookup"><span data-stu-id="0caa4-124">These tools include:</span></span>

- <span data-ttu-id="0caa4-125">`dotnet watch` fournit un observateur de système de fichiers qui attend la modification d’un fichier avant d’exécuter un ensemble désigné de commandes.</span><span class="sxs-lookup"><span data-stu-id="0caa4-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="0caa4-126">Par exemple, la commande suivante reconstruit automatiquement le projet actuel et génère une sortie détaillée à chaque modification d’un fichier :</span><span class="sxs-lookup"><span data-stu-id="0caa4-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="0caa4-127">Remarquez l’option `--` qui précède l’option `--verbose`.</span><span class="sxs-lookup"><span data-stu-id="0caa4-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="0caa4-128">Elle délimite les options passées directement à la commande `dotnet watch` à partir des arguments passés au processus enfant `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="0caa4-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="0caa4-129">Sans elle, l’option `--verbose` s’applique à la commande `dotnet watch`, et non à la commande `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="0caa4-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="0caa4-130">Pour plus d’informations, consultez [développer des applications ASP.net core à l’aide de dotnet Watch](/aspnet/core/tutorials/dotnet-watch).</span><span class="sxs-lookup"><span data-stu-id="0caa4-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch).</span></span>

- <span data-ttu-id="0caa4-131">`dotnet dev-certs` génère et gère les certificats utilisés pendant le développement dans les applications ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0caa4-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="0caa4-132">`dotnet user-secrets` gère les secrets d’un magasin de secrets d’un utilisateur dans les applications ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0caa4-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="0caa4-133">`dotnet sql-cache` crée un tableau et des index dans une base de données Microsoft SQL Server à utiliser pour la mise en cache distribuée.</span><span class="sxs-lookup"><span data-stu-id="0caa4-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="0caa4-134">`dotnet ef` est un outil de gestion des bases de données, des objets <xref:Microsoft.EntityFrameworkCore.DbContext> et des migrations dans les applications Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="0caa4-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="0caa4-135">Pour plus d’informations, consultez [Outils en ligne de commande EF Core .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="0caa4-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="0caa4-136">Outils globaux</span><span class="sxs-lookup"><span data-stu-id="0caa4-136">Global Tools</span></span>

<span data-ttu-id="0caa4-137">.NET Core 2.1 prend en charge les *outils globaux*, autrement dit des outils personnalisés disponibles globalement à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0caa4-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="0caa4-138">Le modèle d’extensibilité des versions précédentes de .NET Core proposant des outils personnalisés par projet uniquement à l’aide de `DotnetCliToolReference`.</span><span class="sxs-lookup"><span data-stu-id="0caa4-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using `DotnetCliToolReference`.</span></span>

<span data-ttu-id="0caa4-139">Pour installer un outil global, vous utilisez la commande [dotnet tool install](../tools/dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="0caa4-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="0caa4-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0caa4-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="0caa4-141">Une fois installé, l’outil peut être exécuté à partir de la ligne de commande en spécifiant le nom de l’outil.</span><span class="sxs-lookup"><span data-stu-id="0caa4-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="0caa4-142">Pour plus d’informations, consultez [Vue d’ensemble des outils globaux .NET Core](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0caa4-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="0caa4-143">Gestion des outils avec la commande `dotnet tool`</span><span class="sxs-lookup"><span data-stu-id="0caa4-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="0caa4-144">Dans le SDK .NET Core 2.1, toutes les opérations avec les outils utilisent la commande `dotnet tool`.</span><span class="sxs-lookup"><span data-stu-id="0caa4-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="0caa4-145">Les options suivantes sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="0caa4-145">The following options are available:</span></span>

- <span data-ttu-id="0caa4-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) pour installer un outil.</span><span class="sxs-lookup"><span data-stu-id="0caa4-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="0caa4-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) pour désinstaller et réinstaller un outil qui le met à jour.</span><span class="sxs-lookup"><span data-stu-id="0caa4-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="0caa4-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) pour répertorier les outils actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="0caa4-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="0caa4-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) pour désinstaller les outils actuellement installés.</span><span class="sxs-lookup"><span data-stu-id="0caa4-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="0caa4-150">Restauration par progression</span><span class="sxs-lookup"><span data-stu-id="0caa4-150">Roll forward</span></span>

<span data-ttu-id="0caa4-151">Toutes les applications .NET Core depuis .NET Core 2.0 extrapolent automatiquement vers la dernière *version mineure* installée sur un système.</span><span class="sxs-lookup"><span data-stu-id="0caa4-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="0caa4-152">À compter de .NET Core 2,0, si la version de .NET Core avec laquelle une application a été générée n’est pas présente au moment de l’exécution, l’application s’exécute automatiquement sur la dernière *version mineure* installée de .net core.</span><span class="sxs-lookup"><span data-stu-id="0caa4-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at run time, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="0caa4-153">En d’autres termes, si une application est générée avec .NET Core 2.0 et que .NET Core 2.0 n’est pas présent sur le système hôte, mais que .NET Core 2.1 l’est, l’application s’exécute avec .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="0caa4-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0caa4-154">Ce comportement de restauration par progression ne s’applique pas aux préversions,</span><span class="sxs-lookup"><span data-stu-id="0caa4-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="0caa4-155">Par défaut, il ne s’applique pas non plus aux versions majeures, mais vous pouvez changer ce comportement avec les paramètres ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="0caa4-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="0caa4-156">Vous pouvez modifier ce comportement en changeant le paramètre d’extrapolation en cas d’absence de framework partagé candidat.</span><span class="sxs-lookup"><span data-stu-id="0caa4-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="0caa4-157">Les paramètres disponibles sont :</span><span class="sxs-lookup"><span data-stu-id="0caa4-157">The available settings are:</span></span>

- <span data-ttu-id="0caa4-158">`0` : désactiver le comportement d’extrapolation de version mineure.</span><span class="sxs-lookup"><span data-stu-id="0caa4-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="0caa4-159">Avec ce paramètre, une application conçue pour .NET Core 2.0.0 extrapole vers .NET Core 2.0.1, mais pas vers .NET Core 2.2.0 ou .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="0caa4-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="0caa4-160">`1` : activer le comportement d’extrapolation de version mineure.</span><span class="sxs-lookup"><span data-stu-id="0caa4-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="0caa4-161">Il s’agit de la valeur par défaut pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="0caa4-161">This is the default value for the setting.</span></span> <span data-ttu-id="0caa4-162">Avec ce paramètre, une application conçue pour .NET Core 2.0.0 extrapole vers .NET Core 2.0.1 ou .NET Core 2.2.0 (en fonction de la version installée), mais n’extrapole pas vers .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="0caa4-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="0caa4-163">`2` : activer le comportement d’extrapolation de version mineure et majeure.</span><span class="sxs-lookup"><span data-stu-id="0caa4-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="0caa4-164">Si cette option est définie, même les versions majeures différentes sont prises en compte. Ainsi, une application conçue pour .NET Core 2.0.0 extrapole vers .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="0caa4-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="0caa4-165">Vous pouvez modifier ce paramètre de trois manières :</span><span class="sxs-lookup"><span data-stu-id="0caa4-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="0caa4-166">Affectez à la variable d’environnement `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="0caa4-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="0caa4-167">Ajoutez la ligne suivante avec la valeur souhaitée au fichier *.runtimeconfig.json* :</span><span class="sxs-lookup"><span data-stu-id="0caa4-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="0caa4-168">Lorsque vous utilisez l' [CLI .net Core](../tools/index.md), ajoutez l’option suivante avec la valeur souhaitée à une commande .net Core, par exemple `run` :</span><span class="sxs-lookup"><span data-stu-id="0caa4-168">When using the [.NET Core CLI](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="0caa4-169">L’extrapolation de version de correctif logiciel est indépendante de ce paramètre, et est effectuée une fois que l’éventuelle extrapolation de version mineure ou majeure a été appliquée.</span><span class="sxs-lookup"><span data-stu-id="0caa4-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="0caa4-170">Déploiement</span><span class="sxs-lookup"><span data-stu-id="0caa4-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="0caa4-171">Maintenance d’une application autonome</span><span class="sxs-lookup"><span data-stu-id="0caa4-171">Self-contained application servicing</span></span>

<span data-ttu-id="0caa4-172">`dotnet publish` publie désormais des applications autonomes avec une version de runtime révisée.</span><span class="sxs-lookup"><span data-stu-id="0caa4-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="0caa4-173">Lorsque vous publiez une application autonome avec le Kit de développement .NET Core 2.1 (2.1.300), votre application inclut la dernière version du runtime révisée et identifiée par ce SDK.</span><span class="sxs-lookup"><span data-stu-id="0caa4-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="0caa4-174">Lorsque vous effectuez une mise à niveau vers le dernier Kit de développement logiciel (SDK), vous publiez avec la dernière version du Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0caa4-174">When you upgrade to the latest SDK, you'll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="0caa4-175">Cela s’applique aux runtimes .NET Core 1.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="0caa4-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="0caa4-176">La publication autonome s’appuie sur les versions du Runtime sur NuGet.org. Vous n’avez pas besoin du runtime desservi sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0caa4-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="0caa4-177">À l’aide du Kit de développement logiciel .NET Core 2.0, les applications autonomes sont publiées avec le runtime .NET Core 2.0.0, sauf si une version différente est spécifiée via la propriété `RuntimeFrameworkVersion`.</span><span class="sxs-lookup"><span data-stu-id="0caa4-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="0caa4-178">Avec ce nouveau comportement, vous n’avez plus besoin de définir cette propriété pour sélectionner une version de Runtime plus élevée pour une application autonome.</span><span class="sxs-lookup"><span data-stu-id="0caa4-178">With this new behavior, you'll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="0caa4-179">Dorénavant, l’approche la plus simple consiste à toujours publier avec le Kit de développement .NET Core 2.1 (2.1.300).</span><span class="sxs-lookup"><span data-stu-id="0caa4-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="0caa4-180">Pour plus d’informations, voir [Restauration par progression du runtime de déploiement autonome](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="0caa4-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>

## <a name="windows-compatibility-pack"></a><span data-ttu-id="0caa4-181">Pack de compatibilité Windows</span><span class="sxs-lookup"><span data-stu-id="0caa4-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="0caa4-182">Lorsque vous portez du code existant de .NET Framework vers .NET Core, vous pouvez utiliser le [pack de compatibilité Windows](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="0caa4-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="0caa4-183">Il permet d’accéder aux plus de 20 000 API disponibles dans .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0caa4-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="0caa4-184">Ces API incluent les types dans l’espace de noms <xref:System.Drawing?displayProperty=nameWithType>, la classe <xref:System.Diagnostics.EventLog>, WMI, les compteurs de performances, les services Windows, ainsi que les types et membres de registre Windows.</span><span class="sxs-lookup"><span data-stu-id="0caa4-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="0caa4-185">Améliorations du compilateur JIT</span><span class="sxs-lookup"><span data-stu-id="0caa4-185">JIT compiler improvements</span></span>

<span data-ttu-id="0caa4-186">.NET Core intègre une nouvelle technologie de compilateur JIT appelée *compilation à plusieurs niveaux* (ou également *optimisation adaptative*), qui peut améliorer considérablement les performances.</span><span class="sxs-lookup"><span data-stu-id="0caa4-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="0caa4-187">La compilation à plusieurs niveaux n’est pas activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="0caa4-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="0caa4-188">Une des tâches importantes effectuées par le compilateur JIT est l’optimisation de l’exécution du code.</span><span class="sxs-lookup"><span data-stu-id="0caa4-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="0caa4-189">Toutefois, pour les chemins de code peu utilisés, le compilateur peut passer plus de temps à optimiser le code que le runtime passe à exécuter du code non optimisé.</span><span class="sxs-lookup"><span data-stu-id="0caa4-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="0caa4-190">La compilation à plusieurs niveaux ajoute deux étapes à la compilation JIT :</span><span class="sxs-lookup"><span data-stu-id="0caa4-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="0caa4-191">Un **premier niveau**, qui génère du code aussi rapidement que possible.</span><span class="sxs-lookup"><span data-stu-id="0caa4-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="0caa4-192">Un **second niveau**, qui génère un code optimisé pour les méthodes fréquemment exécutées.</span><span class="sxs-lookup"><span data-stu-id="0caa4-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="0caa4-193">Le second niveau de compilation est effectué en parallèle pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="0caa4-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="0caa4-194">Vous pouvez activer la compilation à plusieurs niveaux de deux manières.</span><span class="sxs-lookup"><span data-stu-id="0caa4-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="0caa4-195">Pour utiliser la compilation à plusieurs niveaux dans tous les projets qui utilisent le Kit de développement .NET Core 2.1, définissez la variable d’environnement suivante :</span><span class="sxs-lookup"><span data-stu-id="0caa4-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="0caa4-196">Pour utiliser la compilation à plusieurs niveaux par projet, ajoutez la propriété `<TieredCompilation>` à la section `<PropertyGroup>` du fichier projet MSBuild, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0caa4-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="0caa4-197">Modifications d'API</span><span class="sxs-lookup"><span data-stu-id="0caa4-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="0caa4-198">`Span<T>` et `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="0caa4-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="0caa4-199">.NET Core 2.1 inclut certains nouveaux types qui facilitent l’utilisation de tableaux et d’autres types de mémoire beaucoup plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="0caa4-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="0caa4-200">Ces nouveaux types incluent :</span><span class="sxs-lookup"><span data-stu-id="0caa4-200">The new types include:</span></span>

- <span data-ttu-id="0caa4-201">Voir <xref:System.Span%601?displayProperty=nameWithType> et <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0caa4-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="0caa4-202">Voir <xref:System.Memory%601?displayProperty=nameWithType> et <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0caa4-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0caa4-203">Sans ces types, lorsque vous passez des éléments de ce type comme une partie d’un tableau ou d’une section d’une mémoire tampon, vous devez créer une copie d’une partie des données avant de les passer à une méthode.</span><span class="sxs-lookup"><span data-stu-id="0caa4-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="0caa4-204">Ces types fournissent une représentation virtuelle des données, qui supprime les opérations supplémentaires d’allocation de mémoire et de copie.</span><span class="sxs-lookup"><span data-stu-id="0caa4-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="0caa4-205">L’exemple suivant utilise une instance <xref:System.Span%601> et <xref:System.Memory%601> pour fournir une représentation virtuelle de 10 éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="0caa4-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](./snippets/dotnet-core-2-1/csharp/program.cs)]

[!code-vb[Memory\<T>](./snippets/dotnet-core-2-1/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="0caa4-206">Compression de Brotli</span><span class="sxs-lookup"><span data-stu-id="0caa4-206">Brotli compression</span></span>

<span data-ttu-id="0caa4-207">.NET Core 2.1 prend en charge la compression et la décompression de Brotli.</span><span class="sxs-lookup"><span data-stu-id="0caa4-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="0caa4-208">Brotli est un algorithme de compression sans perte à usage général, défini dans [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt), et pris en charge par la plupart des navigateurs web et les principaux serveurs web.</span><span class="sxs-lookup"><span data-stu-id="0caa4-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="0caa4-209">Vous pouvez utiliser une classe <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> basée sur les flux ou des classes hautes performances <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> et <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> basées sur la portée.</span><span class="sxs-lookup"><span data-stu-id="0caa4-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="0caa4-210">L'exemple suivant montre une compression avec la classe <xref:System.IO.Compression.BrotliStream> :</span><span class="sxs-lookup"><span data-stu-id="0caa4-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](./snippets/dotnet-core-2-1/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](./snippets/dotnet-core-2-1/vb/brotli.vb#1)]

<span data-ttu-id="0caa4-211">Le comportement de <xref:System.IO.Compression.BrotliStream> est identique à <xref:System.IO.Compression.DeflateStream> et <xref:System.IO.Compression.GZipStream>, ce qui facilite la convertir du code qui appelle ces API pour <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="0caa4-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="0caa4-212">Nouvelles API de chiffrement et améliorations du chiffrement</span><span class="sxs-lookup"><span data-stu-id="0caa4-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="0caa4-213">.NET Core 2.1 inclut de nombreuses améliorations des API de chiffrement :</span><span class="sxs-lookup"><span data-stu-id="0caa4-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="0caa4-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> est disponible dans le package System.Security.Cryptography.Pkcs.</span><span class="sxs-lookup"><span data-stu-id="0caa4-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="0caa4-215">L’implémentation est identique à la classe <xref:System.Security.Cryptography.Pkcs.SignedCms> du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0caa4-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="0caa4-216">De nouvelles surcharges des méthodes <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> et <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> acceptent un identificateur d’algorithme de hachage permettant aux appelants d’obtenir les valeurs d’empreinte numérique de certificat à l’aide d’algorithmes autres que SHA-1.</span><span class="sxs-lookup"><span data-stu-id="0caa4-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="0caa4-217">De nouvelles API de chiffrement basées sur <xref:System.Span%601> sont disponibles pour le hachage, HMAC, la génération de codes de chiffrement aléatoires, la génération de signatures asymétriques, le traitement de signatures asymétriques et le chiffrement RSA.</span><span class="sxs-lookup"><span data-stu-id="0caa4-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="0caa4-218">Les performances de <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> ont été améliorées d’environ 15 % grâce à une implémentation <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="0caa4-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="0caa4-219">La nouvelle classe <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> inclut deux nouvelles méthodes :</span><span class="sxs-lookup"><span data-stu-id="0caa4-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="0caa4-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> prend une quantité fixe de temps pour renvoyer deux entrées de même longueur, ce qui permet de l’utiliser dans une vérification du chiffrement afin d’éviter la temporisation des informations sur le canal auxiliaire.</span><span class="sxs-lookup"><span data-stu-id="0caa4-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="0caa4-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> est une routine de nettoyage de la mémoire qui ne peut pas être optimisée.</span><span class="sxs-lookup"><span data-stu-id="0caa4-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="0caa4-222">La méthode statique <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> remplit <xref:System.Span%601> de valeurs aléatoires.</span><span class="sxs-lookup"><span data-stu-id="0caa4-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="0caa4-223"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType>Est désormais pris en charge sur Linux et MacOS.</span><span class="sxs-lookup"><span data-stu-id="0caa4-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and macOS.</span></span>

- <span data-ttu-id="0caa4-224">Diffie-Hellman à courbe elliptique (ECDH) est désormais disponible dans la famille de classe <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0caa4-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="0caa4-225">La surface d’exposition est la même que dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0caa4-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="0caa4-226">L’instance retournée par <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> peut chiffrer ou déchiffrer avec OAEP à l’aide d’un condensat SHA-2, et permet de générer ou de valider des signatures à l’aide de RSA-PSS.</span><span class="sxs-lookup"><span data-stu-id="0caa4-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="0caa4-227">Améliorations des sockets</span><span class="sxs-lookup"><span data-stu-id="0caa4-227">Sockets improvements</span></span>

<span data-ttu-id="0caa4-228">.NET Core inclut un nouveau type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, et une <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType> réécrite, qui constituent la base des API de mise en réseau de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="0caa4-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="0caa4-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, par exemple, est la base de l’implémentation <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="0caa4-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="0caa4-230">Dans les versions précédentes de .NET Core, les API de niveau supérieur étaient basées sur des implémentations de mise en réseau natives.</span><span class="sxs-lookup"><span data-stu-id="0caa4-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="0caa4-231">L’implémentation de sockets introduite dans .NET Core 2.1 présente plusieurs avantages :</span><span class="sxs-lookup"><span data-stu-id="0caa4-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="0caa4-232">Une amélioration significative des performances par rapport à l’implémentation précédente.</span><span class="sxs-lookup"><span data-stu-id="0caa4-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="0caa4-233">La suppression des dépendances de plateforme, qui simplifie le déploiement et la maintenance.</span><span class="sxs-lookup"><span data-stu-id="0caa4-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="0caa4-234">Comportement cohérent sur toutes les plates-formes .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0caa4-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="0caa4-235"><xref:System.Net.Http.SocketsHttpHandler> est l’implémentation par défaut dans .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="0caa4-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="0caa4-236">Toutefois, vous pouvez configurer votre application pour utiliser l’ancienne classe <xref:System.Net.Http.HttpClientHandler> en appelant la méthode <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="0caa4-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="0caa4-237">Vous pouvez également utiliser une variable d’environnement pour désactiver l’utilisation des implémentations de sockets basées sur <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="0caa4-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="0caa4-238">Pour cela, définissez `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` sur `false` ou 0.</span><span class="sxs-lookup"><span data-stu-id="0caa4-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="0caa4-239">Sous Windows, vous pouvez également choisir d’utiliser <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, repose sur une implémentation native, ou la classe <xref:System.Net.Http.SocketsHttpHandler> en passant une instance de la classe au constructeur <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="0caa4-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="0caa4-240">Sous Linux et macOS, vous pouvez uniquement configurer <xref:System.Net.Http.HttpClient> par processus.</span><span class="sxs-lookup"><span data-stu-id="0caa4-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="0caa4-241">Sous Linux, vous devez déployer [libcurl](https://curl.haxx.se/libcurl/) si vous souhaitez utiliser l’ancienne implémentation <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="0caa4-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="0caa4-242">(Il est installé avec .NET Core 2.0.)</span><span class="sxs-lookup"><span data-stu-id="0caa4-242">(It is installed with .NET Core 2.0.)</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="0caa4-243">Changements cassants</span><span class="sxs-lookup"><span data-stu-id="0caa4-243">Breaking changes</span></span>

<span data-ttu-id="0caa4-244">Pour plus d’informations sur les modifications avec rupture, consultez [modifications avec rupture pour la migration de la version 2,0 vers 2,1](../compatibility/2.0-2.1.md).</span><span class="sxs-lookup"><span data-stu-id="0caa4-244">For information about breaking changes, see [Breaking changes for migration from version 2.0 to 2.1](../compatibility/2.0-2.1.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0caa4-245">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0caa4-245">See also</span></span>

- [<span data-ttu-id="0caa4-246">Nouveautés de .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="0caa4-246">What's new in .NET Core 3.1</span></span>](dotnet-core-3-1.md)
- [<span data-ttu-id="0caa4-247">Nouvelles fonctionnalités d’EF Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0caa4-247">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="0caa4-248">Nouveautés d’ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0caa4-248">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
