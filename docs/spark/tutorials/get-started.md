---
title: Bien démarrer avec .NET pour Apache Spark
description: Découvrez comment exécuter un .NET pour Apache Spark application à l’aide de .NET Core sur Windows, MacOS et Ubuntu.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: be150bcef0029f69136e21c35791c863220af244
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617650"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="37c06-103">Didacticiel : prise en main de .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="37c06-104">Ce didacticiel vous apprend à exécuter un .NET pour Apache Spark application à l’aide de .NET Core sur Windows, MacOS et Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="37c06-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, MacOS, and Ubuntu.</span></span>

<span data-ttu-id="37c06-105">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="37c06-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="37c06-106">Préparer votre environnement pour .NET pour la Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="37c06-107">Écrire votre première application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="37c06-108">Générez et exécutez votre application .NET simple pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-108">Build and run your simple .NET for Apache Spark application</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="37c06-109">Préparation de votre environnement</span><span class="sxs-lookup"><span data-stu-id="37c06-109">Prepare your environment</span></span>

<span data-ttu-id="37c06-110">Avant de commencer à écrire votre application, vous devez configurer certaines dépendances de la configuration requise.</span><span class="sxs-lookup"><span data-stu-id="37c06-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="37c06-111">Si vous pouvez exécuter `dotnet` , `java` , `mvn` , `spark-shell` à partir de votre environnement de ligne de commande, votre environnement est déjà préparé et vous pouvez passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="37c06-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="37c06-112">Si vous ne pouvez pas exécuter une partie ou l’ensemble des commandes, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="37c06-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="37c06-113">1. installer .NET</span><span class="sxs-lookup"><span data-stu-id="37c06-113">1. Install .NET</span></span>

<span data-ttu-id="37c06-114">Pour commencer à créer des applications .NET, vous devez télécharger et installer le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="37c06-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="37c06-115">Téléchargez et installez le [SDK .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span><span class="sxs-lookup"><span data-stu-id="37c06-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="37c06-116">L’installation du SDK ajoute la chaîne d’outils `dotnet` à votre variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="37c06-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="37c06-117">Une fois que vous avez installé le kit SDK .NET Core, ouvrez une nouvelle invite de commandes ou un terminal, puis exécutez `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="37c06-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="37c06-118">Si la commande s’exécute et imprime des informations sur l’utilisation de DotNet, peut passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="37c06-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="37c06-119">Si vous recevez une `'dotnet' is not recognized as an internal or external command` erreur, assurez-vous d’avoir ouvert une **nouvelle** invite de commandes ou un terminal avant d’exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="37c06-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="37c06-120">2. installer Java</span><span class="sxs-lookup"><span data-stu-id="37c06-120">2. Install Java</span></span>

<span data-ttu-id="37c06-121">Installez [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) pour Windows et MacOS, ou [openjdk 8](https://openjdk.java.net/install/) pour Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="37c06-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and MacOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="37c06-122">Sélectionnez la version appropriée pour votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="37c06-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="37c06-123">Par exemple, sélectionnez **jdk-8u201-windows-x64.exe** pour un ordinateur Windows x64 (comme indiqué ci-dessous) ou **JDK-8u231-MacOSX-x64. dmg** pour MacOS.</span><span class="sxs-lookup"><span data-stu-id="37c06-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for MacOS.</span></span> <span data-ttu-id="37c06-124">Ensuite, utilisez la commande `java` pour vérifier l’installation.</span><span class="sxs-lookup"><span data-stu-id="37c06-124">Then, use the command `java` to verify the installation.</span></span>

![Téléchargement Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="37c06-126">3. installer le logiciel de compression</span><span class="sxs-lookup"><span data-stu-id="37c06-126">3. Install compression software</span></span>

<span data-ttu-id="37c06-127">Apache Spark est téléchargé en tant que fichier. tgz compressé.</span><span class="sxs-lookup"><span data-stu-id="37c06-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="37c06-128">Utilisez un programme d’extraction, tel que [7-zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/), pour extraire le fichier.</span><span class="sxs-lookup"><span data-stu-id="37c06-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="37c06-129">4. Installez Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-129">4. Install Apache Spark</span></span>

<span data-ttu-id="37c06-130">[Téléchargez et installez Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="37c06-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="37c06-131">Vous devez effectuer une sélection dans la version 2,3. \* ou 2.4.0, 2.4.1, 2.4.3 ou 2.4.4 (.NET pour Apache Spark n’est pas compatible avec les autres versions de Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="37c06-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="37c06-132">Les commandes utilisées dans les étapes suivantes supposent que vous avez [téléchargé et installé Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span><span class="sxs-lookup"><span data-stu-id="37c06-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="37c06-133">Si vous souhaitez utiliser une version différente, remplacez **2.4.1** par le numéro de version approprié.</span><span class="sxs-lookup"><span data-stu-id="37c06-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="37c06-134">Ensuite, extrayez le fichier **. tar** et les fichiers de Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="37c06-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="37c06-135">Pour extraire le fichier **. tar** imbriqué :</span><span class="sxs-lookup"><span data-stu-id="37c06-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="37c06-136">Localisez le fichier **Spark-2.4.1-bin-Hadoop 2.7. tgz** que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="37c06-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="37c06-137">Cliquez avec le bouton droit sur le fichier et sélectionnez **7-zip-> extraire ici**.</span><span class="sxs-lookup"><span data-stu-id="37c06-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="37c06-138">**Spark-2.4.1-bin-Hadoop 2.7. tar** est créé avec le fichier **. tgz** que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="37c06-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="37c06-139">Pour extraire les fichiers de Apache Spark :</span><span class="sxs-lookup"><span data-stu-id="37c06-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="37c06-140">Cliquez avec le bouton droit sur **Spark-2.4.1-bin-Hadoop 2.7. tar** et sélectionnez **7-zip-> extraire les fichiers...**</span><span class="sxs-lookup"><span data-stu-id="37c06-140">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="37c06-141">Entrez **C:\bin** dans le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="37c06-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="37c06-142">Désactivez la case à cocher sous le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="37c06-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="37c06-143">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="37c06-143">Select **OK**.</span></span>
* <span data-ttu-id="37c06-144">Les fichiers de Apache Spark sont extraits dans C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="37c06-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![Installation de Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="37c06-146">Exécutez les commandes suivantes pour définir les variables d’environnement utilisées pour localiser Apache Spark sur **Windows**:</span><span class="sxs-lookup"><span data-stu-id="37c06-146">Run the following commands to set the environment variables used to locate Apache Spark on **Windows**:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="37c06-147">Exécutez les commandes suivantes pour définir les variables d’environnement utilisées pour localiser Apache Spark sur **MacOS** et **Ubuntu**:</span><span class="sxs-lookup"><span data-stu-id="37c06-147">Run the following commands to set the environment variables used to locate Apache Spark on **MacOS** and **Ubuntu**:</span></span>

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

<span data-ttu-id="37c06-148">Une fois que vous avez installé tout et défini vos variables d’environnement, ouvrez une **nouvelle** invite de commandes ou un terminal, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="37c06-148">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="37c06-149">Si la commande s’exécute et imprime des informations de version, vous pouvez passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="37c06-149">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="37c06-150">Si vous recevez une `'spark-submit' is not recognized as an internal or external command` erreur, assurez-vous que vous avez ouvert une **nouvelle** invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="37c06-150">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="37c06-151">5. installer .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-151">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="37c06-152">Téléchargez la version [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) à partir du .net pour Apache Spark github.</span><span class="sxs-lookup"><span data-stu-id="37c06-152">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="37c06-153">Par exemple, si vous êtes sur un ordinateur Windows et que vous envisagez d’utiliser .NET Core, [Téléchargez la version Windows x64 netcoreapp 3.1](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span><span class="sxs-lookup"><span data-stu-id="37c06-153">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span></span>

<span data-ttu-id="37c06-154">Pour extraire Microsoft. Spark. Worker :</span><span class="sxs-lookup"><span data-stu-id="37c06-154">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="37c06-155">Localisez le fichier **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="37c06-155">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="37c06-156">Cliquez avec le bouton droit et sélectionnez **7-zip-> extraire les fichiers...**.</span><span class="sxs-lookup"><span data-stu-id="37c06-156">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="37c06-157">Entrez **C:\bin** dans le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="37c06-157">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="37c06-158">Désactivez la case à cocher sous le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="37c06-158">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="37c06-159">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="37c06-159">Select **OK**.</span></span>

![Installer .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="37c06-161">6. installer WinUtils (Windows uniquement)</span><span class="sxs-lookup"><span data-stu-id="37c06-161">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="37c06-162">.NET pour Apache Spark nécessite l’installation de WinUtils avec Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="37c06-162">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="37c06-163">[Téléchargez winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="37c06-163">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="37c06-164">Ensuite, copiez WinUtils dans **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span><span class="sxs-lookup"><span data-stu-id="37c06-164">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="37c06-165">Si vous utilisez une autre version de Hadoop, qui est annotée à la fin de votre nom de dossier d’installation Spark, [Sélectionnez la version de winutils](https://github.com/steveloughran/winutils) qui est compatible avec votre version de Hadoop.</span><span class="sxs-lookup"><span data-stu-id="37c06-165">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="37c06-166">7. définir des DOTNET_WORKER_DIR et vérifier les dépendances</span><span class="sxs-lookup"><span data-stu-id="37c06-166">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="37c06-167">Exécutez l’une des commandes suivantes pour définir la `DOTNET_WORKER_DIR` variable d’environnement, qui est utilisée par les applications .net pour localiser .net pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="37c06-167">Run one of the following commands to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span>

<span data-ttu-id="37c06-168">Sur **Windows**, créez une [variable d’environnement](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` et affectez-lui le répertoire dans lequel vous avez téléchargé et extrait Microsoft. Spark. Worker (par exemple, `C:\bin\Microsoft.Spark.Worker\` ).</span><span class="sxs-lookup"><span data-stu-id="37c06-168">On **Windows**, create a [new environment variable](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, `C:\bin\Microsoft.Spark.Worker\`).</span></span>

<span data-ttu-id="37c06-169">Sur **MacOS**, créez une variable d’environnement en utilisant `export DOTNET_WORKER_DIR <your_path>` et définissez-la sur le répertoire dans lequel vous avez téléchargé et extrait Microsoft. Spark. Worker (par exemple, *~/bin/Microsoft.Spark.Worker/*).</span><span class="sxs-lookup"><span data-stu-id="37c06-169">On **MacOS**, create a new environment variable using `export DOTNET_WORKER_DIR <your_path>` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker/*).</span></span>

<span data-ttu-id="37c06-170">Sur **Ubuntu**, créez une [variable d’environnement](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` et affectez-lui le répertoire dans lequel vous avez téléchargé et extrait Microsoft. Spark. Worker (par exemple, *~/bin/Microsoft.Spark.Worker*).</span><span class="sxs-lookup"><span data-stu-id="37c06-170">On **Ubuntu**, create a [new environment variable](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker*).</span></span>

<span data-ttu-id="37c06-171">Enfin, vérifiez que vous pouvez exécuter `dotnet` , `java` , `mvn` , `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="37c06-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="37c06-172">Écrire une application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="37c06-173">1. créer une application console</span><span class="sxs-lookup"><span data-stu-id="37c06-173">1. Create a console app</span></span>

<span data-ttu-id="37c06-174">Dans votre invite de commandes ou terminal, exécutez les commandes suivantes pour créer une nouvelle application console :</span><span class="sxs-lookup"><span data-stu-id="37c06-174">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="37c06-175">La `dotnet` commande crée une `new` application de type `console` pour vous.</span><span class="sxs-lookup"><span data-stu-id="37c06-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="37c06-176">Le `-o` paramètre crée un répertoire nommé *mySparkApp* dans lequel votre application est stockée et le remplit avec les fichiers requis.</span><span class="sxs-lookup"><span data-stu-id="37c06-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="37c06-177">La `cd mySparkApp` commande remplace le répertoire par le répertoire d’application que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="37c06-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="37c06-178">2. installer le package NuGet</span><span class="sxs-lookup"><span data-stu-id="37c06-178">2. Install NuGet package</span></span>

<span data-ttu-id="37c06-179">Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="37c06-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="37c06-180">Dans votre invite de commandes ou terminal, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="37c06-180">In your command prompt or terminal, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a><span data-ttu-id="37c06-181">3. codez votre application</span><span class="sxs-lookup"><span data-stu-id="37c06-181">3. Code your app</span></span>

<span data-ttu-id="37c06-182">Ouvrez *Program.cs* dans Visual Studio code ou un éditeur de texte, puis remplacez tout le code par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="37c06-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

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

### <a name="4-create-and-add-a-data-file"></a><span data-ttu-id="37c06-183">4. créer et ajouter un fichier de données</span><span class="sxs-lookup"><span data-stu-id="37c06-183">4. Create and add a data file</span></span>

<span data-ttu-id="37c06-184">Ouvrez votre invite de commandes ou votre terminal et accédez à votre dossier d’application.</span><span class="sxs-lookup"><span data-stu-id="37c06-184">Open your command prompt or terminal and navigate into your app folder.</span></span>

```bash
cd <your-app-output-directory>
```

<span data-ttu-id="37c06-185">Votre application traite un fichier contenant des lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="37c06-185">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="37c06-186">Créez un fichier *input.txt* dans votre répertoire *mySparkApp* , contenant le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="37c06-186">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="37c06-187">Exécuter votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-187">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="37c06-188">Exécutez la commande suivante pour générer votre application :</span><span class="sxs-lookup"><span data-stu-id="37c06-188">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="37c06-189">Exécutez la commande suivante pour envoyer votre application pour qu’elle s’exécute sur Apache Spark :</span><span class="sxs-lookup"><span data-stu-id="37c06-189">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > <span data-ttu-id="37c06-190">Cette commande suppose que vous avez téléchargé Apache Spark et que vous l’avez ajouté à votre variable d’environnement PATH pour pouvoir l’utiliser `spark-submit` .</span><span class="sxs-lookup"><span data-stu-id="37c06-190">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="37c06-191">Dans le cas contraire, vous devez utiliser le chemin d’accès complet (par exemple, *C:\bin\apache-spark\bin\spark-Submit* ou *~/Spark/bin/Spark-Submit*).</span><span class="sxs-lookup"><span data-stu-id="37c06-191">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

3. <span data-ttu-id="37c06-192">Lorsque votre application s’exécute, les données de nombre de mots du fichier *input.txt* sont écrites dans la console.</span><span class="sxs-lookup"><span data-stu-id="37c06-192">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="37c06-193">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="37c06-193">Congratulations!</span></span> <span data-ttu-id="37c06-194">Vous avez créé et exécuté une application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="37c06-194">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="37c06-195">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="37c06-195">Next steps</span></span>

<span data-ttu-id="37c06-196">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="37c06-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="37c06-197">Préparer votre environnement Windows pour .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-197">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="37c06-198">Écrire votre première application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-198">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="37c06-199">Générez et exécutez votre application .NET simple pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-199">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="37c06-200">Pour voir une vidéo expliquant les étapes ci-dessus, extrayez la [série de vidéos .net pour Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="37c06-200">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="37c06-201">Pour plus d’informations, consultez la page des ressources.</span><span class="sxs-lookup"><span data-stu-id="37c06-201">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="37c06-202">Ressources .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37c06-202">.NET for Apache Spark Resources</span></span>](../resources/index.md)
