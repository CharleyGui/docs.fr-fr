---
title: Créer une application .NET pour Apache Spark sur Windows
description: Apprenez à créer votre application .NET pour Apache Spark sur Windows.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: 8f197c0050d149ed03e328e72868ad4ba2f728c1
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688109"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Apprenez à créer votre application .NET pour Apache Spark sur Windows

Cet article vous apprend à créer votre .NET pour les applications Apache Spark sur Windows.

## <a name="prerequisites"></a>Prérequis

Si vous disposez déjà de toutes les conditions préalables suivantes, passez aux étapes de [génération](#build) .

  1. Télécharger et installer le **[Kit SDK .net Core](https://dotnet.microsoft.com/download/dotnet-core/3.1)** : l’installation du kit de développement logiciel (SDK) ajoute le `dotnet` chaîne d’outils à votre chemin d’accès. .NET Core 2,1, 2,2 et 3,1 sont pris en charge.
  2. Installez **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (version 16,3 ou ultérieure). La version de la communauté est entièrement gratuite. Lors de la configuration de votre installation, incluez au minimum les composants suivants :
     * Développement .NET Desktop
       * Tous les composants requis
         * Outils de développement .NET Framework 4.6.1
     * Développement multiplateforme .NET Core
       * Tous les composants requis
  3. Installez **[Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.
     - Sélectionnez la version appropriée pour votre système d’exploitation. Par exemple, *jdk-8u201-windows-x64.exe* pour Windows x64 machine.
     - Installez à l’aide du programme d’installation et vérifiez que vous pouvez exécuter `java` à partir de la ligne de commande.
  4. Installez **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)**.
     - Téléchargez [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).
     - Extrayez-le dans un répertoire local. Par exemple, * C:\bin\apache-Maven-3.6.0 \* .
     - Ajoutez Apache Maven à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml). Par exemple, *C:\bin\apache-Maven-3.6.0\Bin*.
     - Vérifiez que vous pouvez exécuter `mvn` à partir de la ligne de commande.
  5. Installez **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)**.
     - Téléchargez [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) et extrayez-le dans un dossier local (par exemple, *C:\bin\spark-3.0.1-bin-hadoop2.7 \* ) à l’aide de [7-zip](https://www.7-zip.org/). (Les versions Spark prises en charge sont 2,3.*, 2.4.0, 2.4.1, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 3.0.0 et 3.0.1)
     - Ajoutez une [nouvelle variable d’environnement](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` . Par exemple, * C:\bin\spark-3.0.1-bin-hadoop2.7 \* .

       ```powershell
       set SPARK_HOME=C:\bin\spark-3.0.1-bin-hadoop2.7\
       ```

     - Ajoutez Apache Spark à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml). Par exemple, *C:\bin\spark-3.0.1-bin-hadoop2.7\bin*.

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - Vérifiez que vous pouvez exécuter `spark-shell` à partir de la ligne de commande.
        Exemple de sortie de console :

        ```output
        Welcome to
              ____              __
             / __/__  ___ _____/ /__
            _\ \/ _ \/ _ `/ __/  '_/
           /___/ .__/\_,_/_/ /_/\_\   version 3.0.1
              /_/

        Using Scala version 2.12.10 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
        Type in expressions to have them evaluated.
        Type :help for more information.

        scala> sc
        res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
        ```

        </details>

  6. Installez **[winutils](https://github.com/steveloughran/winutils)**.
     - Téléchargez le `winutils.exe` fichier binaire à partir du [dépôt winutils](https://github.com/steveloughran/winutils). Vous devez sélectionner la version de Hadoop avec laquelle la distribution Spark a été compilée. Pour exammple, utilisez Hadoop-2.7.1 pour Spark 3.0.1.
     - Enregistrez `winutils.exe` le fichier binaire dans le répertoire de votre choix. Par exemple, *C:\hadoop\bin*.
     - Défini `HADOOP_HOME` pour refléter le répertoire avec winutils.exe (sans bin). Par exemple, à l’aide de la ligne de commande :

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - Définissez la variable d’environnement PATH à inclure `%HADOOP_HOME%\bin` . Par exemple, à l’aide de la ligne de commande :

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Assurez-vous que vous êtes en mesure d’exécuter `dotnet` , `java` , `mvn` , `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante. Vous avez l’impression d’avoir une meilleure solution ? [Ouvrez un problème](https://github.com/dotnet/spark/issues) et n’hésitez pas à contribuer.

> [!NOTE]
> Une nouvelle instance de la ligne de commande peut être requise si des variables d’environnement ont été mises à jour.

## <a name="build"></a>Générer

Pour le reste de ce guide, vous devez avoir cloné le .NET pour Apache Spark référentiel sur votre machine. Vous pouvez choisir n’importe quel emplacement pour le référentiel cloné. Par exemple, * C:\github\dotnet-Spark \* .

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Build .NET pour Apache Spark couche d’extensions Scala

Lorsque vous soumettez une application .NET, .NET pour Apache Spark a la logique nécessaire écrite en Scala qui informe Apache Spark de la gestion de vos demandes (par exemple, la demande de création d’une nouvelle session Spark, la demande de transfert des données du côté .NET vers JVM, etc.). Cette logique se trouve dans le [.net pour le code source Scala Spark](https://github.com/dotnet/spark/tree/master/src/scala).

Que vous utilisiez .NET Framework ou .NET Core, vous devrez générer le .NET pour la couche d’extension Scala Apache Spark :

```powershell
cd src\scala
mvn clean package
```

Vous devez voir les fichiers jar créés pour les versions Spark prises en charge :

* `microsoft-spark-2-3\target\microsoft-spark-2-3_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-2-4\target\microsoft-spark-2-4_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-3-0\target\microsoft-spark-3-0_2.12-<spark-dotnet-version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Générer les exemples d’applications Spark .NET pour Spark

Cette section explique comment créer les [exemples d’applications](https://github.com/dotnet/spark/tree/master/examples) pour .net pour Apache Spark. Ces étapes vous aideront à comprendre le processus global de création pour n’importe quelle application .NET pour Spark.

#### <a name="using-visual-studio-for-net-framework"></a>Utilisation de Visual Studio pour .NET Framework

  1. Ouvrez `src\csharp\Microsoft.Spark.sln` dans Visual Studio et générez le `Microsoft.Spark.CSharp.Examples` projet sous le `examples` dossier (cela générera également le projet de liaisons .net). Si vous le souhaitez, vous pouvez écrire votre propre code dans le `Microsoft.Spark.Examples` projet (le « input_file.jssur » dans cet exemple est un fichier JSON avec les données avec lesquelles vous souhaitez créer le tableau) :
  
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

     Une fois la génération réussie, vous verrez les fichiers binaires appropriés produits dans le répertoire de sortie.
     Exemple de sortie de console :

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

#### <a name="using-net-core-cli-for-net-core"></a>Utilisation de CLI .NET Core pour .NET Core

> [!NOTE]
> Nous travaillons actuellement sur l’automatisation des builds .NET Core pour Spark .NET. Jusqu’à présent, nous vous remercions de votre patience en effectuant certaines étapes manuellement.

  1. Générez le Worker :

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp3.1 -r win-x64
      ```

      Exemple de sortie de console :

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp3.1 -r win-x64
      Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.1\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish\
      ```

  2. Générez les exemples :

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp3.1 -r win-x64
      ```

      Exemple de sortie de console :

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp3.1 -r win-x64
      Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.1\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a>Exécuter les exemples d’applications Spark .NET

Une fois que vous avez généré les exemples, vous pouvez les exécuter à l’aide `spark-submit` de, que vous cibliez .NET Framework ou .net core. Vérifiez que vous avez suivi la section [conditions préalables](#prerequisites) et que vous avez installé Apache Spark.

  1. Définissez la `DOTNET_WORKER_DIR` `PATH` variable d’environnement ou pour inclure le chemin d’accès où le `Microsoft.Spark.Worker` fichier binaire a été généré (par exemple, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* pour .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish* pour .net Core) :

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish
      ```
  
  2. Ouvrez PowerShell et accédez au répertoire dans lequel votre fichier binaire d’application a été généré (par exemple, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* pour .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish* pour .net Core) :

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish
      ```

  3. L’exécution de votre application suit la structure de base :

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     Voici quelques exemples que vous pouvez exécuter :

     - **[Microsoft.Spark.Examples.Sql.Batch. Bases](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft. Spark. examples. Sql. streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (Maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (fichiers jar fournis)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
