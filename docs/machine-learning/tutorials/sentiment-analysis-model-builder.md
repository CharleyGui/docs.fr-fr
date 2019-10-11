---
title: 'Tutoriel : Analyser le sentiment-classification binaire'
description: Ce didacticiel vous montre comment créer une application Razor Pages qui classe les sentiments à partir de commentaires de site Web et prend les mesures appropriées. Le classifieur de sentiment binaire utilise le générateur de modèles dans Visual Studio.
ms.date: 10/08/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4a97fb70caafd7b0003830259ddbb0ec72a2ca8a
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180269"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>Tutoriel : Analyser les sentiments des commentaires de site Web dans une application Web à l’aide du générateur de modèles ML.NET

Découvrez comment analyser les sentiments de commentaires en temps réel dans une application Web.

Ce didacticiel vous montre comment créer une application ASP.NET Core Razor Pages qui classe les sentiments à partir de commentaires de site Web en temps réel.

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
>
> - Créer une application de Razor Pages ASP.NET Core
> - Préparer et comprendre les données
> - Choisir un scénario
> - Charger les données
> - Effectuer l’apprentissage du modèle
> - Évaluer le modèle
> - Utiliser le modèle pour les prévisions

> [!NOTE]
> Model Builder est actuellement en préversion.

Vous pouvez trouver le code source de ce didacticiel dans le référentiel [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples) .

## <a name="pre-requisites"></a>Conditions préalables

Pour obtenir la liste des prérequis et les instructions d’installation, consultez le [Guide d’installation de Model Builder](../how-to-guides/install-model-builder.md).

## <a name="create-a-razor-pages-application"></a>Créer une application Razor Pages

1. Créer une **application de Razor Pages ASP.net Core**.

    1. Ouvrez Visual Studio et sélectionnez **fichier > nouveau > projet** dans la barre de menus.
    1. Dans la boîte de dialogue Nouveau projet, sélectionnez le nœud **Visual C#** , suivi du nœud **Web**.
    1. Ensuite, sélectionnez le modèle de projet **Application web ASP.NET Core**.
    1. Dans la zone de texte **nom** , tapez « SentimentRazor ».
    1. La case à cocher **créer un répertoire pour la solution** doit être activée par défaut. Si ce n’est pas le cas, vérifiez-le.
    1. Sélectionnez le bouton **OK**.
    1. Choisissez **application Web** dans la fenêtre qui affiche les différents types de ASP.net Core projets, puis cliquez sur le bouton **OK** .

## <a name="prepare-and-understand-the-data"></a>Préparer et comprendre les données

Téléchargez le [jeu de données Detox Wikipédia](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv). Lorsque la page Web s’ouvre, cliquez avec le bouton droit sur la page, sélectionnez **Enregistrer sous** , puis enregistrez le fichier sur votre ordinateur.

Chaque ligne du jeu de données *Wikipédia-Detox-250-Line-Data. TSV* représente une révision différente laissée par un utilisateur sur Wikipédia. La première colonne représente le sentiment du texte (0 est non toxique, 1 est toxique) et la deuxième colonne représente le commentaire laissé par l’utilisateur. Les colonnes sont séparées par des tabulations. Les données ressemblent à ce qui suit :

| Sentiment | SentimentText |
| :---: | :---: |
1 | = = IMPROPRE = = dude, vous êtes très impropre à charger cette image Carl, ou autre.
1 | = = OK ! = = IM VA SE RENDRE COMPTE DU WIKI SAUVAGE, !!!
0 | J’espère que cela vous aidera.

## <a name="choose-a-scenario"></a>Choisir un scénario

![Assistant Générateur de modèles dans Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Pour entraîner votre modèle, vous devez sélectionner dans la liste des scénarios Machine Learning disponibles fournis par Model Builder.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet *SentimentRazor* , puis sélectionnez **Ajouter** > **machine learning**.
1. Pour cet exemple, le scénario est l’analyse de sentiments. Dans l’étape de *scénario* de l’outil générateur de modèles, sélectionnez le scénario **analyse des sentiments** .

## <a name="load-the-data"></a>Charger les données

Le générateur de modèles accepte les données de deux sources, une base de données SQL Server ou un fichier local au format `csv` ou `tsv`.

1. Dans l’étape des données de l’outil Model Builder, sélectionnez **Fichier** dans la liste déroulante des sources de données.
1. Sélectionnez le bouton en regard de la zone de texte **Sélectionner un fichier** et utilisez l’Explorateur de fichiers pour parcourir et sélectionner le fichier *Wikipédia-Detox-250-Line-Data. TSV* .
1. Choisissez **sentiments** dans la liste déroulante **colonne à prédire (étiquette)** .
1. Laissez les valeurs par défaut pour la liste déroulante **colonnes d’entrée (fonctionnalités)** .
1. Sélectionnez le lien **former** pour passer à l’étape suivante dans l’outil générateur de modèles.

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

La tâche de Machine Learning utilisée pour l’apprentissage du modèle d’analyse des sentiments dans ce didacticiel est la classification binaire. Pendant le processus d’apprentissage du modèle, le générateur de modèles forme des modèles distincts à l’aide de différents algorithmes et paramètres de classification binaire pour trouver le modèle le plus performant pour votre jeu de données.

Le temps nécessaire pour l’entraînement du modèle est proportionnel à la quantité de données. Le générateur de modèles sélectionne automatiquement une valeur par défaut pour le **temps de formation (en secondes)** en fonction de la taille de votre source de données.

1. Bien que le générateur de modèles définisse la valeur de **temps à former (secondes)** à 10 secondes, augmentez-le à 30 secondes. La formation sur une période plus longue permet au générateur de modèles d’explorer un plus grand nombre d’algorithmes et une combinaison de paramètres dans la recherche du meilleur modèle.
1. Sélectionnez **Commencer l’entraînement**.

    Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.

    - Le champ État affiche l’état d’achèvement du processus d’entraînement.
    - Le champ Meilleure précision affiche la précision du modèle le plus performant trouvé jusqu’à présent par Model Builder. Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test.
    - Le champ Meilleur algorithme affiche le nom de l’algorithme le plus performant trouvé jusqu’à présent par Model Builder.
    - Le champ Dernier algorithme affiche le nom de l’algorithme le plus récemment utilisé par Model Builder pour entraîner le modèle.

1. Une fois l’apprentissage terminé, sélectionnez le lien **évaluer** pour passer à l’étape suivante.

## <a name="evaluate-the-model"></a>Évaluer le modèle

Le résultat de l’étape d’entraînement sera le modèle qui a eu les meilleures performances. Dans l’étape évaluer de l’outil générateur de modèles, la section sortie contient l’algorithme utilisé par le modèle le mieux adapté à l’entrée de **modèle la plus** performante, ainsi que les métriques dont la **précision de modèle**est optimale. Vous voyez aussi un tableau récapitulatif contenant les cinq meilleurs modèles et leurs métriques.

Si vous n’êtes pas satisfait de vos métriques de précision, un moyen facile pour améliorer la précision du modèle consiste à augmenter la quantité de temps pour entraîner le modèle ou à utiliser plus de données. Dans le cas contraire, sélectionnez le lien de **code** pour passer à l’étape finale de l’outil générateur de modèles.

## <a name="add-the-code-to-make-predictions"></a>Ajouter le code pour effectuer des prédictions

Deux projets sont créés à la suite du processus d’entraînement.

### <a name="reference-the-trained-model"></a>Référencer le modèle formé

1. Dans l’étape de *code* de l’outil générateur de modèles, sélectionnez **Ajouter des projets** pour ajouter les projets générés automatiquement à la solution.

    Les projets suivants doivent apparaître dans le **Explorateur de solutions**:

    - *SentimentRazorML. ConsoleApp*: Application console .NET Core qui contient l’apprentissage du modèle et le code de prédiction.
    - *SentimentRazorML. Model*: Bibliothèque de classes .NET Standard contenant les modèles de données qui définissent le schéma des données de modèle d’entrée et de sortie ainsi que la version enregistrée du modèle le plus performant au cours de l’apprentissage.

    Pour ce didacticiel, seul le projet *SentimentRazorML. Model* est utilisé, car les prédictions sont effectuées dans l’application Web *SentimentRazor* plutôt que dans la console. Bien que *SentimentRazorML. ConsoleApp* ne soit pas utilisé pour le calcul de score, il peut être utilisé pour reformer le modèle à l’aide de nouvelles données ultérieurement. Toutefois, la reformation n’entre pas dans le cadre de ce didacticiel.

### <a name="configure-the-predictionengine-pool"></a>Configurer le pool PredictionEngine

Pour effectuer une prédiction unique, vous devez créer un [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe. En outre, vous devez créer une instance de celle-ci partout où elle est nécessaire dans votre application. À mesure que votre application croît, ce processus peut devenir non gérable. Pour améliorer les performances et la sécurité des threads, utilisez une combinaison d’injection de dépendances et le service `PredictionEnginePool`, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d’objets [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pour une utilisation dans votre application.

1. Installez le package NuGet *Microsoft.extensions.ml* :

    1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Gérer les packages NuGet**.
    1. Choisissez « nuget.org » comme source du package.
    1. Sélectionnez l’onglet **Parcourir** et recherchez **Microsoft.extensions.ml**.
    1. Sélectionnez le package dans la liste, puis cliquez sur le bouton **installer** .
    1. Sélectionnez le bouton **OK** dans la boîte de dialogue **aperçu des modifications**
    1. Sélectionnez le bouton **J’accepte** dans la boîte de dialogue acceptation de la **licence** si vous acceptez les termes du contrat de licence pour les packages listés.

1. Ouvrez le fichier *Startup.cs* dans le projet *SentimentRazor* .
1. Ajoutez les instructions using suivantes pour référencer le package NuGet *Microsoft.extensions.ml* et le projet *SentimentRazorML. Model* :

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. Créez une variable globale pour stocker l’emplacement du fichier de modèle formé.

    ```csharp
    private readonly string _modelPath;
    ```

1. Le fichier de modèle est stocké dans le répertoire de build en même temps que les fichiers d’assembly de votre application. Pour faciliter l’accès à, créez une méthode d’assistance appelée `GetAbsolutePath` après la méthode `Configure`

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }    
    ```

1. Utilisez la méthode `GetAbsolutePath` dans le constructeur de classe `Startup` pour définir le `_modelPath`.

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. Configurez la `PredictionEnginePool` pour votre application dans la méthode `ConfigureServices` :

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a>Créer un gestionnaire d’analyse de sentiments

Les prédictions sont effectuées à l’intérieur de la page principale de l’application. Par conséquent, une méthode qui prend l’entrée utilisateur et utilise le `PredictionEnginePool` pour retourner une prédiction doit être ajoutée.

1. Ouvrez le fichier *index.cshtml.cs* situé dans le répertoire *pages* et ajoutez les instructions using suivantes :

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    Pour utiliser le `PredictionEnginePool` configuré dans la classe `Startup`, vous devez l’injecter dans le constructeur du modèle où vous souhaitez l’utiliser.

1. Ajoutez une variable pour référencer le `PredictionEnginePool` à l’intérieur de la classe `IndexModel`.

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. Créez un constructeur dans la classe `IndexModel` et injectez le service `PredictionEnginePool` dans celui-ci.

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }    
    ```

1. Créez un gestionnaire de méthode qui utilise le `PredictionEnginePool` pour faire des prédictions à partir de l’entrée utilisateur reçue de la page Web.

    1. Sous la méthode `OnGet`, créez une nouvelle méthode appelée `OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. À l’intérieur de la méthode `OnGetAnalyzeSentiment`, retournez un sentiment *neutre* si l’entrée de l’utilisateur est vide ou null.

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. En fonction d’une entrée valide, créez une nouvelle instance de `ModelInput`.

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. Utilisez la `PredictionEnginePool` pour prédire le sentiment.

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. Convertissez la valeur prédites `bool` en toxique ou non toxique avec le code suivant.

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. Enfin, retournez le sentiment à la page Web.

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a>Configurer la page Web

Les résultats retournés par la `OnGetAnalyzeSentiment` seront affichés dynamiquement sur la page Web de `Index`.

1. Ouvrez le fichier *index. cshtml* dans le répertoire *pages* et remplacez son contenu par le code suivant :

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. Ensuite, ajoutez le code de style CSS à la fin de la page *site. CSS* dans le répertoire *wwwroot\css* :

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. Après cela, ajoutez du code pour envoyer des entrées de la page Web au gestionnaire `OnGetAnalyzeSentiment`.

    1. Dans le fichier *site. js* situé dans le répertoire *wwwroot\js* , créez une fonction appelée `getSentiment` pour obtenir une requête HTTP avec l’entrée utilisateur du gestionnaire `OnGetAnalyzeSentiment`.

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. En dessous, ajoutez une autre fonction appelée `updateMarker` pour mettre à jour dynamiquement la position du marqueur sur la page Web à mesure que le sentiment est prédit.

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. Créez une fonction de gestionnaire d’événements appelée `updateSentiment` pour récupérer l’entrée de l’utilisateur, envoyez-la à la fonction `OnGetAnalyzeSentiment` à l’aide de la fonction `getSentiment` et mettez à jour le marqueur avec la fonction `updateMarker`.

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. Enfin, enregistrez le gestionnaire d’événements et liez-le à l’élément `textarea` avec l’attribut `id=Message`.

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>Exécuter l'application

Maintenant que votre application est configurée, exécutez l’application qui doit être lancée dans votre navigateur.

Lorsque l’application démarre, entrez le *Générateur de modèles est cool !* dans la zone de texte. Le sentiment prédit affiché ne doit *pas être toxique*.

![Fenêtre en cours d’exécution avec la fenêtre de sentiment prédite](./media/sentiment-analysis-model-builder/web-app.png)

Si vous devez référencer les projets générés par le générateur de modèles ultérieurement dans une autre solution, vous pouvez les Rechercher dans le répertoire `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Créer une application de Razor Pages ASP.NET Core
> - Préparer et comprendre les données
> - Choisir un scénario
> - Charger les données
> - Effectuer l’apprentissage du modèle
> - Évaluer le modèle
> - Utiliser le modèle pour les prévisions

### <a name="additional-resources"></a>Ressources supplémentaires

Pour en savoir plus sur les rubriques mentionnées dans ce tutoriel, consultez les ressources suivantes :

- [Scénarios du Générateur de modèles](../automate-training-with-model-builder.md#scenarios)
- [Classification binaire](../resources/glossary.md#binary-classification)
- [Métriques du modèle de classification binaire](../resources/metrics.md#metrics-for-binary-classification)
