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
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="5ee53-103">Tutorial: Démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5ee53-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="5ee53-104">Ce tutoriel vous apprend à exécuter un .NET pour Apache Spark app en utilisant .NET Core sur Windows, MacOS, et Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5ee53-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, MacOS, and Ubuntu.</span></span>

<span data-ttu-id="5ee53-105">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="5ee53-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="5ee53-106">Préparez votre environnement pour .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5ee53-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="5ee53-107">Écrivez votre premier .NET pour Apache Spark application</span><span class="sxs-lookup"><span data-stu-id="5ee53-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="5ee53-108">Construisez et exécutez votre simple .NET pour Apache Spark application</span><span class="sxs-lookup"><span data-stu-id="5ee53-108">Build and run your simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="5ee53-109">Préparation de votre environnement</span><span class="sxs-lookup"><span data-stu-id="5ee53-109">Prepare your environment</span></span>

<span data-ttu-id="5ee53-110">Avant de commencer à écrire votre application, vous devez configurer certaines dépendances préalables.</span><span class="sxs-lookup"><span data-stu-id="5ee53-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="5ee53-111">Si vous `dotnet`pouvez `java` `mvn`exécuter `spark-shell` , , , à partir de votre environnement de ligne de commande, alors votre environnement est déjà préparé et vous pouvez passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="5ee53-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="5ee53-112">Si vous ne pouvez pas exécuter l’une ou l’autre des commandes, faites les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="5ee53-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="5ee53-113">1. Installer .NET</span><span class="sxs-lookup"><span data-stu-id="5ee53-113">1. Install .NET</span></span>

<span data-ttu-id="5ee53-114">Pour commencer à créer des applications .NET, vous devez télécharger et installer le .NET SDK (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="5ee53-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="5ee53-115">Téléchargez et installez le [SDK .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span><span class="sxs-lookup"><span data-stu-id="5ee53-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="5ee53-116">L’installation du SDK ajoute la chaîne d’outils `dotnet` à votre variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="5ee53-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="5ee53-117">Une fois que vous avez installé le .NET Core SDK, ouvrez une nouvelle invite de commande ou terminal et exécutez `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="5ee53-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="5ee53-118">Si la commande s’exécute et imprime des informations sur la façon d’utiliser dotnet, peut passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="5ee53-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="5ee53-119">Si vous `'dotnet' is not recognized as an internal or external command` recevez une erreur, assurez-vous d’ouvrir une **nouvelle** invite ou terminal de commande avant d’exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="5ee53-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="5ee53-120">2. Installer Java</span><span class="sxs-lookup"><span data-stu-id="5ee53-120">2. Install Java</span></span>

<span data-ttu-id="5ee53-121">Installez [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) pour Windows et MacOS, ou [OpenJDK 8](https://openjdk.java.net/install/) pour Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5ee53-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and MacOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="5ee53-122">Sélectionnez la version appropriée pour votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="5ee53-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="5ee53-123">Par exemple, sélectionnez **jdk-8u201-windows-x64.exe** pour une machine Windows x64 (comme indiqué ci-dessous) ou **jdk-8u231-macosx-x64.dmg** pour MacOS.</span><span class="sxs-lookup"><span data-stu-id="5ee53-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for MacOS.</span></span> <span data-ttu-id="5ee53-124">Ensuite, utilisez `java` la commande pour vérifier l’installation.</span><span class="sxs-lookup"><span data-stu-id="5ee53-124">Then, use the command `java` to verify the installation.</span></span>

![Télécharger Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="5ee53-126">3. Installer un logiciel de compression</span><span class="sxs-lookup"><span data-stu-id="5ee53-126">3. Install compression software</span></span>

<span data-ttu-id="5ee53-127">Apache Spark est téléchargé sous forme de fichier compressé .tgz.</span><span class="sxs-lookup"><span data-stu-id="5ee53-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="5ee53-128">Utilisez un programme d’extraction, comme [7-Zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/), pour extraire le fichier.</span><span class="sxs-lookup"><span data-stu-id="5ee53-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="5ee53-129">4. Installer Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5ee53-129">4. Install Apache Spark</span></span>

<span data-ttu-id="5ee53-130">[Télécharger et installer Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="5ee53-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="5ee53-131">Vous devrez choisir parmi la version 2.3.md ou 2.4.0, 2.4.1, 2.4.3, ou 2.4.4 (.NET pour Apache Spark n’est pas compatible avec d’autres versions d’Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="5ee53-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="5ee53-132">Les commandes utilisées dans les étapes suivantes supposent que vous avez [téléchargé et installé Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span><span class="sxs-lookup"><span data-stu-id="5ee53-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="5ee53-133">Si vous souhaitez utiliser une version différente, remplacez **2.4.1** par le numéro de version approprié.</span><span class="sxs-lookup"><span data-stu-id="5ee53-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="5ee53-134">Ensuite, extraire le fichier **.tar** et les fichiers Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="5ee53-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="5ee53-135">Pour extraire le fichier **.tar** imbriqué :</span><span class="sxs-lookup"><span data-stu-id="5ee53-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="5ee53-136">Localisez le fichier **spark-2.4.1-bin-hadoop2.7.tgz** que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="5ee53-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="5ee53-137">Cliquez à droite sur le fichier et sélectionnez **7-Zip -> Extrait ici**.</span><span class="sxs-lookup"><span data-stu-id="5ee53-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="5ee53-138">**spark-2.4.1-bin-hadoop2.7.tar** est créé à côté du fichier **.tgz** que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="5ee53-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="5ee53-139">Pour extraire les fichiers Apache Spark :</span><span class="sxs-lookup"><span data-stu-id="5ee53-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="5ee53-140">Cliquez à droite sur **spark-2.4.1-bin-hadoop2.7.tar** et sélectionnez **7-Zip -> Fichiers d’extrait...**</span><span class="sxs-lookup"><span data-stu-id="5ee53-140">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="5ee53-141">Entrez **C: 'bin** dans l’extrait **au** champ.</span><span class="sxs-lookup"><span data-stu-id="5ee53-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="5ee53-142">Décochez la case à cocher sous **l’extrait au** champ.</span><span class="sxs-lookup"><span data-stu-id="5ee53-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="5ee53-143">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="5ee53-143">Select **OK**.</span></span>
* <span data-ttu-id="5ee53-144">Les fichiers Apache Spark sont extraits à C: 'bin’spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="5ee53-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7\</span></span>

![Installation de Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="5ee53-146">Exécutez les commandes suivantes pour définir les variables de l’environnement utilisées pour localiser Apache Spark sur **Windows**:</span><span class="sxs-lookup"><span data-stu-id="5ee53-146">Run the following commands to set the environment variables used to locate Apache Spark on **Windows**:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="5ee53-147">Exécutez les commandes suivantes pour définir les variables de l’environnement utilisées pour localiser Apache Spark sur **MacOS** et **Ubuntu**:</span><span class="sxs-lookup"><span data-stu-id="5ee53-147">Run the following commands to set the environment variables used to locate Apache Spark on **MacOS** and **Ubuntu**:</span></span>

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

<span data-ttu-id="5ee53-148">Une fois que vous avez tout installé et définissez vos variables d’environnement, ouvrez une **nouvelle** invite de commande ou terminal et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5ee53-148">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="5ee53-149">Si la commande s’exécute et imprime des informations de version, vous pouvez passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="5ee53-149">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="5ee53-150">Si vous `'spark-submit' is not recognized as an internal or external command` recevez une erreur, assurez-vous d’ouvrir une **nouvelle** invite de commande.</span><span class="sxs-lookup"><span data-stu-id="5ee53-150">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="5ee53-151">5. Installer .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5ee53-151">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="5ee53-152">Téléchargez la version [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) du .NET pour Apache Spark GitHub.</span><span class="sxs-lookup"><span data-stu-id="5ee53-152">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="5ee53-153">Par exemple, si vous êtes sur une machine Windows et prévoyez d’utiliser .NET Core, [téléchargez la version netcore3.1 de Windows x64](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span><span class="sxs-lookup"><span data-stu-id="5ee53-153">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span></span>

<span data-ttu-id="5ee53-154">Pour extraire le Microsoft.Spark.Worker:</span><span class="sxs-lookup"><span data-stu-id="5ee53-154">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="5ee53-155">Localiser le **fichier Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** fichier que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="5ee53-155">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="5ee53-156">Cliquez à droite et sélectionnez **7-Zip -> Fichiers d’extrait...**.</span><span class="sxs-lookup"><span data-stu-id="5ee53-156">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="5ee53-157">Entrez **C: 'bin** dans l’extrait **au** champ.</span><span class="sxs-lookup"><span data-stu-id="5ee53-157">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="5ee53-158">Décochez la case à cocher sous **l’extrait au** champ.</span><span class="sxs-lookup"><span data-stu-id="5ee53-158">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="5ee53-159">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="5ee53-159">Select **OK**.</span></span>

![Installer .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="5ee53-161">6. Installer WinUtils (Windows uniquement)</span><span class="sxs-lookup"><span data-stu-id="5ee53-161">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="5ee53-162">.NET pour Apache Spark nécessite WinUtils d’être installé aux côtés d’Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="5ee53-162">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="5ee53-163">[Télécharger winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="5ee53-163">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="5ee53-164">Ensuite, copiez WinUtils en **C : 'bin’spark-2.4.1-bin-hadoop2.7'bin**.</span><span class="sxs-lookup"><span data-stu-id="5ee53-164">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="5ee53-165">Si vous utilisez une version différente de Hadoop, qui est annotée à la fin de votre nom de dossier d’installation Spark, [sélectionnez la version de WinUtils](https://github.com/steveloughran/winutils) qui est compatible avec votre version de Hadoop.</span><span class="sxs-lookup"><span data-stu-id="5ee53-165">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="5ee53-166">7. Définir DOTNET_WORKER_DIR et vérifier les dépendances</span><span class="sxs-lookup"><span data-stu-id="5ee53-166">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="5ee53-167">Exécutez l’une des commandes `DOTNET_WORKER_DIR` suivantes pour définir la variable d’environnement, qui est utilisée par les applications .NET pour localiser .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="5ee53-167">Run one of the following commands to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span>

<span data-ttu-id="5ee53-168">Sur **Windows**, créer une nouvelle variable `DOTNET_WORKER_DIR` `C:\bin\Microsoft.Spark.Worker\` [d’environnement](https://www.java.com/en/download/help/path.xml) et le définir à l’annuaire où vous avez téléchargé et extrait le Microsoft.Spark.Worker (par exemple, ).</span><span class="sxs-lookup"><span data-stu-id="5ee53-168">On **Windows**, create a [new environment variable](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, `C:\bin\Microsoft.Spark.Worker\`).</span></span>

<span data-ttu-id="5ee53-169">Sur **MacOS**, créer une `export DOTNET_WORKER_DIR <your_path>` nouvelle variable d’environnement en utilisant et le définir à l’annuaire où vous avez téléchargé et extrait le Microsoft.Spark.Worker (par exemple, *'/bin/Microsoft.Spark.Worker/*).</span><span class="sxs-lookup"><span data-stu-id="5ee53-169">On **MacOS**, create a new environment variable using `export DOTNET_WORKER_DIR <your_path>` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker/*).</span></span>

<span data-ttu-id="5ee53-170">Sur **Ubuntu**, créer une nouvelle variable `DOTNET_WORKER_DIR` [d’environnement](https://help.ubuntu.com/community/EnvironmentVariables) et le définir à l’annuaire où vous avez téléchargé et extrait le Microsoft.Spark.Worker (par exemple, *'/bin/Microsoft.Spark.Worker*).</span><span class="sxs-lookup"><span data-stu-id="5ee53-170">On **Ubuntu**, create a [new environment variable](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker*).</span></span>

<span data-ttu-id="5ee53-171">Enfin, vérifiez que vous `dotnet`pouvez `java` `mvn`exécuter `spark-shell` , , , à partir de votre ligne de commande avant de passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="5ee53-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="5ee53-172">Écrire une application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5ee53-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="5ee53-173">1. Créer une application console</span><span class="sxs-lookup"><span data-stu-id="5ee53-173">1. Create a console app</span></span>

<span data-ttu-id="5ee53-174">Dans votre application ou terminal de commande, exécutez les commandes suivantes pour créer une nouvelle application de console :</span><span class="sxs-lookup"><span data-stu-id="5ee53-174">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="5ee53-175">La `dotnet` commande `new` crée une `console` application de type pour vous.</span><span class="sxs-lookup"><span data-stu-id="5ee53-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="5ee53-176">Le `-o` paramètre crée un répertoire nommé *mySparkApp* où votre application est stockée et le remplit avec les fichiers requis.</span><span class="sxs-lookup"><span data-stu-id="5ee53-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="5ee53-177">La `cd mySparkApp` commande modifie l’annuaire de l’annuaire de l’application que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="5ee53-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="5ee53-178">2. Installer le paquet NuGet</span><span class="sxs-lookup"><span data-stu-id="5ee53-178">2. Install NuGet package</span></span>

<span data-ttu-id="5ee53-179">Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="5ee53-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="5ee53-180">Dans votre commande ou terminal, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5ee53-180">In your command prompt or terminal, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a><span data-ttu-id="5ee53-181">3. Codez votre application</span><span class="sxs-lookup"><span data-stu-id="5ee53-181">3. Code your app</span></span>

<span data-ttu-id="5ee53-182">Ouvrez *Program.cs* dans Visual Studio Code, ou n’importe quel éditeur de texte, et remplacez tout le code par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="5ee53-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

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

### <a name="4-create-and-add-a-data-file"></a><span data-ttu-id="5ee53-183">4. Créer et ajouter un fichier de données</span><span class="sxs-lookup"><span data-stu-id="5ee53-183">4. Create and add a data file</span></span>

<span data-ttu-id="5ee53-184">Ouvrez votre invite de commande ou terminal et naviguez dans votre dossier d’application.</span><span class="sxs-lookup"><span data-stu-id="5ee53-184">Open your command prompt or terminal and navigate into your app folder.</span></span>

```bash
cd <your-app-output-directory>
```

<span data-ttu-id="5ee53-185">Votre application traite un fichier contenant des lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="5ee53-185">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="5ee53-186">Créez un fichier *input.txt* dans votre répertoire *mySparkApp,* contenant le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="5ee53-186">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="5ee53-187">Exécuter votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5ee53-187">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="5ee53-188">Exécutez la commande suivante pour construire votre application :</span><span class="sxs-lookup"><span data-stu-id="5ee53-188">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="5ee53-189">Exécutez la commande suivante pour soumettre votre demande pour exécuter sur Apache Spark :</span><span class="sxs-lookup"><span data-stu-id="5ee53-189">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > <span data-ttu-id="5ee53-190">Cette commande suppose que vous avez téléchargé Apache Spark et l’a ajouté à votre variable d’environnement PATH pour être en mesure d’utiliser `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="5ee53-190">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="5ee53-191">Sinon, vous auriez à utiliser le chemin complet (par exemple, *C: 'bin’apache-spark’bin’spark-submit* ou *'/spark/bin/spark/spark-submit*).</span><span class="sxs-lookup"><span data-stu-id="5ee53-191">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

3. <span data-ttu-id="5ee53-192">Lorsque votre application s’exécute, les données de comptage de mot du fichier *input.txt* sont écrites sur la console.</span><span class="sxs-lookup"><span data-stu-id="5ee53-192">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="5ee53-193">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="5ee53-193">Congratulations!</span></span> <span data-ttu-id="5ee53-194">Vous avez créé et exécuté une application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="5ee53-194">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5ee53-195">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5ee53-195">Next steps</span></span>

<span data-ttu-id="5ee53-196">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="5ee53-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="5ee53-197">Préparer votre environnement Windows pour .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5ee53-197">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="5ee53-198">Écrivez votre premier .NET pour Apache Spark application</span><span class="sxs-lookup"><span data-stu-id="5ee53-198">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="5ee53-199">Construisez et exécutez votre simple .NET pour Apache Spark application</span><span class="sxs-lookup"><span data-stu-id="5ee53-199">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="5ee53-200">Pour voir une vidéo expliquant les étapes ci-dessus, consultez le [.NET pour Apache Spark 101 série vidéo](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="5ee53-200">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="5ee53-201">Pour plus d’informations, consultez la page des ressources.</span><span class="sxs-lookup"><span data-stu-id="5ee53-201">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="5ee53-202">Ressources .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5ee53-202">.NET for Apache Spark Resources</span></span>](../resources/index.md)
