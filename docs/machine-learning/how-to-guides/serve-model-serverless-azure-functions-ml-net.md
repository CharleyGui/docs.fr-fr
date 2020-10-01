---
title: Déployer un modèle sur Azure Functions
description: Alimentez un modèle Machine Learning d’analyse des sentiments ML.NET à des fins de prédiction sur Internet avec Azure Functions.
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 74a7a5b941596ba9fffc62ef87a01763937d88c0
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608775"
---
# <a name="deploy-a-model-to-azure-functions"></a>Déployer un modèle sur Azure Functions

Découvrez comment déployer un modèle Machine Learning ML.NET préentraîné pour effectuer des prédictions sur HTTP par le bais d’un environnement serverless Azure Functions.

> [!NOTE]
> Cet exemple exécute une version préliminaire du `PredictionEnginePool` service.

## <a name="prerequisites"></a>Prérequis

- [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou version ultérieure ou visual studio 2017 version 15,6 ou ultérieure avec les charges de travail « développement multiplateforme .net Core » et « développement Azure ».
- [Outils de Azure Functions](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- PowerShell
- un modèle préentraîné : Utilisez le [tutoriel Analyse des sentiments dans ML.NET](../tutorials/sentiment-analysis.md) pour générer votre propre modèle ou téléchargez ce [modèle Machine Learning d’analyse des sentiments préentraîné](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip).

## <a name="azure-functions-sample-overview"></a>Vue d’ensemble de l’exemple Azure Functions

Cet exemple est un **déclencheur http C# Azure Functions application** qui utilise un modèle de classification binaire préformé pour classer le sentiment de texte comme positif ou négatif. Azure Functions offre un moyen simple d’exécuter de petits morceaux de code à l’échelle sur un environnement sans serveur géré dans le Cloud. Le code de cet exemple se trouve dans le référentiel [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) sur GitHub.

## <a name="create-azure-functions-project"></a>Créer un projet Azure Functions

1. Ouvrez Visual Studio 2017. Sélectionnez **fichier**  >  **nouveau**  >  **projet** dans la barre de menus. Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual C#**, suivi du nœud **Cloud**. Ensuite, sélectionnez le modèle de projet **Azure Functions**. Dans la zone de texte **Nom**, tapez « SentimentAnalysisFunctionsApp », puis sélectionnez le bouton **OK**.
1. Dans la boîte de dialogue **Nouveau projet**, ouvrez la liste déroulante au-dessus des options du projet et sélectionnez **Azure Functions v2 (.NET Core)**. Ensuite, sélectionnez le projet **Déclencheur HTTP**, puis sélectionnez le bouton **OK**.
1. Créez un répertoire nommé *MLModels* dans votre projet pour enregistrer votre modèle :

    Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Ajouter** > **Nouveau dossier**. Tapez « MLModels » et appuyez sur Entrée.

1. Installez le **package NuGet Microsoft.ml** version **1.3.1**:

    Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ML**, sélectionnez ce package dans la liste, puis cliquez sur le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

1. Installez le **Package NuGet Microsoft.Azure.Functions.Extensions** :

    Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.Azure.Functions.Extensions**, sélectionnez ce package dans la liste, puis sélectionnez le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

1. Installez la version du **package NuGet Microsoft.extensions.ml** **0.15.1**:

    Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.extensions.ml**, sélectionnez ce package dans la liste, puis cliquez sur le bouton **installer** . Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

1. Installez la version du **package NuGet Microsoft. net. Sdk. Functions** **1.0.31**:

    Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet installé, recherchez **Microsoft. net. Sdk. Functions**, sélectionnez ce package dans la liste, sélectionnez **1.0.31** dans la liste déroulante version, puis cliquez sur le bouton **mettre à jour** . Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

## <a name="add-pre-trained-model-to-project"></a>Ajouter un modèle préentraîné au projet

1. Copiez votre modèle prédéfini dans le dossier *MLModels*.
1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre fichier de modèle prédéfini et sélectionnez **Propriétés**. Sous **avancé**, remplacez la valeur de **copier dans le répertoire de sortie** par **copier si plus récent**.

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

1. Créez un répertoire nommé *datamodels* dans votre projet pour enregistrer vos modèles de données : dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Ajouter > nouveau dossier**. Tapez « DataModels » et appuyez sur Entrée.
2. Dans Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *datamodels* , puis sélectionnez **Ajouter > nouvel élément**.
3. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *SentimentData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

    Le fichier *SentimentData.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction using suivante en haut du fichier *SentimentData.cs* :

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    Supprimez la définition de classe existante et ajoutez le code suivant au fichier *SentimentData.cs* :

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. Dans Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *datamodels* , puis sélectionnez **Ajouter > nouvel élément**.
5. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *SentimentPrediction.cs*. Ensuite, sélectionnez le bouton **Ajouter**. Le fichier *SentimentPrediction.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction using suivante en haut du fichier *SentimentPrediction.cs* :

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    Supprimez la définition de classe existante et ajoutez le code suivant au fichier *SentimentPrediction.cs* :

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction` hérite de `SentimentData`, qui fournit l’accès aux données d’origine dans la propriété `SentimentText` ainsi que la sortie générée par le modèle.

## <a name="register-predictionenginepool-service"></a>Inscrire le service PredictionEnginePool

Pour effectuer une prédiction unique, vous devez créer un [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread-safe. En outre, vous devez créer une instance de celle-ci partout où elle est nécessaire dans votre application. À mesure que votre application croît, ce processus peut devenir non gérable. Pour améliorer les performances et la sécurité des threads, utilisez une combinaison d’injection de dépendances et le `PredictionEnginePool` service, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d' [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objets à utiliser dans votre application.

Le lien suivant fournit plus d’informations si vous souhaitez en savoir plus sur l' [injection de dépendances](https://en.wikipedia.org/wiki/Dependency_injection).

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et définissez la valeur du champ **Nom** sur *Startup.cs*. Ensuite, sélectionnez le bouton **Ajouter**.
1. Ajoutez les instructions using suivantes au début de *Startup.cs*:

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. Supprimez le code existant sous les instructions using et ajoutez le code suivant :

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. Définir des variables pour stocker l’environnement dans lequel l’application s’exécute et le chemin d’accès au fichier où se trouve le modèle à l’intérieur de la `Startup` classe

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. En dessous, créez un constructeur pour définir les valeurs des `_environment` variables et `_modelPath` . Lorsque l’application s’exécute localement, l’environnement par défaut est le *développement*.

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. Ensuite, ajoutez une nouvelle méthode appelée `Configure` pour inscrire le `PredictionEnginePool` service sous le constructeur.

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

À un niveau élevé, ce code initialise automatiquement les objets et les services en vue d’une utilisation ultérieure lorsqu’ils sont demandés par l’application au lieu d’avoir à le faire manuellement.

Les modèles machine learning ne sont pas statiques. À mesure que de nouvelles données d’apprentissage deviennent disponibles, le modèle est reformé et redéployé. Une façon d’utiliser la dernière version du modèle dans votre application consiste à redéployer l’application entière. Toutefois, cela entraîne un temps d’arrêt des applications. Le `PredictionEnginePool` service fournit un mécanisme permettant de recharger un modèle mis à jour sans mettre votre application hors service.

Affectez au paramètre la valeur `watchForChanges` `true` , et le `PredictionEnginePool` démarre un [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) qui écoute les notifications de modification du système de fichiers et déclenche des événements lorsqu’une modification est apportée au fichier. Cela invite le `PredictionEnginePool` à recharger automatiquement le modèle.

Le modèle est identifié par le `modelName` paramètre afin que plusieurs modèles par application puissent être rechargés après modification.

> [!TIP]
> Vous pouvez également utiliser la `FromUri` méthode lorsque vous travaillez avec des modèles stockés à distance. Au lieu d’examiner les événements de modification de fichier, `FromUri` interroge l’emplacement distant pour rechercher les modifications. La valeur par défaut de l’intervalle d’interrogation est de 5 minutes. Vous pouvez augmenter ou diminuer l’intervalle d’interrogation en fonction des exigences de votre application. Dans l’exemple de code ci-dessous, le `PredictionEnginePool` interroge le modèle stocké à l’URI spécifié toutes les minutes.
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

Quand la méthode `Run` s’exécute, les données entrantes issues de la requête HTTP sont désérialisées et utilisées comme entrée pour le `PredictionEnginePool`. La `Predict` méthode est ensuite appelée pour effectuer des prédictions à l’aide du `SentimentAnalysisModel` inscrit dans la `Startup` classe et retourne les résultats à l’utilisateur en cas de réussite.

## <a name="test-locally"></a>Tester les topologies localement

Maintenant que tout est configuré, il est temps de tester l’application :

1. Exécution de l'application
1. Ouvrez PowerShell et entrez le code dans l’invite, où PORT est le port sur lequel s’exécute votre application, en règle générale 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    En cas de réussite, la sortie devrait se présenter ainsi :

    ```powershell
    Negative
    ```

Félicitations ! Vous avez réussi à alimenter votre modèle de façon à effectuer des prédictions sur Internet à l’aide d’une fonction Azure.

## <a name="next-steps"></a>Étapes suivantes

- [Déployer dans Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
