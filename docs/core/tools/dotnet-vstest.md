---
title: Commande dotnet vstest
description: La commande dotnet vstest permet de générer un projet et l’ensemble de ses dépendances.
ms.date: 02/27/2020
ms.openlocfilehash: f7db58f4aab59354b8c69ce0371324c23482dafe
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975392"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="cddb0-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="cddb0-103">dotnet vstest</span></span>

<span data-ttu-id="cddb0-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="cddb0-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cddb0-105">La `dotnet vstest` commande est remplacée par `dotnet test`, qui peut maintenant être utilisée pour exécuter des assemblys.</span><span class="sxs-lookup"><span data-stu-id="cddb0-105">The `dotnet vstest` command is superseded by `dotnet test`, which can now be used to run assemblies.</span></span> <span data-ttu-id="cddb0-106">Voir [`dotnet test`](dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="cddb0-106">See [`dotnet test`](dotnet-test.md).</span></span>

## <a name="name"></a><span data-ttu-id="cddb0-107">Nom</span><span class="sxs-lookup"><span data-stu-id="cddb0-107">Name</span></span>

<span data-ttu-id="cddb0-108">`dotnet-vstest`-Exécute les tests à partir des assemblys spécifiés.</span><span class="sxs-lookup"><span data-stu-id="cddb0-108">`dotnet-vstest` - Runs tests from the specified assemblies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cddb0-109">Synopsis</span><span class="sxs-lookup"><span data-stu-id="cddb0-109">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag <PATH_TO_LOG_FILE>]
    [--Framework <FRAMEWORK>] [--InIsolation] [-lt|--ListTests <FILE_NAME>]
    [--logger <LOGGER_URI/FRIENDLY_NAME>] [--Parallel]
    [--ParentProcessId <PROCESS_ID>] [--Platform] <PLATFORM_TYPE>
    [--Port <PORT>] [--ResultsDirectory<PATH>] [--Settings <SETTINGS_FILE>]
    [--TestAdapterPath <PATH>] [--TestCaseFilter <EXPRESSION>]
    [--Tests <TEST_NAMES>] [[--] <args>...]]

dotnet vstest -?|--Help
```

## <a name="description"></a><span data-ttu-id="cddb0-110">Description</span><span class="sxs-lookup"><span data-stu-id="cddb0-110">Description</span></span>

<span data-ttu-id="cddb0-111">La commande `dotnet-vstest` exécute l’application en ligne de commande `VSTest.Console` pour effectuer des tests unitaires automatisés.</span><span class="sxs-lookup"><span data-stu-id="cddb0-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="cddb0-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="cddb0-112">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="cddb0-113">Exécute les tests à partir des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="cddb0-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="cddb0-114">Séparez les noms d’assembly de test par des espaces.</span><span class="sxs-lookup"><span data-stu-id="cddb0-114">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="cddb0-115">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="cddb0-115">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="cddb0-116">Options</span><span class="sxs-lookup"><span data-stu-id="cddb0-116">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="cddb0-117">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="cddb0-117">Runs the tests in blame mode.</span></span> <span data-ttu-id="cddb0-118">Cette option s’avère utile pour isoler les tests responsables du plantage de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="cddb0-118">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="cddb0-119">Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.</span><span class="sxs-lookup"><span data-stu-id="cddb0-119">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <PATH_TO_LOG_FILE>`**

  <span data-ttu-id="cddb0-120">Active les journaux détaillés de la plateforme de test.</span><span class="sxs-lookup"><span data-stu-id="cddb0-120">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="cddb0-121">Les journaux sont écrits dans le fichier fourni.</span><span class="sxs-lookup"><span data-stu-id="cddb0-121">Logs are written to the provided file.</span></span>

- **`--Framework <FRAMEWORK>`**

  <span data-ttu-id="cddb0-122">Version .NET Framework cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="cddb0-122">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="cddb0-123">Les valeurs valides sont, par exemple, `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="cddb0-123">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="cddb0-124">Les valeurs `Framework40`, `Framework45`, `FrameworkCore10` et `FrameworkUap10` sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cddb0-124">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="cddb0-125">Exécute les tests dans un processus isolé.</span><span class="sxs-lookup"><span data-stu-id="cddb0-125">Runs the tests in an isolated process.</span></span> <span data-ttu-id="cddb0-126">De ce fait, il est moins probable que le processus *vstest.console.exe* soit arrêté sur une erreur dans les tests, mais les tests peuvent s’exécuter plus lentement.</span><span class="sxs-lookup"><span data-stu-id="cddb0-126">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <FILE_NAME>`**

  <span data-ttu-id="cddb0-127">Répertorie tous les tests découverts dans le conteneur de tests donné.</span><span class="sxs-lookup"><span data-stu-id="cddb0-127">Lists all discovered tests from the given test container.</span></span>

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="cddb0-128">Spécifiez un journal pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="cddb0-128">Specify a logger for test results.</span></span>

  - <span data-ttu-id="cddb0-129">Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :</span><span class="sxs-lookup"><span data-stu-id="cddb0-129">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="cddb0-130">Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`.</span><span class="sxs-lookup"><span data-stu-id="cddb0-130">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="cddb0-131">Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné.</span><span class="sxs-lookup"><span data-stu-id="cddb0-131">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="cddb0-132">Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.</span><span class="sxs-lookup"><span data-stu-id="cddb0-132">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="cddb0-133">Exécuter les tests en parallèle.</span><span class="sxs-lookup"><span data-stu-id="cddb0-133">Run tests in parallel.</span></span> <span data-ttu-id="cddb0-134">Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables.</span><span class="sxs-lookup"><span data-stu-id="cddb0-134">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="cddb0-135">Spécifiez un nombre de cœurs explicite en définissant `MaxCpuCount` la propriété sous `RunConfiguration` le nœud dans le fichier *RunSettings* .</span><span class="sxs-lookup"><span data-stu-id="cddb0-135">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <PROCESS_ID>`**

  <span data-ttu-id="cddb0-136">ID du processus parent chargé de lancer le processus actif.</span><span class="sxs-lookup"><span data-stu-id="cddb0-136">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <PLATFORM_TYPE>`**

  <span data-ttu-id="cddb0-137">Architecture de plateforme cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="cddb0-137">Target platform architecture used for test execution.</span></span> <span data-ttu-id="cddb0-138">Les valeurs correctes sont `x86`, `x64` et `ARM`.</span><span class="sxs-lookup"><span data-stu-id="cddb0-138">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <PORT>`**

  <span data-ttu-id="cddb0-139">Spécifie le port de la connexion de socket et la réception des messages d’événement.</span><span class="sxs-lookup"><span data-stu-id="cddb0-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PATH>`**

  <span data-ttu-id="cddb0-140">Un répertoire de résultats de test sera créé dans le chemin d’accès spécifié s’il n’en existe pas.</span><span class="sxs-lookup"><span data-stu-id="cddb0-140">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <SETTINGS_FILE>`**

  <span data-ttu-id="cddb0-141">Paramètres à utiliser durant l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="cddb0-141">Settings to use when running tests.</span></span>

- **`--TestAdapterPath <PATH>`**

  <span data-ttu-id="cddb0-142">Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="cddb0-142">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <EXPRESSION>`**

  <span data-ttu-id="cddb0-143">Exécutez les tests qui correspondent à l'expression donnée.</span><span class="sxs-lookup"><span data-stu-id="cddb0-143">Run tests that match the given expression.</span></span> <span data-ttu-id="cddb0-144">`<EXPRESSION>` est au format `<property>Operator<value>[|&<EXPRESSION>]`, où l’opérateur est `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="cddb0-144">`<EXPRESSION>` is of the format `<property>Operator<value>[|&<EXPRESSION>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="cddb0-145">L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="cddb0-145">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="cddb0-146">`()` Les parenthèses sont utilisées pour regrouper des sous-expressions.</span><span class="sxs-lookup"><span data-stu-id="cddb0-146">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="cddb0-147">Pour plus d’informations, consultez [TestCase Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="cddb0-147">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <TEST_NAMES>`**

  <span data-ttu-id="cddb0-148">Exécutez les tests avec les noms qui correspondent aux valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="cddb0-148">Run tests with names that match the provided values.</span></span> <span data-ttu-id="cddb0-149">Séparez les valeurs par des virgules.</span><span class="sxs-lookup"><span data-stu-id="cddb0-149">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="cddb0-150">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="cddb0-150">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="cddb0-151">Lit le fichier réponse pour obtenir plus d’options.</span><span class="sxs-lookup"><span data-stu-id="cddb0-151">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="cddb0-152">Spécifie des arguments supplémentaires à passer à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="cddb0-152">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="cddb0-153">Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="cddb0-153">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="cddb0-154">Utilisez un espace pour séparer plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="cddb0-154">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="cddb0-155">Exemples</span><span class="sxs-lookup"><span data-stu-id="cddb0-155">Examples</span></span>

<span data-ttu-id="cddb0-156">Exécuter les tests dans *MyTestProject. dll*:</span><span class="sxs-lookup"><span data-stu-id="cddb0-156">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="cddb0-157">Exécutez les tests dans *MyTestProject. dll*, en les exportant vers un dossier personnalisé avec un nom personnalisé :</span><span class="sxs-lookup"><span data-stu-id="cddb0-157">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="cddb0-158">Exécuter les tests dans *MyTestProject. dll* et *myothertestproject. exe*:</span><span class="sxs-lookup"><span data-stu-id="cddb0-158">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="cddb0-159">Exécuter des tests `TestMethod1` :</span><span class="sxs-lookup"><span data-stu-id="cddb0-159">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="cddb0-160">Exécuter des tests `TestMethod1` et `TestMethod2` :</span><span class="sxs-lookup"><span data-stu-id="cddb0-160">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="cddb0-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cddb0-161">See also</span></span>

- [<span data-ttu-id="cddb0-162">Options de ligne de commande VSTest.Console.exe</span><span class="sxs-lookup"><span data-stu-id="cddb0-162">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
