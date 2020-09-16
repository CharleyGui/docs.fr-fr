---
title: 'Didacticiel : prévoir une série chronologique de location de bicyclette'
description: Ce didacticiel vous montre comment prévoir la demande pour un service de location de bicyclettes à l’aide de l’analyse de série chronologique Student et ML.NET.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 214a368ba269103093a90431cdf9e77ab5989c07
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557214"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>Didacticiel : prévoir la demande du service de location de vélos avec l’analyse de série chronologique et ML.NET

Découvrez comment prévoir la demande d’un service de location de bicyclettes à l’aide de l’analyse de série chronologique Student sur les données stockées dans une base de données SQL Server avec ML.NET.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> * Comprendre le problème
> * Charger des données à partir d’une base de données
> * Créer un modèle de prévision
> * Évaluer le modèle de prévision
> * Enregistrer un modèle de prévision
> * Utiliser un modèle de prévision

## <a name="prerequisites"></a>Prérequis

- [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou version ultérieure ou visual studio 2017 version 15,6 ou ultérieure avec la charge de travail « développement multiplateforme .net Core » installée.

## <a name="time-series-forecasting-sample-overview"></a>Vue d’ensemble de l’exemple de prévision de séries chronologiques

Cet exemple est une **application console C# .net Core** qui prévoit la demande de loyers de bicyclettes à l’aide d’un algorithme d’analyse de série chronologique Student appelé analyse du spectre singulier. Le code de cet exemple se trouve dans le référentiel [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) sur GitHub.

## <a name="understand-the-problem"></a>Comprendre le problème

Pour exécuter une opération efficace, la gestion des stocks joue un rôle clé. Le fait d’avoir une trop grande partie d’un produit en stock signifie que les produits invendus se trouvent sur les étagères qui ne génèrent aucun chiffre d’affaires. Le fait d’avoir trop peu de prospects pour les ventes et les clients qui achètent des produits concurrents. Par conséquent, la question constante est, quelle est la quantité optimale d’inventaire à conserver en main ? L’analyse des séries chronologiques vous aide à fournir une réponse à ces questions en examinant les données d’historique, en identifiant les modèles et en utilisant ces informations pour prévoir des valeurs à un moment donné dans le futur.

La technique d’analyse des données utilisée dans ce didacticiel est l’analyse de la série chronologique Student. Les analyses de série chronologique Student examinent une seule observation numérique sur une période à des intervalles spécifiques tels que les ventes mensuelles.

L’algorithme utilisé dans ce didacticiel est l' [analyse du spectre singulier (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf). La SSA fonctionne en décomposant une série chronologique en un ensemble de composants principaux. Ces composants peuvent être interprétés comme les parties d’un signal qui correspondent aux tendances, au bruit, au caractère saisonnier et à de nombreux autres facteurs. Ensuite, ces composants sont reconstruits et utilisés pour prévoir des valeurs à un moment donné dans le futur.

## <a name="create-console-application"></a>Création d’une application de console

1. Créez une nouvelle **application console C# .net Core** appelée « BikeDemandForecasting ».
1. Installer le package NuGet de la version **Microsoft.ml**

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**.
    1. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet **Parcourir** , puis recherchez **Microsoft.ml**.
    1. Cochez la case **inclure la version préliminaire** .
    1. Sélectionnez le bouton **Installer**.
    1. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages répertoriés.
    1. Répétez ces étapes pour **System. Data. SqlClient** et **Microsoft. ml. TimeSeries**.

### <a name="prepare-and-understand-the-data"></a>Préparer et comprendre les données

1. Créez un répertoire nommé *Data*.
1. Téléchargez le [fichier de base de données *DailyDemand. mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) et enregistrez-le dans le répertoire de *données* .

> [!NOTE]
> Les données utilisées dans ce didacticiel proviennent du jeu de données de [partage de bicyclette UCI](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset). Fanaee-T, Hadi et Gama, Joao, 'étiquetage des événements combinaison de détecteurs d’ensembles et de connaissances en arrière-plan', progression de l’intelligence artificielle (2013) : pp. 1-15, Springer Link Berlin Heidelberg, [lien Web](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

Le jeu de données d’origine contient plusieurs colonnes correspondant à caractère saisonnier et météo. Par souci de concision et parce que l’algorithme utilisé dans ce didacticiel nécessite uniquement les valeurs d’une colonne numérique unique, le jeu de données d’origine a été condensé pour inclure uniquement les colonnes suivantes :

- **dteday**: date de l’observation.
- **year**: année encodée de l’observation (0 = 2011, 1 = 2012).
- **CNT**: nombre total d’loyers de bicyclettes pour ce jour-là.

Le DataSet d’origine est mappé à une table de base de données avec le schéma suivant dans une base de données SQL Server.

```sql
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

Voici un exemple de données :

| RentalDate | Year | TotalRentals |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>Créer des classes d’entrée et de sortie

1. Ouvrez le fichier *Program.cs* et remplacez les `using` instructions existantes par ce qui suit :

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. Créez la classe `ModelInput`. Sous la `Program` classe, ajoutez le code suivant.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    La `ModelInput` classe contient les colonnes suivantes :

    - **RentalDate**: date de l’observation.
    - **Year**: année encodée de l’observation (0 = 2011, 1 = 2012).
    - **TotalRentals**: nombre total de loyers de vélo pour ce jour-là.

1. Créez `ModelOutput` la classe sous la classe nouvellement créée `ModelInput` .

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    La `ModelOutput` classe contient les colonnes suivantes :

    - **ForecastedRentals**: valeurs prédites pour la période prévue.
    - **LowerBoundRentals**: valeurs minimales prédites pour la période prévue.
    - **UpperBoundRentals**: valeurs maximales prédites pour la période prévue.

### <a name="define-paths-and-initialize-variables"></a>Définir des chemins d’accès et initialiser des variables

1. À l’intérieur de la `Main` méthode, définissez des variables pour stocker l’emplacement de vos données, la chaîne de connexion et l’emplacement où enregistrer le modèle formé.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. Initialisez la `mlContext` variable avec une nouvelle instance de [`MLContext`](xref:Microsoft.ML.MLContext) en ajoutant la ligne suivante à la `Main` méthode.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    La [`MLContext`](xref:Microsoft.ML.MLContext) classe est un point de départ pour toutes les opérations ml.net et l’initialisation de mlContext crée un nouvel environnement ml.net qui peut être partagé entre les objets de flux de travail de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

## <a name="load-the-data"></a>Chargement des données

1. Créer `DatabaseLoader` qui charge les enregistrements de type `ModelInput` .

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Définissez la requête pour charger les données à partir de la base de données.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    Les algorithmes ML.NET attendent que les données soient de type [`Single`](xref:System.Single) . Par conséquent, les valeurs numériques provenant de la base de données qui ne sont pas de type [`Real`](xref:System.Data.SqlDbType) , une valeur à virgule flottante simple précision, doivent être converties en [`Real`](xref:System.Data.SqlDbType) .

    Les `Year` `TotalRental` colonnes et sont toutes deux des types entiers dans la base de données. À l’aide de la `CAST` fonction intégrée, elles sont toutes deux converties en `Real` .

1. Créez un `DatabaseSource` pour vous connecter à la base de données et exécuter la requête.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Chargez les données dans un `IDataView`.

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. Le jeu de données contient deux années de données. Seules les données de la première année sont utilisées pour l’apprentissage, la deuxième année est conservée pour comparer les valeurs réelles par rapport aux prévisions produites par le modèle. Filtrer les données à l’aide de la [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transformation.

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    Pour la première année, seules les valeurs de la `Year` colonne inférieure à 1 sont sélectionnées en affectant la valeur `upperBound` 1 au paramètre. À l’inverse, pour la deuxième année, les valeurs supérieures ou égales à 1 sont sélectionnées en affectant la valeur `lowerBound` 1 au paramètre.

## <a name="define-time-series-analysis-pipeline"></a>Définir le pipeline d’analyse de série chronologique

1. Définissez un pipeline qui utilise [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) pour prévoir des valeurs dans un jeu de données de série chronologique.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    Le `forecastingPipeline` prend 365 points de données pour la première année et échantillonne ou divise le jeu de données de série chronologique en intervalles de 30 jours (mensuels), comme spécifié par le `seriesLength` paramètre. Chacun de ces exemples est analysé par une fenêtre hebdomadaire ou de 7 jours. Lors de la détermination de la valeur prévue pour la ou les périodes suivantes, les valeurs des sept jours précédents sont utilisées pour effectuer une prédiction. Le modèle est défini pour prévoir sept périodes dans le futur, comme défini par le `horizon` paramètre. Comme une prévision est une estimation réfléchie, elle n’est pas toujours de 100% précise. Par conséquent, il est bon de connaître la plage de valeurs dans les scénarios les plus perversaux et les plus pessimistes, comme défini par les limites supérieure et inférieure. Dans ce cas, le niveau de confiance pour les limites inférieure et supérieure est défini sur 95%. Le niveau de confiance peut être augmenté ou réduit en conséquence. Plus la valeur est élevée, plus la plage est large entre les limites supérieure et inférieure pour atteindre le niveau de confiance souhaité.

1. Utilisez la [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) méthode pour former le modèle et ajuster les données au précédemment défini `forecastingPipeline` .

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Évaluer le modèle

Évaluez le comportement du modèle en prévoyant les données de l’année suivante et en les comparant aux valeurs réelles.

1. Sous la `Main` méthode, créez une nouvelle méthode utilitaire appelée `Evaluate` .

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. À l’intérieur de la `Evaluate` méthode, planifiez les données de la deuxième année à l’aide de la [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) méthode avec le modèle formé.

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. Récupérez les valeurs réelles à partir des données à l’aide de la [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) méthode.

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. Récupérez les valeurs de prévision à l’aide de la [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) méthode.

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Calculez la différence entre les valeurs réelles et les valeurs de prévision, communément appelées « erreur ».

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Mesurez les performances en calculant les valeurs d’erreur absolue moyenne et quadratique moyenne.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    Pour évaluer les performances, les métriques suivantes sont utilisées :

    - **Erreur absolue moyenne**: mesure la manière dont les prédictions sont fermées à la valeur réelle. Cette valeur est comprise entre 0 et l’infini. Plus la valeur est proche de 0, meilleure est la qualité du modèle.
    - **Erreur du carré moyen racine**: résume l’erreur dans le modèle. Cette valeur est comprise entre 0 et l’infini. Plus la valeur est proche de 0, meilleure est la qualité du modèle.

1. Sortie des mesures vers la console.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. Utilisez la `Evaluate` méthode à l’intérieur de la `Main` méthode.

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Enregistrer le modèle

Si vous êtes satisfait de votre modèle, enregistrez-le pour une utilisation ultérieure dans d’autres applications.

1. Dans la `Main` méthode, créez un [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) . [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) est une méthode pratique pour effectuer des prédictions uniques.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Enregistrez le modèle dans un fichier appelé `MLModel.zip` comme spécifié par la variable précédemment définie `modelPath` . Utilisez la [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) méthode pour enregistrer le modèle.

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Utiliser le modèle pour prévoir la demande

1. Sous la `Evaluate` méthode, créez une nouvelle méthode utilitaire appelée `Forecast` .

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. À l’intérieur de la `Forecast` méthode, utilisez la [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) méthode pour prévoir les loyers des sept prochains jours.

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Alignez les valeurs réelles et les prévisions sur sept périodes.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. Itérez au sein de la sortie de la prévision et affichez-la sur la console.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Exécution de l'application

1. À l’intérieur de la `Main` méthode, appelez la `Forecast` méthode.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Exécutez l'application. Une sortie semblable à celle ci-dessous doit apparaître sur la console. Par souci de concision, la sortie a été condensée.

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

L’inspection des valeurs réelles et prévues montre les relations suivantes :

![Comparaison entre les prévisions et les prévisions réelles](./media/time-series-demand-forecasting/forecast.png)

Bien que les valeurs prévues ne prédisent pas le nombre exact de loyers, elles fournissent une plage de valeurs plus étroite qui permet à une opération d’optimiser son utilisation des ressources.

Félicitations ! Vous avez maintenant créé avec succès une série chronologique Machine Learning modèle pour prévoir la demande de location de bicyclette.

Vous pouvez trouver le code source de ce didacticiel dans le référentiel [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) .

## <a name="next-steps"></a>Étapes suivantes

- [Tâches Machine Learning dans ML.NET](../resources/tasks.md)
- [Améliorer la précision du modèle](../resources/improve-machine-learning-model-ml-net.md)
