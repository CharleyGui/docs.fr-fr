---
title: Package de distribution .NET
description: Découvrez comment empaqueter, nommer et version .NET pour la distribution.
author: tmds
ms.date: 10/09/2019
ms.openlocfilehash: 93d040064eb739b3bd045fdb16b356732353ddc8
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216302"
---
# <a name="net-distribution-packaging"></a><span data-ttu-id="4c035-103">Package de distribution .NET</span><span class="sxs-lookup"><span data-stu-id="4c035-103">.NET distribution packaging</span></span>

<span data-ttu-id="4c035-104">Comme .NET 5 (et .NET Core) et les versions ultérieures sont disponibles sur de plus en plus de plateformes, il est utile de savoir comment empaqueter, nommer et créer des applications de version et des bibliothèques qui l’utilisent.</span><span class="sxs-lookup"><span data-stu-id="4c035-104">As .NET 5 (and .NET Core) and later versions become available on more and more platforms, it's useful to learn how to package, name, and version apps and libraries that use it.</span></span> <span data-ttu-id="4c035-105">De cette manière, les chargés de maintenance des packages pourront garantir une expérience cohérente quelle que soit la plateforme choisie par les utilisateurs pour exécuter .NET.</span><span class="sxs-lookup"><span data-stu-id="4c035-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="4c035-106">Cet article est utile pour les utilisateurs qui :</span><span class="sxs-lookup"><span data-stu-id="4c035-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="4c035-107">Tentative de génération de .NET à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="4c035-107">Attempting to build .NET from source.</span></span>
- <span data-ttu-id="4c035-108">Souhaitant apporter des modifications à l’interface CLI .NET qui pourraient avoir un impact sur la disposition ou les packages obtenus.</span><span class="sxs-lookup"><span data-stu-id="4c035-108">Wanting to make changes to the .NET CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="4c035-109">Disposition du disque</span><span class="sxs-lookup"><span data-stu-id="4c035-109">Disk layout</span></span>

<span data-ttu-id="4c035-110">Une fois installé, .NET est constitué de plusieurs composants qui sont disposés comme suit dans le système de fichiers :</span><span class="sxs-lookup"><span data-stu-id="4c035-110">When installed, .NET consists of several components that are laid out as follows in the file system:</span></span>

```
{dotnet_root}                                     (*)
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host                                          (*)
│   └── fxr                                       (*)
│       └── <fxr version>        (2)
├── sdk                                           (*)
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)              (*)
├── packs                                         (*)
│   ├── Microsoft.AspNetCore.App.Ref              (*)
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref                 (*)
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>          (*)
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref          (*)
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref                   (*)
│       └── <netstandard version>        (15)
├── shared                                        (*)
│   ├── Microsoft.NETCore.App                     (*)
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App                  (*)
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All                  (*)
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App              (*)
│       └── <desktop app version> (7)
└── templates                                     (*)
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="4c035-111">(1) **dotnet** L’hôte (également appelé « muxer ») a deux rôles distincts : activer un runtime pour lancer une application, et un SDK pour lui distribuer des commandes.</span><span class="sxs-lookup"><span data-stu-id="4c035-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="4c035-112">L’hôte est un fichier exécutable natif (`dotnet.exe`).</span><span class="sxs-lookup"><span data-stu-id="4c035-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="4c035-113">Alors qu’il n’y a qu’un seul hôte, la plupart des autres composants sont dans des répertoires avec version (2,3,5,6).</span><span class="sxs-lookup"><span data-stu-id="4c035-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="4c035-114">Cela signifie que plusieurs versions peuvent être présentes sur le système, car elles sont installées côte à côte.</span><span class="sxs-lookup"><span data-stu-id="4c035-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="4c035-115">(2) **Host/FXR/ \<fxr version>** contient la logique de résolution de l’infrastructure utilisée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="4c035-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="4c035-116">L’hôte utilise la dernière version de hostfxr qui est installée.</span><span class="sxs-lookup"><span data-stu-id="4c035-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="4c035-117">Le hostfxr est responsable de la sélection du runtime approprié lors de l’exécution d’une application .NET.</span><span class="sxs-lookup"><span data-stu-id="4c035-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET application.</span></span> <span data-ttu-id="4c035-118">Par exemple, une application générée pour .NET Core 2.0.0 utilise le runtime 2.0.5 quand il est disponible.</span><span class="sxs-lookup"><span data-stu-id="4c035-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="4c035-119">De même, hostfxr sélectionne le SDK approprié au cours du développement.</span><span class="sxs-lookup"><span data-stu-id="4c035-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="4c035-120">(3) **SDK/ \<sdk version>** le kit de développement logiciel (SDK) (également appelé « outils ») est un ensemble d’outils gérés servant à écrire et à créer des bibliothèques et des applications .net.</span><span class="sxs-lookup"><span data-stu-id="4c035-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET libraries and applications.</span></span> <span data-ttu-id="4c035-121">Le kit de développement logiciel (SDK) comprend l’interface de commande .NET, les compilateurs de langages managés, MSBuild, ainsi que les tâches et cibles de build associées, NuGet, les nouveaux modèles de projet, etc.</span><span class="sxs-lookup"><span data-stu-id="4c035-121">The SDK includes the .NET CLI, the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="4c035-122">(4) **sdk/NuGetFallbackFolder** contient un cache de packages NuGet utilisés par un SDK pendant l’opération de restauration, comme lors de l’exécution de `dotnet restore` ou `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="4c035-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build`.</span></span> <span data-ttu-id="4c035-123">Ce dossier est utilisé uniquement avant .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="4c035-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="4c035-124">Il ne peut pas être généré à partir de la source, car il contient des éléments binaires prégénérés à partir de `nuget.org` .</span><span class="sxs-lookup"><span data-stu-id="4c035-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="4c035-125">Le dossier **shared** contient des frameworks.</span><span class="sxs-lookup"><span data-stu-id="4c035-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="4c035-126">Un framework partagé fournit un ensemble de bibliothèques à un emplacement central, ce qui permet à différentes applications de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="4c035-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="4c035-127">(5) **Shared/Microsoft. Netcore. app \<runtime version> /** cette infrastructure contient le Runtime .net et prend en charge les bibliothèques managées.</span><span class="sxs-lookup"><span data-stu-id="4c035-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="4c035-128">(6) **Shared/Microsoft. AspNetCore. { Application, All}/ \<aspnetcore version>** contient les bibliothèques ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="4c035-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="4c035-129">Les bibliothèques sous `Microsoft.AspNetCore.App` sont développées et prises en charge dans le cadre du projet .net.</span><span class="sxs-lookup"><span data-stu-id="4c035-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET project.</span></span> <span data-ttu-id="4c035-130">Les bibliothèques sous `Microsoft.AspNetCore.All` sont un sur-ensemble qui contient également des bibliothèques de tiers.</span><span class="sxs-lookup"><span data-stu-id="4c035-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="4c035-131">(7) **Shared/Microsoft. Desktop. app \<desktop app version> /** contient les bibliothèques de bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="4c035-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="4c035-132">Cela n’est pas inclus sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="4c035-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="4c035-133">(8) **LICENSE.txt, ThirdPartyNotices.txt** sont la licence .net et les licences des bibliothèques tierces utilisées dans .net, respectivement.</span><span class="sxs-lookup"><span data-stu-id="4c035-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET license and licenses of third-party libraries used in .NET, respectively.</span></span>

- <span data-ttu-id="4c035-134">(9, 10) **dotnet.1.gz, dotnet** `dotnet.1.gz` est la page du manuel de dotnet.</span><span class="sxs-lookup"><span data-stu-id="4c035-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="4c035-135">`dotnet` est un lien symbolique vers l’hôte dotnet (1).</span><span class="sxs-lookup"><span data-stu-id="4c035-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="4c035-136">Ces fichiers sont installés à des emplacements bien connus pour l’intégration du système.</span><span class="sxs-lookup"><span data-stu-id="4c035-136">These files are installed at well-known locations for system integration.</span></span>

- <span data-ttu-id="4c035-137">(11, 12) **Microsoft. Netcore. app. ref, Microsoft. AspNetCore. app. Ref** décrivent l’API d’une `x.y` version de .net et ASP.net Core respectivement.</span><span class="sxs-lookup"><span data-stu-id="4c035-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET and ASP.NET Core respectively.</span></span> <span data-ttu-id="4c035-138">Ces packs sont utilisés lors de la compilation de ces versions cibles.</span><span class="sxs-lookup"><span data-stu-id="4c035-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="4c035-139">(13) **Microsoft. Netcore. app. Host. \<rid>**</span><span class="sxs-lookup"><span data-stu-id="4c035-139">(13) **Microsoft.NETCore.App.Host.\<rid>**</span></span> <span data-ttu-id="4c035-140">contient un binaire natif pour la plateforme `rid` .</span><span class="sxs-lookup"><span data-stu-id="4c035-140">contains a native binary for platform `rid`.</span></span> <span data-ttu-id="4c035-141">Ce binaire est un modèle lors de la compilation d’une application .NET en binaire natif pour cette plateforme.</span><span class="sxs-lookup"><span data-stu-id="4c035-141">This binary is a template when compiling a .NET application into a native binary for that platform.</span></span>

- <span data-ttu-id="4c035-142">(14) **Microsoft. WindowsDesktop. app. Ref** décrit l’API de la `x.y` version des applications de bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="4c035-142">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="4c035-143">Ces fichiers sont utilisés lors de la compilation pour cette cible.</span><span class="sxs-lookup"><span data-stu-id="4c035-143">These files are used when compiling for that target.</span></span> <span data-ttu-id="4c035-144">Cela n’est pas fourni sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="4c035-144">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="4c035-145">(15) **netstandard. Library. Ref** décrit l’API netstandard `x.y` .</span><span class="sxs-lookup"><span data-stu-id="4c035-145">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="4c035-146">Ces fichiers sont utilisés lors de la compilation pour cette cible.</span><span class="sxs-lookup"><span data-stu-id="4c035-146">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="4c035-147">(16) **/etc/dotnet/install_location** est un fichier qui contient le chemin d’accès complet de `{dotnet_root}` .</span><span class="sxs-lookup"><span data-stu-id="4c035-147">(16) **/etc/dotnet/install_location** is a file that contains the full path for `{dotnet_root}`.</span></span> <span data-ttu-id="4c035-148">Le chemin d’accès peut se terminer par un saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="4c035-148">The path may end with a newline.</span></span> <span data-ttu-id="4c035-149">Il n’est pas nécessaire d’ajouter ce fichier quand la racine est `/usr/share/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="4c035-149">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="4c035-150">(17) les **modèles** contiennent les modèles utilisés par le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="4c035-150">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="4c035-151">Par exemple, `dotnet new` recherche des modèles de projet ici.</span><span class="sxs-lookup"><span data-stu-id="4c035-151">For example, `dotnet new` finds project templates here.</span></span>

<span data-ttu-id="4c035-152">Les dossiers marqués avec `(*)` sont utilisés par plusieurs packages.</span><span class="sxs-lookup"><span data-stu-id="4c035-152">The folders marked with `(*)` are used by multiple packages.</span></span> <span data-ttu-id="4c035-153">Certains formats de package (par exemple, `rpm` ) requièrent un traitement spécial de ces dossiers.</span><span class="sxs-lookup"><span data-stu-id="4c035-153">Some package formats (for example, `rpm`) require special handling of such folders.</span></span> <span data-ttu-id="4c035-154">Le chargé de maintenance des packages doit s’en occuper.</span><span class="sxs-lookup"><span data-stu-id="4c035-154">The package maintainer must take care of this.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="4c035-155">Packages recommandés</span><span class="sxs-lookup"><span data-stu-id="4c035-155">Recommended packages</span></span>

<span data-ttu-id="4c035-156">Le contrôle de version .NET est basé sur les numéros de version du composant d’exécution `[major].[minor]` .</span><span class="sxs-lookup"><span data-stu-id="4c035-156">.NET versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="4c035-157">La version du SDK utilise les mêmes numéros `[major].[minor]` et a un `[patch]` indépendant qui combine la sémantique des fonctionnalités et des correctifs pour le SDK.</span><span class="sxs-lookup"><span data-stu-id="4c035-157">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="4c035-158">Par exemple : SDK version 2.2.302 est la deuxième version de correctif de la troisième version du kit de développement logiciel (SDK) qui prend en charge le runtime 2,2.</span><span class="sxs-lookup"><span data-stu-id="4c035-158">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="4c035-159">Pour plus d’informations sur le fonctionnement du contrôle de version, consultez [vue d’ensemble du contrôle de version .net](./versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c035-159">For more information about how versioning works, see [.NET versioning overview](./versions/index.md).</span></span>

<span data-ttu-id="4c035-160">Le nom de certains packages inclut une partie du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="4c035-160">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="4c035-161">Cela vous permet d’installer une version spécifique.</span><span class="sxs-lookup"><span data-stu-id="4c035-161">This allows you to install a specific version.</span></span>
<span data-ttu-id="4c035-162">Le reste de la version n’est pas inclus dans le nom de version.</span><span class="sxs-lookup"><span data-stu-id="4c035-162">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="4c035-163">Ceci permet au Gestionnaire de package du système d’exploitation de mettre à jour les packages (par exemple d’installer automatiquement des correctifs de sécurité).</span><span class="sxs-lookup"><span data-stu-id="4c035-163">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="4c035-164">Les gestionnaires de packages pris en charge sont spécifiques de Linux.</span><span class="sxs-lookup"><span data-stu-id="4c035-164">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="4c035-165">La liste suivante répertorie les packages recommandés :</span><span class="sxs-lookup"><span data-stu-id="4c035-165">The following lists the recommended packages:</span></span>

- <span data-ttu-id="4c035-166">`dotnet-sdk-[major].[minor]` -Installe le dernier Kit de développement logiciel (SDK) pour un Runtime spécifique</span><span class="sxs-lookup"><span data-stu-id="4c035-166">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="4c035-167">**Version :**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="4c035-167">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="4c035-168">**Exemple :** dotnet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="4c035-168">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="4c035-169">**Contient :** (3), (4)</span><span class="sxs-lookup"><span data-stu-id="4c035-169">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="4c035-170">**Dépendances :** `dotnet-runtime-[major].[minor]` , `aspnetcore-runtime-[major].[minor]` ,, `dotnet-targeting-pack-[major].[minor]` ,, `aspnetcore-targeting-pack-[major].[minor]` `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` `dotnet-apphost-pack-[major].[minor]` , `dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="4c035-170">**Dependencies:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="4c035-171">`aspnetcore-runtime-[major].[minor]` -Installe un runtime ASP.NET Core spécifique</span><span class="sxs-lookup"><span data-stu-id="4c035-171">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="4c035-172">**Version :**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="4c035-172">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="4c035-173">**Exemple :** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="4c035-173">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="4c035-174">**Contient :** (6)</span><span class="sxs-lookup"><span data-stu-id="4c035-174">**Contains:** (6)</span></span>
  - <span data-ttu-id="4c035-175">**Dépendances :**`dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="4c035-175">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="4c035-176">`dotnet-runtime-deps-[major].[minor]`_(Facultatif)_ -installe les dépendances pour l’exécution des applications autonomes</span><span class="sxs-lookup"><span data-stu-id="4c035-176">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="4c035-177">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="4c035-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="4c035-178">**Exemple :** dotnet-Runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="4c035-178">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="4c035-179">**Dépendances :** _dépendances spécifiques à la distribution_</span><span class="sxs-lookup"><span data-stu-id="4c035-179">**Dependencies:** _distribution-specific dependencies_</span></span>

- <span data-ttu-id="4c035-180">`dotnet-runtime-[major].[minor]` -Installe un Runtime spécifique</span><span class="sxs-lookup"><span data-stu-id="4c035-180">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="4c035-181">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="4c035-181">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="4c035-182">**Exemple :** dotnet-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="4c035-182">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="4c035-183">**Contient :** (5)</span><span class="sxs-lookup"><span data-stu-id="4c035-183">**Contains:** (5)</span></span>
  - <span data-ttu-id="4c035-184">**Dépendances :** `dotnet-hostfxr-[major].[minor]` , `dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="4c035-184">**Dependencies:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="4c035-185">`dotnet-hostfxr-[major].[minor]` -dépendance</span><span class="sxs-lookup"><span data-stu-id="4c035-185">`dotnet-hostfxr-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="4c035-186">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="4c035-186">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="4c035-187">**Exemple :** dotnet-hostfxr-3,0</span><span class="sxs-lookup"><span data-stu-id="4c035-187">**Example:** dotnet-hostfxr-3.0</span></span>
  - <span data-ttu-id="4c035-188">**Contient :** (2)</span><span class="sxs-lookup"><span data-stu-id="4c035-188">**Contains:** (2)</span></span>
  - <span data-ttu-id="4c035-189">**Dépendances :**`dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="4c035-189">**Dependencies:** `dotnet-host`</span></span>

- <span data-ttu-id="4c035-190">`dotnet-host` -dépendance</span><span class="sxs-lookup"><span data-stu-id="4c035-190">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="4c035-191">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="4c035-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="4c035-192">**Exemple :** dotnet-Host</span><span class="sxs-lookup"><span data-stu-id="4c035-192">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="4c035-193">**Contient :** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="4c035-193">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="4c035-194">`dotnet-apphost-pack-[major].[minor]` -dépendance</span><span class="sxs-lookup"><span data-stu-id="4c035-194">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="4c035-195">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="4c035-195">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="4c035-196">**Contient :** (13)</span><span class="sxs-lookup"><span data-stu-id="4c035-196">**Contains:** (13)</span></span>

- <span data-ttu-id="4c035-197">`dotnet-targeting-pack-[major].[minor]` -Permet de cibler un Runtime qui n’est pas le plus récent</span><span class="sxs-lookup"><span data-stu-id="4c035-197">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="4c035-198">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="4c035-198">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="4c035-199">**Contient :** (12)</span><span class="sxs-lookup"><span data-stu-id="4c035-199">**Contains:** (12)</span></span>

- <span data-ttu-id="4c035-200">`aspnetcore-targeting-pack-[major].[minor]` -Permet de cibler un Runtime qui n’est pas le plus récent</span><span class="sxs-lookup"><span data-stu-id="4c035-200">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="4c035-201">**Version :**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="4c035-201">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="4c035-202">**Contient :** (11)</span><span class="sxs-lookup"><span data-stu-id="4c035-202">**Contains:** (11)</span></span>

- <span data-ttu-id="4c035-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` -Permet de cibler une version netstandard</span><span class="sxs-lookup"><span data-stu-id="4c035-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="4c035-204">**Version :**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="4c035-204">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="4c035-205">**Contient :** (15)</span><span class="sxs-lookup"><span data-stu-id="4c035-205">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="4c035-206">**Version :**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="4c035-206">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="4c035-207">**Contient :** (15)</span><span class="sxs-lookup"><span data-stu-id="4c035-207">**Contains:** (15)</span></span>

<span data-ttu-id="4c035-208">Le `dotnet-runtime-deps-[major].[minor]` nécessite de comprendre les _dépendances spécifiques à distribution_.</span><span class="sxs-lookup"><span data-stu-id="4c035-208">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro-specific dependencies_.</span></span> <span data-ttu-id="4c035-209">Étant donné que le système de génération distribution peut être en mesure de le dériver automatiquement, le package est facultatif, auquel cas ces dépendances sont ajoutées directement au `dotnet-runtime-[major].[minor]` Package.</span><span class="sxs-lookup"><span data-stu-id="4c035-209">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="4c035-210">Lorsque le contenu du package se trouve dans un dossier avec version, le nom du package `[major].[minor]` correspond au nom du dossier avec version.</span><span class="sxs-lookup"><span data-stu-id="4c035-210">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="4c035-211">Pour tous les packages, à l’exception de `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` , cela correspond également à la version .net.</span><span class="sxs-lookup"><span data-stu-id="4c035-211">For all packages, except the `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, this also matches with the .NET version.</span></span>

<span data-ttu-id="4c035-212">Les dépendances entre les packages doivent utiliser une version _égale ou supérieure à_ la version requise.</span><span class="sxs-lookup"><span data-stu-id="4c035-212">Dependencies between packages should use an _equal or greater than_ version requirement.</span></span> <span data-ttu-id="4c035-213">Par exemple, `dotnet-sdk-2.2:2.2.401` nécessite `aspnetcore-runtime-2.2 >= 2.2.6` .</span><span class="sxs-lookup"><span data-stu-id="4c035-213">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="4c035-214">Cela permet à l’utilisateur de mettre à niveau son installation via un package racine (par exemple, `dnf update dotnet-sdk-2.2` ).</span><span class="sxs-lookup"><span data-stu-id="4c035-214">This makes it possible for the user to upgrade their installation via a root package (for example, `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="4c035-215">La plupart des distributions nécessitent que tous les artefacts soient générés à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="4c035-215">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="4c035-216">Ceci a un certain impact sur les packages :</span><span class="sxs-lookup"><span data-stu-id="4c035-216">This has some impact on the packages:</span></span>

- <span data-ttu-id="4c035-217">Les bibliothèques de tiers sous `shared/Microsoft.AspNetCore.All` ne peuvent pas être facilement générées à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="4c035-217">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="4c035-218">Ce dossier est donc omis du package `aspnetcore-runtime`.</span><span class="sxs-lookup"><span data-stu-id="4c035-218">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="4c035-219">`NuGetFallbackFolder` est rempli avec des artefacts binaires provenant de `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="4c035-219">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="4c035-220">Il doit rester vide.</span><span class="sxs-lookup"><span data-stu-id="4c035-220">It should remain empty.</span></span>

<span data-ttu-id="4c035-221">Plusieurs packages `dotnet-sdk` peuvent fournir les mêmes fichiers pour le `NuGetFallbackFolder`.</span><span class="sxs-lookup"><span data-stu-id="4c035-221">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="4c035-222">Pour éviter des problèmes avec le Gestionnaire de package, ces fichiers doivent être identiques (somme de contrôle, date de modification, etc.).</span><span class="sxs-lookup"><span data-stu-id="4c035-222">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="4c035-223">Génération des packages</span><span class="sxs-lookup"><span data-stu-id="4c035-223">Building packages</span></span>

<span data-ttu-id="4c035-224">Le référentiel de [génération dotnet/source](https://github.com/dotnet/source-build) fournit des instructions sur la façon de créer un tarball source du kit de développement logiciel (SDK) .net et de tous ses composants.</span><span class="sxs-lookup"><span data-stu-id="4c035-224">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET SDK and all its components.</span></span> <span data-ttu-id="4c035-225">La sortie du dépôt de builds sources correspond à la disposition décrite dans la première section de cet article.</span><span class="sxs-lookup"><span data-stu-id="4c035-225">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
