---
title: Installer .NET Core sur macOS
description: En savoir plus sur les versions de macOS sur lesquelles vous pouvez installer .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 06/25/2020
ms.openlocfilehash: 2900d98dbd30c51f689cdce37ea273ccc4f598b5
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308921"
---
# <a name="install-net-core-on-macos"></a><span data-ttu-id="22b17-103">Installer .NET Core sur macOS</span><span class="sxs-lookup"><span data-stu-id="22b17-103">Install .NET Core on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [Installer sur Windows](windows.md)
> - [Installer sur macOS](macos.md)
> - [Installer sur Linux](linux.md)

<span data-ttu-id="22b17-107">Dans cet article, vous allez apprendre à installer .NET Core sur macOS.</span><span class="sxs-lookup"><span data-stu-id="22b17-107">In this article, you'll learn how to install .NET Core on macOS.</span></span> <span data-ttu-id="22b17-108">.NET Core est constitué du runtime et du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="22b17-108">.NET Core is made up of the runtime and the SDK.</span></span> <span data-ttu-id="22b17-109">Le runtime est utilisé pour exécuter une application .NET Core et peut ou ne peut pas être inclus avec l’application.</span><span class="sxs-lookup"><span data-stu-id="22b17-109">The runtime is used to run a .NET Core app and may or may not be included with the app.</span></span> <span data-ttu-id="22b17-110">Le kit de développement logiciel (SDK) est utilisé pour créer des applications et des bibliothèques .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22b17-110">The SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="22b17-111">Le Runtime .NET Core est toujours installé avec le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="22b17-111">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="22b17-112">La dernière version de .NET Core est 3,1.</span><span class="sxs-lookup"><span data-stu-id="22b17-112">The latest version of .NET Core is 3.1.</span></span>

> [!div class="button"]
> [<span data-ttu-id="22b17-113">Télécharger .NET Core</span><span class="sxs-lookup"><span data-stu-id="22b17-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="22b17-114">Versions prises en charge</span><span class="sxs-lookup"><span data-stu-id="22b17-114">Supported releases</span></span>

<span data-ttu-id="22b17-115">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions de macOS sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="22b17-115">The following table is a list of currently supported .NET Core releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="22b17-116">Ces versions restent prises en charge soit la version de [.net Core atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="22b17-116">These versions remain supported either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="22b17-117">Une ✔️ indique que la version de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="22b17-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="22b17-118">Une ❌ indique que la version de .net Core n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="22b17-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="22b17-119">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="22b17-119">Operating System</span></span>          | <span data-ttu-id="22b17-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="22b17-120">.NET Core 2.1</span></span> | <span data-ttu-id="22b17-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="22b17-121">.NET Core 3.1</span></span> | <span data-ttu-id="22b17-122">Version préliminaire de .NET 5</span><span class="sxs-lookup"><span data-stu-id="22b17-122">.NET 5 Preview</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="22b17-123">macOS 10,15 « Catalina »</span><span class="sxs-lookup"><span data-stu-id="22b17-123">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="22b17-124">✔️ 2,1 ([notes de publication][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="22b17-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="22b17-125">✔️ 3,1 ([notes de publication][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="22b17-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="22b17-126">✔️ 5,0 Preview ([notes de publication][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="22b17-126">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="22b17-127">macOS 10,14 « Mojave »</span><span class="sxs-lookup"><span data-stu-id="22b17-127">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="22b17-128">✔️ 2,1 ([notes de publication][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="22b17-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="22b17-129">✔️ 3,1 ([notes de publication][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="22b17-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="22b17-130">✔️ 5,0 Preview ([notes de publication][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="22b17-130">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="22b17-131">macOS 10,13 « High Sierra »</span><span class="sxs-lookup"><span data-stu-id="22b17-131">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="22b17-132">✔️ 2,1 ([notes de publication][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="22b17-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="22b17-133">✔️ 3,1 ([notes de publication][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="22b17-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="22b17-134">✔️ 5,0 Preview ([notes de publication][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="22b17-134">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="22b17-135">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="22b17-135">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="22b17-136">✔️ 2,1 ([notes de publication][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="22b17-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="22b17-137">❌3,1 ([notes de publication][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="22b17-137">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="22b17-138">❌5,0 Preview ([notes de publication][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="22b17-138">❌ 5.0 Preview ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="22b17-139">Mises en production non prises en charge</span><span class="sxs-lookup"><span data-stu-id="22b17-139">Unsupported releases</span></span>

<span data-ttu-id="22b17-140">Les versions suivantes de .NET Core ne sont ❌ plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="22b17-140">The following versions of .NET Core are ❌ no longer supported.</span></span> <span data-ttu-id="22b17-141">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="22b17-141">The downloads for these still remain published:</span></span>

- <span data-ttu-id="22b17-142">3,0 ([notes de publication][release-notes-30])</span><span class="sxs-lookup"><span data-stu-id="22b17-142">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="22b17-143">2,2 ([notes de publication][release-notes-22])</span><span class="sxs-lookup"><span data-stu-id="22b17-143">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="22b17-144">2,0 ([notes de publication][release-notes-20])</span><span class="sxs-lookup"><span data-stu-id="22b17-144">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="22b17-145">Informations d’exécution</span><span class="sxs-lookup"><span data-stu-id="22b17-145">Runtime information</span></span>

<span data-ttu-id="22b17-146">Le runtime est utilisé pour exécuter des applications créées avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22b17-146">The runtime is used to run apps created with .NET Core.</span></span> <span data-ttu-id="22b17-147">Quand un auteur d’application publie une application, il peut inclure le Runtime avec son application.</span><span class="sxs-lookup"><span data-stu-id="22b17-147">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="22b17-148">Si elles n’incluent pas le runtime, c’est à l’utilisateur d’installer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="22b17-148">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="22b17-149">Il existe trois runtimes différents que vous pouvez installer sur macOS :</span><span class="sxs-lookup"><span data-stu-id="22b17-149">There are three different runtimes you can install on macOS:</span></span>

<span data-ttu-id="22b17-150">*Runtime ASP.NET Core*</span><span class="sxs-lookup"><span data-stu-id="22b17-150">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="22b17-151">Exécute ASP.NET Core applications.</span><span class="sxs-lookup"><span data-stu-id="22b17-151">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="22b17-152">Comprend le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22b17-152">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="22b17-153">*Runtime .NET Core*</span><span class="sxs-lookup"><span data-stu-id="22b17-153">*.NET Core runtime*</span></span>\
<span data-ttu-id="22b17-154">Ce Runtime est le runtime le plus simple et n’inclut pas d’autre Runtime.</span><span class="sxs-lookup"><span data-stu-id="22b17-154">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="22b17-155">Il est fortement recommandé d’installer *ASP.net Core Runtime* pour une meilleure compatibilité avec les applications .net core.</span><span class="sxs-lookup"><span data-stu-id="22b17-155">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET Core apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="22b17-156">Télécharger le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="22b17-156">Download .NET Core Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="22b17-157">Informations sur le SDK</span><span class="sxs-lookup"><span data-stu-id="22b17-157">SDK information</span></span>

<span data-ttu-id="22b17-158">Le kit de développement logiciel (SDK) est utilisé pour créer et publier des applications et des bibliothèques .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22b17-158">The SDK is used to build and publish .NET Core apps and libraries.</span></span> <span data-ttu-id="22b17-159">L’installation du kit de développement logiciel (SDK) comprend les deux [runtimes](#runtime-information): ASP.net Core et .net core.</span><span class="sxs-lookup"><span data-stu-id="22b17-159">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET Core.</span></span>

> [!div class="button"]
> [<span data-ttu-id="22b17-160">Télécharger le kit de développement logiciel (SDK) .NET Core</span><span class="sxs-lookup"><span data-stu-id="22b17-160">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a><span data-ttu-id="22b17-161">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="22b17-161">Dependencies</span></span>

<span data-ttu-id="22b17-162">.NET Core est pris en charge sur les versions macOS suivantes :</span><span class="sxs-lookup"><span data-stu-id="22b17-162">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="22b17-163">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="22b17-163">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="22b17-164">Version de .NET Core</span><span class="sxs-lookup"><span data-stu-id="22b17-164">.NET Core Version</span></span> | <span data-ttu-id="22b17-165">macOS</span><span class="sxs-lookup"><span data-stu-id="22b17-165">macOS</span></span>                 | <span data-ttu-id="22b17-166">Architectures</span><span class="sxs-lookup"><span data-stu-id="22b17-166">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="22b17-167">3.1</span><span class="sxs-lookup"><span data-stu-id="22b17-167">3.1</span></span>               | <span data-ttu-id="22b17-168">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="22b17-168">High Sierra (10.13+)</span></span>  | <span data-ttu-id="22b17-169">x64</span><span class="sxs-lookup"><span data-stu-id="22b17-169">x64</span></span> | [<span data-ttu-id="22b17-170">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="22b17-170">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="22b17-171">3.0</span><span class="sxs-lookup"><span data-stu-id="22b17-171">3.0</span></span>               | <span data-ttu-id="22b17-172">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="22b17-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="22b17-173">x64</span><span class="sxs-lookup"><span data-stu-id="22b17-173">x64</span></span> | [<span data-ttu-id="22b17-174">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="22b17-174">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="22b17-175">2.2</span><span class="sxs-lookup"><span data-stu-id="22b17-175">2.2</span></span>               | <span data-ttu-id="22b17-176">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="22b17-176">Sierra (10.12+)</span></span>       | <span data-ttu-id="22b17-177">x64</span><span class="sxs-lookup"><span data-stu-id="22b17-177">x64</span></span> | [<span data-ttu-id="22b17-178">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="22b17-178">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="22b17-179">2.1</span><span class="sxs-lookup"><span data-stu-id="22b17-179">2.1</span></span>               | <span data-ttu-id="22b17-180">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="22b17-180">Sierra (10.12+)</span></span>       | <span data-ttu-id="22b17-181">x64</span><span class="sxs-lookup"><span data-stu-id="22b17-181">x64</span></span> | [<span data-ttu-id="22b17-182">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="22b17-182">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="22b17-183">À partir de macOS Catalina (version 10,15), tous les logiciels générés après le 1er juin 2019, qui sont distribués avec l’ID de développeur, doivent être certifiés.</span><span class="sxs-lookup"><span data-stu-id="22b17-183">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="22b17-184">Cette exigence s’applique au Runtime .NET Core, kit SDK .NET Core et aux logiciels créés avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22b17-184">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="22b17-185">Les programmes d’installation de .NET Core (Runtime et SDK) versions 3,1, 3,0 et 2,1 ont été certifiés depuis le 18 février 2020.</span><span class="sxs-lookup"><span data-stu-id="22b17-185">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="22b17-186">Les versions antérieures publiées ne sont pas certifiées.</span><span class="sxs-lookup"><span data-stu-id="22b17-186">Prior released versions aren't notarized.</span></span> <span data-ttu-id="22b17-187">Si vous exécutez une application non authentifiée, une erreur semblable à l’image suivante s’affiche :</span><span class="sxs-lookup"><span data-stu-id="22b17-187">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![alerte de notaire Catalina macOS](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="22b17-189">Pour plus d’informations sur la façon dont l’application de la notaire affecte .NET Core (et vos applications .NET Core), consultez [utilisation de la méthode de notaire Catalina MacOS](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="22b17-189">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="22b17-190">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="22b17-190">libgdiplus</span></span>

<span data-ttu-id="22b17-191">Les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* nécessitent l’installation de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="22b17-191">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="22b17-192">Pour obtenir facilement des libgdiplus, vous pouvez utiliser le gestionnaire de package [Homebrew (« Brass »)](https://brew.sh/) pour MacOS.</span><span class="sxs-lookup"><span data-stu-id="22b17-192">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="22b17-193">Après l’installation de la commande *infuse*, installez libgdiplus en exécutant les commandes suivantes à une invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="22b17-193">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="22b17-194">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="22b17-194">Install with an installer</span></span>

<span data-ttu-id="22b17-195">macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="22b17-195">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="22b17-196">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="22b17-196">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="22b17-197">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="22b17-197">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="22b17-198">Comme alternative aux programmes d’installation macOS pour .NET Core, vous pouvez télécharger et installer manuellement le kit de développement logiciel (SDK) et le Runtime.</span><span class="sxs-lookup"><span data-stu-id="22b17-198">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="22b17-199">L’installation manuelle est généralement effectuée dans le cadre du test d’intégration continue.</span><span class="sxs-lookup"><span data-stu-id="22b17-199">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="22b17-200">Pour un développeur ou un utilisateur, il est généralement préférable d’utiliser un [programme d’installation](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="22b17-200">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="22b17-201">Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="22b17-201">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="22b17-202">Tout d’abord, téléchargez une version **binaire** pour le kit de développement logiciel (SDK) ou le runtime à partir de l’un des sites suivants :</span><span class="sxs-lookup"><span data-stu-id="22b17-202">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="22b17-203">Téléchargements de ✔️ [.net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="22b17-203">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="22b17-204">✔️ [téléchargements .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="22b17-204">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="22b17-205">✔️ [téléchargements .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="22b17-205">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="22b17-206">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="22b17-206">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="22b17-207">Ensuite, extrayez le fichier téléchargé et utilisez la `export` commande pour définir les variables utilisées par .net Core, puis vérifiez que .net Core se trouve dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="22b17-207">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="22b17-208">Pour extraire le runtime et rendre les commandes CLI .NET Core disponibles sur le terminal, commencez par télécharger une version binaire .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22b17-208">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="22b17-209">Ensuite, ouvrez un terminal et exécutez les commandes suivantes à partir du répertoire dans lequel le fichier a été enregistré.</span><span class="sxs-lookup"><span data-stu-id="22b17-209">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="22b17-210">Le nom du fichier d’archive peut être différent en fonction de ce que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="22b17-210">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="22b17-211">**Utilisez la commande suivante pour extraire le runtime**:</span><span class="sxs-lookup"><span data-stu-id="22b17-211">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.5-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="22b17-212">**Utilisez la commande suivante pour extraire le kit de développement logiciel (SDK)**:</span><span class="sxs-lookup"><span data-stu-id="22b17-212">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="22b17-213">Les `export` commandes précédentes rendent uniquement les commandes CLI .net Core disponibles pour la session Terminal dans laquelle elles ont été exécutées.</span><span class="sxs-lookup"><span data-stu-id="22b17-213">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="22b17-214">Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes.</span><span class="sxs-lookup"><span data-stu-id="22b17-214">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="22b17-215">Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent.</span><span class="sxs-lookup"><span data-stu-id="22b17-215">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="22b17-216">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="22b17-216">For example:</span></span>
>
> - <span data-ttu-id="22b17-217">**Interpréteur**de commandes bash : *~/. bash_profile*, *~ fichier/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="22b17-217">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="22b17-218">**Shell Korn**: *~/.kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="22b17-218">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="22b17-219">**Z Shell**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="22b17-219">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="22b17-220">Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l' `PATH` instruction existante.</span><span class="sxs-lookup"><span data-stu-id="22b17-220">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="22b17-221">Si aucune `PATH` instruction n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="22b17-221">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="22b17-222">Ajoutez également `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="22b17-222">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="22b17-223">Cette approche vous permet d’installer différentes versions dans des emplacements distincts et de choisir explicitement celle qui doit être utilisée par l’application.</span><span class="sxs-lookup"><span data-stu-id="22b17-223">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="22b17-224">Installer avec Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="22b17-224">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="22b17-225">Visual Studio pour Mac installe le kit SDK .NET Core lorsque la charge de travail **.net Core** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="22b17-225">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="22b17-226">Pour commencer à utiliser le développement .NET Core sur macOS, consultez [installer Visual Studio 2019 pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="22b17-226">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="22b17-227">Pour la version la plus récente, .NET Core 3,1, vous devez utiliser le Visual Studio pour Mac 8,4 preview.</span><span class="sxs-lookup"><span data-stu-id="22b17-227">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="22b17-228">[![macOS Visual Studio 2019 pour Mac avec la charge de travail .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="22b17-228">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="22b17-229">Installer en même temps que Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="22b17-229">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="22b17-230">Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau.</span><span class="sxs-lookup"><span data-stu-id="22b17-230">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="22b17-231">Visual Studio Code est disponible pour Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="22b17-231">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="22b17-232">Même si Visual Studio Code n’est pas fourni avec un programme d’installation automatisé de .NET Core, comme Visual Studio, l’ajout de la prise en charge de .NET Core est simple.</span><span class="sxs-lookup"><span data-stu-id="22b17-232">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="22b17-233">[Téléchargez et installez Visual Studio code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="22b17-233">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="22b17-234">[Téléchargez et installez le kit SDK .net Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="22b17-234">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="22b17-235">[Installez l’extension C# à partir de la place de marché Visual Studio code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="22b17-235">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="22b17-236">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="22b17-236">Install with bash automation</span></span>

<span data-ttu-id="22b17-237">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="22b17-237">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="22b17-238">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="22b17-238">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="22b17-239">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="22b17-239">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="22b17-240">Vous pouvez choisir une version spécifique en spécifiant le `current` commutateur.</span><span class="sxs-lookup"><span data-stu-id="22b17-240">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="22b17-241">Incluez le `runtime` commutateur pour installer un Runtime.</span><span class="sxs-lookup"><span data-stu-id="22b17-241">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="22b17-242">Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="22b17-242">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="22b17-243">La commande ci-dessus installe le runtime ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="22b17-243">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="22b17-244">Le runtime ASP.NET Core comprend également le Runtime .NET Core standard.</span><span class="sxs-lookup"><span data-stu-id="22b17-244">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="22b17-245">Docker</span><span class="sxs-lookup"><span data-stu-id="22b17-245">Docker</span></span>

<span data-ttu-id="22b17-246">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="22b17-246">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="22b17-247">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="22b17-247">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="22b17-248">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="22b17-248">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="22b17-249">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="22b17-249">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="22b17-250">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="22b17-250">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="22b17-251">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="22b17-251">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="22b17-252">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="22b17-252">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="22b17-253">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="22b17-253">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="22b17-254">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="22b17-254">Next steps</span></span>

- <span data-ttu-id="22b17-255">[Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="22b17-255">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="22b17-256">[Utilisation de la notaire Catalina MacOS](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="22b17-256">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="22b17-257">[Didacticiel : prise en main de MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="22b17-257">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="22b17-258">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="22b17-258">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="22b17-259">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="22b17-259">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
