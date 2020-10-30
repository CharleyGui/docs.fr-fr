---
title: Globalisation et ICU
ms.date: 05/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- globalization [.NET], about globalization
- global applications, globalization
- international applications [.NET], globalization
- world-ready applications, globalization
- application development [.NET], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: 87d0103e90d46ae83b23c9cc05e9efcaa51c831f
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063987"
---
# <a name="net-globalization-and-icu"></a><span data-ttu-id="c6b26-102">Globalisation et ICU .NET</span><span class="sxs-lookup"><span data-stu-id="c6b26-102">.NET globalization and ICU</span></span>

<span data-ttu-id="c6b26-103">Dans le passé, les API de globalisation .NET utilisaient des bibliothèques sous-jacentes différentes sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="c6b26-103">In the past, the .NET globalization APIs used different underlying libraries on different platforms.</span></span> <span data-ttu-id="c6b26-104">Sur UNIX, les API utilisaient les [composants internationaux pour Unicode (ICU)](http://site.icu-project.org/home)et sur Windows, ils utilisaient le [service NLS (National Language Support)](/windows/win32/intl/national-language-support).</span><span class="sxs-lookup"><span data-stu-id="c6b26-104">On Unix, the APIs used [International Components for Unicode (ICU)](http://site.icu-project.org/home), and on Windows, they used [National Language Support (NLS)](/windows/win32/intl/national-language-support).</span></span> <span data-ttu-id="c6b26-105">Cela a entraîné certaines différences de comportement dans une poignée d’API de globalisation lors de l’exécution d’applications sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="c6b26-105">This resulted in some behavioral differences in a handful of globalization APIs when running applications on different platforms.</span></span> <span data-ttu-id="c6b26-106">Les différences de comportement étaient évidentes dans les domaines suivants :</span><span class="sxs-lookup"><span data-stu-id="c6b26-106">Behavior differences were evident in these areas:</span></span>

- <span data-ttu-id="c6b26-107">Cultures et données de culture</span><span class="sxs-lookup"><span data-stu-id="c6b26-107">Cultures and culture data</span></span>
- <span data-ttu-id="c6b26-108">Casse des chaînes</span><span class="sxs-lookup"><span data-stu-id="c6b26-108">String casing</span></span>
- <span data-ttu-id="c6b26-109">Tri et recherche de chaînes</span><span class="sxs-lookup"><span data-stu-id="c6b26-109">String sorting and searching</span></span>
- <span data-ttu-id="c6b26-110">Trier les clés</span><span class="sxs-lookup"><span data-stu-id="c6b26-110">Sort keys</span></span>
- <span data-ttu-id="c6b26-111">Normalisation des chaînes</span><span class="sxs-lookup"><span data-stu-id="c6b26-111">String normalization</span></span>
- <span data-ttu-id="c6b26-112">Prise en charge des IDN (Internationalized Domain Names)</span><span class="sxs-lookup"><span data-stu-id="c6b26-112">Internationalized Domain Names (IDN) support</span></span>
- <span data-ttu-id="c6b26-113">Nom d’affichage du fuseau horaire sur Linux</span><span class="sxs-lookup"><span data-stu-id="c6b26-113">Time zone display name on Linux</span></span>

<span data-ttu-id="c6b26-114">À compter de .NET 5,0, les développeurs ont plus de contrôle sur la bibliothèque sous-jacente utilisée, ce qui permet aux applications d’éviter les différences entre les plateformes.</span><span class="sxs-lookup"><span data-stu-id="c6b26-114">Starting with .NET 5.0, developers have more control over which underlying library is used, enabling applications to avoid differences across platforms.</span></span>

## <a name="icu-on-windows"></a><span data-ttu-id="c6b26-115">ICU sur Windows</span><span class="sxs-lookup"><span data-stu-id="c6b26-115">ICU on Windows</span></span>

<span data-ttu-id="c6b26-116">La mise à jour de Windows 10 mai 2019 et les versions ultérieures incluent [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) dans le cadre du système d’exploitation, et .net 5,0 et versions ultérieures utilisent ICU par défaut.</span><span class="sxs-lookup"><span data-stu-id="c6b26-116">Windows 10 May 2019 Update and later versions include [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) as part of the OS, and .NET 5.0 and later versions use ICU by default.</span></span> <span data-ttu-id="c6b26-117">Lors de l’exécution sous Windows, .NET 5,0 et versions ultérieures essaient de charger `icu.dll` et, s’il est disponible, les utilise pour l’implémentation de la globalisation.</span><span class="sxs-lookup"><span data-stu-id="c6b26-117">When running on Windows, .NET 5.0 and later versions try to load `icu.dll` and if it's available, uses it for the globalization implementation.</span></span>  <span data-ttu-id="c6b26-118">Si cette bibliothèque est introuvable ou ne peut pas être chargée, par exemple lors de l’exécution sur des versions antérieures de Windows, .NET 5,0 et versions ultérieures reviennent à l’implémentation basée sur NLS.</span><span class="sxs-lookup"><span data-stu-id="c6b26-118">If that library can't be found or loaded, such as when running on older versions of Windows, .NET 5.0 and later versions fall back to the NLS-based implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="c6b26-119">Même quand vous utilisez ICU, `CurrentCulture` les `CurrentUICulture` membres, et `CurrentRegion` continuent d’utiliser les API du système d’exploitation Windows pour honorer les paramètres utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c6b26-119">Even when using ICU, the `CurrentCulture`, `CurrentUICulture`, and `CurrentRegion` members still use Windows operating system APIs to honor user settings.</span></span>

### <a name="using-nls-instead-of-icu"></a><span data-ttu-id="c6b26-120">Utilisation de NLS au lieu d’ICU</span><span class="sxs-lookup"><span data-stu-id="c6b26-120">Using NLS instead of ICU</span></span>

<span data-ttu-id="c6b26-121">L’utilisation de ICU au lieu de NLS peut entraîner des différences de comportement avec certaines opérations liées à la globalisation.</span><span class="sxs-lookup"><span data-stu-id="c6b26-121">Using ICU instead of NLS may result in behavioral differences with some globalization-related operations.</span></span> <span data-ttu-id="c6b26-122">Pour revenir à l’utilisation de NLS, un développeur peut refuser l’implémentation de la bibliothèque ICU.</span><span class="sxs-lookup"><span data-stu-id="c6b26-122">To revert back to using NLS, a developer can opt out of the ICU implementation.</span></span> <span data-ttu-id="c6b26-123">Les applications peuvent activer le mode NLS de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6b26-123">Applications can enable NLS mode in any of the following ways:</span></span>

- <span data-ttu-id="c6b26-124">Dans le fichier projet :</span><span class="sxs-lookup"><span data-stu-id="c6b26-124">In the project file:</span></span>

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
</ItemGroup>
```

- <span data-ttu-id="c6b26-125">Dans le fichier `runtimeconfig.json` :</span><span class="sxs-lookup"><span data-stu-id="c6b26-125">In the `runtimeconfig.json` file:</span></span>

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.UseNls": true
      }
  }
}
```

- <span data-ttu-id="c6b26-126">En affectant à la variable `DOTNET_SYSTEM_GLOBALIZATION_USENLS` d’environnement la valeur `true` ou `1` .</span><span class="sxs-lookup"><span data-stu-id="c6b26-126">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_USENLS` to the value `true` or `1`.</span></span>

> [!NOTE]
> <span data-ttu-id="c6b26-127">Une valeur définie dans le projet ou dans le `runtimeconfig.json` fichier est prioritaire sur la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="c6b26-127">A value set in the project or in the `runtimeconfig.json` file takes precedence over the environment variable.</span></span>

<span data-ttu-id="c6b26-128">Pour plus d’informations, consultez [paramètres de configuration au moment](../../core/run-time-config/globalization.md#nls)de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c6b26-128">For more information, see [Run-time config settings](../../core/run-time-config/globalization.md#nls).</span></span>

## <a name="app-local-icu"></a><span data-ttu-id="c6b26-129">Bibliothèque ICU locale d’application</span><span class="sxs-lookup"><span data-stu-id="c6b26-129">App-local ICU</span></span>

<span data-ttu-id="c6b26-130">Chaque version d’ICU peut apporter des correctifs de bogues, ainsi que des données de référentiel de données locales (CLDR) mises à jour qui décrivent les langues du monde.</span><span class="sxs-lookup"><span data-stu-id="c6b26-130">Each release of ICU may bring with it bug fixes as well as updated Common Locale Data Repository (CLDR) data that describes the world's languages.</span></span> <span data-ttu-id="c6b26-131">Passer d’une version à une autre peut avoir un impact subtil sur le comportement des applications lorsqu’il s’agit d’opérations liées à la globalisation.</span><span class="sxs-lookup"><span data-stu-id="c6b26-131">Moving between versions of ICU can subtly impact app behavior when it comes to globalization-related operations.</span></span>  <span data-ttu-id="c6b26-132">Pour aider les développeurs d’applications à garantir la cohérence de tous les déploiements, .NET 5,0 et versions ultérieures permettent aux applications sur Windows et UNIX de transporter et d’utiliser leur propre copie d’ICU.</span><span class="sxs-lookup"><span data-stu-id="c6b26-132">To help application developers ensure consistency across all deployments, .NET 5.0 and later versions enable apps on both Windows and Unix to carry and use their own copy of ICU.</span></span>

<span data-ttu-id="c6b26-133">Les applications peuvent s’abonner à un mode d’implémentation ICU local d’application de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6b26-133">Applications can opt in to an app-local ICU implementation mode in any of the following ways:</span></span>

- <span data-ttu-id="c6b26-134">Dans le fichier projet :</span><span class="sxs-lookup"><span data-stu-id="c6b26-134">In  the project file:</span></span>

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
</ItemGroup>
```

- <span data-ttu-id="c6b26-135">Dans le fichier `runtimeconfig.json` :</span><span class="sxs-lookup"><span data-stu-id="c6b26-135">In the `runtimeconfig.json` file:</span></span>

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
      }
  }
}
```

- <span data-ttu-id="c6b26-136">En affectant à la variable `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` d’environnement la valeur `<suffix>:<version>` ou `<version>` .</span><span class="sxs-lookup"><span data-stu-id="c6b26-136">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` to the value `<suffix>:<version>` or `<version>`.</span></span>

<span data-ttu-id="c6b26-137">`<suffix>`: Le suffixe facultatif d’une longueur inférieure à 36 caractères, conformément aux conventions d’empaquetage ICU publiques.</span><span class="sxs-lookup"><span data-stu-id="c6b26-137">`<suffix>`: Optional suffix of less than 36 characters in length, following the public ICU packaging conventions.</span></span> <span data-ttu-id="c6b26-138">Lorsque vous créez une bibliothèque ICU personnalisée, vous pouvez la personnaliser pour produire les noms lib et les noms de symboles exportés pour contenir un suffixe, par exemple, `libicuucmyapp` , où `myapp` est le suffixe.</span><span class="sxs-lookup"><span data-stu-id="c6b26-138">When building a custom ICU, you can customize it to produce the lib names and exported symbol names to contain a suffix, for example, `libicuucmyapp`, where `myapp` is the suffix.</span></span>

<span data-ttu-id="c6b26-139">`<version>`: Version ICU valide, par exemple 67,1.</span><span class="sxs-lookup"><span data-stu-id="c6b26-139">`<version>`: A valid ICU version, for example, 67.1.</span></span> <span data-ttu-id="c6b26-140">Cette version est utilisée pour charger les binaires et pour récupérer les symboles exportés.</span><span class="sxs-lookup"><span data-stu-id="c6b26-140">This version is used to load the binaries and to get the exported symbols.</span></span>

<span data-ttu-id="c6b26-141">Pour charger ICU lorsque le commutateur local de l’application est défini, .NET utilise la <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> méthode, qui sonde plusieurs chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="c6b26-141">To load ICU when the app-local switch is set, .NET uses the <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> method, which probes multiple paths.</span></span> <span data-ttu-id="c6b26-142">La méthode essaie d’abord de trouver la bibliothèque dans la `NATIVE_DLL_SEARCH_DIRECTORIES` propriété, qui est créée par l’hôte dotnet en fonction du `deps.json` fichier de l’application.</span><span class="sxs-lookup"><span data-stu-id="c6b26-142">The method first tries to find the library in the `NATIVE_DLL_SEARCH_DIRECTORIES` property, which is created by the dotnet host based on the `deps.json` file for the app.</span></span> <span data-ttu-id="c6b26-143">Pour plus d’informations, consultez [détection par défaut](../../core/dependency-loading/default-probing.md).</span><span class="sxs-lookup"><span data-stu-id="c6b26-143">For more information, see [Default probing](../../core/dependency-loading/default-probing.md).</span></span>

<span data-ttu-id="c6b26-144">Pour les applications autonomes, aucune action spéciale n’est requise de la part de l’utilisateur, à l’exception de l’utilisation de la bibliothèque ICU dans le répertoire de l’application (pour les applications autonomes, le répertoire de travail est défini par défaut sur `NATIVE_DLL_SEARCH_DIRECTORIES` ).</span><span class="sxs-lookup"><span data-stu-id="c6b26-144">For self-contained apps, no special action is required by the user, other than making sure ICU is in the app directory (for self-contained apps, the working directory defaults to `NATIVE_DLL_SEARCH_DIRECTORIES`).</span></span>

<span data-ttu-id="c6b26-145">Si vous utilisez ICU via un package NuGet, cela fonctionne dans les applications dépendantes du Framework.</span><span class="sxs-lookup"><span data-stu-id="c6b26-145">If you're consuming ICU via a NuGet package, this works in framework-dependent applications.</span></span> <span data-ttu-id="c6b26-146">NuGet résout les ressources natives et les comprend dans le `deps.json` fichier et dans le répertoire de sortie de l’application sous le `runtimes` répertoire.</span><span class="sxs-lookup"><span data-stu-id="c6b26-146">NuGet resolves the native assets and includes them in the `deps.json` file and in the output directory for the application under the `runtimes` directory.</span></span> <span data-ttu-id="c6b26-147">.NET le charge à partir de là.</span><span class="sxs-lookup"><span data-stu-id="c6b26-147">.NET loads it from there.</span></span>

<span data-ttu-id="c6b26-148">Pour les applications dépendantes du Framework (non autonomes) où ICU est consommé à partir d’une build locale, vous devez effectuer des étapes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c6b26-148">For framework-dependent apps (not self contained) where ICU is consumed from a local build, you must take additional steps.</span></span> <span data-ttu-id="c6b26-149">Le kit de développement logiciel (SDK) .NET ne dispose pas encore d’une fonctionnalité pour les fichiers binaires natifs « libres » à incorporer dans `deps.json` (consultez [ce problème du SDK](https://github.com/dotnet/sdk/issues/11373)).</span><span class="sxs-lookup"><span data-stu-id="c6b26-149">The .NET SDK doesn't yet have a feature for "loose" native binaries to be incorporated into `deps.json` (see [this SDK issue](https://github.com/dotnet/sdk/issues/11373)).</span></span> <span data-ttu-id="c6b26-150">Au lieu de cela, vous pouvez l’activer en ajoutant des informations supplémentaires dans le fichier projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="c6b26-150">Instead, you can enable this by adding additional information into the application's project file.</span></span> <span data-ttu-id="c6b26-151">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c6b26-151">For example:</span></span>

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

<span data-ttu-id="c6b26-152">Cela doit être fait pour tous les fichiers binaires ICU pour les runtimes pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c6b26-152">This must be done for all the ICU binaries for the supported runtimes.</span></span> <span data-ttu-id="c6b26-153">En outre, les `NuGetPackageId` métadonnées dans le `RuntimeTargetsCopyLocalItems` groupe d’éléments doivent correspondre à un package NuGet auquel le projet fait référence.</span><span class="sxs-lookup"><span data-stu-id="c6b26-153">Also, the `NuGetPackageId` metadata in the `RuntimeTargetsCopyLocalItems` item group needs to match a NuGet package that the project actually references.</span></span>

### <a name="macos-behavior"></a><span data-ttu-id="c6b26-154">comportement macOS</span><span class="sxs-lookup"><span data-stu-id="c6b26-154">macOS behavior</span></span>

<span data-ttu-id="c6b26-155">`macOS` a un comportement différent pour la résolution des bibliothèques dynamiques dépendantes à partir des commandes de chargement spécifiées dans le `match-o` fichier que le chargeur Linux.</span><span class="sxs-lookup"><span data-stu-id="c6b26-155">`macOS` has a different behavior for resolving dependent dynamic libraries from the load commands specified in the `match-o` file than the Linux loader.</span></span> <span data-ttu-id="c6b26-156">Dans le chargeur Linux, .NET peut essayer `libicudata` , `libicuuc` et `libicui18n` (dans cet ordre) pour satisfaire le graphique de dépendance ICU.</span><span class="sxs-lookup"><span data-stu-id="c6b26-156">In the Linux loader, .NET can try `libicudata`, `libicuuc`, and `libicui18n` (in that order) to satisfy ICU dependency graph.</span></span> <span data-ttu-id="c6b26-157">Toutefois, sur macOS, cela ne fonctionne pas.</span><span class="sxs-lookup"><span data-stu-id="c6b26-157">However, on macOS, this doesn't work.</span></span> <span data-ttu-id="c6b26-158">Lors de la création d’une ICU sur macOS, vous pouvez, par défaut, obtenir une bibliothèque dynamique avec ces commandes de chargement dans `libicuuc` .</span><span class="sxs-lookup"><span data-stu-id="c6b26-158">When building ICU on macOS, you, by default, get a dynamic library with these load commands in `libicuuc`.</span></span> <span data-ttu-id="c6b26-159">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c6b26-159">For example.:</span></span>

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

<span data-ttu-id="c6b26-160">Ces commandes font simplement référence au nom des bibliothèques dépendantes pour les autres composants d’ICU.</span><span class="sxs-lookup"><span data-stu-id="c6b26-160">These commands just reference the name of the dependent libraries for the other components of ICU.</span></span> <span data-ttu-id="c6b26-161">Le chargeur effectue la recherche en respectant les `dlopen` conventions, ce qui implique de disposer de ces bibliothèques dans les répertoires système ou de définir les `LD_LIBRARY_PATH` variables env, ou d’avoir une bibliothèque ICU au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="c6b26-161">The loader performs the search following the `dlopen` conventions, which involves having these libraries in the system directories or setting the `LD_LIBRARY_PATH` env vars, or having ICU at the app-level directory.</span></span> <span data-ttu-id="c6b26-162">Si vous ne pouvez pas définir `LD_LIBRARY_PATH` ou vous assurer que les fichiers binaires ICU se trouvent au niveau de l’application, vous devrez effectuer des tâches supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c6b26-162">If you can't set `LD_LIBRARY_PATH` or ensure that ICU binaries are at the app-level directory, you will need to do some extra work.</span></span>

<span data-ttu-id="c6b26-163">Certaines directives pour le chargeur, comme `@loader_path` , indiquent au chargeur de rechercher cette dépendance dans le même répertoire que le fichier binaire de cette commande de chargement.</span><span class="sxs-lookup"><span data-stu-id="c6b26-163">There are some directives for the loader, like `@loader_path`, which tell the loader to search for that dependency in the same directory as the binary with that load command.</span></span> <span data-ttu-id="c6b26-164">Il existe deux moyens de parvenir à cet objectif :</span><span class="sxs-lookup"><span data-stu-id="c6b26-164">There are two ways to achieve this:</span></span>

- `install_name_tool -change`

  <span data-ttu-id="c6b26-165">Exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6b26-165">Run the following commands:</span></span>

```bash
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
```

- <span data-ttu-id="c6b26-166">Mise à jour corrective de la bibliothèque pour produire les noms d’installation `@loader_path`</span><span class="sxs-lookup"><span data-stu-id="c6b26-166">Patch ICU to produce the install names with `@loader_path`</span></span>

  <span data-ttu-id="c6b26-167">Avant d’exécuter autoconf ( `./runConfigureICU` ), remplacez [ces lignes](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) par :</span><span class="sxs-lookup"><span data-stu-id="c6b26-167">Before running autoconf (`./runConfigureICU`), change [these lines](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) to:</span></span>

```
LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
```

## <a name="icu-on-webassembly"></a><span data-ttu-id="c6b26-168">ICU sur webassembly</span><span class="sxs-lookup"><span data-stu-id="c6b26-168">ICU on WebAssembly</span></span>

<span data-ttu-id="c6b26-169">Une version d’ICU est disponible spécifiquement pour les charges de travail webassembly.</span><span class="sxs-lookup"><span data-stu-id="c6b26-169">A version of ICU is available that's specifically for WebAssembly workloads.</span></span> <span data-ttu-id="c6b26-170">Cette version offre une compatibilité de globalisation avec les profils de bureau.</span><span class="sxs-lookup"><span data-stu-id="c6b26-170">This version provides globalization compatibility with desktop profiles.</span></span> <span data-ttu-id="c6b26-171">Pour réduire la taille du fichier de données ICU de 24 Mo à 1,4 Mo (ou ~ 0,3 Mo s’ils sont compressés avec Brotli), cette charge de travail présente quelques limitations.</span><span class="sxs-lookup"><span data-stu-id="c6b26-171">To reduce the ICU data file size from 24 MB to 1.4 MB (or ~0.3 MB if compressed with Brotli), this workload has a handful of limitations.</span></span>

<span data-ttu-id="c6b26-172">Les API suivantes ne sont pas prises en charge :</span><span class="sxs-lookup"><span data-stu-id="c6b26-172">The following APIs are not supported:</span></span>

- <xref:System.Globalization.CultureInfo.EnglishName?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.NativeName?displayProperty=nameWithType>
- <xref:System.Globalization.DateTimeFormatInfo.NativeCalendarName?displayProperty=nameWithType>
- <xref:System.Globalization.RegionInfo.NativeName?displayProperty=nameWithType>

<span data-ttu-id="c6b26-173">Les API suivantes sont prises en charge avec des limitations :</span><span class="sxs-lookup"><span data-stu-id="c6b26-173">The following APIs are supported with limitations:</span></span>

- <span data-ttu-id="c6b26-174"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> et <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> ne prennent pas en charge les formulaires et les rarement utilisés <xref:System.Text.NormalizationForm.FormKC> <xref:System.Text.NormalizationForm.FormKD> .</span><span class="sxs-lookup"><span data-stu-id="c6b26-174"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> and <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> don't support the rarely used <xref:System.Text.NormalizationForm.FormKC> and <xref:System.Text.NormalizationForm.FormKD> forms.</span></span>
- <span data-ttu-id="c6b26-175"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> retourne la même valeur que <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6b26-175"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> returns the same value as <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c6b26-176">En outre, une liste des paramètres régionaux pris en charge est disponible sur la [référentiel dotnet/ICU](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54).</span><span class="sxs-lookup"><span data-stu-id="c6b26-176">In addition, a list of supported locales can be found on the [dotnet/icu repo](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54).</span></span>
