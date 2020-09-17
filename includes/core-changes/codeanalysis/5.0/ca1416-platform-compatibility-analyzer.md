---
ms.openlocfilehash: cd7860a5dfff1eb595625665382689733cffc94a
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90721240"
---
### <a name="ca1416-platform-compatibility"></a><span data-ttu-id="e5f4d-101">CA1416 : compatibilité de la plateforme</span><span class="sxs-lookup"><span data-stu-id="e5f4d-101">CA1416: Platform compatibility</span></span>

<span data-ttu-id="e5f4d-102">La règle de l’analyseur de code .NET [CA1416](/visualstudio/code-quality/ca1416) est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-102">.NET code analyzer rule [CA1416](/visualstudio/code-quality/ca1416) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="e5f4d-103">Il génère un avertissement de génération pour les appels aux API spécifiques à la plateforme à partir des sites d’appel qui ne vérifient pas le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-103">It produces a build warning for calls to platform-specific APIs from call sites that don't verify the operating system.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e5f4d-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e5f4d-104">Change description</span></span>

<span data-ttu-id="e5f4d-105">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="e5f4d-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="e5f4d-106">Plusieurs de ces règles sont activées, par défaut, y compris [CA1416](/visualstudio/code-quality/ca1416).</span><span class="sxs-lookup"><span data-stu-id="e5f4d-106">Several of these rules are enabled, by default, including [CA1416](/visualstudio/code-quality/ca1416).</span></span> <span data-ttu-id="e5f4d-107">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span> <span data-ttu-id="e5f4d-108">La règle CA1416 vous informe lorsque vous utilisez des API spécifiques à la plateforme à partir de emplacements où le contexte de plateforme n’est pas vérifié.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-108">Rule CA1416 informs you when you're using platform-specific APIs from places where the platform context isn't verified.</span></span>

<span data-ttu-id="e5f4d-109">La règle [CA1416](/visualstudio/code-quality/ca1416), l’analyseur de compatibilité de la plateforme, fonctionne à la main avec d’autres fonctionnalités nouvelles dans .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-109">Rule [CA1416](/visualstudio/code-quality/ca1416), the platform compatibility analyzer, works hand-in-hand with some other features that are new in .NET 5.0.</span></span> <span data-ttu-id="e5f4d-110">.NET 5,0 introduit les <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> et <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> , qui vous permettent de spécifier les plateformes sur lesquelles une API *est* ou *n’est pas* prise en charge.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-110">.NET 5.0 introduces the <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>, which let you specify the platforms that an API *is* or *isn't* supported on.</span></span> <span data-ttu-id="e5f4d-111">En l’absence de ces attributs, une API est supposée être prise en charge sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-111">In the absence of these attributes, an API is assumed to be supported on all platforms.</span></span> <span data-ttu-id="e5f4d-112">Ces attributs ont été appliqués aux API spécifiques à la plateforme dans les bibliothèques .NET de base.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-112">These attributes have been applied to platform-specific APIs in the core .NET libraries.</span></span>

<span data-ttu-id="e5f4d-113">Dans les projets qui ciblent des plateformes pour lesquelles les API qu’ils utilisent ne sont pas disponibles, la règle [CA1416](/visualstudio/code-quality/ca1416) signale tous les appels d’API spécifiques à la plateforme où le contexte de plateforme n’est pas vérifié.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-113">In projects that target platforms for which APIs that they use aren't available, rule [CA1416](/visualstudio/code-quality/ca1416) flags any platform-specific API call where the platform context isn't verified.</span></span> <span data-ttu-id="e5f4d-114">La plupart des API qui sont maintenant décorées avec les <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> attributs et lèvent des <xref:System.PlatformNotSupportedException> exceptions lorsqu’elles sont appelées sur un système d’exploitation non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-114">Most of the APIs that are now decorated with the <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> attributes throw <xref:System.PlatformNotSupportedException> exceptions when they're invoked on an unsupported operating system.</span></span> <span data-ttu-id="e5f4d-115">Maintenant que ces API sont marquées comme spécifiques à la plateforme, la règle [CA1416](/visualstudio/code-quality/ca1416) vous aide à éviter les exceptions d’exécution <xref:System.PlatformNotSupportedException> en ajoutant des vérifications du système d’exploitation à vos sites d’appel.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-115">Now that these APIs are marked as platform-specific, rule [CA1416](/visualstudio/code-quality/ca1416) helps you prevent run-time <xref:System.PlatformNotSupportedException> exceptions by adding OS checks to your call sites.</span></span>

#### <a name="examples"></a><span data-ttu-id="e5f4d-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="e5f4d-116">Examples</span></span>

- <span data-ttu-id="e5f4d-117">La <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> méthode est uniquement prise en charge sur Windows (elle est décorée avec `[SupportedOSPlatform("windows")]` ).</span><span class="sxs-lookup"><span data-stu-id="e5f4d-117">The <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> method is only supported on Windows (it's decorated with `[SupportedOSPlatform("windows")]`).</span></span> <span data-ttu-id="e5f4d-118">Le code suivant produira un avertissement CA1416 au moment de la génération si le projet [cible](../../../../docs/standard/frameworks.md) `net5.0` (mais pas `net5.0-windows` ).</span><span class="sxs-lookup"><span data-stu-id="e5f4d-118">The following code will produce a CA1416 warning at build time if the project [targets](../../../../docs/standard/frameworks.md) `net5.0` (but not `net5.0-windows`).</span></span> <span data-ttu-id="e5f4d-119">Pour les actions que vous pouvez entreprendre pour éviter l’avertissement, consultez [action recommandée](#recommended-action).</span><span class="sxs-lookup"><span data-stu-id="e5f4d-119">For actions you can take to avoid the warning, see [Recommended action](#recommended-action).</span></span>

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <span data-ttu-id="e5f4d-120">La <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> méthode n’est pas prise en charge dans le navigateur (elle est décorée avec `[UnsupportedOSPlatform("browser")]` ).</span><span class="sxs-lookup"><span data-stu-id="e5f4d-120">The <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> method is not supported in the browser (it's decorated with `[UnsupportedOSPlatform("browser")]`).</span></span> <span data-ttu-id="e5f4d-121">Le code suivant produira un avertissement CA1416 au moment de la génération si le projet utilise le kit de développement logiciel (SDK) de l’assembly éblouissant ( `<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">` ) ou s’il comprend `browser` une plateforme prise en charge ( `<SupportedPlatform Include="browser" />` ) dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-121">The following code will produce a CA1416 warning at build time if the project uses the Blazor WebAssembly SDK (`<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">`) or includes `browser` as a supported platform (`<SupportedPlatform Include="browser" />`) in the project file.</span></span>

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

#### <a name="version-introduced"></a><span data-ttu-id="e5f4d-122">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e5f4d-122">Version introduced</span></span>

<span data-ttu-id="e5f4d-123">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="e5f4d-123">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e5f4d-124">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e5f4d-124">Recommended action</span></span>

<span data-ttu-id="e5f4d-125">Assurez-vous que les API spécifiques à la plateforme sont appelées uniquement lorsque le code s’exécute sur une plateforme appropriée.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-125">Ensure that platform-specific APIs are only called when the code is running on an appropriate platform.</span></span> <span data-ttu-id="e5f4d-126">Vous pouvez vérifier le système d’exploitation actuel à l’aide de l’une des `Is<Platform>` méthodes de la <xref:System.OperatingSystem?displayProperty=nameWithType> classe, par exemple, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> , avant d’appeler une API spécifique à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-126">You can check the current operating system using one of the `Is<Platform>` methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class, for example, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType>, before calling a platform-specific API.</span></span>

<span data-ttu-id="e5f4d-127">Vous pouvez utiliser l’une des `Is<Platform>` méthodes dans la condition d’une `if` instruction :</span><span class="sxs-lookup"><span data-stu-id="e5f4d-127">You can use one of the `Is<Platform>` methods in the condition of an `if` statement:</span></span>

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

<span data-ttu-id="e5f4d-128">Ou, si vous ne souhaitez pas la surcharge d’une `if` instruction supplémentaire au moment de l’exécution, appelez à la <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> place :</span><span class="sxs-lookup"><span data-stu-id="e5f4d-128">Or, if you don't want the overhead of an additional `if` statement at run time, call <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> instead:</span></span>

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="e5f4d-129">Vous pouvez également marquer votre API comme étant spécifique à la plateforme, auquel cas la charge de vérification des exigences incombe à vos appelants.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-129">You can also mark your API as platform-specific, in which case the burden of checking requirements falls on your callers.</span></span> <span data-ttu-id="e5f4d-130">Vous pouvez marquer des méthodes ou des types spécifiques ou un assembly entier.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-130">You can mark specific methods or types or an entire assembly.</span></span>

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="e5f4d-131">Si vous ne souhaitez pas corriger tous vos sites d’appel, vous pouvez choisir l’une des options suivantes pour supprimer l’avertissement :</span><span class="sxs-lookup"><span data-stu-id="e5f4d-131">If you don't want to fix all your call sites, you can choose one of the following options to suppress the warning:</span></span>

- <span data-ttu-id="e5f4d-132">Pour supprimer CA1416 de règle, vous pouvez utiliser `#pragma` ou l’indicateur [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) du compilateur, ou en [définissant la gravité de la règle](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) sur `none` dans un fichier. editorconfig.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-132">To suppress rule CA1416, you can do so using `#pragma` or the [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) compiler flag, or by [setting the rule's severity](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) to `none` in an .editorconfig file.</span></span>

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- <span data-ttu-id="e5f4d-133">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="e5f4d-133">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="e5f4d-134">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="e5f4d-134">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="e5f4d-135">Category</span><span class="sxs-lookup"><span data-stu-id="e5f4d-135">Category</span></span>

- <span data-ttu-id="e5f4d-136">Analyse du code</span><span class="sxs-lookup"><span data-stu-id="e5f4d-136">Code analysis</span></span>
- <span data-ttu-id="e5f4d-137">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5f4d-137">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e5f4d-138">API affectées</span><span class="sxs-lookup"><span data-stu-id="e5f4d-138">Affected APIs</span></span>

<span data-ttu-id="e5f4d-139">Pour la plateforme Windows :</span><span class="sxs-lookup"><span data-stu-id="e5f4d-139">For Windows platform:</span></span>

- <span data-ttu-id="e5f4d-140">Toutes les API figurant dans <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> .</span><span class="sxs-lookup"><span data-stu-id="e5f4d-140">All APIs listed at <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md>.</span></span>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

<span data-ttu-id="e5f4d-141">Pour la plateforme de l’assembly éblouissant :</span><span class="sxs-lookup"><span data-stu-id="e5f4d-141">For Blazor WebAssembly platform:</span></span>

- <span data-ttu-id="e5f4d-142">Toutes les API figurant dans <https://github.com/dotnet/runtime/issues/41087> .</span><span class="sxs-lookup"><span data-stu-id="e5f4d-142">All APIs listed at <https://github.com/dotnet/runtime/issues/41087>.</span></span>

<!--

#### Affected APIs

- ``

-->

#### <a name="see-also"></a><span data-ttu-id="e5f4d-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5f4d-143">See also</span></span>

- [<span data-ttu-id="e5f4d-144">CA1416 : Valider la compatibilité de la plateforme</span><span class="sxs-lookup"><span data-stu-id="e5f4d-144">CA1416: Validate platform compatibility</span></span>](/visualstudio/code-quality/ca1416)
- [<span data-ttu-id="e5f4d-145">Analyseur d’API .NET</span><span class="sxs-lookup"><span data-stu-id="e5f4d-145">.NET API analyzer</span></span>](../../../../docs/standard/analyzers/api-analyzer.md)
