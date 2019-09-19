---
title: Commande dotnet test
description: La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné.
ms.date: 05/29/2018
ms.openlocfilehash: 306b6f8d890e567afc419b0408d7e683baaa814d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117568"
---
# <a name="dotnet-test"></a><span data-ttu-id="ca144-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="ca144-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ca144-104">Name</span><span class="sxs-lookup"><span data-stu-id="ca144-104">Name</span></span>

<span data-ttu-id="ca144-105">`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="ca144-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ca144-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="ca144-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ca144-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ca144-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ca144-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ca144-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ca144-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ca144-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="ca144-110">Description</span><span class="sxs-lookup"><span data-stu-id="ca144-110">Description</span></span>

<span data-ttu-id="ca144-111">La commande `dotnet test` est utilisée pour exécuter des tests unitaires dans un projet donné.</span><span class="sxs-lookup"><span data-stu-id="ca144-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="ca144-112">La commande `dotnet test` lance l’application console Test Runner spécifiée pour un projet.</span><span class="sxs-lookup"><span data-stu-id="ca144-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="ca144-113">Test Runner exécute les tests définis pour un framework de tests unitaires (par exemple, MSTest, NUnit ou xUnit) et signale la réussite ou l’échec de chaque test.</span><span class="sxs-lookup"><span data-stu-id="ca144-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="ca144-114">Si tous les tests réussissent, l’exécuteur de tests retourne 0 en tant que code de sortie. Sinon, si un test échoue, il retourne 1.</span><span class="sxs-lookup"><span data-stu-id="ca144-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="ca144-115">Test Runner et la bibliothèque de tests unitaires sont empaquetés sous forme de packages NuGet et sont restaurés comme des dépendances ordinaires du projet.</span><span class="sxs-lookup"><span data-stu-id="ca144-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="ca144-116">Les projets de test spécifient l’application Test Runner à l’aide d’un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :</span><span class="sxs-lookup"><span data-stu-id="ca144-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="ca144-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="ca144-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="ca144-118">Chemin du projet de test.</span><span class="sxs-lookup"><span data-stu-id="ca144-118">Path to the test project.</span></span> <span data-ttu-id="ca144-119">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="ca144-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="ca144-120">Options</span><span class="sxs-lookup"><span data-stu-id="ca144-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ca144-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ca144-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="ca144-122">Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="ca144-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="ca144-123">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="ca144-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="ca144-124">Cette option s’avère utile pour isoler les tests responsables du plantage de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="ca144-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="ca144-125">Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.</span><span class="sxs-lookup"><span data-stu-id="ca144-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ca144-126">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="ca144-126">Defines the build configuration.</span></span> <span data-ttu-id="ca144-127">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="ca144-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="ca144-128">Active le collecteur de données pour la série de tests.</span><span class="sxs-lookup"><span data-stu-id="ca144-128">Enables data collector for the test run.</span></span> <span data-ttu-id="ca144-129">Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).</span><span class="sxs-lookup"><span data-stu-id="ca144-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="ca144-130">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="ca144-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ca144-131">Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="ca144-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ca144-132">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="ca144-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ca144-133">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="ca144-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ca144-134">Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ca144-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="ca144-135">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="ca144-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="ca144-136">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="ca144-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="ca144-137">Ne génère pas le projet de test avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="ca144-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="ca144-138">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="ca144-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="ca144-139">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="ca144-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ca144-140">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca144-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="ca144-141">Répertoire où les résultats de test doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="ca144-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="ca144-142">Si le répertoire spécifié n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="ca144-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="ca144-143">Fichier `.runsettings` à utiliser pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="ca144-143">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="ca144-144">Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="ca144-144">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="ca144-145">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="ca144-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ca144-146">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="ca144-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ca144-147">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ca144-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="ca144-148">Arguments passés en tant que paramètres RunSettings pour le test.</span><span class="sxs-lookup"><span data-stu-id="ca144-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="ca144-149">Les arguments sont spécifiés en tant que paires `[name]=[value]` après "-- " (notez l’espace après --).</span><span class="sxs-lookup"><span data-stu-id="ca144-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="ca144-150">Un espace est utilisé pour séparer plusieurs paires `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="ca144-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="ca144-151">Exemple : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="ca144-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="ca144-152">Pour plus d’informations sur RunSettings, consultez [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="ca144-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ca144-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ca144-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="ca144-154">Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="ca144-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ca144-155">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="ca144-155">Defines the build configuration.</span></span> <span data-ttu-id="ca144-156">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="ca144-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="ca144-157">Active le collecteur de données pour la série de tests.</span><span class="sxs-lookup"><span data-stu-id="ca144-157">Enables data collector for the test run.</span></span> <span data-ttu-id="ca144-158">Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).</span><span class="sxs-lookup"><span data-stu-id="ca144-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="ca144-159">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="ca144-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ca144-160">Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="ca144-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ca144-161">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="ca144-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ca144-162">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="ca144-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ca144-163">Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ca144-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="ca144-164">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="ca144-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="ca144-165">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="ca144-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="ca144-166">Ne génère pas le projet de test avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="ca144-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="ca144-167">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="ca144-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="ca144-168">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="ca144-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ca144-169">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca144-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="ca144-170">Répertoire où les résultats de test doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="ca144-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="ca144-171">Si le répertoire spécifié n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="ca144-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="ca144-172">Fichier `.runsettings` à utiliser pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="ca144-172">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="ca144-173">Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="ca144-173">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="ca144-174">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="ca144-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ca144-175">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="ca144-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ca144-176">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ca144-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ca144-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ca144-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="ca144-178">Utilise les adaptateurs de tests personnalisés à partir du chemin spécifié dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="ca144-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ca144-179">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="ca144-179">Defines the build configuration.</span></span> <span data-ttu-id="ca144-180">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="ca144-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="ca144-181">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="ca144-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ca144-182">Recherche des binaires de test pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="ca144-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ca144-183">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="ca144-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ca144-184">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="ca144-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ca144-185">Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ca144-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="ca144-186">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="ca144-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="ca144-187">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="ca144-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="ca144-188">Ne génère pas le projet de test avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="ca144-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ca144-189">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca144-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="ca144-190">Fichier `.runsettings` à utiliser pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="ca144-190">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="ca144-191">Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="ca144-191">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="ca144-192">Répertorie tous les tests découverts dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="ca144-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ca144-193">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="ca144-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ca144-194">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ca144-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ca144-195">Exemples</span><span class="sxs-lookup"><span data-stu-id="ca144-195">Examples</span></span>

<span data-ttu-id="ca144-196">Exécutez les tests du projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="ca144-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="ca144-197">Exécuter les tests dans le projet `test1` :</span><span class="sxs-lookup"><span data-stu-id="ca144-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="ca144-198">Exécutez les tests du projet dans le répertoire actif et générez un fichier de résultats des tests au format trx :</span><span class="sxs-lookup"><span data-stu-id="ca144-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger trx`

## <a name="filter-option-details"></a><span data-ttu-id="ca144-199">Détails de l’option de filtre</span><span class="sxs-lookup"><span data-stu-id="ca144-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ca144-200">`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="ca144-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="ca144-201">`<property>` est un attribut de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="ca144-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="ca144-202">Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :</span><span class="sxs-lookup"><span data-stu-id="ca144-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="ca144-203">Infrastructure de test</span><span class="sxs-lookup"><span data-stu-id="ca144-203">Test Framework</span></span> | <span data-ttu-id="ca144-204">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="ca144-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ca144-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="ca144-205">MSTest</span></span>         | <ul><li><span data-ttu-id="ca144-206">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ca144-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="ca144-207">Name</span><span class="sxs-lookup"><span data-stu-id="ca144-207">Name</span></span></li><li><span data-ttu-id="ca144-208">ClassName</span><span class="sxs-lookup"><span data-stu-id="ca144-208">ClassName</span></span></li><li><span data-ttu-id="ca144-209">Priorité</span><span class="sxs-lookup"><span data-stu-id="ca144-209">Priority</span></span></li><li><span data-ttu-id="ca144-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="ca144-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="ca144-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="ca144-211">xUnit</span></span>          | <ul><li><span data-ttu-id="ca144-212">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ca144-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="ca144-213">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ca144-213">DisplayName</span></span></li><li><span data-ttu-id="ca144-214">Caractéristiques</span><span class="sxs-lookup"><span data-stu-id="ca144-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="ca144-215">La section `<operator>` décrit la relation entre la propriété et la valeur :</span><span class="sxs-lookup"><span data-stu-id="ca144-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="ca144-216">Opérateur</span><span class="sxs-lookup"><span data-stu-id="ca144-216">Operator</span></span> | <span data-ttu-id="ca144-217">Fonction</span><span class="sxs-lookup"><span data-stu-id="ca144-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="ca144-218">Correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="ca144-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="ca144-219">Pas de correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="ca144-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="ca144-220">Contient</span><span class="sxs-lookup"><span data-stu-id="ca144-220">Contains</span></span>        |

<span data-ttu-id="ca144-221">`<value>` est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ca144-221">`<value>` is a string.</span></span> <span data-ttu-id="ca144-222">Toutes les recherches respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="ca144-222">All the lookups are case insensitive.</span></span>

<span data-ttu-id="ca144-223">Une expression sans `<operator>` est automatiquement considérée comme `contains` sur la propriété `FullyQualifiedName` (par exemple, `dotnet test --filter xyz` est identique à `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="ca144-223">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="ca144-224">Les expressions peuvent être associées à des opérateurs conditionnels :</span><span class="sxs-lookup"><span data-stu-id="ca144-224">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="ca144-225">Opérateur</span><span class="sxs-lookup"><span data-stu-id="ca144-225">Operator</span></span>            | <span data-ttu-id="ca144-226">Fonction</span><span class="sxs-lookup"><span data-stu-id="ca144-226">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="ca144-227">OU</span><span class="sxs-lookup"><span data-stu-id="ca144-227">OR</span></span>       |
| `&`                 | <span data-ttu-id="ca144-228">AND</span><span class="sxs-lookup"><span data-stu-id="ca144-228">AND</span></span>      |

<span data-ttu-id="ca144-229">Vous pouvez mettre des expressions entre parenthèses quand vous utilisez des opérateurs conditionnels (par exemple, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="ca144-229">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="ca144-230">Pour plus d’informations et des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ca144-230">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca144-231">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca144-231">See also</span></span>

- [<span data-ttu-id="ca144-232">Frameworks et cibles</span><span class="sxs-lookup"><span data-stu-id="ca144-232">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="ca144-233">Catalogue d’identificateurs de runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="ca144-233">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
