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
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="b1717-103">Didacticiel : prise en main de .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="b1717-104">Ce didacticiel vous apprend à exécuter un .NET pour Apache Spark application à l’aide de .NET Core sur Windows, macOS et Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b1717-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, macOS, and Ubuntu.</span></span>

<span data-ttu-id="b1717-105">Dans ce tutoriel, vous allez découvrir comment :</span><span class="sxs-lookup"><span data-stu-id="b1717-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="b1717-106">Préparer votre environnement pour .NET pour la Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="b1717-107">Écrire votre première application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="b1717-108">Générez et exécutez votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-108">Build and run your .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="b1717-109">Préparation de votre environnement</span><span class="sxs-lookup"><span data-stu-id="b1717-109">Prepare your environment</span></span>

<span data-ttu-id="b1717-110">Avant de commencer à écrire votre application, vous devez configurer certaines dépendances de la configuration requise.</span><span class="sxs-lookup"><span data-stu-id="b1717-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="b1717-111">Si vous pouvez exécuter `dotnet` , `java` , `spark-shell` à partir de votre environnement de ligne de commande, votre environnement est déjà préparé et vous pouvez passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="b1717-111">If you can run `dotnet`, `java`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="b1717-112">Si vous ne pouvez pas exécuter une partie ou l’ensemble des commandes, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="b1717-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="b1717-113">1. installer .NET</span><span class="sxs-lookup"><span data-stu-id="b1717-113">1. Install .NET</span></span>

<span data-ttu-id="b1717-114">Pour commencer à créer des applications .NET, vous devez télécharger et installer le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="b1717-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="b1717-115">Téléchargez et installez le [SDK .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span><span class="sxs-lookup"><span data-stu-id="b1717-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="b1717-116">L’installation du SDK ajoute la chaîne d’outils `dotnet` à votre variable d’environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="b1717-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="b1717-117">Une fois que vous avez installé le kit SDK .NET Core, ouvrez une nouvelle invite de commandes ou un terminal, puis exécutez `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="b1717-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="b1717-118">Si la commande s’exécute et imprime des informations sur l’utilisation de DotNet, peut passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="b1717-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="b1717-119">Si vous recevez une `'dotnet' is not recognized as an internal or external command` erreur, assurez-vous d’avoir ouvert une **nouvelle** invite de commandes ou un terminal avant d’exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="b1717-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="b1717-120">2. installer Java</span><span class="sxs-lookup"><span data-stu-id="b1717-120">2. Install Java</span></span>

<span data-ttu-id="b1717-121">Installez [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) pour Windows et MacOS, ou [openjdk 8](https://openjdk.java.net/install/) pour Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b1717-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and macOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="b1717-122">Sélectionnez la version appropriée pour votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b1717-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="b1717-123">Par exemple, sélectionnez **jdk-8u201-windows-x64.exe** pour un ordinateur Windows x64 (comme indiqué ci-dessous) ou **JDK-8u231-MacOSX-x64. dmg** pour MacOS.</span><span class="sxs-lookup"><span data-stu-id="b1717-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for macOS.</span></span> <span data-ttu-id="b1717-124">Ensuite, utilisez la commande `java` pour vérifier l’installation.</span><span class="sxs-lookup"><span data-stu-id="b1717-124">Then, use the command `java` to verify the installation.</span></span>

![Téléchargement Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="b1717-126">3. installer le logiciel de compression</span><span class="sxs-lookup"><span data-stu-id="b1717-126">3. Install compression software</span></span>

<span data-ttu-id="b1717-127">Apache Spark est téléchargé en tant que fichier. tgz compressé.</span><span class="sxs-lookup"><span data-stu-id="b1717-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="b1717-128">Utilisez un programme d’extraction, tel que [7-zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/), pour extraire le fichier.</span><span class="sxs-lookup"><span data-stu-id="b1717-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="b1717-129">4. Installez Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-129">4. Install Apache Spark</span></span>

<span data-ttu-id="b1717-130">[Téléchargez et installez Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="b1717-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="b1717-131">Vous devez effectuer une sélection dans la version 2,3. \* ou 2.4.0, 2.4.1, 2.4.3 ou 2.4.4 (.NET pour Apache Spark n’est pas compatible avec les autres versions de Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="b1717-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="b1717-132">Les commandes utilisées dans les étapes suivantes supposent que vous avez [téléchargé et installé Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span><span class="sxs-lookup"><span data-stu-id="b1717-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="b1717-133">Si vous souhaitez utiliser une version différente, remplacez **2.4.1** par le numéro de version approprié.</span><span class="sxs-lookup"><span data-stu-id="b1717-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="b1717-134">Ensuite, extrayez le fichier **. tar** et les fichiers de Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b1717-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="b1717-135">Pour extraire le fichier **. tar** imbriqué :</span><span class="sxs-lookup"><span data-stu-id="b1717-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="b1717-136">Localisez le fichier **Spark-2.4.1-bin-Hadoop 2.7. tgz** que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="b1717-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="b1717-137">Cliquez avec le bouton droit sur le fichier et sélectionnez **7-zip-> extraire ici**.</span><span class="sxs-lookup"><span data-stu-id="b1717-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="b1717-138">**Spark-2.4.1-bin-Hadoop 2.7. tar** est créé avec le fichier **. tgz** que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="b1717-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="b1717-139">Pour extraire les fichiers de Apache Spark :</span><span class="sxs-lookup"><span data-stu-id="b1717-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="b1717-140">Cliquez avec le bouton droit sur **Spark-2.4.1-bin-Hadoop 2.7. tar** et sélectionnez **7-zip-> extraire les fichiers...**</span><span class="sxs-lookup"><span data-stu-id="b1717-140">Right-click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="b1717-141">Entrez **C:\bin** dans le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="b1717-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="b1717-142">Désactivez la case à cocher sous le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="b1717-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="b1717-143">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1717-143">Select **OK**.</span></span>
* <span data-ttu-id="b1717-144">Les fichiers de Apache Spark sont extraits dans C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="b1717-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![Installation de Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="b1717-146">Exécutez les commandes suivantes pour définir les variables d’environnement utilisées pour localiser Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b1717-146">Run the following commands to set the environment variables used to locate Apache Spark.</span></span> <span data-ttu-id="b1717-147">Sur Windows, veillez à exécuter l’invite de commandes en mode administrateur.</span><span class="sxs-lookup"><span data-stu-id="b1717-147">On Windows, make sure to run the command prompt in administrator mode.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="b1717-148">Windows</span><span class="sxs-lookup"><span data-stu-id="b1717-148">Windows</span></span>](#tab/windows)

```console
setx /M HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx /M SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx /M PATH "%PATH%;%HADOOP_HOME%;%SPARK_HOME%\bin"
```

#### <a name="maclinux"></a>[<span data-ttu-id="b1717-149">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="b1717-149">Mac/Linux</span></span>](#tab/linux)

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

---

<span data-ttu-id="b1717-150">Une fois que vous avez installé tout et défini vos variables d’environnement, ouvrez une **nouvelle** invite de commandes ou un terminal, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b1717-150">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

```text
spark-submit --version
```

<span data-ttu-id="b1717-151">Si la commande s’exécute et imprime des informations de version, vous pouvez passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="b1717-151">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="b1717-152">Si vous recevez une `'spark-submit' is not recognized as an internal or external command` erreur, assurez-vous que vous avez ouvert une **nouvelle** invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="b1717-152">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="b1717-153">5. installer .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-153">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="b1717-154">Téléchargez la version [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) à partir du .net pour Apache Spark github.</span><span class="sxs-lookup"><span data-stu-id="b1717-154">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="b1717-155">Par exemple, si vous êtes sur un ordinateur Windows et que vous envisagez d’utiliser .NET Core, [Téléchargez la version Windows x64 netcoreapp 3.1](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="b1717-155">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases).</span></span>

<span data-ttu-id="b1717-156">Pour extraire Microsoft. Spark. Worker :</span><span class="sxs-lookup"><span data-stu-id="b1717-156">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="b1717-157">Localisez le fichier **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="b1717-157">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="b1717-158">Cliquez avec le bouton droit et sélectionnez **7-zip-> extraire les fichiers...**.</span><span class="sxs-lookup"><span data-stu-id="b1717-158">Right-click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="b1717-159">Entrez **C:\bin** dans le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="b1717-159">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="b1717-160">Désactivez la case à cocher sous le champ **extraire vers** .</span><span class="sxs-lookup"><span data-stu-id="b1717-160">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="b1717-161">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1717-161">Select **OK**.</span></span>

![Installer .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="b1717-163">6. installer WinUtils (Windows uniquement)</span><span class="sxs-lookup"><span data-stu-id="b1717-163">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="b1717-164">.NET pour Apache Spark nécessite l’installation de WinUtils avec Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b1717-164">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="b1717-165">[Téléchargez winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="b1717-165">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="b1717-166">Ensuite, copiez WinUtils dans **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span><span class="sxs-lookup"><span data-stu-id="b1717-166">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="b1717-167">Si vous utilisez une autre version de Hadoop, qui est annotée à la fin de votre nom de dossier d’installation Spark, [Sélectionnez la version de winutils](https://github.com/steveloughran/winutils) qui est compatible avec votre version de Hadoop.</span><span class="sxs-lookup"><span data-stu-id="b1717-167">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="b1717-168">7. définir des DOTNET_WORKER_DIR et vérifier les dépendances</span><span class="sxs-lookup"><span data-stu-id="b1717-168">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="b1717-169">Exécutez l’une des commandes suivantes pour définir la `DOTNET_WORKER_DIR` variable d’environnement, qui est utilisée par les applications .net pour localiser .net pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b1717-169">Run one of the following commands to set the `DOTNET_WORKER_DIR` environment variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span> <span data-ttu-id="b1717-170">Veillez à remplacer `<PATH-DOTNET_WORKER_DIR>` par le répertoire dans lequel vous avez téléchargé et extrait le `Microsoft.Spark.Worker` .</span><span class="sxs-lookup"><span data-stu-id="b1717-170">Make sure to replace `<PATH-DOTNET_WORKER_DIR>` with the directory where you downloaded and extracted the `Microsoft.Spark.Worker`.</span></span> <span data-ttu-id="b1717-171">Sur Windows, veillez à exécuter l’invite de commandes en mode administrateur.</span><span class="sxs-lookup"><span data-stu-id="b1717-171">On Windows, make sure to run the command prompt in administrator mode.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="b1717-172">Windows</span><span class="sxs-lookup"><span data-stu-id="b1717-172">Windows</span></span>](#tab/windows)

```console
setx /M DOTNET_WORKER_DIR <PATH-DOTNET-WORKER-DIR>
```

#### <a name="maclinux"></a>[<span data-ttu-id="b1717-173">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="b1717-173">Mac/Linux</span></span>](#tab/linux)

```bash
export DOTNET_WORKER_DIR=<PATH-DOTNET-WORKER-DIR>
```

---

<span data-ttu-id="b1717-174">Enfin, vérifiez que vous pouvez exécuter `dotnet` , `java` , `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="b1717-174">Finally, double-check that you can run `dotnet`, `java`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="b1717-175">Écrire une application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-175">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="b1717-176">1. créer une application console</span><span class="sxs-lookup"><span data-stu-id="b1717-176">1. Create a console app</span></span>

<span data-ttu-id="b1717-177">Dans votre invite de commandes ou terminal, exécutez les commandes suivantes pour créer une nouvelle application console :</span><span class="sxs-lookup"><span data-stu-id="b1717-177">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o MySparkApp
cd MySparkApp
```

<span data-ttu-id="b1717-178">La `dotnet` commande crée une `new` application de type `console` pour vous.</span><span class="sxs-lookup"><span data-stu-id="b1717-178">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="b1717-179">Le `-o` paramètre crée un répertoire nommé *MySparkApp* dans lequel votre application est stockée et le remplit avec les fichiers requis.</span><span class="sxs-lookup"><span data-stu-id="b1717-179">The `-o` parameter creates a directory named *MySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="b1717-180">La `cd MySparkApp` commande remplace le répertoire par le répertoire d’application que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="b1717-180">The `cd MySparkApp` command changes the directory to the app directory you created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="b1717-181">2. installer le package NuGet</span><span class="sxs-lookup"><span data-stu-id="b1717-181">2. Install NuGet package</span></span>

<span data-ttu-id="b1717-182">Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="b1717-182">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="b1717-183">Dans votre invite de commandes ou terminal, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b1717-183">In your command prompt or terminal, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.Spark
```

> [!NOTE]
> <span data-ttu-id="b1717-184">Ce didacticiel utilise la version la plus récente du `Microsoft.Spark` package NuGet, sauf indication contraire.</span><span class="sxs-lookup"><span data-stu-id="b1717-184">This tutorial uses the latest version of the `Microsoft.Spark` NuGet package unless otherwise specified.</span></span>

### <a name="3-write-your-app"></a><span data-ttu-id="b1717-185">3. écrire votre application</span><span class="sxs-lookup"><span data-stu-id="b1717-185">3. Write your app</span></span>

<span data-ttu-id="b1717-186">Ouvrez *Program.cs* dans Visual Studio code ou un éditeur de texte, puis remplacez tout le code par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="b1717-186">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

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

<span data-ttu-id="b1717-187">[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) est le point d’entrée de Apache Spark applications, qui gère le contexte et les informations de votre application.</span><span class="sxs-lookup"><span data-stu-id="b1717-187">[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) is the entrypoint of Apache Spark applications, which manages the context and information of your application.</span></span> <span data-ttu-id="b1717-188">À l’aide de la méthode [Text](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) , les données texte du fichier spécifié par le `filePath` sont lues dans un [tableau](xref:Microsoft.Spark.Sql.DataFrame).</span><span class="sxs-lookup"><span data-stu-id="b1717-188">Using the [Text](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) method, the text data from the file specified by the `filePath` is read into a [DataFrame](xref:Microsoft.Spark.Sql.DataFrame).</span></span> <span data-ttu-id="b1717-189">Un tableau est un moyen d’organiser les données en un ensemble de colonnes nommées.</span><span class="sxs-lookup"><span data-stu-id="b1717-189">A DataFrame is a way of organizing data into a set of named columns.</span></span> <span data-ttu-id="b1717-190">Ensuite, une série de transformations est appliquée pour fractionner les phrases dans le fichier, regrouper chacun des mots, les compter et les classer dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="b1717-190">Then, a series of transformations is applied to split the sentences in the file, group each of the words, count them and order them in descending order.</span></span> <span data-ttu-id="b1717-191">Le résultat de ces opérations est stocké dans un autre tableau.</span><span class="sxs-lookup"><span data-stu-id="b1717-191">The result of these operations is stored in another DataFrame.</span></span> <span data-ttu-id="b1717-192">Notez qu’à ce stade, aucune opération n’a eu lieu parce que .NET pour Apache Spark a évalué tardivement les données.</span><span class="sxs-lookup"><span data-stu-id="b1717-192">Note that at this point, no operations have taken place because .NET for Apache Spark lazily evaluates the data.</span></span> <span data-ttu-id="b1717-193">Ce n’est pas jusqu’à ce que la méthode [Show](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) soit appelée pour afficher le contenu des `words` tableau transformés dans la console que les opérations définies dans les lignes ci-dessus s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="b1717-193">It's not until the [Show](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) method is called to display the contents of the `words` transformed DataFrame to the console that the operations defined in the lines above execute.</span></span> <span data-ttu-id="b1717-194">Une fois que vous n’avez plus besoin de la session Spark, utilisez la méthode [Stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) pour arrêter votre session.</span><span class="sxs-lookup"><span data-stu-id="b1717-194">Once you no longer need the Spark session, use the [Stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) method to stop your session.</span></span>

### <a name="4-create-data-file"></a><span data-ttu-id="b1717-195">4. créer un fichier de données</span><span class="sxs-lookup"><span data-stu-id="b1717-195">4. Create data file</span></span>

<span data-ttu-id="b1717-196">Votre application traite un fichier contenant des lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="b1717-196">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="b1717-197">Créez un fichier appelé *input.txt* fichier dans votre répertoire *MySparkApp* , contenant le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="b1717-197">Create a file called *input.txt* file in your *MySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

<span data-ttu-id="b1717-198">Enregistrez les modifications et fermez le fichier.</span><span class="sxs-lookup"><span data-stu-id="b1717-198">Save the changes and close the file.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="b1717-199">Exécuter votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-199">Run your .NET for Apache Spark app</span></span>

<span data-ttu-id="b1717-200">Exécutez la commande suivante pour générer votre application :</span><span class="sxs-lookup"><span data-stu-id="b1717-200">Run the following command to build your application:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="b1717-201">Accédez à votre répertoire de sortie de génération et utilisez la `spark-submit` commande pour soumettre votre application afin qu’elle s’exécute sur Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b1717-201">Navigate to your build output directory and use the `spark-submit` command to submit your application to run on Apache Spark.</span></span> <span data-ttu-id="b1717-202">Veillez à remplacer  `<version>` par la version de votre Worker .net et `<path-of-input.txt>` par le chemin d’accès de votre fichier *input.txt* est stocké.</span><span class="sxs-lookup"><span data-stu-id="b1717-202">Make sure to replace  `<version>` with the version of your .NET worker and `<path-of-input.txt>` with the path of your *input.txt* file is stored.</span></span>

### <a name="windows"></a>[<span data-ttu-id="b1717-203">Windows</span><span class="sxs-lookup"><span data-stu-id="b1717-203">Windows</span></span>](#tab/windows)

```console
spark-submit ^
--class org.apache.spark.deploy.dotnet.DotnetRunner ^
--master local ^
microsoft-spark-2.4.x-<version>.jar ^
dotnet MySparkApp.dll <path-of-input.txt>
```

### <a name="maclinux"></a>[<span data-ttu-id="b1717-204">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="b1717-204">Mac/Linux</span></span>](#tab/linux)

```bash
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master local \
microsoft-spark-2.4.x-<version>.jar \
dotnet MySparkApp.dll <path-of-input.txt>
```

---

> [!NOTE]
> <span data-ttu-id="b1717-205">Cette commande suppose que vous avez téléchargé Apache Spark et que vous l’avez ajouté à votre variable d’environnement PATH pour pouvoir l’utiliser `spark-submit` .</span><span class="sxs-lookup"><span data-stu-id="b1717-205">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="b1717-206">Dans le cas contraire, vous devez utiliser le chemin d’accès complet (par exemple, *C:\bin\apache-spark\bin\spark-Submit* ou *~/Spark/bin/Spark-Submit*).</span><span class="sxs-lookup"><span data-stu-id="b1717-206">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

<span data-ttu-id="b1717-207">Lorsque votre application s’exécute, les données de nombre de mots du fichier *input.txt* sont écrites dans la console.</span><span class="sxs-lookup"><span data-stu-id="b1717-207">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

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

<span data-ttu-id="b1717-208">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="b1717-208">Congratulations!</span></span> <span data-ttu-id="b1717-209">Vous avez créé et exécuté une application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b1717-209">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b1717-210">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b1717-210">Next steps</span></span>

<span data-ttu-id="b1717-211">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="b1717-211">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="b1717-212">Préparer votre environnement pour .NET pour la Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-212">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="b1717-213">Écrire votre première application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-213">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="b1717-214">Générez et exécutez votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-214">Build and run your .NET for Apache Spark application</span></span>

<span data-ttu-id="b1717-215">Pour voir une vidéo expliquant les étapes ci-dessus, consultez la [série de vidéos .net pour Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="b1717-215">To see a video explaining the steps above, check out the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="b1717-216">Pour plus d’informations, consultez la page des ressources.</span><span class="sxs-lookup"><span data-stu-id="b1717-216">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b1717-217">Ressources .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b1717-217">.NET for Apache Spark Resources</span></span>](../resources/index.md)
