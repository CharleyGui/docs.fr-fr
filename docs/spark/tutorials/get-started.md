---
title: Prise en main de .NET pour Apache Spark
description: Découvrez comment exécuter un .NET pour Apache Spark application à l’aide de .NET Core sur Windows.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ce7d7aec6c15385d3d797d5a548519eea33b764
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "69577006"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Tutoriel : Prise en main de .NET pour Apache Spark

Ce didacticiel vous apprend à exécuter un .NET pour Apache Spark application à l’aide de .NET Core sur Windows.

Ce tutoriel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
> * Préparer votre environnement Windows pour .NET pour la Apache Spark
> * Télécharger **Microsoft. Spark. Worker**
> * Générez et exécutez une application .NET simple pour Apache Spark

## <a name="prepare-your-environment"></a>Préparation de votre environnement

Avant de commencer, assurez-vous que `dotnet`vous `java`pouvez exécuter `spark-shell` ,, `mvn`, à partir de votre ligne de commande. Si votre environnement est déjà préparé, vous pouvez passer à la section suivante. Si vous ne pouvez pas exécuter une partie ou l’ensemble des commandes, suivez les étapes ci-dessous.

1. Téléchargez et installez le [Kit de développement logiciel (SDK) .net Core 2.1 x](https://dotnet.microsoft.com/download/dotnet-core/2.1). L’installation du kit de `dotnet` développement logiciel (SDK) ajoute le chaîne d’outils à votre chemin. Utilisez la commande `dotnet --version` PowerShell pour vérifier l’installation.

2. Installez [Visual studio 2017](https://www.visualstudio.com/downloads/) ou [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) avec les dernières mises à jour. Vous pouvez utiliser Community, Professional ou Enterprise. La version de la communauté est gratuite.

   Choisissez les charges de travail suivantes au cours de l’installation:
      * Développement .NET Desktop
          * Tous les composants requis
          * Outils de développement .NET Framework 4.6.1
      * Développement multiplateforme .NET Core
          * Tous les composants requis

3. Installez [Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

    * Sélectionnez la version appropriée pour votre système d’exploitation. Par exemple, sélectionnez **JDK-8u201-Windows-x64. exe** pour un ordinateur Windows x64.
    * Utilisez la commande `java -version` PowerShell pour vérifier l’installation.

4. Installez [Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi).
    * Téléchargez [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).
    * Extraire dans un répertoire local. Par exemple, `c:\bin\apache-maven-3.6.0\`.
    * Ajoutez Apache Maven à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml). Si vous avez extrait `c:\bin\apache-maven-3.6.0\`vers, vous devez `c:\bin\apache-maven-3.6.0\bin` ajouter à votre chemin d’accès.
    * Utilisez la commande `mvn -version` PowerShell pour vérifier l’installation.

5. Installez [Apache Spark 2.3 +](https://spark.apache.org/downloads.html). Apache Spark 2.4 + n’est pas pris en charge.
    * Téléchargez [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) et extrayez-le dans un dossier local à l’aide d’un outil tel que [7-zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/). Par exemple, vous pouvez l’extraire vers `c:\bin\spark-2.3.2-bin-hadoop2.7\`.
    * Ajoutez Apache Spark à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml). Si vous avez extrait `c:\bin\spark-2.3.2-bin-hadoop2.7\`vers, vous devez `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` ajouter à votre chemin d’accès.
    * Ajoutez une [nouvelle variable](https://www.java.com/en/download/help/path.xml) d’environnement `SPARK_HOME`appelée. Si vous avez extrait `C:\bin\spark-2.3.2-bin-hadoop2.7\`vers, `C:\bin\spark-2.3.2-bin-hadoop2.7\` utilisez pour la valeur de la **variable**.
    * Vérifiez que vous êtes en mesure `spark-shell` d’exécuter à partir de la ligne de commande.

6. Configurez [winutils](https://github.com/steveloughran/winutils).
    * Téléchargez le fichier binaire **winutils. exe** à partir du [référentiel winutils](https://github.com/steveloughran/winutils). Sélectionnez la version de Hadoop avec laquelle la distribution Spark a été compilée. Par exemple, vous utilisez **Hadoop-2.7.1** pour **Spark 2.3.2**. La version Hadoop est annotée à la fin du nom du dossier d’installation de Spark.
    * Enregistrez le fichier binaire **winutils. exe** dans le répertoire de votre choix. Par exemple, `c:\hadoop\bin`.
    * Définissez `HADOOP_HOME` pour refléter le répertoire avec **winutils. exe** sans `bin`. Par exemple, `c:\hadoop`.
    * Définissez la variable d’environnement PATH à `%HADOOP_HOME%\bin`inclure.

Vérifiez que vous pouvez `dotnet`exécuter, `java`, `mvn`, `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante.

## <a name="download-the-microsoftsparkworker-release"></a>Télécharger la version Microsoft. Spark. Worker

1. Téléchargez la version [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) à partir de la page .net for Apache Spark GitHub releases sur votre ordinateur local. Par exemple, vous pouvez le télécharger sur le chemin d' `c:\bin\Microsoft.Spark.Worker\`accès,.

2. Créez une [nouvelle variable](https://www.java.com/en/download/help/path.xml) d’environnement `DotnetWorkerPath` appelée et affectez-lui le répertoire dans lequel vous avez téléchargé et extrait **Microsoft. Spark. Worker**. Par exemple, `c:\bin\Microsoft.Spark.Worker`.

## <a name="clone-the-net-for-apache-spark-github-repo"></a>Cloner le .NET pour Apache Spark GitHub référentiel

Utilisez la commande [GitBash](https://gitforwindows.org/) suivante pour cloner le .net pour Apache Spark référentiel sur votre ordinateur.

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a>Écrire un .NET pour une application Apache Spark

1. Ouvrez **Visual Studio** et accédez à **fichier > créer un projet > application console (.net Core)** . Nommez l’application **HelloSpark**.

2. Installez le [package NuGet Microsoft. Spark](https://www.nuget.org/profiles/spark). Pour plus d’informations sur l’installation des packages NuGet, consultez [différentes façons d’installer un package NuGet](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).

3. Dans **Explorateur de solutions**, ouvrez **Program.cs** et écrivez le code C# suivant:

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. Générez la solution.

## <a name="run-your-net-for-apache-spark-app"></a>Exécuter votre application .NET pour Apache Spark

1. Ouvrez **PowerShell** et remplacez le répertoire par le dossier dans lequel votre application est stockée.

   ```powershell
   cd <your-app-output-directory>
   ```

2. Créez un fichier nommé **People. JSON** avec le contenu suivant:

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. Utilisez la commande PowerShell suivante pour exécuter votre application:

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

Félicitations ! Vous avez créé et exécuté une application .NET pour Apache Spark.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez appris à :
> [!div class="checklist"]
> * Préparer votre environnement Windows pour .NET pour la Apache Spark
> * Télécharger **Microsoft. Spark. Worker**
> * Générez et exécutez une application .NET simple pour Apache Spark

Consultez la page des ressources pour en savoir plus.
> [!div class="nextstepaction"]
> [.NET pour les ressources de Apache Spark](../resources/index.md)
