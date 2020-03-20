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
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Apprenez à construire votre application .NET pour Apache Spark sur Windows

Cet article vous apprend à construire votre .NET pour les applications Apache Spark sur Windows.

## <a name="prerequisites"></a>Conditions préalables requises

Si vous avez déjà toutes les conditions préalables suivantes, sautez aux étapes [de construction.](#build)

  1. Téléchargez et installez le **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - `dotnet` l’installation du SDK ajoutera la chaîne à outils à votre chemin. .NET Core 2.1, 2.2 et 3.1 sont pris en charge.
  2. Installez **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 ou plus tard). La version Communautaire est entièrement gratuite. Lors de la configuration de votre installation, inclure ces composants au minimum:
     * Développement .NET Desktop
       * Tous les composants requis
         * Outils de développement .NET Framework 4.6.1
     * Développement multiplateforme .NET Core
       * Tous les composants requis
  3. Installer **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.
     - Sélectionnez la version appropriée pour votre système d’exploitation. Par exemple, *jdk-8u201-windows-x64.exe* pour Windows x64 machine.
     - Installez à l’aide de `java` l’installateur et vérifiez que vous êtes en mesure de courir à partir de votre ligne de commande.
  4. Installer **[Apache Maven 3.6.0 .](https://maven.apache.org/download.cgi)**
     - Téléchargez [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).
     - Extrayez-le dans un répertoire local. Par exemple, 'C:'bin’apache-maven-3.6.0\*.
     - Ajoutez Apache Maven à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml). Par exemple, *C: 'bin’apache-maven-3.6.0'bin*.
     - Vérifiez que vous `mvn` êtes en mesure de courir à partir de votre ligne de commande.
  5. Installez **[Apache Spark 2.3 .](https://spark.apache.org/downloads.html)**
     - Téléchargez [Apache Spark 2.3 et](https://spark.apache.org/downloads.html) extrait dans un dossier local (par exemple, *C: 'bin’spark-2.3.2-bin-hadoop2.7\*) à l’aide de [7 zip](https://www.7-zip.org/). (Les versions d’étincelles prises en charge sont 2.3.*, 2.4.0, 2.4.1, 2.4.3 et 2.4.4)
     - Ajouter une nouvelle `SPARK_HOME` [variable d’environnement](https://www.java.com/en/download/help/path.xml) . Par exemple, 'C:'bin’spark-2.3.2-bin-hadoop2.7\*.

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - Ajoutez Apache Spark à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml). Par exemple, *C: 'bin’spark-2.3.2-bin-hadoop2.7'bin*.

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - Vérifiez que vous `spark-shell` êtes en mesure de courir à partir de votre ligne de commande.
        Sortie de la console d’échantillon :

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

  6. Installer **[WinUtils](https://github.com/steveloughran/winutils)**.
     - Télécharger `winutils.exe` binaire à partir du [référentiel WinUtils](https://github.com/steveloughran/winutils). Vous devez sélectionner la version de Hadoop la distribution Spark a été compilée avec. Pour l’examen, utilisez hadoop-2.7.1 pour Spark 2.3.2.
     - Enregistrer `winutils.exe` binaire à un répertoire de votre choix. Par exemple, *C: hadoop-bin*.
     - Définir `HADOOP_HOME` pour refléter le répertoire avec winutils.exe (sans bac). Par exemple, à l’aide de la ligne de commande :

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - Définir path variable `%HADOOP_HOME%\bin`de l’environnement pour inclure . Par exemple, à l’aide de la ligne de commande :

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Assurez-vous que vous `dotnet` `java`êtes `mvn` `spark-shell` en mesure d’exécuter , , à partir de votre ligne de commande avant de passer à la section suivante. Vous pensez qu’il y a une meilleure façon? [Ouvrez un problème](https://github.com/dotnet/spark/issues) et n’hésitez pas à contribuer.

> [!NOTE]
> Une nouvelle instance de la ligne de commande peut être nécessaire si des variables de l’environnement ont été mises à jour.

## <a name="build"></a>Build

Pour le reste de ce guide, vous aurez besoin d’avoir cloné le référentiel .NET pour Apache Spark dans votre machine. Vous pouvez choisir n’importe quel emplacement pour le référentiel cloné. Par exemple, 'C:'github’dotnet-spark\*.

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Construire .NET pour Apache Spark Scala extensions couche

Lorsque vous soumettez une demande .NET, .NET pour Apache Spark a la logique nécessaire écrite dans Scala qui informe Apache Spark comment traiter vos demandes (par exemple, la demande de créer une nouvelle session Spark, demander de transférer des données de côté .NET côté JVM, etc.). Cette logique peut être trouvée dans le [.NET pour Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).

Peu importe si vous utilisez .NET Framework ou .NET Core, vous aurez besoin de construire le .NET pour Apache Spark Scala couche d’extension:

```powershell
cd src\scala
mvn clean package
```

Vous devriez voir LES créés pour les versions Spark prises en charge :

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Construire le .NET pour les applications d’échantillons Spark

Cette section explique comment construire les [applications d’échantillon](https://github.com/dotnet/spark/tree/master/examples) pour .NET pour Apache Spark. Ces étapes aideront à comprendre le processus global de construction pour n’importe quel .NET pour l’application Spark.

#### <a name="using-visual-studio-for-net-framework"></a>Utilisation de Visual Studio pour .NET Framework

  1. Ouvrez `src\csharp\Microsoft.Spark.sln` en Visual `Microsoft.Spark.CSharp.Examples` Studio et `examples` construisez le projet sous le dossier (ce qui permettra à son tour de construire le projet de liaisons .NET ainsi). Si vous le souhaitez, vous pouvez `Microsoft.Spark.Examples` écrire votre propre code dans le projet (le «input_file.json» dans cet exemple est un fichier json avec les données que vous voulez créer le dataframe avec):
  
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

     Une fois la construction réussie, vous verrez les binaires appropriés produits dans le répertoire de sortie.
     Sortie de la console d’échantillon :

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

#### <a name="using-net-core-cli-for-net-core"></a>Utilisation de .NET Core CLI pour .NET Core

> [!NOTE]
> Nous travaillons actuellement sur l’automatisation .NET Core construit pour Spark .NET. Jusque-là, nous apprécions votre patience dans l’exécution de certaines des étapes manuellement.

  1. Construire le travailleur:

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Sortie de la console d’échantillon :

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

  2. Construire les échantillons:

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Sortie de la console d’échantillon :

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

## <a name="run-the-net-for-spark-sample-applications"></a>Exécuter le .NET pour les applications d’échantillons Spark

Une fois que vous construisez `spark-submit` les échantillons, les exécuter sera à travers indépendamment du fait que vous ciblez .NET Framework ou .NET Core. Assurez-vous d’avoir suivi la section [préalables](#prerequisites) et installé Apache Spark.

  1. Définissez `DOTNET_WORKER_DIR` `PATH` la variable ou l’environnement pour inclure le chemin où le `Microsoft.Spark.Worker` binaire a été généré (par exemple, *C: 'github’dotnet’sparks’artifacts-microsoft.Spark.Worker’Debug’net461* pour .NET Framework, *C:'github’dotnet-sparks’ts-Microsoft.Spark.Worker’Debug’netcoreapp2.1-win10-x64*

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. Ouvrez Powershell et rendez-vous à l’annuaire où votre application binaire a été générée (par exemple, *C : 'github’dotnet’spark’artefacts-bin-Microsoft.Spark.CSharp.Examples-Debug-net461* pour .NET Framework, *C:'github’dotnet-spark’artifacts-microsoft.Spark.CSharp.Examples-Debug-netcoreapp2.1-win10-x64 publish.NET* Core)

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. L’exécution de votre application suit la structure de base :

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     Voici quelques exemples que vous pouvez exécuter :

     - **[Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount (en anglais seulement)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars fournis)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
