---
title: Commande dotnet vstest
description: La commande dotnet vstest permet de générer un projet et l’ensemble de ses dépendances.
author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: 45fda3b34d2649bc6f20cf3f35c65277a9a53cec
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300030"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="500b7-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="500b7-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="500b7-104">Name</span><span class="sxs-lookup"><span data-stu-id="500b7-104">Name</span></span>

<span data-ttu-id="500b7-105">`dotnet-vstest` - Exécute les tests à partir des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="500b7-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="500b7-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="500b7-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="500b7-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="500b7-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="500b7-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="500b7-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="500b7-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="500b7-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="500b7-110">Description</span><span class="sxs-lookup"><span data-stu-id="500b7-110">Description</span></span>

<span data-ttu-id="500b7-111">La commande `dotnet-vstest` exécute l’application en ligne de commande `VSTest.Console` pour effectuer des tests unitaires automatisés.</span><span class="sxs-lookup"><span data-stu-id="500b7-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="500b7-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="500b7-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="500b7-113">Exécute les tests à partir des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="500b7-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="500b7-114">Séparez les noms d’assembly de test par des espaces.</span><span class="sxs-lookup"><span data-stu-id="500b7-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="500b7-115">Options</span><span class="sxs-lookup"><span data-stu-id="500b7-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="500b7-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="500b7-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="500b7-117">Paramètres à utiliser durant l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="500b7-118">Exécutez les tests avec les noms qui correspondent aux valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="500b7-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="500b7-119">Séparez les valeurs par des virgules.</span><span class="sxs-lookup"><span data-stu-id="500b7-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="500b7-120">Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="500b7-121">Architecture de plateforme cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="500b7-122">Les valeurs valides sont `x86`, `x64` et `ARM`.</span><span class="sxs-lookup"><span data-stu-id="500b7-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="500b7-123">Version .NET Framework cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="500b7-124">Les valeurs valides sont, par exemple, `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="500b7-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="500b7-125">Les valeurs `Framework40`, `Framework45`, `FrameworkCore10` et `FrameworkUap10` sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="500b7-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="500b7-126">Exécutez des tests en parallèle.</span><span class="sxs-lookup"><span data-stu-id="500b7-126">Execute tests in parallel.</span></span> <span data-ttu-id="500b7-127">Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables.</span><span class="sxs-lookup"><span data-stu-id="500b7-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="500b7-128">Spécifiez un nombre de cœurs explicite en définissant la propriété MaxCpuCount sous le nœud RunConfiguration du fichier runsettings.</span><span class="sxs-lookup"><span data-stu-id="500b7-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="500b7-129">Exécutez les tests qui correspondent à l'expression donnée.</span><span class="sxs-lookup"><span data-stu-id="500b7-129">Run tests that match the given expression.</span></span> <span data-ttu-id="500b7-130">`<Expression>` est au format `<property>Operator<value>[|&<Expression>]`, où l’opérateur est `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="500b7-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="500b7-131">L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="500b7-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="500b7-132">Les parenthèses `()` sont utilisées pour les sous-expressions de groupe.</span><span class="sxs-lookup"><span data-stu-id="500b7-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="500b7-133">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="500b7-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="500b7-134">Spécifiez un journal pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="500b7-135">Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :</span><span class="sxs-lookup"><span data-stu-id="500b7-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="500b7-136">Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`.</span><span class="sxs-lookup"><span data-stu-id="500b7-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="500b7-137">Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné.</span><span class="sxs-lookup"><span data-stu-id="500b7-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="500b7-138">Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="500b7-139">Répertorie tous les tests découverts dans le conteneur de tests donné.</span><span class="sxs-lookup"><span data-stu-id="500b7-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="500b7-140">ID du processus parent chargé de lancer le processus actif.</span><span class="sxs-lookup"><span data-stu-id="500b7-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="500b7-141">Spécifie le port de la connexion de socket et la réception des messages d’événement.</span><span class="sxs-lookup"><span data-stu-id="500b7-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="500b7-142">Active les journaux détaillés de la plateforme de test.</span><span class="sxs-lookup"><span data-stu-id="500b7-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="500b7-143">Les journaux sont écrits dans le fichier fourni.</span><span class="sxs-lookup"><span data-stu-id="500b7-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="500b7-144">Exécute les tests en mode responsable.</span><span class="sxs-lookup"><span data-stu-id="500b7-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="500b7-145">Cette option s’avère utile pour isoler les tests responsables du plantage de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="500b7-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="500b7-146">Elle crée un fichier de sortie dans le répertoire actif nommé *Sequence.xml* qui capture l’ordre d’exécution des tests avant le plantage.</span><span class="sxs-lookup"><span data-stu-id="500b7-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="500b7-147">Exécute les tests dans un processus isolé.</span><span class="sxs-lookup"><span data-stu-id="500b7-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="500b7-148">De ce fait, il est moins probable que le processus *vstest.console.exe* soit arrêté sur une erreur dans les tests, mais les tests peuvent s’exécuter plus lentement.</span><span class="sxs-lookup"><span data-stu-id="500b7-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="500b7-149">Lit le fichier réponse pour obtenir plus d’options.</span><span class="sxs-lookup"><span data-stu-id="500b7-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="500b7-150">Spécifie des arguments supplémentaires à passer à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="500b7-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="500b7-151">Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="500b7-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="500b7-152">Utilisez un espace pour séparer plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="500b7-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="500b7-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="500b7-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="500b7-154">Paramètres à utiliser durant l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="500b7-155">Exécutez les tests avec les noms qui correspondent aux valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="500b7-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="500b7-156">Séparez les valeurs par des virgules.</span><span class="sxs-lookup"><span data-stu-id="500b7-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="500b7-157">Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="500b7-158">Architecture de plateforme cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="500b7-159">Les valeurs valides sont `x86`, `x64` et `ARM`.</span><span class="sxs-lookup"><span data-stu-id="500b7-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="500b7-160">Version .NET Framework cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="500b7-161">Les valeurs valides sont, par exemple, `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="500b7-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="500b7-162">Les valeurs `Framework40`, `Framework45` et `FrameworkCore10` sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="500b7-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="500b7-163">Exécutez des tests en parallèle.</span><span class="sxs-lookup"><span data-stu-id="500b7-163">Execute tests in parallel.</span></span> <span data-ttu-id="500b7-164">Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables.</span><span class="sxs-lookup"><span data-stu-id="500b7-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="500b7-165">Spécifiez un nombre de cœurs explicite en définissant la propriété MaxCpuCount sous le nœud RunConfiguration du fichier runsettings.</span><span class="sxs-lookup"><span data-stu-id="500b7-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="500b7-166">Exécutez les tests qui correspondent à l'expression donnée.</span><span class="sxs-lookup"><span data-stu-id="500b7-166">Run tests that match the given expression.</span></span> <span data-ttu-id="500b7-167">`<Expression>` est au format `<property>Operator<value>[|&<Expression>]`, où l’opérateur est `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="500b7-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="500b7-168">L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="500b7-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="500b7-169">Les parenthèses `()` sont utilisées pour les sous-expressions de groupe.</span><span class="sxs-lookup"><span data-stu-id="500b7-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="500b7-170">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="500b7-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="500b7-171">Spécifiez un journal pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="500b7-172">Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :</span><span class="sxs-lookup"><span data-stu-id="500b7-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="500b7-173">Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`.</span><span class="sxs-lookup"><span data-stu-id="500b7-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="500b7-174">Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné.</span><span class="sxs-lookup"><span data-stu-id="500b7-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="500b7-175">Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="500b7-176">Répertorie tous les tests découverts dans le conteneur de tests donné.</span><span class="sxs-lookup"><span data-stu-id="500b7-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="500b7-177">ID du processus parent chargé de lancer le processus actif.</span><span class="sxs-lookup"><span data-stu-id="500b7-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="500b7-178">Spécifie le port de la connexion de socket et la réception des messages d’événement.</span><span class="sxs-lookup"><span data-stu-id="500b7-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="500b7-179">Active les journaux détaillés de la plateforme de test.</span><span class="sxs-lookup"><span data-stu-id="500b7-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="500b7-180">Les journaux sont écrits dans le fichier fourni.</span><span class="sxs-lookup"><span data-stu-id="500b7-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="500b7-181">Spécifie des arguments supplémentaires à passer à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="500b7-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="500b7-182">Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="500b7-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="500b7-183">Utilisez un espace pour séparer plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="500b7-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="500b7-184">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="500b7-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="500b7-185">Paramètres à utiliser durant l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="500b7-186">Exécutez les tests avec les noms qui correspondent aux valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="500b7-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="500b7-187">Séparez les valeurs par des virgules.</span><span class="sxs-lookup"><span data-stu-id="500b7-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="500b7-188">Utilisez des adaptateurs de test personnalisés à partir d’un chemin d’accès donné (le cas échéant) dans la série de tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="500b7-189">Architecture de plateforme cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="500b7-190">Les valeurs valides sont `x86`, `x64` et `ARM`.</span><span class="sxs-lookup"><span data-stu-id="500b7-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="500b7-191">Version .NET Framework cible utilisée pour l’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="500b7-192">Les valeurs valides sont, par exemple, `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="500b7-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="500b7-193">Les valeurs `Framework40`, `Framework45` et `FrameworkCore10` sont également prises en charge.</span><span class="sxs-lookup"><span data-stu-id="500b7-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="500b7-194">Exécutez des tests en parallèle.</span><span class="sxs-lookup"><span data-stu-id="500b7-194">Execute tests in parallel.</span></span> <span data-ttu-id="500b7-195">Par défaut, tous les cœurs disponibles sur l’ordinateur sont utilisables.</span><span class="sxs-lookup"><span data-stu-id="500b7-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="500b7-196">Spécifiez un nombre de cœurs explicite en définissant la propriété MaxCpuCount sous le nœud RunConfiguration du fichier runsettings.</span><span class="sxs-lookup"><span data-stu-id="500b7-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="500b7-197">Exécutez les tests qui correspondent à l'expression donnée.</span><span class="sxs-lookup"><span data-stu-id="500b7-197">Run tests that match the given expression.</span></span> <span data-ttu-id="500b7-198">`<Expression>` est au format `<property>Operator<value>[|&<Expression>]`, où l’opérateur est `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="500b7-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="500b7-199">L’opérateur `~` a une sémantique « contient » et est applicable aux propriétés de chaîne comme `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="500b7-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="500b7-200">Les parenthèses `()` sont utilisées pour les sous-expressions de groupe.</span><span class="sxs-lookup"><span data-stu-id="500b7-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="500b7-201">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="500b7-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="500b7-202">Spécifiez un journal pour les résultats de tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="500b7-203">Pour publier les résultats des tests dans Team Foundation Server, utilisez le fournisseur d’enregistreurs `TfsPublisher` :</span><span class="sxs-lookup"><span data-stu-id="500b7-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="500b7-204">Par exemple, pour stocker les résultats dans les fichiers de résultats des tests de Visual Studio (TRX), utilisez le fournisseur d’enregistreurs `trx`.</span><span class="sxs-lookup"><span data-stu-id="500b7-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="500b7-205">Cette commutation crée un fichier dans le répertoire des résultats des tests avec un nom de fichier journal donné.</span><span class="sxs-lookup"><span data-stu-id="500b7-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="500b7-206">Si `LogFileName` n’est pas fourni, un nom de fichier unique est créé pour stocker les résultats des tests.</span><span class="sxs-lookup"><span data-stu-id="500b7-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="500b7-207">Répertorie tous les tests découverts dans le conteneur de tests donné.</span><span class="sxs-lookup"><span data-stu-id="500b7-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="500b7-208">ID du processus parent chargé de lancer le processus actif.</span><span class="sxs-lookup"><span data-stu-id="500b7-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="500b7-209">Spécifie le port de la connexion de socket et la réception des messages d’événement.</span><span class="sxs-lookup"><span data-stu-id="500b7-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="500b7-210">Active les journaux détaillés de la plateforme de test.</span><span class="sxs-lookup"><span data-stu-id="500b7-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="500b7-211">Les journaux sont écrits dans le fichier fourni.</span><span class="sxs-lookup"><span data-stu-id="500b7-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="500b7-212">Spécifie des arguments supplémentaires à passer à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="500b7-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="500b7-213">Les arguments sont spécifiés sous forme de paires nom-valeur du type `<n>=<v>`, où `<n>` est le nom d’argument et `<v>` la valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="500b7-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="500b7-214">Utilisez un espace pour séparer plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="500b7-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="500b7-215">Exemples</span><span class="sxs-lookup"><span data-stu-id="500b7-215">Examples</span></span>

<span data-ttu-id="500b7-216">Exécuter des tests dans `mytestproject.dll` :</span><span class="sxs-lookup"><span data-stu-id="500b7-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="500b7-217">Exécuter des tests dans `mytestproject.dll`, en exportant vers un dossier personnalisé avec un nom personnalisé :</span><span class="sxs-lookup"><span data-stu-id="500b7-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="500b7-218">Exécuter des tests dans `mytestproject.dll` et `myothertestproject.exe` :</span><span class="sxs-lookup"><span data-stu-id="500b7-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="500b7-219">Exécuter des tests `TestMethod1` :</span><span class="sxs-lookup"><span data-stu-id="500b7-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="500b7-220">Exécuter des tests `TestMethod1` et `TestMethod2` :</span><span class="sxs-lookup"><span data-stu-id="500b7-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
