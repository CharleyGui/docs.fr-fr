---
title: 'Tutorial: Prédire les prix en utilisant la régression avec Model Builder'
description: Ce tutoriel montre comment créer un modèle de régression Model Builder ML.NET pour prédire des prix, plus précisément celui des courses de taxi à New York.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: c027fe57f571c791784b0bdb7ad9503fc49daa1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187698"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a>Tutorial: Prédire les prix en utilisant la régression avec Model Builder

Découvrez comment utiliser Model Builder ML.NET pour générer un modèle de régression pour prédire des prix.  L’application console .NET que vous développez dans ce tutoriel prédit les prix des taxis en fonction de l’historique des prix des courses de taxi à New York.

Le modèle de prédiction des prix de Model Builder peut être utilisé pour tout scénario nécessitant une valeur de prédiction numérique. Voici quelques exemples de scénarios : prédiction des prix de l’immobilier, prédiction de la demande et prévisions des ventes.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Préparer et comprendre les données
> - Choisir un scénario
> - Chargement des données
> - Effectuer l’apprentissage du modèle
> - Évaluer le modèle
> - Utiliser le modèle pour les prévisions

> [!NOTE]
> Model Builder est actuellement en préversion.

## <a name="pre-requisites"></a>Conditions préalables

Pour obtenir la liste des prérequis et les instructions d’installation, consultez le [Guide d’installation de Model Builder](../how-to-guides/install-model-builder.md).

## <a name="create-a-console-application"></a>Création d’une application console

1. Créez une **application de console de base C .NET** appelée «TaxiFarePrediction». Assurez-vous que **la solution et le projet Place dans le même répertoire** ne sont pas **contrôlés** (VS 2019), ou **que l’annuaire Créer pour la solution** soit **vérifié** (VS 2017).

## <a name="prepare-and-understand-the-data"></a>Préparer et comprendre les données

1. Créez un répertoire nommé *Data* dans votre projet pour stocker les fichiers du jeu de données.

1. Le jeu de données utilisé pour l’apprentissage et l’évaluation du modèle de Machine Learning provient à l’origine du jeu de données NYC TLC Taxi Trip.

    1. Pour télécharger le jeu de données, accédez au lien de téléchargement [taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).

    1. Lorsque la page se charge, cliquez avec le bouton droit n’importe où sur la page et sélectionnez **Enregistrer sous**.

    1. Utilisez la boîte de dialogue **Enregistrer sous** pour enregistrer le fichier dans le dossier *Data* que vous avez créé à l’étape précédente.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *taxi-fare-train.csv*, puis sélectionnez **Propriétés**. Sous **Advanced**, changer la valeur de **la copie à l’annuaire de sortie** à copier si plus **récent**.

Chaque ligne du jeu de données `taxi-fare-train.csv` contient les détails de courses effectuées par un taxi.

1. Ouvrez le jeu de données **taxi-fare-train.csv**.

    Le jeu de données fourni contient les colonnes suivantes :

    - **vendor_id :** l’ID du taxi est une fonctionnalité.
    - **rate_code :** le type de tarif de la course de taxi est une fonctionnalité.
    - **passenger_count :** le nombre de passagers embarqués est une fonctionnalité.
    - **trip_time_in_secs :** durée totale de la course. Vous voulez prédire le prix de la course avant de l’effectuer. À ce stade vous ne connaissez pas la durée de la course. Par conséquent, la durée de la course n’est pas une fonctionnalité et vous devez exclure cette colonne du modèle.
    - **trip_distance :** la distance de la course est une fonctionnalité.
    - **payment_type :** le mode de paiement (espèces ou carte de crédit) est une fonctionnalité.
    - **fare_amount :** le prix total payé pour la course est l’étiquette.

`label` est la colonne à prédire. Quand vous effectuez une tâche de régression, l’objectif est de prédire une valeur numérique. Dans ce scénario de prédiction des prix, c’est le coût d’une course de taxi qui est prédit. Par conséquent, **fare_amount** est l’étiquette. Les `features` identifiées sont les entrées que vous fournissez au modèle pour prédire `label`. Dans ce cas, le reste des colonnes, à l’exception de **trip_time_in_secs** sont utilisés comme caractéristiques ou entrées pour prédire le montant du tarif.

## <a name="choose-a-scenario"></a>Choisir un scénario

Pour entraîner votre modèle, vous devez sélectionner dans la liste des scénarios Machine Learning disponibles fournis par Model Builder. Dans ce cas, le scénario est `Price Prediction`.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet *TaxiFarePrediction*, puis sélectionnez **Ajouter** > **Machine Learning**.
1. Dans l’étape de scénario de l’outil Model Builder, sélectionnez le scénario *Prédiction de prix*.

## <a name="load-the-data"></a>Chargement des données

Model Builder accepte des données de deux sources : une base de données SQL Server, ou un fichier csv ou tsv local.

1. Dans l’étape des données de l’outil Model Builder, sélectionnez *Fichier* dans la liste déroulante des sources de données.
1. Sélectionnez le bouton en regard de la zone de texte *Sélectionner un fichier* et utilisez l’Explorateur de fichiers pour parcourir et sélectionner *taxi-fare-test.csv* dans le répertoire *Data*.
1. Choisissez *fare_amount* dans la *colonne pour prédire (label)* dropdown.
1. Élargissez le décrochage *des colonnes d’entrée (Caractéristiques)* et décochez la colonne *trip_time_in_secs* pour l’exclure en tant que fonctionnalité pendant la formation.  Naviguez jusqu’à l’étape de train de l’outil Model Builder.

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

La tâche Machine Learning utilisée pour entraîner le modèle de prédiction des prix de ce tutoriel est la régression. Pendant le processus d’entraînement du modèle, Model Builder entraîne des modèles distincts en utilisant différents algorithmes et paramètres de régression pour trouver le modèle le plus performant pour votre jeu de données.

Le temps nécessaire pour l’entraînement du modèle est proportionnel à la quantité de données. Model Builder sélectionne automatiquement une valeur par défaut pour **le temps de train (secondes)** en fonction de la taille de votre source de données.

1. Laissez la valeur par défaut comme c’est le cas pour *le temps de s’entraîner (secondes)* sauf si vous préférez vous entraîner plus longtemps.
2. Sélectionnez *Commencer l’entraînement*.

Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.

- Le champ État affiche l’état d’achèvement du processus d’entraînement.
- Le champ Meilleure précision affiche la précision du modèle le plus performant trouvé jusqu’à présent par Model Builder. Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test.
- Le champ Meilleur algorithme affiche le nom de l’algorithme le plus performant trouvé jusqu’à présent par Model Builder.
- Le champ Dernier algorithme affiche le nom de l’algorithme le plus récemment utilisé par Model Builder pour entraîner le modèle.

Une fois l’entraînement terminé, accédez à l’étape d’évaluation.

## <a name="evaluate-the-model"></a>Évaluer le modèle

Le résultat de l’étape d’entraînement sera le modèle qui a eu les meilleures performances. Dans l’étape d’évaluation de l’outil Model Builder, la section de la sortie contient l’algorithme utilisé par le modèle le plus performant dans l’entrée *Meilleur modèle* ainsi que des métriques dans *Meilleure qualité du modèle (RSquared)*. Vous voyez aussi un tableau récapitulatif contenant les cinq meilleurs modèles et leurs métriques.

Si vous n’êtes pas satisfait de vos métriques de précision, un moyen facile pour améliorer la précision du modèle consiste à augmenter la quantité de temps pour entraîner le modèle ou à utiliser plus de données. Sinon, accédez à l’étape du code.

## <a name="add-the-code-to-make-predictions"></a>Ajouter le code pour effectuer des prédictions

Deux projets sont créés à la suite du processus d’entraînement.

- TaxiFarePredictionML.ConsoleApp: Une application .NET Core Console qui contient le modèle de formation et de code de consommation d’échantillons.
- TaxiFarePredictionML.Modèle: Une bibliothèque de classe standard .NET contenant les modèles de données qui définissent le schéma des données des `ConsumeModel` modèles d’entrée et de sortie, la version enregistrée du modèle le plus performant pendant la formation et une classe d’aide appelée à faire des prédictions.

1. Dans l’étape du code de l’outil Model Builder, sélectionnez **Ajouter des projets** pour ajouter les projets générés automatiquement à la solution.
1. Ouvrez le fichier *Program.cs* dans le projet *TaxiFarePrediction*.
1. Ajoutez l’énoncé suivant à référence du projet *TaxiFarePredictionML.Model* :

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. Pour faire une prédiction sur les nouvelles données à `ModelInput` l’aide du modèle, créez une nouvelle instance de la classe à l’intérieur de la `Main` méthode de votre application. Notez que le montant de la course ne fait pas partie de l’entrée. Cela est dû au fait que le modèle générera la prédiction pour celui-ci.

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. Utilisez `Predict` la méthode `ConsumeModel` de la classe. La `Predict` méthode charge le modèle [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) formé, créer un pour le modèle et l’utilise pour faire des prédictions sur de nouvelles données.

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. Exécutez l'application.

    La sortie générée par le programme doit se présenter comme l’extrait de code ci-dessous :

    ```bash
    Predicted Fare: 14.96086
    ```

Si vous devez référencer ultérieurement les projets générés à l’intérieur d’une autre solution, vous pouvez les trouver dans le répertoire `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Préparer et comprendre les données
> - Choisir un scénario
> - Chargement des données
> - Effectuer l’apprentissage du modèle
> - Évaluer le modèle
> - Utiliser le modèle pour les prévisions

### <a name="additional-resources"></a>Ressources supplémentaires

Pour en savoir plus sur les rubriques mentionnées dans ce tutoriel, consultez les ressources suivantes :

- [Scénarios du Générateur de modèles](../automate-training-with-model-builder.md#scenarios)
- [Régression](../resources/glossary.md#regression)
- [Métriques du modèle de régression](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [Jeu de données NYC TLC Taxi Trip](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
