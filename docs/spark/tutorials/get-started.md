---
title: Bien démarrer avec .NET pour Apache Spark
description: Découvrez comment exécuter une application .NET pour Apache Spark avec .NET Core sur Windows.
ms.date: 11/04/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 679ee7660e96504768a781e1e384acab80362736
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743205"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Didacticiel : prise en main de .NET pour Apache Spark

Ce tutoriel vous explique comment exécuter une application .NET pour Apache Spark avec .NET Core sur Windows.

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
>
> * Préparer votre environnement Windows pour .NET pour Apache Spark
> * Écrire votre première application .NET pour Apache Spark
> * Générez et exécutez votre application .NET simple pour Apache Spark

## <a name="prepare-your-environment"></a>Préparer votre environnement

Avant de commencer à écrire votre application, vous devez configurer certaines dépendances de la configuration requise. Si vous pouvez exécuter `dotnet`, `java`, `mvn`, `spark-shell` à partir de votre environnement de ligne de commande, votre environnement est déjà préparé et vous pouvez passer à la section suivante. Si vous ne pouvez pas exécuter une partie ou l’ensemble des commandes, procédez comme suit.

### <a name="1-install-net"></a>1. installer .NET

Pour commencer à créer des applications .NET, vous devez télécharger et installer le kit de développement logiciel (SDK) .NET.

Téléchargez et installez le [kit SDK .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.0). L’installation du SDK ajoute la chaîne d’outils `dotnet` à votre variable d’environnement PATH.

Une fois que vous avez installé le kit SDK .NET Core, ouvrez une nouvelle invite de commandes et exécutez `dotnet`.

Si la commande s’exécute et imprime des informations sur l’utilisation de DotNet, peut passer à l’étape suivante. Si vous recevez une erreur de `'dotnet' is not recognized as an internal or external command`, veillez à ouvrir une **nouvelle** invite de commandes avant d’exécuter la commande.

### <a name="2-install-java"></a>2. installer Java

Installez [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

Sélectionnez la version appropriée pour votre système d’exploitation. Par exemple, sélectionnez **jdk-8u201-windows-x64.exe** pour une machine Windows x64. Ensuite, utilisez la commande `java` pour vérifier l’installation.

![Téléchargement Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-7-zip"></a>3. Installer 7-zip

Apache Spark est téléchargé en tant que fichier. tgz compressé. Utilisez un programme d’extraction, tel que 7-zip, pour extraire le fichier.

* Visitez [7-téléchargements zip](https://www.7-zip.org/).
* Dans le premier tableau de la page, sélectionnez le téléchargement 32 bits x86 ou 64 bits x64, en fonction de votre système d’exploitation.
* Une fois le téléchargement terminé, exécutez le programme d’installation.

![Téléchargement de 7Zip](https://dotnet.microsoft.com/static/images/7-zip-downloads.png?v=W6qWtFC1tTMKv3YGXz7lBa9F3M22uWyTvkMmunyroNk)

### <a name="4-install-apache-spark"></a>4. Installez Apache Spark

[Téléchargez et installez Apache Spark](https://spark.apache.org/downloads.html). Vous devez effectuer une sélection dans la version 2,3. * ou 2.4.0, 2.4.1, 2.4.3 ou 2.4.4 (.NET pour Apache Spark n’est pas compatible avec les autres versions de Apache Spark).

Les commandes utilisées dans les étapes suivantes supposent que vous avez [téléchargé et installé Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz). Si vous souhaitez utiliser une version différente, remplacez **2.4.1** par le numéro de version approprié. Ensuite, extrayez le fichier **. tar** et les fichiers de Apache Spark.

Pour extraire le fichier **. tar** imbriqué :

* Localisez le fichier **Spark-2.4.1-bin-Hadoop 2.7. tgz** que vous avez téléchargé.
* Cliquez avec le bouton droit sur le fichier et sélectionnez **7-zip-> extraire ici**.
* **Spark-2.4.1-bin-Hadoop 2.7. tar** est créé avec le fichier **. tgz** que vous avez téléchargé.

Pour extraire les fichiers de Apache Spark :

* Cliquez avec le bouton droit sur **Spark-2.4.1-bin-Hadoop 2.7. tar** et sélectionnez **7-zip-> extraire les fichiers...**
* Entrez **C:\bin** dans le champ **extraire vers** .
* Désactivez la case à cocher sous le champ **extraire vers** .
* Sélectionnez **OK**.
* Les fichiers de Apache Spark sont extraits dans C:\bin\spark-2.4.1-bin-hadoop2.7\

![Installer Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

Exécutez les commandes suivantes pour définir les variables d’environnement utilisées pour localiser Apache Spark :

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

Une fois que vous avez installé tout et défini vos variables d’environnement, ouvrez une **nouvelle** invite de commandes et exécutez la commande suivante :

`%SPARK_HOME%\bin\spark-submit --version`

Si la commande s’exécute et imprime des informations de version, vous pouvez passer à l’étape suivante.

Si vous recevez une erreur `'spark-submit' is not recognized as an internal or external command`, assurez-vous que vous avez ouvert une **nouvelle** invite de commandes.

### <a name="5-install-net-for-apache-spark"></a>5. installer .NET pour Apache Spark

Téléchargez la version [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) à partir du .net pour Apache Spark github. Par exemple, si vous êtes sur un ordinateur Windows et que vous envisagez d’utiliser .NET Core, [Téléchargez la version Windows x64 netcoreapp 2.1](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).

Pour extraire Microsoft. Spark. Worker :

* Localisez le fichier **Microsoft. Spark. Worker. netcoreapp 2.1. Win-x64-0.6.0. zip** que vous avez téléchargé.
* Cliquez avec le bouton droit et sélectionnez **7-zip-> extraire les fichiers...** .
* Entrez **C:\bin** dans le champ **extraire vers** .
* Désactivez la case à cocher sous le champ **extraire vers** .
* Sélectionnez **OK**.

![Installer .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils"></a>6. installer WinUtils

.NET pour Apache Spark nécessite l’installation de WinUtils avec Apache Spark. [Téléchargez winutils. exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Ensuite, copiez WinUtils dans **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.

> [!NOTE]
> Si vous utilisez une autre version de Hadoop, qui est annotée à la fin de votre nom de dossier d’installation Spark, [Sélectionnez la version de winutils](https://github.com/steveloughran/winutils) qui est compatible avec votre version de Hadoop.

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. définir des DOTNET_WORKER_DIR et vérifier les dépendances

Exécutez la commande suivante pour définir la variable d’environnement `DOTNET_WORKER_DIR`, qui est utilisée par les applications .NET pour localiser .NET pour Apache Spark :

`setx DOTNET_WORKER_DIR "C:\bin\Microsoft.Spark.Worker-0.6.0"`

Enfin, vérifiez que vous pouvez exécuter `dotnet`, `java``mvn`, `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante.

## <a name="write-a-net-for-apache-spark-app"></a>Écrire une application .NET pour Apache Spark

### <a name="1-create-a-console-app"></a>1. créer une application console

À l’invite de commandes, exécutez les commandes suivantes pour créer une nouvelle application console :

```console
dotnet new console -o mySparkApp
cd mySparkApp
```

La commande `dotnet` crée pour vous une application `new` de type `console`. Le paramètre `-o` crée un répertoire nommé *mySparkApp* dans lequel votre application est stockée et le remplit avec les fichiers requis. La commande `cd mySparkApp` remplace le répertoire par le répertoire d’application que vous venez de créer.

### <a name="2-install-nuget-package"></a>2. installer le package NuGet

Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft. Spark. Dans votre invite de commandes, exécutez la commande suivante :

`dotnet add package Microsoft.Spark --version 0.6.0`

### <a name="3-code-your-app"></a>3. codez votre application

Ouvrez *Program.cs* dans Visual Studio code ou un éditeur de texte, puis remplacez tout le code par ce qui suit :

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            var spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            var words = dataFrame
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

### <a name="4-add-data-file"></a>4. Ajouter un fichier de données

Votre application traite un fichier contenant des lignes de texte. Créez un fichier *Input. txt* dans votre répertoire *mySparkApp* , contenant le texte suivant :

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Exécuter votre application .NET pour Apache Spark

1. Exécutez la commande suivante pour générer votre application :

   ```dotnetcli
   dotnet build
   ```

2. Exécutez la commande suivante pour envoyer votre application pour qu’elle s’exécute sur Apache Spark :

   ```powershell
   %SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local bin\Debug\netcoreapp3.0\microsoft-spark-2.4.x-0.6.0.jar dotnet bin\Debug\netcoreapp3.0\mySparkApp.dll
   ```

3. Lorsque votre application s’exécute, les données de nombre de mots du fichier *Input. txt* sont écrites dans la console.

Félicitations ! Vous avez créé et exécuté une application .NET pour Apache Spark.

## <a name="next-steps"></a>Étapes suivantes :

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Préparer votre environnement Windows pour .NET pour Apache Spark
> * Écrire votre première application .NET pour Apache Spark
> * Générez et exécutez votre application .NET simple pour Apache Spark

Pour voir une vidéo expliquant les étapes ci-dessus, extrayez la [série de vidéos .net pour Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).

Pour plus d’informations, consultez la page des ressources.
> [!div class="nextstepaction"]
> [Ressources .NET pour Apache Spark](../resources/index.md)
