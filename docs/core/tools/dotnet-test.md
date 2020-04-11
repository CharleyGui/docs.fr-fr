---
title: Commande dotnet test
description: La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné.
ms.date: 02/27/2020
ms.openlocfilehash: 359e4522b26e2b59092d55eea3fca575d2afaf1f
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121041"
---
# <a name="dotnet-test"></a><span data-ttu-id="ebea0-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="ebea0-103">dotnet test</span></span>

<span data-ttu-id="ebea0-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="ebea0-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ebea0-105">Nom</span><span class="sxs-lookup"><span data-stu-id="ebea0-105">Name</span></span>

<span data-ttu-id="ebea0-106">`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="ebea0-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ebea0-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ebea0-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path] [--blame] [-c|--configuration]
    [--collect] [-d|--diag] [-f|--framework] [--filter]
    [--interactive] [-l|--logger] [--no-build] [--nologo]
    [--no-restore] [-o|--output] [-r|--results-directory]
    [--runtime] [-s|--settings] [-t|--list-tests]
    [-v|--verbosity] [[--] <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="ebea0-108">Description</span><span class="sxs-lookup"><span data-stu-id="ebea0-108">Description</span></span>

<span data-ttu-id="ebea0-109">La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné.</span><span class="sxs-lookup"><span data-stu-id="ebea0-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="ebea0-110">La commande `dotnet test` lance l’application console Test Runner spécifiée pour un projet.</span><span class="sxs-lookup"><span data-stu-id="ebea0-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="ebea0-111">Test Runner exécute les tests définis pour un framework de tests unitaires (par exemple, MSTest, NUnit ou xUnit) et signale la réussite ou l’échec de chaque test.</span><span class="sxs-lookup"><span data-stu-id="ebea0-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="ebea0-112">Si tous les tests réussissent, l’exécuteur de tests retourne 0 en tant que code de sortie. Sinon, si un test échoue, il retourne 1.</span><span class="sxs-lookup"><span data-stu-id="ebea0-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="ebea0-113">Test Runner et la bibliothèque de tests unitaires sont empaquetés sous forme de packages NuGet et sont restaurés comme des dépendances ordinaires du projet.</span><span class="sxs-lookup"><span data-stu-id="ebea0-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="ebea0-114">Les projets de test spécifient l’application Test Runner à l’aide d’un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :</span><span class="sxs-lookup"><span data-stu-id="ebea0-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="ebea0-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="ebea0-115">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="ebea0-116">Chemin vers le projet d’essai ou la solution.</span><span class="sxs-lookup"><span data-stu-id="ebea0-116">Path to the test project or solution.</span></span> <span data-ttu-id="ebea0-117">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="ebea0-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="ebea0-118">Options</span><span class="sxs-lookup"><span data-stu-id="ebea0-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="ebea0-119">Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="ebea0-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="ebea0-120">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="ebea0-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="ebea0-121">Cette option est utile pour isoler les tests problématiques qui provoquent l’écrasement de l’hôte d’essai.</span><span class="sxs-lookup"><span data-stu-id="ebea0-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="ebea0-122">Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.</span><span class="sxs-lookup"><span data-stu-id="ebea0-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="ebea0-123">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="ebea0-123">Defines the build configuration.</span></span> <span data-ttu-id="ebea0-124">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="ebea0-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="ebea0-125">Active le collecteur de données pour la série de tests.</span><span class="sxs-lookup"><span data-stu-id="ebea0-125">Enables data collector for the test run.</span></span> <span data-ttu-id="ebea0-126">Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).</span><span class="sxs-lookup"><span data-stu-id="ebea0-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="ebea0-127">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="ebea0-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebea0-128">Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="ebea0-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="ebea0-129">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="ebea0-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ebea0-130">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="ebea0-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ebea0-131">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ebea0-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="ebea0-132">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="ebea0-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="ebea0-133">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ebea0-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="ebea0-134">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="ebea0-134">For example, to complete authentication.</span></span> <span data-ttu-id="ebea0-135">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ebea0-135">Available since .NET Core 3.0 SDK.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="ebea0-136">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="ebea0-136">Specifies a logger for test results.</span></span> <span data-ttu-id="ebea0-137">Contrairement à MSBuild, le test dotnet n’accepte `-l "console;v=d"` pas `-l "console;verbosity=detailed"`les abréviations : au lieu d’une utilisation.</span><span class="sxs-lookup"><span data-stu-id="ebea0-137">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="ebea0-138">Ne génère pas le projet de test avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="ebea0-138">Doesn't build the test project before running it.</span></span> <span data-ttu-id="ebea0-139">Il définit aussi implicitement le drapeau. `--no-restore`</span><span class="sxs-lookup"><span data-stu-id="ebea0-139">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="ebea0-140">Exécutez des tests sans afficher la bannière Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="ebea0-140">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="ebea0-141">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ebea0-141">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ebea0-142">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="ebea0-142">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="ebea0-143">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ebea0-143">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="ebea0-144">Répertoire où les résultats de test doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="ebea0-144">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="ebea0-145">Si le répertoire spécifié n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="ebea0-145">If the specified directory doesn't exist, it's created.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="ebea0-146">Le temps d’exécution de la cible à tester.</span><span class="sxs-lookup"><span data-stu-id="ebea0-146">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="ebea0-147">Fichier `.runsettings` à utiliser pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="ebea0-147">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="ebea0-148">Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="ebea0-148">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="ebea0-149">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="ebea0-149">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="ebea0-150">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="ebea0-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ebea0-151">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ebea0-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ebea0-152">Par défaut, il s’agit de `minimal`.</span><span class="sxs-lookup"><span data-stu-id="ebea0-152">The default is `minimal`.</span></span> <span data-ttu-id="ebea0-153">Pour plus d’informations, consultez <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="ebea0-153">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="ebea0-154">`RunSettings`Arguments</span><span class="sxs-lookup"><span data-stu-id="ebea0-154">`RunSettings` arguments</span></span>

  <span data-ttu-id="ebea0-155">Les arguments `RunSettings` sont adoptés comme configurations pour le test.</span><span class="sxs-lookup"><span data-stu-id="ebea0-155">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="ebea0-156">Les arguments sont spécifiés en tant que paires `[name]=[value]` après "-- " (notez l’espace après --).</span><span class="sxs-lookup"><span data-stu-id="ebea0-156">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="ebea0-157">Un espace est utilisé pour séparer plusieurs paires `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="ebea0-157">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="ebea0-158">Exemple : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="ebea0-158">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="ebea0-159">Pour plus d’informations, voir [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="ebea0-159">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="ebea0-160">Exemples</span><span class="sxs-lookup"><span data-stu-id="ebea0-160">Examples</span></span>

- <span data-ttu-id="ebea0-161">Exécutez les tests du projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="ebea0-161">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="ebea0-162">Exécuter les tests dans le projet `test1` :</span><span class="sxs-lookup"><span data-stu-id="ebea0-162">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="ebea0-163">Exécutez les tests dans le projet dans l’annuaire actuel, et de générer un fichier de résultats de test dans le format trx:</span><span class="sxs-lookup"><span data-stu-id="ebea0-163">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="ebea0-164">Exécutez les tests dans le projet dans l’annuaire actuel, et connectez-vous avec la verbosité détaillée à la console:</span><span class="sxs-lookup"><span data-stu-id="ebea0-164">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="ebea0-165">Détails de l’option de filtre</span><span class="sxs-lookup"><span data-stu-id="ebea0-165">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ebea0-166">`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="ebea0-166">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="ebea0-167">`<property>` est un attribut de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="ebea0-167">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="ebea0-168">Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :</span><span class="sxs-lookup"><span data-stu-id="ebea0-168">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="ebea0-169">Framework de test</span><span class="sxs-lookup"><span data-stu-id="ebea0-169">Test Framework</span></span> | <span data-ttu-id="ebea0-170">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="ebea0-170">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ebea0-171">MSTest</span><span class="sxs-lookup"><span data-stu-id="ebea0-171">MSTest</span></span>         | <ul><li><span data-ttu-id="ebea0-172">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ebea0-172">FullyQualifiedName</span></span></li><li><span data-ttu-id="ebea0-173">Nom</span><span class="sxs-lookup"><span data-stu-id="ebea0-173">Name</span></span></li><li><span data-ttu-id="ebea0-174">ClassName</span><span class="sxs-lookup"><span data-stu-id="ebea0-174">ClassName</span></span></li><li><span data-ttu-id="ebea0-175">Priority</span><span class="sxs-lookup"><span data-stu-id="ebea0-175">Priority</span></span></li><li><span data-ttu-id="ebea0-176">TestCategory</span><span class="sxs-lookup"><span data-stu-id="ebea0-176">TestCategory</span></span></li></ul> |
| <span data-ttu-id="ebea0-177">xUnit</span><span class="sxs-lookup"><span data-stu-id="ebea0-177">xUnit</span></span>          | <ul><li><span data-ttu-id="ebea0-178">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ebea0-178">FullyQualifiedName</span></span></li><li><span data-ttu-id="ebea0-179">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ebea0-179">DisplayName</span></span></li><li><span data-ttu-id="ebea0-180">Caractéristiques</span><span class="sxs-lookup"><span data-stu-id="ebea0-180">Traits</span></span></li></ul>                                   |

<span data-ttu-id="ebea0-181">La section `<operator>` décrit la relation entre la propriété et la valeur :</span><span class="sxs-lookup"><span data-stu-id="ebea0-181">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="ebea0-182">Opérateur</span><span class="sxs-lookup"><span data-stu-id="ebea0-182">Operator</span></span> | <span data-ttu-id="ebea0-183">Fonction</span><span class="sxs-lookup"><span data-stu-id="ebea0-183">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="ebea0-184">Concordance exacte</span><span class="sxs-lookup"><span data-stu-id="ebea0-184">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="ebea0-185">Pas de correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="ebea0-185">Not exact match</span></span> |
| `~`      | <span data-ttu-id="ebea0-186">Contient</span><span class="sxs-lookup"><span data-stu-id="ebea0-186">Contains</span></span>        |
| `!~`     | <span data-ttu-id="ebea0-187">Ne contient pas</span><span class="sxs-lookup"><span data-stu-id="ebea0-187">Not contains</span></span>    |

<span data-ttu-id="ebea0-188">`<value>` est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ebea0-188">`<value>` is a string.</span></span> <span data-ttu-id="ebea0-189">Toutes les recherches respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="ebea0-189">All the lookups are case insensitive.</span></span>

<span data-ttu-id="ebea0-190">Une expression sans `<operator>` est automatiquement considérée comme `contains` sur la propriété `FullyQualifiedName` (par exemple, `dotnet test --filter xyz` est identique à `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="ebea0-190">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="ebea0-191">Les expressions peuvent être associées à des opérateurs conditionnels :</span><span class="sxs-lookup"><span data-stu-id="ebea0-191">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="ebea0-192">Opérateur</span><span class="sxs-lookup"><span data-stu-id="ebea0-192">Operator</span></span>            | <span data-ttu-id="ebea0-193">Fonction</span><span class="sxs-lookup"><span data-stu-id="ebea0-193">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="ebea0-194">OR</span><span class="sxs-lookup"><span data-stu-id="ebea0-194">OR</span></span>       |
| `&`                 | <span data-ttu-id="ebea0-195">AND</span><span class="sxs-lookup"><span data-stu-id="ebea0-195">AND</span></span>      |

<span data-ttu-id="ebea0-196">Vous pouvez mettre des expressions entre parenthèses quand vous utilisez des opérateurs conditionnels (par exemple, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="ebea0-196">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="ebea0-197">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ebea0-197">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ebea0-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebea0-198">See also</span></span>

- [<span data-ttu-id="ebea0-199">Infrastructures et cibles</span><span class="sxs-lookup"><span data-stu-id="ebea0-199">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="ebea0-200">Catalogue d’identificateurs de runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="ebea0-200">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="ebea0-201">Passing runsettings arguments à travers la ligne de commandement</span><span class="sxs-lookup"><span data-stu-id="ebea0-201">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
