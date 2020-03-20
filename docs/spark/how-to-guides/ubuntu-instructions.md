---
title: Construire une application .NET pour Apache Spark sur Ubuntu
description: Apprenez à construire votre application .NET pour Apache Spark sur Ubuntu
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 6dd6f60bb89a51c47fe17182fc47de818cd00b80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187568"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a><span data-ttu-id="a3e93-103">Apprenez à construire votre application .NET pour Apache Spark sur Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a3e93-103">Learn how to build your .NET for Apache Spark application on Ubuntu</span></span>

<span data-ttu-id="a3e93-104">Cet article vous apprend à construire votre .NET pour apache Spark applications sur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a3e93-104">This article teaches you how to build your .NET for Apache Spark applications on Ubuntu.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a3e93-105">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="a3e93-105">Prerequisites</span></span>

<span data-ttu-id="a3e93-106">Si vous avez déjà toutes les conditions préalables suivantes, sautez aux étapes [de construction.](#build)</span><span class="sxs-lookup"><span data-stu-id="a3e93-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

1. <span data-ttu-id="a3e93-107">Téléchargez et installez **[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** ou le **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - l’installation du SDK ajoute la `dotnet` chaîne à outils à votre chemin.</span><span class="sxs-lookup"><span data-stu-id="a3e93-107">Download and install **[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** or the **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - installing the SDK adds the `dotnet` toolchain to your path.</span></span>  <span data-ttu-id="a3e93-108">.NET Core 2.1, 2.2 et 3.1 sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a3e93-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>

2. <span data-ttu-id="a3e93-109">Installer **[OpenJDK 8](https://openjdk.java.net/install/)**.</span><span class="sxs-lookup"><span data-stu-id="a3e93-109">Install **[OpenJDK 8](https://openjdk.java.net/install/)**.</span></span>

   - <span data-ttu-id="a3e93-110">Vous pouvez utiliser la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a3e93-110">You can use the following command:</span></span>

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * <span data-ttu-id="a3e93-111">Vérifiez que vous `java` êtes en mesure de courir à partir de votre ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a3e93-111">Verify you are able to run `java` from your command-line.</span></span>

      <span data-ttu-id="a3e93-112">Exemple de sortie java-version:</span><span class="sxs-lookup"><span data-stu-id="a3e93-112">Sample java -version output:</span></span>

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * <span data-ttu-id="a3e93-113">Si vous avez déjà plusieurs versions OpenJDK installées et que vous souhaitez sélectionner OpenJDK 8, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a3e93-113">If you already have multiple OpenJDK versions installed and want to select OpenJDK 8, use the following command:</span></span>

      ```bash
      sudo update-alternatives --config java
      ```

3. <span data-ttu-id="a3e93-114">Installer **[Apache Maven 3.6.0 .](https://maven.apache.org/download.cgi)**</span><span class="sxs-lookup"><span data-stu-id="a3e93-114">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>

   * <span data-ttu-id="a3e93-115">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a3e93-115">Run the following command:</span></span>

      ```bash
      mkdir -p ~/bin/maven
      cd ~/bin/maven
      wget https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
      tar -xvzf apache-maven-3.6.0-bin.tar.gz
      ln -s apache-maven-3.6.0 current
      export M2_HOME=~/bin/maven/current
      export PATH=${M2_HOME}/bin:${PATH}
      source ~/.bashrc
      ```

       <span data-ttu-id="a3e93-116">Notez que ces variables de l’environnement seront perdues lorsque vous fermez votre terminal.</span><span class="sxs-lookup"><span data-stu-id="a3e93-116">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="a3e93-117">Si vous voulez que les modifications soient permanentes, ajoutez les `export` lignes à votre `~/.bashrc` fichier.</span><span class="sxs-lookup"><span data-stu-id="a3e93-117">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="a3e93-118">Vérifiez que vous `mvn` êtes en mesure de courir à partir de votre ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a3e93-118">Verify you are able to run `mvn` from your command-line</span></span>

       <span data-ttu-id="a3e93-119">Exemple mvn -version sortie:</span><span class="sxs-lookup"><span data-stu-id="a3e93-119">Sample mvn -version output:</span></span>

       ```
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. <span data-ttu-id="a3e93-120">Installez **[Apache Spark 2.3 .](https://spark.apache.org/downloads.html)**</span><span class="sxs-lookup"><span data-stu-id="a3e93-120">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
<span data-ttu-id="a3e93-121">Téléchargez [Apache Spark 2.3 et](https://spark.apache.org/downloads.html) extrait dans un dossier `~/bin/spark-2.3.2-bin-hadoop2.7`local (p. ex., ).</span><span class="sxs-lookup"><span data-stu-id="a3e93-121">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7`).</span></span> <span data-ttu-id="a3e93-122">(Les versions d’étincelles prises en charge sont de 2,3. , 2.4.0, 2.4.1, 2.4.3 et 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="a3e93-122">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * <span data-ttu-id="a3e93-123">Ajouter les `SPARK_HOME` [variables de l’environnement](https://www.java.com/en/download/help/path.xml) nécessaires `PATH` (p. ex.) `$SPARK_HOME/bin:$PATH` `~/bin/spark-2.3.2-bin-hadoop2.7/`et (p. ex., )</span><span class="sxs-lookup"><span data-stu-id="a3e93-123">Add the necessary [environment variables](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7/`) and `PATH` (e.g., `$SPARK_HOME/bin:$PATH`)</span></span>

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      <span data-ttu-id="a3e93-124">Notez que ces variables de l’environnement seront perdues lorsque vous fermez votre terminal.</span><span class="sxs-lookup"><span data-stu-id="a3e93-124">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="a3e93-125">Si vous voulez que les modifications soient permanentes, ajoutez les `export` lignes à votre `~/.bashrc` fichier.</span><span class="sxs-lookup"><span data-stu-id="a3e93-125">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="a3e93-126">Vérifiez que vous `spark-shell` êtes en mesure de courir à partir de votre ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a3e93-126">Verify you are able to run `spark-shell` from your command-line.</span></span>

      <span data-ttu-id="a3e93-127">Sortie de la console d’échantillon :</span><span class="sxs-lookup"><span data-stu-id="a3e93-127">Sample console output:</span></span>

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

<span data-ttu-id="a3e93-128">Assurez-vous que vous `dotnet` `java`êtes `mvn` `spark-shell` en mesure d’exécuter , , à partir de votre ligne de commande avant de passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="a3e93-128">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="a3e93-129">Vous pensez qu’il y a une meilleure façon?</span><span class="sxs-lookup"><span data-stu-id="a3e93-129">Feel there is a better way?</span></span> <span data-ttu-id="a3e93-130">S’il vous plaît [ouvrir un problème](https://github.com/dotnet/spark/issues) et n’hésitez pas à contribuer.</span><span class="sxs-lookup"><span data-stu-id="a3e93-130">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

## <a name="build"></a><span data-ttu-id="a3e93-131">Build</span><span class="sxs-lookup"><span data-stu-id="a3e93-131">Build</span></span>

<span data-ttu-id="a3e93-132">Pour le reste de ce guide, vous aurez besoin d’avoir cloné le .NET pour `~/dotnet.spark/`Apache Spark référentiel dans votre machine par exemple, .</span><span class="sxs-lookup"><span data-stu-id="a3e93-132">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine e.g., `~/dotnet.spark/`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a><span data-ttu-id="a3e93-133">Construire .NET pour Spark Scala extensions couche</span><span class="sxs-lookup"><span data-stu-id="a3e93-133">Build .NET for Spark Scala extensions layer</span></span>

<span data-ttu-id="a3e93-134">Lorsque vous soumettez une demande .NET, .NET pour Apache Spark a la logique nécessaire écrite dans Scala qui informe Apache Spark comment traiter vos demandes (par exemple, la demande de créer une nouvelle session Spark, la demande de transfert de données de côté .NET à côté JVM, etc.)</span><span class="sxs-lookup"><span data-stu-id="a3e93-134">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="a3e93-135">Cette logique peut être trouvée dans le [.NET pour Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span><span class="sxs-lookup"><span data-stu-id="a3e93-135">This logic can be found in the [.NET for Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="a3e93-136">La prochaine étape est de construire le .NET pour Apache Spark Scala couche d’extension:</span><span class="sxs-lookup"><span data-stu-id="a3e93-136">The next step is to build the .NET for Apache Spark Scala extension layer:</span></span>

```bash
cd src/scala
mvn clean package
```

<span data-ttu-id="a3e93-137">Vous devriez voir LES créés pour les versions Spark prises en charge :</span><span class="sxs-lookup"><span data-stu-id="a3e93-137">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a><span data-ttu-id="a3e93-138">Construire des applications d’échantillons .NET à l’aide de CLI core .NET</span><span class="sxs-lookup"><span data-stu-id="a3e93-138">Build .NET sample applications using .NET Core CLI</span></span>

<span data-ttu-id="a3e93-139">Cette section explique comment construire les [applications d’échantillon](https://github.com/dotnet/spark/tree/master/examples) pour .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="a3e93-139">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="a3e93-140">Ces étapes aideront à comprendre le processus global de construction pour n’importe quel .NET pour l’application Spark.</span><span class="sxs-lookup"><span data-stu-id="a3e93-140">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

1. <span data-ttu-id="a3e93-141">Construire le travailleur:</span><span class="sxs-lookup"><span data-stu-id="a3e93-141">Build the worker:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="a3e93-142">Sortie de la console d’échantillon :</span><span class="sxs-lookup"><span data-stu-id="a3e93-142">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 36.03 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker/Microsoft.Spark.Worker.csproj.
      Restore completed in 35.94 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.Worker.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```

2. <span data-ttu-id="a3e93-143">Construire les échantillons:</span><span class="sxs-lookup"><span data-stu-id="a3e93-143">Build the samples:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="a3e93-144">Sortie de la console d’échantillon :</span><span class="sxs-lookup"><span data-stu-id="a3e93-144">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 37.11 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Restore completed in 281.63 ms for /home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/Microsoft.Spark.CSharp.Examples.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.CSharp.Examples.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```  

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="a3e93-145">Exécuter le .NET pour les applications d’échantillons Spark</span><span class="sxs-lookup"><span data-stu-id="a3e93-145">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="a3e93-146">Une fois que vous avez `spark-submit` construit les échantillons, vous pouvez utiliser pour soumettre vos applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a3e93-146">Once you build the samples, you can use `spark-submit` to submit your .NET Core apps.</span></span> <span data-ttu-id="a3e93-147">Assurez-vous d’avoir suivi la section [préalables](#prerequisites) et installé Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="a3e93-147">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

1. <span data-ttu-id="a3e93-148">Définissez `DOTNET_WORKER_DIR` `PATH` la variable ou l’environnement pour inclure le chemin où le `Microsoft.Spark.Worker` binaire a été généré (par exemple, `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span><span class="sxs-lookup"><span data-stu-id="a3e93-148">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. <span data-ttu-id="a3e93-149">Ouvrez un terminal et rendez-vous à l’annuaire où `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`votre application binaire a été générée (par exemple, ).</span><span class="sxs-lookup"><span data-stu-id="a3e93-149">Open a terminal and go to the directory where your app binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. <span data-ttu-id="a3e93-150">L’exécution de votre application suit la structure de base :</span><span class="sxs-lookup"><span data-stu-id="a3e93-150">Running your app follows the basic structure:</span></span>

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   <span data-ttu-id="a3e93-151">Voici quelques exemples que vous pouvez exécuter :</span><span class="sxs-lookup"><span data-stu-id="a3e93-151">Here are some examples you can run:</span></span>

   * <span data-ttu-id="a3e93-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="a3e93-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * <span data-ttu-id="a3e93-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount (en anglais seulement)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="a3e93-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * <span data-ttu-id="a3e93-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="a3e93-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * <span data-ttu-id="a3e93-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars fournis)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="a3e93-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
