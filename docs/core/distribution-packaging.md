---
title: Empaquetage de la distribution de .NET Core
description: Découvrez comment empaqueter, nommer et versionner .NET Core pour la distribution.
author: tmds
ms.date: 10/09/2019
ms.openlocfilehash: 3324a6a151fc6dc46a8f13ea17c89da99d108d82
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062884"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="2af2b-103">Empaquetage de la distribution de .NET Core</span><span class="sxs-lookup"><span data-stu-id="2af2b-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="2af2b-104">.NET Core est disponible sur de plus en plus de plateformes ; il est donc utile de savoir comment l’empaqueter, le nommer et le versionner.</span><span class="sxs-lookup"><span data-stu-id="2af2b-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="2af2b-105">De cette manière, les chargés de maintenance des packages pourront garantir une expérience cohérente quelle que soit la plateforme choisie par les utilisateurs pour exécuter .NET.</span><span class="sxs-lookup"><span data-stu-id="2af2b-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="2af2b-106">Cet article est utile pour les utilisateurs qui :</span><span class="sxs-lookup"><span data-stu-id="2af2b-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="2af2b-107">Essaient de générer .NET Core à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="2af2b-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="2af2b-108">Souhaitent apporter des modifications à l’interface CLI .NET Core susceptibles d’impacter la disposition résultante ou les packages générés.</span><span class="sxs-lookup"><span data-stu-id="2af2b-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="2af2b-109">Disposition du disque</span><span class="sxs-lookup"><span data-stu-id="2af2b-109">Disk layout</span></span>

<span data-ttu-id="2af2b-110">Une fois installé, .NET Core est constitué de plusieurs composants qui sont disposés comme suit dans le système de fichiers :</span><span class="sxs-lookup"><span data-stu-id="2af2b-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

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

- <span data-ttu-id="2af2b-111">(1) **dotnet** L’hôte (également appelé « muxer ») a deux rôles distincts : activer un runtime pour lancer une application, et un SDK pour lui distribuer des commandes.</span><span class="sxs-lookup"><span data-stu-id="2af2b-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="2af2b-112">L’hôte est un fichier exécutable natif (`dotnet.exe`).</span><span class="sxs-lookup"><span data-stu-id="2af2b-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="2af2b-113">Alors qu’il n’y a qu’un seul hôte, la plupart des autres composants sont dans des répertoires avec version (2,3,5,6).</span><span class="sxs-lookup"><span data-stu-id="2af2b-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="2af2b-114">Cela signifie que plusieurs versions peuvent être présentes sur le système, car elles sont installées côte à côte.</span><span class="sxs-lookup"><span data-stu-id="2af2b-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="2af2b-115">(2) \*\*Host/FXR/ \<fxr version> \*\* contient la logique de résolution de l’infrastructure utilisée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="2af2b-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="2af2b-116">L’hôte utilise la dernière version de hostfxr qui est installée.</span><span class="sxs-lookup"><span data-stu-id="2af2b-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="2af2b-117">hostfxr est chargé de sélectionner le runtime approprié lors de l’exécution d’une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2af2b-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="2af2b-118">Par exemple, une application générée pour .NET Core 2.0.0 utilise le runtime 2.0.5 quand il est disponible.</span><span class="sxs-lookup"><span data-stu-id="2af2b-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="2af2b-119">De même, hostfxr sélectionne le SDK approprié au cours du développement.</span><span class="sxs-lookup"><span data-stu-id="2af2b-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="2af2b-120">(3) \*\*SDK/ \<sdk version> \*\* le kit de développement logiciel (SDK) (également appelé « outils ») est un ensemble d’outils gérés servant à écrire et à générer des bibliothèques et des applications .net core.</span><span class="sxs-lookup"><span data-stu-id="2af2b-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="2af2b-121">Le kit de développement logiciel (SDK) comprend les CLI .NET Core, les compilateurs de langage managé, MSBuild, ainsi que les tâches et cibles de build associées, NuGet, les nouveaux modèles de projet, etc.</span><span class="sxs-lookup"><span data-stu-id="2af2b-121">The SDK includes the .NET Core CLI, the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="2af2b-122">(4) **sdk/NuGetFallbackFolder** contient un cache de packages NuGet utilisés par un SDK pendant l’opération de restauration, comme lors de l’exécution de `dotnet restore` ou `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="2af2b-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build`.</span></span> <span data-ttu-id="2af2b-123">Ce dossier est utilisé uniquement avant .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2af2b-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="2af2b-124">Il ne peut pas être généré à partir de la source, car il contient des éléments binaires prégénérés à partir de `nuget.org` .</span><span class="sxs-lookup"><span data-stu-id="2af2b-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="2af2b-125">Le dossier **shared** contient des frameworks.</span><span class="sxs-lookup"><span data-stu-id="2af2b-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="2af2b-126">Un framework partagé fournit un ensemble de bibliothèques à un emplacement central, ce qui permet à différentes applications de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="2af2b-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="2af2b-127">(5) **Shared/Microsoft. Netcore. app \<runtime version> /** cette infrastructure contient le Runtime .net Core et prend en charge les bibliothèques managées.</span><span class="sxs-lookup"><span data-stu-id="2af2b-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="2af2b-128">(6) \*\*Shared/Microsoft. AspNetCore. { Application, All}/ \<aspnetcore version> \*\* contient les bibliothèques ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="2af2b-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="2af2b-129">Les bibliothèques sous `Microsoft.AspNetCore.App` sont développées et prises en charge dans le cadre du projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2af2b-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="2af2b-130">Les bibliothèques sous `Microsoft.AspNetCore.All` sont un sur-ensemble qui contient également des bibliothèques de tiers.</span><span class="sxs-lookup"><span data-stu-id="2af2b-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="2af2b-131">(7) **Shared/Microsoft. Desktop. app \<desktop app version> /** contient les bibliothèques de bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="2af2b-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="2af2b-132">Cela n’est pas inclus sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="2af2b-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="2af2b-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** sont la licence .NET Core et les licences des bibliothèques de tiers utilisées dans .NET Core, respectivement.</span><span class="sxs-lookup"><span data-stu-id="2af2b-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="2af2b-134">(9, 10) **dotnet.1.gz, dotnet** `dotnet.1.gz` est la page du manuel de dotnet.</span><span class="sxs-lookup"><span data-stu-id="2af2b-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="2af2b-135">`dotnet` est un lien symbolique vers l’hôte dotnet (1).</span><span class="sxs-lookup"><span data-stu-id="2af2b-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="2af2b-136">Ces fichiers sont installés à des emplacements bien connus pour l’intégration du système.</span><span class="sxs-lookup"><span data-stu-id="2af2b-136">These files are installed at well-known locations for system integration.</span></span>

- <span data-ttu-id="2af2b-137">(11, 12) **Microsoft. Netcore. app. ref, Microsoft. AspNetCore. app. Ref** décrivent l’API d’une `x.y` version de .net Core et ASP.net Core respectivement.</span><span class="sxs-lookup"><span data-stu-id="2af2b-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="2af2b-138">Ces packs sont utilisés lors de la compilation de ces versions cibles.</span><span class="sxs-lookup"><span data-stu-id="2af2b-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="2af2b-139">(13) \*\*Microsoft. Netcore. app. Host. \<rid> \*\*</span><span class="sxs-lookup"><span data-stu-id="2af2b-139">(13) **Microsoft.NETCore.App.Host.\<rid>**</span></span> <span data-ttu-id="2af2b-140">contient un binaire natif pour la plateforme `rid` .</span><span class="sxs-lookup"><span data-stu-id="2af2b-140">contains a native binary for platform `rid`.</span></span> <span data-ttu-id="2af2b-141">Ce binaire est un modèle lors de la compilation d’une application .NET Core en binaire natif pour cette plateforme.</span><span class="sxs-lookup"><span data-stu-id="2af2b-141">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="2af2b-142">(14) **Microsoft. WindowsDesktop. app. Ref** décrit l’API de la `x.y` version des applications de bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="2af2b-142">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="2af2b-143">Ces fichiers sont utilisés lors de la compilation pour cette cible.</span><span class="sxs-lookup"><span data-stu-id="2af2b-143">These files are used when compiling for that target.</span></span> <span data-ttu-id="2af2b-144">Cela n’est pas fourni sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="2af2b-144">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="2af2b-145">(15) **netstandard. Library. Ref** décrit l’API netstandard `x.y` .</span><span class="sxs-lookup"><span data-stu-id="2af2b-145">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="2af2b-146">Ces fichiers sont utilisés lors de la compilation pour cette cible.</span><span class="sxs-lookup"><span data-stu-id="2af2b-146">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="2af2b-147">(16) **/etc/dotnet/install_location** est un fichier qui contient le chemin d’accès complet de `{dotnet_root}` .</span><span class="sxs-lookup"><span data-stu-id="2af2b-147">(16) **/etc/dotnet/install_location** is a file that contains the full path for `{dotnet_root}`.</span></span> <span data-ttu-id="2af2b-148">Le chemin d’accès peut se terminer par un saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="2af2b-148">The path may end with a newline.</span></span> <span data-ttu-id="2af2b-149">Il n’est pas nécessaire d’ajouter ce fichier quand la racine est `/usr/share/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="2af2b-149">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="2af2b-150">(17) les **modèles** contiennent les modèles utilisés par le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="2af2b-150">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="2af2b-151">Par exemple, `dotnet new` recherche des modèles de projet ici.</span><span class="sxs-lookup"><span data-stu-id="2af2b-151">For example, `dotnet new` finds project templates here.</span></span>

<span data-ttu-id="2af2b-152">Les dossiers marqués avec `(*)` sont utilisés par plusieurs packages.</span><span class="sxs-lookup"><span data-stu-id="2af2b-152">The folders marked with `(*)` are used by multiple packages.</span></span> <span data-ttu-id="2af2b-153">Certains formats de package (par exemple, `rpm` ) requièrent un traitement spécial de ces dossiers.</span><span class="sxs-lookup"><span data-stu-id="2af2b-153">Some package formats (for example, `rpm`) require special handling of such folders.</span></span> <span data-ttu-id="2af2b-154">Le chargé de maintenance des packages doit s’en occuper.</span><span class="sxs-lookup"><span data-stu-id="2af2b-154">The package maintainer must take care of this.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="2af2b-155">Packages recommandés</span><span class="sxs-lookup"><span data-stu-id="2af2b-155">Recommended packages</span></span>

<span data-ttu-id="2af2b-156">Le contrôle de version de .NET Core est basé sur les numéros de version `[major].[minor]` du composant runtime.</span><span class="sxs-lookup"><span data-stu-id="2af2b-156">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="2af2b-157">La version du SDK utilise les mêmes numéros `[major].[minor]` et a un `[patch]` indépendant qui combine la sémantique des fonctionnalités et des correctifs pour le SDK.</span><span class="sxs-lookup"><span data-stu-id="2af2b-157">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="2af2b-158">Par exemple : SDK version 2.2.302 est la deuxième version de correctif de la troisième version du kit de développement logiciel (SDK) qui prend en charge le runtime 2,2.</span><span class="sxs-lookup"><span data-stu-id="2af2b-158">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="2af2b-159">Pour plus d’informations sur le fonctionnement de la gestion des versions, consultez [Vue d’ensemble de la gestion des versions .NET Core](./versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="2af2b-159">For more information about how versioning works, see [.NET Core versioning overview](./versions/index.md).</span></span>

<span data-ttu-id="2af2b-160">Le nom de certains packages inclut une partie du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="2af2b-160">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="2af2b-161">Cela vous permet d’installer une version spécifique.</span><span class="sxs-lookup"><span data-stu-id="2af2b-161">This allows you to install a specific version.</span></span>
<span data-ttu-id="2af2b-162">Le reste de la version n’est pas inclus dans le nom de version.</span><span class="sxs-lookup"><span data-stu-id="2af2b-162">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="2af2b-163">Ceci permet au Gestionnaire de package du système d’exploitation de mettre à jour les packages (par exemple d’installer automatiquement des correctifs de sécurité).</span><span class="sxs-lookup"><span data-stu-id="2af2b-163">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="2af2b-164">Les gestionnaires de packages pris en charge sont spécifiques de Linux.</span><span class="sxs-lookup"><span data-stu-id="2af2b-164">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="2af2b-165">La liste suivante répertorie les packages recommandés :</span><span class="sxs-lookup"><span data-stu-id="2af2b-165">The following lists the recommended packages:</span></span>

- <span data-ttu-id="2af2b-166">`dotnet-sdk-[major].[minor]`-Installe le dernier Kit de développement logiciel (SDK) pour un Runtime spécifique</span><span class="sxs-lookup"><span data-stu-id="2af2b-166">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="2af2b-167">**Version :**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="2af2b-167">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="2af2b-168">**Exemple :** dotnet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="2af2b-168">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="2af2b-169">**Contient :** (3), (4)</span><span class="sxs-lookup"><span data-stu-id="2af2b-169">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="2af2b-170">**Dépendances :** `dotnet-runtime-[major].[minor]` , `aspnetcore-runtime-[major].[minor]` ,, `dotnet-targeting-pack-[major].[minor]` ,, `aspnetcore-targeting-pack-[major].[minor]` `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` `dotnet-apphost-pack-[major].[minor]` ,`dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="2af2b-170">**Dependencies:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="2af2b-171">`aspnetcore-runtime-[major].[minor]`-Installe un runtime ASP.NET Core spécifique</span><span class="sxs-lookup"><span data-stu-id="2af2b-171">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="2af2b-172">**Version :**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="2af2b-172">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="2af2b-173">**Exemple :** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="2af2b-173">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="2af2b-174">**Contient :** (6)</span><span class="sxs-lookup"><span data-stu-id="2af2b-174">**Contains:** (6)</span></span>
  - <span data-ttu-id="2af2b-175">**Dépendances :**`dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="2af2b-175">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="2af2b-176">`dotnet-runtime-deps-[major].[minor]`_(Facultatif)_ -installe les dépendances pour l’exécution des applications autonomes</span><span class="sxs-lookup"><span data-stu-id="2af2b-176">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="2af2b-177">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2af2b-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2af2b-178">**Exemple :** dotnet-Runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="2af2b-178">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="2af2b-179">**Dépendances :** _dépendances spécifiques à la distribution_</span><span class="sxs-lookup"><span data-stu-id="2af2b-179">**Dependencies:** _distribution-specific dependencies_</span></span>

- <span data-ttu-id="2af2b-180">`dotnet-runtime-[major].[minor]`-Installe un Runtime spécifique</span><span class="sxs-lookup"><span data-stu-id="2af2b-180">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="2af2b-181">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2af2b-181">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2af2b-182">**Exemple :** dotnet-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="2af2b-182">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="2af2b-183">**Contient :** (5)</span><span class="sxs-lookup"><span data-stu-id="2af2b-183">**Contains:** (5)</span></span>
  - <span data-ttu-id="2af2b-184">**Dépendances :** `dotnet-hostfxr-[major].[minor]` ,`dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="2af2b-184">**Dependencies:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="2af2b-185">`dotnet-hostfxr-[major].[minor]`-dépendance</span><span class="sxs-lookup"><span data-stu-id="2af2b-185">`dotnet-hostfxr-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="2af2b-186">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2af2b-186">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2af2b-187">**Exemple :** dotnet-hostfxr-3,0</span><span class="sxs-lookup"><span data-stu-id="2af2b-187">**Example:** dotnet-hostfxr-3.0</span></span>
  - <span data-ttu-id="2af2b-188">**Contient :** (2)</span><span class="sxs-lookup"><span data-stu-id="2af2b-188">**Contains:** (2)</span></span>
  - <span data-ttu-id="2af2b-189">**Dépendances :**`dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="2af2b-189">**Dependencies:** `dotnet-host`</span></span>

- <span data-ttu-id="2af2b-190">`dotnet-host`-dépendance</span><span class="sxs-lookup"><span data-stu-id="2af2b-190">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="2af2b-191">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2af2b-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2af2b-192">**Exemple :** dotnet-Host</span><span class="sxs-lookup"><span data-stu-id="2af2b-192">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="2af2b-193">**Contient :** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="2af2b-193">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="2af2b-194">`dotnet-apphost-pack-[major].[minor]`-dépendance</span><span class="sxs-lookup"><span data-stu-id="2af2b-194">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="2af2b-195">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2af2b-195">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2af2b-196">**Contient :** (13)</span><span class="sxs-lookup"><span data-stu-id="2af2b-196">**Contains:** (13)</span></span>

- <span data-ttu-id="2af2b-197">`dotnet-targeting-pack-[major].[minor]`-Permet de cibler un Runtime qui n’est pas le plus récent</span><span class="sxs-lookup"><span data-stu-id="2af2b-197">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="2af2b-198">**Version :**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="2af2b-198">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2af2b-199">**Contient :** (12)</span><span class="sxs-lookup"><span data-stu-id="2af2b-199">**Contains:** (12)</span></span>

- <span data-ttu-id="2af2b-200">`aspnetcore-targeting-pack-[major].[minor]`-Permet de cibler un Runtime qui n’est pas le plus récent</span><span class="sxs-lookup"><span data-stu-id="2af2b-200">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="2af2b-201">**Version :**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="2af2b-201">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="2af2b-202">**Contient :** (11)</span><span class="sxs-lookup"><span data-stu-id="2af2b-202">**Contains:** (11)</span></span>

- <span data-ttu-id="2af2b-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`-Permet de cibler une version netstandard</span><span class="sxs-lookup"><span data-stu-id="2af2b-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="2af2b-204">**Version :**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="2af2b-204">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="2af2b-205">**Contient :** (15)</span><span class="sxs-lookup"><span data-stu-id="2af2b-205">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="2af2b-206">**Version :**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="2af2b-206">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="2af2b-207">**Contient :** (15)</span><span class="sxs-lookup"><span data-stu-id="2af2b-207">**Contains:** (15)</span></span>

<span data-ttu-id="2af2b-208">Le `dotnet-runtime-deps-[major].[minor]` nécessite de comprendre les _dépendances spécifiques à distribution_.</span><span class="sxs-lookup"><span data-stu-id="2af2b-208">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro-specific dependencies_.</span></span> <span data-ttu-id="2af2b-209">Étant donné que le système de génération distribution peut être en mesure de le dériver automatiquement, le package est facultatif, auquel cas ces dépendances sont ajoutées directement au `dotnet-runtime-[major].[minor]` Package.</span><span class="sxs-lookup"><span data-stu-id="2af2b-209">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="2af2b-210">Lorsque le contenu du package se trouve dans un dossier avec version, le nom du package `[major].[minor]` correspond au nom du dossier avec version.</span><span class="sxs-lookup"><span data-stu-id="2af2b-210">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="2af2b-211">Pour tous les packages, à l’exception de `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` , cela correspond également à la version .net core.</span><span class="sxs-lookup"><span data-stu-id="2af2b-211">For all packages, except the `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="2af2b-212">Les dépendances entre les packages doivent utiliser une version _égale ou supérieure à_ la version requise.</span><span class="sxs-lookup"><span data-stu-id="2af2b-212">Dependencies between packages should use an _equal or greater than_ version requirement.</span></span> <span data-ttu-id="2af2b-213">Par exemple, `dotnet-sdk-2.2:2.2.401` nécessite `aspnetcore-runtime-2.2 >= 2.2.6` .</span><span class="sxs-lookup"><span data-stu-id="2af2b-213">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="2af2b-214">Cela permet à l’utilisateur de mettre à niveau son installation via un package racine (par exemple, `dnf update dotnet-sdk-2.2` ).</span><span class="sxs-lookup"><span data-stu-id="2af2b-214">This makes it possible for the user to upgrade their installation via a root package (for example, `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="2af2b-215">La plupart des distributions nécessitent que tous les artefacts soient générés à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="2af2b-215">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="2af2b-216">Ceci a un certain impact sur les packages :</span><span class="sxs-lookup"><span data-stu-id="2af2b-216">This has some impact on the packages:</span></span>

- <span data-ttu-id="2af2b-217">Les bibliothèques de tiers sous `shared/Microsoft.AspNetCore.All` ne peuvent pas être facilement générées à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="2af2b-217">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="2af2b-218">Ce dossier est donc omis du package `aspnetcore-runtime`.</span><span class="sxs-lookup"><span data-stu-id="2af2b-218">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="2af2b-219">`NuGetFallbackFolder` est rempli avec des artefacts binaires provenant de `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="2af2b-219">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="2af2b-220">Il doit rester vide.</span><span class="sxs-lookup"><span data-stu-id="2af2b-220">It should remain empty.</span></span>

<span data-ttu-id="2af2b-221">Plusieurs packages `dotnet-sdk` peuvent fournir les mêmes fichiers pour le `NuGetFallbackFolder`.</span><span class="sxs-lookup"><span data-stu-id="2af2b-221">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="2af2b-222">Pour éviter des problèmes avec le Gestionnaire de package, ces fichiers doivent être identiques (somme de contrôle, date de modification, etc.).</span><span class="sxs-lookup"><span data-stu-id="2af2b-222">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="2af2b-223">Génération des packages</span><span class="sxs-lookup"><span data-stu-id="2af2b-223">Building packages</span></span>

<span data-ttu-id="2af2b-224">Le référentiel [dotnet/source-build](https://github.com/dotnet/source-build) fournit des instructions qui expliquent comment créer un tarball source du Kit SDK .NET Core et de tous ses composants.</span><span class="sxs-lookup"><span data-stu-id="2af2b-224">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="2af2b-225">La sortie du dépôt de builds sources correspond à la disposition décrite dans la première section de cet article.</span><span class="sxs-lookup"><span data-stu-id="2af2b-225">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
