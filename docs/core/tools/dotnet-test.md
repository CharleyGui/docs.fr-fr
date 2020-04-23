---
title: Commande dotnet test
description: La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné.
ms.date: 02/27/2020
ms.openlocfilehash: 69b8101f9b1052f4726dce8a86234da99f5dc89c
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102739"
---
# <a name="dotnet-test"></a><span data-ttu-id="1ffa6-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="1ffa6-103">dotnet test</span></span>

<span data-ttu-id="1ffa6-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="1ffa6-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1ffa6-105">Nom</span><span class="sxs-lookup"><span data-stu-id="1ffa6-105">Name</span></span>

<span data-ttu-id="1ffa6-106">`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1ffa6-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="1ffa6-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="1ffa6-108">Description</span><span class="sxs-lookup"><span data-stu-id="1ffa6-108">Description</span></span>

<span data-ttu-id="1ffa6-109">La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="1ffa6-110">La commande `dotnet test` lance l’application console Test Runner spécifiée pour un projet.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="1ffa6-111">Test Runner exécute les tests définis pour un framework de tests unitaires (par exemple, MSTest, NUnit ou xUnit) et signale la réussite ou l’échec de chaque test.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="1ffa6-112">Si tous les tests réussissent, l’exécuteur de tests retourne 0 en tant que code de sortie. Sinon, si un test échoue, il retourne 1.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="1ffa6-113">Test Runner et la bibliothèque de tests unitaires sont empaquetés sous forme de packages NuGet et sont restaurés comme des dépendances ordinaires du projet.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="1ffa6-114">Les projets de test spécifient l’application Test Runner à l’aide d’un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :</span><span class="sxs-lookup"><span data-stu-id="1ffa6-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="1ffa6-115">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="1ffa6-115">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="1ffa6-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="1ffa6-116">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="1ffa6-117">Chemin vers le projet d’essai ou la solution.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-117">Path to the test project or solution.</span></span> <span data-ttu-id="1ffa6-118">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="1ffa6-119">Options</span><span class="sxs-lookup"><span data-stu-id="1ffa6-119">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="1ffa6-120">Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-120">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="1ffa6-121">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-121">Runs the tests in blame mode.</span></span> <span data-ttu-id="1ffa6-122">Cette option est utile pour isoler les tests problématiques qui provoquent l’écrasement de l’hôte d’essai.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-122">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="1ffa6-123">Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-123">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="1ffa6-124">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-124">Defines the build configuration.</span></span> <span data-ttu-id="1ffa6-125">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-125">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="1ffa6-126">Active le collecteur de données pour la série de tests.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-126">Enables data collector for the test run.</span></span> <span data-ttu-id="1ffa6-127">Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).</span><span class="sxs-lookup"><span data-stu-id="1ffa6-127">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="1ffa6-128">Permet le mode de diagnostic pour la plate-forme de test et écrit des messages diagnostiques au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-128">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="1ffa6-129">Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-129">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="1ffa6-130">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-130">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="1ffa6-131">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="1ffa6-131">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="1ffa6-132">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="1ffa6-132">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="1ffa6-133">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-133">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="1ffa6-134">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-134">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="1ffa6-135">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-135">For example, to complete authentication.</span></span> <span data-ttu-id="1ffa6-136">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-136">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="1ffa6-137">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-137">Specifies a logger for test results.</span></span> <span data-ttu-id="1ffa6-138">Contrairement à MSBuild, le test dotnet n’accepte `-l "console;v=d"` pas `-l "console;verbosity=detailed"`les abréviations : au lieu d’une utilisation.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-138">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="1ffa6-139">Ne génère pas le projet de test avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-139">Doesn't build the test project before running it.</span></span> <span data-ttu-id="1ffa6-140">Il définit aussi implicitement le drapeau. `--no-restore`</span><span class="sxs-lookup"><span data-stu-id="1ffa6-140">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="1ffa6-141">Exécutez des tests sans afficher la bannière Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-141">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="1ffa6-142">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-142">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="1ffa6-143">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-143">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="1ffa6-144">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-144">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="1ffa6-145">S’il n’est pas spécifié, le chemin d'accès par défaut est `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-145">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="1ffa6-146">Pour les projets avec plusieurs `TargetFrameworks` cadres cibles (via `--framework` la propriété), vous devez également définir lorsque vous spécifiez cette option.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-146">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="1ffa6-147">Répertoire où les résultats de test doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-147">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="1ffa6-148">Si le répertoire spécifié n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-148">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="1ffa6-149">La valeur `TestResults` par défaut se trouve dans l’annuaire qui contient le fichier du projet.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-149">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="1ffa6-150">Le temps d’exécution de la cible à tester.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-150">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="1ffa6-151">Fichier `.runsettings` à utiliser pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-151">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="1ffa6-152">Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-152">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="1ffa6-153">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-153">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="1ffa6-154">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1ffa6-155">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="1ffa6-156">Par défaut, il s’agit de `minimal`.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-156">The default is `minimal`.</span></span> <span data-ttu-id="1ffa6-157">Pour plus d’informations, consultez <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-157">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="1ffa6-158">**`RunSettings`** Arguments</span><span class="sxs-lookup"><span data-stu-id="1ffa6-158">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="1ffa6-159">Les arguments `RunSettings` sont adoptés comme configurations pour le test.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-159">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="1ffa6-160">Les arguments sont spécifiés en tant que paires `[name]=[value]` après "-- " (notez l’espace après --).</span><span class="sxs-lookup"><span data-stu-id="1ffa6-160">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="1ffa6-161">Un espace est utilisé pour séparer plusieurs paires `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-161">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="1ffa6-162">Exemple : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="1ffa6-162">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="1ffa6-163">Pour plus d’informations, voir [Passing RunSettings arguments à travers la ligne de commande](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="1ffa6-163">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="1ffa6-164">Exemples</span><span class="sxs-lookup"><span data-stu-id="1ffa6-164">Examples</span></span>

- <span data-ttu-id="1ffa6-165">Exécutez les tests du projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="1ffa6-165">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="1ffa6-166">Exécuter les tests dans le projet `test1` :</span><span class="sxs-lookup"><span data-stu-id="1ffa6-166">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="1ffa6-167">Exécutez les tests dans le projet dans l’annuaire actuel, et de générer un fichier de résultats de test dans le format trx:</span><span class="sxs-lookup"><span data-stu-id="1ffa6-167">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="1ffa6-168">Exécutez les tests dans le projet dans l’annuaire actuel, et connectez-vous avec la verbosité détaillée à la console:</span><span class="sxs-lookup"><span data-stu-id="1ffa6-168">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="1ffa6-169">Détails de l’option de filtre</span><span class="sxs-lookup"><span data-stu-id="1ffa6-169">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="1ffa6-170">`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-170">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="1ffa6-171">`<property>` est un attribut de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-171">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="1ffa6-172">Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :</span><span class="sxs-lookup"><span data-stu-id="1ffa6-172">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="1ffa6-173">Framework de test</span><span class="sxs-lookup"><span data-stu-id="1ffa6-173">Test Framework</span></span> | <span data-ttu-id="1ffa6-174">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="1ffa6-174">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1ffa6-175">MSTest</span><span class="sxs-lookup"><span data-stu-id="1ffa6-175">MSTest</span></span>         | <ul><li><span data-ttu-id="1ffa6-176">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="1ffa6-176">FullyQualifiedName</span></span></li><li><span data-ttu-id="1ffa6-177">Nom</span><span class="sxs-lookup"><span data-stu-id="1ffa6-177">Name</span></span></li><li><span data-ttu-id="1ffa6-178">ClassName</span><span class="sxs-lookup"><span data-stu-id="1ffa6-178">ClassName</span></span></li><li><span data-ttu-id="1ffa6-179">Priority</span><span class="sxs-lookup"><span data-stu-id="1ffa6-179">Priority</span></span></li><li><span data-ttu-id="1ffa6-180">TestCategory</span><span class="sxs-lookup"><span data-stu-id="1ffa6-180">TestCategory</span></span></li></ul> |
| <span data-ttu-id="1ffa6-181">xUnit</span><span class="sxs-lookup"><span data-stu-id="1ffa6-181">xUnit</span></span>          | <ul><li><span data-ttu-id="1ffa6-182">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="1ffa6-182">FullyQualifiedName</span></span></li><li><span data-ttu-id="1ffa6-183">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1ffa6-183">DisplayName</span></span></li><li><span data-ttu-id="1ffa6-184">Caractéristiques</span><span class="sxs-lookup"><span data-stu-id="1ffa6-184">Traits</span></span></li></ul>                                   |

<span data-ttu-id="1ffa6-185">La section `<operator>` décrit la relation entre la propriété et la valeur :</span><span class="sxs-lookup"><span data-stu-id="1ffa6-185">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="1ffa6-186">Opérateur</span><span class="sxs-lookup"><span data-stu-id="1ffa6-186">Operator</span></span> | <span data-ttu-id="1ffa6-187">Fonction</span><span class="sxs-lookup"><span data-stu-id="1ffa6-187">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="1ffa6-188">Concordance exacte</span><span class="sxs-lookup"><span data-stu-id="1ffa6-188">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="1ffa6-189">Pas de correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="1ffa6-189">Not exact match</span></span> |
| `~`      | <span data-ttu-id="1ffa6-190">Contient</span><span class="sxs-lookup"><span data-stu-id="1ffa6-190">Contains</span></span>        |
| `!~`     | <span data-ttu-id="1ffa6-191">Ne contient pas</span><span class="sxs-lookup"><span data-stu-id="1ffa6-191">Not contains</span></span>    |

<span data-ttu-id="1ffa6-192">`<value>` est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-192">`<value>` is a string.</span></span> <span data-ttu-id="1ffa6-193">Toutes les recherches respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="1ffa6-193">All the lookups are case insensitive.</span></span>

<span data-ttu-id="1ffa6-194">Une expression sans `<operator>` est automatiquement considérée comme `contains` sur la propriété `FullyQualifiedName` (par exemple, `dotnet test --filter xyz` est identique à `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="1ffa6-194">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="1ffa6-195">Les expressions peuvent être associées à des opérateurs conditionnels :</span><span class="sxs-lookup"><span data-stu-id="1ffa6-195">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="1ffa6-196">Opérateur</span><span class="sxs-lookup"><span data-stu-id="1ffa6-196">Operator</span></span>            | <span data-ttu-id="1ffa6-197">Fonction</span><span class="sxs-lookup"><span data-stu-id="1ffa6-197">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="1ffa6-198">OR</span><span class="sxs-lookup"><span data-stu-id="1ffa6-198">OR</span></span>       |
| `&`                 | <span data-ttu-id="1ffa6-199">AND</span><span class="sxs-lookup"><span data-stu-id="1ffa6-199">AND</span></span>      |

<span data-ttu-id="1ffa6-200">Vous pouvez mettre des expressions entre parenthèses quand vous utilisez des opérateurs conditionnels (par exemple, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="1ffa6-200">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="1ffa6-201">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="1ffa6-201">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ffa6-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ffa6-202">See also</span></span>

- [<span data-ttu-id="1ffa6-203">Infrastructures et cibles</span><span class="sxs-lookup"><span data-stu-id="1ffa6-203">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="1ffa6-204">Catalogue d’identificateurs de runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="1ffa6-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="1ffa6-205">Passing runsettings arguments à travers la ligne de commandement</span><span class="sxs-lookup"><span data-stu-id="1ffa6-205">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
