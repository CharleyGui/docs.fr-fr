---
title: Déployer un modèle dans une API web ASP.NET Core
description: Alimentez un modèle Machine Learning d’analyse des sentiments ML.NET sur Internet avec l’API web ASP.NET Core.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: f588d4681ee277ad15b50d5553473b1c9e84d578
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608762"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>Déployer un modèle dans une API web ASP.NET Core

Découvrez comment alimenter un modèle Machine Learning ML.NET préentraîné sur le web avec une API web ASP.NET Core. L’alimentation d’un modèle sur une API web permet d’effectuer des prédictions par le biais de méthodes HTTP standard.

## <a name="prerequisites"></a>Prérequis

- [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou version ultérieure ou visual studio 2017 version 15,6 ou ultérieure avec la charge de travail « développement multiplateforme .net Core » installée.
- PowerShell.
- un modèle préentraîné : Utilisez le [tutoriel Analyse des sentiments dans ML.NET](../tutorials/sentiment-analysis.md) pour générer votre propre modèle ou téléchargez ce [modèle Machine Learning d’analyse des sentiments préentraîné](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip).

## <a name="create-aspnet-core-web-api-project"></a>Créer un projet d’API web ASP.NET Core

1. Ouvrez Visual Studio 2017. Sélectionnez **Fichier > Nouveau > Projet** dans la barre de menus. Dans la boîte de dialogue Nouveau projet, sélectionnez le nœud **Visual C#**, suivi du nœud **Web**. Ensuite, sélectionnez le modèle de projet **Application web ASP.NET Core**. Dans la zone de texte **Nom**, tapez « SentimentAnalysisWebAPI », puis sélectionnez le bouton **OK**.

1. Dans la fenêtre qui affiche les différents types de projets ASP.NET Core, sélectionnez **API**, puis le bouton **OK**.

1. Créez un répertoire nommé *MLModels* dans votre projet pour enregistrer les fichiers de votre modèle Machine Learning prédéfini :

    Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez Ajouter > Nouveau dossier. Tapez « MLModels » et appuyez sur Entrée.

1. Installez le **package NuGet Microsoft.ML** :

    Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ML**, sélectionnez ce package dans la liste, puis cliquez sur le bouton Installer. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages répertoriés.

1. Installez le **package NuGet Microsoft.Extensions.ML** :

    Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.Extensions.ML**, sélectionnez ce package dans la liste, puis sélectionnez le bouton Installer. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages répertoriés.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Ajouter un modèle au projet d’API web ASP.NET Core

1. Copiez votre modèle prédéfini dans le répertoire *MLModels*.
1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier zip du modèle et sélectionnez Propriétés. Sous Avancé, remplacez la valeur Copier dans le répertoire de sortie par Copier si plus récent.

## <a name="create-data-models"></a>Créer des modèles de données

Vous devez créer des classes pour vos données d’entrée et prévisions. Ajoutez une nouvelle classe à votre projet :

1. Créez un répertoire nommé *DataModels* dans votre projet pour enregistrer vos modèles de données :

    Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez Ajouter > Nouveau dossier. Tapez « DataModels » et appuyez sur **entrée**.

2. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *DataModels*, puis sélectionnez Ajouter > Nouvel élément.
3. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *SentimentData.cs*. Ensuite, sélectionnez le bouton **Ajouter**. Le fichier *SentimentData.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction using suivante en haut du fichier *SentimentData.cs* :

    ```csharp
    using Microsoft.ML.Data;
    ```

    Supprimez la définition de classe existante et ajoutez le code suivant au fichier **SentimentData.cs** :

    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. Dans Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *datamodels* , puis sélectionnez **Ajouter > nouvel élément**.
5. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *SentimentPrediction.cs*. Ensuite, sélectionnez le bouton Ajouter. Le fichier *SentimentPrediction.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction using suivante en haut du fichier *SentimentPrediction.cs* :

    ```csharp
    using Microsoft.ML.Data;
    ```

    Supprimez la définition de classe existante et ajoutez le code suivant au fichier *SentimentPrediction.cs* :

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction` hérite de `SentimentData`. Vous pouvez ainsi mieux voir les données d’origine dans la propriété `SentimentText` ainsi que la sortie générée par le modèle.

## <a name="register-predictionenginepool-for-use-in-the-application"></a>Inscrire PredictionEnginePool pour l’utiliser dans l’application

Pour effectuer une prédiction unique, vous devez créer un [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread-safe. En outre, vous devez créer une instance de celle-ci partout où elle est nécessaire dans votre application. À mesure que votre application croît, ce processus peut devenir non gérable. Pour améliorer les performances et la sécurité des threads, utilisez une combinaison d’injection de dépendances et le `PredictionEnginePool` service, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d' [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objets à utiliser dans votre application.

Le lien suivant fournit plus d’informations si vous souhaitez en savoir plus sur [l’injection de dépendances dans ASP.net Core](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Ouvrez la classe *Startup.cs* et ajoutez l’instruction using suivante en haut du fichier :

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. Ajoutez le code suivant à la méthode *ConfigureServices* :

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

À un niveau élevé, ce code initialise automatiquement les objets et les services en vue d’une utilisation ultérieure lorsqu’ils sont demandés par l’application au lieu d’avoir à le faire manuellement.

Les modèles machine learning ne sont pas statiques. À mesure que de nouvelles données d’apprentissage deviennent disponibles, le modèle est reformé et redéployé. Une façon d’utiliser la dernière version du modèle dans votre application consiste à redéployer l’application entière. Toutefois, cela entraîne un temps d’arrêt des applications. Le `PredictionEnginePool` service fournit un mécanisme permettant de recharger un modèle mis à jour sans mettre votre application hors service.

Affectez au paramètre la valeur `watchForChanges` `true` , et le `PredictionEnginePool` démarre un [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) qui écoute les notifications de modification du système de fichiers et déclenche des événements lorsqu’une modification est apportée au fichier. Cela invite le `PredictionEnginePool` à recharger automatiquement le modèle.

Le modèle est identifié par le `modelName` paramètre afin que plusieurs modèles par application puissent être rechargés après modification.

> [!TIP]
> Vous pouvez également utiliser la `FromUri` méthode lorsque vous travaillez avec des modèles stockés à distance. Au lieu d’examiner les événements de modification de fichier, `FromUri` interroge l’emplacement distant pour rechercher les modifications. La valeur par défaut de l’intervalle d’interrogation est de 5 minutes. Vous pouvez augmenter ou diminuer l’intervalle d’interrogation en fonction des exigences de votre application. Dans l’exemple de code ci-dessous, le `PredictionEnginePool` interroge le modèle stocké à l’URI spécifié toutes les minutes.
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a>Créer un contrôleur de prédictions

Pour traiter les requêtes HTTP entrantes, créez un contrôleur.

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *Contrôleurs*, puis sélectionnez **Ajouter > Contrôleur**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Contrôleur d’API vide** et **Ajouter**.
1. À l’invite, remplacez la valeur du champ **Nom du contrôleur** par *PredictController.cs*. Ensuite, sélectionnez le bouton Ajouter. Le fichier *PredictController.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction using suivante en haut du fichier *PredictController.cs* :

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    Supprimez la définition de classe existante et ajoutez le code suivant au fichier *PredictController.cs* :

    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

Ce code affecte le `PredictionEnginePool` en le passant au constructeur du contrôleur, obtenu par injection de dépendances. Ensuite, la `Predict` méthode du contrôleur `Post` utilise le `PredictionEnginePool` pour effectuer des prédictions à l’aide du `SentimentAnalysisModel` inscrit dans la `Startup` classe et retourner les résultats à l’utilisateur en cas de réussite.

## <a name="test-web-api-locally"></a>Tester l’API web localement

Maintenant que tout est configuré, il est temps de tester l’application.

1. Exécutez l'application.
1. Ouvrez PowerShell et entrez le code suivant, où PORT est le port sur lequel votre application est à l’écoute.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    En cas de réussite, la sortie devrait se présenter ainsi :

    ```powershell
    Negative
    ```

Félicitations ! Vous avez réussi à alimenter votre modèle de façon à effectuer des prédictions sur Internet à l’aide d’une API web ASP.NET Core.

## <a name="next-steps"></a>Étapes suivantes

- [Déployer dans Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
