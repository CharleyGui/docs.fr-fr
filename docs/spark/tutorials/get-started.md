---
title: Bien démarrer avec .NET pour Apache Spark
description: Découvrez comment exécuter une application .NET pour Apache Spark à l’aide de .NET Core sur Windows, MacOS et Ubuntu.
ms.date: 01/31/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7375c385245a05d7dc29d5df89d875bf6cb4141a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187545"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Tutorial: Démarrer avec .NET pour Apache Spark

Ce tutoriel vous apprend à exécuter un .NET pour Apache Spark app en utilisant .NET Core sur Windows, MacOS, et Ubuntu.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> * Préparez votre environnement pour .NET pour Apache Spark
> * Écrivez votre premier .NET pour Apache Spark application
> * Construisez et exécutez votre simple .NET pour Apache Spark application

## <a name="prepare-your-environment"></a>Préparation de votre environnement

Avant de commencer à écrire votre application, vous devez configurer certaines dépendances préalables. Si vous `dotnet`pouvez `java` `mvn`exécuter `spark-shell` , , , à partir de votre environnement de ligne de commande, alors votre environnement est déjà préparé et vous pouvez passer à la section suivante. Si vous ne pouvez pas exécuter l’une ou l’autre des commandes, faites les étapes suivantes.

### <a name="1-install-net"></a>1. Installer .NET

Pour commencer à créer des applications .NET, vous devez télécharger et installer le .NET SDK (Software Development Kit).

Téléchargez et installez le [SDK .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.1). L’installation du SDK ajoute la chaîne d’outils `dotnet` à votre variable d’environnement PATH.

Une fois que vous avez installé le .NET Core SDK, ouvrez une nouvelle invite de commande ou terminal et exécutez `dotnet`.

Si la commande s’exécute et imprime des informations sur la façon d’utiliser dotnet, peut passer à l’étape suivante. Si vous `'dotnet' is not recognized as an internal or external command` recevez une erreur, assurez-vous d’ouvrir une **nouvelle** invite ou terminal de commande avant d’exécuter la commande.

### <a name="2-install-java"></a>2. Installer Java

Installez [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) pour Windows et MacOS, ou [OpenJDK 8](https://openjdk.java.net/install/) pour Ubuntu.

Sélectionnez la version appropriée pour votre système d’exploitation. Par exemple, sélectionnez **jdk-8u201-windows-x64.exe** pour une machine Windows x64 (comme indiqué ci-dessous) ou **jdk-8u231-macosx-x64.dmg** pour MacOS. Ensuite, utilisez `java` la commande pour vérifier l’installation.

![Télécharger Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. Installer un logiciel de compression

Apache Spark est téléchargé sous forme de fichier compressé .tgz. Utilisez un programme d’extraction, comme [7-Zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/), pour extraire le fichier.

### <a name="4-install-apache-spark"></a>4. Installer Apache Spark

[Télécharger et installer Apache Spark](https://spark.apache.org/downloads.html). Vous devrez choisir parmi la version 2.3.md ou 2.4.0, 2.4.1, 2.4.3, ou 2.4.4 (.NET pour Apache Spark n’est pas compatible avec d’autres versions d’Apache Spark).

Les commandes utilisées dans les étapes suivantes supposent que vous avez [téléchargé et installé Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz). Si vous souhaitez utiliser une version différente, remplacez **2.4.1** par le numéro de version approprié. Ensuite, extraire le fichier **.tar** et les fichiers Apache Spark.

Pour extraire le fichier **.tar** imbriqué :

* Localisez le fichier **spark-2.4.1-bin-hadoop2.7.tgz** que vous avez téléchargé.
* Cliquez à droite sur le fichier et sélectionnez **7-Zip -> Extrait ici**.
* **spark-2.4.1-bin-hadoop2.7.tar** est créé à côté du fichier **.tgz** que vous avez téléchargé.

Pour extraire les fichiers Apache Spark :

* Cliquez à droite sur **spark-2.4.1-bin-hadoop2.7.tar** et sélectionnez **7-Zip -> Fichiers d’extrait...**
* Entrez **C: 'bin** dans l’extrait **au** champ.
* Décochez la case à cocher sous **l’extrait au** champ.
* Sélectionnez **OK**.
* Les fichiers Apache Spark sont extraits à C: 'bin’spark-2.4.1-bin-hadoop2.7

![Installation de Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

Exécutez les commandes suivantes pour définir les variables de l’environnement utilisées pour localiser Apache Spark sur **Windows**:

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

Exécutez les commandes suivantes pour définir les variables de l’environnement utilisées pour localiser Apache Spark sur **MacOS** et **Ubuntu**:

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

Une fois que vous avez tout installé et définissez vos variables d’environnement, ouvrez une **nouvelle** invite de commande ou terminal et exécutez la commande suivante :

`%SPARK_HOME%\bin\spark-submit --version`

Si la commande s’exécute et imprime des informations de version, vous pouvez passer à l’étape suivante.

Si vous `'spark-submit' is not recognized as an internal or external command` recevez une erreur, assurez-vous d’ouvrir une **nouvelle** invite de commande.

### <a name="5-install-net-for-apache-spark"></a>5. Installer .NET pour Apache Spark

Téléchargez la version [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) du .NET pour Apache Spark GitHub. Par exemple, si vous êtes sur une machine Windows et prévoyez d’utiliser .NET Core, [téléchargez la version netcore3.1 de Windows x64](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).

Pour extraire le Microsoft.Spark.Worker:

* Localiser le **fichier Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** fichier que vous avez téléchargé.
* Cliquez à droite et sélectionnez **7-Zip -> Fichiers d’extrait...**.
* Entrez **C: 'bin** dans l’extrait **au** champ.
* Décochez la case à cocher sous **l’extrait au** champ.
* Sélectionnez **OK**.

![Installer .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. Installer WinUtils (Windows uniquement)

.NET pour Apache Spark nécessite WinUtils d’être installé aux côtés d’Apache Spark. [Télécharger winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Ensuite, copiez WinUtils en **C : 'bin’spark-2.4.1-bin-hadoop2.7'bin**.

> [!NOTE]
> Si vous utilisez une version différente de Hadoop, qui est annotée à la fin de votre nom de dossier d’installation Spark, [sélectionnez la version de WinUtils](https://github.com/steveloughran/winutils) qui est compatible avec votre version de Hadoop.

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. Définir DOTNET_WORKER_DIR et vérifier les dépendances

Exécutez l’une des commandes `DOTNET_WORKER_DIR` suivantes pour définir la variable d’environnement, qui est utilisée par les applications .NET pour localiser .NET pour Apache Spark.

Sur **Windows**, créer une nouvelle variable `DOTNET_WORKER_DIR` `C:\bin\Microsoft.Spark.Worker\` [d’environnement](https://www.java.com/en/download/help/path.xml) et le définir à l’annuaire où vous avez téléchargé et extrait le Microsoft.Spark.Worker (par exemple, ).

Sur **MacOS**, créer une `export DOTNET_WORKER_DIR <your_path>` nouvelle variable d’environnement en utilisant et le définir à l’annuaire où vous avez téléchargé et extrait le Microsoft.Spark.Worker (par exemple, *'/bin/Microsoft.Spark.Worker/*).

Sur **Ubuntu**, créer une nouvelle variable `DOTNET_WORKER_DIR` [d’environnement](https://help.ubuntu.com/community/EnvironmentVariables) et le définir à l’annuaire où vous avez téléchargé et extrait le Microsoft.Spark.Worker (par exemple, *'/bin/Microsoft.Spark.Worker*).

Enfin, vérifiez que vous `dotnet`pouvez `java` `mvn`exécuter `spark-shell` , , , à partir de votre ligne de commande avant de passer à la section suivante.

## <a name="write-a-net-for-apache-spark-app"></a>Écrire une application .NET pour Apache Spark

### <a name="1-create-a-console-app"></a>1. Créer une application console

Dans votre application ou terminal de commande, exécutez les commandes suivantes pour créer une nouvelle application de console :

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

La `dotnet` commande `new` crée une `console` application de type pour vous. Le `-o` paramètre crée un répertoire nommé *mySparkApp* où votre application est stockée et le remplit avec les fichiers requis. La `cd mySparkApp` commande modifie l’annuaire de l’annuaire de l’application que vous venez de créer.

### <a name="2-install-nuget-package"></a>2. Installer le paquet NuGet

Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft.Spark. Dans votre commande ou terminal, exécutez la commande suivante :

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a>3. Codez votre application

Ouvrez *Program.cs* dans Visual Studio Code, ou n’importe quel éditeur de texte, et remplacez tout le code par ce qui suit :

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-create-and-add-a-data-file"></a>4. Créer et ajouter un fichier de données

Ouvrez votre invite de commande ou terminal et naviguez dans votre dossier d’application.

```bash
cd <your-app-output-directory>
```

Votre application traite un fichier contenant des lignes de texte. Créez un fichier *input.txt* dans votre répertoire *mySparkApp,* contenant le texte suivant :

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Exécuter votre application .NET pour Apache Spark

1. Exécutez la commande suivante pour construire votre application :

   ```dotnetcli
   dotnet build
   ```

2. Exécutez la commande suivante pour soumettre votre demande pour exécuter sur Apache Spark :

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > Cette commande suppose que vous avez téléchargé Apache Spark et l’a ajouté à votre variable d’environnement PATH pour être en mesure d’utiliser `spark-submit`. Sinon, vous auriez à utiliser le chemin complet (par exemple, *C: 'bin’apache-spark’bin’spark-submit* ou *'/spark/bin/spark/spark-submit*).

3. Lorsque votre application s’exécute, les données de comptage de mot du fichier *input.txt* sont écrites sur la console.

Félicitations ! Vous avez créé et exécuté une application .NET pour Apache Spark.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Préparer votre environnement Windows pour .NET pour Apache Spark
> * Écrivez votre premier .NET pour Apache Spark application
> * Construisez et exécutez votre simple .NET pour Apache Spark application

Pour voir une vidéo expliquant les étapes ci-dessus, consultez le [.NET pour Apache Spark 101 série vidéo](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).

Pour plus d’informations, consultez la page des ressources.
> [!div class="nextstepaction"]
> [Ressources .NET pour Apache Spark](../resources/index.md)
