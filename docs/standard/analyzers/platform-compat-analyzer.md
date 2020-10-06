---
title: Analyseur de compatibilité de plateforme
description: Analyseur Roslyn qui peut aider à détecter les problèmes de compatibilité de plateforme dans les applications et les bibliothèques multiplateforme.
author: buyaa-n
ms.date: 09/17/2020
ms.openlocfilehash: fcd5ec755789ff7f2472d8077dd52f321bf9f167
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756180"
---
# <a name="platform-compatibility-analyzer"></a><span data-ttu-id="fe033-103">Analyseur de compatibilité de plateforme</span><span class="sxs-lookup"><span data-stu-id="fe033-103">Platform compatibility analyzer</span></span>

<span data-ttu-id="fe033-104">Vous avez probablement entendu parler de « One .NET » : une plateforme unique et unifiée pour la création de n’importe quel type d’application.</span><span class="sxs-lookup"><span data-stu-id="fe033-104">You've probably heard the motto of "One .NET": a single, unified platform for building any type of application.</span></span> <span data-ttu-id="fe033-105">Le kit de développement logiciel (SDK) .NET 5,0 comprend ASP.NET Core, Entity Framework Core, WinForms, WPF, Xamarin et ML.NET, et ajoute la prise en charge d’autres plateformes au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="fe033-105">The .NET 5.0 SDK includes ASP.NET Core, Entity Framework Core, WinForms, WPF, Xamarin, and ML.NET, and will add support for more platforms over time.</span></span> <span data-ttu-id="fe033-106">.NET 5,0 s’efforce de fournir une expérience dans laquelle vous n’avez pas à vous soucier des différentes versions de .NET, mais ne tente pas d’effectuer une abstraction totale du système d’exploitation sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="fe033-106">.NET 5.0 strives to provide an experience where you don't have to reason about the different flavors of .NET, but doesn't attempt to fully abstract away the underlying operating system (OS).</span></span> <span data-ttu-id="fe033-107">Vous continuerez à être en mesure d’appeler des API spécifiques à la plateforme, par exemple, P/Invoke, WinRT ou les liaisons Xamarin pour iOS et Android.</span><span class="sxs-lookup"><span data-stu-id="fe033-107">You'll continue to be able to call platform-specific APIs, for example, P/Invokes, WinRT, or the Xamarin bindings for iOS and Android.</span></span>

<span data-ttu-id="fe033-108">Toutefois, l’utilisation d’API spécifiques à une plateforme sur un composant signifie que le code ne fonctionne plus sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="fe033-108">But using platform-specific APIs on a component means the code no longer works across all platforms.</span></span> <span data-ttu-id="fe033-109">Nous avions besoin d’une méthode pour la détecter au moment de la conception afin que les développeurs reçoivent des diagnostics lorsqu’ils utilisent par inadvertance des API spécifiques à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="fe033-109">We needed a way to detect this at design time so developers get diagnostics when they inadvertently use platform-specific APIs.</span></span> <span data-ttu-id="fe033-110">Pour atteindre cet objectif, .NET 5,0 introduit l' [Analyseur de compatibilité de plateforme](/visualstudio/code-quality/ca1416) et les API complémentaires pour aider les développeurs à identifier et utiliser les API spécifiques à la plateforme, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="fe033-110">To achieve this goal, .NET 5.0 introduces the [platform compatibility analyzer](/visualstudio/code-quality/ca1416) and complementary APIs to help developers identify and use platform-specific APIs where appropriate.</span></span>
<span data-ttu-id="fe033-111">Les nouvelles API sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fe033-111">The new APIs include:</span></span>

- <span data-ttu-id="fe033-112"><xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> pour annoter des API comme étant spécifiques <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> à une plateforme et pour annoter des API non prises en charge sur un système d’exploitation particulier.</span><span class="sxs-lookup"><span data-stu-id="fe033-112"><xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> to annotate APIs as being platform-specific and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> to annotate APIs as being unsupported on a particular OS.</span></span> <span data-ttu-id="fe033-113">Ces attributs peuvent éventuellement inclure le numéro de version et ont déjà été appliqués à certaines API spécifiques à la plateforme dans les bibliothèques .NET de base.</span><span class="sxs-lookup"><span data-stu-id="fe033-113">These attributes can optionally include the version number, and have already been applied to some platform-specific APIs in the core .NET libraries.</span></span>
- <span data-ttu-id="fe033-114">`Is<Platform>()` et `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` les méthodes statiques de la <xref:System.OperatingSystem?displayProperty=nameWithType> classe pour appeler sans risque des API spécifiques à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="fe033-114">`Is<Platform>()` and `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` static methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class for safely calling platform-specific APIs.</span></span> <span data-ttu-id="fe033-115">Par exemple, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> peut être utilisé pour protéger un appel à une API spécifique à Windows, et <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> () peut être utilisé pour protéger un appel d’API spécifique à la version de Windows.</span><span class="sxs-lookup"><span data-stu-id="fe033-115">For example, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> can be used to guard a call to a Windows-specific API, and <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>() can be used to guard a versioned Windows-specific API call.</span></span> <span data-ttu-id="fe033-116">Consultez ces [exemples](#guard-platform-specific-apis-with-guard-methods) illustrant comment ces méthodes peuvent être utilisées comme protecteurs de références d’API spécifiques à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="fe033-116">See these [examples](#guard-platform-specific-apis-with-guard-methods) of how these methods can be used as guards of platform-specific API references.</span></span>

> [!TIP]
> <span data-ttu-id="fe033-117">L’analyseur de compatibilité de la plateforme met à niveau et remplace la fonctionnalité de [détection des problèmes inter-plateformes](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues) de l' [analyseur d’API .net](../../standard/analyzers/api-analyzer.md).</span><span class="sxs-lookup"><span data-stu-id="fe033-117">The platform compatibility analyzer upgrades and replaces the [Discovering cross-platform issues](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues) feature of the [.NET API analyzer](../../standard/analyzers/api-analyzer.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fe033-118">Prérequis</span><span class="sxs-lookup"><span data-stu-id="fe033-118">Prerequisites</span></span>

<span data-ttu-id="fe033-119">L’analyseur de compatibilité de la plateforme est l’un des analyseurs de la qualité du code Roslyn.</span><span class="sxs-lookup"><span data-stu-id="fe033-119">The platform compatibility analyzer is one of the Roslyn code quality analyzers.</span></span> <span data-ttu-id="fe033-120">À compter de .NET 5,0, ces analyseurs sont [inclus dans le kit de développement logiciel (SDK) .net](../../fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="fe033-120">Starting in .NET 5.0, these analyzers are [included with the .NET SDK](../../fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="fe033-121">L’analyseur de compatibilité de plateforme est activé par défaut uniquement pour les projets qui ciblent `net5.0` ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="fe033-121">The platform compatibility analyzer is enabled by default only for projects that target `net5.0` or a later version.</span></span> <span data-ttu-id="fe033-122">Toutefois, vous pouvez l' [activer](/visualstudio/code-quality/ca1416.md#configurability) pour les projets qui ciblent d’autres infrastructures.</span><span class="sxs-lookup"><span data-stu-id="fe033-122">However, you can [enable](/visualstudio/code-quality/ca1416.md#configurability) it for projects that target other frameworks.</span></span>

## <a name="how-the-analyzer-determines-platform-dependency"></a><span data-ttu-id="fe033-123">Comment l’analyseur détermine la dépendance de la plateforme</span><span class="sxs-lookup"><span data-stu-id="fe033-123">How the analyzer determines platform dependency</span></span>

- <span data-ttu-id="fe033-124">Une **API non attributée** est considérée pour fonctionner sur **toutes les plateformes de système d’exploitation**.</span><span class="sxs-lookup"><span data-stu-id="fe033-124">An **unattributed API** is considered to work on **all OS platforms**.</span></span>
- <span data-ttu-id="fe033-125">Une API marquée avec `[SupportedOSPlatform("platform")]` est considérée comme portable uniquement pour le système d’exploitation spécifié `platform` .</span><span class="sxs-lookup"><span data-stu-id="fe033-125">An API marked with `[SupportedOSPlatform("platform")]` is considered only portable to the specified OS `platform`.</span></span>
  - <span data-ttu-id="fe033-126">L’attribut peut être appliqué plusieurs fois pour indiquer la **prise en charge de plusieurs plateformes** ( `[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]` ).</span><span class="sxs-lookup"><span data-stu-id="fe033-126">The attribute can be applied multiple times to indicate **multiple platform support** (`[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]`).</span></span>
  - <span data-ttu-id="fe033-127">L’analyseur produira un **Avertissement** si les API spécifiques à la plateforme sont référencées sans un **contexte de plateforme**approprié :</span><span class="sxs-lookup"><span data-stu-id="fe033-127">The analyzer will produce a **warning** if platform-specific APIs are referenced without a proper **platform context**:</span></span>
    - <span data-ttu-id="fe033-128">**Avertit** si le projet ne cible pas la plateforme prise en charge (par exemple, un appel d’API spécifique à Windows et les cibles de projet `<TargetFramework>net5.0-ios14.0</TargetFramework>` ).</span><span class="sxs-lookup"><span data-stu-id="fe033-128">**Warns** if the project doesn't target the supported platform (for example, a Windows-specific API call and the project targets `<TargetFramework>net5.0-ios14.0</TargetFramework>`).</span></span>
    - <span data-ttu-id="fe033-129">**Avertit** si le projet est multi-ciblé ( `<TargetFramework>net5.0</TargetFramework>` ).</span><span class="sxs-lookup"><span data-stu-id="fe033-129">**Warns** if the project is multi-targeted (`<TargetFramework>net5.0</TargetFramework>`).</span></span>
    - <span data-ttu-id="fe033-130">**N’avertit pas** si l’API spécifique à la plateforme est référencée dans un projet qui cible l’une des **plateformes spécifiées** (par exemple, pour un appel d’API spécifique à Windows et les cibles de projet `<TargetFramework>net5.0-windows</TargetFramework>` ).</span><span class="sxs-lookup"><span data-stu-id="fe033-130">**Doesn't warn** if the platform-specific API is referenced within a project that targets any of the **specified platforms** (for example, for a Windows-specific API call and the project targets `<TargetFramework>net5.0-windows</TargetFramework>`).</span></span>
    - <span data-ttu-id="fe033-131">**N’avertit pas** si l’appel d’API spécifique à la plateforme est protégé par les méthodes de vérification de plateforme correspondantes (par exemple, `if(OperatingSystem.IsWindows())` ).</span><span class="sxs-lookup"><span data-stu-id="fe033-131">**Doesn't warn** if the platform-specific API call is guarded by corresponding platform-check methods (for example, `if(OperatingSystem.IsWindows())`).</span></span>
    - <span data-ttu-id="fe033-132">**N’avertit pas** si l’API spécifique à la plateforme est référencée à partir du même contexte spécifique à la plateforme (le**site d’appel est également attribué** avec `[SupportedOSPlatform("platform")` ).</span><span class="sxs-lookup"><span data-stu-id="fe033-132">**Doesn't warn** if the platform-specific API is referenced from the same platform-specific context (**call site also attributed** with `[SupportedOSPlatform("platform")`).</span></span>
- <span data-ttu-id="fe033-133">Une API marquée avec `[UnsupportedOSPlatform("platform")]` est considérée comme non prise en charge uniquement sur le système d’exploitation spécifié `platform` , mais prise en charge pour toutes les autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="fe033-133">An API marked with `[UnsupportedOSPlatform("platform")]` is considered unsupported only on the specified OS `platform` but supported for all other platforms.</span></span>
  - <span data-ttu-id="fe033-134">L’attribut peut être appliqué plusieurs fois avec différentes plateformes, par exemple, `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]` .</span><span class="sxs-lookup"><span data-stu-id="fe033-134">The attribute can be applied multiple times with different platforms, for example, `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]`.</span></span>
  - <span data-ttu-id="fe033-135">L’analyseur génère un **Avertissement** uniquement si le `platform` est efficace pour le site d’appel :</span><span class="sxs-lookup"><span data-stu-id="fe033-135">The analyzer produces a **warning** only if the `platform` is effective for the call site:</span></span>
    - <span data-ttu-id="fe033-136">**Avertit** si le projet cible la plateforme dont l’attribut n’est pas pris en charge (par exemple, si l’API est attribuée avec `[UnsupportedOSPlatform("windows")]` et les cibles de site d’appel `<TargetFramework>net5.0-windows</TargetFramework>` ).</span><span class="sxs-lookup"><span data-stu-id="fe033-136">**Warns** if the project targets the platform that's attributed as unsupported (for example, if the API is attributed with `[UnsupportedOSPlatform("windows")]` and the call site targets `<TargetFramework>net5.0-windows</TargetFramework>`).</span></span>
    - <span data-ttu-id="fe033-137">**Avertit** si le projet est multi-ciblé et `platform` s’il est inclus dans le groupe d’éléments [MSBuild `<SupportedPlatform>` ](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) par défaut, ou `platform` s’il est inclus manuellement dans le `MSBuild` \<SupportedPlatform> groupe d’éléments :</span><span class="sxs-lookup"><span data-stu-id="fe033-137">**Warns** if the project is multi-targeted and the `platform` is included in the default [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) items group, or the `platform` is manually included within the `MSBuild` \<SupportedPlatform> items group:</span></span>

      ```XML
      <ItemGroup>
          <SupportedPlatform Include="platform" />
      </ItemGroup>
      ```

    - <span data-ttu-id="fe033-138">**Ne vous avertit** pas si vous créez une application qui ne cible pas la plateforme non prise en charge ou qui est multi-ciblée et que la plateforme n’est pas incluse dans le groupe d’éléments [ `<SupportedPlatform>` MSBuild](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) par défaut.</span><span class="sxs-lookup"><span data-stu-id="fe033-138">**Doesn't warn** if you're building an app that doesn't target the unsupported platform or is multi-targeted and the platform is not included in the default [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) items group.</span></span>
- <span data-ttu-id="fe033-139">Les deux attributs peuvent être instanciés avec ou sans numéros de version dans le cadre du nom de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="fe033-139">Both attributes can be instantiated with or without version numbers as part of the platform name.</span></span>
  - <span data-ttu-id="fe033-140">Les numéros de version sont au format `major.minor[.build[.revision]]` ; `major.minor` est requis et les `build` `revision` composants et sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="fe033-140">Version numbers are in the format of `major.minor[.build[.revision]]`; `major.minor` is required and the `build` and `revision` parts are optional.</span></span> <span data-ttu-id="fe033-141">Par exemple, « Windows 7.0 » indique la version de Windows 7,0, mais « Windows » est interprété comme étant Windows 0,0.</span><span class="sxs-lookup"><span data-stu-id="fe033-141">For example, "Windows7.0" indicates Windows version 7.0, but "Windows" is interpreted as Windows 0.0.</span></span>

<span data-ttu-id="fe033-142">Pour plus d’informations, consultez [des exemples de fonctionnement des attributs et des diagnostics qu’ils entraînent](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce).</span><span class="sxs-lookup"><span data-stu-id="fe033-142">For more information, see [examples of how the attributes work and what diagnostics they cause](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce).</span></span>

### <a name="advanced-scenarios-for-combining-attributes"></a><span data-ttu-id="fe033-143">Scénarios avancés pour la combinaison d’attributs</span><span class="sxs-lookup"><span data-stu-id="fe033-143">Advanced scenarios for combining attributes</span></span>

- <span data-ttu-id="fe033-144">Si une combinaison d' `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` attributs et est présente, tous les attributs sont regroupés par identificateur de plateforme de système d’exploitation :</span><span class="sxs-lookup"><span data-stu-id="fe033-144">If a combination of `[SupportedOSPlatform]` and `[UnsupportedOSPlatform]` attributes are present, all attributes are grouped by OS platform identifier:</span></span>
  - <span data-ttu-id="fe033-145">**Liste uniquement prise en charge**.</span><span class="sxs-lookup"><span data-stu-id="fe033-145">**Supported only list**.</span></span> <span data-ttu-id="fe033-146">Si la version la plus basse de chaque plateforme de système d’exploitation est un `[SupportedOSPlatform]` attribut, l’API est considérée comme uniquement prise en charge par les plateformes listées et non prise en charge par toutes les autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="fe033-146">If the lowest version for each OS platform is a `[SupportedOSPlatform]` attribute, the API is considered to only be supported by the listed platforms and unsupported by all other platforms.</span></span> <span data-ttu-id="fe033-147">Les attributs facultatifs `[UnsupportedOSPlatform]` pour chaque plateforme peuvent uniquement avoir une version plus récente de la version minimale prise en charge, ce qui indique que l’API est supprimée à partir de la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fe033-147">The optional `[UnsupportedOSPlatform]` attributes for each platform can only have higher version of the minimum supported version, which denotes that the API is removed starting from the specified version.</span></span>

    ```csharp
    // The API only supported on Windows 8.0 and later, not supported for all other.
    // The API is removed/unsupported from version 10.0.19041.0.
    [SupportedOSPlatform("windows8.0")]
    [UnsupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows80SupportFromCertainVersion();
    ```

  - <span data-ttu-id="fe033-148">**Liste uniquement non prise en charge**.</span><span class="sxs-lookup"><span data-stu-id="fe033-148">**Unsupported only list**.</span></span> <span data-ttu-id="fe033-149">Si la version la plus basse pour chaque plateforme de système d’exploitation est un `[UnsupportedOSPlatform]` attribut, l’API est considérée uniquement comme non prise en charge par les plateformes listées et prise en charge par toutes les autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="fe033-149">If the lowest version for each OS platform is an `[UnsupportedOSPlatform]` attribute, then the API is considered to only be unsupported by the listed platforms and supported by all other platforms.</span></span> <span data-ttu-id="fe033-150">La liste peut avoir `[SupportedOSPlatform]` un attribut avec la même plateforme, mais une version plus récente, ce qui indique que l’API est prise en charge à partir de cette version.</span><span class="sxs-lookup"><span data-stu-id="fe033-150">The list could have `[SupportedOSPlatform]` attribute with the same platform but a higher version, which denotes that the API is supported starting from that version.</span></span>

    ```csharp
    // The API was unsupported on Windows until version 10.0.19041.0.
    // The API is considered supported everywhere else without constraints.
    [UnsupportedOSPlatform("windows")]
    [SupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows8UnsupportFromWindows10();
    ```

  - <span data-ttu-id="fe033-151">**Liste incohérente**.</span><span class="sxs-lookup"><span data-stu-id="fe033-151">**Inconsistent list**.</span></span> <span data-ttu-id="fe033-152">Si la version la plus basse pour certaines plateformes est `[SupportedOSPlatform]` alors qu’elle est `[UnsupportedOSPlatform]` destinée à d’autres plateformes, elle est considérée comme étant incohérente, ce qui n’est pas pris en charge pour l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="fe033-152">If the lowest version for some platforms is `[SupportedOSPlatform]` while it is `[UnsupportedOSPlatform]` for other platforms, it's considered to be inconsistent, which is not supported for the analyzer.</span></span>
  - <span data-ttu-id="fe033-153">Si les versions les plus basses des `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` attributs et sont égales, l’analyseur considère la plateforme comme faisant partie de la **liste uniquement prise en charge**.</span><span class="sxs-lookup"><span data-stu-id="fe033-153">If the lowest versions of `[SupportedOSPlatform]` and `[UnsupportedOSPlatform]` attributes are equal, the analyzer considers the platform as part of the **Supported only list**.</span></span>
- <span data-ttu-id="fe033-154">Les attributs de plateforme peuvent être appliqués à des types, des membres (méthodes, champs, propriétés et événements) et à des assemblys avec des noms ou des versions de plateforme différents.</span><span class="sxs-lookup"><span data-stu-id="fe033-154">Platform attributes can be applied to types, members (methods, fields, properties, and events) and assemblies with different platform names or versions.</span></span>
  - <span data-ttu-id="fe033-155">Les attributs appliqués au niveau supérieur `target` affectent tous ses membres et types.</span><span class="sxs-lookup"><span data-stu-id="fe033-155">Attributes applied at the top level `target` affect all of its members and types.</span></span>
  - <span data-ttu-id="fe033-156">Les attributs de niveau enfant s’appliquent uniquement s’ils adhèrent à la règle. les annotations enfants peuvent limiter la prise en charge des plateformes, mais elles ne peuvent pas les élargir.</span><span class="sxs-lookup"><span data-stu-id="fe033-156">Child-level attributes only apply if they adhere to the rule "child annotations can narrow the platforms support, but they cannot widen it".</span></span>
    - <span data-ttu-id="fe033-157">Si le parent n’a que la liste des attributs **pris en charge** , les attributs des membres enfants ne peuvent pas ajouter de nouvelle prise en charge de plateforme, car cela permettrait d’étendre la prise en charge du parent</span><span class="sxs-lookup"><span data-stu-id="fe033-157">When parent has **Supported only** list, then child member attributes cannot add a new platform support, as that would be extending parent support.</span></span> <span data-ttu-id="fe033-158">La prise en charge d’une nouvelle plateforme peut uniquement être ajoutée au parent lui-même.</span><span class="sxs-lookup"><span data-stu-id="fe033-158">Support for a new platform can only be added to the parent itself.</span></span> <span data-ttu-id="fe033-159">Toutefois, l’enfant peut avoir l' `Supported` attribut pour la même plate-forme avec les versions ultérieures, ce qui réduit la prise en charge.</span><span class="sxs-lookup"><span data-stu-id="fe033-159">But the child can have the `Supported` attribute for the same platform with later versions as that narrows the support.</span></span> <span data-ttu-id="fe033-160">En outre, l’enfant peut avoir l' `Unsupported` attribut avec la même plateforme que celle qui restreint également la prise en charge du parent.</span><span class="sxs-lookup"><span data-stu-id="fe033-160">Also, the child can have the `Unsupported` attribute with the same platform as that also narrows parent support.</span></span>
    - <span data-ttu-id="fe033-161">Lorsque le parent n’a qu’une liste **non prise en charge** , les attributs des membres enfants peuvent ajouter la prise en charge d’une nouvelle plateforme, car cela réduit la prise en charge du parent.</span><span class="sxs-lookup"><span data-stu-id="fe033-161">When parent has **Unsupported only** list, then child member attributes can add support for a new platform, as that narrows parent support.</span></span> <span data-ttu-id="fe033-162">Mais il ne peut pas avoir l' `Supported` attribut pour la même plateforme que le parent, car cela étend la prise en charge du parent.</span><span class="sxs-lookup"><span data-stu-id="fe033-162">But it cannot have the `Supported` attribute for the same platform as the parent, because that extends parent support.</span></span> <span data-ttu-id="fe033-163">La prise en charge de la même plate-forme peut être ajoutée uniquement au parent où l’attribut d’origine `Unsupported` a été appliqué.</span><span class="sxs-lookup"><span data-stu-id="fe033-163">Support for the same platform can only be added to the parent where the original `Unsupported` attribute was applied.</span></span>
  - <span data-ttu-id="fe033-164">Si `[SupportedOSPlatform("platformVersion")]` est appliqué plus d’une fois pour une API portant le même `platform` nom, l’analyseur considère uniquement celui avec la version minimale.</span><span class="sxs-lookup"><span data-stu-id="fe033-164">If `[SupportedOSPlatform("platformVersion")]` is applied more than once for an API with the same `platform` name, the analyzer only considers the one with the minimum version.</span></span>
  - <span data-ttu-id="fe033-165">Si `[UnsupportedOSPlatform("platformVersion")]` est appliqué plus de deux fois pour une API portant le même `platform` nom, l’analyseur considère uniquement les deux avec les versions les plus anciennes.</span><span class="sxs-lookup"><span data-stu-id="fe033-165">If `[UnsupportedOSPlatform("platformVersion")]` is applied more than twice for an API with the same `platform` name, the analyzer only considers the two with the earliest versions.</span></span>

  > [!NOTE]
  > <span data-ttu-id="fe033-166">Une API qui était prise en charge initialement mais non prise en charge (supprimée) dans une version ultérieure n’est pas censée être reprise dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="fe033-166">An API that was supported initially but unsupported (removed) in a later version is not expected to get resupported in an even later version.</span></span>

### <a name="examples-of-how-the-attributes-work-and-what-diagnostics-they-produce"></a><span data-ttu-id="fe033-167">Exemples illustrant le fonctionnement des attributs et les diagnostics qu’ils produisent</span><span class="sxs-lookup"><span data-stu-id="fe033-167">Examples of how the attributes work and what diagnostics they produce</span></span>

  ```csharp
  // An API supported only on Windows.
  [SupportedOSPlatform("Windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  public void Caller()
  {
      WindowsOnlyApi(); // warns: 'WindowsOnlyApi' is supported on 'windows'

      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Windows'
      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Linux'
      SupportedOnWindowsAndLinuxOnly();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 8.0 and later
      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // for same platform analyzer only warn for the latest version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on android but supported on all other.
  [UnsupportedOSPlatform("android")]
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  public void Caller2()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'android'

      // warns:'StartedWindowsSupportFromVersion8' is unsupported on 'windows'
      // warns:'StartedWindowsSupportFromVersion8' is supported on 'windows' 8.0 and later
      StartedWindowsSupportFromVersion8();

      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is unsupported on 'windows'
      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is supported on 'windows' 8.0 and later
      // even there were 3 diagnostics found analyzer warn only for the first 2.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

## <a name="handle-reported-warnings"></a><span data-ttu-id="fe033-168">Gérer les avertissements signalés</span><span class="sxs-lookup"><span data-stu-id="fe033-168">Handle reported warnings</span></span>

<span data-ttu-id="fe033-169">La méthode recommandée pour traiter ces diagnostics consiste à s’assurer que vous appelez uniquement des API spécifiques à la plateforme lors de l’exécution sur une plateforme appropriée.</span><span class="sxs-lookup"><span data-stu-id="fe033-169">The recommended way to deal with these diagnostics is to make sure you only call platform-specific APIs when running on an appropriate platform.</span></span> <span data-ttu-id="fe033-170">Vous trouverez ci-dessous les options que vous pouvez utiliser pour traiter les avertissements. choisissez celui qui convient le mieux à votre situation :</span><span class="sxs-lookup"><span data-stu-id="fe033-170">Following are the options you can use to address the warnings; choose whichever is most appropriate for your situation:</span></span>

- <span data-ttu-id="fe033-171">**Protégez l’appel**.</span><span class="sxs-lookup"><span data-stu-id="fe033-171">**Guard the call**.</span></span> <span data-ttu-id="fe033-172">Vous pouvez y parvenir en appelant de façon conditionnelle le code au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fe033-172">You can achieve this by conditionally calling the code at run time.</span></span> <span data-ttu-id="fe033-173">Vérifiez si vous êtes en cours d’exécution à `Platform` l’aide d’une des méthodes de contrôle de plateforme, par exemple `OperatingSystem.Is<Platform>()` ou `OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` .</span><span class="sxs-lookup"><span data-stu-id="fe033-173">Check whether you're running on a desired `Platform` by using one of platform-check methods, for example, `OperatingSystem.Is<Platform>()` or `OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)`.</span></span>

- <span data-ttu-id="fe033-174">**Marquez le site d’appel comme étant spécifique à la plateforme**.</span><span class="sxs-lookup"><span data-stu-id="fe033-174">**Mark the call site as platform-specific**.</span></span> <span data-ttu-id="fe033-175">Vous pouvez également choisir de marquer vos propres API comme étant spécifiques à la plateforme, ce qui fait simplement de transférer les exigences à vos appelants.</span><span class="sxs-lookup"><span data-stu-id="fe033-175">You can also choose to mark your own APIs as being platform-specific, thus effectively just forwarding the requirements to your callers.</span></span> <span data-ttu-id="fe033-176">Marquez la méthode ou le type conteneur ou l’assembly entier avec les mêmes attributs que l’appel dépendant de la plateforme référencé.</span><span class="sxs-lookup"><span data-stu-id="fe033-176">Mark the containing method or type or the entire assembly with the same attributes as the referenced platform-dependent call.</span></span> <span data-ttu-id="fe033-177">[Exemples](#mark-call-site-as-platform-specific).</span><span class="sxs-lookup"><span data-stu-id="fe033-177">[Examples](#mark-call-site-as-platform-specific).</span></span>

- <span data-ttu-id="fe033-178">**Déclarez le site d’appel avec la vérification de la plateforme**.</span><span class="sxs-lookup"><span data-stu-id="fe033-178">**Assert the call site with platform check**.</span></span> <span data-ttu-id="fe033-179">Si vous ne souhaitez pas la surcharge d’une `if` instruction supplémentaire au moment de l’exécution, utilisez <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fe033-179">If you don't want the overhead of an additional `if` statement at run time, use <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fe033-180">[Exemple](#assert-the-call-site-with-platform-check).</span><span class="sxs-lookup"><span data-stu-id="fe033-180">[Example](#assert-the-call-site-with-platform-check).</span></span>

- <span data-ttu-id="fe033-181">**Supprimez le code**.</span><span class="sxs-lookup"><span data-stu-id="fe033-181">**Delete the code**.</span></span> <span data-ttu-id="fe033-182">Ce n’est généralement pas ce que vous voulez, car cela signifie que vous perdez la fidélité lorsque votre code est utilisé par les utilisateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="fe033-182">Generally not what you want because it means you lose fidelity when your code is used by Windows users.</span></span> <span data-ttu-id="fe033-183">Dans les cas où une alternative multiplateforme existe, il est probablement préférable de l’utiliser sur des API spécifiques à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="fe033-183">For cases where a cross-platform alternative exists, you're likely better off using that over platform-specific APIs.</span></span>

- <span data-ttu-id="fe033-184">**Supprimez l’avertissement**.</span><span class="sxs-lookup"><span data-stu-id="fe033-184">**Suppress the warning**.</span></span> <span data-ttu-id="fe033-185">Vous pouvez également simplement supprimer l’avertissement à l’aide d’une entrée EditorConfig ou `#pragma warning disable ca1416` .</span><span class="sxs-lookup"><span data-stu-id="fe033-185">You can also simply suppress the warning, either via an EditorConfig entry or `#pragma warning disable ca1416`.</span></span> <span data-ttu-id="fe033-186">Toutefois, cette option doit être en dernier recours lors de l’utilisation d’API spécifiques à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="fe033-186">However, this option should be a last resort when using platform-specific APIs.</span></span>

### <a name="guard-platform-specific-apis-with-guard-methods"></a><span data-ttu-id="fe033-187">Protéger les API spécifiques à une plateforme avec des méthodes Guard</span><span class="sxs-lookup"><span data-stu-id="fe033-187">Guard platform-specific APIs with guard methods</span></span>

<span data-ttu-id="fe033-188">Le nom de la plateforme de la méthode Guard doit correspondre au nom de la plateforme d’API dépendante de la plateforme appelante.</span><span class="sxs-lookup"><span data-stu-id="fe033-188">The guard method's platform name should match with the calling platform-dependent API platform name.</span></span> <span data-ttu-id="fe033-189">Si la chaîne de plateforme de l’API appelante comprend la version :</span><span class="sxs-lookup"><span data-stu-id="fe033-189">If the platform string of the calling API includes the version:</span></span>

- <span data-ttu-id="fe033-190">Pour l' `[SupportedOSPlatform("platformVersion")]` attribut, la plateforme de la méthode Guard `version` doit être supérieure ou égale à celle de la plateforme appelante `Version` .</span><span class="sxs-lookup"><span data-stu-id="fe033-190">For the `[SupportedOSPlatform("platformVersion")]` attribute, the guard method platform `version` should be greater than or equal to the calling platform's `Version`.</span></span>
- <span data-ttu-id="fe033-191">Pour l' `[UnsupportedOSPlatform("platformVersion")]` attribut, la plateforme de la méthode Guard `version` doit être inférieure ou égale à celle de la plateforme appelante `Version` .</span><span class="sxs-lookup"><span data-stu-id="fe033-191">For the `[UnsupportedOSPlatform("platformVersion")]` attribute, the guard method's platform `version` should be less than or equal to the calling platform's `Version`.</span></span>

  ```csharp
  public void CallingSupportedOnlyApis() // Allow list calls
  {
      if (OperatingSystem.IsWindows())
      {
          WindowsOnlyApi(); // will not warn
      }

      if (OperatingSystem.IsLinux())
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn, within one of the supported context
      }

      // Can use &&, || logical operators to guard combined attributes
      if (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10.0.19041)))
      {
          ApiSupportedFromWindows8UnsupportFromWindows10();
      }

      if (OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903))
      {
          AssemblySupportedOnWindowsApiSupportedFromWindows10(); // Only need to check latest supported version
      }
  }

  public void CallingUnsupportedApis()
  {
      if (!OperatingSystem.IsAndroid())
      {
          DoesNotWorkOnAndroid(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || OperatingSystem.IsWindowsVersionAtLeast(8))
      {
          StartedWindowsSupportFromVersion8(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || // supported all other platforms
         (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903)))
      {
          StartedWindowsSupportFrom8UnsupportedFrom10(); // will not warn
      }
  }
  ```

- <span data-ttu-id="fe033-192">Si vous devez protéger du code qui cible `netstandard` ou `netcoreapp` où de nouvelles <xref:System.OperatingSystem> API ne sont pas disponibles, l' <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> API peut être utilisée et sera respectée par l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="fe033-192">If you need to guard code that targets `netstandard` or `netcoreapp` where new <xref:System.OperatingSystem> APIs are not available, the <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> API can be used and will be respected by the analyzer.</span></span> <span data-ttu-id="fe033-193">Mais elle n’est pas aussi optimisée que les nouvelles API ajoutées dans <xref:System.OperatingSystem> .</span><span class="sxs-lookup"><span data-stu-id="fe033-193">But it's not as optimized as the new APIs added in <xref:System.OperatingSystem>.</span></span> <span data-ttu-id="fe033-194">Si la plateforme n’est pas prise en charge dans la <xref:System.Runtime.InteropServices.OSPlatform> structure, vous pouvez appeler <xref:System.Runtime.InteropServices.OSPlatform.Create(System.String)?displayProperty=nameWithType> et passer le nom de la plateforme, que l’analyseur respecte également.</span><span class="sxs-lookup"><span data-stu-id="fe033-194">If the platform is not supported in the <xref:System.Runtime.InteropServices.OSPlatform> struct, you can call <xref:System.Runtime.InteropServices.OSPlatform.Create(System.String)?displayProperty=nameWithType> and pass in the platform name, which the analyzer also respects.</span></span>

  ```csharp
  public void CallingSupportedOnlyApis()
  {
      if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn
      }

      if (RuntimeInformation.IsOSPlatform(OSPlatform.Create("browser")))
      {
          ApiOnlySupportedOnBrowser(); // call of browser specific API
      }
  }
  ```

### <a name="mark-call-site-as-platform-specific"></a><span data-ttu-id="fe033-195">Marquer le site d’appel comme spécifique à la plateforme</span><span class="sxs-lookup"><span data-stu-id="fe033-195">Mark call site as platform-specific</span></span>

<span data-ttu-id="fe033-196">Les noms de plateforme doivent correspondre à l’API dépendante de la plateforme appelante.</span><span class="sxs-lookup"><span data-stu-id="fe033-196">Platform names should match the calling platform-dependent API.</span></span> <span data-ttu-id="fe033-197">Si la chaîne de plateforme contient une version :</span><span class="sxs-lookup"><span data-stu-id="fe033-197">If the platform string includes a version:</span></span>

- <span data-ttu-id="fe033-198">Pour l' `[SupportedOSPlatform("platformVersion")]` attribut, la plateforme de site d’appel `version` doit être supérieure ou égale à celle de la plateforme appelante `Version`</span><span class="sxs-lookup"><span data-stu-id="fe033-198">For the `[SupportedOSPlatform("platformVersion")]` attribute, the call site platform `version` should be greater than or equal to the calling platform's `Version`</span></span>
- <span data-ttu-id="fe033-199">Pour l' `[UnsupportedOSPlatform("platformVersion")]` attribut, la plateforme de site d’appel `version` doit être inférieure ou égale à celle de la plateforme appelante `Version`</span><span class="sxs-lookup"><span data-stu-id="fe033-199">For the `[UnsupportedOSPlatform("platformVersion")]` attribute, the call site platform `version` should be less than or equal to the calling platform's `Version`</span></span>

  ```csharp
  // an API supported only on Windows.
  [SupportedOSPlatform("windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  [SupportedOSPlatform("windows8.0")] // call site attributed Windows 8.0 or above.
  public void Caller()
  {
      WindowsOnlyApi(); // will not warn as call site is for Windows.

      // will not warn as call site is for Windows.
      SupportedOnWindowsAndLinuxOnly();

      // will not warn for the API's [SupportedOSPlatform("windows8.0")] attribute.
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // as the call site version is lower than calling version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows11.0")] // call site attributed with windows 11.0 or above.
  public void Caller2()
  {
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // will not warn as call site version higher than calling API.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")] // call site supports Windows from version 8.0 to 10.0.19041.0.
  public void Caller3()
  {
      // will not warn as caller has exact same attributes.
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // As call site stopped support from that version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on Android but supported on all other.
  [UnsupportedOSPlatform("android")]
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  [UnsupportedOSPlatform("windows")] // Caller no support Windows for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'Android'.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }

  [UnsupportedOSPlatform("windows")]
  [UnsupportedOSPlatform("android")] // Caller not support Windows and Android for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // will not warn as call site not supports Android.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

### <a name="assert-the-call-site-with-platform-check"></a><span data-ttu-id="fe033-200">Déclarer le site d’appel avec la vérification de la plateforme</span><span class="sxs-lookup"><span data-stu-id="fe033-200">Assert the call-site with platform check</span></span>

<span data-ttu-id="fe033-201">Toutes les vérifications conditionnelles utilisées dans les exemples de la [plateforme Guard](#guard-platform-specific-apis-with-guard-methods) peuvent également être utilisées comme condition pour <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fe033-201">All the conditional checks used in the [platform guard examples](#guard-platform-specific-apis-with-guard-methods) can also be used as the condition for <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>.</span></span>

  ```csharp
  // An API supported only on Linux.
  [SupportedOSPlatform("linux")]
  public void LinuxOnlyApi() { }

  public void Caller()
  {
      Debug.Assert(OperatingSystem.IsLinux());

      LinuxOnlyApi(); // will not warn
  }
  ```

## <a name="see-also"></a><span data-ttu-id="fe033-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe033-202">See also</span></span>

- [<span data-ttu-id="fe033-203">Noms des frameworks cibles dans .NET 5</span><span class="sxs-lookup"><span data-stu-id="fe033-203">Target Framework Names in .NET 5</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md)
- [<span data-ttu-id="fe033-204">Annotation d’API spécifiques à la plateforme et détection de son utilisation</span><span class="sxs-lookup"><span data-stu-id="fe033-204">Annotating platform-specific APIs and detecting its use</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-checks/platform-checks.md)
- [<span data-ttu-id="fe033-205">Annotation des API comme non prises en charge sur des plateformes spécifiques</span><span class="sxs-lookup"><span data-stu-id="fe033-205">Annotating APIs as unsupported on specific platforms</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-exclusion/platform-exclusion.md)
- [<span data-ttu-id="fe033-206">Analyseur de compatibilité de plateforme CA1416</span><span class="sxs-lookup"><span data-stu-id="fe033-206">CA1416 Platform compatibility analyzer</span></span>](/visualstudio/code-quality/ca1416)
- [<span data-ttu-id="fe033-207">Analyseur d’API .NET</span><span class="sxs-lookup"><span data-stu-id="fe033-207">.NET API analyzer</span></span>](../../standard/analyzers/api-analyzer.md)
