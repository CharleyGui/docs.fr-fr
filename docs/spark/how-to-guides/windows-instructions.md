---
title: Créer une application .NET pour Apache Spark sur Windows
description: Apprenez à créer votre application .NET pour Apache Spark sur Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: e6dec09f7d3e8d478cdcccf9df1c3e72d5f884eb
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76928035"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Apprenez à créer votre application .NET pour Apache Spark sur Windows

Cet article vous apprend à créer votre .NET pour les applications Apache Spark sur Windows.

## <a name="prerequisites"></a>Prerequisites

Si vous disposez déjà de toutes les conditions préalables suivantes, passez aux étapes de [génération](#build) .

  1. Télécharger et installer le **[Kit SDK .net Core](https://dotnet.microsoft.com/download/dotnet-core/2.1)** : l’installation du kit de développement logiciel (SDK) ajoute les chaîne d’outils `dotnet` à votre chemin. .NET Core 2,1, 2,2 et 3,1 sont pris en charge.
  2. Installez **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (version 16,3 ou ultérieure). La version de la communauté est entièrement gratuite. Lors de la configuration de votre installation, incluez au minimum les composants suivants :
     * Développement .NET Desktop
       * Tous les composants requis
         * Outils de développement .NET Framework 4.6.1
     * Développement multiplateforme .NET Core
       * Tous les composants requis
  3. Installez **[Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)** . 
     - Sélectionnez la version appropriée pour votre système d’exploitation, par exemple, JDK-8u201-Windows-x64. exe pour Win x64 machine.
     - Installez à l’aide du programme d’installation et vérifiez que vous pouvez exécuter `java` à partir de votre ligne de commande.
  4. Installez **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)** .
     - Téléchargez [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).
     - Extraire dans un répertoire local, par exemple, `C:\bin\apache-maven-3.6.0\`.
     - Ajoutez Apache Maven à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml) , par exemple, `C:\bin\apache-maven-3.6.0\bin`.
     - Vérifiez que vous pouvez exécuter `mvn` à partir de votre ligne de commande.
  5. Installez **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)** .
     - Téléchargez [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) et extrayez-le dans un dossier local (par exemple, `C:\bin\spark-2.3.2-bin-hadoop2.7\`) à l’aide de [7-zip](https://www.7-zip.org/). (Les versions Spark prises en charge sont 2,3. *, 2.4.0, 2.4.1, 2.4.3 et 2.4.4)
     - Ajoutez une [nouvelle variable d’environnement](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` par exemple, `C:\bin\spark-2.3.2-bin-hadoop2.7\`.

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\       
       ```

     - Ajoutez Apache Spark à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml) , par exemple, `C:\bin\spark-2.3.2-bin-hadoop2.7\bin`.

       ```powershell       
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```
     
     - Vérifiez que vous pouvez exécuter `spark-shell` à partir de votre ligne de commande.        
        Exemple de sortie de console :

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

  6. Installez **[winutils](https://github.com/steveloughran/winutils)** .
     - Téléchargez `winutils.exe` fichier binaire à partir du [référentiel winutils](https://github.com/steveloughran/winutils). Vous devez sélectionner la version de Hadoop avec laquelle la distribution Spark a été compilée, par exemple, utilisez Hadoop-2.7.1 pour Spark 2.3.2.
     - Enregistrez `winutils.exe` fichier binaire dans un répertoire de votre choix, par exemple, `C:\hadoop\bin`.
     - Définissez `HADOOP_HOME` pour refléter le répertoire avec winutils. exe (sans bin). Par exemple, à l’aide de la ligne de commande :

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - Définissez la variable d’environnement PATH pour inclure `%HADOOP_HOME%\bin`. Par exemple, à l’aide de la ligne de commande :

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Assurez-vous que vous êtes en mesure d’exécuter `dotnet`, `java`, `mvn`, `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante. Vous avez l’impression d’avoir une meilleure solution ? Veuillez [ouvrir un problème](https://github.com/dotnet/spark/issues) et n’hésitez pas à contribuer.

> [!NOTE]
> Une nouvelle instance de la ligne de commande peut être requise si des variables d’environnement ont été mises à jour.

## <a name="build"></a>Générer

Pour le reste de ce guide, vous devez avoir cloné le .NET pour Apache Spark référentiel sur votre machine. Vous pouvez choisir n’importe quel emplacement pour le référentiel cloné, par exemple, `C:\github\dotnet-spark\`.

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Build .NET pour Apache Spark couche d’extensions Scala

Lorsque vous soumettez une application .NET, .NET pour Apache Spark a la logique nécessaire écrite en Scala qui informe Apache Spark la gestion de vos demandes (par exemple, la demande de création d’une nouvelle session Spark, la demande de transfert des données du côté .NET vers JVM, etc.). Cette logique se trouve dans le [.net pour le code source Scala Spark](https://github.com/dotnet/spark/tree/master/src/scala).

Que vous utilisiez .NET Framework ou .NET Core, vous devrez générer le .NET pour la couche d’extension Scala Apache Spark :

```powershell
cd src\scala
mvn clean package 
```

Vous devez voir les fichiers jar créés pour les versions Spark prises en charge :

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Générer les exemples d’applications Spark .NET pour Spark

Cette section explique comment créer les [exemples d’applications](https://github.com/dotnet/spark/tree/master/examples) pour .net pour Apache Spark. Ces étapes vous aideront à comprendre le processus global de création pour n’importe quelle application .NET pour Spark.

#### <a name="using-visual-studio-for-net-framework"></a>Utilisation de Visual Studio pour .NET Framework

  1. Ouvrez `src\csharp\Microsoft.Spark.sln` dans Visual Studio et générez le projet `Microsoft.Spark.CSharp.Examples` dans le dossier `examples` (cela génère également le projet de liaison .NET). Si vous le souhaitez, vous pouvez écrire votre propre code dans le projet `Microsoft.Spark.Examples` (le’input_file. JSON’dans cet exemple est un fichier JSON avec les données avec lesquelles vous souhaitez créer le tableau) :
  
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
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
      
      Exemple de sortie de console :

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

  2. Générez les exemples :

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
   
      Exemple de sortie de console :

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

## <a name="run-the-net-for-spark-sample-applications"></a>Exécuter les exemples d’applications Spark .NET

Une fois que vous avez généré les exemples, vous devez les exécuter à l’aide de `spark-submit` que vous cibliez .NET Framework ou .NET Core. Vérifiez que vous avez suivi la section [conditions préalables](#prerequisites) et que vous avez installé Apache Spark.

  1. Définissez la variable d’environnement `DOTNET_WORKER_DIR` ou `PATH` pour inclure le chemin d’accès où le fichier binaire `Microsoft.Spark.Worker` a été généré (par exemple, `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461` pour .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish` pour .NET Core) :

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. Ouvrez PowerShell et accédez au répertoire dans lequel votre fichier binaire d’application a été généré (par exemple, `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461` pour .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish` pour .NET Core) :

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
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

     - **[Microsoft. Spark. examples. Sql. batch. Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft. Spark. examples. Sql. streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (Maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (fichiers jar fournis)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd 
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
