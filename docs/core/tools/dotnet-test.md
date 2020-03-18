---
title: Commande dotnet test
description: La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné.
ms.date: 02/27/2020
ms.openlocfilehash: bac2f0e613c34bc9f657551a5eac4038207a93ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847896"
---
# <a name="dotnet-test"></a><span data-ttu-id="e1673-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="e1673-103">dotnet test</span></span>

<span data-ttu-id="e1673-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="e1673-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e1673-105">Nom</span><span class="sxs-lookup"><span data-stu-id="e1673-105">Name</span></span>

<span data-ttu-id="e1673-106">`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="e1673-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e1673-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="e1673-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="e1673-108">Description</span><span class="sxs-lookup"><span data-stu-id="e1673-108">Description</span></span>

<span data-ttu-id="e1673-109">La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné.</span><span class="sxs-lookup"><span data-stu-id="e1673-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="e1673-110">La commande `dotnet test` lance l’application console Test Runner spécifiée pour un projet.</span><span class="sxs-lookup"><span data-stu-id="e1673-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="e1673-111">Test Runner exécute les tests définis pour un framework de tests unitaires (par exemple, MSTest, NUnit ou xUnit) et signale la réussite ou l’échec de chaque test.</span><span class="sxs-lookup"><span data-stu-id="e1673-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="e1673-112">Si tous les tests réussissent, l’exécuteur de tests retourne 0 en tant que code de sortie. Sinon, si un test échoue, il retourne 1.</span><span class="sxs-lookup"><span data-stu-id="e1673-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="e1673-113">Test Runner et la bibliothèque de tests unitaires sont empaquetés sous forme de packages NuGet et sont restaurés comme des dépendances ordinaires du projet.</span><span class="sxs-lookup"><span data-stu-id="e1673-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="e1673-114">Les projets de test spécifient l’application Test Runner à l’aide d’un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :</span><span class="sxs-lookup"><span data-stu-id="e1673-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="e1673-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="e1673-115">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="e1673-116">Chemin vers le projet d’essai ou la solution.</span><span class="sxs-lookup"><span data-stu-id="e1673-116">Path to the test project or solution.</span></span> <span data-ttu-id="e1673-117">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="e1673-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="e1673-118">Options</span><span class="sxs-lookup"><span data-stu-id="e1673-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="e1673-119">Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="e1673-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="e1673-120">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="e1673-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="e1673-121">Cette option est utile pour isoler les tests problématiques qui provoquent l’écrasement de l’hôte d’essai.</span><span class="sxs-lookup"><span data-stu-id="e1673-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="e1673-122">Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.</span><span class="sxs-lookup"><span data-stu-id="e1673-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="e1673-123">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="e1673-123">Defines the build configuration.</span></span> <span data-ttu-id="e1673-124">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="e1673-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="e1673-125">Active le collecteur de données pour la série de tests.</span><span class="sxs-lookup"><span data-stu-id="e1673-125">Enables data collector for the test run.</span></span> <span data-ttu-id="e1673-126">Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).</span><span class="sxs-lookup"><span data-stu-id="e1673-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="e1673-127">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="e1673-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e1673-128">Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="e1673-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="e1673-129">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="e1673-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="e1673-130">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="e1673-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="e1673-131">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e1673-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="e1673-132">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="e1673-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="e1673-133">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e1673-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="e1673-134">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="e1673-134">For example, to complete authentication.</span></span> <span data-ttu-id="e1673-135">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e1673-135">Available since .NET Core 3.0 SDK.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="e1673-136">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="e1673-136">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="e1673-137">Ne génère pas le projet de test avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="e1673-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="e1673-138">Il définit aussi implicitement le drapeau. `--no-restore`</span><span class="sxs-lookup"><span data-stu-id="e1673-138">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="e1673-139">Exécutez des tests sans afficher la bannière Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="e1673-139">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="e1673-140">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e1673-140">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e1673-141">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="e1673-141">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e1673-142">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="e1673-142">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="e1673-143">Répertoire où les résultats de test doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="e1673-143">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="e1673-144">Si le répertoire spécifié n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="e1673-144">If the specified directory doesn't exist, it's created.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="e1673-145">Le temps d’exécution de la cible à tester.</span><span class="sxs-lookup"><span data-stu-id="e1673-145">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="e1673-146">Fichier `.runsettings` à utiliser pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="e1673-146">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="e1673-147">Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="e1673-147">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="e1673-148">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="e1673-148">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e1673-149">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="e1673-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e1673-150">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e1673-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="e1673-151">`RunSettings`Arguments</span><span class="sxs-lookup"><span data-stu-id="e1673-151">`RunSettings` arguments</span></span>

  <span data-ttu-id="e1673-152">Les arguments `RunSettings` sont adoptés comme configurations pour le test.</span><span class="sxs-lookup"><span data-stu-id="e1673-152">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="e1673-153">Les arguments sont spécifiés en tant que paires `[name]=[value]` après "-- " (notez l’espace après --).</span><span class="sxs-lookup"><span data-stu-id="e1673-153">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="e1673-154">Un espace est utilisé pour séparer plusieurs paires `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="e1673-154">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="e1673-155">Exemple : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="e1673-155">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="e1673-156">Pour plus d’informations, voir [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="e1673-156">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="e1673-157">Exemples</span><span class="sxs-lookup"><span data-stu-id="e1673-157">Examples</span></span>

- <span data-ttu-id="e1673-158">Exécutez les tests du projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="e1673-158">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="e1673-159">Exécuter les tests dans le projet `test1` :</span><span class="sxs-lookup"><span data-stu-id="e1673-159">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="e1673-160">Exécutez les tests du projet dans le répertoire actif et générez un fichier de résultats des tests au format trx :</span><span class="sxs-lookup"><span data-stu-id="e1673-160">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="e1673-161">Détails de l’option de filtre</span><span class="sxs-lookup"><span data-stu-id="e1673-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="e1673-162">`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="e1673-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="e1673-163">`<property>` est un attribut de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="e1673-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="e1673-164">Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :</span><span class="sxs-lookup"><span data-stu-id="e1673-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="e1673-165">Framework de test</span><span class="sxs-lookup"><span data-stu-id="e1673-165">Test Framework</span></span> | <span data-ttu-id="e1673-166">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="e1673-166">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e1673-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="e1673-167">MSTest</span></span>         | <ul><li><span data-ttu-id="e1673-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="e1673-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="e1673-169">Nom</span><span class="sxs-lookup"><span data-stu-id="e1673-169">Name</span></span></li><li><span data-ttu-id="e1673-170">ClassName</span><span class="sxs-lookup"><span data-stu-id="e1673-170">ClassName</span></span></li><li><span data-ttu-id="e1673-171">Priority</span><span class="sxs-lookup"><span data-stu-id="e1673-171">Priority</span></span></li><li><span data-ttu-id="e1673-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="e1673-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="e1673-173">xUnit</span><span class="sxs-lookup"><span data-stu-id="e1673-173">xUnit</span></span>          | <ul><li><span data-ttu-id="e1673-174">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="e1673-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="e1673-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e1673-175">DisplayName</span></span></li><li><span data-ttu-id="e1673-176">Caractéristiques</span><span class="sxs-lookup"><span data-stu-id="e1673-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="e1673-177">La section `<operator>` décrit la relation entre la propriété et la valeur :</span><span class="sxs-lookup"><span data-stu-id="e1673-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="e1673-178">Opérateur</span><span class="sxs-lookup"><span data-stu-id="e1673-178">Operator</span></span> | <span data-ttu-id="e1673-179">Fonction</span><span class="sxs-lookup"><span data-stu-id="e1673-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="e1673-180">Concordance exacte</span><span class="sxs-lookup"><span data-stu-id="e1673-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="e1673-181">Pas de correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="e1673-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="e1673-182">Contient</span><span class="sxs-lookup"><span data-stu-id="e1673-182">Contains</span></span>        |
| `!~`     | <span data-ttu-id="e1673-183">Ne contient pas</span><span class="sxs-lookup"><span data-stu-id="e1673-183">Not contains</span></span>    |

<span data-ttu-id="e1673-184">`<value>` est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e1673-184">`<value>` is a string.</span></span> <span data-ttu-id="e1673-185">Toutes les recherches respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="e1673-185">All the lookups are case insensitive.</span></span>

<span data-ttu-id="e1673-186">Une expression sans `<operator>` est automatiquement considérée comme `contains` sur la propriété `FullyQualifiedName` (par exemple, `dotnet test --filter xyz` est identique à `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="e1673-186">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="e1673-187">Les expressions peuvent être associées à des opérateurs conditionnels :</span><span class="sxs-lookup"><span data-stu-id="e1673-187">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="e1673-188">Opérateur</span><span class="sxs-lookup"><span data-stu-id="e1673-188">Operator</span></span>            | <span data-ttu-id="e1673-189">Fonction</span><span class="sxs-lookup"><span data-stu-id="e1673-189">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="e1673-190">OR</span><span class="sxs-lookup"><span data-stu-id="e1673-190">OR</span></span>       |
| `&`                 | <span data-ttu-id="e1673-191">AND</span><span class="sxs-lookup"><span data-stu-id="e1673-191">AND</span></span>      |

<span data-ttu-id="e1673-192">Vous pouvez mettre des expressions entre parenthèses quand vous utilisez des opérateurs conditionnels (par exemple, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="e1673-192">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="e1673-193">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e1673-193">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1673-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1673-194">See also</span></span>

- [<span data-ttu-id="e1673-195">Infrastructures et cibles</span><span class="sxs-lookup"><span data-stu-id="e1673-195">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="e1673-196">Catalogue d’identificateurs de runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="e1673-196">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
