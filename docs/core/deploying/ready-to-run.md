---
title: Présentation du déploiement de ReadyToRun
description: Découvrez les déploiements ReadyToRun et les raisons pour lesquelles vous devez envisager de l’utiliser dans le cadre de la publication de votre application avec .NET 5 et .NET Core 3,0 et versions ultérieures.
author: davidwr
ms.author: davidwr
ms.date: 09/21/2020
ms.openlocfilehash: b4052a0c0f4ed9f6cfd273abe5ef45d018bd0ae0
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654962"
---
# <a name="readytorun-compilation"></a><span data-ttu-id="7c887-103">Compilation ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="7c887-103">ReadyToRun Compilation</span></span>

<span data-ttu-id="7c887-104">Le temps de démarrage et la latence de l’application .NET peuvent être améliorés en compilant vos assemblys d’application au format ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="7c887-104">.NET application startup time and latency can be improved by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="7c887-105">R2R est une forme de compilation ahead-of-time (AOT).</span><span class="sxs-lookup"><span data-stu-id="7c887-105">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="7c887-106">Les fichiers binaires R2R améliorent les performances de démarrage en réduisant la quantité de travail que le compilateur juste-à-temps (JIT) doit faire lorsque votre application est chargée.</span><span class="sxs-lookup"><span data-stu-id="7c887-106">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="7c887-107">Les fichiers binaires contiennent du code natif similaire à ce que la compilation JIT produirait.</span><span class="sxs-lookup"><span data-stu-id="7c887-107">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="7c887-108">Cependant, les fichiers binaires R2R sont plus grands, car ils contiennent à la fois le code du langage intermédiaire (IL), qui est toujours nécessaire pour certains scénarios, et la version native du même code.</span><span class="sxs-lookup"><span data-stu-id="7c887-108">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="7c887-109">R2R est disponible uniquement lorsque vous publiez une application qui cible des environnements d’exécution spécifiques (RID) tels que Linux x64 ou Windows x64.</span><span class="sxs-lookup"><span data-stu-id="7c887-109">R2R is only available when you publish an app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="7c887-110">Pour compiler votre projet en tant que ReadyToRun, l’application doit être publiée avec la propriété PublishReadyToRun définie sur true.</span><span class="sxs-lookup"><span data-stu-id="7c887-110">To compile your project as ReadyToRun, the application must be published with the PublishReadyToRun property set to true.</span></span>

<span data-ttu-id="7c887-111">Il existe deux façons de publier votre application en tant que ReadyToRun :</span><span class="sxs-lookup"><span data-stu-id="7c887-111">There are two ways to publish your app as ReadyToRun:</span></span>

01. <span data-ttu-id="7c887-112">Spécifiez l’indicateur PublishReadyToRun directement à la commande dotnet publish.</span><span class="sxs-lookup"><span data-stu-id="7c887-112">Specify the PublishReadyToRun flag directly to the dotnet publish command.</span></span> <span data-ttu-id="7c887-113">Pour plus d’informations, consultez [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="7c887-113">See [dotnet publish](../tools/dotnet-publish.md) for details.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
    ```

02. <span data-ttu-id="7c887-114">Spécifier la propriété dans le projet</span><span class="sxs-lookup"><span data-stu-id="7c887-114">Specify the property in the project</span></span>

    - <span data-ttu-id="7c887-115">Ajoutez le `<PublishReadyToRun>` paramètre à votre projet.</span><span class="sxs-lookup"><span data-stu-id="7c887-115">Add the `<PublishReadyToRun>` setting to your project.</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

    - <span data-ttu-id="7c887-116">Publiez l’application sans paramètres spéciaux.</span><span class="sxs-lookup"><span data-stu-id="7c887-116">Publish the application without any special parameters.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64
    ```

## <a name="impact-of-using-the-readytorun-feature"></a><span data-ttu-id="7c887-117">Impact de l’utilisation de la fonctionnalité ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="7c887-117">Impact of using the ReadyToRun feature</span></span>

<span data-ttu-id="7c887-118">La compilation à l’avance a un impact complexe sur les performances des applications, ce qui peut être difficile à prédire.</span><span class="sxs-lookup"><span data-stu-id="7c887-118">Ahead-of-time compilation has complex performance impact on application performance, which may be difficult to predict.</span></span> <span data-ttu-id="7c887-119">En général, la taille d’un assembly est comprise entre deux et trois fois plus grand.</span><span class="sxs-lookup"><span data-stu-id="7c887-119">In general, the size of an assembly will grow to between two to three times larger.</span></span> <span data-ttu-id="7c887-120">Cette augmentation de la taille physique du fichier peut réduire les performances de chargement de l’assembly à partir du disque et augmenter la plage de travail du processus.</span><span class="sxs-lookup"><span data-stu-id="7c887-120">This increase in the physical size of the file may reduce the performance of loading the assembly from disk, and increase working set of the process.</span></span> <span data-ttu-id="7c887-121">Toutefois, en retour, le nombre de méthodes compilées au moment de l’exécution est généralement réduit de façon significative.</span><span class="sxs-lookup"><span data-stu-id="7c887-121">However, in return the number of methods compiled at runtime is typically reduced substantially.</span></span> <span data-ttu-id="7c887-122">Le résultat est que la plupart des applications qui tirent de grandes quantités de code reçoivent des avantages en matière de performances en activant ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="7c887-122">The result is that most applications that large amounts of code receive large performance benefits from enabling ReadyToRun.</span></span> <span data-ttu-id="7c887-123">Les applications, qui ont de petites quantités de code ne subiront probablement pas une amélioration significative de l’activation de ReadyToRun, car les bibliothèques du Runtime .NET ont déjà été précompilées avec ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="7c887-123">Applications, which have small amounts of code will likely not experience a significant improvement from enabling ReadyToRun, as the .NET runtime libraries have already been precompiled with ReadyToRun.</span></span>

<span data-ttu-id="7c887-124">L’amélioration du démarrage décrite ici s’applique non seulement au démarrage de l’application, mais également à la première utilisation du code dans l’application.</span><span class="sxs-lookup"><span data-stu-id="7c887-124">The startup improvement discussed here applies not only to application startup, but also to the first use of any code in the application.</span></span> <span data-ttu-id="7c887-125">Par exemple, ReadyToRun peut être utilisé pour réduire la latence de la réponse de la première utilisation de l’API Web dans une application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7c887-125">For instance, ReadyToRun can be used to reduce the response latency of the first use  of Web API in an ASP.NET application.</span></span>

### <a name="interaction-with-tiered-compilation"></a><span data-ttu-id="7c887-126">Interaction avec la compilation à plusieurs niveaux</span><span class="sxs-lookup"><span data-stu-id="7c887-126">Interaction with tiered compilation</span></span>

<span data-ttu-id="7c887-127">La génération anticipée n’est pas aussi hautement optimisée que le code produit par le JIT.</span><span class="sxs-lookup"><span data-stu-id="7c887-127">Ahead-of-time generated is not as highly optimized as code produced by the JIT.</span></span> <span data-ttu-id="7c887-128">Pour résoudre ce problème, la compilation à plusieurs niveaux remplace les méthodes ReadyToRun couramment utilisées par les méthodes générées juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="7c887-128">To address this issue, tiered compilation will replace commonly used ReadyToRun methods with JIT-generated methods.</span></span>

## <a name="how-is-the-set-of-precompiled-assemblies-chosen"></a><span data-ttu-id="7c887-129">Comment l’ensemble d’assemblys précompilés est-il choisi ?</span><span class="sxs-lookup"><span data-stu-id="7c887-129">How is the set of precompiled assemblies chosen?</span></span>

<span data-ttu-id="7c887-130">Le kit de développement logiciel (SDK) précompile les assemblys qui sont distribués avec l’application.</span><span class="sxs-lookup"><span data-stu-id="7c887-130">The SDK will precompile the assemblies that are distributed with the application.</span></span> <span data-ttu-id="7c887-131">Pour les applications autonomes, cet ensemble d’assemblys inclut le Framework.</span><span class="sxs-lookup"><span data-stu-id="7c887-131">For self-contained applications, this set of assemblies will include the framework.</span></span> <span data-ttu-id="7c887-132">Les binaires C++/CLI ne sont pas éligibles pour la compilation ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="7c887-132">C++/CLI binaries are not eligible for ReadyToRun compilation.</span></span>

## <a name="how-is-the-set-of-methods-to-precompile-chosen"></a><span data-ttu-id="7c887-133">Comment l’ensemble de méthodes à précompiler est-il choisi ?</span><span class="sxs-lookup"><span data-stu-id="7c887-133">How is the set of methods to precompile chosen?</span></span>

<span data-ttu-id="7c887-134">Le compilateur tente de précompiler autant de méthodes que possible.</span><span class="sxs-lookup"><span data-stu-id="7c887-134">The compiler will attempt to pre-compile as many methods as it can.</span></span> <span data-ttu-id="7c887-135">Toutefois, différentes raisons pour lesquelles il n’est pas prévu d’utiliser la fonctionnalité ReadyToRun empêchent l’exécution du JIT.</span><span class="sxs-lookup"><span data-stu-id="7c887-135">However various reasons it is not expected that using the ReadyToRun feature will result in preventing the JIT from executing.</span></span>

<span data-ttu-id="7c887-136">Ces raisons peuvent inclure, mais ne sont pas limitées à :</span><span class="sxs-lookup"><span data-stu-id="7c887-136">Such reasons may include, but are not limited to:</span></span>

- <span data-ttu-id="7c887-137">Utilisation de types génériques définis dans des assemblys séparés</span><span class="sxs-lookup"><span data-stu-id="7c887-137">Use of generic types defined in separate assemblies</span></span>
- <span data-ttu-id="7c887-138">Interopérabilité avec du code natif</span><span class="sxs-lookup"><span data-stu-id="7c887-138">Interop with native code</span></span>
- <span data-ttu-id="7c887-139">Utilisation des intrinsèques matériels que le compilateur ne peut pas prouver pouvoir utiliser sur un ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="7c887-139">Use of hardware intrinsics that the compiler cannot prove are safe to use on a target machine</span></span>
- <span data-ttu-id="7c887-140">Certains modèles de langage intermédiaire inhabituels</span><span class="sxs-lookup"><span data-stu-id="7c887-140">Certain unusual IL patterns</span></span>
- <span data-ttu-id="7c887-141">Création de méthodes dynamiques via la réflexion, ou LINQ</span><span class="sxs-lookup"><span data-stu-id="7c887-141">Dynamic method creation via reflection, or LINQ</span></span>

## <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="7c887-142">Restrictions d’architecture/de multiplateforme</span><span class="sxs-lookup"><span data-stu-id="7c887-142">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="7c887-143">Pour certaines plateformes du kit de développement logiciel (SDK), le compilateur ReadyToRun peut effectuer une compilation croisée pour d’autres plateformes cibles.</span><span class="sxs-lookup"><span data-stu-id="7c887-143">For some SDK platforms, the ReadyToRun compiler is capable of cross-compiling for other target platforms.</span></span> <span data-ttu-id="7c887-144">Les cibles de compilation prises en charge sont décrites dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="7c887-144">Supported compilation targets are described in the table below.</span></span>

| <span data-ttu-id="7c887-145">Plateforme du Kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="7c887-145">SDK platform</span></span> | <span data-ttu-id="7c887-146">Plateformes cibles prises en charge</span><span class="sxs-lookup"><span data-stu-id="7c887-146">Supported target platforms</span></span> |
| ------------ | --------------------------- |
| <span data-ttu-id="7c887-147">Windows X64</span><span class="sxs-lookup"><span data-stu-id="7c887-147">Windows X64</span></span>  | <span data-ttu-id="7c887-148">Windows x86, Windows x64, Windows ARM32, Windows ARM64</span><span class="sxs-lookup"><span data-stu-id="7c887-148">Windows X86, Windows X64, Windows ARM32, Windows ARM64</span></span> |
| <span data-ttu-id="7c887-149">Windows x86</span><span class="sxs-lookup"><span data-stu-id="7c887-149">Windows X86</span></span>  | <span data-ttu-id="7c887-150">Windows x86, Windows ARM32</span><span class="sxs-lookup"><span data-stu-id="7c887-150">Windows X86, Windows ARM32</span></span> |
| <span data-ttu-id="7c887-151">Linux X64</span><span class="sxs-lookup"><span data-stu-id="7c887-151">Linux X64</span></span>    | <span data-ttu-id="7c887-152">Linux x86, Linux x64, Linux ARM32, Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="7c887-152">Linux X86, Linux X64, Linux ARM32, Linux ARM64</span></span> |
| <span data-ttu-id="7c887-153">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="7c887-153">Linux ARM32</span></span>  | <span data-ttu-id="7c887-154">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="7c887-154">Linux ARM32</span></span> |
| <span data-ttu-id="7c887-155">ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="7c887-155">Linux ARM64</span></span>  | <span data-ttu-id="7c887-156">ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="7c887-156">Linux ARM64</span></span> |
| <span data-ttu-id="7c887-157">macOS x64</span><span class="sxs-lookup"><span data-stu-id="7c887-157">macOS X64</span></span>    | <span data-ttu-id="7c887-158">macOS x64</span><span class="sxs-lookup"><span data-stu-id="7c887-158">macOS X64</span></span> |
