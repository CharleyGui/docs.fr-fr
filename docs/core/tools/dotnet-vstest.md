---
title: Commande dotnet vstest
description: La commande dotnet vstest permet de générer un projet et l’ensemble de ses dépendances.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156931"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="5325a-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="5325a-103">dotnet vstest</span></span>

<span data-ttu-id="5325a-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="5325a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5325a-105">Nom</span><span class="sxs-lookup"><span data-stu-id="5325a-105">Name</span></span>

<span data-ttu-id="5325a-106">`dotnet-vstest` - Exécute les tests à partir des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="5325a-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5325a-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="5325a-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a><span data-ttu-id="5325a-108">Description</span><span class="sxs-lookup"><span data-stu-id="5325a-108">Description</span></span>

<span data-ttu-id="5325a-109">La commande `dotnet-vstest` exécute l’application en ligne de commande `VSTest.Console` pour effectuer des tests unitaires automatisés.</span><span class="sxs-lookup"><span data-stu-id="5325a-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="5325a-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="5325a-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="5325a-111">Exécute les tests à partir des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="5325a-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="5325a-112">Séparez les noms d’assembly de test par des espaces.</span><span class="sxs-lookup"><span data-stu-id="5325a-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="5325a-113">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5325a-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="5325a-114">Options</span><span class="sxs-lookup"><span data-stu-id="5325a-114">Options</span></span>

- **`--Settings <Settings File>`**

  <span data-ttu-id="5325a-115">Paramètres à utiliser durant l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="5325a-115">Settings to use when running tests.</span></span>

- **`--Tests <Test Names>`**

  <span data-ttu-id="5325a-116">Exécutez les tests avec les noms qui correspondent aux valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="5325a-116">Run tests with names that match the provided values.</span></span> <span data-ttu-id="5325a-117">Séparez les valeurs par des virgules.</span><span class="sxs-lookup"><span data-stu-id="5325a-117">Separate multiple values with commas.</span></span>

- **`--TestAdapterPath`**

  <span data-ttu-id="5325a-118">Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="5325a-118">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--Platform <Platform type>`**

  <span data-ttu-id="5325a-119">Architecture de plateforme cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="5325a-119">Target platform architecture used for test execution.</span></span> <span data-ttu-id="5325a-120">Les valeurs correctes sont `x86`, `x64` et `ARM`.</span><span class="sxs-lookup"><span data-stu-id="5325a-120">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Framework <Framework Version>`**

  <span data-ttu-id="5325a-121">Version .NET Framework cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="5325a-121">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="5325a-122">Les valeurs valides sont, par exemple, `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="5325a-122">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="5325a-123">Les valeurs `Framework40`, `Framework45`, `FrameworkCore10` et `FrameworkUap10` sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="5325a-123">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--Parallel`**

  <span data-ttu-id="5325a-124">Exécuter les tests en parallèle.</span><span class="sxs-lookup"><span data-stu-id="5325a-124">Run tests in parallel.</span></span> <span data-ttu-id="5325a-125">Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables.</span><span class="sxs-lookup"><span data-stu-id="5325a-125">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="5325a-126">Spécifiez un nombre de cœurs explicite en définissant la propriété `MaxCpuCount` sous le nœud `RunConfiguration` dans le fichier *RunSettings* .</span><span class="sxs-lookup"><span data-stu-id="5325a-126">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--TestCaseFilter <Expression>`**

  <span data-ttu-id="5325a-127">Exécutez les tests qui correspondent à l'expression donnée.</span><span class="sxs-lookup"><span data-stu-id="5325a-127">Run tests that match the given expression.</span></span> <span data-ttu-id="5325a-128">`<Expression>` est au format `<property>Operator<value>[|&<Expression>]`, où l’opérateur est `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="5325a-128">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="5325a-129">L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="5325a-129">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="5325a-130">Les parenthèses `()` sont utilisées pour regrouper les sous-expressions.</span><span class="sxs-lookup"><span data-stu-id="5325a-130">Parenthesis `()` are used to group subexpressions.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="5325a-131">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="5325a-131">Prints out a short help for the command.</span></span>

- **`--logger <Logger Uri/FriendlyName>`**

  <span data-ttu-id="5325a-132">Spécifiez un journal pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="5325a-132">Specify a logger for test results.</span></span>

  - <span data-ttu-id="5325a-133">Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :</span><span class="sxs-lookup"><span data-stu-id="5325a-133">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="5325a-134">Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`.</span><span class="sxs-lookup"><span data-stu-id="5325a-134">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="5325a-135">Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné.</span><span class="sxs-lookup"><span data-stu-id="5325a-135">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="5325a-136">Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.</span><span class="sxs-lookup"><span data-stu-id="5325a-136">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  <span data-ttu-id="5325a-137">Répertorie tous les tests découverts dans le conteneur de tests donné.</span><span class="sxs-lookup"><span data-stu-id="5325a-137">Lists all discovered tests from the given test container.</span></span>

- **`--ParentProcessId <ParentProcessId>`**

  <span data-ttu-id="5325a-138">ID du processus parent chargé de lancer le processus actif.</span><span class="sxs-lookup"><span data-stu-id="5325a-138">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Port <Port>`**

  <span data-ttu-id="5325a-139">Spécifie le port de la connexion de socket et la réception des messages d’événement.</span><span class="sxs-lookup"><span data-stu-id="5325a-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--Diag <Path to log file>`**

  <span data-ttu-id="5325a-140">Active les journaux détaillés de la plateforme de test.</span><span class="sxs-lookup"><span data-stu-id="5325a-140">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="5325a-141">Les journaux sont écrits dans le fichier fourni.</span><span class="sxs-lookup"><span data-stu-id="5325a-141">Logs are written to the provided file.</span></span>

- **`--Blame`**

  <span data-ttu-id="5325a-142">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="5325a-142">Runs the tests in blame mode.</span></span> <span data-ttu-id="5325a-143">Cette option s’avère utile pour isoler les tests responsables du plantage de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="5325a-143">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="5325a-144">Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.</span><span class="sxs-lookup"><span data-stu-id="5325a-144">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="5325a-145">Exécute les tests dans un processus isolé.</span><span class="sxs-lookup"><span data-stu-id="5325a-145">Runs the tests in an isolated process.</span></span> <span data-ttu-id="5325a-146">De ce fait, il est moins probable que le processus *vstest.console.exe* soit arrêté sur une erreur dans les tests, mais les tests peuvent s’exécuter plus lentement.</span><span class="sxs-lookup"><span data-stu-id="5325a-146">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`@<file>`**

  <span data-ttu-id="5325a-147">Lit le fichier réponse pour obtenir plus d’options.</span><span class="sxs-lookup"><span data-stu-id="5325a-147">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="5325a-148">Spécifie des arguments supplémentaires à passer à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="5325a-148">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="5325a-149">Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="5325a-149">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="5325a-150">Utilisez un espace pour séparer plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="5325a-150">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="5325a-151">Exemples</span><span class="sxs-lookup"><span data-stu-id="5325a-151">Examples</span></span>

<span data-ttu-id="5325a-152">Exécuter les tests dans *MyTestProject. dll*:</span><span class="sxs-lookup"><span data-stu-id="5325a-152">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="5325a-153">Exécutez les tests dans *MyTestProject. dll*, en les exportant vers un dossier personnalisé avec un nom personnalisé :</span><span class="sxs-lookup"><span data-stu-id="5325a-153">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="5325a-154">Exécuter les tests dans *MyTestProject. dll* et *myothertestproject. exe*:</span><span class="sxs-lookup"><span data-stu-id="5325a-154">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="5325a-155">Exécuter des tests `TestMethod1` :</span><span class="sxs-lookup"><span data-stu-id="5325a-155">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="5325a-156">Exécuter des tests `TestMethod1` et `TestMethod2` :</span><span class="sxs-lookup"><span data-stu-id="5325a-156">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
