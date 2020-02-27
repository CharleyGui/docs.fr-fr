---
title: Créer une application .NET pour Apache Spark sur Windows
description: Apprenez à créer votre application .NET pour Apache Spark sur Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: 640459c8c80b6d798718b89d4965802cdacd6c63
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628655"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="21e37-103">Apprenez à créer votre application .NET pour Apache Spark sur Windows</span><span class="sxs-lookup"><span data-stu-id="21e37-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="21e37-104">Cet article vous apprend à créer votre .NET pour les applications Apache Spark sur Windows.</span><span class="sxs-lookup"><span data-stu-id="21e37-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21e37-105">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="21e37-105">Prerequisites</span></span>

<span data-ttu-id="21e37-106">Si vous disposez déjà de toutes les conditions préalables suivantes, passez aux étapes de [génération](#build) .</span><span class="sxs-lookup"><span data-stu-id="21e37-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="21e37-107">Télécharger et installer le **[Kit SDK .net Core](https://dotnet.microsoft.com/download/dotnet-core/2.1)** : l’installation du kit de développement logiciel (SDK) ajoute les chaîne d’outils `dotnet` à votre chemin.</span><span class="sxs-lookup"><span data-stu-id="21e37-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="21e37-108">.NET Core 2,1, 2,2 et 3,1 sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="21e37-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="21e37-109">Installez **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (version 16,3 ou ultérieure).</span><span class="sxs-lookup"><span data-stu-id="21e37-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="21e37-110">La version de la communauté est entièrement gratuite.</span><span class="sxs-lookup"><span data-stu-id="21e37-110">The Community version is completely free.</span></span> <span data-ttu-id="21e37-111">Lors de la configuration de votre installation, incluez au minimum les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="21e37-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="21e37-112">Développement .NET Desktop</span><span class="sxs-lookup"><span data-stu-id="21e37-112">.NET desktop development</span></span>
       * <span data-ttu-id="21e37-113">Tous les composants requis</span><span class="sxs-lookup"><span data-stu-id="21e37-113">All Required Components</span></span>
         * <span data-ttu-id="21e37-114">Outils de développement .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="21e37-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="21e37-115">Développement multiplateforme .NET Core</span><span class="sxs-lookup"><span data-stu-id="21e37-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="21e37-116">Tous les composants requis</span><span class="sxs-lookup"><span data-stu-id="21e37-116">All Required Components</span></span>
  3. <span data-ttu-id="21e37-117">Installez **[Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)** .</span><span class="sxs-lookup"><span data-stu-id="21e37-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span> 
     - <span data-ttu-id="21e37-118">Sélectionnez la version appropriée pour votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="21e37-118">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="21e37-119">Par exemple, *JDK-8u201-Windows-x64. exe* pour Windows x64 machine.</span><span class="sxs-lookup"><span data-stu-id="21e37-119">For example, *jdk-8u201-windows-x64.exe* for Windows x64 machine.</span></span>
     - <span data-ttu-id="21e37-120">Installez à l’aide du programme d’installation et vérifiez que vous pouvez exécuter `java` à partir de votre ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="21e37-120">Install using the installer and verify you are able to run `java` from your command line.</span></span>
  4. <span data-ttu-id="21e37-121">Installez **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)** .</span><span class="sxs-lookup"><span data-stu-id="21e37-121">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="21e37-122">Téléchargez [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="21e37-122">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span></span>
     - <span data-ttu-id="21e37-123">Extrayez-le dans un répertoire local.</span><span class="sxs-lookup"><span data-stu-id="21e37-123">Extract to a local directory.</span></span> <span data-ttu-id="21e37-124">Par exemple, \* C:\bin\apache-Maven-3.6.0\*.</span><span class="sxs-lookup"><span data-stu-id="21e37-124">For example, \*C:\bin\apache-maven-3.6.0\*.</span></span>
     - <span data-ttu-id="21e37-125">Ajoutez Apache Maven à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="21e37-125">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="21e37-126">Par exemple, *C:\bin\apache-Maven-3.6.0\Bin*.</span><span class="sxs-lookup"><span data-stu-id="21e37-126">For example, *C:\bin\apache-maven-3.6.0\bin*.</span></span>
     - <span data-ttu-id="21e37-127">Vérifiez que vous pouvez exécuter `mvn` à partir de votre ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="21e37-127">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="21e37-128">Installez **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)** .</span><span class="sxs-lookup"><span data-stu-id="21e37-128">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="21e37-129">Téléchargez [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) et extrayez-le dans un dossier local (par exemple, *C:\bin\spark-2.3.2-bin-hadoop2.7\*) à l’aide de [7-zip](https://www.7-zip.org/). (Les versions Spark prises en charge sont 2,3.* , 2.4.0, 2.4.1, 2.4.3 et 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="21e37-129">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (for example, *C:\bin\spark-2.3.2-bin-hadoop2.7\*) using [7-zip](https://www.7-zip.org/). (The supported spark versions are 2.3.*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>
     - <span data-ttu-id="21e37-130">Ajoutez une [nouvelle variable d’environnement](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`.</span><span class="sxs-lookup"><span data-stu-id="21e37-130">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`.</span></span> <span data-ttu-id="21e37-131">Par exemple, \* C:\bin\spark-2.3.2-bin-hadoop2.7\*.</span><span class="sxs-lookup"><span data-stu-id="21e37-131">For example, \*C:\bin\spark-2.3.2-bin-hadoop2.7\*.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\       
       ```

     - <span data-ttu-id="21e37-132">Ajoutez Apache Spark à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="21e37-132">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="21e37-133">Par exemple, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.</span><span class="sxs-lookup"><span data-stu-id="21e37-133">For example, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.</span></span>

       ```powershell       
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```
     
     - <span data-ttu-id="21e37-134">Vérifiez que vous pouvez exécuter `spark-shell` à partir de votre ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="21e37-134">Verify you are able to run `spark-shell` from your command-line.</span></span>        
        <span data-ttu-id="21e37-135">Exemple de sortie de console :</span><span class="sxs-lookup"><span data-stu-id="21e37-135">Sample console output:</span></span>

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

  6. <span data-ttu-id="21e37-136">Installez **[winutils](https://github.com/steveloughran/winutils)** .</span><span class="sxs-lookup"><span data-stu-id="21e37-136">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="21e37-137">Téléchargez `winutils.exe` fichier binaire à partir du [référentiel winutils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="21e37-137">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="21e37-138">Vous devez sélectionner la version de Hadoop avec laquelle la distribution Spark a été compilée.</span><span class="sxs-lookup"><span data-stu-id="21e37-138">You should select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="21e37-139">Pour exammple, utilisez Hadoop-2.7.1 pour Spark 2.3.2.</span><span class="sxs-lookup"><span data-stu-id="21e37-139">For exammple, use hadoop-2.7.1 for Spark 2.3.2.</span></span>
     - <span data-ttu-id="21e37-140">Enregistrez `winutils.exe` fichier binaire dans le répertoire de votre choix.</span><span class="sxs-lookup"><span data-stu-id="21e37-140">Save `winutils.exe` binary to a directory of your choice.</span></span> <span data-ttu-id="21e37-141">Par exemple, *C:\hadoop\bin*.</span><span class="sxs-lookup"><span data-stu-id="21e37-141">For example, *C:\hadoop\bin*.</span></span>
     - <span data-ttu-id="21e37-142">Définissez `HADOOP_HOME` pour refléter le répertoire avec winutils. exe (sans bin).</span><span class="sxs-lookup"><span data-stu-id="21e37-142">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="21e37-143">Par exemple, à l’aide de la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="21e37-143">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="21e37-144">Définissez la variable d’environnement PATH pour inclure `%HADOOP_HOME%\bin`.</span><span class="sxs-lookup"><span data-stu-id="21e37-144">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="21e37-145">Par exemple, à l’aide de la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="21e37-145">For instance, using command line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="21e37-146">Assurez-vous que vous êtes en mesure d’exécuter `dotnet`, `java`, `mvn`, `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="21e37-146">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span> <span data-ttu-id="21e37-147">Vous avez l’impression d’avoir une meilleure solution ?</span><span class="sxs-lookup"><span data-stu-id="21e37-147">Feel there is a better way?</span></span> <span data-ttu-id="21e37-148">[Ouvrez un problème](https://github.com/dotnet/spark/issues) et n’hésitez pas à contribuer.</span><span class="sxs-lookup"><span data-stu-id="21e37-148">[Open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="21e37-149">Une nouvelle instance de la ligne de commande peut être requise si des variables d’environnement ont été mises à jour.</span><span class="sxs-lookup"><span data-stu-id="21e37-149">A new instance of the command line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="21e37-150">Build</span><span class="sxs-lookup"><span data-stu-id="21e37-150">Build</span></span>

<span data-ttu-id="21e37-151">Pour le reste de ce guide, vous devez avoir cloné le .NET pour Apache Spark référentiel sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="21e37-151">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="21e37-152">Vous pouvez choisir n’importe quel emplacement pour le référentiel cloné.</span><span class="sxs-lookup"><span data-stu-id="21e37-152">You can choose any location for the cloned repository.</span></span> <span data-ttu-id="21e37-153">Par exemple, \* C:\github\dotnet-Spark\*.</span><span class="sxs-lookup"><span data-stu-id="21e37-153">For example, \*C:\github\dotnet-spark\*.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="21e37-154">Build .NET pour Apache Spark couche d’extensions Scala</span><span class="sxs-lookup"><span data-stu-id="21e37-154">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="21e37-155">Lorsque vous soumettez une application .NET, .NET pour Apache Spark a la logique nécessaire écrite en Scala qui informe Apache Spark de la gestion de vos demandes (par exemple, la demande de création d’une nouvelle session Spark, la demande de transfert des données du côté .NET vers JVM, etc.).</span><span class="sxs-lookup"><span data-stu-id="21e37-155">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (for example, request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="21e37-156">Cette logique se trouve dans le [.net pour le code source Scala Spark](https://github.com/dotnet/spark/tree/master/src/scala).</span><span class="sxs-lookup"><span data-stu-id="21e37-156">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="21e37-157">Que vous utilisiez .NET Framework ou .NET Core, vous devrez générer le .NET pour la couche d’extension Scala Apache Spark :</span><span class="sxs-lookup"><span data-stu-id="21e37-157">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package 
```

<span data-ttu-id="21e37-158">Vous devez voir les fichiers jar créés pour les versions Spark prises en charge :</span><span class="sxs-lookup"><span data-stu-id="21e37-158">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="21e37-159">Générer les exemples d’applications Spark .NET pour Spark</span><span class="sxs-lookup"><span data-stu-id="21e37-159">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="21e37-160">Cette section explique comment créer les [exemples d’applications](https://github.com/dotnet/spark/tree/master/examples) pour .net pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="21e37-160">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="21e37-161">Ces étapes vous aideront à comprendre le processus global de création pour n’importe quelle application .NET pour Spark.</span><span class="sxs-lookup"><span data-stu-id="21e37-161">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="21e37-162">Utilisation de Visual Studio pour .NET Framework</span><span class="sxs-lookup"><span data-stu-id="21e37-162">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="21e37-163">Ouvrez `src\csharp\Microsoft.Spark.sln` dans Visual Studio et générez le projet `Microsoft.Spark.CSharp.Examples` dans le dossier `examples` (cela génère également le projet de liaison .NET).</span><span class="sxs-lookup"><span data-stu-id="21e37-163">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="21e37-164">Si vous le souhaitez, vous pouvez écrire votre propre code dans le projet `Microsoft.Spark.Examples` (le’input_file. JSON’dans cet exemple est un fichier JSON avec les données avec lesquelles vous souhaitez créer le tableau) :</span><span class="sxs-lookup"><span data-stu-id="21e37-164">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
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

     <span data-ttu-id="21e37-165">Une fois la génération réussie, vous verrez les fichiers binaires appropriés produits dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="21e37-165">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>     
     <span data-ttu-id="21e37-166">Exemple de sortie de console :</span><span class="sxs-lookup"><span data-stu-id="21e37-166">Sample console output:</span></span>
     
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

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="21e37-167">Utilisation de CLI .NET Core pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="21e37-167">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="21e37-168">Nous travaillons actuellement sur l’automatisation des builds .NET Core pour Spark .NET.</span><span class="sxs-lookup"><span data-stu-id="21e37-168">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="21e37-169">Jusqu’à présent, nous vous remercions de votre patience en effectuant certaines étapes manuellement.</span><span class="sxs-lookup"><span data-stu-id="21e37-169">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="21e37-170">Générez le Worker :</span><span class="sxs-lookup"><span data-stu-id="21e37-170">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
      
      <span data-ttu-id="21e37-171">Exemple de sortie de console :</span><span class="sxs-lookup"><span data-stu-id="21e37-171">Sample console output:</span></span>

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

  2. <span data-ttu-id="21e37-172">Générez les exemples :</span><span class="sxs-lookup"><span data-stu-id="21e37-172">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
   
      <span data-ttu-id="21e37-173">Exemple de sortie de console :</span><span class="sxs-lookup"><span data-stu-id="21e37-173">Sample console output:</span></span>

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

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="21e37-174">Exécuter les exemples d’applications Spark .NET</span><span class="sxs-lookup"><span data-stu-id="21e37-174">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="21e37-175">Une fois que vous avez généré les exemples, vous devez les exécuter à l’aide de `spark-submit` que vous cibliez .NET Framework ou .NET Core.</span><span class="sxs-lookup"><span data-stu-id="21e37-175">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="21e37-176">Vérifiez que vous avez suivi la section [conditions préalables](#prerequisites) et que vous avez installé Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="21e37-176">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="21e37-177">Définissez la variable d’environnement `DOTNET_WORKER_DIR` ou `PATH` pour inclure le chemin d’accès où le fichier binaire `Microsoft.Spark.Worker` a été généré (par exemple, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* pour .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* pour .net Core) :</span><span class="sxs-lookup"><span data-stu-id="21e37-177">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. <span data-ttu-id="21e37-178">Ouvrez PowerShell et accédez au répertoire dans lequel votre fichier binaire d’application a été généré (par exemple, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* pour .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* pour .net Core) :</span><span class="sxs-lookup"><span data-stu-id="21e37-178">Open Powershell and go to the directory where your app binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. <span data-ttu-id="21e37-179">L’exécution de votre application suit la structure de base :</span><span class="sxs-lookup"><span data-stu-id="21e37-179">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="21e37-180">Voici quelques exemples que vous pouvez exécuter :</span><span class="sxs-lookup"><span data-stu-id="21e37-180">Here are some examples you can run:</span></span>

     - <span data-ttu-id="21e37-181">**[Microsoft. Spark. examples. Sql. batch. Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="21e37-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="21e37-182">**[Microsoft. Spark. examples. Sql. streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="21e37-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="21e37-183">**[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (Maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="21e37-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="21e37-184">**[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (fichiers jar fournis)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="21e37-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd 
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
