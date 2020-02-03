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
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="4f975-103">Didacticiel : prise en main de .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="4f975-104">Ce tutoriel vous explique comment exécuter une application .NET pour Apache Spark avec .NET Core sur Windows.</span><span class="sxs-lookup"><span data-stu-id="4f975-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="4f975-105">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="4f975-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="4f975-106">Préparer votre environnement Windows pour .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="4f975-107">Écrire votre première application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="4f975-108">Générez et exécutez votre application .NET simple pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-108">Build and run your simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="4f975-109">Préparation de votre environnement</span><span class="sxs-lookup"><span data-stu-id="4f975-109">Prepare your environment</span></span>

<span data-ttu-id="4f975-110">Avant de commencer à écrire votre application, vous devez configurer certaines dépendances de la configuration requise.</span><span class="sxs-lookup"><span data-stu-id="4f975-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="4f975-111">Si vous pouvez exécuter `dotnet`, `java`, `mvn`, `spark-shell` à partir de votre environnement de ligne de commande, votre environnement est déjà préparé et vous pouvez passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="4f975-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="4f975-112">Si vous ne pouvez pas exécuter une partie ou l’ensemble des commandes, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="4f975-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="4f975-113">1. installer .NET</span><span class="sxs-lookup"><span data-stu-id="4f975-113">1. Install .NET</span></span>

<span data-ttu-id="4f975-114">Pour commencer à créer des applications .NET, vous devez télécharger et installer le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="4f975-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="4f975-115">Téléchargez et installez le [kit SDK .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="4f975-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span> <span data-ttu-id="4f975-116">L’installation du SDK ajoute la chaîne d’outils `dotnet` à votre variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="4f975-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="4f975-117">Une fois que vous avez installé le kit SDK .NET Core, ouvrez une nouvelle invite de commandes et exécutez `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="4f975-117">Once you've installed the .NET Core SDK, open a new command prompt and run `dotnet`.</span></span>

<span data-ttu-id="4f975-118">Si la commande s’exécute et imprime des informations sur l’utilisation de DotNet, peut passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="4f975-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="4f975-119">Si vous recevez une erreur de `'dotnet' is not recognized as an internal or external command`, veillez à ouvrir une **nouvelle** invite de commandes avant d’exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="4f975-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="4f975-120">2. installer Java</span><span class="sxs-lookup"><span data-stu-id="4f975-120">2. Install Java</span></span>

<span data-ttu-id="4f975-121">Installez [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span><span class="sxs-lookup"><span data-stu-id="4f975-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

<span data-ttu-id="4f975-122">Sélectionnez la version appropriée pour votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="4f975-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="4f975-123">Par exemple, sélectionnez **jdk-8u201-windows-x64.exe** pour une machine Windows x64.</span><span class="sxs-lookup"><span data-stu-id="4f975-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span> <span data-ttu-id="4f975-124">Ensuite, utilisez la commande `java` pour vérifier l’installation.</span><span class="sxs-lookup"><span data-stu-id="4f975-124">Then, use the command `java` to verify the installation.</span></span>

![Téléchargement Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-7-zip"></a><span data-ttu-id="4f975-126">3. Installer 7-zip</span><span class="sxs-lookup"><span data-stu-id="4f975-126">3. Install 7-zip</span></span>

<span data-ttu-id="4f975-127">Apache Spark est téléchargé en tant que fichier. tgz compressé.</span><span class="sxs-lookup"><span data-stu-id="4f975-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="4f975-128">Utilisez un programme d’extraction, tel que 7-zip, pour extraire le fichier.</span><span class="sxs-lookup"><span data-stu-id="4f975-128">Use an extraction program, like 7-zip, to extract the file.</span></span>

* <span data-ttu-id="4f975-129">Visitez [7-téléchargements zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="4f975-129">Visit [7-Zip downloads](https://www.7-zip.org/).</span></span>
* <span data-ttu-id="4f975-130">Dans le premier tableau de la page, sélectionnez le téléchargement 32 bits x86 ou 64 bits x64, en fonction de votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="4f975-130">In the first table on the page, select the 32-bit x86 or 64-bit x64 download, depending on your operating system.</span></span>
* <span data-ttu-id="4f975-131">Une fois le téléchargement terminé, exécutez le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="4f975-131">When the download completes, run the installer.</span></span>

![Téléchargement de 7Zip](https://dotnet.microsoft.com/static/images/7-zip-downloads.png?v=W6qWtFC1tTMKv3YGXz7lBa9F3M22uWyTvkMmunyroNk)

### <a name="4-install-apache-spark"></a><span data-ttu-id="4f975-133">4. Installez Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-133">4. Install Apache Spark</span></span>

<span data-ttu-id="4f975-134">[Téléchargez et installez Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="4f975-134">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="4f975-135">Vous devez effectuer une sélection dans la version 2,3. \* ou 2.4.0, 2.4.1, 2.4.3 ou 2.4.4 (.NET pour Apache Spark n’est pas compatible avec les autres versions de Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="4f975-135">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="4f975-136">Les commandes utilisées dans les étapes suivantes supposent que vous avez [téléchargé et installé Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span><span class="sxs-lookup"><span data-stu-id="4f975-136">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="4f975-137">Si vous souhaitez utiliser une version différente, remplacez **2.4.1** par le numéro de version approprié.</span><span class="sxs-lookup"><span data-stu-id="4f975-137">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="4f975-138">Ensuite, extrayez le fichier **. tar** et les fichiers de Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="4f975-138">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="4f975-139">Pour extraire le fichier **. tar** imbriqué :</span><span class="sxs-lookup"><span data-stu-id="4f975-139">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="4f975-140">Localisez le fichier **Spark-2.4.1-bin-Hadoop 2.7. tgz** que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="4f975-140">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="4f975-141">Cliquez avec le bouton droit sur le fichier et sélectionnez **7-zip-> extraire ici**.</span><span class="sxs-lookup"><span data-stu-id="4f975-141">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="4f975-142">**Spark-2.4.1-bin-Hadoop 2.7. tar** est créé avec le fichier **. tgz** que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="4f975-142">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="4f975-143">Pour extraire les fichiers de Apache Spark :</span><span class="sxs-lookup"><span data-stu-id="4f975-143">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="4f975-144">Cliquez avec le bouton droit sur **Spark-2.4.1-bin-Hadoop 2.7. tar** et sélectionnez **7-zip-> extraire les fichiers...**</span><span class="sxs-lookup"><span data-stu-id="4f975-144">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="4f975-145">Entrez **C:\bin** dans le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="4f975-145">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="4f975-146">Désactivez la case à cocher sous le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="4f975-146">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="4f975-147">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="4f975-147">Select **OK**.</span></span>
* <span data-ttu-id="4f975-148">Les fichiers de Apache Spark sont extraits dans C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="4f975-148">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![Installer Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="4f975-150">Exécutez les commandes suivantes pour définir les variables d’environnement utilisées pour localiser Apache Spark :</span><span class="sxs-lookup"><span data-stu-id="4f975-150">Run the following commands to set the environment variables used to locate Apache Spark:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="4f975-151">Une fois que vous avez installé tout et défini vos variables d’environnement, ouvrez une **nouvelle** invite de commandes et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4f975-151">Once you've installed everything and set your environment variables, open a **new** command prompt and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="4f975-152">Si la commande s’exécute et imprime des informations de version, vous pouvez passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="4f975-152">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="4f975-153">Si vous recevez une erreur `'spark-submit' is not recognized as an internal or external command`, assurez-vous que vous avez ouvert une **nouvelle** invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="4f975-153">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="4f975-154">5. installer .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-154">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="4f975-155">Téléchargez la version [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) à partir du .net pour Apache Spark github.</span><span class="sxs-lookup"><span data-stu-id="4f975-155">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="4f975-156">Par exemple, si vous êtes sur un ordinateur Windows et que vous envisagez d’utiliser .NET Core, [Téléchargez la version Windows x64 netcoreapp 2.1](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).</span><span class="sxs-lookup"><span data-stu-id="4f975-156">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp2.1 release](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).</span></span>

<span data-ttu-id="4f975-157">Pour extraire Microsoft. Spark. Worker :</span><span class="sxs-lookup"><span data-stu-id="4f975-157">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="4f975-158">Localisez le fichier **Microsoft. Spark. Worker. netcoreapp 2.1. Win-x64-0.6.0. zip** que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="4f975-158">Locate the **Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="4f975-159">Cliquez avec le bouton droit et sélectionnez **7-zip-> extraire les fichiers...** .</span><span class="sxs-lookup"><span data-stu-id="4f975-159">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="4f975-160">Entrez **C:\bin** dans le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="4f975-160">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="4f975-161">Désactivez la case à cocher sous le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="4f975-161">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="4f975-162">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="4f975-162">Select **OK**.</span></span>

![Installer .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils"></a><span data-ttu-id="4f975-164">6. installer WinUtils</span><span class="sxs-lookup"><span data-stu-id="4f975-164">6. Install WinUtils</span></span>

<span data-ttu-id="4f975-165">.NET pour Apache Spark nécessite l’installation de WinUtils avec Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="4f975-165">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="4f975-166">[Téléchargez winutils. exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="4f975-166">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="4f975-167">Ensuite, copiez WinUtils dans **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span><span class="sxs-lookup"><span data-stu-id="4f975-167">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="4f975-168">Si vous utilisez une autre version de Hadoop, qui est annotée à la fin de votre nom de dossier d’installation Spark, [Sélectionnez la version de winutils](https://github.com/steveloughran/winutils) qui est compatible avec votre version de Hadoop.</span><span class="sxs-lookup"><span data-stu-id="4f975-168">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="4f975-169">7. définir des DOTNET_WORKER_DIR et vérifier les dépendances</span><span class="sxs-lookup"><span data-stu-id="4f975-169">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="4f975-170">Exécutez la commande suivante pour définir la variable d’environnement `DOTNET_WORKER_DIR`, qui est utilisée par les applications .NET pour localiser .NET pour Apache Spark :</span><span class="sxs-lookup"><span data-stu-id="4f975-170">Run the following command to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark:</span></span>

`setx DOTNET_WORKER_DIR "C:\bin\Microsoft.Spark.Worker-0.6.0"`

<span data-ttu-id="4f975-171">Enfin, vérifiez que vous pouvez exécuter `dotnet`, `java``mvn`, `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="4f975-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="4f975-172">Écrire une application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="4f975-173">1. créer une application console</span><span class="sxs-lookup"><span data-stu-id="4f975-173">1. Create a console app</span></span>

<span data-ttu-id="4f975-174">À l’invite de commandes, exécutez les commandes suivantes pour créer une nouvelle application console :</span><span class="sxs-lookup"><span data-stu-id="4f975-174">In your command prompt, run the following commands to create a new console application:</span></span>

```console
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="4f975-175">La commande `dotnet` crée pour vous une application `new` de type `console`.</span><span class="sxs-lookup"><span data-stu-id="4f975-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="4f975-176">Le paramètre `-o` crée un répertoire nommé *mySparkApp* dans lequel votre application est stockée et le remplit avec les fichiers requis.</span><span class="sxs-lookup"><span data-stu-id="4f975-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="4f975-177">La commande `cd mySparkApp` remplace le répertoire par le répertoire d’application que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="4f975-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="4f975-178">2. installer le package NuGet</span><span class="sxs-lookup"><span data-stu-id="4f975-178">2. Install NuGet package</span></span>

<span data-ttu-id="4f975-179">Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="4f975-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="4f975-180">Dans votre invite de commandes, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4f975-180">In your command prompt, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.6.0`

### <a name="3-code-your-app"></a><span data-ttu-id="4f975-181">3. codez votre application</span><span class="sxs-lookup"><span data-stu-id="4f975-181">3. Code your app</span></span>

<span data-ttu-id="4f975-182">Ouvrez *Program.cs* dans Visual Studio code ou un éditeur de texte, puis remplacez tout le code par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4f975-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

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

### <a name="4-add-data-file"></a><span data-ttu-id="4f975-183">4. Ajouter un fichier de données</span><span class="sxs-lookup"><span data-stu-id="4f975-183">4. Add data file</span></span>

<span data-ttu-id="4f975-184">Votre application traite un fichier contenant des lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="4f975-184">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="4f975-185">Créez un fichier *Input. txt* dans votre répertoire *mySparkApp* , contenant le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="4f975-185">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="4f975-186">Exécuter votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-186">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="4f975-187">Exécutez la commande suivante pour générer votre application :</span><span class="sxs-lookup"><span data-stu-id="4f975-187">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="4f975-188">Exécutez la commande suivante pour envoyer votre application pour qu’elle s’exécute sur Apache Spark :</span><span class="sxs-lookup"><span data-stu-id="4f975-188">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```powershell
   %SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local bin\Debug\netcoreapp3.0\microsoft-spark-2.4.x-0.6.0.jar dotnet bin\Debug\netcoreapp3.0\mySparkApp.dll
   ```

3. <span data-ttu-id="4f975-189">Lorsque votre application s’exécute, les données de nombre de mots du fichier *Input. txt* sont écrites dans la console.</span><span class="sxs-lookup"><span data-stu-id="4f975-189">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="4f975-190">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="4f975-190">Congratulations!</span></span> <span data-ttu-id="4f975-191">Vous avez créé et exécuté une application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="4f975-191">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4f975-192">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4f975-192">Next steps</span></span>

<span data-ttu-id="4f975-193">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="4f975-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="4f975-194">Préparer votre environnement Windows pour .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-194">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="4f975-195">Écrire votre première application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-195">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="4f975-196">Générez et exécutez votre application .NET simple pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-196">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="4f975-197">Pour voir une vidéo expliquant les étapes ci-dessus, extrayez la [série de vidéos .net pour Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="4f975-197">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="4f975-198">Pour plus d’informations, consultez la page des ressources.</span><span class="sxs-lookup"><span data-stu-id="4f975-198">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="4f975-199">Ressources .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4f975-199">.NET for Apache Spark Resources</span></span>](../resources/index.md)
