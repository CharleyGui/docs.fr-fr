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
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a>Apprenez à construire votre application .NET pour Apache Spark sur Ubuntu

Cet article vous apprend à construire votre .NET pour apache Spark applications sur Ubuntu.

## <a name="prerequisites"></a>Conditions préalables requises

Si vous avez déjà toutes les conditions préalables suivantes, sautez aux étapes [de construction.](#build)

1. Téléchargez et installez **[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** ou le **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - l’installation du SDK ajoute la `dotnet` chaîne à outils à votre chemin.  .NET Core 2.1, 2.2 et 3.1 sont pris en charge.

2. Installer **[OpenJDK 8](https://openjdk.java.net/install/)**.

   - Vous pouvez utiliser la commande suivante :

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * Vérifiez que vous `java` êtes en mesure de courir à partir de votre ligne de commande.

      Exemple de sortie java-version:

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * Si vous avez déjà plusieurs versions OpenJDK installées et que vous souhaitez sélectionner OpenJDK 8, utilisez la commande suivante :

      ```bash
      sudo update-alternatives --config java
      ```

3. Installer **[Apache Maven 3.6.0 .](https://maven.apache.org/download.cgi)**

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

       Notez que ces variables de l’environnement seront perdues lorsque vous fermez votre terminal. Si vous voulez que les modifications soient permanentes, ajoutez les `export` lignes à votre `~/.bashrc` fichier.

   * Vérifiez que vous `mvn` êtes en mesure de courir à partir de votre ligne de commande

       Exemple mvn -version sortie:

       ```
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. Installez **[Apache Spark 2.3 .](https://spark.apache.org/downloads.html)**
Téléchargez [Apache Spark 2.3 et](https://spark.apache.org/downloads.html) extrait dans un dossier `~/bin/spark-2.3.2-bin-hadoop2.7`local (p. ex., ). (Les versions d’étincelles prises en charge sont de 2,3. , 2.4.0, 2.4.1, 2.4.3 et 2.4.4)

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * Ajouter les `SPARK_HOME` [variables de l’environnement](https://www.java.com/en/download/help/path.xml) nécessaires `PATH` (p. ex.) `$SPARK_HOME/bin:$PATH` `~/bin/spark-2.3.2-bin-hadoop2.7/`et (p. ex., )

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      Notez que ces variables de l’environnement seront perdues lorsque vous fermez votre terminal. Si vous voulez que les modifications soient permanentes, ajoutez les `export` lignes à votre `~/.bashrc` fichier.

   * Vérifiez que vous `spark-shell` êtes en mesure de courir à partir de votre ligne de commande.

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

Assurez-vous que vous `dotnet` `java`êtes `mvn` `spark-shell` en mesure d’exécuter , , à partir de votre ligne de commande avant de passer à la section suivante. Vous pensez qu’il y a une meilleure façon? S’il vous plaît [ouvrir un problème](https://github.com/dotnet/spark/issues) et n’hésitez pas à contribuer.

## <a name="build"></a>Build

Pour le reste de ce guide, vous aurez besoin d’avoir cloné le .NET pour `~/dotnet.spark/`Apache Spark référentiel dans votre machine par exemple, .

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a>Construire .NET pour Spark Scala extensions couche

Lorsque vous soumettez une demande .NET, .NET pour Apache Spark a la logique nécessaire écrite dans Scala qui informe Apache Spark comment traiter vos demandes (par exemple, la demande de créer une nouvelle session Spark, la demande de transfert de données de côté .NET à côté JVM, etc.) Cette logique peut être trouvée dans le [.NET pour Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).

La prochaine étape est de construire le .NET pour Apache Spark Scala couche d’extension:

```bash
cd src/scala
mvn clean package
```

Vous devriez voir LES créés pour les versions Spark prises en charge :

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a>Construire des applications d’échantillons .NET à l’aide de CLI core .NET

Cette section explique comment construire les [applications d’échantillon](https://github.com/dotnet/spark/tree/master/examples) pour .NET pour Apache Spark. Ces étapes aideront à comprendre le processus global de construction pour n’importe quel .NET pour l’application Spark.

1. Construire le travailleur:

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   Sortie de la console d’échantillon :

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

2. Construire les échantillons:

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   Sortie de la console d’échantillon :

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

## <a name="run-the-net-for-spark-sample-applications"></a>Exécuter le .NET pour les applications d’échantillons Spark

Une fois que vous avez `spark-submit` construit les échantillons, vous pouvez utiliser pour soumettre vos applications .NET Core. Assurez-vous d’avoir suivi la section [préalables](#prerequisites) et installé Apache Spark.

1. Définissez `DOTNET_WORKER_DIR` `PATH` la variable ou l’environnement pour inclure le chemin où le `Microsoft.Spark.Worker` binaire a été généré (par exemple, `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. Ouvrez un terminal et rendez-vous à l’annuaire où `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`votre application binaire a été générée (par exemple, ).

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. L’exécution de votre application suit la structure de base :

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   Voici quelques exemples que vous pouvez exécuter :

   * **[Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.Spark.Examples.Sql.Batch.Basic Microsoft.](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount (en anglais seulement)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars fournis)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
