---
title: 'Didacticiel : créer un projet de recommandation-factorisation de la matrice'
description: Ce tutoriel explique comment créer un système de suggestion de films à l’aide de ML.NET dans une application console .NET. Les étapes de ce tutoriel utilisent le langage C# et Visual Studio 2019.
author: briacht
ms.date: 06/30/2020
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 5445a255d32f824b1e451c828f1d46b3e1c16001
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803376"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a>Didacticiel : créer un conseiller de film à l’aide du factorisation de matrice avec ML.NET

Ce tutoriel explique comment créer un système de suggestion de films à l’aide de ML.NET dans une application console .NET. Les étapes de ce tutoriel utilisent le langage C# et Visual Studio 2019.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> * Sélectionner un algorithme de machine learning.
> * Préparer et charger vos données.
> * Créer et entraîner un modèle.
> * Évaluer un modèle.
> * Déployer et consommer un modèle.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation).

## <a name="machine-learning-workflow"></a>Flux de travail de l’apprentissage automatique

Vous effectuerez les étapes suivantes pour accomplir votre tâche, ainsi que toute autre tâche ML.NET :

1. [Charger vos données](#load-your-data)
2. [Créer et entraîner votre modèle](#build-and-train-your-model)
3. [Évaluer votre modèle](#evaluate-your-model)
4. [Utiliser le modèle](#use-your-model)

## <a name="prerequisites"></a>Prérequis

* [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou version ultérieure ou visual studio 2017 version 15,6 ou ultérieure avec la charge de travail « développement multiplateforme .net Core » installée.

## <a name="select-the-appropriate-machine-learning-task"></a>Sélectionner la tâche d’apprentissage automatique appropriée

Il existe plusieurs façons d’aborder les problèmes de suggestion, par exemple la suggestion d’une liste de films ou d’une liste de produits associés. Dans le cas présent, vous allez prédire l’évaluation (1-5) qu’un utilisateur attribuera à un film spécifique et suggérer ce film si la note est supérieure à un seuil défini (plus l’évaluation est élevée, plus il est probable qu’un utilisateur apprécie un film).

## <a name="create-a-console-application"></a>Création d’une application console

### <a name="create-a-project"></a>Création d’un projet

1. Ouvrez Visual Studio 2017. Sélectionnez **fichier**  >  **nouveau**  >  **projet** dans la barre de menus. Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual C#** suivi du nœud **.NET Core**. Ensuite, sélectionnez le modèle de projet **Application console (.NET Core)**. Dans la zone de texte **Nom**, tapez « MovieRecommender », puis sélectionnez le bouton **OK**.

2. Créez un répertoire nommé *Données* dans votre projet pour enregistrer le jeu de données :

    Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouveau dossier**. Tapez « Données » et appuyez sur Entrée.

3. Installez les packages NuGet **Microsoft.ML** et **Microsoft.ML.Recommender** :

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet et sélectionnez **gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet **Parcourir**, recherchez **Microsoft.ML**, sélectionnez le package dans la liste, puis sélectionnez le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés. Répétez ces étapes pour **Microsoft.ML.Recommender**.

4. Ajoutez les instructions `using` suivantes en tête de votre fichier *Program.cs* :

    [!code-csharp[UsingStatements](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Télécharger vos données

1. Téléchargez les deux jeux de données et enregistrez-les dans le dossier *Données* que vous avez créé :

   * Cliquez avec le bouton droit sur [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) et sélectionnez « Enregistrer le lien (ou la cible) sous... ».
   * Cliquez avec le bouton droit sur [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) et sélectionnez « Enregistrer le lien (ou la cible) sous... ».

     Veillez à enregistrer les \* fichiers. csv dans le dossier de *données* , ou après l’avoir enregistré ailleurs, déplacez les \* fichiers. csv vers le dossier de *données* .

2. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur chacun des fichiers \*.csv, puis sélectionnez **Propriétés**. Sous **avancé**, remplacez la valeur de **copier dans le répertoire de sortie** par **copier si plus récent**.

   ![GIF d’un utilisateur qui sélectionne copier si plus récent dans Visual Studio.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a>Charger vos données

La première étape du processus ML.NET consiste à préparer et à charger les données d’entraînement et de test de votre modèle.

Les données d’évaluation pour les suggestions sont divisées en jeux de données `Train` et `Test`. Les données `Train` sont utilisées pour ajuster votre modèle. Les données `Test` sont utilisées pour élaborer des prédictions avec votre modèle entraîné et à évaluer les performances du modèle. Il est courant d’avoir une répartition 80/20 avec les données `Train` et `Test`.

Voici un aperçu des données de vos fichiers \*.csv :

![Capture d’écran de la préversion du jeu de données CVS.](./media/movie-recommendation/csv-file-dataset-preview.png)

Les fichiers \*.csv comportent quatre colonnes :

* `userId`
* `movieId`
* `rating`
* `timestamp`

En machine learning, les colonnes qui servent à élaborer une prédiction sont appelées [Caractéristiques](../resources/glossary.md#feature), et la colonne contenant la prédiction retournée est appelée [Étiquette](../resources/glossary.md#label).

Puisque vous souhaitez prédire des évaluations de films, c’est la colonne d’évaluation qui est la `Label`. Les trois autres colonnes, `userId`, `movieId` et `timestamp`, sont toutes des `Features` utilisées pour prédire la `Label`.

| Fonctionnalités      | Etiquette         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

C’est à vous de décider quelles `Features` sont utilisées pour prévoir la `Label`. Vous pouvez également utiliser des méthodes comme l’importance de la [fonctionnalité de permutation](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) pour vous aider à sélectionner le meilleur `Features` .

Dans ce cas, vous devez retirer la colonne `timestamp` comme `Feature`, car l’horodatage n’affecte pas vraiment comment un utilisateur évalue un film donné et ne contribue donc pas à la précision de la prédiction :

| Fonctionnalités      | Etiquette         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Ensuite, vous devez définir votre structure de données pour la classe d’entrée.

Ajoutez une nouvelle classe à votre projet :

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter > Nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *MovieRatingData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

Le fichier *MovieRatingData.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction `using` suivante en haut de *MovieRatingData.cs* :

```csharp
using Microsoft.ML.Data;
```

Créez une classe nommée `MovieRating` en supprimant la définition de classe existante et en ajoutant le code suivant dans *MovieRatingData.cs* :

[!code-csharp[MovieRatingClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating` spécifie une classe de données d’entrée. L’attribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) spécifie les colonnes (par index de colonne) du jeu de données qui doivent être chargées. Les colonnes `userId` et `movieId` correspondent à vos `Features` (il s’agit des entrées que vous fournirez au modèle pour prédire la `Label`), et la colonne d’évaluation est la `Label` que vous allez prédire (la sortie du modèle).

Créez une autre classe, `MovieRatingPrediction`, pour représenter les résultats prédits en ajoutant le code suivant après la classe `MovieRating` dans *MovieRatingData.cs* :

[!code-csharp[PredictionClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

Dans *Program.cs*, remplacez `Console.WriteLine("Hello World!")` par le code suivant dans `Main()` :

[!code-csharp[MLContext](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MLContext "Add MLContext")]

La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

Après `Main()`, créez une méthode nommée `LoadData()` :

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> Cette méthode donne une erreur tant que vous n’avez pas ajouté d’instruction de retour aux étapes suivantes.

Initialisez vos variables de chemin de données, chargez les données à partir des fichiers \*.csv, et retournez les données `Train` et `Test` en tant qu’objets `IDataView` en ajoutant la ligne de code suivante dans `LoadData()` :

[!code-csharp[LoadData](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadData "Load data from data paths")]

Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView). `IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte). Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier. Elle prend les variables de chemin de données et retourne un `IDataView`. Dans ce cas, fournissez le chemin pour vos fichiers `Test` et `Train`, et indiquez l’en-tête du fichier texte (pour qu’elle puisse utiliser les noms de colonnes correctement) et la virgule de séparation des données caractère (le séparateur par défaut est un onglet).

Ajoutez le code suivant dans la méthode `Main()` pour appeler votre méthode `LoadData()` et retourner les données `Train` et `Test` :

[!code-csharp[LoadDataMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a>Créer et entraîner votre modèle

Il existe trois concepts majeurs dans ML.NET : les [données](../resources/glossary.md#data), les [transformateurs](../resources/glossary.md#transformer)et les [estimateurs](../resources/glossary.md#estimator).

Les algorithmes d’entraînement de machine Learning nécessitent des données dans un certain format. Les `Transformers` servent à transformer les données tabulaires dans un format compatible.

![Diagramme du flux de données du transformateur.](./media/movie-recommendation/data-transformer-transformed.png)

Vous créez des `Transformers` dans ML.NET en créant des `Estimators`. Les `Estimators` prennent des données et retournent des `Transformers`.

![Diagramme du flux de données de l’estimateur.](./media/movie-recommendation/data-estimator-transformer.png)

L’algorithme d’entraînement de suggestion que vous utiliserez pour l’entraînement de votre modèle est un exemple d’`Estimator`.

Générez un `Estimator` en effectuant les étapes suivantes :

Créez la méthode `BuildAndTrainModel()` juste après la méthode `LoadData()`, en utilisant le code suivant :

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> Cette méthode donne une erreur tant que vous n’avez pas ajouté d’instruction de retour aux étapes suivantes.

Définissez les transformations de données en ajoutant le code suivant à `BuildAndTrainModel()` :

[!code-csharp[DataTransformations](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

Étant donné que `userId` et `movieId` représentent des utilisateurs et des titres de films, et non des valeurs réelles, vous utilisez la méthode [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) pour transformer chaque `userId` et chaque `movieId` en colonne `Feature` de type de clé numérique (un format accepté par les algorithmes de suggestion) et vous les ajoutez en tant que nouvelles colonnes de jeu de données :

| userId | movieId | Etiquette | userIdEncoded | movieIdEncoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1 | 1 | 4 | userKey1 | movieKey1 |
| 1 | 3 | 4 | userKey1 | movieKey2 |
| 1 | 6 | 4 | userKey1 | movieKey3 |

Choisissez l’algorithme de machine learning et ajoutez-le aux définitions de transformation de données en ajoutant la ligne de code suivante dans `BuildAndTrainModel()` :

[!code-csharp[AddAlgorithm](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) est votre algorithme d’entraînement de suggestion.  La [factorisation de matrice](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) est une approche courante pour la suggestion quand vous avez des données concernant la façon dont les utilisateurs ont évalué des produits dans le passé, ce qui est le cas pour les jeux de données dans ce tutoriel. Il existe d’autres algorithmes de suggestion adaptés quand vous avez des données différentes (voir la section [Autres algorithmes de suggestion](#other-recommendation-algorithms) ci-dessous pour en savoir plus).

Dans ce cas, l’algorithme `Matrix Factorization` utilise une méthode appelée « filtrage collaboratif », qui part du principe que si l’utilisateur 1 a le même avis que l’utilisateur 2 sur une certaine question, alors l’utilisateur 1 est davantage susceptible d’avoir le même avis que l’utilisateur 2 sur une autre question.

Par exemple, si les utilisateurs 1 et 2 donnent une évaluation similaire à des films, il est plus probable que l’utilisateur 2 appréciera un film que l’utilisateur 1 a vu et auquel il a donné une évaluation élevée :

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Utilisateur 1 | A vu et apprécié le film | A vu et apprécié le film | A vu et apprécié le film |
| Utilisateur 2 | A vu et apprécié le film | A vu et apprécié le film | N’a pas vu --SUGGÉRER le film |

L’entraîneur de `Matrix Factorization` dispose de plusieurs [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), qui sont détaillées dans la section [Hyperparamètres d’algorithme](#algorithm-hyperparameters) ci-dessous.

Ajustez le modèle aux données `Train` et retournez le modèle entraîné en ajoutant la ligne de code suivante dans la méthode `BuildAndTrainModel()` :

[!code-csharp[FitModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

La méthode [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) entraîne votre modèle avec le jeu de données d’entraînement fourni. Techniquement, elle exécute les définitions `Estimator` en transformant les données et en appliquant l’entraînement, puis retourne le modèle entraîné, qui est un `Transformer`.

Ajoutez la ligne de code suivante dans la méthode `Main()` pour appeler votre méthode `BuildAndTrainModel()` et retourner le modèle entraîné :

[!code-csharp[BuildTrainModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Évaluer votre modèle

Une fois que vous avez entraîné votre modèle, utilisez vos données de test pour évaluer ses performances.

Créez la méthode `EvaluateModel()` juste après la méthode `BuildAndTrainModel()`, en utilisant le code suivant :

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

Transformez les données `Test` en ajoutant le code suivant à `EvaluateModel()` :

[!code-csharp[Transform](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Transform "Transform the test data")]

La méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) établit des prédictions pour plusieurs lignes d’entrée fournies d’un jeu de données de test.

Évaluez le modèle en ajoutant la ligne de code suivante dans la méthode `EvaluateModel()` :

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

Une fois que vous avez le jeu de prédiction, la méthode [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) évalue le modèle (elle compare les valeurs prédites aux `Labels` réelles dans le jeu de données de test et retourne des métriques relatives aux performances du modèle).

Imprimez vos métriques d’évaluation sur la console en ajoutant la ligne de code suivante dans la méthode `EvaluateModel()` :

[!code-csharp[PrintMetrics](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

Ajoutez la ligne de code suivante dans la méthode `Main()` pour appeler votre méthode `EvaluateModel()` :

[!code-csharp[EvaluateModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

À ce stade, la sortie doit ressembler au texte suivant :

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5403   3.1262e+05
   1       0.9221   1.6030e+05
   2       0.8687   1.5046e+05
   3       0.8416   1.4584e+05
   4       0.8142   1.4209e+05
   5       0.7849   1.3907e+05
   6       0.7544   1.3594e+05
   7       0.7266   1.3361e+05
   8       0.6987   1.3110e+05
   9       0.6751   1.2948e+05
  10       0.6530   1.2766e+05
  11       0.6350   1.2644e+05
  12       0.6197   1.2541e+05
  13       0.6067   1.2470e+05
  14       0.5953   1.2382e+05
  15       0.5871   1.2342e+05
  16       0.5781   1.2279e+05
  17       0.5713   1.2240e+05
  18       0.5660   1.2230e+05
  19       0.5592   1.2179e+05
=============== Evaluating the model ===============
Rms: 0.994051469730769
RSquared: 0.412556298844873
```

Dans cette sortie, il existe 20 itérations. Dans chaque itération, la mesure d’erreur diminue et converge de plus en plus proche de 0.

La mesure RMSE (`root of mean squared error`) sert à mesurer les différences entre les valeurs prédites par un modèle et les valeurs observées dans un jeu de données de test. Techniquement, il s’agit de la racine carrée de la moyenne des carrés des erreurs. Plus sa valeur est faible, plus le modèle est bon.

`R Squared` indique le niveau d’adéquation des données avec un modèle. Cette valeur est comprise entre 0 et 1. Une valeur de 0 signifie que les données sont aléatoires ou ne s’intègrent pas au modèle. Une valeur de 1 signifie que le modèle correspond exactement aux données. Il faut que le score `R Squared` soit le plus proche possible de 1.

La création de modèles efficaces est un processus itératif. Celui-ci présente une qualité initiale médiocre, car le tutoriel utilise de petits jeux de données pour permettre un apprentissage rapide du modèle. Si vous n’êtes pas satisfait de la qualité du modèle, vous pouvez essayer de l’améliorer en fournissant de plus gros jeux de données d’apprentissage ou en choisissant d’autres algorithmes d’apprentissage avec différents hyperparamètres pour chacun. Pour plus d’informations, voir la section [Améliorer le modèle](#improve-your-model) ci-dessous.

## <a name="use-your-model"></a>Utiliser le modèle

Vous pouvez maintenant utiliser votre modèle entraîné pour établir des prédictions sur de nouvelles données.

Créez la méthode `UseModelForSinglePrediction()` juste après la méthode `EvaluateModel()`, en utilisant le code suivant :

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Utilisez le `PredictionEngine` pour prédire l’évaluation en ajoutant le code suivant à `UseModelForSinglePrediction()` :

[!code-csharp[PredictionEngine](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas thread-safe. Il est acceptable d’utiliser dans des environnements à thread unique ou prototype. Pour améliorer les performances et la sécurité des threads dans les environnements de production, utilisez le `PredictionEnginePool` service, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d' [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objets à utiliser dans votre application. Pour plus d’informations sur l' [utilisation `PredictionEnginePool` de dans une API Web ASP.net Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application), consultez ce guide.

> [!NOTE]
> L’extension de service `PredictionEnginePool` est disponible en préversion.

Créez une instance de `MovieRating` nommée `testInput` et transmettez-la au moteur de prédiction en ajoutant les lignes de code suivantes dans la méthode `UseModelForSinglePrediction()` :

[!code-csharp[MakeSinglePrediction](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

La fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) établit une prédiction sur une seule colonne de données.

Vous pouvez ensuite utiliser le `Score`, ou évaluation prédite, pour déterminer si vous souhaitez suggérer le film avec movieId 10 à l’utilisateur 6. Plus `Score` est élevé, plus il est probable qu’un utilisateur appréciera un film donné. Dans le cas présent, supposez que vous recommandez des films avec une évaluation prédite supérieure à 3,5.

Pour afficher les résultats, ajoutez les lignes de code suivantes dans la méthode `UseModelForSinglePrediction()` :

[!code-csharp[PrintResults](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

Ajoutez la ligne de code suivante dans la méthode `Main()` pour appeler votre méthode `UseModelForSinglePrediction()` :

[!code-csharp[UseModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

La sortie de cette méthode doit ressembler au texte suivant :

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Enregistrez votre modèle

Pour utiliser votre modèle afin d’établir des prédictions dans des applications pour utilisateur final, vous devez d’abord enregistrer le modèle.

Créez la méthode `SaveModel()` juste après la méthode `UseModelForSinglePrediction()`, en utilisant le code suivant :

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Enregistrez votre modèle entraîné en ajoutant le code suivant dans la méthode `SaveModel()` :

[!code-csharp[SaveModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

Cette méthode enregistre votre modèle entraîné dans un fichier .zip (dans le dossier « Données »), qui peut ensuite être utilisé dans d’autres applications .NET pour établir des prédictions.

Ajoutez la ligne de code suivante dans la méthode `Main()` pour appeler votre méthode `SaveModel()` :

[!code-csharp[SaveModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Utiliser le modèle enregistré

Une fois que vous avez enregistré votre modèle formé, vous pouvez utiliser le modèle dans différents environnements. Consultez [enregistrer et charger des modèles formés](../how-to-guides/save-load-machine-learning-models-ml-net.md) pour apprendre à faire fonctionner un modèle de machine learning formé dans des applications.

## <a name="results"></a>Résultats

Après avoir effectué les étapes ci-dessus, exécutez votre application console (Ctrl + F5). Les résultats de la prédiction unique ci-dessus doivent ressembler à ce qui suit. Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5382   3.1213e+05
   1       0.9223   1.6051e+05
   2       0.8691   1.5050e+05
   3       0.8413   1.4576e+05
   4       0.8145   1.4208e+05
   5       0.7848   1.3895e+05
   6       0.7552   1.3613e+05
   7       0.7259   1.3357e+05
   8       0.6987   1.3121e+05
   9       0.6747   1.2949e+05
  10       0.6533   1.2766e+05
  11       0.6353   1.2636e+05
  12       0.6209   1.2561e+05
  13       0.6072   1.2462e+05
  14       0.5965   1.2394e+05
  15       0.5868   1.2352e+05
  16       0.5782   1.2279e+05
  17       0.5713   1.2227e+05
  18       0.5637   1.2190e+05
  19       0.5604   1.2178e+05
=============== Evaluating the model ===============
Rms: 0.977175077487166
RSquared: 0.43233349213192
=============== Making a prediction ===============
Movie 10 is recommended for user 6
=============== Saving the model to a file ===============
```

Félicitations ! Vous avez réussi à créer un modèle Machine Learning pour la suggestion de films. Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation).

## <a name="improve-your-model"></a>Améliorer votre modèle

Il existe plusieurs façons d’améliorer les performances du modèle afin d’obtenir des prédictions plus précises.

### <a name="data"></a>Données

L’ajout de données d’entraînement comportant suffisamment d’échantillons pour chaque utilisateur et ID de film peut aider à améliorer la qualité du modèle de suggestion.

La [validation croisée](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) est une technique d’évaluation des modèles qui fractionne aléatoirement les données en sous-ensembles (au lieu d’extraire des données de test à partir du jeu de données comme vous l’avez fait dans ce tutoriel) et prend certains groupes comme données d’entraînement et certains autres comme données de test. En termes de qualité du modèle, cette méthode est supérieure à un fractionnement entraînement-test.

### <a name="features"></a>Fonctionnalités

Dans ce tutoriel, vous utilisez uniquement les trois `Features` (`user id`, `movie id` et `rating`) qui sont fournies par le jeu de données.

Même si c’est un bon point de départ, en réalité vous souhaiterez sans doute ajouter d’autres attributs ou `Features` (par exemple l’âge, le sexe, l’emplacement géographique et ainsi de suite) s’ils sont inclus dans le jeu de données. L’ajout de `Features` plus pertinentes peut aider à améliorer les performances de votre modèle de suggestion.

Si vous n’êtes pas sûr de ce qui `Features` peut être le plus pertinent pour votre tâche de machine learning, vous pouvez également utiliser la FCC (Feature contribution Calculation) et l’importance de la [fonctionnalité de permutation](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md), que ml.NET fournit pour découvrir le plus d’influence `Features` .

### <a name="algorithm-hyperparameters"></a>Hyperparamètres d’algorithme

Bien que ML.NET fournisse de bons algorithmes d’entraînement par défaut, vous pouvez optimiser les performances en changeant les [hyperparamètres](../resources/glossary.md#hyperparameter) d’algorithme.

Pour la `Matrix Factorization`, vous pouvez expérimenter avec des hyperparamètres comme [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) et [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) pour voir si cela donne de meilleurs résultats.

Par exemple, dans ce tutoriel, les options d’algorithme sont :

```csharp
var options = new MatrixFactorizationTrainer.Options
{
    MatrixColumnIndexColumnName = "userIdEncoded",
    MatrixRowIndexColumnName = "movieIdEncoded",
    LabelColumnName = "Label",
    NumberOfIterations = 20,
    ApproximationRank = 100
};
```

### <a name="other-recommendation-algorithms"></a>Autres algorithmes de suggestion

L’algorithme de factorisation de matrice avec filtrage collaboratif n’est qu’une approche parmi d’autres pour effectuer des suggestions de films. Dans de nombreux cas, vous ne disposerez peut-être pas des données d’évaluation et aurez uniquement l’historique des films des utilisateurs. Dans d’autres cas, vous aurez peut-être davantage que juste les données d’évaluation de l’utilisateur.

| Algorithm       | Scénario           | Exemple  |
| ------------- |:-------------:| -----:|
| Factorisation de matrice à une classe | Utilisez-la quand vous avez uniquement userId et movieId. Ce style de suggestion est basé sur le scénario de coachat (ou produits fréquemment achetés ensemble), ce qui signifie qu’il suggérera aux clients un ensemble de produits en fonction de leur propre historique de commandes. | [>l’essayer](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Machines de factorisation prenant en charge les champs | Elles permettent d’effectuer des suggestions quand vous disposez d’autres caractéristiques en plus de userId, productId et rating (par exemple la description du produit ou le prix du produit). Cette méthode adopte également une approche avec filtrage collaboratif. | [>l’essayer](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Scénario avec nouvel utilisateur

L’un des problèmes courants dans le filtrage collaboratif est le problème de démarrage à froid, c’est-à-dire quand vous avez un nouvel utilisateur sans données à partir desquelles tirer des inférences. Pour le résoudre, il suffit souvent de demander aux nouveaux utilisateurs de créer un profil et, par exemple, d’évaluer les films qu’ils ont déjà vus. Même si cette méthode met un poids sur l’utilisateur, elle fournit certaines données de départ pour les nouveaux utilisateurs sans aucun historique d’évaluation.

## <a name="resources"></a>Ressources

Les données utilisées dans ce tutoriel sont dérivées du [Jeu de données MovieLens](http://files.grouplens.org/datasets/movielens/).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :

> [!div class="checklist"]
>
> * Sélectionner un algorithme de machine learning.
> * Préparer et charger vos données.
> * Créer et entraîner un modèle.
> * Évaluer un modèle.
> * Déployer et consommer un modèle.

Passer au tutoriel suivant pour en savoir plus
> [!div class="nextstepaction"]
> [Analyse des sentiments](sentiment-analysis.md)
