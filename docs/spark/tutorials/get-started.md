---
title: Bien démarrer avec .NET pour Apache Spark
description: Découvrez comment exécuter une application .NET pour Apache Spark avec .NET Core sur Windows.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c4dbce74d0d8c0a682250a8021d983ef2990971f
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250326"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Tutoriel : Bien démarrer avec .NET pour Apache Spark

Ce tutoriel vous explique comment exécuter une application .NET pour Apache Spark avec .NET Core sur Windows.

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
>
> * Préparer votre environnement Windows pour .NET pour Apache Spark
> * Télécharger **Microsoft.Spark.Worker**
> * Générer et exécuter une application .NET pour Apache Spark simple

## <a name="prepare-your-environment"></a>Préparer votre environnement

Avant de commencer, vérifiez que vous pouvez exécuter `dotnet`, `java`, `mvn` et `spark-shell` à partir de votre ligne de commande. Si votre environnement est déjà préparé, vous pouvez passer à la section suivante. Si vous ne pouvez pas exécuter tout ou partie des commandes, suivez les étapes ci-dessous.

1. Téléchargez et installez le [SDK .NET Core 2.1x](https://dotnet.microsoft.com/download/dotnet-core/2.1). L’installation du SDK ajoute la chaîne d’outils `dotnet` à votre variable d’environnement PATH. Utilisez la commande PowerShell `dotnet --version` pour vérifier l’installation.

2. Installez [Visual Studio 2017](https://www.visualstudio.com/downloads/) ou [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) avec les dernières mises à jour. Vous pouvez utiliser l’édition Community, Professional ou Enterprise. La version Community est gratuite.

   Choisissez les charges de travail suivantes lors de l’installation :
      * Développement .NET Desktop
          * Tous les composants nécessaires
          * Outils de développement .NET Framework 4.6.1
      * Développement multiplateforme .NET Core
          * Tous les composants nécessaires

3. Installez [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

    * Sélectionnez la version appropriée pour votre système d’exploitation. Par exemple, sélectionnez **jdk-8u201-windows-x64.exe** pour une machine Windows x64.
    * Utilisez la commande PowerShell `java -version` pour vérifier l’installation.

4. Installez [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi).
    * Téléchargez [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).
    * Extrayez-le dans un répertoire local. Par exemple, `c:\bin\apache-maven-3.6.0\`.
    * Ajoutez Apache Maven à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml). Si vous avez fait l’extraction vers `c:\bin\apache-maven-3.6.0\`, vous devez ajouter `c:\bin\apache-maven-3.6.0\bin` à votre variable d’environnement PATH.
    * Utilisez la commande PowerShell `mvn -version` pour vérifier l’installation.

5. Installez [Apache Spark 2.3+](https://spark.apache.org/downloads.html). Apache Spark 2.4+ n’est pas pris en charge.
    * Téléchargez [Apache Spark 2.3+](https://spark.apache.org/downloads.html) et extrayez-le dans un dossier local en utilisant un outil comme [7-zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/). Par exemple, vous pouvez l’extraire vers `c:\bin\spark-2.3.2-bin-hadoop2.7\`.
    * Ajoutez Apache Spark à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml). Si vous avez fait l’extraction vers `c:\bin\spark-2.3.2-bin-hadoop2.7\`, vous devez ajouter `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` à votre variable d’environnement PATH.
    * Ajoutez une [nouvelle variable d’environnement](https://www.java.com/en/download/help/path.xml) appelée `SPARK_HOME`. Si vous avez fait l’extraction vers `C:\bin\spark-2.3.2-bin-hadoop2.7\`, utilisez `C:\bin\spark-2.3.2-bin-hadoop2.7\` pour la **Valeur de la variable**.
    * Vérifiez que vous pouvez exécuter `spark-shell` à partir de votre ligne de commande.

6. Configurez [WinUtils](https://github.com/steveloughran/winutils).
    * Téléchargez le fichier binaire **winutils.exe** à partir du [dépôt WinUtils](https://github.com/steveloughran/winutils). Sélectionnez la version d’Hadoop avec laquelle la distribution Spark a été compilée. Par exemple, vous utilisez **hadoop-2.7.1** pour **Spark 2.3.2**. La version d’Hadoop est annotée à la fin du nom du dossier d’installation de Spark.
    * Enregistrez le fichier binaire **winutils.exe** dans le répertoire de votre choix. Par exemple, `c:\hadoop\bin`.
    * Définissez `HADOOP_HOME` de façon à refléter le répertoire avec **winutils.exe** sans `bin`. Par exemple, `c:\hadoop`.
    * Définissez la variable d’environnement PATH pour y inclure `%HADOOP_HOME%\bin`.

Vérifiez bien que vous pouvez exécuter `dotnet`, `java`, `mvn` et `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante.

## <a name="download-the-microsoftsparkworker-release"></a>Télécharger la version de Microsoft.Spark.Worker

1. Téléchargez la version de [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) à partir de la page GitHub des versions de .NET pour Apache Spark sur votre machine locale. Par exemple, vous pouvez la télécharger dans le chemin `c:\bin\Microsoft.Spark.Worker\`.

2. Créez une [variable d’environnement](https://www.java.com/en/download/help/path.xml) appelée `DOTNET_WORKER_DIR` et définissez-la sur le répertoire où vous avez téléchargé et extrait **Microsoft.Spark.Worker**. Par exemple, `c:\bin\Microsoft.Spark.Worker`.

## <a name="clone-the-net-for-apache-spark-github-repo"></a>Cloner le dépôt GitHub .NET pour Apache Spark

Utilisez la commande [GitBash](https://gitforwindows.org/) suivante pour cloner le dépôt .NET pour Apache Spark sur votre machine.

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a>Écrire une application .NET pour Apache Spark

1. Ouvrez **Visual Studio** et accédez à **Fichier > Créer un projet > Application console (.NET Core)** . Nommez l’application **HelloSpark**.

2. Installez le [package NuGet Microsoft.Spark](https://www.nuget.org/profiles/spark). Pour plus d’informations sur l’installation des packages NuGet, consultez [Les différentes façons d’installer un package NuGet](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).

3. Dans l’**Explorateur de solutions**, ouvrez **Program.cs** et écrivez le code C# suivant :

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. Générez la solution.

## <a name="run-your-net-for-apache-spark-app"></a>Exécuter votre application .NET pour Apache Spark

1. Ouvrez **PowerShell** et remplacez le répertoire par le dossier où votre application est stockée.

   ```powershell
   cd <your-app-output-directory>
   ```

2. Créez un fichier appelé **people.json** avec le contenu suivant :

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. Utilisez la commande PowerShell suivante pour exécuter votre application :

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

Félicitations ! Vous avez créé et exécuté une application .NET pour Apache Spark.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Préparer votre environnement Windows pour .NET pour Apache Spark
> * Télécharger **Microsoft.Spark.Worker**
> * Générer et exécuter une application .NET pour Apache Spark simple

Pour plus d’informations, consultez la page des ressources.
> [!div class="nextstepaction"]
> [Ressources .NET pour Apache Spark](../resources/index.md)
