---
title: Construire une application .NET pour Apache Spark sur Windows
description: Découvrez comment construire votre application .NET pour Apache Spark sur Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: cb7154185fc9aa08bc447cb846798995301a6651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185758"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="47215-103">Apprenez à construire votre application .NET pour Apache Spark sur Windows</span><span class="sxs-lookup"><span data-stu-id="47215-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="47215-104">Cet article vous apprend à construire votre .NET pour les applications Apache Spark sur Windows.</span><span class="sxs-lookup"><span data-stu-id="47215-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="47215-105">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="47215-105">Prerequisites</span></span>

<span data-ttu-id="47215-106">Si vous avez déjà toutes les conditions préalables suivantes, sautez aux étapes [de construction.](#build)</span><span class="sxs-lookup"><span data-stu-id="47215-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="47215-107">Téléchargez et installez le **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - `dotnet` l’installation du SDK ajoutera la chaîne à outils à votre chemin.</span><span class="sxs-lookup"><span data-stu-id="47215-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="47215-108">.NET Core 2.1, 2.2 et 3.1 sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="47215-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="47215-109">Installez **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 ou plus tard).</span><span class="sxs-lookup"><span data-stu-id="47215-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="47215-110">La version Communautaire est entièrement gratuite.</span><span class="sxs-lookup"><span data-stu-id="47215-110">The Community version is completely free.</span></span> <span data-ttu-id="47215-111">Lors de la configuration de votre installation, inclure ces composants au minimum:</span><span class="sxs-lookup"><span data-stu-id="47215-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="47215-112">Développement .NET Desktop</span><span class="sxs-lookup"><span data-stu-id="47215-112">.NET desktop development</span></span>
       * <span data-ttu-id="47215-113">Tous les composants requis</span><span class="sxs-lookup"><span data-stu-id="47215-113">All Required Components</span></span>
         * <span data-ttu-id="47215-114">Outils de développement .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="47215-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="47215-115">Développement multiplateforme .NET Core</span><span class="sxs-lookup"><span data-stu-id="47215-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="47215-116">Tous les composants requis</span><span class="sxs-lookup"><span data-stu-id="47215-116">All Required Components</span></span>
  3. <span data-ttu-id="47215-117">Installer **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span><span class="sxs-lookup"><span data-stu-id="47215-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span>
     - <span data-ttu-id="47215-118">Sélectionnez la version appropriée pour votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="47215-118">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="47215-119">Par exemple, *jdk-8u201-windows-x64.exe* pour Windows x64 machine.</span><span class="sxs-lookup"><span data-stu-id="47215-119">For example, *jdk-8u201-windows-x64.exe* for Windows x64 machine.</span></span>
     - <span data-ttu-id="47215-120">Installez à l’aide de `java` l’installateur et vérifiez que vous êtes en mesure de courir à partir de votre ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="47215-120">Install using the installer and verify you are able to run `java` from your command line.</span></span>
  4. <span data-ttu-id="47215-121">Installer **[Apache Maven 3.6.0 .](https://maven.apache.org/download.cgi)**</span><span class="sxs-lookup"><span data-stu-id="47215-121">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="47215-122">Téléchargez [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="47215-122">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span></span>
     - <span data-ttu-id="47215-123">Extrayez-le dans un répertoire local.</span><span class="sxs-lookup"><span data-stu-id="47215-123">Extract to a local directory.</span></span> <span data-ttu-id="47215-124">Par exemple, 'C:'bin’apache-maven-3.6.0\*.</span><span class="sxs-lookup"><span data-stu-id="47215-124">For example, \*C:\bin\apache-maven-3.6.0\*.</span></span>
     - <span data-ttu-id="47215-125">Ajoutez Apache Maven à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="47215-125">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="47215-126">Par exemple, *C: 'bin’apache-maven-3.6.0'bin*.</span><span class="sxs-lookup"><span data-stu-id="47215-126">For example, *C:\bin\apache-maven-3.6.0\bin*.</span></span>
     - <span data-ttu-id="47215-127">Vérifiez que vous `mvn` êtes en mesure de courir à partir de votre ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="47215-127">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="47215-128">Installez **[Apache Spark 2.3 .](https://spark.apache.org/downloads.html)**</span><span class="sxs-lookup"><span data-stu-id="47215-128">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="47215-129">Téléchargez [Apache Spark 2.3 et](https://spark.apache.org/downloads.html) extrait dans un dossier local (par exemple, *C: 'bin’spark-2.3.2-bin-hadoop2.7\*) à l’aide de [7 zip](https://www.7-zip.org/). (Les versions d’étincelles prises en charge sont 2.3.*, 2.4.0, 2.4.1, 2.4.3 et 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="47215-129">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (for example, *C:\bin\spark-2.3.2-bin-hadoop2.7\*) using [7-zip](https://www.7-zip.org/). (The supported spark versions are 2.3.*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>
     - <span data-ttu-id="47215-130">Ajouter une nouvelle `SPARK_HOME` [variable d’environnement](https://www.java.com/en/download/help/path.xml) .</span><span class="sxs-lookup"><span data-stu-id="47215-130">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`.</span></span> <span data-ttu-id="47215-131">Par exemple, 'C:'bin’spark-2.3.2-bin-hadoop2.7\*.</span><span class="sxs-lookup"><span data-stu-id="47215-131">For example, \*C:\bin\spark-2.3.2-bin-hadoop2.7\*.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - <span data-ttu-id="47215-132">Ajoutez Apache Spark à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="47215-132">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="47215-133">Par exemple, *C: 'bin’spark-2.3.2-bin-hadoop2.7'bin*.</span><span class="sxs-lookup"><span data-stu-id="47215-133">For example, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.</span></span>

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - <span data-ttu-id="47215-134">Vérifiez que vous `spark-shell` êtes en mesure de courir à partir de votre ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="47215-134">Verify you are able to run `spark-shell` from your command-line.</span></span>
        <span data-ttu-id="47215-135">Sortie de la console d’échantillon :</span><span class="sxs-lookup"><span data-stu-id="47215-135">Sample console output:</span></span>

        ```
        Welcome to
              ____              __
             / __/__  ___ _____/ /__
            _\ \/ _ \/ _ `/ __/  '_/
           /___/ .__/\_,_/_/ /_/\_\   version 2.3.2
              /_/

        Using Scala version 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
        Type in expressions to have them evaluated.
        Type :help for more information.

        scala> sc
        res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
        ```

        </details>

  6. <span data-ttu-id="47215-136">Installer **[WinUtils](https://github.com/steveloughran/winutils)**.</span><span class="sxs-lookup"><span data-stu-id="47215-136">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="47215-137">Télécharger `winutils.exe` binaire à partir du [référentiel WinUtils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="47215-137">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="47215-138">Vous devez sélectionner la version de Hadoop la distribution Spark a été compilée avec.</span><span class="sxs-lookup"><span data-stu-id="47215-138">You should select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="47215-139">Pour l’examen, utilisez hadoop-2.7.1 pour Spark 2.3.2.</span><span class="sxs-lookup"><span data-stu-id="47215-139">For exammple, use hadoop-2.7.1 for Spark 2.3.2.</span></span>
     - <span data-ttu-id="47215-140">Enregistrer `winutils.exe` binaire à un répertoire de votre choix.</span><span class="sxs-lookup"><span data-stu-id="47215-140">Save `winutils.exe` binary to a directory of your choice.</span></span> <span data-ttu-id="47215-141">Par exemple, *C: hadoop-bin*.</span><span class="sxs-lookup"><span data-stu-id="47215-141">For example, *C:\hadoop\bin*.</span></span>
     - <span data-ttu-id="47215-142">Définir `HADOOP_HOME` pour refléter le répertoire avec winutils.exe (sans bac).</span><span class="sxs-lookup"><span data-stu-id="47215-142">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="47215-143">Par exemple, à l’aide de la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="47215-143">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="47215-144">Définir path variable `%HADOOP_HOME%\bin`de l’environnement pour inclure .</span><span class="sxs-lookup"><span data-stu-id="47215-144">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="47215-145">Par exemple, à l’aide de la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="47215-145">For instance, using command line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="47215-146">Assurez-vous que vous `dotnet` `java`êtes `mvn` `spark-shell` en mesure d’exécuter , , à partir de votre ligne de commande avant de passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="47215-146">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span> <span data-ttu-id="47215-147">Vous pensez qu’il y a une meilleure façon?</span><span class="sxs-lookup"><span data-stu-id="47215-147">Feel there is a better way?</span></span> <span data-ttu-id="47215-148">[Ouvrez un problème](https://github.com/dotnet/spark/issues) et n’hésitez pas à contribuer.</span><span class="sxs-lookup"><span data-stu-id="47215-148">[Open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="47215-149">Une nouvelle instance de la ligne de commande peut être nécessaire si des variables de l’environnement ont été mises à jour.</span><span class="sxs-lookup"><span data-stu-id="47215-149">A new instance of the command line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="47215-150">Build</span><span class="sxs-lookup"><span data-stu-id="47215-150">Build</span></span>

<span data-ttu-id="47215-151">Pour le reste de ce guide, vous aurez besoin d’avoir cloné le référentiel .NET pour Apache Spark dans votre machine.</span><span class="sxs-lookup"><span data-stu-id="47215-151">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="47215-152">Vous pouvez choisir n’importe quel emplacement pour le référentiel cloné.</span><span class="sxs-lookup"><span data-stu-id="47215-152">You can choose any location for the cloned repository.</span></span> <span data-ttu-id="47215-153">Par exemple, 'C:'github’dotnet-spark\*.</span><span class="sxs-lookup"><span data-stu-id="47215-153">For example, \*C:\github\dotnet-spark\*.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="47215-154">Construire .NET pour Apache Spark Scala extensions couche</span><span class="sxs-lookup"><span data-stu-id="47215-154">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="47215-155">Lorsque vous soumettez une demande .NET, .NET pour Apache Spark a la logique nécessaire écrite dans Scala qui informe Apache Spark comment traiter vos demandes (par exemple, la demande de créer une nouvelle session Spark, demander de transférer des données de côté .NET côté JVM, etc.).</span><span class="sxs-lookup"><span data-stu-id="47215-155">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (for example, request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="47215-156">Cette logique peut être trouvée dans le [.NET pour Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span><span class="sxs-lookup"><span data-stu-id="47215-156">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="47215-157">Peu importe si vous utilisez .NET Framework ou .NET Core, vous aurez besoin de construire le .NET pour Apache Spark Scala couche d’extension:</span><span class="sxs-lookup"><span data-stu-id="47215-157">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package
```

<span data-ttu-id="47215-158">Vous devriez voir LES créés pour les versions Spark prises en charge :</span><span class="sxs-lookup"><span data-stu-id="47215-158">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="47215-159">Construire le .NET pour les applications d’échantillons Spark</span><span class="sxs-lookup"><span data-stu-id="47215-159">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="47215-160">Cette section explique comment construire les [applications d’échantillon](https://github.com/dotnet/spark/tree/master/examples) pour .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="47215-160">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="47215-161">Ces étapes aideront à comprendre le processus global de construction pour n’importe quel .NET pour l’application Spark.</span><span class="sxs-lookup"><span data-stu-id="47215-161">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="47215-162">Utilisation de Visual Studio pour .NET Framework</span><span class="sxs-lookup"><span data-stu-id="47215-162">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="47215-163">Ouvrez `src\csharp\Microsoft.Spark.sln` en Visual `Microsoft.Spark.CSharp.Examples` Studio et `examples` construisez le projet sous le dossier (ce qui permettra à son tour de construire le projet de liaisons .NET ainsi).</span><span class="sxs-lookup"><span data-stu-id="47215-163">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="47215-164">Si vous le souhaitez, vous pouvez `Microsoft.Spark.Examples` écrire votre propre code dans le projet (le «input_file.json» dans cet exemple est un fichier json avec les données que vous voulez créer le dataframe avec):</span><span class="sxs-lookup"><span data-stu-id="47215-164">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     <span data-ttu-id="47215-165">Une fois la construction réussie, vous verrez les binaires appropriés produits dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="47215-165">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>
     <span data-ttu-id="47215-166">Sortie de la console d’échantillon :</span><span class="sxs-lookup"><span data-stu-id="47215-166">Sample console output:</span></span>

      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="47215-167">Utilisation de .NET Core CLI pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="47215-167">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="47215-168">Nous travaillons actuellement sur l’automatisation .NET Core construit pour Spark .NET.</span><span class="sxs-lookup"><span data-stu-id="47215-168">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="47215-169">Jusque-là, nous apprécions votre patience dans l’exécution de certaines des étapes manuellement.</span><span class="sxs-lookup"><span data-stu-id="47215-169">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="47215-170">Construire le travailleur:</span><span class="sxs-lookup"><span data-stu-id="47215-170">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      <span data-ttu-id="47215-171">Sortie de la console d’échantillon :</span><span class="sxs-lookup"><span data-stu-id="47215-171">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish\
      ```

  2. <span data-ttu-id="47215-172">Construire les échantillons:</span><span class="sxs-lookup"><span data-stu-id="47215-172">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      <span data-ttu-id="47215-173">Sortie de la console d’échantillon :</span><span class="sxs-lookup"><span data-stu-id="47215-173">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="47215-174">Exécuter le .NET pour les applications d’échantillons Spark</span><span class="sxs-lookup"><span data-stu-id="47215-174">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="47215-175">Une fois que vous construisez `spark-submit` les échantillons, les exécuter sera à travers indépendamment du fait que vous ciblez .NET Framework ou .NET Core.</span><span class="sxs-lookup"><span data-stu-id="47215-175">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="47215-176">Assurez-vous d’avoir suivi la section [préalables](#prerequisites) et installé Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="47215-176">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="47215-177">Définissez `DOTNET_WORKER_DIR` `PATH` la variable ou l’environnement pour inclure le chemin où le `Microsoft.Spark.Worker` binaire a été généré (par exemple, *C: 'github’dotnet’sparks’artifacts-microsoft.Spark.Worker’Debug’net461* pour .NET Framework, *C:'github’dotnet-sparks’ts-Microsoft.Spark.Worker’Debug’netcoreapp2.1-win10-x64*</span><span class="sxs-lookup"><span data-stu-id="47215-177">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. <span data-ttu-id="47215-178">Ouvrez Powershell et rendez-vous à l’annuaire où votre application binaire a été générée (par exemple, *C : 'github’dotnet’spark’artefacts-bin-Microsoft.Spark.CSharp.Examples-Debug-net461* pour .NET Framework, *C:'github’dotnet-spark’artifacts-microsoft.Spark.CSharp.Examples-Debug-netcoreapp2.1-win10-x64 publish.NET* Core)</span><span class="sxs-lookup"><span data-stu-id="47215-178">Open Powershell and go to the directory where your app binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. <span data-ttu-id="47215-179">L’exécution de votre application suit la structure de base :</span><span class="sxs-lookup"><span data-stu-id="47215-179">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="47215-180">Voici quelques exemples que vous pouvez exécuter :</span><span class="sxs-lookup"><span data-stu-id="47215-180">Here are some examples you can run:</span></span>

     - <span data-ttu-id="47215-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="47215-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="47215-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount (en anglais seulement)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="47215-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="47215-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="47215-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="47215-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars fournis)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="47215-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
