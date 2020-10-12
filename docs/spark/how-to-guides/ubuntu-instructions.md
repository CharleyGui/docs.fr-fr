---
title: Créer une application .NET pour Apache Spark sur Ubuntu
description: Découvrez comment créer votre application .NET pour Apache Spark sur Ubuntu
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dfe105bb1549560ebdd2526a8441c4e2c5d141bf
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955060"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a>Découvrez comment créer votre application .NET pour Apache Spark sur Ubuntu

Cet article vous apprend à créer votre .NET pour les applications Apache Spark sur Ubuntu.

## <a name="prerequisites"></a>Prérequis

Si vous disposez déjà de toutes les conditions préalables suivantes, passez aux étapes de [génération](#build) .

1. Télécharger et installer le kit de développement logiciel (SDK) **[.net core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)** ou **[.net Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** -l’installation du kit de développement logiciel (SDK) ajoute `dotnet` chaîne d’outils à votre chemin.  .NET Core 2,1, 2,2 et 3,1 sont pris en charge.

2. Installez **[openjdk 8](https://openjdk.java.net/install/)**.

   - Vous pouvez utiliser la commande suivante :

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * Vérifiez que vous pouvez exécuter `java` à partir de la ligne de commande.

      Exemple de sortie de version Java :

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * Si vous avez déjà installé plusieurs versions de OpenJDK et que vous souhaitez sélectionner OpenJDK 8, utilisez la commande suivante :

      ```bash
      sudo update-alternatives --config java
      ```

3. Installez **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)**.

   * Exécutez la commande suivante :

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

       Notez que ces variables d’environnement seront perdues lorsque vous fermerez votre terminal. Si vous souhaitez que les modifications soient permanentes, ajoutez les `export` lignes à votre `~/.bashrc` fichier.

   * Vérifiez que vous pouvez exécuter `mvn` à partir de votre ligne de commande

       Exemple de sortie MVN-version :

       ```output
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. Installez **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)**.
Téléchargez [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) et extrayez-le dans un dossier local (par exemple, `~/bin/spark-2.3.2-bin-hadoop2.7` ). (Les versions Spark prises en charge sont 2,3. *, 2.4.0, 2.4.1, 2.4.3 et 2.4.4)

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * Ajoutez les [variables d’environnement](https://www.java.com/en/download/help/path.xml) nécessaires `SPARK_HOME` (par exemple, `~/bin/spark-2.3.2-bin-hadoop2.7/` ) et `PATH` (par exemple, `$SPARK_HOME/bin:$PATH` )

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      Notez que ces variables d’environnement seront perdues lorsque vous fermerez votre terminal. Si vous souhaitez que les modifications soient permanentes, ajoutez les `export` lignes à votre `~/.bashrc` fichier.

   * Vérifiez que vous pouvez exécuter `spark-shell` à partir de la ligne de commande.

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

Assurez-vous que vous êtes en mesure d’exécuter `dotnet` , `java` , `mvn` , `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante. Vous avez l’impression d’avoir une meilleure solution ? Veuillez [ouvrir un problème](https://github.com/dotnet/spark/issues) et n’hésitez pas à contribuer.

## <a name="build"></a>Build

Pour le reste de ce guide, vous devez avoir cloné le .NET pour Apache Spark référentiel sur votre ordinateur, par exemple, `~/dotnet.spark/` .

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a>Build .NET pour les extensions Spark Scala

Lorsque vous soumettez une application .NET, .NET pour Apache Spark a la logique nécessaire écrite en Scala qui informe Apache Spark la gestion de vos demandes (par exemple, la demande de création d’une nouvelle session Spark, la demande de transfert des données du côté .NET vers JVM, etc.). Cette logique se trouve dans [.net pour Apache Spark code source Scala](https://github.com/dotnet/spark/tree/master/src/scala).

L’étape suivante consiste à créer le .NET pour Apache Spark couche d’extension Scala :

```bash
cd src/scala
mvn clean package
```

Vous devez voir les fichiers jar créés pour les versions Spark prises en charge :

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a>Générez des exemples d’applications .NET à l’aide de CLI .NET Core

Cette section explique comment créer les [exemples d’applications](https://github.com/dotnet/spark/tree/master/examples) pour .net pour Apache Spark. Ces étapes vous aideront à comprendre le processus global de création pour n’importe quelle application .NET pour Spark.

1. Générez le Worker :

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   Exemple de sortie de console :

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

2. Générez les exemples :

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   Exemple de sortie de console :

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

## <a name="run-the-net-for-spark-sample-applications"></a>Exécuter les exemples d’applications Spark .NET

Une fois que vous avez généré les exemples, vous pouvez utiliser `spark-submit` pour envoyer vos applications .net core. Vérifiez que vous avez suivi la section [conditions préalables](#prerequisites) et que vous avez installé Apache Spark.

1. Définissez la `DOTNET_WORKER_DIR` `PATH` variable d’environnement ou pour inclure le chemin d’accès où le `Microsoft.Spark.Worker` fichier binaire a été généré (par exemple, `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish` ).

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. Ouvrez un terminal et accédez au répertoire dans lequel votre fichier binaire d’application a été généré (par exemple, `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish` ).

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. L’exécution de votre application suit la structure de base :

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   Voici quelques exemples que vous pouvez exécuter :

   * **[Microsoft.Spark.Examples.Sql.Batch. Bases](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * **[Microsoft. Spark. examples. Sql. streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * **[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (Maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * **[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (fichiers jar fournis)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
