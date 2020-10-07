---
title: Analyseur de compatibilité de plateforme
description: Analyseur Roslyn qui peut aider à détecter les problèmes de compatibilité de plateforme dans les applications et les bibliothèques multiplateforme.
author: buyaa-n
ms.date: 09/17/2020
ms.openlocfilehash: 44c2c2d9674b13f314a057f847df2d4d474cc2be
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805296"
---
# <a name="platform-compatibility-analyzer"></a>Analyseur de compatibilité de plateforme

Vous avez probablement entendu parler de « One .NET » : une plateforme unique et unifiée pour la création de n’importe quel type d’application. Le kit de développement logiciel (SDK) .NET 5,0 comprend ASP.NET Core, Entity Framework Core, WinForms, WPF, Xamarin et ML.NET, et ajoute la prise en charge d’autres plateformes au fil du temps. .NET 5,0 s’efforce de fournir une expérience dans laquelle vous n’avez pas à vous soucier des différentes versions de .NET, mais ne tente pas d’effectuer une abstraction totale du système d’exploitation sous-jacent. Vous continuerez à être en mesure d’appeler des API spécifiques à la plateforme, par exemple, P/Invoke, WinRT ou les liaisons Xamarin pour iOS et Android.

Toutefois, l’utilisation d’API spécifiques à une plateforme sur un composant signifie que le code ne fonctionne plus sur toutes les plateformes. Nous avions besoin d’une méthode pour la détecter au moment de la conception afin que les développeurs reçoivent des diagnostics lorsqu’ils utilisent par inadvertance des API spécifiques à la plateforme. Pour atteindre cet objectif, .NET 5,0 introduit l' [Analyseur de compatibilité de plateforme](/visualstudio/code-quality/ca1416) et les API complémentaires pour aider les développeurs à identifier et utiliser les API spécifiques à la plateforme, le cas échéant.
Les nouvelles API sont les suivantes :

- <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> pour annoter des API comme étant spécifiques <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> à une plateforme et pour annoter des API non prises en charge sur un système d’exploitation particulier. Ces attributs peuvent éventuellement inclure le numéro de version et ont déjà été appliqués à certaines API spécifiques à la plateforme dans les bibliothèques .NET de base.
- `Is<Platform>()` et `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` les méthodes statiques de la <xref:System.OperatingSystem?displayProperty=nameWithType> classe pour appeler sans risque des API spécifiques à la plateforme. Par exemple, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> peut être utilisé pour protéger un appel à une API spécifique à Windows, et <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> () peut être utilisé pour protéger un appel d’API spécifique à la version de Windows. Consultez ces [exemples](#guard-platform-specific-apis-with-guard-methods) illustrant comment ces méthodes peuvent être utilisées comme protecteurs de références d’API spécifiques à la plateforme.

> [!TIP]
> L’analyseur de compatibilité de la plateforme met à niveau et remplace la fonctionnalité de [détection des problèmes inter-plateformes](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues) de l' [analyseur d’API .net](../../standard/analyzers/api-analyzer.md).

## <a name="prerequisites"></a>Prérequis

L’analyseur de compatibilité de la plateforme est l’un des analyseurs de la qualité du code Roslyn. À compter de .NET 5,0, ces analyseurs sont [inclus dans le kit de développement logiciel (SDK) .net](../../fundamentals/code-analysis/overview.md). L’analyseur de compatibilité de plateforme est activé par défaut uniquement pour les projets qui ciblent `net5.0` ou une version ultérieure. Toutefois, vous pouvez l' [activer](/visualstudio/code-quality/ca1416.md#configurability) pour les projets qui ciblent d’autres infrastructures.

## <a name="how-the-analyzer-determines-platform-dependency"></a>Comment l’analyseur détermine la dépendance de la plateforme

- Une **API non attributée** est considérée pour fonctionner sur **toutes les plateformes de système d’exploitation**.
- Une API marquée avec `[SupportedOSPlatform("platform")]` est considérée comme portable uniquement pour le système d’exploitation spécifié `platform` .
  - L’attribut peut être appliqué plusieurs fois pour indiquer la **prise en charge de plusieurs plateformes** ( `[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]` ).
  - L’analyseur produira un **Avertissement** si les API spécifiques à la plateforme sont référencées sans un **contexte de plateforme**approprié :
    - **Avertit** si le projet ne cible pas la plateforme prise en charge (par exemple, un appel d’API spécifique à Windows et les cibles de projet `<TargetFramework>net5.0-ios14.0</TargetFramework>` ).
    - **Avertit** si le projet est multi-ciblé ( `<TargetFramework>net5.0</TargetFramework>` ).
    - **N’avertit pas** si l’API spécifique à la plateforme est référencée dans un projet qui cible l’une des **plateformes spécifiées** (par exemple, pour un appel d’API spécifique à Windows et les cibles de projet `<TargetFramework>net5.0-windows</TargetFramework>` ).
    - **N’avertit pas** si l’appel d’API spécifique à la plateforme est protégé par les méthodes de vérification de plateforme correspondantes (par exemple, `if(OperatingSystem.IsWindows())` ).
    - **N’avertit pas** si l’API spécifique à la plateforme est référencée à partir du même contexte spécifique à la plateforme (le**site d’appel est également attribué** avec `[SupportedOSPlatform("platform")` ).
- Une API marquée avec `[UnsupportedOSPlatform("platform")]` est considérée comme non prise en charge uniquement sur le système d’exploitation spécifié `platform` , mais prise en charge pour toutes les autres plateformes.
  - L’attribut peut être appliqué plusieurs fois avec différentes plateformes, par exemple, `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]` .
  - L’analyseur génère un **Avertissement** uniquement si le `platform` est efficace pour le site d’appel :
    - **Avertit** si le projet cible la plateforme dont l’attribut n’est pas pris en charge (par exemple, si l’API est attribuée avec `[UnsupportedOSPlatform("windows")]` et les cibles de site d’appel `<TargetFramework>net5.0-windows</TargetFramework>` ).
    - **Avertit** si le projet est multi-ciblé et `platform` s’il est inclus dans le groupe d’éléments [MSBuild `<SupportedPlatform>` ](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) par défaut, ou `platform` s’il est inclus manuellement dans le `MSBuild` \<SupportedPlatform> groupe d’éléments :

      ```XML
      <ItemGroup>
          <SupportedPlatform Include="platform" />
      </ItemGroup>
      ```

    - **Ne vous avertit** pas si vous créez une application qui ne cible pas la plateforme non prise en charge ou qui est multi-ciblée et que la plateforme n’est pas incluse dans le groupe d’éléments [ `<SupportedPlatform>` MSBuild](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) par défaut.
- Les deux attributs peuvent être instanciés avec ou sans numéros de version dans le cadre du nom de la plateforme.
  - Les numéros de version sont au format `major.minor[.build[.revision]]` ; `major.minor` est requis et les `build` `revision` composants et sont facultatifs. Par exemple, « Windows 7.0 » indique la version de Windows 7,0, mais « Windows » est interprété comme étant Windows 0,0.

Pour plus d’informations, consultez [des exemples de fonctionnement des attributs et des diagnostics qu’ils entraînent](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce).

### <a name="advanced-scenarios-for-combining-attributes"></a>Scénarios avancés pour la combinaison d’attributs

- Si une combinaison d' `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` attributs et est présente, tous les attributs sont regroupés par identificateur de plateforme de système d’exploitation :
  - **Liste uniquement prise en charge**. Si la version la plus basse de chaque plateforme de système d’exploitation est un `[SupportedOSPlatform]` attribut, l’API est considérée comme uniquement prise en charge par les plateformes listées et non prise en charge par toutes les autres plateformes. Les attributs facultatifs `[UnsupportedOSPlatform]` pour chaque plateforme peuvent uniquement avoir une version plus récente de la version minimale prise en charge, ce qui indique que l’API est supprimée à partir de la version spécifiée.

    ```csharp
    // The API only supported on Windows 8.0 and later, not supported for all other.
    // The API is removed/unsupported from version 10.0.19041.0.
    [SupportedOSPlatform("windows8.0")]
    [UnsupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows80SupportFromCertainVersion();
    ```

  - **Liste uniquement non prise en charge**. Si la version la plus basse pour chaque plateforme de système d’exploitation est un `[UnsupportedOSPlatform]` attribut, l’API est considérée uniquement comme non prise en charge par les plateformes listées et prise en charge par toutes les autres plateformes. La liste peut avoir `[SupportedOSPlatform]` un attribut avec la même plateforme, mais une version plus récente, ce qui indique que l’API est prise en charge à partir de cette version.

    ```csharp
    // The API was unsupported on Windows until version 10.0.19041.0.
    // The API is considered supported everywhere else without constraints.
    [UnsupportedOSPlatform("windows")]
    [SupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows8UnsupportFromWindows10();
    ```

  - **Liste incohérente**. Si la version la plus basse pour certaines plateformes est `[SupportedOSPlatform]` alors qu’elle est `[UnsupportedOSPlatform]` destinée à d’autres plateformes, elle est considérée comme étant incohérente, ce qui n’est pas pris en charge pour l’analyseur.
  - Si les versions les plus basses des `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` attributs et sont égales, l’analyseur considère la plateforme comme faisant partie de la **liste uniquement prise en charge**.
- Les attributs de plateforme peuvent être appliqués à des types, des membres (méthodes, champs, propriétés et événements) et à des assemblys avec des noms ou des versions de plateforme différents.
  - Les attributs appliqués au niveau supérieur `target` affectent tous ses membres et types.
  - Les attributs de niveau enfant s’appliquent uniquement s’ils adhèrent à la règle. les annotations enfants peuvent limiter la prise en charge des plateformes, mais elles ne peuvent pas les élargir.
    - Si le parent n’a que la liste des attributs **pris en charge** , les attributs des membres enfants ne peuvent pas ajouter de nouvelle prise en charge de plateforme, car cela permettrait d’étendre la prise en charge du parent La prise en charge d’une nouvelle plateforme peut uniquement être ajoutée au parent lui-même. Toutefois, l’enfant peut avoir l' `Supported` attribut pour la même plate-forme avec les versions ultérieures, ce qui réduit la prise en charge. En outre, l’enfant peut avoir l' `Unsupported` attribut avec la même plateforme que celle qui restreint également la prise en charge du parent.
    - Lorsque le parent n’a qu’une liste **non prise en charge** , les attributs des membres enfants peuvent ajouter la prise en charge d’une nouvelle plateforme, car cela réduit la prise en charge du parent. Mais il ne peut pas avoir l' `Supported` attribut pour la même plateforme que le parent, car cela étend la prise en charge du parent. La prise en charge de la même plate-forme peut être ajoutée uniquement au parent où l’attribut d’origine `Unsupported` a été appliqué.
  - Si `[SupportedOSPlatform("platformVersion")]` est appliqué plus d’une fois pour une API portant le même `platform` nom, l’analyseur considère uniquement celui avec la version minimale.
  - Si `[UnsupportedOSPlatform("platformVersion")]` est appliqué plus de deux fois pour une API portant le même `platform` nom, l’analyseur considère uniquement les deux avec les versions les plus anciennes.

  > [!NOTE]
  > Une API qui était prise en charge initialement mais non prise en charge (supprimée) dans une version ultérieure n’est pas censée être reprise dans une version ultérieure.

### <a name="examples-of-how-the-attributes-work-and-what-diagnostics-they-produce"></a>Exemples illustrant le fonctionnement des attributs et les diagnostics qu’ils produisent

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

## <a name="handle-reported-warnings"></a>Gérer les avertissements signalés

La méthode recommandée pour traiter ces diagnostics consiste à s’assurer que vous appelez uniquement des API spécifiques à la plateforme lors de l’exécution sur une plateforme appropriée. Vous trouverez ci-dessous les options que vous pouvez utiliser pour traiter les avertissements. choisissez celui qui convient le mieux à votre situation :

- **Protégez l’appel**. Vous pouvez y parvenir en appelant de façon conditionnelle le code au moment de l’exécution. Vérifiez si vous êtes en cours d’exécution à `Platform` l’aide d’une des méthodes de contrôle de plateforme, par exemple `OperatingSystem.Is<Platform>()` ou `OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` .

- **Marquez le site d’appel comme étant spécifique à la plateforme**. Vous pouvez également choisir de marquer vos propres API comme étant spécifiques à la plateforme, ce qui fait simplement de transférer les exigences à vos appelants. Marquez la méthode ou le type conteneur ou l’assembly entier avec les mêmes attributs que l’appel dépendant de la plateforme référencé. [Exemples](#mark-call-site-as-platform-specific).

- **Déclarez le site d’appel avec la vérification de la plateforme**. Si vous ne souhaitez pas la surcharge d’une `if` instruction supplémentaire au moment de l’exécution, utilisez <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> . [Exemple](#assert-the-call-site-with-platform-check).

- **Supprimez le code**. Ce n’est généralement pas ce que vous voulez, car cela signifie que vous perdez la fidélité lorsque votre code est utilisé par les utilisateurs Windows. Dans les cas où une alternative multiplateforme existe, il est probablement préférable de l’utiliser sur des API spécifiques à la plateforme.

- **Supprimez l’avertissement**. Vous pouvez également simplement supprimer l’avertissement à l’aide d’une entrée EditorConfig ou `#pragma warning disable ca1416` . Toutefois, cette option doit être en dernier recours lors de l’utilisation d’API spécifiques à la plateforme.

### <a name="guard-platform-specific-apis-with-guard-methods"></a>Protéger les API spécifiques à une plateforme avec des méthodes Guard

Le nom de la plateforme de la méthode Guard doit correspondre au nom de la plateforme d’API dépendante de la plateforme appelante. Si la chaîne de plateforme de l’API appelante comprend la version :

- Pour l' `[SupportedOSPlatform("platformVersion")]` attribut, la plateforme de la méthode Guard `version` doit être supérieure ou égale à celle de la plateforme appelante `Version` .
- Pour l' `[UnsupportedOSPlatform("platformVersion")]` attribut, la plateforme de la méthode Guard `version` doit être inférieure ou égale à celle de la plateforme appelante `Version` .

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

- Si vous devez protéger du code qui cible `netstandard` ou `netcoreapp` où de nouvelles <xref:System.OperatingSystem> API ne sont pas disponibles, l' <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> API peut être utilisée et sera respectée par l’analyseur. Mais elle n’est pas aussi optimisée que les nouvelles API ajoutées dans <xref:System.OperatingSystem> . Si la plateforme n’est pas prise en charge dans la <xref:System.Runtime.InteropServices.OSPlatform> structure, vous pouvez appeler <xref:System.Runtime.InteropServices.OSPlatform.Create(System.String)?displayProperty=nameWithType> et passer le nom de la plateforme, que l’analyseur respecte également.

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

### <a name="mark-call-site-as-platform-specific"></a>Marquer le site d’appel comme spécifique à la plateforme

Les noms de plateforme doivent correspondre à l’API dépendante de la plateforme appelante. Si la chaîne de plateforme contient une version :

- Pour l' `[SupportedOSPlatform("platformVersion")]` attribut, la plateforme de site d’appel `version` doit être supérieure ou égale à celle de la plateforme appelante `Version`
- Pour l' `[UnsupportedOSPlatform("platformVersion")]` attribut, la plateforme de site d’appel `version` doit être inférieure ou égale à celle de la plateforme appelante `Version`

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

### <a name="assert-the-call-site-with-platform-check"></a>Déclarer le site d’appel avec la vérification de la plateforme

Toutes les vérifications conditionnelles utilisées dans les exemples de la [plateforme Guard](#guard-platform-specific-apis-with-guard-methods) peuvent également être utilisées comme condition pour <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> .

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

## <a name="see-also"></a>Voir aussi

- [Noms des frameworks cibles dans .NET 5](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md)
- [Annotation d’API spécifiques à la plateforme et détection de son utilisation](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-checks/platform-checks.md)
- [Annotation des API comme non prises en charge sur des plateformes spécifiques](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-exclusion/platform-exclusion.md)
- [Analyseur de compatibilité de plateforme CA1416](../../fundamentals/code-analysis/quality-rules/ca1416.md)
- [Analyseur d’API .NET](../../standard/analyzers/api-analyzer.md)
