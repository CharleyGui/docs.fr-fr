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
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="3ae9c-103">Tutoriel : Prise en main de .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3ae9c-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="3ae9c-104">Ce didacticiel vous apprend à exécuter un .NET pour Apache Spark application à l’aide de .NET Core sur Windows.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="3ae9c-105">Ce tutoriel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3ae9c-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="3ae9c-106">Préparer votre environnement Windows pour .NET pour la Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3ae9c-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="3ae9c-107">Télécharger **Microsoft. Spark. Worker**</span><span class="sxs-lookup"><span data-stu-id="3ae9c-107">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="3ae9c-108">Générez et exécutez une application .NET simple pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3ae9c-108">Build and run a simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="3ae9c-109">Préparation de votre environnement</span><span class="sxs-lookup"><span data-stu-id="3ae9c-109">Prepare your environment</span></span>

<span data-ttu-id="3ae9c-110">Avant de commencer, assurez-vous que `dotnet`vous `java`pouvez exécuter `spark-shell` ,, `mvn`, à partir de votre ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-110">Before you begin, make sure you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line.</span></span> <span data-ttu-id="3ae9c-111">Si votre environnement est déjà préparé, vous pouvez passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-111">If your environment is already prepared, you can skip to the next section.</span></span> <span data-ttu-id="3ae9c-112">Si vous ne pouvez pas exécuter une partie ou l’ensemble des commandes, suivez les étapes ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-112">If you cannot run any or all of the commands, follow the steps below.</span></span>

1. <span data-ttu-id="3ae9c-113">Téléchargez et installez le [Kit de développement logiciel (SDK) .net Core 2.1 x](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-113">Download and install the [.NET Core 2.1x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span> <span data-ttu-id="3ae9c-114">L’installation du kit de `dotnet` développement logiciel (SDK) ajoute le chaîne d’outils à votre chemin.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-114">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span> <span data-ttu-id="3ae9c-115">Utilisez la commande `dotnet --version` PowerShell pour vérifier l’installation.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-115">Use the PowerShell command `dotnet --version` to verify the installation.</span></span>

2. <span data-ttu-id="3ae9c-116">Installez [Visual studio 2017](https://www.visualstudio.com/downloads/) ou [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) avec les dernières mises à jour.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-116">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/) or [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) with the latest updates.</span></span> <span data-ttu-id="3ae9c-117">Vous pouvez utiliser Community, Professional ou Enterprise.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-117">You can use Community, Professional, or Enterprise.</span></span> <span data-ttu-id="3ae9c-118">La version de la communauté est gratuite.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-118">The Community version is free.</span></span>

   <span data-ttu-id="3ae9c-119">Choisissez les charges de travail suivantes au cours de l’installation:</span><span class="sxs-lookup"><span data-stu-id="3ae9c-119">Choose the following workloads during installation:</span></span>
      * <span data-ttu-id="3ae9c-120">Développement .NET Desktop</span><span class="sxs-lookup"><span data-stu-id="3ae9c-120">.NET desktop development</span></span>
          * <span data-ttu-id="3ae9c-121">Tous les composants requis</span><span class="sxs-lookup"><span data-stu-id="3ae9c-121">All required components</span></span>
          * <span data-ttu-id="3ae9c-122">Outils de développement .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="3ae9c-122">.NET Framework 4.6.1 Development Tools</span></span>
      * <span data-ttu-id="3ae9c-123">Développement multiplateforme .NET Core</span><span class="sxs-lookup"><span data-stu-id="3ae9c-123">.NET Core cross-platform development</span></span>
          * <span data-ttu-id="3ae9c-124">Tous les composants requis</span><span class="sxs-lookup"><span data-stu-id="3ae9c-124">All required components</span></span>

3. <span data-ttu-id="3ae9c-125">Installez [Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-125">Install [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

    * <span data-ttu-id="3ae9c-126">Sélectionnez la version appropriée pour votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-126">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="3ae9c-127">Par exemple, sélectionnez **JDK-8u201-Windows-x64. exe** pour un ordinateur Windows x64.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-127">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span>
    * <span data-ttu-id="3ae9c-128">Utilisez la commande `java -version` PowerShell pour vérifier l’installation.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-128">Use the PowerShell command `java -version` to verify the installation.</span></span>

4. <span data-ttu-id="3ae9c-129">Installez [Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-129">Install [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi).</span></span>
    * <span data-ttu-id="3ae9c-130">Téléchargez [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-130">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span></span>
    * <span data-ttu-id="3ae9c-131">Extraire dans un répertoire local.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-131">Extract to a local directory.</span></span> <span data-ttu-id="3ae9c-132">Par exemple, `c:\bin\apache-maven-3.6.0\`.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-132">For example, `c:\bin\apache-maven-3.6.0\`.</span></span>
    * <span data-ttu-id="3ae9c-133">Ajoutez Apache Maven à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-133">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="3ae9c-134">Si vous avez extrait `c:\bin\apache-maven-3.6.0\`vers, vous devez `c:\bin\apache-maven-3.6.0\bin` ajouter à votre chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-134">If you extracted to `c:\bin\apache-maven-3.6.0\`, you would add `c:\bin\apache-maven-3.6.0\bin` to your PATH.</span></span>
    * <span data-ttu-id="3ae9c-135">Utilisez la commande `mvn -version` PowerShell pour vérifier l’installation.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-135">Use the PowerShell command `mvn -version` to verify the installation.</span></span>

5. <span data-ttu-id="3ae9c-136">Installez [Apache Spark 2.3 +](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-136">Install [Apache Spark 2.3+](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="3ae9c-137">Apache Spark 2.4 + n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-137">Apache Spark 2.4+ isn't supported.</span></span>
    * <span data-ttu-id="3ae9c-138">Téléchargez [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) et extrayez-le dans un dossier local à l’aide d’un outil tel que [7-zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-138">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder using a tool like [7-zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/).</span></span> <span data-ttu-id="3ae9c-139">Par exemple, vous pouvez l’extraire vers `c:\bin\spark-2.3.2-bin-hadoop2.7\`.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-139">For example, you might extract it to `c:\bin\spark-2.3.2-bin-hadoop2.7\`.</span></span>
    * <span data-ttu-id="3ae9c-140">Ajoutez Apache Spark à votre [variable d’environnement PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-140">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="3ae9c-141">Si vous avez extrait `c:\bin\spark-2.3.2-bin-hadoop2.7\`vers, vous devez `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` ajouter à votre chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-141">If you extracted to `c:\bin\spark-2.3.2-bin-hadoop2.7\`, you would add `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` to your PATH.</span></span>
    * <span data-ttu-id="3ae9c-142">Ajoutez une [nouvelle variable](https://www.java.com/en/download/help/path.xml) d’environnement `SPARK_HOME`appelée.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-142">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) called `SPARK_HOME`.</span></span> <span data-ttu-id="3ae9c-143">Si vous avez extrait `C:\bin\spark-2.3.2-bin-hadoop2.7\`vers, `C:\bin\spark-2.3.2-bin-hadoop2.7\` utilisez pour la valeur de la **variable**.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-143">If you extracted to `C:\bin\spark-2.3.2-bin-hadoop2.7\`, use  `C:\bin\spark-2.3.2-bin-hadoop2.7\` for the **Variable value**.</span></span>
    * <span data-ttu-id="3ae9c-144">Vérifiez que vous êtes en mesure `spark-shell` d’exécuter à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-144">Verify you are able to run `spark-shell` from your command line.</span></span>

6. <span data-ttu-id="3ae9c-145">Configurez [winutils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-145">Set up [WinUtils](https://github.com/steveloughran/winutils).</span></span>
    * <span data-ttu-id="3ae9c-146">Téléchargez le fichier binaire **winutils. exe** à partir du [référentiel winutils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-146">Download the **winutils.exe** binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="3ae9c-147">Sélectionnez la version de Hadoop avec laquelle la distribution Spark a été compilée.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-147">Select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="3ae9c-148">Par exemple, vous utilisez **Hadoop-2.7.1** pour **Spark 2.3.2**.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-148">For example, you use **hadoop-2.7.1** for **Spark 2.3.2**.</span></span> <span data-ttu-id="3ae9c-149">La version Hadoop est annotée à la fin du nom du dossier d’installation de Spark.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-149">The Hadoop version is annotated at the end of your Spark install folder name.</span></span>
    * <span data-ttu-id="3ae9c-150">Enregistrez le fichier binaire **winutils. exe** dans le répertoire de votre choix.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-150">Save the **winutils.exe** binary to a directory of your choice.</span></span> <span data-ttu-id="3ae9c-151">Par exemple, `c:\hadoop\bin`.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-151">For example, `c:\hadoop\bin`.</span></span>
    * <span data-ttu-id="3ae9c-152">Définissez `HADOOP_HOME` pour refléter le répertoire avec **winutils. exe** sans `bin`.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-152">Set `HADOOP_HOME` to reflect the directory with **winutils.exe** without `bin`.</span></span> <span data-ttu-id="3ae9c-153">Par exemple, `c:\hadoop`.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-153">For example, `c:\hadoop`.</span></span>
    * <span data-ttu-id="3ae9c-154">Définissez la variable d’environnement PATH à `%HADOOP_HOME%\bin`inclure.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-154">Set the PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span>

<span data-ttu-id="3ae9c-155">Vérifiez que vous pouvez `dotnet`exécuter, `java`, `mvn`, `spark-shell` à partir de votre ligne de commande avant de passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-155">Double check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="download-the-microsoftsparkworker-release"></a><span data-ttu-id="3ae9c-156">Télécharger la version Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="3ae9c-156">Download the Microsoft.Spark.Worker release</span></span>

1. <span data-ttu-id="3ae9c-157">Téléchargez la version [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) à partir de la page .net for Apache Spark GitHub releases sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-157">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub Releases page to your local machine.</span></span> <span data-ttu-id="3ae9c-158">Par exemple, vous pouvez le télécharger sur le chemin d' `c:\bin\Microsoft.Spark.Worker\`accès,.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-158">For example, you might download it to the path, `c:\bin\Microsoft.Spark.Worker\`.</span></span>

2. <span data-ttu-id="3ae9c-159">Créez une [nouvelle variable](https://www.java.com/en/download/help/path.xml) d’environnement `DotnetWorkerPath` appelée et affectez-lui le répertoire dans lequel vous avez téléchargé et extrait **Microsoft. Spark. Worker**.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-159">Create a [new environment variable](https://www.java.com/en/download/help/path.xml) called `DotnetWorkerPath` and set it to the directory where you downloaded and extracted the **Microsoft.Spark.Worker**.</span></span> <span data-ttu-id="3ae9c-160">Par exemple, `c:\bin\Microsoft.Spark.Worker`.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-160">For example, `c:\bin\Microsoft.Spark.Worker`.</span></span>

## <a name="clone-the-net-for-apache-spark-github-repo"></a><span data-ttu-id="3ae9c-161">Cloner le .NET pour Apache Spark GitHub référentiel</span><span class="sxs-lookup"><span data-stu-id="3ae9c-161">Clone the .NET for Apache Spark GitHub repo</span></span>

<span data-ttu-id="3ae9c-162">Utilisez la commande [GitBash](https://gitforwindows.org/) suivante pour cloner le .net pour Apache Spark référentiel sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-162">Use the following [GitBash](https://gitforwindows.org/) command to clone the .NET for Apache Spark repo to your machine.</span></span>

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="3ae9c-163">Écrire un .NET pour une application Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3ae9c-163">Write a .NET for Apache Spark app</span></span>

1. <span data-ttu-id="3ae9c-164">Ouvrez **Visual Studio** et accédez à **fichier > créer un projet > application console (.net Core)** .</span><span class="sxs-lookup"><span data-stu-id="3ae9c-164">Open **Visual Studio** and navigate to **File > Create New Project > Console App (.NET Core)**.</span></span> <span data-ttu-id="3ae9c-165">Nommez l’application **HelloSpark**.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-165">Name the application **HelloSpark**.</span></span>

2. <span data-ttu-id="3ae9c-166">Installez le [package NuGet Microsoft. Spark](https://www.nuget.org/profiles/spark).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-166">Install the [Microsoft.Spark NuGet package](https://www.nuget.org/profiles/spark).</span></span> <span data-ttu-id="3ae9c-167">Pour plus d’informations sur l’installation des packages NuGet, consultez [différentes façons d’installer un package NuGet](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span><span class="sxs-lookup"><span data-stu-id="3ae9c-167">For more information on installing NuGet packages, see [Different ways to install a NuGet Package](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span></span>

3. <span data-ttu-id="3ae9c-168">Dans **Explorateur de solutions**, ouvrez **Program.cs** et écrivez le code C# suivant:</span><span class="sxs-lookup"><span data-stu-id="3ae9c-168">In **Solution Explorer**, open **Program.cs** and write the following C# code:</span></span>

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. <span data-ttu-id="3ae9c-169">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-169">Build the solution.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="3ae9c-170">Exécuter votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3ae9c-170">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="3ae9c-171">Ouvrez **PowerShell** et remplacez le répertoire par le dossier dans lequel votre application est stockée.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-171">Open **PowerShell** and change the directory to the folder where your app is stored.</span></span>

   ```powershell
   cd <your-app-output-directory>
   ```

2. <span data-ttu-id="3ae9c-172">Créez un fichier nommé **People. JSON** avec le contenu suivant:</span><span class="sxs-lookup"><span data-stu-id="3ae9c-172">Create a file called **people.json** with the following content:</span></span>

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. <span data-ttu-id="3ae9c-173">Utilisez la commande PowerShell suivante pour exécuter votre application:</span><span class="sxs-lookup"><span data-stu-id="3ae9c-173">Use the following PowerShell command to run your app:</span></span>

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

<span data-ttu-id="3ae9c-174">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="3ae9c-174">Congratulations!</span></span> <span data-ttu-id="3ae9c-175">Vous avez créé et exécuté une application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-175">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3ae9c-176">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3ae9c-176">Next steps</span></span>

<span data-ttu-id="3ae9c-177">Dans ce tutoriel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="3ae9c-177">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="3ae9c-178">Préparer votre environnement Windows pour .NET pour la Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3ae9c-178">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="3ae9c-179">Télécharger **Microsoft. Spark. Worker**</span><span class="sxs-lookup"><span data-stu-id="3ae9c-179">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="3ae9c-180">Générez et exécutez une application .NET simple pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3ae9c-180">Build and run a simple .NET for Apache Spark application</span></span>

<span data-ttu-id="3ae9c-181">Consultez la page des ressources pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="3ae9c-181">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3ae9c-182">.NET pour les ressources de Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3ae9c-182">.NET for Apache Spark Resources</span></span>](../resources/index.md)
