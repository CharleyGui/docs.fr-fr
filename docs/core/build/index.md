---
title: Générer .NET Core à partir de la source
description: Découvrez comment générer .NET Core et le .NET Core CLI à partir du code source.
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
ms.openlocfilehash: dcd7c909325eec5a79db74098d7ac880000eafa1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105385"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="21eca-103">Générer .NET Core à partir de la source</span><span class="sxs-lookup"><span data-stu-id="21eca-103">Build .NET Core from source</span></span>

<span data-ttu-id="21eca-104">La capacité de générer .NET Core à partir de son code source est importante à plusieurs titres : elle facilite le portage de .NET Core vers de nouvelles plateformes, elle permet les contributions et les correctifs pour le produit, et elle permet la création de versions personnalisées de .NET.</span><span class="sxs-lookup"><span data-stu-id="21eca-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="21eca-105">Cet article fournit de l’aide aux développeurs qui veulent créer et distribuer leurs propres versions de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="21eca-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="21eca-106">Générer le CLR à partir de la source</span><span class="sxs-lookup"><span data-stu-id="21eca-106">Build the CLR from source</span></span>

<span data-ttu-id="21eca-107">Vous trouverez le code source de .NET CoreCLR dans le référentiel [dotnet/coreclr](https://github.com/dotnet/coreclr/) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="21eca-107">The source code for the .NET CoreCLR can be found in the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository on GitHub.</span></span>

<span data-ttu-id="21eca-108">La génération dépend actuellement des prérequis suivants :</span><span class="sxs-lookup"><span data-stu-id="21eca-108">The build currently depends on the following prerequisites:</span></span>

- [<span data-ttu-id="21eca-109">Git</span><span class="sxs-lookup"><span data-stu-id="21eca-109">Git</span></span>](https://git-scm.com/)
- [<span data-ttu-id="21eca-110">CMake</span><span class="sxs-lookup"><span data-stu-id="21eca-110">CMake</span></span>](https://cmake.org/)
- [<span data-ttu-id="21eca-111">Python</span><span class="sxs-lookup"><span data-stu-id="21eca-111">Python</span></span>](https://www.python.org/)
- <span data-ttu-id="21eca-112">Un compilateur C++.</span><span class="sxs-lookup"><span data-stu-id="21eca-112">a C++ compiler.</span></span>

<span data-ttu-id="21eca-113">Une fois ces composants requis installés, vous pouvez générer le CLR en appelant le script de génération (`build.cmd` sur Windows ou `build.sh` sur Linux et macOS) à la base du dépôt [dotnet/coreclr](https://github.com/dotnet/coreclr/).</span><span class="sxs-lookup"><span data-stu-id="21eca-113">After you've installed these prerequisites, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository.</span></span>

<span data-ttu-id="21eca-114">L’installation des composants diffère selon le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="21eca-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="21eca-115">Consultez les instructions de génération pour votre système d’exploitation spécifique :</span><span class="sxs-lookup"><span data-stu-id="21eca-115">See the build instructions for your specific OS:</span></span>

- [<span data-ttu-id="21eca-116">Fenêtres</span><span class="sxs-lookup"><span data-stu-id="21eca-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [<span data-ttu-id="21eca-117">Linux</span><span class="sxs-lookup"><span data-stu-id="21eca-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [<span data-ttu-id="21eca-118">macOS</span><span class="sxs-lookup"><span data-stu-id="21eca-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [<span data-ttu-id="21eca-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="21eca-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [<span data-ttu-id="21eca-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="21eca-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="21eca-121">La génération croisée entre systèmes d’exploitation n’est pas possible (sauf pour ARM, qui est basé sur X64).</span><span class="sxs-lookup"><span data-stu-id="21eca-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="21eca-122">Vous devez être sur la plateforme spécifique pour générer cette plateforme.</span><span class="sxs-lookup"><span data-stu-id="21eca-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="21eca-123">La build a deux `buildTypes` principaux :</span><span class="sxs-lookup"><span data-stu-id="21eca-123">The build has two main `buildTypes`:</span></span>

- <span data-ttu-id="21eca-124">Debug (par défaut) : compile le runtime avec des optimisations minimales et des vérifications (assertions) supplémentaires à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="21eca-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="21eca-125">Cette réduction du niveau d’optimisation et les vérifications supplémentaires ralentissent l’exécution du runtime, mais sont utiles pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="21eca-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="21eca-126">Il s’agit du paramètre recommandé pour les environnements de développement et de test.</span><span class="sxs-lookup"><span data-stu-id="21eca-126">This is the recommended setting for development and testing environments.</span></span>
- <span data-ttu-id="21eca-127">Release : compile le runtime avec des optimisations complètes et sans les vérifications supplémentaires à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="21eca-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="21eca-128">Vous obtenez des performances d’exécution plus rapides, mais la génération peut prendre plus de temps et être difficile à déboguer.</span><span class="sxs-lookup"><span data-stu-id="21eca-128">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="21eca-129">Passez `release` au script de compilation pour sélectionner ce type de build.</span><span class="sxs-lookup"><span data-stu-id="21eca-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="21eca-130">Par défaut, la génération crée non seulement les exécutables du runtime, mais elle produit également tous les tests.</span><span class="sxs-lookup"><span data-stu-id="21eca-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="21eca-131">Il existe un bon nombre de tests qui prennent un temps considérable alors qu’ils ne sont pas nécessaires si vous voulez faire des essais avec des modifications.</span><span class="sxs-lookup"><span data-stu-id="21eca-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="21eca-132">Vous pouvez ignorer les builds de tests en ajoutant l’argument `skiptests` au script de génération, comme dans l’exemple suivant (remplacez `.\build` par `./build.sh` sur les machines Unix) :</span><span class="sxs-lookup"><span data-stu-id="21eca-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests
```

<span data-ttu-id="21eca-133">L’exemple précédent a montré comment générer la version `Debug`, avec les vérifications (assertions) au moment du développement activées et les optimisations désactivées.</span><span class="sxs-lookup"><span data-stu-id="21eca-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="21eca-134">Pour générer la version Release (celle qui s’exécute à pleine vitesse), procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="21eca-134">To build the release (full speed) flavor, do the following:</span></span>

```bat
    .\build release skiptests
```

<span data-ttu-id="21eca-135">Vous trouverez plus d’options de génération de la build en utilisant le qualificateur -?</span><span class="sxs-lookup"><span data-stu-id="21eca-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="21eca-136">ou - help.</span><span class="sxs-lookup"><span data-stu-id="21eca-136">or -help qualifier.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="21eca-137">Utilisation de votre build</span><span class="sxs-lookup"><span data-stu-id="21eca-137">Using Your Build</span></span>

<span data-ttu-id="21eca-138">La build place tous les fichiers générés sous le répertoire `bin` à la base du dépôt.</span><span class="sxs-lookup"><span data-stu-id="21eca-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="21eca-139">Il existe un répertoire *bin\Log* qui contient les fichiers journaux générés pendant la génération (utiles principalement en cas d’échec de la build).</span><span class="sxs-lookup"><span data-stu-id="21eca-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="21eca-140">Le résultat est placé dans un répertoire *bin\Product\[plateforme].[Architecture d’UC].[type de build]* , comme *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="21eca-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="21eca-141">Si la sortie « brute » de la build est parfois utile, vous n’êtes normalement intéressé que par les packages NuGet, qui sont placés dans le sous-répertoire `.nuget\pkg` du répertoire de sortie précédent.</span><span class="sxs-lookup"><span data-stu-id="21eca-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="21eca-142">Vous pouvez utiliser votre nouveau runtime selon deux techniques de base :</span><span class="sxs-lookup"><span data-stu-id="21eca-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="21eca-143">**Utiliser dotnet.exe et NuGet pour composer une application**.</span><span class="sxs-lookup"><span data-stu-id="21eca-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="21eca-144">Consultez [Utilisation de votre build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) pour obtenir des instructions sur la création d’un programme qui utilise votre nouveau runtime avec les packages NuGet que vous venez de créer et l’interface de ligne de commande (CLI) « dotnet ».</span><span class="sxs-lookup"><span data-stu-id="21eca-144">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="21eca-145">Cette technique est celle que les développeurs « non-runtime » vont probablement utiliser pour consommer votre nouveau runtime.</span><span class="sxs-lookup"><span data-stu-id="21eca-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>

 2. <span data-ttu-id="21eca-146">**Utiliser corerun.exe pour exécuter une application avec des DLL non packagées**.</span><span class="sxs-lookup"><span data-stu-id="21eca-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="21eca-147">Ce dépôt définit également un hôte simple appelé corerun.exe, qui n’accepte AUCUNE dépendance de NuGet.</span><span class="sxs-lookup"><span data-stu-id="21eca-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="21eca-148">Vous devez indiquer à l’hôte où obtenir les DLL nécessaires que vous utilisez, puis vous devez les rassembler manuellement.</span><span class="sxs-lookup"><span data-stu-id="21eca-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="21eca-149">Cette technique, utilisée par tous les tests du référentiel [dotnet/coreclr](https://github.com/dotnet/coreclr), est utile pour la boucle locale rapide « Édition-Compilation-Débogage », comme les tests unitaires préliminaires.</span><span class="sxs-lookup"><span data-stu-id="21eca-149">This technique is used by all the tests in the [dotnet/coreclr](https://github.com/dotnet/coreclr) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="21eca-150">Pour plus d’informations sur l’utilisation de cette technique, consultez [Exécution d’applications .NET Core avec CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md).</span><span class="sxs-lookup"><span data-stu-id="21eca-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="21eca-151">Générer l’interface CLI à partir de la source</span><span class="sxs-lookup"><span data-stu-id="21eca-151">Build the CLI from source</span></span>

<span data-ttu-id="21eca-152">Vous trouverez le code source de l’interface CLI .NET Core dans le référentiel [dotnet/cli](https://github.com/dotnet/cli/) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="21eca-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="21eca-153">Pour générer l’interface CLI de .NET Core, les éléments suivants doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="21eca-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

- <span data-ttu-id="21eca-154">Windows et Linux :</span><span class="sxs-lookup"><span data-stu-id="21eca-154">Windows & Linux:</span></span>
  - <span data-ttu-id="21eca-155">git sur la variable PATH</span><span class="sxs-lookup"><span data-stu-id="21eca-155">git on the PATH</span></span>
- <span data-ttu-id="21eca-156">macOS :</span><span class="sxs-lookup"><span data-stu-id="21eca-156">macOS:</span></span>
  - <span data-ttu-id="21eca-157">git sur la variable PATH</span><span class="sxs-lookup"><span data-stu-id="21eca-157">git on the PATH</span></span>
  - <span data-ttu-id="21eca-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="21eca-158">Xcode</span></span>
  - <span data-ttu-id="21eca-159">Openssl</span><span class="sxs-lookup"><span data-stu-id="21eca-159">OpenSSL</span></span>

<span data-ttu-id="21eca-160">Pour générer, exécutez `build.cmd` sur Windows, ou `build.sh` sur Linux et macOS à partir de la racine.</span><span class="sxs-lookup"><span data-stu-id="21eca-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="21eca-161">Si vous ne voulez pas exécuter les tests, exécutez `build.cmd -t:Compile` ou `./build.sh -t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="21eca-161">If you don't want to execute tests, run `build.cmd -t:Compile` or `./build.sh -t:Compile`.</span></span> <span data-ttu-id="21eca-162">Pour générer l’interface CLI dans macOS Sierra, vous devez définir la variable d’environnement DOTNET_RUNTIME_ID en exécutant `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="21eca-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="21eca-163">Utilisation de votre build</span><span class="sxs-lookup"><span data-stu-id="21eca-163">Using your build</span></span>

<span data-ttu-id="21eca-164">Utilisez l’exécutable `dotnet` à partir de *artifacts/{os}-{arch}/stage2* pour essayer l’interface CLI nouvellement générée.</span><span class="sxs-lookup"><span data-stu-id="21eca-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="21eca-165">Si vous voulez utiliser la sortie de la génération lors de l’appel de `dotnet` à partir de la console active, vous pouvez également ajouter *artifacts/{os}-{arch}/stage2* à la variable PATH.</span><span class="sxs-lookup"><span data-stu-id="21eca-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="21eca-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21eca-166">See also</span></span>

- [<span data-ttu-id="21eca-167">Common Language Runtime .NET Core (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="21eca-167">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
- [<span data-ttu-id="21eca-168">Guide du développeur de l’interface CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="21eca-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [<span data-ttu-id="21eca-169">Empaquetage de la distribution de .NET Core</span><span class="sxs-lookup"><span data-stu-id="21eca-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
