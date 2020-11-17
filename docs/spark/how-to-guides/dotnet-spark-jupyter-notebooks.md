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
# <a name="use-net-for-apache-spark-in-jupyter-notebooks"></a>Utiliser .NET pour Apache Spark dans les blocs-notes Jupyter

Dans cet article, vous allez apprendre à exécuter .NET pour Apache Spark travaux de manière interactive dans Jupyter Notebook et Visual Studio Code (VS Code) avec .NET interactive.

## <a name="about-jupyter"></a>À propos de Jupyter

[Jupyter](https://jupyter.org/) est un environnement informatique multiplateforme et open source qui permet aux utilisateurs de créer des prototypes et de développer des applications de manière interactive. Vous pouvez interagir avec Jupyter par le biais d’une grande variété d’interfaces, telles que Jupyter Notebook, Jupyter Lab et VS Code.

Dans le contexte de .NET, [.net interactive](https://github.com/dotnet/interactive), un outil Global .net Core, fournit un noyau pour l’écriture de code .net (C#/f #) dans des environnements de calcul interactifs tels que les Jupyter Notebook.

## <a name="prerequisites"></a>Prérequis

- [Kit SDK .NET Core 3.1](../../core/install/index.yml)
- [Apache Spark](https://spark.apache.org/downloads.html)
- [Apache Spark Worker .NET](https://github.com/dotnet/spark/releases)

Pour plus d’informations sur la configuration de votre environnement .NET pour Apache Spark, consultez le [didacticiel de mise](../tutorials/get-started.md) en route.

## <a name="prepare-environment"></a>Préparer l’environnement

Pour travailler avec des blocs-notes Jupyter, vous avez besoin de deux choses.

1. Installer l' [outil .net interactive global](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md) .net
1. Téléchargez le `Microsoft.Spark` package NuGet.
    1. Accédez à la page package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) .

        > [!IMPORTANT]
        > Par défaut, la version la plus récente du package est téléchargée. **Assurez-vous que la version que vous téléchargez est identique à celle de votre Apache Spark Worker .NET.**

    1. Dans le volet d' **informations** , sélectionnez **Télécharger le package** pour télécharger la dernière version du package. Le nom du package est similaire à  *Microsoft. Spark. [ PACKAGE-VERSION]. nupkg*.
    1. Décompressez le package téléchargé. Le répertoire dézippé doit contenir un sous-répertoire appelé *jar*. Prenez note du chemin d’accès, car il est utilisé ultérieurement.

## <a name="start-net-for-apache-spark"></a>Démarrer .NET pour Apache Spark

Exécutez la commande suivante pour démarrer .NET pour Apache Spark en mode débogage. Cette `spark-submit` commande démarre un processus et attend des connexions à partir d’un [SparkSession](xref:Microsoft.Spark.Sql.SparkSession). Veillez à fournir le chemin d’accès au `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` pour la version respective de .net pour Apache Spark vous utilisez.

**Ubuntu**

```bash
spark-submit \
    --class org.apache.spark.deploy.dotnet.DotnetRunner \
    --master local \
    <path-to-microsoft-spark-jar> \
    debug
```

**Windows**

```cmd
spark-submit ^
    --class org.apache.spark.deploy.dotnet.DotnetRunner ^
    --master local ^
    <path-to-microsoft-spark-jar> ^
    debug
```

## <a name="create-a-notebook"></a>Créer un notebook

Vous pouvez utiliser différentes interfaces pour interagir avec Jupyter. Pour une interface basée sur un navigateur, utilisez les blocs-notes Jupyter ou le laboratoire Jupyter. Pour une expérience d’éditeur locale, utilisez VS Code.

### <a name="jupyter-notebooks--jupyter-lab"></a>Blocs-notes Jupyter & Lab Jupyter

1. Dans une autre invite de commandes, démarrez Jupyter Notebook ou le laboratoire Jupyter à l’aide de l’une des commandes ci-dessous :

    **Jupyter Notebook**

    ```bash
    jupyter notebook
    ```

    **Jupyter Lab**

    ```bash
    jupyter lab
    ```

    Ces commandes lancent une fenêtre de navigateur avec l’interface Jupyter Notebook ou Jupyter Lab.

1. Dans le navigateur, créez un nouveau bloc-notes.

    **Jupyter Notebook**

    Sélectionner **un nouveau > .net (C#)** ou **New > .net (F #)**

    **Jupyter Lab**

    Dans la fenêtre du lanceur, sélectionnez **.net (C#)** ou **.net (F #)**

### <a name="visual-studio-code-preview"></a>Visual Studio Code (version préliminaire)

> [!IMPORTANT]
> Pour utiliser les blocs-notes Jupyter dans VS Code, vous devez installer :
>
>- [VS Code Insiders](https://code.visualstudio.com/insiders/)
>- [Extension de bloc-notes .NET interactive](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode)

1. Ouvrez Visual Studio Code.
1. Ouvrez l’affichage de la palette de commandes **> palette de commandes**.

    Lorsque la palette de commandes s’affiche, entrez la commande suivante pour créer un nouveau bloc-notes .NET interactive :

    ```text
    >.NET Interactive: Create new blank notebook
    ```

    Si vous souhaitez ouvrir un bloc-notes .NET interactive existant avec l’extension *. ipynb* , vous pouvez également utiliser la commande suivante :

    ```text
    >.NET Interactive: Open notebook
    ```

## <a name="initialize-a-spark-session"></a>Initialiser une session Spark

1. Lorsque le bloc-notes s’ouvre, installez le `Microsoft.Spark` package NuGet. Assurez-vous que la version que vous installez est identique à celle du Worker .NET.

    ```text
    #r "nuget:Microsoft.Spark, 0.12.1"
    ```

1. Ajoutez l’instruction using suivante au bloc-notes.

    ```csharp
    using Microsoft.Spark.Sql;
    ```

1. Initialisez votre [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).

    ```csharp
    var sparkSession =
    SparkSession
        .Builder()
        .AppName("dotnet-interactive-spark")
        .GetOrCreate();
    ```

Le bloc-notes doit être similaire à celui de l’image suivante. Cet exemple utilise VS Code, mais Jupyter Notebook et Jupyter Lab doivent se présenter de la même façon.

> [!div class="mx-imgBorder"]
![.NET pour Apache Spark Jupyter Notebook VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)

## <a name="next-steps"></a>Étapes suivantes

- [Bien démarrer avec .NET pour Apache Spark](../tutorials/get-started.md)
- [Prédire les sentiments à l’aide de .NET pour Apache Spark et ML.NET](../tutorials/ml-sentiment-analysis.md)
- Pour plus d’informations sur .NET interactive, consultez la [documentation interactive .net](https://github.com/dotnet/interactive/blob/main/docs/README.md).
