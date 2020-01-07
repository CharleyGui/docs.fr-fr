---
title: 'Didacticiel : classer les violations d’intégrité avec le générateur de modèles'
description: Ce didacticiel explique comment créer un modèle de classification multiclasse à l’aide du générateur de modèles ML.NET pour classifier le niveau de gravité de violation de l’intégrité d’un restaurant à San Francisco.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 90abbc9ffe5765880d18d0d29c8e13bc1330ddc3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341555"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>Didacticiel : classer la gravité des violations d’intégrité d’un restaurant avec le générateur de modèles

Découvrez comment créer un modèle de classification multiclasse à l’aide du générateur de modèles pour catégoriser le niveau de risque des violations de restaurant détectées lors des inspections de l’intégrité.

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
>
> - Préparer et comprendre les données
> - Choisir un scénario
> - Charger des données à partir d’une base de données
> - Effectuer l’apprentissage du modèle
> - Évaluer le modèle
> - Utiliser le modèle pour les prévisions

> [!NOTE]
> Model Builder est actuellement en préversion.

## <a name="prerequisites"></a>Configuration requise

Pour obtenir la liste des conditions préalables et des instructions d’installation, consultez le [Guide d’installation du générateur de modèles](../how-to-guides/install-model-builder.md).

## <a name="model-builder-multiclass-classification-overview"></a>Vue d’ensemble de la classification multiclasse de générateur de modèles

Cet exemple crée une C# application console .net core qui catégorise les risques de violations d’intégrité à l’aide d’un modèle de machine learning généré avec le générateur de modèles. Vous pouvez trouver le code source de ce didacticiel dans le référentiel GitHub [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) .

## <a name="create-a-console-application"></a>Créer une application console

1. Créez une  **C# application console .net Core** appelée « RestaurantViolations ». Vérifiez que la case à cocher **Placer la solution et le projet dans le même répertoire** est **désactivée** (vs 2019) ou que l’option **créer le répertoire pour la solution** est **cochée** (vs 2017).

## <a name="prepare-and-understand-the-data"></a>Préparer et comprendre les données

> Le jeu de données utilisé pour l’apprentissage et l’évaluation du modèle de Machine Learning provient à l’origine du [département San Francisco des scores de sécurité du restaurant Public Health](https://www.sfdph.org/dph/EH/Food/score/default.asp). Pour plus de commodité, le jeu de données a été condensé pour inclure uniquement les colonnes pertinentes pour l’apprentissage du modèle et la création de prédictions. Visitez le site Web suivant pour en savoir plus sur le [jeu de données](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0).

[Téléchargez le jeu de données des scores de sécurité de restaurant](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) et décompressez-le.

Chaque ligne du jeu de données contient des informations relatives aux violations observées au cours d’une inspection du service de contrôle d’intégrité et une évaluation des risques de la menace que ces violations présentent à la santé publique et à la sécurité.

| InspectionType | ViolationDescription | RiskCategory |
| --- | --- | --- |
| Routine non planifiée | Surfaces de contact alimentaire nettoyées ou désinfectées de manière inappropriée | Risque modéré |
| Nouvelle propriété | Infestation des vermines à risque élevé | Risque élevé |
| Routine non planifiée | Les chiffons de nettoyage ne sont pas nettoyés ou correctement stockés ou expurgés | Risque faible |

- **InspectionType**: type d’inspection. Il peut s’agir de la première inspection d’un nouvel établissement, d’une inspection de routine, d’une inspection des plaintes et de nombreux autres types.
- **ViolationDescription**: description de la violation trouvée lors de l’inspection.
- **RiskCategory**: gravité du risque qu’une violation pose à la sécurité et à la santé publique.

`label` est la colonne à prédire. Lors de l’exécution d’une tâche de classification, l’objectif est d’affecter une catégorie (texte ou numérique). Dans ce scénario de classification, la gravité de la violation se voit affecter la valeur de risque faible, modéré ou élevé. Par conséquent, **RiskCategory** est l’étiquette. Les `features` sont les entrées que vous fournissez au modèle pour prédire les `label`. Dans ce cas, les **InspectionType** et **ViolationDescription** sont utilisés en tant que fonctionnalités ou entrées pour prédire le **RiskCategory**.

## <a name="choose-a-scenario"></a>Choisir un scénario

![Assistant Générateur de modèles dans Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Pour effectuer l’apprentissage de votre modèle, sélectionnez dans la liste des scénarios de Machine Learning disponibles fournis par le générateur de modèles. Dans ce cas, le scénario est la *classification des problèmes*.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet *RestaurantViolations* , puis sélectionnez **Ajouter** > **machine learning**.
1. Pour cet exemple, le scénario est la classification multiclasse. Dans l’étape *scénario* du générateur de modèles, sélectionnez le scénario de **classification des problèmes** .

## <a name="load-the-data"></a>Charger les données

Le générateur de modèles accepte les données d’une base de données SQL Server ou d’un fichier local au format `csv` ou `tsv`.

1. Dans l’étape données de l’outil générateur de modèles, sélectionnez **SQL Server** dans la liste déroulante source de données.
1. Sélectionnez le bouton en regard de la zone **de texte connexion à SQL Server base de données** .
    1. Dans la boîte de dialogue **choisir des données** , sélectionnez **Microsoft SQL Server fichier de base de données**.
    1. Désactivez la case à cocher **toujours utiliser cette sélection** , puis sélectionnez **Continuer**.
    1. Dans la boîte de dialogue **Propriétés de connexion** , sélectionnez **Parcourir** , puis sélectionnez le fichier *RestaurantScores. mdf* téléchargé.
    1. Sélectionnez **OK**.
1. Choisissez **violations** dans la liste déroulante nom de la **table** .
1. Choisissez **RiskCategory** dans la liste déroulante **colonne à prédire (étiquette)** .
1. Laissez les sélections de colonnes par défaut, **InspectionType** et **ViolationDescription**, cochées dans la liste déroulante **colonnes d’entrée (fonctionnalités)** .
1. Sélectionnez le lien **train** pour passer à l’étape suivante dans le générateur de modèles.

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

La tâche de Machine Learning utilisée pour l’apprentissage du modèle de classification des problèmes dans ce didacticiel est la classification multiclasse. Pendant le processus d’apprentissage du modèle, le générateur de modèles forme des modèles distincts à l’aide de différents algorithmes et paramètres de classification multiclasse pour trouver le modèle le plus performant pour votre jeu de données.

Le temps nécessaire à l’apprentissage du modèle est proportionnel à la quantité de données. Le générateur de modèles sélectionne automatiquement une valeur par défaut pour le **temps de formation (en secondes)** en fonction de la taille de votre source de données.

1. Bien que le générateur de modèles définisse la valeur de **temps à former (secondes)** à 10 secondes, augmentez-le à 30 secondes. La formation sur une période plus longue permet au générateur de modèles d’explorer un plus grand nombre d’algorithmes et une combinaison de paramètres dans la recherche du meilleur modèle.
1. Sélectionnez **Commencer l’entraînement**.

    Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.

    - **État** affiche l’état d’achèvement du processus d’apprentissage.
    - **Meilleure précision** affiche la précision du modèle le plus performant trouvé par le générateur de modèles jusqu’à présent. Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test.
    - **Best algorithm** affiche le nom de l’algorithme le plus performant trouvé par le générateur de modèles jusqu’à présent.
    - **Dernier algorithme** affiche le nom de l’algorithme le plus récemment utilisé par le générateur de modèles pour effectuer l’apprentissage du modèle.

1. Une fois l’apprentissage terminé, sélectionnez le lien **évaluer** pour passer à l’étape suivante.

## <a name="evaluate-the-model"></a>Évaluer le modèle

Le résultat de l’étape de formation est le seul modèle qui avait les meilleures performances. Dans l’étape évaluer du générateur de modèles, la section de sortie contient l’algorithme utilisé par le modèle le mieux adapté à l’entrée de **modèle la plus** performante, ainsi que les métriques dans la **meilleure précision de modèle**. En outre, une table de résumé contenant jusqu’à cinq modèles qui ont été explorés et leurs métriques s’affiche.

Si vous n’êtes pas satisfait de vos mesures de précision, vous pouvez facilement essayer d’améliorer la précision du modèle en augmentant la durée nécessaire à l’apprentissage du modèle ou à l’utilisation de plus de données. Sinon, sélectionnez le lien de **code** pour passer à l’étape finale dans le générateur de modèles.

## <a name="add-the-code-to-make-predictions"></a>Ajouter le code pour effectuer des prédictions

Deux projets sont créés à la suite du processus d’apprentissage.

- RestaurantViolationsML. ConsoleApp : application C# console .net core qui contient l’apprentissage du modèle et le code de consommation des exemples.
- RestaurantViolationsML. Model : bibliothèque de classes .NET Standard contenant les modèles de données qui définissent le schéma des données de modèle d’entrée et de sortie, la version enregistrée du modèle le plus performant au cours de l’apprentissage et une classe d’assistance appelée `ConsumeModel` pour effectuer des prédictions.

1. Dans l’étape de code du générateur de modèles, sélectionnez **Ajouter des projets** pour ajouter les projets générés automatiquement à la solution.
1. Ouvrez le fichier *Program.cs* dans le projet *RestaurantViolations* .
1. Ajoutez l’instruction using suivante pour référencer le projet *RestaurantViolationsML. Model* :

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. Pour effectuer une prédiction sur les nouvelles données à l’aide du modèle, créez une nouvelle instance de la classe `ModelInput` à l’intérieur de la méthode `Main` de votre application. Notez que la catégorie risque ne fait pas partie de l’entrée. Cela est dû au fait que le modèle génère la prédiction pour celui-ci.

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. Utilisez la méthode `Predict` de la classe `ConsumeModel`. La méthode `Predict` charge le modèle formé, crée une [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pour le modèle et l’utilise pour effectuer des prédictions sur de nouvelles données.

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. Exécutez l'application.

    La sortie générée par le programme doit se présenter comme l’extrait de code ci-dessous :

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

Si vous devez référencer ultérieurement les projets générés à l’intérieur d’une autre solution, vous pouvez les trouver dans le répertoire `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

Félicitations ! Vous avez correctement créé un modèle de Machine Learning pour classer les risques de violations d’intégrité à l’aide du générateur de modèles. Vous pouvez trouver le code source de ce didacticiel dans le référentiel GitHub [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) .

## <a name="additional-resources"></a>Ressources supplémentaires

Pour en savoir plus sur les rubriques mentionnées dans ce tutoriel, consultez les ressources suivantes :

- [Scénarios du Générateur de modèles](../automate-training-with-model-builder.md#scenarios)
- [Classification multiclasse](../resources/glossary.md#multiclass-classification)
- [Métriques du modèle de classification multiclasse](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
