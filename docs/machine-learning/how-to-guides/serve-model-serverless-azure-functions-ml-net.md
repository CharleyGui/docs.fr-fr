---
title: Déployer un modèle sur Azure Functions
description: Alimentez un modèle Machine Learning d’analyse des sentiments ML.NET à des fins de prédiction sur Internet avec Azure Functions.
ms.date: 06/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 7df7a6f9fcc5a4702171e1aac4b6b67e0c343748
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025980"
---
# <a name="deploy-a-model-to-azure-functions"></a>Déployer un modèle sur Azure Functions

Découvrez comment déployer un modèle Machine Learning ML.NET préentraîné pour effectuer des prédictions sur HTTP par le bais d’un environnement serverless Azure Functions.

> [!NOTE]
> L’extension de service `PredictionEnginePool` est disponible en préversion.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .NET Core » et « Développement Azure » ;
- Package NuGet version 1.0.28+ de Microsoft.NET.Sdk.Functions.
- [Azure Functions Tools](/azure/azure-functions/functions-develop-vs#check-your-tools-version) ;
- PowerShell ;
- un modèle préentraîné : Utilisez le [tutoriel Analyse des sentiments dans ML.NET](../tutorials/sentiment-analysis.md) pour générer votre propre modèle ou téléchargez ce [modèle Machine Learning d’analyse des sentiments préentraîné](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip).

## <a name="create-azure-functions-project"></a>Créer un projet Azure Functions

1. Ouvrez Visual Studio 2017. Sélectionnez **Fichier** > **Nouveau** > **Projet** dans la barre de menus. Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual C#** , suivi du nœud **Cloud**. Ensuite, sélectionnez le modèle de projet **Azure Functions**. Dans la zone de texte **Nom**, tapez « SentimentAnalysisFunctionsApp », puis sélectionnez le bouton **OK**.
1. Dans la boîte de dialogue **Nouveau projet**, ouvrez la liste déroulante au-dessus des options du projet et sélectionnez **Azure Functions v2 (.NET Core)** . Ensuite, sélectionnez le projet **Déclencheur HTTP**, puis sélectionnez le bouton **OK**.
1. Créez un répertoire nommé *MLModels* dans votre projet pour enregistrer votre modèle :

    Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Ajouter** > **Nouveau dossier**. Tapez « MLModels » et appuyez sur Entrée.

1. Installez le **package NuGet Microsoft.ML** :

    Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ML**, sélectionnez ce package dans la liste, puis cliquez sur le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

1. Installez le **Package NuGet Microsoft.Azure.Functions.Extensions** :

    Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.Azure.Functions.Extensions**, sélectionnez ce package dans la liste, puis sélectionnez le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

1. Installez le **package NuGet Microsoft.Extensions.ML** :

    Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.Extensions.ML**, sélectionnez ce package dans la liste, puis sélectionnez le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

1. Mettez à jour le **Package NuGet Microsoft.NET.Sdk.Functions** vers la version 1.0.28 :

    Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Installé, recherchez **Microsoft.NET.Sdk.Functions**, sélectionnez ce package dans la liste, sélectionnez 1.0.28 ou une version ultérieure dans la liste déroulante Version et sélectionnez le bouton **Mettre à jour**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

## <a name="add-pre-trained-model-to-project"></a>Ajouter un modèle préentraîné au projet

1. Copiez votre modèle prédéfini dans le dossier *MLModels*.
1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre fichier de modèle prédéfini et sélectionnez **Propriétés**. Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Créer une fonction Azure d’analyse des sentiments

Créez une classe pour prédire le sentiment. Ajoutez une nouvelle classe à votre projet :

1. Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Fonction Azure** et remplacez la valeur du champ **Nom** par *AnalyzeSentiment.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

1. Dans la boîte de dialogue **Nouvelle fonction Azure**, sélectionnez **Déclencheur HTTP**. Ensuite, sélectionnez le bouton **OK**.

    Le fichier *AnalyzeSentiment.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction suivante `using` en haut du fichier *AnalyzeSentiment.cs* :

    ```csharp
    using System;
    using System.IO;
    using System.Threading.Tasks;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using Microsoft.AspNetCore.Http;
    using Microsoft.Extensions.Logging;
    using Newtonsoft.Json;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    Par défaut, la classe `AnalyzeSentiment` est `static`. Veillez à supprimer le mot clé `static` de la définition de classe.

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a>Créer des modèles de données

Vous devez créer des classes pour vos données d’entrée et prévisions. Ajoutez une nouvelle classe à votre projet :

1. Créez un répertoire nommé *DataModels* dans votre projet pour enregistrer vos modèles de données : Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **Ajouter > Nouveau dossier**. Tapez « DataModels » et appuyez sur Entrée.
2. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *DataModels*, puis sélectionnez **Ajouter > Nouvel élément**.
3. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *SentimentData.cs*. Ensuite, sélectionnez le bouton **Ajouter**. 

    Le fichier *SentimentData.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction using suivante en haut du fichier *SentimentData.cs* :

    ```csharp
    using Microsoft.ML.Data;
    ```

    Supprimez la définition de classe existante et ajoutez le code suivant au fichier *SentimentData.cs* :
    
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
5. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *SentimentPrediction.cs*. Ensuite, sélectionnez le bouton **Ajouter**. Le fichier *SentimentPrediction.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction using suivante en haut du fichier *SentimentPrediction.cs* :

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

    `SentimentPrediction` hérite de `SentimentData`, qui fournit l’accès aux données d’origine dans la propriété `SentimentText` ainsi que la sortie générée par le modèle.

## <a name="register-predictionenginepool-service"></a>Inscrire le service PredictionEnginePool

Pour établir une prédiction unique, utilisez [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). Pour pouvoir utiliser la classe [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dans votre application, vous devez la créer quand vous en avez besoin. Dans ce cas, il est recommandé d’utiliser l’injection de dépendances.

Pour plus d’informations, voir [Injection de dépendances](https://en.wikipedia.org/wiki/Dependency_injection).

1. Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et définissez la valeur du champ **Nom** sur *Startup.cs*. Ensuite, sélectionnez le bouton **Ajouter**. 

    Le fichier *Startup.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction using suivante en haut du fichier *Startup.cs* :

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    Supprimez le code sous les instructions using et ajoutez le code suivant au fichier *Startup.cs* :

    ```csharp
    [assembly: WebJobsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        class Startup : IWebJobsStartup
        {
            public void Configure(IWebJobsBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

À haut niveau, ce code initialise automatiquement les objets et les services à la demande de l’application, ce qui évite d’avoir à le faire manuellement.

> [!WARNING]
> [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe. Pour améliorer les performances et la cohérence de thread, utilisez le service `PredictionEnginePool`, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d’objets `PredictionEngine` à utiliser avec l’application. 

## <a name="load-the-model-into-the-function"></a>Charger le modèle dans la fonction

Insérez le code suivant à l’intérieur de la classe *AnalyzeSentiment* :

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

Ce code affecte le `PredictionEnginePool` en le passant au constructeur de la fonction, obtenu par injection de dépendances.

## <a name="use-the-model-to-make-predictions"></a>Utiliser le modèle pour élaborer des prédictions

Remplacez l’implémentation existante de la méthode *Run* dans la classe *AnalyzeSentiment* par le code suivant :

```csharp
[FunctionName("AnalyzeSentiment")]
public async Task<IActionResult> Run(
[HttpTrigger(AuthorizationLevel.Function, "post", Route = null)] HttpRequest req,
ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    //Parse HTTP Request Body
    string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
    SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);
    
    //Make Prediction
    SentimentPrediction prediction = _predictionEnginePool.Predict(data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

Quand la méthode `Run` s’exécute, les données entrantes issues de la requête HTTP sont désérialisées et utilisées comme entrée pour le `PredictionEnginePool`. La méthode `Predict` est ensuite appelée pour générer une prédiction et retourner le résultat à l’utilisateur. 

## <a name="test-locally"></a>Tester localement

Maintenant que tout est configuré, il est temps de tester l’application :

1. Exécuter l'application
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

- [Déployer sur Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
