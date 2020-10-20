---
title: Ciblage multiplateforme pour les bibliothèques .NET
description: Meilleures pratiques recommandées pour la création de bibliothèques .NET multiplateformes.
ms.date: 08/12/2019
ms.openlocfilehash: 6309e300861ab286dcaba3256267b3459e6e0d10
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223338"
---
# <a name="cross-platform-targeting"></a><span data-ttu-id="662ce-103">Ciblage multiplateforme</span><span class="sxs-lookup"><span data-stu-id="662ce-103">Cross-platform targeting</span></span>

<span data-ttu-id="662ce-104">L’infrastructure .NET moderne prend en charge plusieurs systèmes d’exploitation et appareils.</span><span class="sxs-lookup"><span data-stu-id="662ce-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="662ce-105">Il est important que les bibliothèques .NET open source prennent en charge autant de développeurs que possible, que ce soit pour développer un site Web ASP.NET hébergé dans Azure ou un jeu .NET dans Unity.</span><span class="sxs-lookup"><span data-stu-id="662ce-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="662ce-106">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="662ce-106">.NET Standard</span></span>

<span data-ttu-id="662ce-107">.NET Standard est la meilleure façon d’ajouter une prise en charge multiplateforme à une bibliothèque .NET.</span><span class="sxs-lookup"><span data-stu-id="662ce-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="662ce-108">[.NET Standard](../net-standard.md) est une spécification des API .NET disponibles sur toutes les implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="662ce-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="662ce-109">Le ciblage .NET Standard vous permet de produire des bibliothèques qui sont contraints d’utiliser des API qui se trouvent dans une version donnée de .NET Standard, ce qui signifie qu’elle est utilisable par toutes les plateformes qui implémentent cette version de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="662ce-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of .NET Standard.</span></span>

<span data-ttu-id="662ce-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="662ce-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="662ce-111">Le ciblage .NET Standard et la compilation avec succès de votre projet ne garantissent pas que la bibliothèque fonctionne correctement sur toutes les plateformes :</span><span class="sxs-lookup"><span data-stu-id="662ce-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="662ce-112">des API propres à une plateforme échoueront sur d’autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="662ce-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="662ce-113">Par exemple, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> réussiront sur Windows mais lèveront une exception <xref:System.PlatformNotSupportedException> s’ils sont utilisés sur n’importe quel autre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="662ce-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="662ce-114">Les API peuvent se comporter différemment.</span><span class="sxs-lookup"><span data-stu-id="662ce-114">APIs can behave differently.</span></span> <span data-ttu-id="662ce-115">Par exemple, les API de réflexion ont des caractéristiques de performances différentes lorsqu’une application utilise la compilation AOT (Ahead Of Time) sur iOS ou UWP.</span><span class="sxs-lookup"><span data-stu-id="662ce-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="662ce-116">L’équipe .NET [propose un analyseur Roslyn](../analyzers/api-analyzer.md) pour vous aider à détecter les éventuels problèmes.</span><span class="sxs-lookup"><span data-stu-id="662ce-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="662ce-117">✔️ À FAIRE : Commencer par inclure une cible `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="662ce-117">✔️ DO start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="662ce-118">La plupart des bibliothèques à usage général ne devraient pas avoir besoin d’API en dehors de .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="662ce-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="662ce-119">.NET Standard 2.0 est pris en charge par toutes les plateformes modernes et constitue la méthode recommandée pour prendre en charge plusieurs plateformes avec une cible.</span><span class="sxs-lookup"><span data-stu-id="662ce-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="662ce-120">❌ Évitez d’inclure une `netstandard1.x` cible.</span><span class="sxs-lookup"><span data-stu-id="662ce-120">❌ AVOID including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="662ce-121">.NET Standard 1.x est distribué sous la forme d’un ensemble précis de packages NuGet, qui crée un grand graphique des dépendances de package et amène les développeurs à télécharger un grand nombre de packages lors de la génération.</span><span class="sxs-lookup"><span data-stu-id="662ce-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="662ce-122">Les plateformes .NET modernes, y compris .NET Framework 4.6.1, UWP et Xamarin, prennent toutes en charge .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="662ce-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="662ce-123">Vous devez uniquement cibler .NET Standard 1.x si vous avez besoin de cibler une plateforme plus ancienne.</span><span class="sxs-lookup"><span data-stu-id="662ce-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="662ce-124">✔️ À FAIRE  : Inclure une cible `netstandard2.0` si vous avez besoin d’une cible `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="662ce-124">✔️ DO include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="662ce-125">Toutes les plateformes prenant en charge .NET Standard 2.0 utiliseront la cible `netstandard2.0` et bénéficieront d’un graphique de packages plus petit, tandis que les anciennes plateformes continueront de fonctionner et utiliseront la cible `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="662ce-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="662ce-126">❌ N’incluez pas de cible .NET Standard si la bibliothèque s’appuie sur un modèle d’application spécifique à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="662ce-126">❌ DO NOT include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="662ce-127">Par exemple, une bibliothèque de boîte à outils de contrôle UWP dépend d’un modèle d’application uniquement disponible sur UWP.</span><span class="sxs-lookup"><span data-stu-id="662ce-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="662ce-128">Les API spécifiques à un modèle d’application ne seront pas disponibles dans .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="662ce-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="662ce-129">Multi-ciblage</span><span class="sxs-lookup"><span data-stu-id="662ce-129">Multi-targeting</span></span>

<span data-ttu-id="662ce-130">Parfois, vous avez besoin accéder à des API spécifiques à une infrastructure à partir de vos bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="662ce-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="662ce-131">La meilleure façon d’appeler des API spécifiques à une infrastructure consiste à utiliser le multi-ciblage, qui génère votre projet pour un grand nombre [d’infrastructures .NET cible](../frameworks.md) plutôt que pour une seule.</span><span class="sxs-lookup"><span data-stu-id="662ce-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="662ce-132">Pour éviter à vos consommateurs d’avoir à créer pour chaque infrastructure, vous devez vous efforcer d’avoir une sortie Standard .NET ainsi qu’une ou plusieurs sorties spécifiques à l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="662ce-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="662ce-133">Avec le multi-ciblage, tous les assemblys sont empaquetés dans un même package NuGet.</span><span class="sxs-lookup"><span data-stu-id="662ce-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="662ce-134">Les consommateurs peuvent ensuite référencer le même package, et NuGet choisit l’implémentation appropriée.</span><span class="sxs-lookup"><span data-stu-id="662ce-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="662ce-135">Votre bibliothèque .NET Standard sert de bibliothèque de secours utilisée partout, sauf si votre package NuGet offre une implémentation spécifique à une infrastructure.</span><span class="sxs-lookup"><span data-stu-id="662ce-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="662ce-136">Le multi-ciblage permet d’utiliser la compilation conditionnelle dans votre code et d’appeler des API spécifiques à une infrastructure.</span><span class="sxs-lookup"><span data-stu-id="662ce-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="662ce-137">![Package NuGet avec plusieurs assemblys](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Package NuGet avec plusieurs assemblys")</span><span class="sxs-lookup"><span data-stu-id="662ce-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="662ce-138">✔️ À ENVISAGER : cibler des implémentations .NET en plus de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="662ce-138">✔️ CONSIDER targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="662ce-139">Le ciblage d’implémentations .NET vous permet d’appeler des API spécifiques à la plateforme qui sont trouvent en dehors de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="662ce-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="662ce-140">Ne supprimez pas la prise en charge de .NET Standard lorsque vous effectuez cette opération.</span><span class="sxs-lookup"><span data-stu-id="662ce-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="662ce-141">Au lieu de cela, levez une exception à partir de l’implémentation et offrez la fonctionnalité API.</span><span class="sxs-lookup"><span data-stu-id="662ce-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="662ce-142">De cette façon, votre bibliothèque peut être utilisée partout et prend en charge le runtime des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="662ce-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

```csharp
public static class GpsLocation
{
    // This project uses multi-targeting to expose device-specific APIs to .NET Standard.
    public static async Task<(double latitude, double longitude)> GetCoordinatesAsync()
    {
#if NET461
        return CallDotNetFramworkApi();
#elif WINDOWS_UWP
        return CallUwpApi();
#else
        throw new PlatformNotSupportedException();
#endif
    }

    // Allows callers to check without having to catch PlatformNotSupportedException
    // or replicating the OS check.
    public static bool IsSupported
    {
        get
        {
#if NET461 || WINDOWS_UWP
            return true;
#else
            return false;
#endif
        }
    }
}
```

<span data-ttu-id="662ce-143">❌ Évitez le multi-ciblage et le ciblage .NET Standard, si votre code source est le même pour toutes les cibles.</span><span class="sxs-lookup"><span data-stu-id="662ce-143">❌ AVOID multi-targeting as well as targeting .NET Standard, if your source code is the same for all targets.</span></span>

> <span data-ttu-id="662ce-144">L’assembly .NET Standard sera automatiquement utilisé par NuGet.</span><span class="sxs-lookup"><span data-stu-id="662ce-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="662ce-145">Le ciblage d’implémentations .NET individuelles augmente la taille `*.nupkg` sans apporter d’avantage.</span><span class="sxs-lookup"><span data-stu-id="662ce-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="662ce-146">✔️ À ENVISAGER : Ajouter une cible pour `net461` lorsque que vous proposez une cible `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="662ce-146">✔️ CONSIDER adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span>

> <span data-ttu-id="662ce-147">L’utilisation de .NET Standard 2.0 dans .NET Framework entraîne certains problèmes qui ont été résolus dans .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="662ce-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="662ce-148">Vous pouvez améliorer l’expérience des développeurs qui utilisent toujours .NET Framework 4.6.1 - 4.7.1 en leur offrant un fichier binaire conçu pour .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="662ce-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="662ce-149">✔️ À FAIRE : Distribuer votre bibliothèque à l’aide d’un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="662ce-149">✔️ DO distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="662ce-150">NuGet sélectionnera la meilleure cible pour les développeurs et leur évitera d’avoir à choisir l’implémentation appropriée.</span><span class="sxs-lookup"><span data-stu-id="662ce-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="662ce-151">✔️ À FAIRE : Utiliser la propriété `TargetFrameworks` d’un fichier projet lors du multi-ciblage.</span><span class="sxs-lookup"><span data-stu-id="662ce-151">✔️ DO use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="662ce-152">✔️ À ENVISAGER : Utiliser [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) lors du multi-ciblage pour UWP et Xamarin car cela simplifie considérablement votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="662ce-152">✔️ CONSIDER using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="662ce-153">Anciennes cibles</span><span class="sxs-lookup"><span data-stu-id="662ce-153">Older targets</span></span>

<span data-ttu-id="662ce-154">.NET prend en charge le ciblage de versions .NET Framework qui ne sont plus prises en charge depuis longtemps, ainsi que les plateformes qui ne sont plus couramment utilisées.</span><span class="sxs-lookup"><span data-stu-id="662ce-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="662ce-155">Bien qu'il soit utile de faire fonctionner votre bibliothèque sur autant de cibles que possible, le fait de devoir contourner des API manquantes peut entraîner d’importants frais généraux.</span><span class="sxs-lookup"><span data-stu-id="662ce-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="662ce-156">Nous estimons que certaines infrastructures ne valent plus la peine d'être ciblées, compte tenu de leur portée et de leurs limites.</span><span class="sxs-lookup"><span data-stu-id="662ce-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="662ce-157">❌ N’incluez pas une cible de bibliothèque de classes portable (PCL).</span><span class="sxs-lookup"><span data-stu-id="662ce-157">❌ DO NOT include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="662ce-158">Par exemple : `portable-net45+win8+wpa81+wp8`.</span><span class="sxs-lookup"><span data-stu-id="662ce-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="662ce-159">.NET standard est la méthode moderne de prendre en charge les bibliothèques .NET multiplateformes et remplace les PCL.</span><span class="sxs-lookup"><span data-stu-id="662ce-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="662ce-160">❌ N’incluez pas de cibles pour les plateformes .NET qui ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="662ce-160">❌ DO NOT include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="662ce-161">Par exemple, `SL4`, `WP`.</span><span class="sxs-lookup"><span data-stu-id="662ce-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="662ce-162">[Précédent](get-started.md) 
> [Suivant](strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="662ce-162">[Previous](get-started.md)
[Next](strong-naming.md)</span></span>
