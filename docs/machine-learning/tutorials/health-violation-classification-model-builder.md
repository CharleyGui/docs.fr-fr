---
title: 'Tutorial: Classify health violations with Model Builder'
description: Ce tutoriel illustre comment construire un modèle de classification multiclasse en utilisant ML.NET Model Builder pour classer la gravité des violations de la santé des restaurants à San Francisco.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: e94313277a025d482105a6d78b6608d4df442c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185842"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>Tutorial: Classify the severity of restaurant health violations with Model Builder

Apprenez à construire un modèle de classification multiclasse à l’aide de Model Builder pour classer le niveau de risque d’infractions aux restaurants constaté lors des inspections de santé.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> - Préparer et comprendre les données
> - Choisir un scénario
> - Chargez les données d’une base de données
> - Effectuer l’apprentissage du modèle
> - Évaluer le modèle
> - Utiliser le modèle pour les prévisions

> [!NOTE]
> Model Builder est actuellement en préversion.

## <a name="prerequisites"></a>Conditions préalables requises

Pour une liste de conditions préalables et d’instructions d’installation, visitez le [guide d’installation Model Builder](../how-to-guides/install-model-builder.md).

## <a name="model-builder-multiclass-classification-overview"></a>Aperçu de classification multiclasse de Model Builder

Cet échantillon crée une application de console C .NET Core qui catégorise le risque de violations de la santé à l’aide d’un modèle d’apprentissage automatique construit avec Model Builder. Vous pouvez trouver le code source pour ce tutoriel au [référentiel GitHub dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)

## <a name="create-a-console-application"></a>Création d’une application console

1. Créez une **application de console C .NET Core** appelée "RestaurantViolations". Assurez-vous que **la solution et le projet Place dans le même répertoire** ne sont pas **contrôlés** (VS 2019), ou **que l’annuaire Créer pour la solution** soit **vérifié** (VS 2017).

## <a name="prepare-and-understand-the-data"></a>Préparer et comprendre les données

> L’ensemble de données utilisé pour former et évaluer le modèle d’apprentissage automatique est originaire [du San Francisco Department of Public Health Restaurant Safety Scores](https://www.sfdph.org/dph/EH/Food/score/default.asp). Pour plus de commodité, le jeu de données a été condensé pour inclure uniquement les colonnes pertinentes pour former le modèle et faire des prédictions. Visitez le site Web suivant pour en savoir plus sur le [jeu de données](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0).

[Téléchargez le jeu de données Restaurant Safety Scores](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) et décompressez-le.

Chaque rangée de l’ensemble de données contient des informations sur les violations observées lors d’une inspection du ministère de la Santé et une évaluation des risques de la menace que représentent les violations présentes à la santé et à la sécurité publiques.

| InspectionType | ViolationDescription | RiskCategory (en) |
| --- | --- | --- |
| Routine - Imprévu | Surfaces de contact alimentaires mal nettoyées ou aseptisées | Risque modéré |
| Nouvelle propriété | Infestation de vermine à haut risque | Risque élevé |
| Routine - Imprévu | Essuyage des chiffons non propres ou bien entreposés ou désinfectants inadéquats | Faible risque |

- **InspectionType**: le type d’inspection. Il peut s’agir soit d’une première inspection pour un nouvel établissement, d’une inspection de routine, d’une inspection des plaintes et de nombreux autres types.
- **ViolationDéscription**: une description de la violation trouvée lors de l’inspection.
- **RiskCategory**: la sévérité du risque qu’une violation constitue pour la santé et la sécurité publiques.

`label` est la colonne à prédire. Lors de l’exécution d’une tâche de classification, l’objectif est d’attribuer une catégorie (texte ou numérique). Dans ce scénario de classification, la gravité de la violation est attribuée à la valeur d’un risque faible, modéré ou élevé. Par conséquent, le **RiskCategory** est l’étiquette. Les `features` entrées que vous donnez le `label`modèle pour prédire le . Dans ce cas, **l’InspectionType** et **ViolationDescription** sont utilisés comme caractéristiques ou entrées pour prédire la **RiskCategory**.

## <a name="choose-a-scenario"></a>Choisir un scénario

![Assistant de constructeur de modèle dans visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Pour former votre modèle, sélectionnez parmi la liste des scénarios d’apprentissage automatique disponibles fournis par Model Builder. Dans ce cas, le scénario est *la classification des questions*.

1. Dans **Solution Explorer**, cliquez à droite sur le projet *RestaurantViolations,* et sélectionnez **Add** > Machine**Learning**.
1. Pour cet échantillon, le scénario est la classification multiclasse. Dans l’étape *du scénario* de Model Builder, sélectionnez le scénario de classification **des problèmes.**

## <a name="load-the-data"></a>Chargement des données

Model Builder accepte les données d’une base `csv` de `tsv` données SQL Server ou d’un fichier local dans ou en format.

1. Dans l’étape de données de l’outil Model Builder, sélectionnez **SQL Server** à partir de la source de données.
1. Sélectionnez le bouton à côté de la boîte **texte de base de données Connect to SQL Server.**
    1. Dans le dialogue **Choisissez les données,** sélectionnez **Microsoft SQL Server Database File**.
    1. Décochez **la toujours utiliser cette** case à cocher de sélection et **sélectionnez Continuer**.
    1. Dans le dialogue **Connection Properties,** **sélectionnez Browse** et sélectionnez le fichier *Télécharger RestaurantScores.mdf.*
    1. Sélectionnez **OK**.
1. Choisissez **les violations** de la chute du nom de **table.**
1. Choisissez **RiskCategory** dans la **colonne pour prédire (label)** dropdown.
1. Laissez les sélections de colonnes par défaut, **InspectionType** et **ViolationDescription**, vérifiées dans les **colonnes d’entrée (Caractéristiques)** dropdown.
1. Sélectionnez le lien **Train** pour passer à l’étape suivante dans Model Builder.

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

La tâche d’apprentissage automatique utilisée pour former le modèle de classification des questions dans ce tutoriel est la classification multiclasse. Pendant le processus de formation du modèle, Model Builder forme des modèles distincts à l’aide de différents algorithmes et paramètres de classification multiclasses pour trouver le modèle le plus performant pour votre jeu de données.

Le temps requis pour que le modèle se forme est proportionnel à la quantité de données. Model Builder sélectionne automatiquement une valeur par défaut pour **le temps de train (secondes)** en fonction de la taille de votre source de données.

1. Bien que Model Builder fixe la valeur du **temps de train (secondes)** à 10 secondes, l’augmenter à 30 secondes. La formation pour une plus longue période de temps permet à Model Builder d’explorer un plus grand nombre d’algorithmes et de combinaison de paramètres à la recherche du meilleur modèle.
1. Sélectionnez **Commencer l’entraînement**.

    Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.

    - **L’état** affiche l’état d’achèvement du processus de formation.
    - **La meilleure précision** affiche la précision du modèle le plus performant trouvé par Model Builder jusqu’à présent. Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test.
    - **Le meilleur algorithme** affiche le nom de l’algorithme le plus performant trouvé par Model Builder jusqu’à présent.
    - **Dernier algorithme** affiche le nom de l’algorithme le plus récemment utilisé par Model Builder pour former le modèle.

1. Une fois la formation terminée, sélectionnez le lien **Evaluate** pour passer à l’étape suivante.

## <a name="evaluate-the-model"></a>Évaluer le modèle

Le résultat de l’étape de formation est le seul modèle qui a eu la meilleure performance. Dans l’étape d’évaluation de Model Builder, la section de sortie contient l’algorithme utilisé par le modèle le plus performant dans **l’entrée du meilleur modèle** avec des mesures dans **la meilleure précision du modèle**. En outre, un tableau sommaire contenant jusqu’à cinq modèles qui ont été explorés et leurs mesures sont affichées.

Si vous n’êtes pas satisfait de vos mesures de précision, certains moyens faciles d’essayer d’améliorer la précision du modèle sont d’augmenter la quantité de temps pour former le modèle ou utiliser plus de données. Dans le cas contraire, sélectionnez le lien **de code** pour passer à l’étape finale de Model Builder.

## <a name="add-the-code-to-make-predictions"></a>Ajouter le code pour effectuer des prédictions

Deux projets sont créés à la suite du processus de formation.

- RestaurantViolationsML.ConsoleApp: A C ' .NET Core Console application qui contient le modèle de formation et de code de consommation d’échantillons.
- RestaurantViolationsML.Modèle: Une bibliothèque de classe standard .NET contenant les modèles de données qui définissent le schéma des données des modèles `ConsumeModel` d’entrée et de sortie, la version enregistrée du modèle le plus performant pendant la formation, et une classe d’aide appelée à faire des prédictions.

1. Dans l’étape de code de Model Builder, sélectionnez **Ajouter des projets** pour ajouter les projets autogénérés à la solution.
1. Ouvrez le fichier *Program.cs* dans le projet *RestaurantViolations.*
1. Ajoutez l’énoncé suivant à l’intention du projet *RestaurantViolationsML.Model* :

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. Pour faire une prédiction sur les nouvelles données à `ModelInput` l’aide du modèle, créez une nouvelle instance de la classe à l’intérieur de la `Main` méthode de votre application. Notez que la catégorie de risque ne fait pas partie de l’entrée. C’est parce que le modèle génère la prédiction pour elle.

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. Utilisez `Predict` la méthode `ConsumeModel` de la classe. La `Predict` méthode charge le modèle [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) formé, crée un pour le modèle, et l’utilise pour faire des prédictions sur de nouvelles données.

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. Exécutez l'application.

    La sortie générée par le programme doit se présenter comme l’extrait de code ci-dessous :

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

Si vous devez référencer ultérieurement les projets générés à l’intérieur d’une autre solution, vous pouvez les trouver dans le répertoire `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

Félicitations ! Vous avez réussi à construire un modèle d’apprentissage automatique pour catégoriser le risque de violations de la santé à l’aide de Model Builder. Vous pouvez trouver le code source pour ce tutoriel au [référentiel GitHub dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)

## <a name="additional-resources"></a>Ressources supplémentaires

Pour en savoir plus sur les rubriques mentionnées dans ce tutoriel, consultez les ressources suivantes :

- [Scénarios du Générateur de modèles](../automate-training-with-model-builder.md#scenarios)
- [Classification multiclasse](../resources/glossary.md#multiclass-classification)
- [Mesures du modèle de classification multiclasse](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
