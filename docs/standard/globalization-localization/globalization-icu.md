---
title: Globalisation et ICU
ms.date: 05/21/2020
helpviewer_keywords:
- globalization [.NET], about globalization
- global applications, globalization
- international applications [.NET], globalization
- world-ready applications, globalization
- application development [.NET], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: d0361ba41b3a10d6a316341fcdacb869e7a35d26
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827111"
---
# <a name="net-globalization-and-icu"></a><span data-ttu-id="af693-102">Globalisation et ICU .NET</span><span class="sxs-lookup"><span data-stu-id="af693-102">.NET globalization and ICU</span></span>

<span data-ttu-id="af693-103">Dans le passé, les API de globalisation .NET utilisaient des bibliothèques sous-jacentes différentes sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="af693-103">In the past, the .NET globalization APIs used different underlying libraries on different platforms.</span></span> <span data-ttu-id="af693-104">Sur UNIX, les API utilisaient les [composants internationaux pour Unicode (ICU)](http://site.icu-project.org/home)et sur Windows, ils utilisaient le [service NLS (National Language Support)](/windows/win32/intl/national-language-support).</span><span class="sxs-lookup"><span data-stu-id="af693-104">On Unix, the APIs used [International Components for Unicode (ICU)](http://site.icu-project.org/home), and on Windows, they used [National Language Support (NLS)](/windows/win32/intl/national-language-support).</span></span> <span data-ttu-id="af693-105">Cela a entraîné certaines différences de comportement dans une poignée d’API de globalisation lors de l’exécution d’applications sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="af693-105">This resulted in some behavioral differences in a handful of globalization APIs when running applications on different platforms.</span></span> <span data-ttu-id="af693-106">Les différences de comportement étaient évidentes dans les domaines suivants :</span><span class="sxs-lookup"><span data-stu-id="af693-106">Behavior differences were evident in these areas:</span></span>

- <span data-ttu-id="af693-107">Cultures et données de culture</span><span class="sxs-lookup"><span data-stu-id="af693-107">Cultures and culture data</span></span>
- <span data-ttu-id="af693-108">Casse des chaînes</span><span class="sxs-lookup"><span data-stu-id="af693-108">String casing</span></span>
- <span data-ttu-id="af693-109">Tri et recherche de chaînes</span><span class="sxs-lookup"><span data-stu-id="af693-109">String sorting and searching</span></span>
- <span data-ttu-id="af693-110">Trier les clés</span><span class="sxs-lookup"><span data-stu-id="af693-110">Sort keys</span></span>
- <span data-ttu-id="af693-111">Normalisation des chaînes</span><span class="sxs-lookup"><span data-stu-id="af693-111">String normalization</span></span>
- <span data-ttu-id="af693-112">Prise en charge des IDN (Internationalized Domain Names)</span><span class="sxs-lookup"><span data-stu-id="af693-112">Internationalized Domain Names (IDN) support</span></span>
- <span data-ttu-id="af693-113">Nom d’affichage du fuseau horaire sur Linux</span><span class="sxs-lookup"><span data-stu-id="af693-113">Time zone display name on Linux</span></span>

<span data-ttu-id="af693-114">À compter de .NET 5,0, les développeurs ont plus de contrôle sur la bibliothèque sous-jacente utilisée, ce qui permet aux applications d’éviter les différences entre les plateformes.</span><span class="sxs-lookup"><span data-stu-id="af693-114">Starting with .NET 5.0, developers have more control over which underlying library is used, enabling applications to avoid differences across platforms.</span></span>

## <a name="icu-on-windows"></a><span data-ttu-id="af693-115">ICU sur Windows</span><span class="sxs-lookup"><span data-stu-id="af693-115">ICU on Windows</span></span>

<span data-ttu-id="af693-116">La mise à jour de Windows 10 mai 2019 et les versions ultérieures incluent [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) dans le cadre du système d’exploitation, et .net 5,0 et versions ultérieures utilisent ICU par défaut.</span><span class="sxs-lookup"><span data-stu-id="af693-116">Windows 10 May 2019 Update and later versions include [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) as part of the OS, and .NET 5.0 and later versions use ICU by default.</span></span> <span data-ttu-id="af693-117">Lors de l’exécution sous Windows, .NET 5,0 et versions ultérieures essaient de charger `icu.dll` et, s’il est disponible, l’utilisent pour l’implémentation de la globalisation.</span><span class="sxs-lookup"><span data-stu-id="af693-117">When running on Windows, .NET 5.0 and later versions try to load `icu.dll` and, if it's available, use it for the globalization implementation.</span></span> <span data-ttu-id="af693-118">Si la bibliothèque ICU est introuvable ou ne peut pas être chargée, par exemple lors de l’exécution sur des versions antérieures de Windows, .NET 5,0 et versions ultérieures reviennent à l’implémentation basée sur NLS.</span><span class="sxs-lookup"><span data-stu-id="af693-118">If the ICU library can't be found or loaded, such as when running on older versions of Windows, .NET 5.0 and later versions fall back to the NLS-based implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="af693-119">Même quand vous utilisez ICU, `CurrentCulture` les `CurrentUICulture` membres, et `CurrentRegion` continuent d’utiliser les API du système d’exploitation Windows pour honorer les paramètres utilisateur.</span><span class="sxs-lookup"><span data-stu-id="af693-119">Even when using ICU, the `CurrentCulture`, `CurrentUICulture`, and `CurrentRegion` members still use Windows operating system APIs to honor user settings.</span></span>

### <a name="behavioral-differences"></a><span data-ttu-id="af693-120">Différences de comportement</span><span class="sxs-lookup"><span data-stu-id="af693-120">Behavioral differences</span></span>

<span data-ttu-id="af693-121">Si vous mettez à niveau votre application pour cibler .NET 5, vous pouvez voir les modifications apportées à votre application, même si vous ne vous rendez pas compte que vous utilisez des fonctionnalités de globalisation.</span><span class="sxs-lookup"><span data-stu-id="af693-121">If you upgrade your app to target .NET 5, you might see changes in your app even if you don't realize you're using globalization facilities.</span></span> <span data-ttu-id="af693-122">Cette section répertorie l’une des modifications comportementales que vous pouvez voir, mais il en existe d’autres.</span><span class="sxs-lookup"><span data-stu-id="af693-122">This section lists one of the behavioral changes you might see, but there are others too.</span></span>

##### <a name="stringindexof"></a><span data-ttu-id="af693-123">String.IndexOf</span><span class="sxs-lookup"><span data-stu-id="af693-123">String.IndexOf</span></span>

<span data-ttu-id="af693-124">Prenons le code suivant qui appelle <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> pour Rechercher l’index du caractère de saut de ligne dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="af693-124">Consider the following code that calls <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> to find the index of the newline character in a string.</span></span>

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- <span data-ttu-id="af693-125">Dans les versions précédentes de .NET sur Windows, l’extrait de code s’imprime `6` .</span><span class="sxs-lookup"><span data-stu-id="af693-125">In previous versions of .NET on Windows, the snippet prints `6`.</span></span>
- <span data-ttu-id="af693-126">Dans .NET 5,0 et versions ultérieures sur Windows 10 mai 2019 Update et versions ultérieures, l’extrait de code s’imprime `-1` .</span><span class="sxs-lookup"><span data-stu-id="af693-126">In .NET 5.0 and later versions on Windows 10 May 2019 Update and later versions, the snippet prints `-1`.</span></span>

<span data-ttu-id="af693-127">Pour corriger ce code en effectuant une recherche ordinale au lieu d’une recherche dépendante de la culture, appelez la <xref:System.String.IndexOf(System.String,System.StringComparison)> surcharge et transmettez-la <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="af693-127">To fix this code by conducting an ordinal search instead of a culture-sensitive search, call the <xref:System.String.IndexOf(System.String,System.StringComparison)> overload and pass in <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> as an argument.</span></span>

<span data-ttu-id="af693-128">Vous pouvez exécuter les règles [d’analyse du code CA1307 : spécifiez StringComparison pour plus de clarté](../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md) et [Ca1309 : utiliser StringComparison](../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md) avec la valeur ordinale pour rechercher ces sites d’appel dans votre code.</span><span class="sxs-lookup"><span data-stu-id="af693-128">You can run code analysis rules [CA1307: Specify StringComparison for clarity](../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309: Use ordinal StringComparison](../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md) to find these call sites in your code.</span></span>

<span data-ttu-id="af693-129">Pour plus d’informations, consultez [changements de comportement lors de la comparaison de chaînes sur .net 5 +](../base-types/string-comparison-net-5-plus.md).</span><span class="sxs-lookup"><span data-stu-id="af693-129">For more information, see [Behavior changes when comparing strings on .NET 5+](../base-types/string-comparison-net-5-plus.md).</span></span>

### <a name="use-nls-instead-of-icu"></a><span data-ttu-id="af693-130">Utiliser NLS au lieu de ICU</span><span class="sxs-lookup"><span data-stu-id="af693-130">Use NLS instead of ICU</span></span>

<span data-ttu-id="af693-131">L’utilisation de ICU au lieu de NLS peut entraîner des différences de comportement avec certaines opérations liées à la globalisation.</span><span class="sxs-lookup"><span data-stu-id="af693-131">Using ICU instead of NLS may result in behavioral differences with some globalization-related operations.</span></span> <span data-ttu-id="af693-132">Pour revenir à l’utilisation de NLS, un développeur peut refuser l’implémentation de la bibliothèque ICU.</span><span class="sxs-lookup"><span data-stu-id="af693-132">To revert back to using NLS, a developer can opt out of the ICU implementation.</span></span> <span data-ttu-id="af693-133">Les applications peuvent activer le mode NLS de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="af693-133">Applications can enable NLS mode in any of the following ways:</span></span>

- <span data-ttu-id="af693-134">Dans le fichier projet :</span><span class="sxs-lookup"><span data-stu-id="af693-134">In the project file:</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="af693-135">Dans le fichier `runtimeconfig.json` :</span><span class="sxs-lookup"><span data-stu-id="af693-135">In the `runtimeconfig.json` file:</span></span>

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.UseNls": true
        }
    }
  }
  ```

- <span data-ttu-id="af693-136">En affectant à la variable `DOTNET_SYSTEM_GLOBALIZATION_USENLS` d’environnement la valeur `true` ou `1` .</span><span class="sxs-lookup"><span data-stu-id="af693-136">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_USENLS` to the value `true` or `1`.</span></span>

> [!NOTE]
> <span data-ttu-id="af693-137">Une valeur définie dans le projet ou dans le `runtimeconfig.json` fichier est prioritaire sur la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="af693-137">A value set in the project or in the `runtimeconfig.json` file takes precedence over the environment variable.</span></span>

<span data-ttu-id="af693-138">Pour plus d’informations, consultez [paramètres de configuration au moment](../../core/run-time-config/globalization.md#nls)de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="af693-138">For more information, see [Run-time config settings](../../core/run-time-config/globalization.md#nls).</span></span>

## <a name="app-local-icu"></a><span data-ttu-id="af693-139">Bibliothèque ICU locale d’application</span><span class="sxs-lookup"><span data-stu-id="af693-139">App-local ICU</span></span>

<span data-ttu-id="af693-140">Chaque version d’ICU peut apporter des correctifs de bogues, ainsi que des données de référentiel de données locales (CLDR) mises à jour qui décrivent les langues du monde.</span><span class="sxs-lookup"><span data-stu-id="af693-140">Each release of ICU may bring with it bug fixes as well as updated Common Locale Data Repository (CLDR) data that describes the world's languages.</span></span> <span data-ttu-id="af693-141">Passer d’une version à une autre peut avoir un impact subtil sur le comportement des applications lorsqu’il s’agit d’opérations liées à la globalisation.</span><span class="sxs-lookup"><span data-stu-id="af693-141">Moving between versions of ICU can subtly impact app behavior when it comes to globalization-related operations.</span></span> <span data-ttu-id="af693-142">Pour aider les développeurs d’applications à garantir la cohérence de tous les déploiements, .NET 5,0 et versions ultérieures permettent aux applications sur Windows et UNIX de transporter et d’utiliser leur propre copie d’ICU.</span><span class="sxs-lookup"><span data-stu-id="af693-142">To help application developers ensure consistency across all deployments, .NET 5.0 and later versions enable apps on both Windows and Unix to carry and use their own copy of ICU.</span></span>

<span data-ttu-id="af693-143">Les applications peuvent s’abonner à un mode d’implémentation ICU local d’application de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="af693-143">Applications can opt in to an app-local ICU implementation mode in any of the following ways:</span></span>

- <span data-ttu-id="af693-144">Dans le fichier projet :</span><span class="sxs-lookup"><span data-stu-id="af693-144">In  the project file:</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
  </ItemGroup>
  ```

- <span data-ttu-id="af693-145">Dans le fichier `runtimeconfig.json` :</span><span class="sxs-lookup"><span data-stu-id="af693-145">In the `runtimeconfig.json` file:</span></span>

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
       }
    }
  }
  ```

- <span data-ttu-id="af693-146">En affectant à la variable `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` d’environnement la valeur `<suffix>:<version>` ou `<version>` .</span><span class="sxs-lookup"><span data-stu-id="af693-146">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` to the value `<suffix>:<version>` or `<version>`.</span></span>

  <span data-ttu-id="af693-147">`<suffix>`: Le suffixe facultatif d’une longueur inférieure à 36 caractères, conformément aux conventions d’empaquetage ICU publiques.</span><span class="sxs-lookup"><span data-stu-id="af693-147">`<suffix>`: Optional suffix of fewer than 36 characters in length, following the public ICU packaging conventions.</span></span> <span data-ttu-id="af693-148">Lorsque vous créez une bibliothèque ICU personnalisée, vous pouvez la personnaliser pour produire les noms lib et les noms de symboles exportés pour contenir un suffixe, par exemple, `libicuucmyapp` , où `myapp` est le suffixe.</span><span class="sxs-lookup"><span data-stu-id="af693-148">When building a custom ICU, you can customize it to produce the lib names and exported symbol names to contain a suffix, for example, `libicuucmyapp`, where `myapp` is the suffix.</span></span>

  <span data-ttu-id="af693-149">`<version>`: Version ICU valide, par exemple 67,1.</span><span class="sxs-lookup"><span data-stu-id="af693-149">`<version>`: A valid ICU version, for example, 67.1.</span></span> <span data-ttu-id="af693-150">Cette version est utilisée pour charger les binaires et pour récupérer les symboles exportés.</span><span class="sxs-lookup"><span data-stu-id="af693-150">This version is used to load the binaries and to get the exported symbols.</span></span>

<span data-ttu-id="af693-151">Pour charger ICU lorsque le commutateur local de l’application est défini, .NET utilise la <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> méthode, qui sonde plusieurs chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="af693-151">To load ICU when the app-local switch is set, .NET uses the <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> method, which probes multiple paths.</span></span> <span data-ttu-id="af693-152">La méthode essaie d’abord de trouver la bibliothèque dans la `NATIVE_DLL_SEARCH_DIRECTORIES` propriété, qui est créée par l’hôte dotnet en fonction du `deps.json` fichier de l’application.</span><span class="sxs-lookup"><span data-stu-id="af693-152">The method first tries to find the library in the `NATIVE_DLL_SEARCH_DIRECTORIES` property, which is created by the dotnet host based on the `deps.json` file for the app.</span></span> <span data-ttu-id="af693-153">Pour plus d’informations, consultez [détection par défaut](../../core/dependency-loading/default-probing.md).</span><span class="sxs-lookup"><span data-stu-id="af693-153">For more information, see [Default probing](../../core/dependency-loading/default-probing.md).</span></span>

<span data-ttu-id="af693-154">Pour les applications autonomes, aucune action spéciale n’est requise de la part de l’utilisateur, à l’exception de l’utilisation de la bibliothèque ICU dans le répertoire de l’application (pour les applications autonomes, le répertoire de travail est défini par défaut sur `NATIVE_DLL_SEARCH_DIRECTORIES` ).</span><span class="sxs-lookup"><span data-stu-id="af693-154">For self-contained apps, no special action is required by the user, other than making sure ICU is in the app directory (for self-contained apps, the working directory defaults to `NATIVE_DLL_SEARCH_DIRECTORIES`).</span></span>

<span data-ttu-id="af693-155">Si vous utilisez ICU via un package NuGet, cela fonctionne dans les applications dépendantes du Framework.</span><span class="sxs-lookup"><span data-stu-id="af693-155">If you're consuming ICU via a NuGet package, this works in framework-dependent applications.</span></span> <span data-ttu-id="af693-156">NuGet résout les ressources natives et les comprend dans le `deps.json` fichier et dans le répertoire de sortie de l’application sous le `runtimes` répertoire.</span><span class="sxs-lookup"><span data-stu-id="af693-156">NuGet resolves the native assets and includes them in the `deps.json` file and in the output directory for the application under the `runtimes` directory.</span></span> <span data-ttu-id="af693-157">.NET le charge à partir de là.</span><span class="sxs-lookup"><span data-stu-id="af693-157">.NET loads it from there.</span></span>

<span data-ttu-id="af693-158">Pour les applications dépendantes du Framework (non autonomes) où ICU est consommé à partir d’une build locale, vous devez effectuer des étapes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="af693-158">For framework-dependent apps (not self contained) where ICU is consumed from a local build, you must take additional steps.</span></span> <span data-ttu-id="af693-159">Le kit de développement logiciel (SDK) .NET ne dispose pas encore d’une fonctionnalité pour les fichiers binaires natifs « libres » à incorporer dans `deps.json` (consultez [ce problème du SDK](https://github.com/dotnet/sdk/issues/11373)).</span><span class="sxs-lookup"><span data-stu-id="af693-159">The .NET SDK doesn't yet have a feature for "loose" native binaries to be incorporated into `deps.json` (see [this SDK issue](https://github.com/dotnet/sdk/issues/11373)).</span></span> <span data-ttu-id="af693-160">Au lieu de cela, vous pouvez l’activer en ajoutant des informations supplémentaires dans le fichier projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="af693-160">Instead, you can enable this by adding additional information into the application's project file.</span></span> <span data-ttu-id="af693-161">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="af693-161">For example:</span></span>

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

<span data-ttu-id="af693-162">Cela doit être fait pour tous les fichiers binaires ICU pour les runtimes pris en charge.</span><span class="sxs-lookup"><span data-stu-id="af693-162">This must be done for all the ICU binaries for the supported runtimes.</span></span> <span data-ttu-id="af693-163">En outre, les `NuGetPackageId` métadonnées dans le `RuntimeTargetsCopyLocalItems` groupe d’éléments doivent correspondre à un package NuGet auquel le projet fait référence.</span><span class="sxs-lookup"><span data-stu-id="af693-163">Also, the `NuGetPackageId` metadata in the `RuntimeTargetsCopyLocalItems` item group needs to match a NuGet package that the project actually references.</span></span>

### <a name="macos-behavior"></a><span data-ttu-id="af693-164">comportement macOS</span><span class="sxs-lookup"><span data-stu-id="af693-164">macOS behavior</span></span>

<span data-ttu-id="af693-165">`macOS` a un comportement différent pour la résolution des bibliothèques dynamiques dépendantes à partir des commandes de chargement spécifiées dans le `match-o` fichier que le chargeur Linux.</span><span class="sxs-lookup"><span data-stu-id="af693-165">`macOS` has a different behavior for resolving dependent dynamic libraries from the load commands specified in the `match-o` file than the Linux loader.</span></span> <span data-ttu-id="af693-166">Dans le chargeur Linux, .NET peut essayer `libicudata` , `libicuuc` et `libicui18n` (dans cet ordre) pour satisfaire le graphique de dépendance ICU.</span><span class="sxs-lookup"><span data-stu-id="af693-166">In the Linux loader, .NET can try `libicudata`, `libicuuc`, and `libicui18n` (in that order) to satisfy ICU dependency graph.</span></span> <span data-ttu-id="af693-167">Toutefois, sur macOS, cela ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="af693-167">However, on macOS, this doesn't work.</span></span> <span data-ttu-id="af693-168">Lors de la création d’une ICU sur macOS, vous pouvez, par défaut, obtenir une bibliothèque dynamique avec ces commandes de chargement dans `libicuuc` .</span><span class="sxs-lookup"><span data-stu-id="af693-168">When building ICU on macOS, you, by default, get a dynamic library with these load commands in `libicuuc`.</span></span> <span data-ttu-id="af693-169">L’extrait de code suivant montre un exemple.</span><span class="sxs-lookup"><span data-stu-id="af693-169">The following snippet shows an example.</span></span>

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

<span data-ttu-id="af693-170">Ces commandes font simplement référence au nom des bibliothèques dépendantes pour les autres composants d’ICU.</span><span class="sxs-lookup"><span data-stu-id="af693-170">These commands just reference the name of the dependent libraries for the other components of ICU.</span></span> <span data-ttu-id="af693-171">Le chargeur effectue la recherche en respectant les `dlopen` conventions, ce qui implique de disposer de ces bibliothèques dans les répertoires système ou de définir les `LD_LIBRARY_PATH` variables env, ou d’avoir une bibliothèque ICU au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="af693-171">The loader performs the search following the `dlopen` conventions, which involves having these libraries in the system directories or setting the `LD_LIBRARY_PATH` env vars, or having ICU at the app-level directory.</span></span> <span data-ttu-id="af693-172">Si vous ne pouvez pas définir `LD_LIBRARY_PATH` ou vous assurer que les fichiers binaires ICU se trouvent au niveau de l’application, vous devrez effectuer des tâches supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="af693-172">If you can't set `LD_LIBRARY_PATH` or ensure that ICU binaries are at the app-level directory, you will need to do some extra work.</span></span>

<span data-ttu-id="af693-173">Certaines directives pour le chargeur, comme `@loader_path` , indiquent au chargeur de rechercher cette dépendance dans le même répertoire que le fichier binaire de cette commande de chargement.</span><span class="sxs-lookup"><span data-stu-id="af693-173">There are some directives for the loader, like `@loader_path`, which tell the loader to search for that dependency in the same directory as the binary with that load command.</span></span> <span data-ttu-id="af693-174">Il existe deux moyens de parvenir à cet objectif :</span><span class="sxs-lookup"><span data-stu-id="af693-174">There are two ways to achieve this:</span></span>

- `install_name_tool -change`

  <span data-ttu-id="af693-175">Exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="af693-175">Run the following commands:</span></span>

  ```bash
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
  install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
  ```

- <span data-ttu-id="af693-176">Mise à jour corrective de la bibliothèque pour produire les noms d’installation `@loader_path`</span><span class="sxs-lookup"><span data-stu-id="af693-176">Patch ICU to produce the install names with `@loader_path`</span></span>

  <span data-ttu-id="af693-177">Avant d’exécuter autoconf ( `./runConfigureICU` ), remplacez [ces lignes](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) par :</span><span class="sxs-lookup"><span data-stu-id="af693-177">Before running autoconf (`./runConfigureICU`), change [these lines](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) to:</span></span>

  ```
  LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
  ```

## <a name="icu-on-webassembly"></a><span data-ttu-id="af693-178">ICU sur webassembly</span><span class="sxs-lookup"><span data-stu-id="af693-178">ICU on WebAssembly</span></span>

<span data-ttu-id="af693-179">Une version d’ICU est disponible spécifiquement pour les charges de travail webassembly.</span><span class="sxs-lookup"><span data-stu-id="af693-179">A version of ICU is available that's specifically for WebAssembly workloads.</span></span> <span data-ttu-id="af693-180">Cette version offre une compatibilité de globalisation avec les profils de bureau.</span><span class="sxs-lookup"><span data-stu-id="af693-180">This version provides globalization compatibility with desktop profiles.</span></span> <span data-ttu-id="af693-181">Pour réduire la taille du fichier de données ICU de 24 Mo à 1,4 Mo (ou ~ 0,3 Mo s’ils sont compressés avec Brotli), cette charge de travail présente quelques limitations.</span><span class="sxs-lookup"><span data-stu-id="af693-181">To reduce the ICU data file size from 24 MB to 1.4 MB (or ~0.3 MB if compressed with Brotli), this workload has a handful of limitations.</span></span>

<span data-ttu-id="af693-182">Les API suivantes ne sont pas prises en charge :</span><span class="sxs-lookup"><span data-stu-id="af693-182">The following APIs are not supported:</span></span>

- <xref:System.Globalization.CultureInfo.EnglishName?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.NativeName?displayProperty=nameWithType>
- <xref:System.Globalization.DateTimeFormatInfo.NativeCalendarName?displayProperty=nameWithType>
- <xref:System.Globalization.RegionInfo.NativeName?displayProperty=nameWithType>

<span data-ttu-id="af693-183">Les API suivantes sont prises en charge avec des limitations :</span><span class="sxs-lookup"><span data-stu-id="af693-183">The following APIs are supported with limitations:</span></span>

- <span data-ttu-id="af693-184"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> et <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> ne prennent pas en charge les formulaires et les rarement utilisés <xref:System.Text.NormalizationForm.FormKC> <xref:System.Text.NormalizationForm.FormKD> .</span><span class="sxs-lookup"><span data-stu-id="af693-184"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> and <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> don't support the rarely used <xref:System.Text.NormalizationForm.FormKC> and <xref:System.Text.NormalizationForm.FormKD> forms.</span></span>
- <span data-ttu-id="af693-185"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> retourne la même valeur que <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af693-185"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> returns the same value as <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="af693-186">En outre, une liste des paramètres régionaux pris en charge est disponible sur la [référentiel dotnet/ICU](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54).</span><span class="sxs-lookup"><span data-stu-id="af693-186">In addition, a list of supported locales can be found on the [dotnet/icu repo](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54).</span></span>
