---
title: Installer .NET sur macOS
description: En savoir plus sur les versions de macOS sur lesquelles vous pouvez installer .NET.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: b1434938a8e8e81da81e495a6b99e6c99467aae1
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009356"
---
# <a name="install-net-on-macos"></a><span data-ttu-id="c5114-103">Installer .NET sur macOS</span><span class="sxs-lookup"><span data-stu-id="c5114-103">Install .NET on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [Installer sur Windows](windows.md)
> - [Installer sur macOS](macos.md)
> - [Installer sur Linux](linux.md)

<span data-ttu-id="c5114-107">Dans cet article, vous allez apprendre à installer .NET sur macOS.</span><span class="sxs-lookup"><span data-stu-id="c5114-107">In this article, you'll learn how to install .NET on macOS.</span></span> <span data-ttu-id="c5114-108">.NET est constitué du runtime et du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="c5114-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="c5114-109">Le runtime est utilisé pour exécuter une application .NET et peut ou non être inclus avec l’application.</span><span class="sxs-lookup"><span data-stu-id="c5114-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="c5114-110">Le kit de développement logiciel (SDK) est utilisé pour créer des applications et des bibliothèques .NET.</span><span class="sxs-lookup"><span data-stu-id="c5114-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="c5114-111">Le Runtime .NET est toujours installé avec le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="c5114-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="c5114-112">La dernière version de .NET est 5,0.</span><span class="sxs-lookup"><span data-stu-id="c5114-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="c5114-113">Télécharger .NET Core</span><span class="sxs-lookup"><span data-stu-id="c5114-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="c5114-114">Versions prises en charge</span><span class="sxs-lookup"><span data-stu-id="c5114-114">Supported releases</span></span>

<span data-ttu-id="c5114-115">Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de macOS sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c5114-115">The following table is a list of currently supported .NET releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="c5114-116">Ces versions restent prises en charge soit la version de [.net atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="c5114-116">These versions remain supported either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="c5114-117">Une ✔️ indique que la version de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="c5114-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="c5114-118">Une ❌ indique que la version de .net Core n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="c5114-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="c5114-119">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="c5114-119">Operating System</span></span>          | <span data-ttu-id="c5114-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c5114-120">.NET Core 2.1</span></span> | <span data-ttu-id="c5114-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c5114-121">.NET Core 3.1</span></span> | <span data-ttu-id="c5114-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="c5114-122">.NET 5.0</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="c5114-123">macOS 11,0 « Big sur »</span><span class="sxs-lookup"><span data-stu-id="c5114-123">macOS 11.0 "Big Sur"</span></span>        | <span data-ttu-id="c5114-124">✔️ 2,1 ([notes de publication][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="c5114-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="c5114-125">✔️ 3,1 ([notes de publication][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="c5114-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="c5114-126">✔️ 5,0 ([notes de publication][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="c5114-126">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="c5114-127">macOS 10.15 « Catalina »</span><span class="sxs-lookup"><span data-stu-id="c5114-127">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="c5114-128">✔️ 2,1 ([notes de publication][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="c5114-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="c5114-129">✔️ 3,1 ([notes de publication][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="c5114-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="c5114-130">✔️ 5,0 ([notes de publication][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="c5114-130">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="c5114-131">macOS 10.14 « Mojave »</span><span class="sxs-lookup"><span data-stu-id="c5114-131">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="c5114-132">✔️ 2,1 ([notes de publication][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="c5114-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="c5114-133">✔️ 3,1 ([notes de publication][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="c5114-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="c5114-134">✔️ 5,0 ([notes de publication][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="c5114-134">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="c5114-135">macOS 10.13 « High Sierra »</span><span class="sxs-lookup"><span data-stu-id="c5114-135">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="c5114-136">✔️ 2,1 ([notes de publication][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="c5114-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="c5114-137">✔️ 3,1 ([notes de publication][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="c5114-137">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="c5114-138">✔️ 5,0 ([notes de publication][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="c5114-138">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="c5114-139">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="c5114-139">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="c5114-140">✔️ 2,1 ([notes de publication][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="c5114-140">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="c5114-141">❌ 3,1 ([notes de publication][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="c5114-141">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="c5114-142">❌ 5,0 ([notes de publication][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="c5114-142">❌ 5.0 ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="c5114-143">Mises en production non prises en charge</span><span class="sxs-lookup"><span data-stu-id="c5114-143">Unsupported releases</span></span>

<span data-ttu-id="c5114-144">Les versions suivantes de .NET ne sont ❌ plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c5114-144">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="c5114-145">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="c5114-145">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c5114-146">3,0 ([notes de publication][release-notes-30])</span><span class="sxs-lookup"><span data-stu-id="c5114-146">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="c5114-147">2,2 ([notes de publication][release-notes-22])</span><span class="sxs-lookup"><span data-stu-id="c5114-147">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="c5114-148">2,0 ([notes de publication][release-notes-20])</span><span class="sxs-lookup"><span data-stu-id="c5114-148">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="c5114-149">Informations d’exécution</span><span class="sxs-lookup"><span data-stu-id="c5114-149">Runtime information</span></span>

<span data-ttu-id="c5114-150">Le runtime est utilisé pour exécuter des applications créées avec .NET.</span><span class="sxs-lookup"><span data-stu-id="c5114-150">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="c5114-151">Quand un auteur d’application publie une application, il peut inclure le Runtime avec son application.</span><span class="sxs-lookup"><span data-stu-id="c5114-151">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="c5114-152">Si elles n’incluent pas le runtime, c’est à l’utilisateur d’installer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="c5114-152">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="c5114-153">Il existe trois runtimes différents que vous pouvez installer sur macOS :</span><span class="sxs-lookup"><span data-stu-id="c5114-153">There are three different runtimes you can install on macOS:</span></span>

<span data-ttu-id="c5114-154">*Runtime ASP.NET Core*</span><span class="sxs-lookup"><span data-stu-id="c5114-154">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="c5114-155">Exécute ASP.NET Core applications.</span><span class="sxs-lookup"><span data-stu-id="c5114-155">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="c5114-156">Comprend le Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="c5114-156">Includes the .NET runtime.</span></span>

<span data-ttu-id="c5114-157">*Runtime .NET*</span><span class="sxs-lookup"><span data-stu-id="c5114-157">*.NET runtime*</span></span>\
<span data-ttu-id="c5114-158">Ce Runtime est le runtime le plus simple et n’inclut pas d’autre Runtime.</span><span class="sxs-lookup"><span data-stu-id="c5114-158">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="c5114-159">Il est fortement recommandé d’installer *ASP.net Core Runtime* pour une meilleure compatibilité avec les applications .net.</span><span class="sxs-lookup"><span data-stu-id="c5114-159">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="c5114-160">Télécharger le Runtime .NET</span><span class="sxs-lookup"><span data-stu-id="c5114-160">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="c5114-161">Informations sur le SDK</span><span class="sxs-lookup"><span data-stu-id="c5114-161">SDK information</span></span>

<span data-ttu-id="c5114-162">Le kit de développement logiciel (SDK) est utilisé pour générer et publier des applications et des bibliothèques .NET.</span><span class="sxs-lookup"><span data-stu-id="c5114-162">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="c5114-163">L’installation du kit de développement logiciel (SDK) comprend les deux [runtimes](#runtime-information): ASP.net Core et .net.</span><span class="sxs-lookup"><span data-stu-id="c5114-163">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="c5114-164">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="c5114-164">Dependencies</span></span>

<span data-ttu-id="c5114-165">.NET est pris en charge sur les versions macOS suivantes :</span><span class="sxs-lookup"><span data-stu-id="c5114-165">.NET is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="c5114-166">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="c5114-166">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="c5114-167">Version de .NET Core</span><span class="sxs-lookup"><span data-stu-id="c5114-167">.NET Core Version</span></span> | <span data-ttu-id="c5114-168">macOS</span><span class="sxs-lookup"><span data-stu-id="c5114-168">macOS</span></span>                 | <span data-ttu-id="c5114-169">Architectures</span><span class="sxs-lookup"><span data-stu-id="c5114-169">Architectures</span></span> | <span data-ttu-id="c5114-170">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="c5114-170">More information</span></span>    |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="c5114-171">5.0</span><span class="sxs-lookup"><span data-stu-id="c5114-171">5.0</span></span>               | <span data-ttu-id="c5114-172">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="c5114-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="c5114-173">x64</span><span class="sxs-lookup"><span data-stu-id="c5114-173">x64</span></span> | [<span data-ttu-id="c5114-174">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="c5114-174">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) |
| <span data-ttu-id="c5114-175">3.1</span><span class="sxs-lookup"><span data-stu-id="c5114-175">3.1</span></span>               | <span data-ttu-id="c5114-176">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="c5114-176">High Sierra (10.13+)</span></span>  | <span data-ttu-id="c5114-177">x64</span><span class="sxs-lookup"><span data-stu-id="c5114-177">x64</span></span> | [<span data-ttu-id="c5114-178">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="c5114-178">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="c5114-179">3.0</span><span class="sxs-lookup"><span data-stu-id="c5114-179">3.0</span></span>               | <span data-ttu-id="c5114-180">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="c5114-180">High Sierra (10.13+)</span></span>  | <span data-ttu-id="c5114-181">x64</span><span class="sxs-lookup"><span data-stu-id="c5114-181">x64</span></span> | [<span data-ttu-id="c5114-182">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="c5114-182">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="c5114-183">2.2</span><span class="sxs-lookup"><span data-stu-id="c5114-183">2.2</span></span>               | <span data-ttu-id="c5114-184">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="c5114-184">Sierra (10.12+)</span></span>       | <span data-ttu-id="c5114-185">x64</span><span class="sxs-lookup"><span data-stu-id="c5114-185">x64</span></span> | [<span data-ttu-id="c5114-186">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="c5114-186">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="c5114-187">2.1</span><span class="sxs-lookup"><span data-stu-id="c5114-187">2.1</span></span>               | <span data-ttu-id="c5114-188">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="c5114-188">Sierra (10.12+)</span></span>       | <span data-ttu-id="c5114-189">x64</span><span class="sxs-lookup"><span data-stu-id="c5114-189">x64</span></span> | [<span data-ttu-id="c5114-190">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="c5114-190">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="c5114-191">À partir de macOS Catalina (version 10,15), tous les logiciels générés après le 1er juin 2019, qui sont distribués avec l’ID de développeur, doivent être certifiés.</span><span class="sxs-lookup"><span data-stu-id="c5114-191">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="c5114-192">Cette exigence s’applique au Runtime .NET, au kit de développement logiciel (SDK) .NET et aux logiciels créés avec .NET.</span><span class="sxs-lookup"><span data-stu-id="c5114-192">This requirement applies to the .NET runtime, .NET SDK, and software created with .NET.</span></span>

<span data-ttu-id="c5114-193">Les programmes d’installation du runtime et du SDK pour .NET 5,0 et .NET Core 3,1, 3,0 et 2,1 ont été certifiés depuis le 18 février 2020.</span><span class="sxs-lookup"><span data-stu-id="c5114-193">The runtime and SDK installers for .NET 5.0 and .NET Core 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="c5114-194">Les versions antérieures publiées ne sont pas certifiées.</span><span class="sxs-lookup"><span data-stu-id="c5114-194">Prior released versions aren't notarized.</span></span> <span data-ttu-id="c5114-195">Si vous exécutez une application non authentifiée, une erreur semblable à l’image suivante s’affiche :</span><span class="sxs-lookup"><span data-stu-id="c5114-195">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![alerte de notaire Catalina macOS](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="c5114-197">Pour plus d’informations sur la façon dont l’application de la notaire affecte .NET (et vos applications .NET), consultez [utilisation de la méthode de notaire Catalina MacOS](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="c5114-197">For more information about how enforced-notarization affects .NET (and your .NET apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="c5114-198">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="c5114-198">libgdiplus</span></span>

<span data-ttu-id="c5114-199">Les applications .NET qui utilisent l’assembly *System. Drawing. Common* nécessitent l’installation de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="c5114-199">.NET applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="c5114-200">Pour obtenir facilement des libgdiplus, vous pouvez utiliser le gestionnaire de package [Homebrew (« Brass »)](https://brew.sh/) pour MacOS.</span><span class="sxs-lookup"><span data-stu-id="c5114-200">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="c5114-201">Après l’installation de la commande *infuse*, installez libgdiplus en exécutant les commandes suivantes à une invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="c5114-201">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="c5114-202">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="c5114-202">Install with an installer</span></span>

<span data-ttu-id="c5114-203">macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le kit de développement logiciel (SDK) .NET 5,0 :</span><span class="sxs-lookup"><span data-stu-id="c5114-203">macOS has standalone installers that can be used to install the .NET 5.0 SDK:</span></span>

- [<span data-ttu-id="c5114-204">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="c5114-204">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/5.0)

## <a name="download-and-manually-install"></a><span data-ttu-id="c5114-205">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="c5114-205">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="c5114-206">Comme alternative aux programmes d’installation macOS pour .NET, vous pouvez télécharger et installer manuellement le kit de développement logiciel (SDK) et le Runtime.</span><span class="sxs-lookup"><span data-stu-id="c5114-206">As an alternative to the macOS installers for .NET, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="c5114-207">L’installation manuelle est généralement effectuée dans le cadre du test d’intégration continue.</span><span class="sxs-lookup"><span data-stu-id="c5114-207">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="c5114-208">Pour un développeur ou un utilisateur, il est généralement préférable d’utiliser un [programme d’installation](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="c5114-208">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="c5114-209">Si vous installez le kit de développement logiciel (SDK) .NET, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="c5114-209">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="c5114-210">Tout d’abord, téléchargez une version **binaire** pour le kit de développement logiciel (SDK) ou le runtime à partir de l’un des sites suivants :</span><span class="sxs-lookup"><span data-stu-id="c5114-210">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="c5114-211">[téléchargements .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0) ✔️</span><span class="sxs-lookup"><span data-stu-id="c5114-211">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="c5114-212">✔️ [téléchargements .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="c5114-212">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="c5114-213">✔️ [téléchargements .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="c5114-213">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="c5114-214">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="c5114-214">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="c5114-215">Ensuite, extrayez le fichier téléchargé et utilisez la `export` commande pour définir les variables utilisées par .net, puis vérifiez que .net est dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="c5114-215">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="c5114-216">Pour extraire le runtime et rendre les commandes de l’interface de commande .NET CLI disponibles sur le terminal, commencez par télécharger une version binaire .NET.</span><span class="sxs-lookup"><span data-stu-id="c5114-216">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="c5114-217">Ensuite, ouvrez un terminal et exécutez les commandes suivantes à partir du répertoire dans lequel le fichier a été enregistré.</span><span class="sxs-lookup"><span data-stu-id="c5114-217">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="c5114-218">Le nom du fichier d’archive peut être différent en fonction de ce que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="c5114-218">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="c5114-219">**Utilisez la commande suivante pour extraire le runtime**:</span><span class="sxs-lookup"><span data-stu-id="c5114-219">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="c5114-220">**Utilisez la commande suivante pour extraire le kit de développement logiciel (SDK)**:</span><span class="sxs-lookup"><span data-stu-id="c5114-220">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="c5114-221">Les `export` commandes précédentes rendent uniquement les commandes de l’interface de commande .net CLI disponibles pour la session Terminal dans laquelle elle a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="c5114-221">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="c5114-222">Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes.</span><span class="sxs-lookup"><span data-stu-id="c5114-222">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="c5114-223">Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent.</span><span class="sxs-lookup"><span data-stu-id="c5114-223">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="c5114-224">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c5114-224">For example:</span></span>
>
> - <span data-ttu-id="c5114-225">**Interpréteur** de commandes bash : *~/.bash_profile*, *~ fichier/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="c5114-225">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="c5114-226">**Shell Korn**: *~/.kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="c5114-226">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="c5114-227">**Z Shell**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="c5114-227">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="c5114-228">Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l' `PATH` instruction existante.</span><span class="sxs-lookup"><span data-stu-id="c5114-228">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="c5114-229">Si aucune `PATH` instruction n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="c5114-229">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="c5114-230">Ajoutez également `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="c5114-230">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="c5114-231">Cette approche vous permet d’installer différentes versions dans des emplacements distincts et de choisir explicitement celle qui doit être utilisée par l’application.</span><span class="sxs-lookup"><span data-stu-id="c5114-231">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="c5114-232">Installer avec Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="c5114-232">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="c5114-233">Visual Studio pour Mac installe le kit de développement logiciel (SDK) .NET lorsque la charge de travail **.net** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="c5114-233">Visual Studio for Mac installs the .NET SDK when the **.NET** workload is selected.</span></span> <span data-ttu-id="c5114-234">Pour commencer à utiliser le développement .NET sur macOS, consultez [installer Visual Studio 2019 pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="c5114-234">To get started with .NET development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

| <span data-ttu-id="c5114-235">Version du Kit de développement logiciel (SDK) .NET</span><span class="sxs-lookup"><span data-stu-id="c5114-235">.NET SDK version</span></span>      | <span data-ttu-id="c5114-236">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c5114-236">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="c5114-237">5.0</span><span class="sxs-lookup"><span data-stu-id="c5114-237">5.0</span></span>                   | <span data-ttu-id="c5114-238">Visual Studio 2019 pour Mac version 8,8 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c5114-238">Visual Studio 2019 for Mac version 8.8 or higher.</span></span> |
| <span data-ttu-id="c5114-239">3.1</span><span class="sxs-lookup"><span data-stu-id="c5114-239">3.1</span></span>                   | <span data-ttu-id="c5114-240">Visual Studio 2019 pour Mac version 8,4 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c5114-240">Visual Studio 2019 for Mac version 8.4 or higher.</span></span> |
| <span data-ttu-id="c5114-241">2.1</span><span class="sxs-lookup"><span data-stu-id="c5114-241">2.1</span></span>                   | <span data-ttu-id="c5114-242">Visual Studio 2019 pour Mac version 8,0 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c5114-242">Visual Studio 2019 for Mac version 8.0 or higher.</span></span> |

<span data-ttu-id="c5114-243">[![fonctionnalité de charge de travail de macOS Visual Studio 2019 pour Mac avec .NET](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="c5114-243">[![macOS Visual Studio 2019 for Mac with .NET workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="c5114-244">Installer en même temps que Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c5114-244">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="c5114-245">Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau.</span><span class="sxs-lookup"><span data-stu-id="c5114-245">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="c5114-246">Visual Studio Code est disponible pour Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="c5114-246">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="c5114-247">Même si Visual Studio Code n’est pas fourni avec un programme d’installation automatisé de .NET, comme Visual Studio, l’ajout de la prise en charge de .NET est simple.</span><span class="sxs-lookup"><span data-stu-id="c5114-247">While Visual Studio Code doesn't come with an automated .NET installer like Visual Studio does, adding .NET support is simple.</span></span>

01. <span data-ttu-id="c5114-248">[Téléchargez et installez Visual Studio code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="c5114-248">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="c5114-249">[Téléchargez et installez le kit de développement logiciel (SDK) .net](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="c5114-249">[Download and install the .NET SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="c5114-250">[Installez l’extension C# à partir de la place de marché Visual Studio code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="c5114-250">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="c5114-251">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="c5114-251">Install with bash automation</span></span>

<span data-ttu-id="c5114-252">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="c5114-252">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="c5114-253">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="c5114-253">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="c5114-254">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="c5114-254">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="c5114-255">Vous pouvez choisir une version spécifique en spécifiant le `current` commutateur.</span><span class="sxs-lookup"><span data-stu-id="c5114-255">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="c5114-256">Incluez le `runtime` commutateur pour installer un Runtime.</span><span class="sxs-lookup"><span data-stu-id="c5114-256">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="c5114-257">Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](./windows.md).</span><span class="sxs-lookup"><span data-stu-id="c5114-257">Otherwise, the script installs the [SDK](./windows.md).</span></span>

```bash
./dotnet-install.sh --channel 5.0 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="c5114-258">La commande précédente installe le runtime ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="c5114-258">The previous command installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="c5114-259">Le runtime ASP.NET Core comprend également le Runtime .NET standard.</span><span class="sxs-lookup"><span data-stu-id="c5114-259">The ASP.NET Core runtime also includes the standard .NET runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="c5114-260">Docker</span><span class="sxs-lookup"><span data-stu-id="c5114-260">Docker</span></span>

<span data-ttu-id="c5114-261">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="c5114-261">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="c5114-262">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="c5114-262">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="c5114-263">.NET peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="c5114-263">.NET can run in a Docker container.</span></span> <span data-ttu-id="c5114-264">Les images officielles de la station d’accueil .NET sont publiées dans le Container Registry Microsoft et sont détectables dans le [référentiel du hub d’ancrage Microsoft .net Core](https://hub.docker.com/_/microsoft-dotnet/).</span><span class="sxs-lookup"><span data-stu-id="c5114-264">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet/).</span></span> <span data-ttu-id="c5114-265">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="c5114-265">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="c5114-266">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="c5114-266">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="c5114-267">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-aspnet) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="c5114-267">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="c5114-268">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="c5114-268">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c5114-269">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="c5114-269">Next steps</span></span>

- <span data-ttu-id="c5114-270">[Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="c5114-270">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="c5114-271">[Utilisation de la notaire Catalina MacOS](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="c5114-271">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="c5114-272">[Didacticiel : prise en main de MacOS](../tutorials/with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="c5114-272">[Tutorial: Get started on macOS](../tutorials/with-visual-studio-mac.md).</span></span>
- <span data-ttu-id="c5114-273">[Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="c5114-273">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="c5114-274">[Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="c5114-274">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
