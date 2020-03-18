---
title: Déployer un modèle sur Azure Functions
description: Alimentez un modèle Machine Learning d’analyse des sentiments ML.NET à des fins de prédiction sur Internet avec Azure Functions.
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 33afd568bb12b855a3888bec31f2e9bbc3c720da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628668"
---
# <a name="deploy-a-model-to-azure-functions"></a>Déployer un modèle sur Azure Functions

Découvrez comment déployer un modèle Machine Learning ML.NET préentraîné pour effectuer des prédictions sur HTTP par le bais d’un environnement serverless Azure Functions.

> [!NOTE]
> Cet exemple exécute une `PredictionEnginePool` version de prévisualisation du service.

## <a name="prerequisites"></a>Conditions préalables requises

- [Visual Studio 2017 version 15.6 ou plus tard](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) avec la charge de travail ".NET Core cross-platform development" et "Azure development" installé.
- [Outils Azure Functions](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- un modèle préentraîné : Utilisez le [tutoriel Analyse des sentiments dans ML.NET](../tutorials/sentiment-analysis.md) pour générer votre propre modèle ou téléchargez ce [modèle Machine Learning d’analyse des sentiments préentraîné](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip).

## <a name="azure-functions-sample-overview"></a>Azure Functions échantillon aperçu

Cet exemple est une **application CMD HTTP Trigger Azure Functions** qui utilise un modèle de classification binaire préentraînal pour classer le sentiment du texte comme positif ou négatif. Azure Functions offre un moyen facile d’exécuter de petits morceaux de code à l’échelle sur un environnement géré sans serveur dans le cloud. Le code de cet échantillon se trouve sur le référentiel [d’échantillons d’achat de points/machines](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) sur GitHub.

## <a name="create-azure-functions-project"></a>Créer un projet Azure Functions

1. Ouvrez Visual Studio 2017. Sélectionnez **File** > **New** > **Project** à partir de la barre de menu. Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual C#**, suivi du nœud **Cloud**. Ensuite, sélectionnez le modèle de projet **Azure Functions**. Dans la zone de texte **Nom**, tapez « SentimentAnalysisFunctionsApp », puis sélectionnez le bouton **OK**.
1. Dans la boîte de dialogue **Nouveau projet**, ouvrez la liste déroulante au-dessus des options du projet et sélectionnez **Azure Functions v2 (.NET Core)**. Ensuite, sélectionnez le projet **Déclencheur HTTP**, puis sélectionnez le bouton **OK**.
1. Créez un répertoire nommé *MLModels* dans votre projet pour enregistrer votre modèle :

    Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Ajouter** > **Nouveau dossier**. Tapez « MLModels » et appuyez sur Entrée.

1. Installer la **version Microsoft.ML NuGet Package** **1.3.1**:

    Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ML**, sélectionnez ce package dans la liste, puis cliquez sur le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

1. Installez le **Package NuGet Microsoft.Azure.Functions.Extensions** :

    Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.Azure.Functions.Extensions**, sélectionnez ce package dans la liste, puis sélectionnez le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

1. Installer la **version Microsoft.Extensions.ML NuGet Package** **0.15.1**:

    Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**. Choisissez "nuget.org" comme source de paquet, sélectionnez l’onglet Parcourir, recherchez **Microsoft.Extensions.ML,** sélectionnez ce paquet dans la liste et sélectionnez le bouton **Installer.** Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

1. Installer la version **Microsoft.NET.Sdk.Functions NuGet Package** **1.0.31**:

    Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**. Choisissez "nuget.org" comme source de paquet, sélectionnez l’onglet Installé, recherchez **Microsoft.NET.Sdk.Functions**, sélectionnez ce paquet dans la liste, sélectionnez **1.0.31** à partir du dropdown version, et sélectionnez le bouton **Mise à jour.** Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

## <a name="add-pre-trained-model-to-project"></a>Ajouter un modèle préentraîné au projet

1. Copiez votre modèle prédéfini dans le dossier *MLModels*.
1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre fichier de modèle prédéfini et sélectionnez **Propriétés**. Sous **Advanced**, changer la valeur de **la copie à l’annuaire de sortie** à copier si plus **récent**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Créer une fonction Azure d’analyse des sentiments

Créez une classe pour prédire le sentiment. Ajoutez une nouvelle classe à votre projet :

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Fonction Azure** et remplacez la valeur du champ **Nom** par *AnalyzeSentiment.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

1. Dans la boîte de dialogue **Nouvelle fonction Azure**, sélectionnez **Déclencheur HTTP**. Ensuite, sélectionnez le bouton **OK**.

    Le fichier *AnalyzeSentiment.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction suivante `using` en haut du fichier *AnalyzeSentiment.cs* :

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    Par défaut, la classe `AnalyzeSentiment` est `static`. Veillez à supprimer le mot clé `static` de la définition de classe.

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a>Créer des modèles de données

Vous devez créer des classes pour vos données d’entrée et prévisions. Ajoutez une nouvelle classe à votre projet :

1. Créez un répertoire nommé *DataModels* dans votre projet pour enregistrer vos modèles de données : Dans Solution Explorer, cliquez à droite sur votre projet et **sélectionnez Ajouter > nouveau dossier**. Tapez « DataModels » et appuyez sur Entrée.
2. Dans Solution Explorer, cliquez à droite sur l’annuaire *DataModels,* puis **sélectionnez Ajouter > nouvel article**.
3. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *SentimentData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

    Le fichier *SentimentData.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction using suivante en haut du fichier *SentimentData.cs* :

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    Supprimer la définition de classe existante et ajouter le code suivant au fichier *SentimentData.cs* :

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. Dans Solution Explorer, cliquez à droite sur l’annuaire *DataModels,* puis **sélectionnez Ajouter > nouvel article**.
5. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *SentimentPrediction.cs*. Ensuite, sélectionnez le bouton **Ajouter**. Le fichier *SentimentPrediction.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction using suivante en haut du fichier *SentimentPrediction.cs* :

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    Supprimez la définition de classe existante et ajoutez le code suivant au fichier *SentimentPrediction.cs* :

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction` hérite de `SentimentData`, qui fournit l’accès aux données d’origine dans la propriété `SentimentText` ainsi que la sortie générée par le modèle.

## <a name="register-predictionenginepool-service"></a>Inscrire le service PredictionEnginePool

Pour faire une seule prédiction, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)vous devez créer un . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas sans fil. En outre, vous devez créer une instance de celui-ci partout où il est nécessaire dans votre application. Au fur et à mesure que votre application se développe, ce processus peut devenir ingérable. Pour améliorer les performances et la sécurité des `PredictionEnginePool` fils, utilisez [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) une combinaison d’injection de dépendance et le service, qui crée un des objets à utiliser tout au long de votre application.

Le lien suivant fournit plus d’informations si vous voulez en savoir plus sur [l’injection de dépendance](https://en.wikipedia.org/wiki/Dependency_injection).

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et définissez la valeur du champ **Nom** sur *Startup.cs*. Ensuite, sélectionnez le bouton **Ajouter**.
1. Ajoutez les instructions suivantes en utilisant les instructions au sommet de *Startup.cs*:

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. Supprimer le code existant en dessous des instructions à l’aide et ajouter le code suivant :

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. Définissez les variables pour stocker l’environnement dans lequel l’application `Startup` est en cours d’exécution et le chemin de fichier où le modèle est situé à l’intérieur de la classe

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. En dessous, créez un constructeur pour `_environment` définir `_modelPath` les valeurs et les variables. Lorsque l’application est en cours d’exécution localement, l’environnement par défaut est *Développement*.

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. Ensuite, ajoutez une `Configure` nouvelle méthode `PredictionEnginePool` appelée pour enregistrer le service en dessous du constructeur.

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

À un niveau élevé, ce code initialise automatiquement les objets et les services pour une utilisation ultérieure sur demande par l’application au lieu d’avoir à le faire manuellement.

Les modèles d’apprentissage automatique ne sont pas statiques. Au fur et à mesure que de nouvelles données de formation sont disponibles, le modèle est requalifié et redéployé. Une façon d’obtenir la dernière version du modèle dans votre application est de redéployer l’ensemble de l’application. Toutefois, cela introduit des temps d’arrêt d’application. Le `PredictionEnginePool` service fournit un mécanisme pour recharger un modèle mis à jour sans prendre votre application vers le bas.

Définissez `watchForChanges` le `true`paramètre `PredictionEnginePool` à [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) , et le commence un qui écoute le système de fichiers modifier les notifications et soulève des événements quand il ya une modification du fichier. Cela incite `PredictionEnginePool` à recharger automatiquement le modèle.

Le modèle est `modelName` identifié par le paramètre de sorte que plus d’un modèle par application peut être rechargé lors du changement.

> [!TIP]
> Alternativement, vous pouvez `FromUri` utiliser la méthode lorsque vous travaillez avec des modèles stockés à distance. Plutôt que de regarder `FromUri` pour les événements changés de fichier, les sondages de l’emplacement éloigné pour les changements. L’intervalle de vote est par défaut à 5 minutes. Vous pouvez augmenter ou diminuer l’intervalle de vote en fonction des exigences de votre demande. Dans l’échantillon de `PredictionEnginePool` code ci-dessous, les sondages stockés sur l’URI spécifiés chaque minute.
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a>Charger le modèle dans la fonction

Insérez le code suivant à l’intérieur de la classe *AnalyzeSentiment* :

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

Ce code affecte le `PredictionEnginePool` en le passant au constructeur de la fonction, obtenu par injection de dépendances.

## <a name="use-the-model-to-make-predictions"></a>Utiliser le modèle pour élaborer des prédictions

Remplacez l’implémentation existante de la méthode *Run* dans la classe *AnalyzeSentiment* par le code suivant :

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

Quand la méthode `Run` s’exécute, les données entrantes issues de la requête HTTP sont désérialisées et utilisées comme entrée pour le `PredictionEnginePool`. La `Predict` méthode est ensuite appelée `SentimentAnalysisModel` pour faire `Startup` des prédictions en utilisant l’enregistrement dans la classe et retourne les résultats à l’utilisateur en cas de succès.

## <a name="test-locally"></a>Tester les topologies localement

Maintenant que tout est configuré, il est temps de tester l’application :

1. Exécuter l’application
1. Ouvrez PowerShell et entrez le code dans l’invite, où PORT est le port sur lequel s’exécute votre application, en règle générale 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    En cas de réussite, la sortie devrait se présenter ainsi :

    ```powershell
    Negative
    ```

Félicitations ! Vous avez réussi à alimenter votre modèle de façon à effectuer des prédictions sur Internet à l’aide d’une fonction Azure.

## <a name="next-steps"></a>Étapes suivantes

- [Déploiement à Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
