---
title: 'Didacticiel : classer des fleurs Iris-k-signifiant clustering'
description: Découvrez comment utiliser ML.NET dans un scénario de clustering
author: pkulikov
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 0cc42a196589a7ffe77300c9f2cd9cb28229a0a9
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803974"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Didacticiel : classer des fleurs d’iris à l’aide du clustering k-signifiant avec ML.NET

Ce tutoriel montre comment utiliser ML.NET pour générer un [modèle de clustering](../resources/tasks.md#clustering) pour le [jeu de données Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Comprendre le problème
> - Sélectionner la tâche d’apprentissage automatique appropriée
> - Préparer les données
> - Charger et transformer les données
> - Choisir un algorithme d’apprentissage
> - Effectuer l’apprentissage du modèle
> - Utiliser le modèle pour les prévisions

## <a name="prerequisites"></a>Prérequis

- [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou version ultérieure ou visual studio 2017 version 15,6 ou ultérieure avec la charge de travail « développement multiplateforme .net Core » installée.

## <a name="understand-the-problem"></a>Comprendre le problème

Ce problème concerne la division de l’ensemble des iris en différents groupes basés sur les caractéristiques de la fleur. Ces caractéristiques sont la longueur et la largeur d’un sépale, ainsi que la longueur et la largeur d’un pétale. Pour ce tutoriel, supposons que le type de chaque fleur est inconnu. Vous souhaitez connaître la structure d’un jeu de données à partir des caractéristiques et prédire la façon dont une instance de données s’intègre à cette structure.

## <a name="select-the-appropriate-machine-learning-task"></a>Sélectionner la tâche d’apprentissage automatique appropriée

Comme vous ne savez pas à quel groupe appartient chaque fleur, vous choisissez la tâche [Apprentissage automatique non supervisé](../resources/glossary.md#unsupervised-machine-learning). Pour diviser un jeu de données en groupes de telle sorte que les éléments dans le même groupe soient plus similaires les uns aux autres qu’à ceux des autres groupes, utilisez une tâche d’apprentissage automatique de [clustering](../resources/tasks.md#clustering).

## <a name="create-a-console-application"></a>Création d’une application console

1. Ouvrez Visual Studio. Sélectionnez **fichier**  >  **nouveau**  >  **projet** dans la barre de menus. Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual C#** suivi du nœud **.NET Core**. Ensuite, sélectionnez le modèle de projet **Application console (.NET Core)**. Dans la zone de texte **Nom**, tapez « IrisFlowerClustering », puis sélectionnez le bouton **OK**.

1. Créez un répertoire nommé *Data* dans votre projet pour stocker le jeu de données et les fichiers de modèle :

    Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouveau dossier**. Tapez « Données » et appuyez sur Entrée.

1. Installez le package NuGet **Microsoft.ml** :

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet et sélectionnez **gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet **Parcourir** , recherchez **Microsoft.ml** , puis sélectionnez le bouton **installer** . Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

## <a name="prepare-the-data"></a>Préparer les données

1. Téléchargez le jeu de données [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) et enregistrez-le dans le dossier *Data* que vous avez créé à l’étape précédente. Pour plus d’informations sur le jeu de données Iris, consultez la page Wikipédia [Iris de Fisher](https://en.wikipedia.org/wiki/Iris_flower_data_set) et la page [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris), qui est la source du jeu de données.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *iris.data* et sélectionnez **Propriétés**. Sous **avancé**, remplacez la valeur de **copier dans le répertoire de sortie** par **copier si plus récent**.

Le fichier *iris.data* contient cinq colonnes qui représentent :

- sépales longueur en centimètres
- largeur de sépales en centimètres
- longueur du pétale en centimètres
- largeur du pétale en centimètres
- le type d’iris

Dans le cadre de cet exemple de clustering, ce tutoriel ignore la dernière colonne.

## <a name="create-data-classes"></a>Créer des classes de données

Créez des classes pour les données d’entrée et les prédictions :

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et définissez la valeur du champ **Nom** sur *IrisData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.
1. Ajoutez la directive `using` suivante au nouveau fichier :

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

Supprimez la définition de classe existante et ajoutez le code suivant, qui définit les classes `IrisData` et `ClusterPrediction`, au fichier *IrisData.cs* :

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

`IrisData` est la classe des données d’entrée et a des définitions pour chaque caractéristique du jeu de données. Utilisez l’attribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) pour spécifier les index des colonnes sources dans le fichier de jeu de données.

La classe `ClusterPrediction` représente la sortie du modèle de clustering appliqué à une instance `IrisData`. Utilisez l’attribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) pour lier les champs `PredictedClusterId` et `Distances` aux colonnes **PredictedLabel** et **Score** respectivement. Dans le cas de la tâche de clustering, ces colonnes ont la signification suivante :

- La colonne **PredictedLabel** contient l’ID du cluster prédit.
- La colonne **Score** contient un tableau avec les distances Euclidiennes au carré jusqu’aux centroïdes des clusters. La longueur du tableau est égale au nombre de clusters.

> [!NOTE]
> Utilisez le type `float` pour représenter les valeurs à virgule flottante dans les classes de données d’entrée et de prédiction.

## <a name="define-data-and-model-paths"></a>Définir des chemins de données et de modèle

Revenez au fichier *Program.cs* et ajoutez deux champs pour contenir les chemins du fichier de jeu de données et du fichier pour enregistrer le modèle :

- `_dataPath` contient le chemin du fichier avec le jeu de données utilisé pour l’apprentissage du modèle.
- `_modelPath` contient le chemin du fichier où le modèle formé est stocké.

Ajoutez le code suivant juste au-dessus de la méthode `Main` pour spécifier ces chemins :

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

Pour compiler le code précédent, ajoutez les directives `using` suivantes en haut du fichier *Program.cs* :

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>Créer un contexte ML

Ajoutez les directives `using` supplémentaires suivantes en haut du fichier *Program.cs* :

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

Dans la méthode `Main`, remplacez la ligne `Console.WriteLine("Hello World!");` par le code suivant :

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

La classe <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> représente l’environnement Machine Learning et fournit des mécanismes de journalisation et des points d’entrée pour le chargement des données, l’apprentissage du modèle, la prédiction et d’autres tâches. Cela s’apparente conceptuellement à l’aide `DbContext` dans Entity Framework.

## <a name="set-up-data-loading"></a>Configurer le chargement des données

Ajoutez le code suivant à la `Main` méthode pour configurer la façon de charger les données :

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

La [ `MLContext.Data.LoadFromTextFile` méthode d’extension](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) générique déduit le schéma du jeu de données à partir du `IrisData` type fourni et retourne <xref:Microsoft.ML.IDataView> qui peut être utilisé comme entrée pour les transformateurs.

## <a name="create-a-learning-pipeline"></a>Créer un pipeline d’apprentissage

Pour ce tutoriel, le pipeline d’apprentissage de la tâche de clustering comprend les deux étapes suivantes :

- concaténer des colonnes chargées en une seule colonne **Fonctionnalités**, utilisée par un formateur en clustering ;
- utiliser un formateur <xref:Microsoft.ML.Trainers.KMeansTrainer> pour former le modèle à l’aide de l’algorithme de clustering k-means++.

Ajoutez le code suivant à la méthode `Main` :

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

Le code spécifie que le jeu de données doit être divisé en trois clusters.

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

Les étapes ajoutées dans les sections précédentes ont préparé le pipeline pour l’apprentissage, toutefois, aucune n’a été exécutée. Ajoutez la ligne suivante à la méthode `Main` pour effectuer le chargement des données et l’apprentissage du modèle :

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Enregistrer le modèle

À ce stade, vous disposez d’un modèle qui peut être intégré à n’importe laquelle de vos applications .NET existantes ou nouvelles. Pour enregistrer votre modèle dans un fichier .zip, ajoutez le code suivant à la méthode `Main` :

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Utiliser le modèle pour les prévisions

Pour effectuer des prédictions, utilisez la classe <xref:Microsoft.ML.PredictionEngine%602> qui prend des instances du type d’entrée via le pipeline de transformateur et produit des instances du type de sortie. Ajoutez la ligne suivante à la méthode `Main` pour créer une instance de cette classe :

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas thread-safe. Il est acceptable d’utiliser dans des environnements à thread unique ou prototype. Pour améliorer les performances et la sécurité des threads dans les environnements de production, utilisez le `PredictionEnginePool` service, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d' [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objets à utiliser dans votre application. Pour plus d’informations sur l' [utilisation `PredictionEnginePool` de dans une API Web ASP.net Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application), consultez ce guide.

> [!NOTE]
> L’extension de service `PredictionEnginePool` est disponible en préversion.

Créez la classe `TestIrisData` qui contiendra les instances de données de test :

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *TestIrisData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.
1. Modifiez la classe pour la rendre statique, comme dans l’exemple suivant :

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

Ce tutoriel présente une instance de données d’iris au sein de cette classe. Vous pouvez ajouter d’autres scénarios à tester avec le modèle. Ajoutez le code suivant à la classe `TestIrisData` :

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

Pour déterminer à quel cluster l’élément spécifié appartient, revenez au fichier *Program.cs* et ajoutez le code suivant dans la méthode `Main`:

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

Exécutez le programme pour voir quel cluster contient l’instance de données spécifiée et les distances au carré à partir de cette instance jusqu’aux centroïdes des clusters. Vous devriez obtenir les résultats suivants :

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Félicitations ! Vous venez de créer un modèle d’apprentissage automatique de clustering des iris et l’avez utilisé pour réaliser des prédictions. Vous trouverez le code source de ce tutoriel dans le dépôt GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Comprendre le problème
> - Sélectionner la tâche d’apprentissage automatique appropriée
> - Préparer les données
> - Charger et transformer les données
> - Choisir un algorithme d’apprentissage
> - Effectuer l’apprentissage du modèle
> - Utiliser le modèle pour les prévisions

Consultez notre référentiel GitHub pour continuer l’apprentissage et obtenir d’autres exemples.
> [!div class="nextstepaction"]
> [Référentiel GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/)
