---
title: Empaquetage de la distribution de .NET Core
description: Découvrez comment empaqueter, nommer et versionner .NET Core pour la distribution.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: d72677cba1e7685f8e05cf479ec508683dd77b55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394161"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="bddf1-103">Empaquetage de la distribution de .NET Core</span><span class="sxs-lookup"><span data-stu-id="bddf1-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="bddf1-104">.NET Core est disponible sur de plus en plus de plateformes ; il est donc utile de savoir comment l’empaqueter, le nommer et le versionner.</span><span class="sxs-lookup"><span data-stu-id="bddf1-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="bddf1-105">De cette manière, les chargés de maintenance des packages pourront garantir une expérience cohérente quelle que soit la plateforme choisie par les utilisateurs pour exécuter .NET.</span><span class="sxs-lookup"><span data-stu-id="bddf1-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="bddf1-106">Cet article est utile pour les utilisateurs qui :</span><span class="sxs-lookup"><span data-stu-id="bddf1-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="bddf1-107">Essaient de générer .NET Core à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="bddf1-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="bddf1-108">Souhaitent apporter des modifications à l’interface CLI .NET Core susceptibles d’impacter la disposition résultante ou les packages générés.</span><span class="sxs-lookup"><span data-stu-id="bddf1-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="bddf1-109">Disposition du disque</span><span class="sxs-lookup"><span data-stu-id="bddf1-109">Disk layout</span></span>

<span data-ttu-id="bddf1-110">Une fois installé, .NET Core est constitué de plusieurs composants qui sont disposés comme suit dans le système de fichiers :</span><span class="sxs-lookup"><span data-stu-id="bddf1-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
├── packs
│   ├── Microsoft.AspNetCore.App.Ref
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref
│       └── <netstandard version>        (15)
├── shared
│   ├── Microsoft.NETCore.App
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App
│       └── <desktop app version> (7)
└── templates
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="bddf1-111">(1) **dotnet** L’hôte (également appelé « muxer ») a deux rôles distincts : activer un runtime pour lancer une application, et un SDK pour lui distribuer des commandes.</span><span class="sxs-lookup"><span data-stu-id="bddf1-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="bddf1-112">L’hôte est un fichier exécutable natif (`dotnet.exe`).</span><span class="sxs-lookup"><span data-stu-id="bddf1-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="bddf1-113">Alors qu’il n’y a qu’un seul hôte, la plupart des autres composants sont dans des répertoires avec version (2,3,5,6).</span><span class="sxs-lookup"><span data-stu-id="bddf1-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="bddf1-114">Cela signifie que plusieurs versions peuvent être présentes sur le système, car elles sont installées côte à côte.</span><span class="sxs-lookup"><span data-stu-id="bddf1-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="bddf1-115">(2) **host/fxr/\<version fxr>** contient la logique de résolution du framework utilisé par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="bddf1-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="bddf1-116">L’hôte utilise la dernière version de hostfxr qui est installée.</span><span class="sxs-lookup"><span data-stu-id="bddf1-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="bddf1-117">hostfxr est chargé de sélectionner le runtime approprié lors de l’exécution d’une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bddf1-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="bddf1-118">Par exemple, une application générée pour .NET Core 2.0.0 utilise le runtime 2.0.5 quand il est disponible.</span><span class="sxs-lookup"><span data-stu-id="bddf1-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="bddf1-119">De même, hostfxr sélectionne le SDK approprié au cours du développement.</span><span class="sxs-lookup"><span data-stu-id="bddf1-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="bddf1-120">(3) **sdk/\<version sdk>** Le SDK (également appelé « outils ») est un ensemble d’outils gérés servant à écrire et à générer des bibliothèques et des applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bddf1-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="bddf1-121">Le SDK inclut, entre autres, l’interface de ligne de commande de .NET Core (CLI), les compilateurs de langages managés, MSBuild, les cibles et les tâches de génération associées, NuGet et de nouveaux modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="bddf1-121">The SDK includes the .NET Core Command-line interface (CLI), the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="bddf1-122">(4) **sdk/NuGetFallbackFolder** contient un cache de packages NuGet utilisés par un SDK pendant l’opération de restauration, comme lors de l’exécution de `dotnet restore` ou `dotnet build /t:Restore`.</span><span class="sxs-lookup"><span data-stu-id="bddf1-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="bddf1-123">Ce dossier est utilisé uniquement avant .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="bddf1-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="bddf1-124">Il ne peut pas être généré à partir de la source, car il contient `nuget.org`des éléments binaires prégénérés à partir de.</span><span class="sxs-lookup"><span data-stu-id="bddf1-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="bddf1-125">Le dossier **shared** contient des frameworks.</span><span class="sxs-lookup"><span data-stu-id="bddf1-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="bddf1-126">Un framework partagé fournit un ensemble de bibliothèques à un emplacement central, ce qui permet à différentes applications de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="bddf1-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="bddf1-127">(5) **shared/Microsoft.NETCore.App/\<version runtime>** Ce framework contient le runtime .NET Core et des bibliothèques managées qui le prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="bddf1-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="bddf1-128">(6) **Shared/Microsoft. AspNetCore. { Application, All}/\<aspnetcore version >** contient les bibliothèques ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="bddf1-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="bddf1-129">Les bibliothèques sous `Microsoft.AspNetCore.App` sont développées et prises en charge dans le cadre du projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bddf1-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="bddf1-130">Les bibliothèques sous `Microsoft.AspNetCore.All` sont un sur-ensemble qui contient également des bibliothèques de tiers.</span><span class="sxs-lookup"><span data-stu-id="bddf1-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="bddf1-131">(7) **Shared/Microsoft. Desktop. app\</App Desktop version >** contient les bibliothèques de bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="bddf1-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="bddf1-132">Cela n’est pas inclus sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="bddf1-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="bddf1-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** sont la licence .NET Core et les licences des bibliothèques de tiers utilisées dans .NET Core, respectivement.</span><span class="sxs-lookup"><span data-stu-id="bddf1-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="bddf1-134">(9, 10) **dotnet.1.gz, dotnet** `dotnet.1.gz` est la page du manuel de dotnet.</span><span class="sxs-lookup"><span data-stu-id="bddf1-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="bddf1-135">`dotnet` est un lien symbolique vers l’hôte dotnet (1).</span><span class="sxs-lookup"><span data-stu-id="bddf1-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="bddf1-136">Ces fichiers sont installés aux emplacements habituels pour l’intégration du système.</span><span class="sxs-lookup"><span data-stu-id="bddf1-136">These files are installed at well known locations for system integration.</span></span>

- <span data-ttu-id="bddf1-137">(11, 12) **Microsoft. Netcore. app. ref, Microsoft. AspNetCore. app. Ref** décrivent l’API d' `x.y` une version de .net Core et ASP.net Core respectivement.</span><span class="sxs-lookup"><span data-stu-id="bddf1-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="bddf1-138">Ces packs sont utilisés lors de la compilation de ces versions cibles.</span><span class="sxs-lookup"><span data-stu-id="bddf1-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="bddf1-139">(13) **Microsoft. Netcore. app. Host.\< RID >** contient un binaire natif pour la `rid`plateforme.</span><span class="sxs-lookup"><span data-stu-id="bddf1-139">(13) **Microsoft.NETCore.App.Host.\<rid>** contains a native binary for platform `rid`.</span></span> <span data-ttu-id="bddf1-140">Ce binaire est un modèle lors de la compilation d’une application .NET Core en binaire natif pour cette plateforme.</span><span class="sxs-lookup"><span data-stu-id="bddf1-140">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="bddf1-141">(14) **Microsoft. WindowsDesktop. app. Ref** décrit l’API de `x.y` la version des applications de bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="bddf1-141">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="bddf1-142">Ces fichiers sont utilisés lors de la compilation pour cette cible.</span><span class="sxs-lookup"><span data-stu-id="bddf1-142">These files are used when compiling for that target.</span></span> <span data-ttu-id="bddf1-143">Cela n’est pas fourni sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="bddf1-143">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="bddf1-144">(15) **netstandard. Library. Ref** décrit l’API netstandard `x.y` .</span><span class="sxs-lookup"><span data-stu-id="bddf1-144">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="bddf1-145">Ces fichiers sont utilisés lors de la compilation pour cette cible.</span><span class="sxs-lookup"><span data-stu-id="bddf1-145">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="bddf1-146">(16) **/etc/dotnet/install_location** est un fichier qui contient le chemin d’accès complet au dossier qui contient `dotnet` le fichier binaire de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="bddf1-146">(16) **/etc/dotnet/install_location** is a file that contains the full path to the folder that contains the `dotnet` host binary.</span></span> <span data-ttu-id="bddf1-147">Le chemin d’accès peut se terminer par un saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="bddf1-147">The path may be terminated with a newline.</span></span> <span data-ttu-id="bddf1-148">Il n’est pas nécessaire d’ajouter ce fichier quand la racine `/usr/share/dotnet`est.</span><span class="sxs-lookup"><span data-stu-id="bddf1-148">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="bddf1-149">(17) les **modèles** contiennent les modèles utilisés par le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="bddf1-149">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="bddf1-150">Par exemple, `dotnet new` recherche des modèles de projet ici.</span><span class="sxs-lookup"><span data-stu-id="bddf1-150">For example, `dotnet new` finds project templates here.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="bddf1-151">Packages recommandés</span><span class="sxs-lookup"><span data-stu-id="bddf1-151">Recommended packages</span></span>

<span data-ttu-id="bddf1-152">Le contrôle de version de .NET Core est basé sur les numéros de version `[major].[minor]` du composant runtime.</span><span class="sxs-lookup"><span data-stu-id="bddf1-152">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="bddf1-153">La version du SDK utilise les mêmes numéros `[major].[minor]` et a un `[patch]` indépendant qui combine la sémantique des fonctionnalités et des correctifs pour le SDK.</span><span class="sxs-lookup"><span data-stu-id="bddf1-153">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="bddf1-154">Par exemple :  SDK version 2.2.302 est la deuxième version du correctif de la troisième version des fonctionnalités du SDK qui prend en charge le runtime 2.2.</span><span class="sxs-lookup"><span data-stu-id="bddf1-154">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="bddf1-155">Pour plus d’informations sur le fonctionnement de la gestion des versions, consultez [Vue d’ensemble de la gestion des versions .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="bddf1-155">For more information about how versioning works, see [.NET Core versioning overview](../versions/index.md).</span></span>

<span data-ttu-id="bddf1-156">Le nom de certains packages inclut une partie du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="bddf1-156">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="bddf1-157">Cela vous permet d’installer une version spécifique.</span><span class="sxs-lookup"><span data-stu-id="bddf1-157">This allows you to install a specific version.</span></span>
<span data-ttu-id="bddf1-158">Le reste de la version n’est pas inclus dans le nom de version.</span><span class="sxs-lookup"><span data-stu-id="bddf1-158">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="bddf1-159">Ceci permet au Gestionnaire de package du système d’exploitation de mettre à jour les packages (par exemple d’installer automatiquement des correctifs de sécurité).</span><span class="sxs-lookup"><span data-stu-id="bddf1-159">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="bddf1-160">Les gestionnaires de packages pris en charge sont spécifiques de Linux.</span><span class="sxs-lookup"><span data-stu-id="bddf1-160">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="bddf1-161">La liste suivante répertorie les packages recommandés :</span><span class="sxs-lookup"><span data-stu-id="bddf1-161">The following lists the recommended packages:</span></span>

- <span data-ttu-id="bddf1-162">`dotnet-sdk-[major].[minor]`-Installe le dernier Kit de développement logiciel (SDK) pour un Runtime spécifique</span><span class="sxs-lookup"><span data-stu-id="bddf1-162">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="bddf1-163">**Version :** \<version du runtime ></span><span class="sxs-lookup"><span data-stu-id="bddf1-163">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="bddf1-164">**Exemple :** dotnet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="bddf1-164">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="bddf1-165">**Comprend** (3),(4)</span><span class="sxs-lookup"><span data-stu-id="bddf1-165">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="bddf1-166">**Dépendances :** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`,`dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="bddf1-166">**Dependencies:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="bddf1-167">`aspnetcore-runtime-[major].[minor]`-Installe un runtime ASP.NET Core spécifique</span><span class="sxs-lookup"><span data-stu-id="bddf1-167">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="bddf1-168">**Version :** \<version du runtime aspnetcore ></span><span class="sxs-lookup"><span data-stu-id="bddf1-168">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="bddf1-169">**Exemple :** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="bddf1-169">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="bddf1-170">**Comprend** (6)</span><span class="sxs-lookup"><span data-stu-id="bddf1-170">**Contains:** (6)</span></span>
  - <span data-ttu-id="bddf1-171">**Dépendances :** `dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="bddf1-171">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="bddf1-172">`dotnet-runtime-deps-[major].[minor]` _(Facultatif)_ -installe les dépendances pour l’exécution des applications autonomes</span><span class="sxs-lookup"><span data-stu-id="bddf1-172">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="bddf1-173">**Version :** \<version du runtime ></span><span class="sxs-lookup"><span data-stu-id="bddf1-173">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="bddf1-174">**Exemple :** dotnet-Runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="bddf1-174">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="bddf1-175">**Dépendances :** _dépendances spécifiques à distribution_</span><span class="sxs-lookup"><span data-stu-id="bddf1-175">**Dependencies:** _distro specific dependencies_</span></span>

- <span data-ttu-id="bddf1-176">`dotnet-runtime-[major].[minor]`-Installe un Runtime spécifique</span><span class="sxs-lookup"><span data-stu-id="bddf1-176">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="bddf1-177">**Version :** \<version du runtime ></span><span class="sxs-lookup"><span data-stu-id="bddf1-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="bddf1-178">**Exemple :** dotnet-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="bddf1-178">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="bddf1-179">**Comprend** (5)</span><span class="sxs-lookup"><span data-stu-id="bddf1-179">**Contains:** (5)</span></span>
  - <span data-ttu-id="bddf1-180">**Dépendances :** `dotnet-hostfxr:<runtime version>+`,`dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="bddf1-180">**Dependencies:** `dotnet-hostfxr:<runtime version>+`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="bddf1-181">`dotnet-hostfxr`-dépendance</span><span class="sxs-lookup"><span data-stu-id="bddf1-181">`dotnet-hostfxr` - dependency</span></span>
  - <span data-ttu-id="bddf1-182">**Version :** \<version du runtime ></span><span class="sxs-lookup"><span data-stu-id="bddf1-182">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="bddf1-183">**Exemple :** dotnet-hostfxr</span><span class="sxs-lookup"><span data-stu-id="bddf1-183">**Example:** dotnet-hostfxr</span></span>
  - <span data-ttu-id="bddf1-184">**Comprend**  (2)</span><span class="sxs-lookup"><span data-stu-id="bddf1-184">**Contains:** (2)</span></span>
  - <span data-ttu-id="bddf1-185">**Dépendances :** `host:<runtime version>+`</span><span class="sxs-lookup"><span data-stu-id="bddf1-185">**Dependencies:** `host:<runtime version>+`</span></span>

- <span data-ttu-id="bddf1-186">`dotnet-host`-dépendance</span><span class="sxs-lookup"><span data-stu-id="bddf1-186">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="bddf1-187">**Version :** \<version du runtime ></span><span class="sxs-lookup"><span data-stu-id="bddf1-187">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="bddf1-188">**Exemple :** dotnet-Host</span><span class="sxs-lookup"><span data-stu-id="bddf1-188">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="bddf1-189">**Comprend** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="bddf1-189">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="bddf1-190">`dotnet-apphost-pack-[major].[minor]`-dépendance</span><span class="sxs-lookup"><span data-stu-id="bddf1-190">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="bddf1-191">**Version :** \<version du runtime ></span><span class="sxs-lookup"><span data-stu-id="bddf1-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="bddf1-192">**Comprend** 12</span><span class="sxs-lookup"><span data-stu-id="bddf1-192">**Contains:** (13)</span></span>

- <span data-ttu-id="bddf1-193">`dotnet-targeting-pack-[major].[minor]`-Permet de cibler un Runtime qui n’est pas le plus récent</span><span class="sxs-lookup"><span data-stu-id="bddf1-193">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="bddf1-194">**Version :** \<version du runtime ></span><span class="sxs-lookup"><span data-stu-id="bddf1-194">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="bddf1-195">**Comprend** douze</span><span class="sxs-lookup"><span data-stu-id="bddf1-195">**Contains:** (12)</span></span>

- <span data-ttu-id="bddf1-196">`aspnetcore-targeting-pack-[major].[minor]`-Permet de cibler un Runtime qui n’est pas le plus récent</span><span class="sxs-lookup"><span data-stu-id="bddf1-196">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="bddf1-197">**Version :** \<version du runtime aspnetcore ></span><span class="sxs-lookup"><span data-stu-id="bddf1-197">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="bddf1-198">**Comprend** 11</span><span class="sxs-lookup"><span data-stu-id="bddf1-198">**Contains:** (11)</span></span>

- <span data-ttu-id="bddf1-199">`netstandard-targeting-pack-[major].[minor]`-Permet de cibler une version netstandard</span><span class="sxs-lookup"><span data-stu-id="bddf1-199">`netstandard-targeting-pack-[major].[minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="bddf1-200">**Version :** \<version du kit de développement logiciel ></span><span class="sxs-lookup"><span data-stu-id="bddf1-200">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="bddf1-201">**Comprend** 4,5</span><span class="sxs-lookup"><span data-stu-id="bddf1-201">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="bddf1-202">**Version :** \<version du kit de développement logiciel ></span><span class="sxs-lookup"><span data-stu-id="bddf1-202">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="bddf1-203">**Comprend** 4,5</span><span class="sxs-lookup"><span data-stu-id="bddf1-203">**Contains:** (15)</span></span>

<span data-ttu-id="bddf1-204">Le `dotnet-runtime-deps-[major].[minor]` nécessite de comprendre les _dépendances spécifiques à distribution_.</span><span class="sxs-lookup"><span data-stu-id="bddf1-204">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro specific dependencies_.</span></span> <span data-ttu-id="bddf1-205">Étant donné que le système de génération distribution peut être en mesure de le dériver automatiquement, le package est facultatif, auquel cas ces dépendances `dotnet-runtime-[major].[minor]` sont ajoutées directement au package.</span><span class="sxs-lookup"><span data-stu-id="bddf1-205">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="bddf1-206">Lorsque le contenu du package se trouve dans un dossier avec version, `[major].[minor]` le nom du package correspond au nom du dossier avec version.</span><span class="sxs-lookup"><span data-stu-id="bddf1-206">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="bddf1-207">Pour tous les packages, à `netstandard-targeting-pack-[major].[minor]`l’exception de, cela correspond également à la version .net core.</span><span class="sxs-lookup"><span data-stu-id="bddf1-207">For all packages, except the `netstandard-targeting-pack-[major].[minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="bddf1-208">Les dépendances entre les packages doivent utiliser une version _égale ou supérieure à_ la version requise.</span><span class="sxs-lookup"><span data-stu-id="bddf1-208">Dependencies between packages should use a _equal or greater than_ version requirement.</span></span> <span data-ttu-id="bddf1-209">Par exemple, `dotnet-sdk-2.2:2.2.401` nécessite `aspnetcore-runtime-2.2 >= 2.2.6`.</span><span class="sxs-lookup"><span data-stu-id="bddf1-209">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="bddf1-210">Cela permet à l’utilisateur de mettre à niveau son installation via un package racine (par exemple `dnf update dotnet-sdk-2.2`,).</span><span class="sxs-lookup"><span data-stu-id="bddf1-210">This makes it possible for the user to upgrade their installation via a root package (e.g. `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="bddf1-211">La plupart des distributions nécessitent que tous les artefacts soient générés à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="bddf1-211">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="bddf1-212">Ceci a un certain impact sur les packages :</span><span class="sxs-lookup"><span data-stu-id="bddf1-212">This has some impact on the packages:</span></span>

- <span data-ttu-id="bddf1-213">Les bibliothèques de tiers sous `shared/Microsoft.AspNetCore.All` ne peuvent pas être facilement générées à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="bddf1-213">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="bddf1-214">Ce dossier est donc omis du package `aspnetcore-runtime`.</span><span class="sxs-lookup"><span data-stu-id="bddf1-214">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="bddf1-215">`NuGetFallbackFolder` est rempli avec des artefacts binaires provenant de `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="bddf1-215">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="bddf1-216">Il doit rester vide.</span><span class="sxs-lookup"><span data-stu-id="bddf1-216">It should remain empty.</span></span>

<span data-ttu-id="bddf1-217">Plusieurs packages `dotnet-sdk` peuvent fournir les mêmes fichiers pour le `NuGetFallbackFolder`.</span><span class="sxs-lookup"><span data-stu-id="bddf1-217">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="bddf1-218">Pour éviter des problèmes avec le Gestionnaire de package, ces fichiers doivent être identiques (somme de contrôle, date de modification, etc.).</span><span class="sxs-lookup"><span data-stu-id="bddf1-218">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="bddf1-219">Génération des packages</span><span class="sxs-lookup"><span data-stu-id="bddf1-219">Building packages</span></span>

<span data-ttu-id="bddf1-220">Le référentiel [dotnet/source-build](https://github.com/dotnet/source-build) fournit des instructions qui expliquent comment créer un tarball source du Kit SDK .NET Core et de tous ses composants.</span><span class="sxs-lookup"><span data-stu-id="bddf1-220">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="bddf1-221">La sortie du dépôt de builds sources correspond à la disposition décrite dans la première section de cet article.</span><span class="sxs-lookup"><span data-stu-id="bddf1-221">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
