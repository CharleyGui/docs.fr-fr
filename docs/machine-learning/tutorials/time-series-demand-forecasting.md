---
title: 'Tutorial: Prévisions de la demande de location de vélos - série de temps'
description: Ce tutoriel vous montre comment prévoir la demande pour un service de location de vélos en utilisant une analyse de la série temporelle et ML.NET.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: bceb32f4ea22ade6d3b49b3a99d7ec48a7ba168d
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607400"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>Tutorial: Prévisions de la demande de service de location de vélos avec analyse des séries chrono temporelles et ML.NET

Découvrez comment prévoir la demande d’un service de location de vélos à l’aide d’analyses ponctuelles nonivate sur les données stockées dans une base de données SQL Server avec ML.NET.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> * Comprendre le problème
> * Chargez les données d’une base de données
> * Créer un modèle de prévision
> * Évaluer le modèle de prévision
> * Enregistrer un modèle de prévision
> * Utiliser un modèle de prévision

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou plus tard ou Visual Studio 2017 version 15.6 ou plus tard avec le ".NET Core cross-platform development" charge de travail installée.

## <a name="time-series-forecasting-sample-overview"></a>Aperçu de l’échantillon de prévision des séries chrono temporelles

Cet exemple est une **application de console de base C .NET** qui prévoit la demande de location de vélos à l’aide d’un algorithme d’analyse de séries chronomètres nonivate connu sous le nom d’analyse du spectre unique. Le code de cet échantillon se trouve sur le référentiel [d’échantillons d’achat de points/machines](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) sur GitHub.

## <a name="understand-the-problem"></a>Comprendre le problème

Afin d’exécuter une opération efficace, la gestion des stocks joue un rôle clé. Avoir trop d’un produit en stock signifie des produits invendus assis sur les étagères ne générant pas de revenus. Avoir trop peu de produits conduit à la perte de ventes et les clients d’acheter auprès de concurrents. Par conséquent, la question constante est, quelle est la quantité optimale d’inventaire à garder sous la main? L’analyse des séries chrono temporelles aide à répondre à ces questions en examinant les données historiques, en identifiant les tendances et en utilisant ces renseignements pour prévoir les valeurs dans le futur.

La technique d’analyse des données utilisées dans ce tutoriel est une analyse de séries chronoueuses non ivariée. L’analyse de la série temporelle nonivate examine une seule observation numérique sur une période de temps à des intervalles précis tels que les ventes mensuelles.

L’algorithme utilisé dans ce tutoriel est [Single Spectrum Analysis (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf). SSA travaille en décomposant une série temporelle en un ensemble de composants principaux. Ces composants peuvent être interprétés comme les parties d’un signal qui correspondent aux tendances, au bruit, à la saisonnalité et à bien d’autres facteurs. Ensuite, ces composants sont reconstruits et utilisés pour prévoir les valeurs dans le futur.

## <a name="create-console-application"></a>Création d’une application de console

1. Créez une nouvelle **application de console C .NET Core** appelée "BikeDemandForecasting".
1. Installer **Microsoft.ML** version **1.4.0** Paquet NuGet
    1. Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**.
    1. Choisissez "nuget.org" comme source de paquet, sélectionnez **l’onglet Parcourir,** recherchez **Microsoft.ML**.
    1. Vérifiez la case à cocher **prérelease Inclure.**
    1. Sélectionnez le bouton **Installer**.
    1. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages répertoriés.
    1. Répétez ces étapes pour **System.Data.SqlClient** version **4.7.0** et **Microsoft.ML.TimeSeries** version **1.4.0**.

### <a name="prepare-and-understand-the-data"></a>Préparer et comprendre les données

1. Créer un répertoire appelé *Data*.
1. Téléchargez le fichier de base de données [ *DailyDemand.mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) et enregistrez-le sur le répertoire *Data.*

> [!NOTE]
> Les données utilisées dans ce tutoriel proviennent de [l’UCI Bike Sharing Dataset](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset). Fanaee-T, Hadi, et Gama, Joao, ' Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

Le jeu de données d’origine contient plusieurs colonnes correspondant à la saisonnalité et aux conditions météorologiques. Pour la brièveté et parce que l’algorithme utilisé dans ce tutoriel ne nécessite que les valeurs d’une seule colonne numérique, le jeu de données d’origine a été condensé pour inclure uniquement les colonnes suivantes:

- **dteday**: La date de l’observation.
- **année**: L’année codée de l’observation (0-2011, 1-2012).
- **cnt**: Le nombre total de locations de vélos pour ce jour-là.

Le jeu de données d’origine est cartographié sur une table de base de données avec le schéma suivant dans une base de données SQL Server.

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

Voici un échantillon des données :

| LocationDate | Year | TotalRentals TotalRentals TotalRentals TotalRent |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>Créer des classes d’entrée et de sortie

1. Ouvrez *Program.cs* fichier et remplacez les relevés existants `using` par les éléments suivants :

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. Créez la classe `ModelInput`. Ci-dessous la `Program` classe, ajoutez le code suivant.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    La `ModelInput` classe contient les colonnes suivantes :

    - **LocationDate**: La date de l’observation.
    - **Année**: L’année codée de l’observation (0-2011, 1-2012).
    - **TotalRentals**: Le nombre total de locations de vélos pour ce jour-là.

1. Créez `ModelOutput` une classe `ModelInput` en dessous de la classe nouvellement créée.

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    La `ModelOutput` classe contient les colonnes suivantes :

    - **PrévisionsRentales**: Les valeurs prévues pour la période prévue.
    - **LowerBoundRentals**: Les valeurs minimales prévues pour la période prévue.
    - **UpperBoundRentals**: Les valeurs maximales prévues pour la période prévue.

### <a name="define-paths-and-initialize-variables"></a>Définir les chemins et les variables d’initialisation

1. À `Main` l’intérieur de la méthode, définissez les variables pour stocker l’emplacement de vos données, de votre chaîne de connexion et où enregistrer le modèle qualifié.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. Initialiser `mlContext` la variable avec [`MLContext`](xref:Microsoft.ML.MLContext) une nouvelle instance de `Main` en ajoutant la ligne suivante à la méthode.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    La [`MLContext`](xref:Microsoft.ML.MLContext) classe est un point de départ pour toutes les opérations ML.NET, et l’initialisation mlContext crée un nouvel environnement ML.NET qui peut être partagé à travers les objets de flux de travail de création modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

## <a name="load-the-data"></a>Chargement des données

1. Créer `DatabaseLoader` qui charge des `ModelInput`enregistrements de type .

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Définissez la requête pour charger les données de la base de données.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    ML.NET algorithmes s’attendent à [`Single`](xref:System.Single)ce que les données soient de type . Par conséquent, les valeurs numériques provenant [`Real`](xref:System.Data.SqlDbType)de la base de données qui ne sont [`Real`](xref:System.Data.SqlDbType)pas de type , une valeur à point flottant de précision unique, doivent être converties en .

    Les `Year` `TotalRental` colonnes et les colonnes sont toutes deux des types d’intégrerie dans la base de données. En `CAST` utilisant la fonction intégrée, ils `Real`sont tous deux jetés à .

1. Créez `DatabaseSource` un pour vous connecter à la base de données et exécuter la requête.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Chargez les données dans un `IDataView`.

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. Le jeu de données contient deux années de données. Seules les données de la première année sont utilisées pour la formation, la deuxième année est prévue pour comparer les valeurs réelles avec les prévisions produites par le modèle. Filtrer les [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) données à l’aide de la transformation.

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    Pour la première année, seules `Year` les valeurs de la colonne `upperBound` inférieures à 1 sont sélectionnées en définissant le paramètre à 1. Inversement, pour la deuxième année, des valeurs supérieures ou `lowerBound` égales à 1 sont sélectionnées en fixant le paramètre à 1.

## <a name="define-time-series-analysis-pipeline"></a>Décrivez le pipeline d’analyse des séries chronos

1. Définissez un pipeline qui utilise le [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) pour prévoir les valeurs dans un jeu de données de série temporelle.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    Le `forecastingPipeline` prend 365 points de données pour la première année et échantillonne ou divise l’ensemble de `seriesLength` données de la série temporelle en intervalles de 30 jours (mensuels) comme spécifié par le paramètre. Chacun de ces échantillons est analysé par une fenêtre hebdomadaire ou de 7 jours. Lors de la détermination de la valeur prévue pour la prochaine période,s, les valeurs des sept jours précédents sont utilisées pour faire une prédiction. Le modèle est configuré pour prévoir sept `horizon` périodes dans l’avenir telles que définies par le paramètre. Parce qu’une prévision est une supposition éclairée, elle n’est pas toujours exacte à 100%. Par conséquent, il est bon de connaître la gamme de valeurs dans les meilleurs et les pires scénarios tels que définis par les limites supérieures et inférieures. Dans ce cas, le niveau de confiance pour les limites inférieures et supérieures est fixé à 95%. Le niveau de confiance peut être augmenté ou diminué en conséquence. Plus la valeur est élevée, plus la plage est large entre les limites supérieures et inférieures pour atteindre le niveau de confiance souhaité.

1. Utilisez [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) la méthode pour former le modèle et `forecastingPipeline`adapter les données à la définition préalable .

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Évaluer le modèle

Évaluez le rendement du modèle en prévoyant les données de l’année prochaine et en les comparant aux valeurs réelles.

1. Ci-dessous la `Main` méthode, créer `Evaluate`une nouvelle méthode d’utilité appelée .

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. À `Evaluate` l’intérieur de la méthode, prévoir [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) les données de la deuxième année en utilisant la méthode avec le modèle formé.

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. Obtenez les valeurs réelles des [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) données en utilisant la méthode.

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. Obtenez les valeurs de [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) prévision en utilisant la méthode.

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Calculez la différence entre les valeurs réelles et les valeurs de prévision, communément appelées l’erreur.

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Mesurez les performances en calculant les valeurs d’erreur absolue moyenne et root Mean Squared Error.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    Pour évaluer le rendement, les mesures suivantes sont utilisées :

    - **Erreur absolue moyenne**: Mesure la proximité des prédictions avec la valeur réelle. Cette valeur varie entre 0 et l’infini. Plus le plus proche de 0, mieux la qualité du modèle.
    - **Root Mean Squared Error**: résume l’erreur dans le modèle. Cette valeur varie entre 0 et l’infini. Plus le plus proche de 0, mieux la qualité du modèle.

1. Sortie des mesures à la console.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. Utilisez `Evaluate` la méthode `Main` à l’intérieur de la méthode.

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Enregistrer le modèle

Si vous êtes satisfait de votre modèle, enregistrez-le pour une utilisation ultérieure dans d’autres applications.

1. Dans `Main` la méthode, [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)créer un . [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)est une méthode de commodité pour faire des prédictions uniques.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Enregistrez le modèle `MLModel.zip` sur un fichier `modelPath` appelé comme spécifié par la variable précédemment définie. Utilisez [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) la méthode pour enregistrer le modèle.

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Utiliser le modèle pour prévoir la demande

1. Ci-dessous la `Evaluate` méthode, créer `Forecast`une nouvelle méthode d’utilité appelée .

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. À `Forecast` l’intérieur [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) de la méthode, utilisez la méthode pour prévoir les locations pour les sept prochains jours.

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Alignez les valeurs réelles et prévisionnelles pendant sept périodes.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. Itérer à travers la sortie de prévision et l’afficher sur la console.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Exécution de l'application

1. À `Main` l’intérieur `Forecast` de la méthode, appelez la méthode.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Exécutez l'application. La sortie similaire à celle ci-dessous doit apparaître sur la console. Pour la brièveté, la sortie a été condensée.

    ```text
    Evaluation Metrics
    ---------------------
    Mean Absolute Error: 726.416
    Root Mean Squared Error: 987.658

    Rental Forecast
    ---------------------
    Date: 1/1/2012
    Actual Rentals: 2294
    Lower Estimate: 1197.842
    Forecast: 2334.443
    Upper Estimate: 3471.044

    Date: 1/2/2012
    Actual Rentals: 1951
    Lower Estimate: 1148.412
    Forecast: 2360.861
    Upper Estimate: 3573.309
    ```

L’inspection des valeurs réelles et prévues montre les relations suivantes :

![Comparaison réelle par rapport aux prévisions](./media/time-series-demand-forecasting/forecast.png)

Bien que les valeurs prévues ne prédisent pas le nombre exact de locations, elles fournissent une gamme plus étroite de valeurs qui permet à une opération d’optimiser leur utilisation des ressources.

Félicitations ! Vous avez maintenant construit avec succès un modèle d’apprentissage automatique de série temporelle pour prévoir la demande de location de vélos.

Vous pouvez trouver le code source pour ce tutoriel au référentiel [dotnet/machinelearning-échantillons.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)

## <a name="next-steps"></a>Étapes suivantes

- [Tâches Machine Learning dans ML.NET](../resources/tasks.md)
- [Améliorer la précision du modèle](../resources/improve-machine-learning-model-ml-net.md)
