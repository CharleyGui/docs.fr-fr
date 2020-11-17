---
title: Utiliser des blocs-notes Jupyter
titleSuffix: .NET for Apache Spark
description: Utilisez .NET pour Apache Spark dans des environnements interactifs comme Jupyter Notebook, Jupyter Lab ou Visual Studio Code (VS Code)
ms.author: luquinta
author: luisquintanilla
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc, how-to
ms.openlocfilehash: efebaf0a66863eae0f71fbf1158b80260d7469cf
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688174"
---
# <a name="use-net-for-apache-spark-in-jupyter-notebooks"></a><span data-ttu-id="62df0-103">Utiliser .NET pour Apache Spark dans les blocs-notes Jupyter</span><span class="sxs-lookup"><span data-stu-id="62df0-103">Use .NET for Apache Spark in Jupyter notebooks</span></span>

<span data-ttu-id="62df0-104">Dans cet article, vous allez apprendre à exécuter .NET pour Apache Spark travaux de manière interactive dans Jupyter Notebook et Visual Studio Code (VS Code) avec .NET interactive.</span><span class="sxs-lookup"><span data-stu-id="62df0-104">In this article, you learn how to run .NET for Apache Spark jobs interactively in Jupyter Notebook and Visual Studio Code (VS Code) with .NET Interactive.</span></span>

## <a name="about-jupyter"></a><span data-ttu-id="62df0-105">À propos de Jupyter</span><span class="sxs-lookup"><span data-stu-id="62df0-105">About Jupyter</span></span>

<span data-ttu-id="62df0-106">[Jupyter](https://jupyter.org/) est un environnement informatique multiplateforme et open source qui permet aux utilisateurs de créer des prototypes et de développer des applications de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="62df0-106">[Jupyter](https://jupyter.org/) is an open-source, cross-platform computing environment that provides a way for users to prototype and develop applications interactively.</span></span> <span data-ttu-id="62df0-107">Vous pouvez interagir avec Jupyter par le biais d’une grande variété d’interfaces, telles que Jupyter Notebook, Jupyter Lab et VS Code.</span><span class="sxs-lookup"><span data-stu-id="62df0-107">You can interact with Jupyter through a wide variety of interfaces such as Jupyter Notebook, Jupyter Lab, and VS Code.</span></span>

<span data-ttu-id="62df0-108">Dans le contexte de .NET, [.net interactive](https://github.com/dotnet/interactive), un outil Global .net Core, fournit un noyau pour l’écriture de code .net (C#/f #) dans des environnements de calcul interactifs tels que les Jupyter Notebook.</span><span class="sxs-lookup"><span data-stu-id="62df0-108">In the context of .NET, [.NET Interactive](https://github.com/dotnet/interactive), a .NET Core global tool, provides a kernel for writing .NET code (C#/F#) in interactive computing environments such as Jupyter Notebook.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="62df0-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="62df0-109">Prerequisites</span></span>

- [<span data-ttu-id="62df0-110">Kit SDK .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="62df0-110">.NET Core 3.1 SDK</span></span>](../../core/install/index.yml)
- [<span data-ttu-id="62df0-111">Apache Spark</span><span class="sxs-lookup"><span data-stu-id="62df0-111">Apache Spark</span></span>](https://spark.apache.org/downloads.html)
- [<span data-ttu-id="62df0-112">Apache Spark Worker .NET</span><span class="sxs-lookup"><span data-stu-id="62df0-112">Apache Spark .NET Worker</span></span>](https://github.com/dotnet/spark/releases)

<span data-ttu-id="62df0-113">Pour plus d’informations sur la configuration de votre environnement .NET pour Apache Spark, consultez le [didacticiel de mise](../tutorials/get-started.md) en route.</span><span class="sxs-lookup"><span data-stu-id="62df0-113">See the [getting started tutorial](../tutorials/get-started.md) for more information on setting up your .NET for Apache Spark environment.</span></span>

## <a name="prepare-environment"></a><span data-ttu-id="62df0-114">Préparer l’environnement</span><span class="sxs-lookup"><span data-stu-id="62df0-114">Prepare environment</span></span>

<span data-ttu-id="62df0-115">Pour travailler avec des blocs-notes Jupyter, vous avez besoin de deux choses.</span><span class="sxs-lookup"><span data-stu-id="62df0-115">To work with Jupyter Notebooks, you'll need two things.</span></span>

1. <span data-ttu-id="62df0-116">Installer l' [outil .net interactive global](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md) .net</span><span class="sxs-lookup"><span data-stu-id="62df0-116">Install the [.NET Interactive global .NET tool](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)</span></span>
1. <span data-ttu-id="62df0-117">Téléchargez le `Microsoft.Spark` package NuGet.</span><span class="sxs-lookup"><span data-stu-id="62df0-117">Download the `Microsoft.Spark` NuGet package.</span></span>
    1. <span data-ttu-id="62df0-118">Accédez à la page package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) .</span><span class="sxs-lookup"><span data-stu-id="62df0-118">Navigate to the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package page.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="62df0-119">Par défaut, la version la plus récente du package est téléchargée.</span><span class="sxs-lookup"><span data-stu-id="62df0-119">By default, the latest version of the package is downloaded.</span></span> <span data-ttu-id="62df0-120">**Assurez-vous que la version que vous téléchargez est identique à celle de votre Apache Spark Worker .NET.**</span><span class="sxs-lookup"><span data-stu-id="62df0-120">**Make sure that the version you download is the same as your Apache Spark .NET Worker.**</span></span>

    1. <span data-ttu-id="62df0-121">Dans le volet d' **informations** , sélectionnez **Télécharger le package** pour télécharger la dernière version du package.</span><span class="sxs-lookup"><span data-stu-id="62df0-121">In the **Info** pane, select **Download package** to download the latest version of the package.</span></span> <span data-ttu-id="62df0-122">Le nom du package est similaire à  *Microsoft. Spark. [ PACKAGE-VERSION]. nupkg*.</span><span class="sxs-lookup"><span data-stu-id="62df0-122">The name of the package is similar to  *microsoft.spark.[PACKAGE-VERSION].nupkg*.</span></span>
    1. <span data-ttu-id="62df0-123">Décompressez le package téléchargé.</span><span class="sxs-lookup"><span data-stu-id="62df0-123">Unzip the downloaded package.</span></span> <span data-ttu-id="62df0-124">Le répertoire dézippé doit contenir un sous-répertoire appelé *jar*.</span><span class="sxs-lookup"><span data-stu-id="62df0-124">The unzipped directory should contain a subdirectory called *jars*.</span></span> <span data-ttu-id="62df0-125">Prenez note du chemin d’accès, car il est utilisé ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="62df0-125">Take note of the path since it's used at a later time.</span></span>

## <a name="start-net-for-apache-spark"></a><span data-ttu-id="62df0-126">Démarrer .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="62df0-126">Start .NET for Apache Spark</span></span>

<span data-ttu-id="62df0-127">Exécutez la commande suivante pour démarrer .NET pour Apache Spark en mode débogage.</span><span class="sxs-lookup"><span data-stu-id="62df0-127">Run the following command to start .NET for Apache Spark in debug mode.</span></span> <span data-ttu-id="62df0-128">Cette `spark-submit` commande démarre un processus et attend des connexions à partir d’un [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span><span class="sxs-lookup"><span data-stu-id="62df0-128">This `spark-submit` command starts a process and waits for connections from a [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span> <span data-ttu-id="62df0-129">Veillez à fournir le chemin d’accès au `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` pour la version respective de .net pour Apache Spark vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="62df0-129">Make sure to provide the path to the `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` for the respective version of .NET for Apache Spark you're using.</span></span>

<span data-ttu-id="62df0-130">**Ubuntu**</span><span class="sxs-lookup"><span data-stu-id="62df0-130">**Ubuntu**</span></span>

```bash
spark-submit \
    --class org.apache.spark.deploy.dotnet.DotnetRunner \
    --master local \
    <path-to-microsoft-spark-jar> \
    debug
```

<span data-ttu-id="62df0-131">**Windows**</span><span class="sxs-lookup"><span data-stu-id="62df0-131">**Windows**</span></span>

```cmd
spark-submit ^
    --class org.apache.spark.deploy.dotnet.DotnetRunner ^
    --master local ^
    <path-to-microsoft-spark-jar> ^
    debug
```

## <a name="create-a-notebook"></a><span data-ttu-id="62df0-132">Créer un notebook</span><span class="sxs-lookup"><span data-stu-id="62df0-132">Create a notebook</span></span>

<span data-ttu-id="62df0-133">Vous pouvez utiliser différentes interfaces pour interagir avec Jupyter.</span><span class="sxs-lookup"><span data-stu-id="62df0-133">You can use different interfaces to interact with Jupyter.</span></span> <span data-ttu-id="62df0-134">Pour une interface basée sur un navigateur, utilisez les blocs-notes Jupyter ou le laboratoire Jupyter.</span><span class="sxs-lookup"><span data-stu-id="62df0-134">For a browser-based interface, use Jupyter Notebooks or Jupyter Lab.</span></span> <span data-ttu-id="62df0-135">Pour une expérience d’éditeur locale, utilisez VS Code.</span><span class="sxs-lookup"><span data-stu-id="62df0-135">For a local editor experience, use VS Code.</span></span>

### <a name="jupyter-notebooks--jupyter-lab"></a><span data-ttu-id="62df0-136">Blocs-notes Jupyter & Lab Jupyter</span><span class="sxs-lookup"><span data-stu-id="62df0-136">Jupyter Notebooks & Jupyter Lab</span></span>

1. <span data-ttu-id="62df0-137">Dans une autre invite de commandes, démarrez Jupyter Notebook ou le laboratoire Jupyter à l’aide de l’une des commandes ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="62df0-137">In another command prompt, start Jupyter Notebook or Jupyter Lab using one of the commands below:</span></span>

    <span data-ttu-id="62df0-138">**Jupyter Notebook**</span><span class="sxs-lookup"><span data-stu-id="62df0-138">**Jupyter Notebook**</span></span>

    ```bash
    jupyter notebook
    ```

    <span data-ttu-id="62df0-139">**Jupyter Lab**</span><span class="sxs-lookup"><span data-stu-id="62df0-139">**Jupyter Lab**</span></span>

    ```bash
    jupyter lab
    ```

    <span data-ttu-id="62df0-140">Ces commandes lancent une fenêtre de navigateur avec l’interface Jupyter Notebook ou Jupyter Lab.</span><span class="sxs-lookup"><span data-stu-id="62df0-140">These commands launch a browser window with the Jupyter Notebook or Jupyter Lab interface.</span></span>

1. <span data-ttu-id="62df0-141">Dans le navigateur, créez un nouveau bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="62df0-141">In the browser, create a new notebook.</span></span>

    <span data-ttu-id="62df0-142">**Jupyter Notebook**</span><span class="sxs-lookup"><span data-stu-id="62df0-142">**Jupyter Notebook**</span></span>

    <span data-ttu-id="62df0-143">Sélectionner **un nouveau > .net (C#)** ou **New > .net (F #)**</span><span class="sxs-lookup"><span data-stu-id="62df0-143">Select **New > .NET (C#)** or **New > .NET (F#)**</span></span>

    <span data-ttu-id="62df0-144">**Jupyter Lab**</span><span class="sxs-lookup"><span data-stu-id="62df0-144">**Jupyter Lab**</span></span>

    <span data-ttu-id="62df0-145">Dans la fenêtre du lanceur, sélectionnez **.net (C#)** ou **.net (F #)**</span><span class="sxs-lookup"><span data-stu-id="62df0-145">In the Launcher window, select **.NET (C#)** or **.NET (F#)**</span></span>

### <a name="visual-studio-code-preview"></a><span data-ttu-id="62df0-146">Visual Studio Code (version préliminaire)</span><span class="sxs-lookup"><span data-stu-id="62df0-146">Visual Studio Code (preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="62df0-147">Pour utiliser les blocs-notes Jupyter dans VS Code, vous devez installer :</span><span class="sxs-lookup"><span data-stu-id="62df0-147">To use Jupyter Notebooks in VS Code, you have to install:</span></span>
>
>- [<span data-ttu-id="62df0-148">VS Code Insiders</span><span class="sxs-lookup"><span data-stu-id="62df0-148">VS Code Insiders</span></span>](https://code.visualstudio.com/insiders/)
>- [<span data-ttu-id="62df0-149">Extension de bloc-notes .NET interactive</span><span class="sxs-lookup"><span data-stu-id="62df0-149">.NET Interactive Notebooks extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode)

1. <span data-ttu-id="62df0-150">Ouvrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="62df0-150">Open VS Code.</span></span>
1. <span data-ttu-id="62df0-151">Ouvrez l’affichage de la palette de commandes **> palette de commandes**.</span><span class="sxs-lookup"><span data-stu-id="62df0-151">Open the command palette **View > Command Palette**.</span></span>

    <span data-ttu-id="62df0-152">Lorsque la palette de commandes s’affiche, entrez la commande suivante pour créer un nouveau bloc-notes .NET interactive :</span><span class="sxs-lookup"><span data-stu-id="62df0-152">When the command palette appears, enter the following command to create a new .NET Interactive notebook:</span></span>

    ```text
    >.NET Interactive: Create new blank notebook
    ```

    <span data-ttu-id="62df0-153">Si vous souhaitez ouvrir un bloc-notes .NET interactive existant avec l’extension *. ipynb* , vous pouvez également utiliser la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="62df0-153">Alternatively, if you want to open an existing .NET Interactive notebook with the *.ipynb* extension, use the following command:</span></span>

    ```text
    >.NET Interactive: Open notebook
    ```

## <a name="initialize-a-spark-session"></a><span data-ttu-id="62df0-154">Initialiser une session Spark</span><span class="sxs-lookup"><span data-stu-id="62df0-154">Initialize a Spark Session</span></span>

1. <span data-ttu-id="62df0-155">Lorsque le bloc-notes s’ouvre, installez le `Microsoft.Spark` package NuGet.</span><span class="sxs-lookup"><span data-stu-id="62df0-155">When the notebook opens, install the `Microsoft.Spark` NuGet package.</span></span> <span data-ttu-id="62df0-156">Assurez-vous que la version que vous installez est identique à celle du Worker .NET.</span><span class="sxs-lookup"><span data-stu-id="62df0-156">Make sure the version you install is the same as the .NET Worker.</span></span>

    ```text
    #r "nuget:Microsoft.Spark, 0.12.1"
    ```

1. <span data-ttu-id="62df0-157">Ajoutez l’instruction using suivante au bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="62df0-157">Add the following using statement to the notebook.</span></span>

    ```csharp
    using Microsoft.Spark.Sql;
    ```

1. <span data-ttu-id="62df0-158">Initialisez votre [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span><span class="sxs-lookup"><span data-stu-id="62df0-158">Initialize your [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span>

    ```csharp
    var sparkSession =
    SparkSession
        .Builder()
        .AppName("dotnet-interactive-spark")
        .GetOrCreate();
    ```

<span data-ttu-id="62df0-159">Le bloc-notes doit être similaire à celui de l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="62df0-159">The notebook should look similar to the one in the following image.</span></span> <span data-ttu-id="62df0-160">Cet exemple utilise VS Code, mais Jupyter Notebook et Jupyter Lab doivent se présenter de la même façon.</span><span class="sxs-lookup"><span data-stu-id="62df0-160">This example uses VS Code, but Jupyter Notebook and Jupyter Lab should look about the same.</span></span>

> [!div class="mx-imgBorder"]
<span data-ttu-id="62df0-161">![.NET pour Apache Spark Jupyter Notebook VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span><span class="sxs-lookup"><span data-stu-id="62df0-161">![.NET for Apache Spark Jupyter Notebook VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span></span>

## <a name="next-steps"></a><span data-ttu-id="62df0-162">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="62df0-162">Next Steps</span></span>

- [<span data-ttu-id="62df0-163">Bien démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="62df0-163">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
- [<span data-ttu-id="62df0-164">Prédire les sentiments à l’aide de .NET pour Apache Spark et ML.NET</span><span class="sxs-lookup"><span data-stu-id="62df0-164">Predict sentiment using .NET for Apache Spark and ML.NET</span></span>](../tutorials/ml-sentiment-analysis.md)
- <span data-ttu-id="62df0-165">Pour plus d’informations sur .NET interactive, consultez la [documentation interactive .net](https://github.com/dotnet/interactive/blob/main/docs/README.md).</span><span class="sxs-lookup"><span data-stu-id="62df0-165">For more information on .NET Interactive, see the [.NET Interactive documentation](https://github.com/dotnet/interactive/blob/main/docs/README.md).</span></span>
