---
title: Commande dotnet vstest
description: La commande dotnet vstest permet de générer un projet et l’ensemble de ses dépendances.
ms.date: 02/27/2020
ms.openlocfilehash: e8fa94cf12ca2fe5fb99c6e3c1dcdb52185798c0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463287"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="74f57-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="74f57-103">dotnet vstest</span></span>

<span data-ttu-id="74f57-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="74f57-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="74f57-105">Nom</span><span class="sxs-lookup"><span data-stu-id="74f57-105">Name</span></span>

<span data-ttu-id="74f57-106">`dotnet-vstest` - Exécute les tests à partir des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="74f57-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="74f57-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="74f57-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="74f57-108">Description</span><span class="sxs-lookup"><span data-stu-id="74f57-108">Description</span></span>

<span data-ttu-id="74f57-109">La commande `dotnet-vstest` exécute l’application en ligne de commande `VSTest.Console` pour effectuer des tests unitaires automatisés.</span><span class="sxs-lookup"><span data-stu-id="74f57-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="74f57-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="74f57-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="74f57-111">Exécute les tests à partir des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="74f57-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="74f57-112">Séparez les noms d’assembly de test par des espaces.</span><span class="sxs-lookup"><span data-stu-id="74f57-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="74f57-113">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="74f57-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="74f57-114">Options</span><span class="sxs-lookup"><span data-stu-id="74f57-114">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="74f57-115">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="74f57-115">Runs the tests in blame mode.</span></span> <span data-ttu-id="74f57-116">Cette option s’avère utile pour isoler les tests responsables du plantage de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="74f57-116">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="74f57-117">Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.</span><span class="sxs-lookup"><span data-stu-id="74f57-117">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <PATH_TO_LOG_FILE>`**

  <span data-ttu-id="74f57-118">Active les journaux détaillés de la plateforme de test.</span><span class="sxs-lookup"><span data-stu-id="74f57-118">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="74f57-119">Les journaux sont écrits dans le fichier fourni.</span><span class="sxs-lookup"><span data-stu-id="74f57-119">Logs are written to the provided file.</span></span>

- **`--Framework <FRAMEWORK>`**

  <span data-ttu-id="74f57-120">Version .NET Framework cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="74f57-120">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="74f57-121">Les valeurs valides sont, par exemple, `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="74f57-121">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="74f57-122">Les valeurs `Framework40`, `Framework45`, `FrameworkCore10` et `FrameworkUap10` sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="74f57-122">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="74f57-123">Exécute les tests dans un processus isolé.</span><span class="sxs-lookup"><span data-stu-id="74f57-123">Runs the tests in an isolated process.</span></span> <span data-ttu-id="74f57-124">De ce fait, il est moins probable que le processus *vstest.console.exe* soit arrêté sur une erreur dans les tests, mais les tests peuvent s’exécuter plus lentement.</span><span class="sxs-lookup"><span data-stu-id="74f57-124">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <FILE_NAME>`**

  <span data-ttu-id="74f57-125">Répertorie tous les tests découverts dans le conteneur de tests donné.</span><span class="sxs-lookup"><span data-stu-id="74f57-125">Lists all discovered tests from the given test container.</span></span>

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="74f57-126">Spécifiez un journal pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="74f57-126">Specify a logger for test results.</span></span>

  - <span data-ttu-id="74f57-127">Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :</span><span class="sxs-lookup"><span data-stu-id="74f57-127">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="74f57-128">Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`.</span><span class="sxs-lookup"><span data-stu-id="74f57-128">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="74f57-129">Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné.</span><span class="sxs-lookup"><span data-stu-id="74f57-129">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="74f57-130">Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.</span><span class="sxs-lookup"><span data-stu-id="74f57-130">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="74f57-131">Exécuter des tests en parallèle.</span><span class="sxs-lookup"><span data-stu-id="74f57-131">Run tests in parallel.</span></span> <span data-ttu-id="74f57-132">Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables.</span><span class="sxs-lookup"><span data-stu-id="74f57-132">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="74f57-133">Spécifier un nombre explicite `MaxCpuCount` de `RunConfiguration` cœurs en plaçant la propriété sous le nœud dans le fichier *runsettings.*</span><span class="sxs-lookup"><span data-stu-id="74f57-133">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <PROCESS_ID>`**

  <span data-ttu-id="74f57-134">ID du processus parent chargé de lancer le processus actif.</span><span class="sxs-lookup"><span data-stu-id="74f57-134">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <PLATFORM_TYPE>`**

  <span data-ttu-id="74f57-135">Architecture de plateforme cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="74f57-135">Target platform architecture used for test execution.</span></span> <span data-ttu-id="74f57-136">Les valeurs correctes sont `x86`, `x64` et `ARM`.</span><span class="sxs-lookup"><span data-stu-id="74f57-136">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <PORT>`**

  <span data-ttu-id="74f57-137">Spécifie le port de la connexion de socket et la réception des messages d’événement.</span><span class="sxs-lookup"><span data-stu-id="74f57-137">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PATH>`**

  <span data-ttu-id="74f57-138">Un répertoire de résultats de test sera créé dans le chemin d’accès spécifié s’il n’en existe pas.</span><span class="sxs-lookup"><span data-stu-id="74f57-138">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <SETTINGS_FILE>`**

  <span data-ttu-id="74f57-139">Paramètres à utiliser durant l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="74f57-139">Settings to use when running tests.</span></span>

- **`--TestAdapterPath <PATH>`**

  <span data-ttu-id="74f57-140">Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="74f57-140">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <EXPRESSION>`**

  <span data-ttu-id="74f57-141">Exécutez les tests qui correspondent à l'expression donnée.</span><span class="sxs-lookup"><span data-stu-id="74f57-141">Run tests that match the given expression.</span></span> <span data-ttu-id="74f57-142">`<EXPRESSION>` est au format `<property>Operator<value>[|&<EXPRESSION>]`, où l’opérateur est `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="74f57-142">`<EXPRESSION>` is of the format `<property>Operator<value>[|&<EXPRESSION>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="74f57-143">L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="74f57-143">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="74f57-144">Les parenthèses sont utilisées pour regrouper les `()` sous-exemples.</span><span class="sxs-lookup"><span data-stu-id="74f57-144">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="74f57-145">Pour plus d’informations, voir [filtre TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="74f57-145">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <TEST_NAMES>`**

  <span data-ttu-id="74f57-146">Exécutez les tests avec les noms qui correspondent aux valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="74f57-146">Run tests with names that match the provided values.</span></span> <span data-ttu-id="74f57-147">Séparez les valeurs par des virgules.</span><span class="sxs-lookup"><span data-stu-id="74f57-147">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="74f57-148">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="74f57-148">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="74f57-149">Lit le fichier réponse pour obtenir plus d’options.</span><span class="sxs-lookup"><span data-stu-id="74f57-149">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="74f57-150">Spécifie des arguments supplémentaires à passer à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="74f57-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="74f57-151">Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="74f57-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="74f57-152">Utilisez un espace pour séparer plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="74f57-152">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="74f57-153">Exemples</span><span class="sxs-lookup"><span data-stu-id="74f57-153">Examples</span></span>

<span data-ttu-id="74f57-154">Exécuter des tests dans *mytestproject.dll*:</span><span class="sxs-lookup"><span data-stu-id="74f57-154">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="74f57-155">Exécuter des tests dans *mytestproject.dll*, l’exportation vers le dossier personnalisé avec le nom personnalisé:</span><span class="sxs-lookup"><span data-stu-id="74f57-155">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="74f57-156">Exécuter des tests dans *mytestproject.dll* et *myothertestproject.exe:*</span><span class="sxs-lookup"><span data-stu-id="74f57-156">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="74f57-157">Exécuter des tests `TestMethod1` :</span><span class="sxs-lookup"><span data-stu-id="74f57-157">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="74f57-158">Exécuter des tests `TestMethod1` et `TestMethod2` :</span><span class="sxs-lookup"><span data-stu-id="74f57-158">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="74f57-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74f57-159">See also</span></span>

- [<span data-ttu-id="74f57-160">Options de ligne de commande VSTest.Console.exe</span><span class="sxs-lookup"><span data-stu-id="74f57-160">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
