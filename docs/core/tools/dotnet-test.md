---
title: Commande dotnet test
description: La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné.
ms.date: 04/29/2020
ms.openlocfilehash: a8218b6596601069b89a60ad018adf89a1f47cf6
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624889"
---
# <a name="dotnet-test"></a><span data-ttu-id="5a0f4-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5a0f4-103">dotnet test</span></span>

<span data-ttu-id="5a0f4-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="5a0f4-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5a0f4-105">Nom</span><span class="sxs-lookup"><span data-stu-id="5a0f4-105">Name</span></span>

<span data-ttu-id="5a0f4-106">`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5a0f4-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="5a0f4-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
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

## <a name="description"></a><span data-ttu-id="5a0f4-108">Description</span><span class="sxs-lookup"><span data-stu-id="5a0f4-108">Description</span></span>

<span data-ttu-id="5a0f4-109">La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="5a0f4-110">La commande `dotnet test` lance l’application console Test Runner spécifiée pour un projet.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="5a0f4-111">Test Runner exécute les tests définis pour un framework de tests unitaires (par exemple, MSTest, NUnit ou xUnit) et signale la réussite ou l’échec de chaque test.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="5a0f4-112">Si tous les tests réussissent, l’exécuteur de tests retourne 0 en tant que code de sortie. Sinon, si un test échoue, il retourne 1.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="5a0f4-113">Pour les projets multi-ciblés, les tests sont exécutés pour chaque Framework ciblé.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="5a0f4-114">Test Runner et la bibliothèque de tests unitaires sont empaquetés sous forme de packages NuGet et sont restaurés comme des dépendances ordinaires du projet.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="5a0f4-115">Les projets de test spécifient l’application Test Runner à l’aide d’un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :</span><span class="sxs-lookup"><span data-stu-id="5a0f4-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="5a0f4-116">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="5a0f4-116">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="5a0f4-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="5a0f4-117">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="5a0f4-118">Chemin d’accès au projet de test ou à la solution.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-118">Path to the test project or solution.</span></span> <span data-ttu-id="5a0f4-119">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="5a0f4-120">Options</span><span class="sxs-lookup"><span data-stu-id="5a0f4-120">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="5a0f4-121">Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-121">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="5a0f4-122">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="5a0f4-123">Cette option est utile pour isoler les tests problématiques qui provoquent le blocage de l’hôte de test.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-123">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="5a0f4-124">Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="5a0f4-125">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-125">Defines the build configuration.</span></span> <span data-ttu-id="5a0f4-126">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="5a0f4-127">Active le collecteur de données pour la série de tests.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-127">Enables data collector for the test run.</span></span> <span data-ttu-id="5a0f4-128">Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).</span><span class="sxs-lookup"><span data-stu-id="5a0f4-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="5a0f4-129">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-129">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5a0f4-130">Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="5a0f4-131">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="5a0f4-132">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="5a0f4-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="5a0f4-133">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="5a0f4-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="5a0f4-134">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="5a0f4-135">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-135">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="5a0f4-136">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-136">For example, to complete authentication.</span></span> <span data-ttu-id="5a0f4-137">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="5a0f4-138">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-138">Specifies a logger for test results.</span></span> <span data-ttu-id="5a0f4-139">Contrairement à MSBuild, dotnet test n’accepte pas les abréviations `-l "console;v=d"` : `-l "console;verbosity=detailed"`au lieu d’utiliser.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-139">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="5a0f4-140">Ne génère pas le projet de test avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-140">Doesn't build the test project before running it.</span></span> <span data-ttu-id="5a0f4-141">Il définit également implicitement l’indicateur `--no-restore` -.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-141">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="5a0f4-142">Exécuter les tests sans afficher la bannière Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-142">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="5a0f4-143">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="5a0f4-144">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="5a0f4-145">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-145">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="5a0f4-146">S’il n’est pas spécifié, le chemin d'accès par défaut est `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-146">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="5a0f4-147">Pour les projets avec plusieurs frameworks cibles (via `TargetFrameworks` la propriété), vous devez également définir `--framework` lorsque vous spécifiez cette option.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-147">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="5a0f4-148">`dotnet test`Exécutez toujours les tests à partir du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-148">`dotnet test` always run tests from the output directory.</span></span> <span data-ttu-id="5a0f4-149">Vous pouvez utiliser <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> pour consommer des ressources de test dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-149">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="5a0f4-150">Répertoire où les résultats de test doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-150">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="5a0f4-151">Si le répertoire spécifié n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-151">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="5a0f4-152">La valeur par `TestResults` défaut se trouve dans le répertoire qui contient le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-152">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="5a0f4-153">Runtime cible à tester.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-153">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="5a0f4-154">Fichier `.runsettings` à utiliser pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-154">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="5a0f4-155">Notez que l' `TargetPlatform` élément (x86 | x64) n’a aucun effet `dotnet test`pour.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-155">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="5a0f4-156">Pour exécuter des tests ciblant x86, installez la version x86 de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-156">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="5a0f4-157">Le nombre de bits de *dotnet. exe* qui se trouve sur le chemin d’accès correspond à ce qui sera utilisé pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-157">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="5a0f4-158">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="5a0f4-158">for more information, see the following resources:</span></span>

  - [<span data-ttu-id="5a0f4-159">Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-159">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="5a0f4-160">Configurer une série de tests</span><span class="sxs-lookup"><span data-stu-id="5a0f4-160">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="5a0f4-161">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-161">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5a0f4-162">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5a0f4-163">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5a0f4-164">Par défaut, il s’agit de `minimal`.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-164">The default is `minimal`.</span></span> <span data-ttu-id="5a0f4-165">Pour plus d’informations, consultez <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-165">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="5a0f4-166">**`RunSettings`** arguments</span><span class="sxs-lookup"><span data-stu-id="5a0f4-166">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="5a0f4-167">Les arguments sont passés `RunSettings` comme configurations pour le test.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-167">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="5a0f4-168">Les arguments sont spécifiés en tant que paires `[name]=[value]` après "-- " (notez l’espace après --).</span><span class="sxs-lookup"><span data-stu-id="5a0f4-168">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="5a0f4-169">Un espace est utilisé pour séparer plusieurs paires `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-169">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="5a0f4-170">Exemple : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="5a0f4-170">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="5a0f4-171">Pour plus d’informations, consultez [transmission d’arguments RunSettings via la ligne de commande](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="5a0f4-171">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="5a0f4-172">Exemples</span><span class="sxs-lookup"><span data-stu-id="5a0f4-172">Examples</span></span>

- <span data-ttu-id="5a0f4-173">Exécutez les tests du projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="5a0f4-173">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="5a0f4-174">Exécuter les tests dans le projet `test1` :</span><span class="sxs-lookup"><span data-stu-id="5a0f4-174">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="5a0f4-175">Exécutez les tests dans le projet dans le répertoire actif et générez un fichier de résultats de test au format trx :</span><span class="sxs-lookup"><span data-stu-id="5a0f4-175">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="5a0f4-176">Exécutez les tests dans le projet dans le répertoire actif, puis consignez des commentaires détaillés sur la console :</span><span class="sxs-lookup"><span data-stu-id="5a0f4-176">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="5a0f4-177">Détails de l’option de filtre</span><span class="sxs-lookup"><span data-stu-id="5a0f4-177">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="5a0f4-178">`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-178">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="5a0f4-179">`<property>` est un attribut de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-179">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="5a0f4-180">Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :</span><span class="sxs-lookup"><span data-stu-id="5a0f4-180">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="5a0f4-181">Framework de test</span><span class="sxs-lookup"><span data-stu-id="5a0f4-181">Test Framework</span></span> | <span data-ttu-id="5a0f4-182">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="5a0f4-182">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="5a0f4-183">MSTest</span><span class="sxs-lookup"><span data-stu-id="5a0f4-183">MSTest</span></span>         | <ul><li><span data-ttu-id="5a0f4-184">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="5a0f4-184">FullyQualifiedName</span></span></li><li><span data-ttu-id="5a0f4-185">Nom</span><span class="sxs-lookup"><span data-stu-id="5a0f4-185">Name</span></span></li><li><span data-ttu-id="5a0f4-186">ClassName</span><span class="sxs-lookup"><span data-stu-id="5a0f4-186">ClassName</span></span></li><li><span data-ttu-id="5a0f4-187">Priority</span><span class="sxs-lookup"><span data-stu-id="5a0f4-187">Priority</span></span></li><li><span data-ttu-id="5a0f4-188">TestCategory</span><span class="sxs-lookup"><span data-stu-id="5a0f4-188">TestCategory</span></span></li></ul> |
| <span data-ttu-id="5a0f4-189">xUnit</span><span class="sxs-lookup"><span data-stu-id="5a0f4-189">xUnit</span></span>          | <ul><li><span data-ttu-id="5a0f4-190">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="5a0f4-190">FullyQualifiedName</span></span></li><li><span data-ttu-id="5a0f4-191">DisplayName</span><span class="sxs-lookup"><span data-stu-id="5a0f4-191">DisplayName</span></span></li><li><span data-ttu-id="5a0f4-192">Caractéristiques</span><span class="sxs-lookup"><span data-stu-id="5a0f4-192">Traits</span></span></li></ul>                                   |

<span data-ttu-id="5a0f4-193">La section `<operator>` décrit la relation entre la propriété et la valeur :</span><span class="sxs-lookup"><span data-stu-id="5a0f4-193">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="5a0f4-194">Opérateur</span><span class="sxs-lookup"><span data-stu-id="5a0f4-194">Operator</span></span> | <span data-ttu-id="5a0f4-195">Fonction</span><span class="sxs-lookup"><span data-stu-id="5a0f4-195">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="5a0f4-196">Concordance exacte</span><span class="sxs-lookup"><span data-stu-id="5a0f4-196">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="5a0f4-197">Pas de correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="5a0f4-197">Not exact match</span></span> |
| `~`      | <span data-ttu-id="5a0f4-198">Contient</span><span class="sxs-lookup"><span data-stu-id="5a0f4-198">Contains</span></span>        |
| `!~`     | <span data-ttu-id="5a0f4-199">Ne contient pas</span><span class="sxs-lookup"><span data-stu-id="5a0f4-199">Not contains</span></span>    |

<span data-ttu-id="5a0f4-200">`<value>` est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-200">`<value>` is a string.</span></span> <span data-ttu-id="5a0f4-201">Toutes les recherches respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="5a0f4-201">All the lookups are case insensitive.</span></span>

<span data-ttu-id="5a0f4-202">Une expression sans `<operator>` est automatiquement considérée comme `contains` sur la propriété `FullyQualifiedName` (par exemple, `dotnet test --filter xyz` est identique à `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="5a0f4-202">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="5a0f4-203">Les expressions peuvent être associées à des opérateurs conditionnels :</span><span class="sxs-lookup"><span data-stu-id="5a0f4-203">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="5a0f4-204">Opérateur</span><span class="sxs-lookup"><span data-stu-id="5a0f4-204">Operator</span></span>            | <span data-ttu-id="5a0f4-205">Fonction</span><span class="sxs-lookup"><span data-stu-id="5a0f4-205">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="5a0f4-206">OR</span><span class="sxs-lookup"><span data-stu-id="5a0f4-206">OR</span></span>       |
| `&`                 | <span data-ttu-id="5a0f4-207">AND</span><span class="sxs-lookup"><span data-stu-id="5a0f4-207">AND</span></span>      |

<span data-ttu-id="5a0f4-208">Vous pouvez mettre des expressions entre parenthèses quand vous utilisez des opérateurs conditionnels (par exemple, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="5a0f4-208">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="5a0f4-209">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="5a0f4-209">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5a0f4-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a0f4-210">See also</span></span>

- [<span data-ttu-id="5a0f4-211">Infrastructures et cibles</span><span class="sxs-lookup"><span data-stu-id="5a0f4-211">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="5a0f4-212">Catalogue d’identificateurs de runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="5a0f4-212">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="5a0f4-213">Passage d’arguments RunSettings via la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="5a0f4-213">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
