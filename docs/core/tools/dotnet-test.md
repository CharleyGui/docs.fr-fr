---
title: Commande dotnet test
description: La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné.
ms.date: 05/29/2018
ms.openlocfilehash: 890d1fc3fd9d47f2bdcd63f2a25248c3edd705e4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626045"
---
# <a name="dotnet-test"></a><span data-ttu-id="f3354-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="f3354-103">dotnet test</span></span>

<span data-ttu-id="f3354-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="f3354-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f3354-105">Name</span><span class="sxs-lookup"><span data-stu-id="f3354-105">Name</span></span>

<span data-ttu-id="f3354-106">`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="f3354-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f3354-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="f3354-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame]
    [-c|--configuration] [--collect] [-d|--diag] [-f|--framework]
    [--filter] [-l|--logger] [--no-build] [--no-restore]
    [-o|--output] [-r|--results-directory] [-s|--settings]
    [-t|--list-tests] [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f3354-108">Description</span><span class="sxs-lookup"><span data-stu-id="f3354-108">Description</span></span>

<span data-ttu-id="f3354-109">La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné.</span><span class="sxs-lookup"><span data-stu-id="f3354-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="f3354-110">La commande `dotnet test` lance l’application console Test Runner spécifiée pour un projet.</span><span class="sxs-lookup"><span data-stu-id="f3354-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="f3354-111">Test Runner exécute les tests définis pour un framework de tests unitaires (par exemple, MSTest, NUnit ou xUnit) et signale la réussite ou l’échec de chaque test.</span><span class="sxs-lookup"><span data-stu-id="f3354-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="f3354-112">Si tous les tests réussissent, l’exécuteur de tests retourne 0 en tant que code de sortie. Sinon, si un test échoue, il retourne 1.</span><span class="sxs-lookup"><span data-stu-id="f3354-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="f3354-113">Test Runner et la bibliothèque de tests unitaires sont empaquetés sous forme de packages NuGet et sont restaurés comme des dépendances ordinaires du projet.</span><span class="sxs-lookup"><span data-stu-id="f3354-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="f3354-114">Les projets de test spécifient l’application Test Runner à l’aide d’un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :</span><span class="sxs-lookup"><span data-stu-id="f3354-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="f3354-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="f3354-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="f3354-116">Chemin du projet de test.</span><span class="sxs-lookup"><span data-stu-id="f3354-116">Path to the test project.</span></span> <span data-ttu-id="f3354-117">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="f3354-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="f3354-118">Options</span><span class="sxs-lookup"><span data-stu-id="f3354-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="f3354-119">Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="f3354-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="f3354-120">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="f3354-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="f3354-121">Cette option est utile pour isoler les tests problématiques qui provoquent le blocage de l’hôte de test.</span><span class="sxs-lookup"><span data-stu-id="f3354-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="f3354-122">Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.</span><span class="sxs-lookup"><span data-stu-id="f3354-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration {Debug|Release}`**

  <span data-ttu-id="f3354-123">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="f3354-123">Defines the build configuration.</span></span> <span data-ttu-id="f3354-124">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="f3354-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="f3354-125">Active le collecteur de données pour la série de tests.</span><span class="sxs-lookup"><span data-stu-id="f3354-125">Enables data collector for the test run.</span></span> <span data-ttu-id="f3354-126">Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).</span><span class="sxs-lookup"><span data-stu-id="f3354-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="f3354-127">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="f3354-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f3354-128">Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="f3354-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="f3354-129">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="f3354-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f3354-130">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="f3354-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f3354-131">Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f3354-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="f3354-132">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="f3354-132">Prints out a short help for the command.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="f3354-133">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="f3354-133">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="f3354-134">Ne génère pas le projet de test avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="f3354-134">Doesn't build the test project before running it.</span></span> <span data-ttu-id="f3354-135">Il définit également implicitement l’indicateur-`--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="f3354-135">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f3354-136">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="f3354-136">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f3354-137">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="f3354-137">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="f3354-138">Répertoire où les résultats de test doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="f3354-138">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="f3354-139">Si le répertoire spécifié n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="f3354-139">If the specified directory doesn't exist, it's created.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="f3354-140">Fichier `.runsettings` à utiliser pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="f3354-140">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="f3354-141">Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="f3354-141">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="f3354-142">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="f3354-142">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f3354-143">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="f3354-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f3354-144">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f3354-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="f3354-145">arguments `RunSettings`</span><span class="sxs-lookup"><span data-stu-id="f3354-145">`RunSettings` arguments</span></span>

  <span data-ttu-id="f3354-146">Les arguments sont passés en tant que `RunSettings` configurations pour le test.</span><span class="sxs-lookup"><span data-stu-id="f3354-146">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="f3354-147">Les arguments sont spécifiés en tant que paires `[name]=[value]` après "-- " (notez l’espace après --).</span><span class="sxs-lookup"><span data-stu-id="f3354-147">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="f3354-148">Un espace est utilisé pour séparer plusieurs paires `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="f3354-148">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="f3354-149">Exemple : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="f3354-149">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="f3354-150">Pour plus d’informations, consultez [VSTest. Console. exe : passage de RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="f3354-150">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="f3354-151">Exemples</span><span class="sxs-lookup"><span data-stu-id="f3354-151">Examples</span></span>

- <span data-ttu-id="f3354-152">Exécutez les tests du projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="f3354-152">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="f3354-153">Exécuter les tests dans le projet `test1` :</span><span class="sxs-lookup"><span data-stu-id="f3354-153">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="f3354-154">Exécutez les tests du projet dans le répertoire actif et générez un fichier de résultats des tests au format trx :</span><span class="sxs-lookup"><span data-stu-id="f3354-154">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="f3354-155">Détails de l’option de filtre</span><span class="sxs-lookup"><span data-stu-id="f3354-155">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f3354-156">`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="f3354-156">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="f3354-157">`<property>` est un attribut de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="f3354-157">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="f3354-158">Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :</span><span class="sxs-lookup"><span data-stu-id="f3354-158">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="f3354-159">Infrastructure de test</span><span class="sxs-lookup"><span data-stu-id="f3354-159">Test Framework</span></span> | <span data-ttu-id="f3354-160">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="f3354-160">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f3354-161">MSTest</span><span class="sxs-lookup"><span data-stu-id="f3354-161">MSTest</span></span>         | <ul><li><span data-ttu-id="f3354-162">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f3354-162">FullyQualifiedName</span></span></li><li><span data-ttu-id="f3354-163">Name</span><span class="sxs-lookup"><span data-stu-id="f3354-163">Name</span></span></li><li><span data-ttu-id="f3354-164">ClassName</span><span class="sxs-lookup"><span data-stu-id="f3354-164">ClassName</span></span></li><li><span data-ttu-id="f3354-165">Priority</span><span class="sxs-lookup"><span data-stu-id="f3354-165">Priority</span></span></li><li><span data-ttu-id="f3354-166">TestCategory</span><span class="sxs-lookup"><span data-stu-id="f3354-166">TestCategory</span></span></li></ul> |
| <span data-ttu-id="f3354-167">xUnit</span><span class="sxs-lookup"><span data-stu-id="f3354-167">xUnit</span></span>          | <ul><li><span data-ttu-id="f3354-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f3354-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="f3354-169">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f3354-169">DisplayName</span></span></li><li><span data-ttu-id="f3354-170">Caractéristiques</span><span class="sxs-lookup"><span data-stu-id="f3354-170">Traits</span></span></li></ul>                                   |

<span data-ttu-id="f3354-171">La section `<operator>` décrit la relation entre la propriété et la valeur :</span><span class="sxs-lookup"><span data-stu-id="f3354-171">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="f3354-172">Opérateur</span><span class="sxs-lookup"><span data-stu-id="f3354-172">Operator</span></span> | <span data-ttu-id="f3354-173">Fonction</span><span class="sxs-lookup"><span data-stu-id="f3354-173">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="f3354-174">Concordance exacte</span><span class="sxs-lookup"><span data-stu-id="f3354-174">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="f3354-175">Pas de correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="f3354-175">Not exact match</span></span> |
| `~`      | <span data-ttu-id="f3354-176">Contient</span><span class="sxs-lookup"><span data-stu-id="f3354-176">Contains</span></span>        |
| `!~`     | <span data-ttu-id="f3354-177">Ne contient pas</span><span class="sxs-lookup"><span data-stu-id="f3354-177">Not contains</span></span>    |

<span data-ttu-id="f3354-178">`<value>` est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="f3354-178">`<value>` is a string.</span></span> <span data-ttu-id="f3354-179">Toutes les recherches respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="f3354-179">All the lookups are case insensitive.</span></span>

<span data-ttu-id="f3354-180">Une expression sans `<operator>` est automatiquement considérée comme `contains` sur la propriété `FullyQualifiedName` (par exemple, `dotnet test --filter xyz` est identique à `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="f3354-180">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="f3354-181">Les expressions peuvent être associées à des opérateurs conditionnels :</span><span class="sxs-lookup"><span data-stu-id="f3354-181">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="f3354-182">Opérateur</span><span class="sxs-lookup"><span data-stu-id="f3354-182">Operator</span></span>            | <span data-ttu-id="f3354-183">Fonction</span><span class="sxs-lookup"><span data-stu-id="f3354-183">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="f3354-184">OR</span><span class="sxs-lookup"><span data-stu-id="f3354-184">OR</span></span>       |
| `&`                 | <span data-ttu-id="f3354-185">AND</span><span class="sxs-lookup"><span data-stu-id="f3354-185">AND</span></span>      |

<span data-ttu-id="f3354-186">Vous pouvez mettre des expressions entre parenthèses quand vous utilisez des opérateurs conditionnels (par exemple, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="f3354-186">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="f3354-187">Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f3354-187">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3354-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3354-188">See also</span></span>

- [<span data-ttu-id="f3354-189">Infrastructures et cibles</span><span class="sxs-lookup"><span data-stu-id="f3354-189">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="f3354-190">Catalogue d’identificateurs de runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="f3354-190">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
