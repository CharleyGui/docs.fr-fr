---
title: Commande dotnet test
description: La commande dotnet test est utilisée pour exécuter des tests unitaires dans un projet donné.
ms.date: 04/29/2020
ms.openlocfilehash: d67521084330b206afca89baf59228b99ca799a1
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656753"
---
# <a name="dotnet-test"></a><span data-ttu-id="32c5d-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="32c5d-103">dotnet test</span></span>

<span data-ttu-id="32c5d-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="32c5d-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="32c5d-105">Nom</span><span class="sxs-lookup"><span data-stu-id="32c5d-105">Name</span></span>

<span data-ttu-id="32c5d-106">`dotnet test` - Pilote de test .NET utilisée pour exécuter des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="32c5d-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="32c5d-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="32c5d-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="32c5d-108">Description</span><span class="sxs-lookup"><span data-stu-id="32c5d-108">Description</span></span>

<span data-ttu-id="32c5d-109">La `dotnet test` commande est utilisée pour exécuter des tests unitaires dans une solution donnée.</span><span class="sxs-lookup"><span data-stu-id="32c5d-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="32c5d-110">La `dotnet test` commande génère la solution et exécute une application hôte de test pour chaque projet de test de la solution.</span><span class="sxs-lookup"><span data-stu-id="32c5d-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="32c5d-111">L’hôte de test exécute des tests dans le projet donné à l’aide d’une infrastructure de test, par exemple, MSTest, NUnit ou xUnit, et signale la réussite ou l’échec de chaque test.</span><span class="sxs-lookup"><span data-stu-id="32c5d-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="32c5d-112">Si tous les tests réussissent, l’exécuteur de tests retourne 0 en tant que code de sortie. Sinon, si un test échoue, il retourne 1.</span><span class="sxs-lookup"><span data-stu-id="32c5d-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="32c5d-113">Pour les projets multi-ciblés, les tests sont exécutés pour chaque Framework ciblé.</span><span class="sxs-lookup"><span data-stu-id="32c5d-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="32c5d-114">L’hôte de test et l’infrastructure de tests unitaires sont empaquetés en tant que packages NuGet et sont restaurés en tant que dépendances ordinaires pour le projet.</span><span class="sxs-lookup"><span data-stu-id="32c5d-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="32c5d-115">Les projets de test spécifient l’application Test Runner à l’aide d’un élément `<PackageReference>` ordinaire, comme indiqué dans l’exemple de fichier projet suivant :</span><span class="sxs-lookup"><span data-stu-id="32c5d-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="32c5d-116">Où `Microsoft.NET.Test.Sdk` est l’hôte de test, `xunit` est l’infrastructure de test.</span><span class="sxs-lookup"><span data-stu-id="32c5d-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="32c5d-117">Et `xunit.runner.visualstudio` est un adaptateur de test, qui permet à l’infrastructure xUnit de fonctionner avec l’hôte de test.</span><span class="sxs-lookup"><span data-stu-id="32c5d-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="32c5d-118">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="32c5d-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="32c5d-119">Arguments</span><span class="sxs-lookup"><span data-stu-id="32c5d-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="32c5d-120">Chemin du projet de test.</span><span class="sxs-lookup"><span data-stu-id="32c5d-120">Path to the test project.</span></span>
  - <span data-ttu-id="32c5d-121">Chemin d’accès à la solution.</span><span class="sxs-lookup"><span data-stu-id="32c5d-121">Path to the solution.</span></span>
  - <span data-ttu-id="32c5d-122">Chemin d’accès à un répertoire qui contient un projet ou une solution.</span><span class="sxs-lookup"><span data-stu-id="32c5d-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="32c5d-123">Chemin d’accès à un fichier *. dll* de projet de test.</span><span class="sxs-lookup"><span data-stu-id="32c5d-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="32c5d-124">S’il n’est pas spécifié, il recherche un projet ou une solution dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="32c5d-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="32c5d-125">Options</span><span class="sxs-lookup"><span data-stu-id="32c5d-125">Options</span></span>

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  <span data-ttu-id="32c5d-126">Chemin d’accès à un répertoire dans lequel rechercher d’autres adaptateurs de test.</span><span class="sxs-lookup"><span data-stu-id="32c5d-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="32c5d-127">Seuls les fichiers *. dll* avec suffixe `.TestAdapter.dll` sont inspectés.</span><span class="sxs-lookup"><span data-stu-id="32c5d-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="32c5d-128">S’il n’est pas spécifié, la recherche s’effectue dans le répertoire du *fichier test. dll* .</span><span class="sxs-lookup"><span data-stu-id="32c5d-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="32c5d-129">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="32c5d-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="32c5d-130">Cette option est utile pour isoler les tests problématiques qui provoquent le blocage de l’hôte de test.</span><span class="sxs-lookup"><span data-stu-id="32c5d-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="32c5d-131">Lorsqu’un incident est détecté, il crée un fichier de séquence dans `TestResults/<Guid>/<Guid>_Sequence.xml` qui capture l’ordre des tests qui ont été exécutés avant l’incident.</span><span class="sxs-lookup"><span data-stu-id="32c5d-131">When a crash is detected, it creates a sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- <span data-ttu-id="32c5d-132">**`--blame-crash`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)</span><span class="sxs-lookup"><span data-stu-id="32c5d-132">**`--blame-crash`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="32c5d-133">Exécute les tests en mode de responsabilité et collecte un vidage sur incident lorsque l’hôte de test s’arrête de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="32c5d-133">Runs the tests in blame mode and collects a crash dump when the test host exits unexpectedly.</span></span> <span data-ttu-id="32c5d-134">Cette option est uniquement prise en charge sur Windows.</span><span class="sxs-lookup"><span data-stu-id="32c5d-134">This option is only supported on Windows.</span></span> <span data-ttu-id="32c5d-135">Un répertoire qui contient *procdump.exe* et *procdump64.exe* doit se trouver dans la variable d’environnement PATH ou PROCDUMP_PATH.</span><span class="sxs-lookup"><span data-stu-id="32c5d-135">A directory that contains *procdump.exe* and *procdump64.exe* must be in the PATH or PROCDUMP_PATH environment variable.</span></span> <span data-ttu-id="32c5d-136">[Téléchargez les outils](https://docs.microsoft.com/sysinternals/downloads/procdump).</span><span class="sxs-lookup"><span data-stu-id="32c5d-136">[Download the tools](https://docs.microsoft.com/sysinternals/downloads/procdump).</span></span> <span data-ttu-id="32c5d-137">Implique `--blame` .</span><span class="sxs-lookup"><span data-stu-id="32c5d-137">Implies `--blame`.</span></span>

- <span data-ttu-id="32c5d-138">**`--blame-crash-dump-type <DUMP_TYPE>`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)</span><span class="sxs-lookup"><span data-stu-id="32c5d-138">**`--blame-crash-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="32c5d-139">Type de vidage sur incident à collecter.</span><span class="sxs-lookup"><span data-stu-id="32c5d-139">The type of crash dump to be collected.</span></span> <span data-ttu-id="32c5d-140">Implique `--blame-crash` .</span><span class="sxs-lookup"><span data-stu-id="32c5d-140">Implies `--blame-crash`.</span></span>

- <span data-ttu-id="32c5d-141">**`--blame-crash-collect-always`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)</span><span class="sxs-lookup"><span data-stu-id="32c5d-141">**`--blame-crash-collect-always`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="32c5d-142">Collecte un vidage sur incident sur la sortie attendue et sur l’hôte de test inattendu.</span><span class="sxs-lookup"><span data-stu-id="32c5d-142">Collects a crash dump on expected as well as unexpected test host exit.</span></span>

- <span data-ttu-id="32c5d-143">**`--blame-hang`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)</span><span class="sxs-lookup"><span data-stu-id="32c5d-143">**`--blame-hang`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="32c5d-144">Exécuter les tests en mode de responsabilité et collecter un vidage sur le blocage quand un test dépasse le délai d’attente donné.</span><span class="sxs-lookup"><span data-stu-id="32c5d-144">Run the tests in blame mode and collects a hang dump when a test exceeds the given timeout.</span></span>

- <span data-ttu-id="32c5d-145">**`--blame-hang-dump-type <DUMP_TYPE>`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)</span><span class="sxs-lookup"><span data-stu-id="32c5d-145">**`--blame-hang-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="32c5d-146">Type de vidage sur incident à collecter.</span><span class="sxs-lookup"><span data-stu-id="32c5d-146">The type of crash dump to be collected.</span></span> <span data-ttu-id="32c5d-147">Il doit s’agir `full` de, `mini` ou `none` .</span><span class="sxs-lookup"><span data-stu-id="32c5d-147">It should be `full`, `mini`, or `none`.</span></span> <span data-ttu-id="32c5d-148">Lorsque `none` est spécifié, l’hôte de test se termine à l’expiration du délai d’attente, mais aucun vidage n’est collecté.</span><span class="sxs-lookup"><span data-stu-id="32c5d-148">When `none` is specified, test host is terminated on timeout, but no dump is collected.</span></span> <span data-ttu-id="32c5d-149">Implique `--blame-hang` .</span><span class="sxs-lookup"><span data-stu-id="32c5d-149">Implies `--blame-hang`.</span></span>

- <span data-ttu-id="32c5d-150">**`--blame-hang-timeout <TIMESPAN>`** (Disponible depuis le kit de développement logiciel (SDK) .NET 5,0 Preview)</span><span class="sxs-lookup"><span data-stu-id="32c5d-150">**`--blame-hang-timeout <TIMESPAN>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="32c5d-151">Délai d’attente par test, après lequel un vidage sur le blocage est déclenché et le processus hôte de test est terminé.</span><span class="sxs-lookup"><span data-stu-id="32c5d-151">Per-test timeout, after which a hang dump is triggered and the test host process is terminated.</span></span> <span data-ttu-id="32c5d-152">La valeur du délai d’attente est spécifiée dans l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="32c5d-152">The timeout value is specified in one of the following formats:</span></span>
  
  - <span data-ttu-id="32c5d-153">1.5 h</span><span class="sxs-lookup"><span data-stu-id="32c5d-153">1.5h</span></span>
  - <span data-ttu-id="32c5d-154">90m</span><span class="sxs-lookup"><span data-stu-id="32c5d-154">90m</span></span>
  - <span data-ttu-id="32c5d-155">5400</span><span class="sxs-lookup"><span data-stu-id="32c5d-155">5400s</span></span>
  - <span data-ttu-id="32c5d-156">5400000ms</span><span class="sxs-lookup"><span data-stu-id="32c5d-156">5400000ms</span></span>

  <span data-ttu-id="32c5d-157">Quand aucune unité n’est utilisée (par exemple, 5,4 millions), la valeur est supposée être en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="32c5d-157">When no unit is used (for example, 5400000), the value is assumed to be in milliseconds.</span></span> <span data-ttu-id="32c5d-158">Lorsqu’il est utilisé avec les tests pilotés par les données, le comportement du délai d’attente dépend de l’adaptateur de test utilisé.</span><span class="sxs-lookup"><span data-stu-id="32c5d-158">When used together with data driven tests, the timeout behavior depends on the test adapter used.</span></span> <span data-ttu-id="32c5d-159">Pour xUnit et NUnit, le délai d’attente est renouvelé après chaque cas de test.</span><span class="sxs-lookup"><span data-stu-id="32c5d-159">For xUnit and NUnit the timeout is renewed after every test case.</span></span> <span data-ttu-id="32c5d-160">Pour MSTest, le délai d’attente est utilisé pour tous les cas de test.</span><span class="sxs-lookup"><span data-stu-id="32c5d-160">For MSTest, the timeout is used for all test cases.</span></span> <span data-ttu-id="32c5d-161">Cette option est prise en charge sur Windows avec netcoreapp 2.1 et versions ultérieures, et sur Linux avec netcoreapp 3.1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="32c5d-161">This option is supported on Windows with netcoreapp2.1 and later, and on Linux with netcoreapp3.1 and later.</span></span> <span data-ttu-id="32c5d-162">macOS n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="32c5d-162">macOS is not supported.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="32c5d-163">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="32c5d-163">Defines the build configuration.</span></span> <span data-ttu-id="32c5d-164">La valeur par défaut est `Debug`, mais la configuration de votre projet peut remplacer ce paramètre du kit SDK par défaut.</span><span class="sxs-lookup"><span data-stu-id="32c5d-164">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_NAME>`**

  <span data-ttu-id="32c5d-165">Active le collecteur de données pour la série de tests.</span><span class="sxs-lookup"><span data-stu-id="32c5d-165">Enables data collector for the test run.</span></span> <span data-ttu-id="32c5d-166">Pour plus d’informations, consultez [Monitor and analyze test run](https://aka.ms/vstest-collect) (Surveiller et analyser la série de tests).</span><span class="sxs-lookup"><span data-stu-id="32c5d-166">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="32c5d-167">Pour collecter la couverture du code sur toutes les plateformes prises en charge par .NET Core, installez [coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) et utilisez l' `--collect:"XPlat Code Coverage"` option.</span><span class="sxs-lookup"><span data-stu-id="32c5d-167">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="32c5d-168">Sur Windows, vous pouvez collecter la couverture du code à l’aide de l' `--collect "Code Coverage"` option.</span><span class="sxs-lookup"><span data-stu-id="32c5d-168">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="32c5d-169">Cette option génère un fichier *. coverage* , qui peut être ouvert dans Visual Studio 2019 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="32c5d-169">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="32c5d-170">Pour plus d’informations, consultez Utilisation de la [couverture du code](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) et personnalisation de l’analyse de la [couverture du code](/visualstudio/test/customizing-code-coverage-analysis).</span><span class="sxs-lookup"><span data-stu-id="32c5d-170">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <LOG_FILE>`**

  <span data-ttu-id="32c5d-171">Active le mode de diagnostic pour la plateforme de test et écrit des messages de diagnostic dans le fichier spécifié et dans des fichiers à côté de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="32c5d-171">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="32c5d-172">Le processus d’enregistrement des messages détermine quels fichiers sont créés, par exemple `*.host_<date>.txt` pour le journal de l’hôte de test et `*.datacollector_<date>.txt` pour le journal du collecteur de données.</span><span class="sxs-lookup"><span data-stu-id="32c5d-172">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="32c5d-173">Force l’utilisation de `dotnet` ou .NET Framework hôte de test pour les binaires de test.</span><span class="sxs-lookup"><span data-stu-id="32c5d-173">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="32c5d-174">Cette option détermine uniquement le type d’hôte à utiliser.</span><span class="sxs-lookup"><span data-stu-id="32c5d-174">This option only determines which type of host to use.</span></span> <span data-ttu-id="32c5d-175">La version de .NET Framework à utiliser est déterminée par le *runtimeconfig.js* du projet de test.</span><span class="sxs-lookup"><span data-stu-id="32c5d-175">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="32c5d-176">Lorsqu’il n’est pas spécifié, l' [attribut d’assembly TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) est utilisé pour déterminer le type d’hôte.</span><span class="sxs-lookup"><span data-stu-id="32c5d-176">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="32c5d-177">Lorsque cet attribut est supprimé du *fichier. dll*, l’hôte .NET Framework est utilisé.</span><span class="sxs-lookup"><span data-stu-id="32c5d-177">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="32c5d-178">Filtre les tests dans le projet actuel à l’aide de l’expression donnée.</span><span class="sxs-lookup"><span data-stu-id="32c5d-178">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="32c5d-179">Pour plus de détails, consultez la section [Détails de l’option de filtre](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="32c5d-179">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="32c5d-180">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="32c5d-180">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="32c5d-181">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="32c5d-181">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="32c5d-182">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="32c5d-182">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="32c5d-183">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="32c5d-183">For example, to complete authentication.</span></span> <span data-ttu-id="32c5d-184">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="32c5d-184">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER>`**

  <span data-ttu-id="32c5d-185">Spécifie un enregistreur d’événements pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="32c5d-185">Specifies a logger for test results.</span></span> <span data-ttu-id="32c5d-186">Contrairement à MSBuild, dotnet test n’accepte pas les abréviations : au lieu d' `-l "console;v=d"` utiliser `-l "console;verbosity=detailed"` .</span><span class="sxs-lookup"><span data-stu-id="32c5d-186">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="32c5d-187">Ne génère pas le projet de test avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="32c5d-187">Doesn't build the test project before running it.</span></span> <span data-ttu-id="32c5d-188">Il définit également implicitement l' `--no-restore` indicateur-.</span><span class="sxs-lookup"><span data-stu-id="32c5d-188">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="32c5d-189">Exécuter les tests sans afficher la bannière Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="32c5d-189">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="32c5d-190">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="32c5d-190">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="32c5d-191">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="32c5d-191">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="32c5d-192">Répertoire dans lequel rechercher les binaires à exécuter.</span><span class="sxs-lookup"><span data-stu-id="32c5d-192">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="32c5d-193">S’il n’est pas spécifié, le chemin d'accès par défaut est `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="32c5d-193">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="32c5d-194">Pour les projets avec plusieurs frameworks cibles (via la `TargetFrameworks` propriété), vous devez également définir `--framework` lorsque vous spécifiez cette option.</span><span class="sxs-lookup"><span data-stu-id="32c5d-194">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="32c5d-195">`dotnet test` exécute toujours les tests à partir du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="32c5d-195">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="32c5d-196">Vous pouvez utiliser <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> pour consommer des ressources de test dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="32c5d-196">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <RESULTS_DIR>`**

  <span data-ttu-id="32c5d-197">Répertoire où les résultats de test doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="32c5d-197">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="32c5d-198">Si le répertoire spécifié n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="32c5d-198">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="32c5d-199">La valeur par défaut se trouve `TestResults` dans le répertoire qui contient le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="32c5d-199">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="32c5d-200">Runtime cible à tester.</span><span class="sxs-lookup"><span data-stu-id="32c5d-200">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="32c5d-201">Fichier `.runsettings` à utiliser pour exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="32c5d-201">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="32c5d-202">L' `TargetPlatform` élément (x86 | x64) n’a aucun effet pour `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="32c5d-202">The `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="32c5d-203">Pour exécuter des tests ciblant x86, installez la version x86 de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="32c5d-203">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="32c5d-204">Le nombre de bits de l' *dotnet.exe* qui se trouve sur le chemin d’accès correspond à ce qui sera utilisé pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="32c5d-204">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="32c5d-205">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="32c5d-205">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="32c5d-206">Configurez des tests unitaires à l’aide d’un fichier `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="32c5d-206">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="32c5d-207">Configurer une série de tests</span><span class="sxs-lookup"><span data-stu-id="32c5d-207">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="32c5d-208">Répertoriez les tests découverts au lieu d’exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="32c5d-208">List the discovered tests instead of running the tests.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="32c5d-209">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="32c5d-209">Sets the verbosity level of the command.</span></span> <span data-ttu-id="32c5d-210">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="32c5d-210">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="32c5d-211">La valeur par défaut est `minimal`.</span><span class="sxs-lookup"><span data-stu-id="32c5d-211">The default is `minimal`.</span></span> <span data-ttu-id="32c5d-212">Pour plus d'informations, consultez <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="32c5d-212">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="32c5d-213">**`RunSettings`** arguments</span><span class="sxs-lookup"><span data-stu-id="32c5d-213">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="32c5d-214">Inline `RunSettings` sont passés comme derniers arguments sur la ligne de commande après « -- » (Notez l’espace après--).</span><span class="sxs-lookup"><span data-stu-id="32c5d-214">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="32c5d-215">Inline `RunSettings` sont spécifiés en tant que `[name]=[value]` paires.</span><span class="sxs-lookup"><span data-stu-id="32c5d-215">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="32c5d-216">Un espace est utilisé pour séparer plusieurs paires `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="32c5d-216">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="32c5d-217">Exemple : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="32c5d-217">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="32c5d-218">Pour plus d’informations, consultez [transmission d’arguments RunSettings via la ligne de commande](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="32c5d-218">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="32c5d-219">Exemples</span><span class="sxs-lookup"><span data-stu-id="32c5d-219">Examples</span></span>

- <span data-ttu-id="32c5d-220">Exécutez les tests du projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="32c5d-220">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="32c5d-221">Exécuter les tests dans le projet `test1` :</span><span class="sxs-lookup"><span data-stu-id="32c5d-221">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="32c5d-222">Exécutez les tests dans le projet dans le répertoire actif et générez un fichier de résultats de test au format trx :</span><span class="sxs-lookup"><span data-stu-id="32c5d-222">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="32c5d-223">Exécutez les tests dans le projet dans le répertoire actif et générez un fichier de couverture du code (après l’installation de l’intégration des collecteurs [coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) ) :</span><span class="sxs-lookup"><span data-stu-id="32c5d-223">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) collectors integration):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="32c5d-224">Exécutez les tests dans le projet dans le répertoire actif et générez un fichier de couverture du code (Windows uniquement) :</span><span class="sxs-lookup"><span data-stu-id="32c5d-224">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="32c5d-225">Exécutez les tests dans le projet dans le répertoire actif, puis consignez des commentaires détaillés sur la console :</span><span class="sxs-lookup"><span data-stu-id="32c5d-225">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- <span data-ttu-id="32c5d-226">Exécutez les tests dans le projet dans le répertoire actif et testez les tests qui étaient en cours lorsque l’hôte de test s’est arrêté :</span><span class="sxs-lookup"><span data-stu-id="32c5d-226">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="32c5d-227">Détails de l’option de filtre</span><span class="sxs-lookup"><span data-stu-id="32c5d-227">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="32c5d-228">`<Expression>` est au format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="32c5d-228">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="32c5d-229">`<property>` est un attribut de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="32c5d-229">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="32c5d-230">Les propriétés suivantes sont prises en charge par les principales infrastructures de tests unitaires :</span><span class="sxs-lookup"><span data-stu-id="32c5d-230">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="32c5d-231">Framework de test</span><span class="sxs-lookup"><span data-stu-id="32c5d-231">Test Framework</span></span> | <span data-ttu-id="32c5d-232">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="32c5d-232">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="32c5d-233">MSTest</span><span class="sxs-lookup"><span data-stu-id="32c5d-233">MSTest</span></span>         | <ul><li><span data-ttu-id="32c5d-234">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="32c5d-234">FullyQualifiedName</span></span></li><li><span data-ttu-id="32c5d-235">Nom</span><span class="sxs-lookup"><span data-stu-id="32c5d-235">Name</span></span></li><li><span data-ttu-id="32c5d-236">ClassName</span><span class="sxs-lookup"><span data-stu-id="32c5d-236">ClassName</span></span></li><li><span data-ttu-id="32c5d-237">Priority</span><span class="sxs-lookup"><span data-stu-id="32c5d-237">Priority</span></span></li><li><span data-ttu-id="32c5d-238">TestCategory</span><span class="sxs-lookup"><span data-stu-id="32c5d-238">TestCategory</span></span></li></ul> |
| <span data-ttu-id="32c5d-239">xUnit</span><span class="sxs-lookup"><span data-stu-id="32c5d-239">xUnit</span></span>          | <ul><li><span data-ttu-id="32c5d-240">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="32c5d-240">FullyQualifiedName</span></span></li><li><span data-ttu-id="32c5d-241">DisplayName</span><span class="sxs-lookup"><span data-stu-id="32c5d-241">DisplayName</span></span></li><li><span data-ttu-id="32c5d-242">Caractéristiques</span><span class="sxs-lookup"><span data-stu-id="32c5d-242">Traits</span></span></li></ul>                                   |
| <span data-ttu-id="32c5d-243">NUnit</span><span class="sxs-lookup"><span data-stu-id="32c5d-243">NUnit</span></span>          | <ul><li><span data-ttu-id="32c5d-244">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="32c5d-244">FullyQualifiedName</span></span></li><li><span data-ttu-id="32c5d-245">Nom</span><span class="sxs-lookup"><span data-stu-id="32c5d-245">Name</span></span></li><li><span data-ttu-id="32c5d-246">TestCategory</span><span class="sxs-lookup"><span data-stu-id="32c5d-246">TestCategory</span></span></li><li><span data-ttu-id="32c5d-247">Priority</span><span class="sxs-lookup"><span data-stu-id="32c5d-247">Priority</span></span></li></ul>                                   |

<span data-ttu-id="32c5d-248">La section `<operator>` décrit la relation entre la propriété et la valeur :</span><span class="sxs-lookup"><span data-stu-id="32c5d-248">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="32c5d-249">Opérateur</span><span class="sxs-lookup"><span data-stu-id="32c5d-249">Operator</span></span> | <span data-ttu-id="32c5d-250">Fonction</span><span class="sxs-lookup"><span data-stu-id="32c5d-250">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="32c5d-251">Concordance exacte</span><span class="sxs-lookup"><span data-stu-id="32c5d-251">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="32c5d-252">Pas de correspondance exacte</span><span class="sxs-lookup"><span data-stu-id="32c5d-252">Not exact match</span></span> |
| `~`      | <span data-ttu-id="32c5d-253">Contient</span><span class="sxs-lookup"><span data-stu-id="32c5d-253">Contains</span></span>        |
| `!~`     | <span data-ttu-id="32c5d-254">Ne contient pas</span><span class="sxs-lookup"><span data-stu-id="32c5d-254">Not contains</span></span>    |

<span data-ttu-id="32c5d-255">`<value>` est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="32c5d-255">`<value>` is a string.</span></span> <span data-ttu-id="32c5d-256">Toutes les recherches respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="32c5d-256">All the lookups are case insensitive.</span></span>

<span data-ttu-id="32c5d-257">Une expression sans `<operator>` est automatiquement considérée comme `contains` sur la propriété `FullyQualifiedName` (par exemple, `dotnet test --filter xyz` est identique à `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="32c5d-257">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="32c5d-258">Les expressions peuvent être associées à des opérateurs conditionnels :</span><span class="sxs-lookup"><span data-stu-id="32c5d-258">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="32c5d-259">Opérateur</span><span class="sxs-lookup"><span data-stu-id="32c5d-259">Operator</span></span>            | <span data-ttu-id="32c5d-260">Fonction</span><span class="sxs-lookup"><span data-stu-id="32c5d-260">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="32c5d-261">OR</span><span class="sxs-lookup"><span data-stu-id="32c5d-261">OR</span></span>       |
| `&`                 | <span data-ttu-id="32c5d-262">AND</span><span class="sxs-lookup"><span data-stu-id="32c5d-262">AND</span></span>      |

<span data-ttu-id="32c5d-263">Vous pouvez mettre des expressions entre parenthèses quand vous utilisez des opérateurs conditionnels (par exemple, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="32c5d-263">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="32c5d-264">Pour plus d’informations et pour obtenir des exemples sur la façon d’utiliser le filtrage de test unitaire sélectif, consultez [Exécution de tests unitaires sélectifs](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="32c5d-264">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="32c5d-265">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32c5d-265">See also</span></span>

- [<span data-ttu-id="32c5d-266">Infrastructures et cibles</span><span class="sxs-lookup"><span data-stu-id="32c5d-266">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="32c5d-267">Catalogue d’identificateurs de Runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="32c5d-267">.NET Core Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="32c5d-268">Passage d’arguments RunSettings via la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="32c5d-268">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
