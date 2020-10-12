---
title: Bien démarrer avec .NET pour Apache Spark
description: Découvrez comment exécuter un .NET pour Apache Spark application à l’aide de .NET Core sur Windows, macOS et Ubuntu.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: d4f44d095fffdfa05b82516cfe79700f9e239110
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955406"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Didacticiel : prise en main de .NET pour Apache Spark

Ce didacticiel vous apprend à exécuter un .NET pour Apache Spark application à l’aide de .NET Core sur Windows, macOS et Ubuntu.

Dans ce tutoriel, vous allez découvrir comment :

> [!div class="checklist"]
>
> * Préparer votre environnement pour .NET pour la Apache Spark
> * Écrire votre première application .NET pour Apache Spark
> * Générez et exécutez votre application .NET pour Apache Spark

## <a name="prepare-your-environment"></a>Préparation de votre environnement

Avant de commencer à écrire votre application, vous devez configurer certaines dépendances de la configuration requise. Si vous pouvez exécuter `dotnet` , `java` , `spark-shell` à partir de votre environnement de ligne de commande, votre environnement est déjà préparé et vous pouvez passer à la section suivante. Si vous ne pouvez pas exécuter une partie ou l’ensemble des commandes, procédez comme suit.

### <a name="1-install-net"></a>1. installer .NET

Pour commencer à créer des applications .NET, vous devez télécharger et installer le kit de développement logiciel (SDK) .NET.

Téléchargez et installez le [SDK .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.1). L’installation du SDK ajoute la chaîne d’outils `dotnet` à votre variable d’environnement PATH.

Une fois que vous avez installé le kit SDK .NET Core, ouvrez une nouvelle invite de commandes ou un terminal, puis exécutez `dotnet` .

Si la commande s’exécute et imprime des informations sur l’utilisation de DotNet, peut passer à l’étape suivante. Si vous recevez une `'dotnet' is not recognized as an internal or external command` erreur, assurez-vous d’avoir ouvert une **nouvelle** invite de commandes ou un terminal avant d’exécuter la commande.

### <a name="2-install-java"></a>2. installer Java

Installez [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) pour Windows et MacOS, ou [openjdk 8](https://openjdk.java.net/install/) pour Ubuntu.

Sélectionnez la version appropriée pour votre système d’exploitation. Par exemple, sélectionnez **jdk-8u201-windows-x64.exe** pour un ordinateur Windows x64 (comme indiqué ci-dessous) ou **JDK-8u231-MacOSX-x64. dmg** pour MacOS. Ensuite, utilisez la commande `java` pour vérifier l’installation.

![Téléchargement Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. installer le logiciel de compression

Apache Spark est téléchargé en tant que fichier. tgz compressé. Utilisez un programme d’extraction, tel que [7-zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/), pour extraire le fichier.

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

![Installation de Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

Exécutez les commandes suivantes pour définir les variables d’environnement utilisées pour localiser Apache Spark. Sur Windows, veillez à exécuter l’invite de commandes en mode administrateur.

#### <a name="windows"></a>[Windows](#tab/windows)

```console
setx /M HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx /M SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx /M PATH "%PATH%;%HADOOP_HOME%;%SPARK_HOME%\bin"
```

#### <a name="maclinux"></a>[Mac/Linux](#tab/linux)

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

---

Une fois que vous avez installé tout et défini vos variables d’environnement, ouvrez une **nouvelle** invite de commandes ou un terminal, puis exécutez la commande suivante :

```text
spark-submit --version
```

Si la commande s’exécute et imprime des informations de version, vous pouvez passer à l’étape suivante.

Si vous recevez une `'spark-submit' is not recognized as an internal or external command` erreur, assurez-vous que vous avez ouvert une **nouvelle** invite de commandes.

### <a name="5-install-net-for-apache-spark"></a>5. installer .NET pour Apache Spark

Téléchargez la version [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) à partir du .net pour Apache Spark github. Par exemple, si vous êtes sur un ordinateur Windows et que vous envisagez d’utiliser .NET Core, [Téléchargez la version Windows x64 netcoreapp 3.1](https://github.com/dotnet/spark/releases).

Pour extraire Microsoft. Spark. Worker :

* Localisez le fichier **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** que vous avez téléchargé.
* Cliquez avec le bouton droit et sélectionnez **7-zip-> extraire les fichiers...**.
* Entrez **C:\bin** dans le champ **extraire vers** .
* Désactivez la case à cocher sous le champ **extraire vers** .
* Sélectionnez **OK**.

![Installer .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. installer WinUtils (Windows uniquement)

.NET pour Apache Spark nécessite l’installation de WinUtils avec Apache Spark. [Téléchargez winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Ensuite, copiez WinUtils dans **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.

> [!NOTE]
> Si vous utilisez une autre version de Hadoop, qui est annotée à la fin de votre nom de dossier d’installation Spark, [Sélectionnez la version de winutils](https://github.com/steveloughran/winutils) qui est compatible avec votre version de Hadoop.

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. définir des DOTNET_WORKER_DIR et vérifier les dépendances

Exécutez l’une des commandes suivantes pour définir la `DOTNET_WORKER_DIR` variable d’environnement, qui est utilisée par les applications .net pour localiser .net pour Apache Spark. Veillez à remplacer `<PATH-DOTNET_WORKER_DIR>` par le répertoire dans lequel vous avez téléchargé et extrait le `Microsoft.Spark.Worker` . Sur Windows, veillez à exécuter l’invite de commandes en mode administrateur.

#### <a name="windows"></a>[Windows](#tab/windows)

```console
setx /M DOTNET_WORKER_DIR <PATH-DOTNET-WORKER-DIR>
```

#### <a name="maclinux"></a>[Mac/Linux](#tab/linux)

```bash
export DOTNET_WORKER_DIR=<PATH-DOTNET-WORKER-DIR>
```

---

Enfin, vérifiez que vous pouvez exécuter `dotnet` , `java` , `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante.

## <a name="write-a-net-for-apache-spark-app"></a>Écrire une application .NET pour Apache Spark

### <a name="1-create-a-console-app"></a>1. créer une application console

Dans votre invite de commandes ou terminal, exécutez les commandes suivantes pour créer une nouvelle application console :

```dotnetcli
dotnet new console -o MySparkApp
cd MySparkApp
```

La `dotnet` commande crée une `new` application de type `console` pour vous. Le `-o` paramètre crée un répertoire nommé *MySparkApp* dans lequel votre application est stockée et le remplit avec les fichiers requis. La `cd MySparkApp` commande remplace le répertoire par le répertoire d’application que vous avez créé.

### <a name="2-install-nuget-package"></a>2. installer le package NuGet

Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft. Spark. Dans votre invite de commandes ou terminal, exécutez la commande suivante :

```dotnetcli
dotnet add package Microsoft.Spark
```

> [!NOTE]
> Ce didacticiel utilise la version la plus récente du `Microsoft.Spark` package NuGet, sauf indication contraire.

### <a name="3-write-your-app"></a>3. écrire votre application

Ouvrez *Program.cs* dans Visual Studio code ou un éditeur de texte, puis remplacez tout le code par ce qui suit :

```csharp
using Microsoft.Spark.Sql;
using static Microsoft.Spark.Sql.Functions;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create Spark session
            SparkSession spark =
                SparkSession
                    .Builder()
                    .AppName("word_count_sample")
                    .GetOrCreate();

            // Create initial DataFrame
            string filePath = args[0];
            DataFrame dataFrame = spark.Read().Text(filePath);

            //Count words
            DataFrame words =
                dataFrame
                    .Select(Split(Col("value")," ").Alias("words"))
                    .Select(Explode(Col("words")).Alias("word"))
                    .GroupBy("word")
                    .Count()
                    .OrderBy(Col("count").Desc());

            // Display results
            words.Show();

            // Stop Spark session
            spark.Stop();
        }
    }
}
```

[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) est le point d’entrée de Apache Spark applications, qui gère le contexte et les informations de votre application. À l’aide de la méthode [Text](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) , les données texte du fichier spécifié par le `filePath` sont lues dans un [tableau](xref:Microsoft.Spark.Sql.DataFrame). Un tableau est un moyen d’organiser les données en un ensemble de colonnes nommées. Ensuite, une série de transformations est appliquée pour fractionner les phrases dans le fichier, regrouper chacun des mots, les compter et les classer dans l’ordre décroissant. Le résultat de ces opérations est stocké dans un autre tableau. Notez qu’à ce stade, aucune opération n’a eu lieu parce que .NET pour Apache Spark a évalué tardivement les données. Ce n’est pas jusqu’à ce que la méthode [Show](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) soit appelée pour afficher le contenu des `words` tableau transformés dans la console que les opérations définies dans les lignes ci-dessus s’exécutent. Une fois que vous n’avez plus besoin de la session Spark, utilisez la méthode [Stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) pour arrêter votre session.

### <a name="4-create-data-file"></a>4. créer un fichier de données

Votre application traite un fichier contenant des lignes de texte. Créez un fichier appelé *input.txt* fichier dans votre répertoire *MySparkApp* , contenant le texte suivant :

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

Enregistrez les modifications et fermez le fichier.

## <a name="run-your-net-for-apache-spark-app"></a>Exécuter votre application .NET pour Apache Spark

Exécutez la commande suivante pour générer votre application :

```dotnetcli
dotnet build
```

Accédez à votre répertoire de sortie de génération et utilisez la `spark-submit` commande pour soumettre votre application afin qu’elle s’exécute sur Apache Spark. Veillez à remplacer  `<version>` par la version de votre Worker .net et `<path-of-input.txt>` par le chemin d’accès de votre fichier *input.txt* est stocké.

### <a name="windows"></a>[Windows](#tab/windows)

```console
spark-submit ^
--class org.apache.spark.deploy.dotnet.DotnetRunner ^
--master local ^
microsoft-spark-2.4.x-<version>.jar ^
dotnet MySparkApp.dll <path-of-input.txt>
```

### <a name="maclinux"></a>[Mac/Linux](#tab/linux)

```bash
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master local \
microsoft-spark-2.4.x-<version>.jar \
dotnet MySparkApp.dll <path-of-input.txt>
```

---

> [!NOTE]
> Cette commande suppose que vous avez téléchargé Apache Spark et que vous l’avez ajouté à votre variable d’environnement PATH pour pouvoir l’utiliser `spark-submit` . Dans le cas contraire, vous devez utiliser le chemin d’accès complet (par exemple, *C:\bin\apache-spark\bin\spark-Submit* ou *~/Spark/bin/Spark-Submit*).

Lorsque votre application s’exécute, les données de nombre de mots du fichier *input.txt* sont écrites dans la console.

```console
+------+-----+
|  word|count|
+------+-----+
|  .NET|    3|
|Apache|    2|
|   app|    2|
|  This|    2|
| Spark|    2|
| World|    1|
|counts|    1|
|   for|    1|
| words|    1|
|  with|    1|
| Hello|    1|
|  uses|    1|
+------+-----+
```

Félicitations ! Vous avez créé et exécuté une application .NET pour Apache Spark.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Préparer votre environnement pour .NET pour la Apache Spark
> * Écrire votre première application .NET pour Apache Spark
> * Générez et exécutez votre application .NET pour Apache Spark

Pour voir une vidéo expliquant les étapes ci-dessus, consultez la [série de vidéos .net pour Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).

Pour plus d’informations, consultez la page des ressources.
> [!div class="nextstepaction"]
> [Ressources .NET pour Apache Spark](../resources/index.md)
