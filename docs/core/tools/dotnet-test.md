---
title: Commande dotnet test
description: La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné.
ms.date: 04/29/2020
ms.openlocfilehash: 22b27007d26c98cff40733ef8d449ce334f87848
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802679"
---
# <a name="dotnet-test"></a><span data-ttu-id="8d236-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8d236-103">dotnet test</span></span>

<span data-ttu-id="8d236-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="8d236-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8d236-105">Nom</span><span class="sxs-lookup"><span data-stu-id="8d236-105">Name</span></span>

<span data-ttu-id="8d236-106">`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="8d236-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8d236-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8d236-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="8d236-108">Description</span><span class="sxs-lookup"><span data-stu-id="8d236-108">Description</span></span>

<span data-ttu-id="8d236-109">La `dotnet test` commande est utilisée pour exécuter des tests unitaires dans une solution donnée.</span><span class="sxs-lookup"><span data-stu-id="8d236-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="8d236-110">La `dotnet test` commande génère la solution et exécute une application hôte de test pour chaque projet de test de la solution.</span><span class="sxs-lookup"><span data-stu-id="8d236-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="8d236-111">L’hôte de test exécute des tests dans le projet donné à l’aide d’une infrastructure de test, par exemple, MSTest, NUnit ou xUnit, et signale la réussite ou l’échec de chaque test.</span><span class="sxs-lookup"><span data-stu-id="8d236-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="8d236-112">Si tous les tests réussissent, l’exécuteur de tests retourne 0 en tant que code de sortie. Sinon, si un test échoue, il retourne 1.</span><span class="sxs-lookup"><span data-stu-id="8d236-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="8d236-113">Pour les projets multi-ciblés, les tests sont exécutés pour chaque Framework ciblé.</span><span class="sxs-lookup"><span data-stu-id="8d236-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="8d236-114">L’hôte de test et l’infrastructure de tests unitaires sont empaquetés en tant que packages NuGet et sont restaurés en tant que dépendances ordinaires pour le projet.</span><span class="sxs-lookup"><span data-stu-id="8d236-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="8d236-115">Les projets de test spécifient l’application Test Runner à l’aide d’un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :</span><span class="sxs-lookup"><span data-stu-id="8d236-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="8d236-116">Où `Microsoft.NET.Test.Sdk` est l’hôte de test, `xunit` est l’infrastructure de test.</span><span class="sxs-lookup"><span data-stu-id="8d236-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="8d236-117">Et `xunit.runner.visualstudio` est un adaptateur de test, qui permet à l’infrastructure xUnit de fonctionner avec l’hôte de test.</span><span class="sxs-lookup"><span data-stu-id="8d236-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="8d236-118">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="8d236-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="8d236-119">Arguments</span><span class="sxs-lookup"><span data-stu-id="8d236-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="8d236-120">Chemin du projet de test.</span><span class="sxs-lookup"><span data-stu-id="8d236-120">Path to the test project.</span></span>
  - <span data-ttu-id="8d236-121">Chemin d’accès à la solution.</span><span class="sxs-lookup"><span data-stu-id="8d236-121">Path to the solution.</span></span>
  - <span data-ttu-id="8d236-122">Chemin d’accès à un répertoire qui contient un projet ou une solution.</span><span class="sxs-lookup"><span data-stu-id="8d236-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="8d236-123">Chemin d’accès à un fichier *. dll* de projet de test.</span><span class="sxs-lookup"><span data-stu-id="8d236-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="8d236-124">S’il n’est pas spécifié, il recherche un projet ou une solution dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="8d236-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="8d236-125">Options</span><span class="sxs-lookup"><span data-stu-id="8d236-125">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="8d236-126">Chemin d’accès à un répertoire dans lequel rechercher d’autres adaptateurs de test.</span><span class="sxs-lookup"><span data-stu-id="8d236-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="8d236-127">Seuls les fichiers *. dll* avec suffixe `.TestAdapter.dll` sont inspectés.</span><span class="sxs-lookup"><span data-stu-id="8d236-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="8d236-128">S’il n’est pas spécifié, la recherche s’effectue dans le répertoire du *fichier test. dll* .</span><span class="sxs-lookup"><span data-stu-id="8d236-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="8d236-129">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="8d236-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="8d236-130">Cette option est utile pour isoler les tests problématiques qui provoquent le blocage de l’hôte de test.</span><span class="sxs-lookup"><span data-stu-id="8d236-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="8d236-131">Lorsqu’un incident est détecté, il crée un fichier de séquence dans `TestResults/<Guid>/<Guid>_Sequence.xml` qui capture l’ordre des tests qui ont été exécutés avant l’incident.</span><span class="sxs-lookup"><span data-stu-id="8d236-131">When a crash is detected, it creates an sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="8d236-132">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="8d236-132">Defines the build configuration.</span></span> <span data-ttu-id="8d236-133">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="8d236-133">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="8d236-134">Active le collecteur de données pour la série de tests.</span><span class="sxs-lookup"><span data-stu-id="8d236-134">Enables data collector for the test run.</span></span> <span data-ttu-id="8d236-135">Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).</span><span class="sxs-lookup"><span data-stu-id="8d236-135">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="8d236-136">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié et dans des fichiers à côté de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="8d236-136">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="8d236-137">Le processus d’enregistrement des messages détermine quels fichiers sont créés, par exemple `*.host_<date>.txt` pour le journal de l’hôte de test et `*.datacollector_<date>.txt` pour le journal du collecteur de données.</span><span class="sxs-lookup"><span data-stu-id="8d236-137">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="8d236-138">Force l’utilisation de `dotnet` ou .NET Framework hôte de test pour les binaires de test.</span><span class="sxs-lookup"><span data-stu-id="8d236-138">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="8d236-139">Cette option détermine uniquement le type d’hôte à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8d236-139">This option only determines which type of host to use.</span></span> <span data-ttu-id="8d236-140">La version d’infrastructure réelle à utiliser est déterminée par le *runtimeconfig. JSON* du projet de test.</span><span class="sxs-lookup"><span data-stu-id="8d236-140">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="8d236-141">Lorsqu’il n’est pas spécifié, l' [attribut d’assembly TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) est utilisé pour déterminer le type d’hôte.</span><span class="sxs-lookup"><span data-stu-id="8d236-141">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="8d236-142">Lorsque cet attribut est supprimé du *fichier. dll*, l’hôte .NET Framework est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8d236-142">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="8d236-143">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="8d236-143">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="8d236-144">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="8d236-144">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="8d236-145">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="8d236-145">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="8d236-146">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="8d236-146">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="8d236-147">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8d236-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="8d236-148">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="8d236-148">For example, to complete authentication.</span></span> <span data-ttu-id="8d236-149">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8d236-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="8d236-150">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="8d236-150">Specifies a logger for test results.</span></span> <span data-ttu-id="8d236-151">Contrairement à MSBuild, dotnet test n’accepte pas les abréviations : au lieu d' `-l "console;v=d"` utiliser `-l "console;verbosity=detailed"` .</span><span class="sxs-lookup"><span data-stu-id="8d236-151">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="8d236-152">Ne génère pas le projet de test avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="8d236-152">Doesn't build the test project before running it.</span></span> <span data-ttu-id="8d236-153">Il définit également implicitement l' `--no-restore` indicateur-.</span><span class="sxs-lookup"><span data-stu-id="8d236-153">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="8d236-154">Exécuter les tests sans afficher la bannière Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="8d236-154">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="8d236-155">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8d236-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="8d236-156">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="8d236-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="8d236-157">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="8d236-157">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="8d236-158">S’il n’est pas spécifié, le chemin d'accès par défaut est `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="8d236-158">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="8d236-159">Pour les projets avec plusieurs frameworks cibles (via la `TargetFrameworks` propriété), vous devez également définir `--framework` lorsque vous spécifiez cette option.</span><span class="sxs-lookup"><span data-stu-id="8d236-159">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="8d236-160">`dotnet test`exécute toujours les tests à partir du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="8d236-160">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="8d236-161">Vous pouvez utiliser <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> pour consommer des ressources de test dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="8d236-161">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="8d236-162">Répertoire où les résultats de test doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="8d236-162">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="8d236-163">Si le répertoire spécifié n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="8d236-163">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="8d236-164">La valeur par défaut se trouve `TestResults` dans le répertoire qui contient le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="8d236-164">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="8d236-165">Runtime cible à tester.</span><span class="sxs-lookup"><span data-stu-id="8d236-165">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="8d236-166">Fichier `.runsettings` à utiliser pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="8d236-166">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="8d236-167">Notez que l' `TargetPlatform` élément (x86 | x64) n’a aucun effet pour `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="8d236-167">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="8d236-168">Pour exécuter des tests ciblant x86, installez la version x86 de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8d236-168">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="8d236-169">Le nombre de bits de *dotnet. exe* qui se trouve sur le chemin d’accès correspond à ce qui sera utilisé pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="8d236-169">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="8d236-170">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d236-170">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="8d236-171">Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="8d236-171">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="8d236-172">Configurer une série de tests</span><span class="sxs-lookup"><span data-stu-id="8d236-172">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="8d236-173">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="8d236-173">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="8d236-174">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="8d236-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8d236-175">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="8d236-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="8d236-176">Par défaut, il s’agit de `minimal`.</span><span class="sxs-lookup"><span data-stu-id="8d236-176">The default is `minimal`.</span></span> <span data-ttu-id="8d236-177">Pour plus d'informations, consultez <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="8d236-177">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="8d236-178">**`RunSettings`** arguments</span><span class="sxs-lookup"><span data-stu-id="8d236-178">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="8d236-179">Inline `RunSettings` sont passés comme derniers arguments sur la ligne de commande après « -- » (Notez l’espace après--).</span><span class="sxs-lookup"><span data-stu-id="8d236-179">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="8d236-180">Inline `RunSettings` sont spécifiés en tant que `[name]=[value]` paires.</span><span class="sxs-lookup"><span data-stu-id="8d236-180">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="8d236-181">Un espace est utilisé pour séparer plusieurs paires `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="8d236-181">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="8d236-182">Exemple : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="8d236-182">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="8d236-183">Pour plus d’informations, consultez [transmission d’arguments RunSettings via la ligne de commande](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="8d236-183">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="8d236-184">Exemples</span><span class="sxs-lookup"><span data-stu-id="8d236-184">Examples</span></span>

- <span data-ttu-id="8d236-185">Exécutez les tests du projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="8d236-185">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="8d236-186">Exécuter les tests dans le projet `test1` :</span><span class="sxs-lookup"><span data-stu-id="8d236-186">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="8d236-187">Exécutez les tests dans le projet dans le répertoire actif et générez un fichier de résultats de test au format trx :</span><span class="sxs-lookup"><span data-stu-id="8d236-187">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="8d236-188">Exécutez les tests dans le projet dans le répertoire actif, puis consignez des commentaires détaillés sur la console :</span><span class="sxs-lookup"><span data-stu-id="8d236-188">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - <span data-ttu-id="8d236-189">Exécutez les tests dans le projet dans le répertoire actif et testez les tests qui étaient en cours lorsque l’hôte de test s’est arrêté :</span><span class="sxs-lookup"><span data-stu-id="8d236-189">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="8d236-190">Détails de l’option de filtre</span><span class="sxs-lookup"><span data-stu-id="8d236-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="8d236-191">`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="8d236-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="8d236-192">`<property>` est un attribut de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="8d236-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="8d236-193">Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :</span><span class="sxs-lookup"><span data-stu-id="8d236-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="8d236-194">Framework de test</span><span class="sxs-lookup"><span data-stu-id="8d236-194">Test Framework</span></span> | <span data-ttu-id="8d236-195">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="8d236-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="8d236-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="8d236-196">MSTest</span></span>         | <ul><li><span data-ttu-id="8d236-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="8d236-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="8d236-198">Nom</span><span class="sxs-lookup"><span data-stu-id="8d236-198">Name</span></span></li><li><span data-ttu-id="8d236-199">ClassName</span><span class="sxs-lookup"><span data-stu-id="8d236-199">ClassName</span></span></li><li><span data-ttu-id="8d236-200">Priority</span><span class="sxs-lookup"><span data-stu-id="8d236-200">Priority</span></span></li><li><span data-ttu-id="8d236-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="8d236-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="8d236-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="8d236-202">xUnit</span></span>          | <ul><li><span data-ttu-id="8d236-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="8d236-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="8d236-204">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8d236-204">DisplayName</span></span></li><li><span data-ttu-id="8d236-205">Caractéristiques</span><span class="sxs-lookup"><span data-stu-id="8d236-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="8d236-206">La section `<operator>` décrit la relation entre la propriété et la valeur :</span><span class="sxs-lookup"><span data-stu-id="8d236-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="8d236-207">Opérateur</span><span class="sxs-lookup"><span data-stu-id="8d236-207">Operator</span></span> | <span data-ttu-id="8d236-208">Fonction</span><span class="sxs-lookup"><span data-stu-id="8d236-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="8d236-209">Concordance exacte</span><span class="sxs-lookup"><span data-stu-id="8d236-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="8d236-210">Pas de correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="8d236-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="8d236-211">Contient</span><span class="sxs-lookup"><span data-stu-id="8d236-211">Contains</span></span>        |
| `!~`     | <span data-ttu-id="8d236-212">Ne contient pas</span><span class="sxs-lookup"><span data-stu-id="8d236-212">Not contains</span></span>    |

<span data-ttu-id="8d236-213">`<value>` est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="8d236-213">`<value>` is a string.</span></span> <span data-ttu-id="8d236-214">Toutes les recherches respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="8d236-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="8d236-215">Une expression sans `<operator>` est automatiquement considérée comme `contains` sur la propriété `FullyQualifiedName` (par exemple, `dotnet test --filter xyz` est identique à `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="8d236-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="8d236-216">Les expressions peuvent être associées à des opérateurs conditionnels :</span><span class="sxs-lookup"><span data-stu-id="8d236-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="8d236-217">Opérateur</span><span class="sxs-lookup"><span data-stu-id="8d236-217">Operator</span></span>            | <span data-ttu-id="8d236-218">Fonction</span><span class="sxs-lookup"><span data-stu-id="8d236-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="8d236-219">OR</span><span class="sxs-lookup"><span data-stu-id="8d236-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="8d236-220">AND</span><span class="sxs-lookup"><span data-stu-id="8d236-220">AND</span></span>      |

<span data-ttu-id="8d236-221">Vous pouvez mettre des expressions entre parenthèses quand vous utilisez des opérateurs conditionnels (par exemple, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="8d236-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="8d236-222">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="8d236-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d236-223">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d236-223">See also</span></span>

- [<span data-ttu-id="8d236-224">Infrastructures et cibles</span><span class="sxs-lookup"><span data-stu-id="8d236-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="8d236-225">Catalogue d’identificateurs de runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="8d236-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="8d236-226">Passage d’arguments RunSettings via la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="8d236-226">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
