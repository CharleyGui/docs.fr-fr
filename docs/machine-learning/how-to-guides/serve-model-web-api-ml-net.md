---
title: Déployer un modèle dans une API web ASP.NET Core
description: Alimentez un modèle Machine Learning d’analyse des sentiments ML.NET sur Internet avec l’API web ASP.NET Core.
ms.date: 08/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 8d21ae5ae3aa4701ddd7d042d5069351c22864bb
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182552"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>Déployer un modèle dans une API web ASP.NET Core

Découvrez comment alimenter un modèle Machine Learning ML.NET préentraîné sur le web avec une API web ASP.NET Core. L’alimentation d’un modèle sur une API web permet d’effectuer des prédictions par le biais de méthodes HTTP standard.

> [!NOTE]
> L’extension de service `PredictionEnginePool` est disponible en préversion.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .Net Core » installée.
- PowerShell ;
- un modèle préentraîné : Utilisez le [tutoriel Analyse des sentiments dans ML.NET](../tutorials/sentiment-analysis.md) pour générer votre propre modèle ou téléchargez ce [modèle Machine Learning d’analyse des sentiments préentraîné](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip).

## <a name="create-aspnet-core-web-api-project"></a>Créer un projet d’API web ASP.NET Core

1. Ouvrez Visual Studio 2017. Sélectionnez **Fichier > Nouveau > Projet** dans la barre de menus. Dans la boîte de dialogue Nouveau projet, sélectionnez le nœud **Visual C#** , suivi du nœud **Web**. Ensuite, sélectionnez le modèle de projet **Application web ASP.NET Core**. Dans la zone de texte **Nom**, tapez « SentimentAnalysisWebAPI », puis sélectionnez le bouton **OK**.

1. Dans la fenêtre qui affiche les différents types de projets ASP.NET Core, sélectionnez **API**, puis le bouton **OK**.

1. Créez un répertoire nommé *MLModels* dans votre projet pour enregistrer les fichiers de votre modèle Machine Learning prédéfini :

    Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez Ajouter > Nouveau dossier. Tapez « MLModels » et appuyez sur Entrée.

1. Installez le **package NuGet Microsoft.ML** :

    Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ML**, sélectionnez ce package dans la liste, puis sélectionnez le bouton Installer. Sélectionnez le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages de la liste.

1. Installez le **package NuGet Microsoft.Extensions.ML** :

    Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.Extensions.ML**, sélectionnez ce package dans la liste, puis sélectionnez le bouton Installer. Sélectionnez le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages de la liste.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Ajouter un modèle au projet d’API web ASP.NET Core

1. Copiez votre modèle prédéfini dans le répertoire *MLModels*.
1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier zip du modèle et sélectionnez Propriétés. Sous Avancé, remplacez la valeur Copier dans le répertoire de sortie par Copier si plus récent.

## <a name="create-data-models"></a>Créer des modèles de données

Vous devez créer des classes pour vos données d’entrée et prévisions. Ajoutez une nouvelle classe à votre projet :

1. Créez un répertoire nommé *DataModels* dans votre projet pour enregistrer vos modèles de données :

    Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez Ajouter > Nouveau dossier. Tapez « DataModels » et appuyez sur **Entrée**.

2. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *DataModels*, puis sélectionnez Ajouter > Nouvel élément.
3. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *SentimentData.cs*. Ensuite, sélectionnez le bouton **Ajouter**. Le fichier *SentimentData.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction using suivante en haut du fichier *SentimentData.cs* :

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    Supprimez la définition de classe existante et ajoutez le code suivant au fichier **SentimentData.cs** :
    
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

4. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *DataModels*, puis sélectionnez **Ajouter > Nouvel élément**.
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

Pour établir une prédiction unique, utilisez [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). Pour pouvoir utiliser la classe [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dans votre application, vous devez la créer quand vous en avez besoin. Dans ce cas, il est recommandé d’utiliser l’injection de dépendances.

Pour plus d’informations, consultez [Injection de dépendances dans ASP.NET Core](/aspnet/core/fundamentals/dependency-injection).

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
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

À haut niveau, ce code initialise automatiquement les objets et les services à la demande de l’application, ce qui évite d’avoir à le faire manuellement.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe. Pour améliorer les performances et la cohérence de thread, utilisez le service `PredictionEnginePool`, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d’objets `PredictionEngine` à utiliser avec l’application. Lisez le billet de blog suivant pour en savoir plus sur [la création et l’utilisation de pools d’objets `PredictionEngine` dans ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).  

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

            SentimentPrediction prediction = _predictionEnginePool.Predict(input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

Ce code affecte le `PredictionEnginePool` en le passant au constructeur du contrôleur, obtenu par injection de dépendances. Ensuite, la méthode `Post` du contrôleur `Predict` utilise le `PredictionEnginePool` pour établir des prédictions et retourner les résultats à l’utilisateur en cas de réussite.

## <a name="test-web-api-locally"></a>Tester l’API web localement

Maintenant que tout est configuré, il est temps de tester l’application.

1. Exécutez l'application.
1. Ouvrez PowerShell et entrez le code suivant, où PORT est le port d’écoute de votre application.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    En cas de réussite, la sortie devrait se présenter ainsi :
    
    ```powershell
    Negative
    ```

Félicitations ! Vous avez réussi à alimenter votre modèle de façon à effectuer des prédictions sur Internet à l’aide d’une API web ASP.NET Core.

## <a name="next-steps"></a>Étapes suivantes

- [Déployer sur Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
