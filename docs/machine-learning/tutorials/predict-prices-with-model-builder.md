---
title: Prédire des prix en utilisant la régression avec Model Builder
description: Ce tutoriel montre comment créer un modèle de régression Model Builder ML.NET pour prédire des prix, plus précisément celui des courses de taxi à New York.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: db9788e3065a0f2f21d712b2d4826efea2d8a829
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410577"
---
# <a name="predict-prices-using-regression-with-model-builder"></a>Prédire des prix en utilisant la régression avec Model Builder

Découvrez comment utiliser Model Builder ML.NET pour générer un [modèle de régression](../resources/glossary.md#regression) pour prédire des prix.  L’application console .NET que vous développez dans ce tutoriel prédit les prix des taxis en fonction de l’historique des prix des courses de taxi à New York.

Le modèle de prédiction des prix de Model Builder peut être utilisé pour tout scénario nécessitant une valeur de prédiction numérique. Voici quelques exemples de scénarios : prédiction des prix de l’immobilier, prédiction de la demande et prévisions des ventes.

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> * Préparer et comprendre les données
> * Choisir un scénario
> * Charger les données
> * Effectuer l’apprentissage du modèle
> * Évaluer le modèle
> * Utiliser le modèle pour les prévisions

> [!NOTE]
> Model Builder est actuellement en préversion.

## <a name="pre-requisites"></a>Conditions préalables

Pour obtenir la liste des prérequis et les instructions d’installation, consultez le [Guide d’installation de Model Builder](../how-to-guides/install-model-builder.md).

## <a name="create-a-console-application"></a>Créer une application console

1. Créez une **application console .NET Core** appelée « TaxiFarePrediction ».

1. Installez le package NuGet **Microsoft.ML** :

    Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet *TaxiFarePrediction*, puis sélectionnez **Gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet **Parcourir**, recherchez **Microsoft.ML**, sélectionnez le package dans la liste, puis sélectionnez le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

## <a name="prepare-and-understand-the-data"></a>Préparer et comprendre les données

1. Créez un répertoire nommé *Data* dans votre projet pour stocker les fichiers du jeu de données.

1. Téléchargez le jeu de données [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) et enregistrez-le dans le dossier *Data* que vous avez créé à l’étape précédente. Ce jeu de données est utilisé pour entraîner et évaluer le modèle Machine Learning. Ce jeu de données provient du [jeu de données NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *taxi-fare-train.csv*, puis sélectionnez **Propriétés**. Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.

Chaque ligne du jeu de données `taxi-fare-train.csv` contient les détails de courses effectuées par un taxi. 

1. Ouvrez le jeu de données **taxi-fare-train.csv**.

    Le jeu de données fourni contient les colonnes suivantes :

    * **vendor_id :** l’ID du taxi est une fonctionnalité.
    * **rate_code :** le type de tarif de la course de taxi est une fonctionnalité.
    * **passenger_count :** le nombre de passagers embarqués est une fonctionnalité.
    * **trip_time_in_secs :** durée totale de la course. Vous voulez prédire le prix de la course avant de l’effectuer. À ce stade vous ne connaissez pas la durée de la course. Par conséquent, la durée de la course n’est pas une fonctionnalité et vous devez exclure cette colonne du modèle.
    * **trip_distance :** la distance de la course est une fonctionnalité.
    * **payment_type :** le mode de paiement (espèces ou carte de crédit) est une fonctionnalité.
    * **fare_amount :** le prix total payé pour la course est l’étiquette.

`label` est la colonne à prédire. Quand vous effectuez une tâche de régression, l’objectif est de prédire une valeur numérique. Dans ce scénario de prédiction des prix, c’est le coût d’une course de taxi qui est prédit. Par conséquent, **fare_amount** est l’étiquette. Les `features` identifiées sont les entrées que vous fournissez au modèle pour prédire `label`. Dans ce cas, le reste des colonnes sont utilisées comme caractéristiques ou comme entrées pour prédire le prix de la course.

## <a name="choose-a-scenario"></a>Choisir un scénario

Pour entraîner votre modèle, vous devez sélectionner dans la liste des scénarios Machine Learning disponibles fournis par Model Builder. Dans ce cas, le scénario est `Price Prediction`. Pour obtenir une liste plus complète, consultez l’[article donnant une vue d’ensemble de Model Builder](../automate-training-with-model-builder.md#scenarios).

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet *TaxiFarePrediction*, puis sélectionnez **Ajouter** > **Machine Learning**.
1. Dans l’étape de scénario de l’outil Model Builder, sélectionnez le scénario *Prédiction de prix*.

## <a name="load-the-data"></a>Charger les données

Model Builder accepte des données de deux sources : une base de données SQL Server, ou un fichier csv ou tsv local. Pour plus d’informations sur les exigences quant aux formats de données, consultez le [lien](../how-to-guides/install-model-builder.md#limitations) suivant.

1. Dans l’étape des données de l’outil Model Builder, sélectionnez *Fichier* dans la liste déroulante des sources de données.
1. Sélectionnez le bouton en regard de la zone de texte *Sélectionner un fichier* et utilisez l’Explorateur de fichiers pour parcourir et sélectionner *taxi-fare-test.csv* dans le répertoire *Data*.
1. Choisissez *fare_amount* dans la liste déroulante *Étiquette ou colonne à prédire*, puis accédez à l’étape d’entraînement de l’outil Model Builder.

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

La tâche Machine Learning utilisée pour entraîner le modèle de prédiction des prix de ce tutoriel est la régression. Pendant le processus d’entraînement du modèle, Model Builder entraîne des modèles distincts en utilisant différents algorithmes et paramètres de régression pour trouver le modèle le plus performant pour votre jeu de données.

Le temps nécessaire pour l’entraînement du modèle est proportionnel à la quantité de données. Utilisez ce graphique pour vous aider à sélectionner une valeur adéquate pour le champ `Time to train (seconds)` :

*Taille du jeu de données  | Type du jeu de données       | Avg. Durée de l’entraînement*
------------- | ------------------ | --------------
0 - 10 Mo     | Numérique et texte   | 10 s
10 - 100 Mo   | Numérique et texte   | 10 min
100 - 500 Mo  | Numérique et texte   | 30 min
500 - 1 Go    | Numérique et texte   | 60 min
\+ de 1 Go         | Numérique et texte   | \+ de 3 heures

1. Le fichier de données d’entraînement ayant une taille supérieure à 10 Mo, utilisez 600 secondes (10 minutes) comme valeur pour *Durée de l’entraînement (secondes)* .
2. Sélectionnez *Commencer l’entraînement*.

Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.

- Le champ État affiche l’état d’achèvement du processus d’entraînement.
- Le champ Meilleure précision affiche la précision du modèle le plus performant trouvé jusqu’à présent par Model Builder. Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test. 
- Le champ Meilleur algorithme affiche le nom de l’algorithme le plus performant trouvé jusqu’à présent par Model Builder.
- Le champ Dernier algorithme affiche le nom de l’algorithme le plus récemment utilisé par Model Builder pour entraîner le modèle.

Une fois l’entraînement terminé, accédez à l’étape d’évaluation.

## <a name="evaluate-the-model"></a>Évaluer le modèle

Le résultat de l’étape d’entraînement sera le modèle qui a eu les meilleures performances. Dans l’étape d’évaluation de l’outil Model Builder, la section de la sortie contient l’algorithme utilisé par le modèle le plus performant dans l’entrée *Meilleur modèle* ainsi que des métriques dans *Meilleure qualité du modèle (RSquared)* . Vous voyez aussi un tableau récapitulatif contenant les cinq meilleurs modèles et leurs métriques. Pour plus d’informations, consultez [Évaluation des métriques des modèles](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).

Si vous n’êtes pas satisfait de vos métriques de précision, un moyen facile pour améliorer la précision du modèle consiste à augmenter la quantité de temps pour entraîner le modèle ou à utiliser plus de données.

## <a name="use-the-model-for-predictions"></a>Utiliser le modèle pour les prévisions

Deux projets sont créés à la suite du processus d’entraînement.

- TaxiFarePredictionML.ConsoleApp : Une application console .NET qui contient le code d’entraînement et d’utilisation du modèle.
- TaxiFarePredictionML.Model : Une bibliothèque de classes .NET Standard contenant les modèles de données qui définissent le schéma des données du modèle en entrée et en sortie, ainsi que la version enregistrée du modèle le plus performant lors de l’entraînement.

1. Dans la section du code de l’outil Model Builder, sélectionnez **Projets ajoutés** pour ajouter les projets à la solution.
1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet *TaxiFarePrediction*. Ensuite, sélectionnez **Ajouter > Élément existant**. Dans la liste déroulante des types de fichiers, sélectionnez `All Files`, accédez au répertoire du projet *TaxiFarePredictionML.Model* et sélectionnez le fichier `MLModel.zip`. Ensuite, cliquez avec le bouton droit sur le fichier `MLModel.zip` récemment ajouté, puis sélectionnez *Propriétés*. Pour l’option Copier dans le répertoire de sortie, sélectionnez *Copier si plus récent* dans la liste déroulante.
1. Cliquez avec le bouton droit sur le projet *TaxiFarePrediction*. Choisissez ensuite **Ajouter > Référence**. Choisissez le nœud **Projets > Solution** puis, dans la liste, cochez le projet *TaxiFarePredictionML.Model* et sélectionnez OK.

4. Ouvrez le fichier *Program.cs* dans le projet *TaxiFarePrediction*.
5. Ajoutez les instructions using suivantes :

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. Ajoutez la méthode `ConsumeModel` à la classe `Program`. Le `ConsumeModel` va créer un `PredictionEngine` basé sur le modèle généré par Model Builder pour effectuer des prédictions sur de nouvelles données et les afficher sur la console.

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

7. Ajoutez le code suivant à la méthode `Main` et exécutez l’application.

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    La sortie générée par le programme doit se présenter comme l’extrait de code ci-dessous :

    ```bash
    Predicted Fare: 16.82245
    ```

Si vous devez référencer ultérieurement les projets générés à l’intérieur d’une autre solution, vous pouvez les trouver dans le répertoire `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> * Préparer et comprendre les données
> * Choisir un scénario
> * Charger les données
> * Effectuer l’apprentissage du modèle
> * Évaluer le modèle
> * Utiliser le modèle pour les prévisions

Passez à l’un des articles de guide pratique suivants pour découvrir comment déployer votre modèle.

> [!div class="nextstepaction"]
> [Déployer un modèle sur Azure Functions](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [Déployer un modèle sur une API web](../how-to-guides/serve-model-web-api-ml-net.md)
