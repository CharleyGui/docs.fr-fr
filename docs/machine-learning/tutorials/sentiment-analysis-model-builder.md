---
title: 'Tutorial: Analyser le sentiment - classification binaire'
description: Ce tutoriel vous montre comment créer une application Razor Pages qui classe le sentiment à partir de commentaires sur le site Et prend les mesures appropriées. Le classificateur de sentiment binaire utilise Model Builder dans Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 3419afb36d73599b8fdb0417a8c0cc4057f60089
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187634"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>Tutorial: Analyser le sentiment des commentaires du site Web dans une application web en utilisant ML.NET Model Builder

Apprenez à analyser le sentiment à partir de commentaires en temps réel à l’intérieur d’une application web.

Ce tutoriel vous montre comment créer une application ASP.NET Core Razor Pages qui classe le sentiment des commentaires du site En temps réel.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> - Créez une application ASP.NET Core Razor Pages
> - Préparer et comprendre les données
> - Choisir un scénario
> - Chargement des données
> - Effectuer l’apprentissage du modèle
> - Évaluer le modèle
> - Utiliser le modèle pour les prévisions

> [!NOTE]
> Model Builder est actuellement en préversion.

Vous pouvez trouver le code source pour ce tutoriel au référentiel [dotnet/machinelearning-échantillons.](https://github.com/dotnet/machinelearning-samples)

## <a name="pre-requisites"></a>Conditions préalables

Pour obtenir la liste des prérequis et les instructions d’installation, consultez le [Guide d’installation de Model Builder](../how-to-guides/install-model-builder.md).

## <a name="create-a-razor-pages-application"></a>Créer une application Razor Pages

1. Créez une **application ASP.NET Core Razor Pages**.

    1. Ouvrez Visual Studio et sélectionnez **File > New > Project** à partir de la barre de menu.
    1. Dans la boîte de dialogue Nouveau projet, sélectionnez le nœud **Visual C#**, suivi du nœud **Web**.
    1. Ensuite, sélectionnez le modèle de projet **Application web ASP.NET Core**.
    1. Dans la boîte à texte **Name,** tapez "SentimentRazor".
    1. Assurez-vous que **la solution et le projet Place dans le même répertoire** ne sont pas **contrôlés** (VS 2019), ou **que l’annuaire Créer pour la solution** soit **vérifié** (VS 2017).
    1. Sélectionnez le bouton **OK.**
    1. Choisissez **l’application Web** dans la fenêtre qui affiche les différents types de projets de base ASP.NET, puis sélectionnez le bouton **OK.**

## <a name="prepare-and-understand-the-data"></a>Préparer et comprendre les données

Télécharger [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv). Lorsque la page Web s’ouvre, cliquez à droite sur la page, sélectionnez **Save As** et enregistrez le fichier n’importe où sur votre ordinateur.

Chaque ligne dans le jeu de données *wikipedia-detox-250-line-data.tsv* représente un examen différent laissé par un utilisateur sur Wikipédia. La première colonne représente le sentiment du texte (0 est non toxique, 1 est toxique), et la deuxième colonne représente le commentaire laissé par l’utilisateur. Les colonnes sont séparées par des onglets. Les données ressemblent à ce qui suit :

| Sentiments | SentimentText |
| :---: | :---: |
1 | Dude de 'RUDE', vous êtes grossier télécharger cette photo de carl en arrière, ou bien.
1 | OK ! IM VA VANDALISER LES SAUVAGES WIKI ALORS!!!
0 | J’espère que ça aidera.

## <a name="choose-a-scenario"></a>Choisir un scénario

![Assistant de constructeur de modèle dans visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Pour entraîner votre modèle, vous devez sélectionner dans la liste des scénarios Machine Learning disponibles fournis par Model Builder.

1. Dans **Solution Explorer**, cliquez à droite sur le projet *SentimentRazor,* et sélectionnez **Add** > Machine**Learning**.
1. Pour cet échantillon, le scénario est l’analyse du sentiment. Dans l’étape du *scénario* de l’outil Model Builder, sélectionnez le scénario **d’analyse de sentiment.**

## <a name="load-the-data"></a>Chargement des données

Model Builder accepte les données de deux sources, une `csv` base `tsv` de données SQL Server ou un fichier local dans ou en format.

1. Dans l’étape des données de l’outil Model Builder, sélectionnez **Fichier** dans la liste déroulante des sources de données.
1. Sélectionnez le bouton à côté de la boîte de texte **De fichier Sélectionnez** et utilisez File Explorer pour parcourir et sélectionner le fichier *wikipedia-detox-250-line-data.tsv.*
1. Choisissez **Sentiment** dans la **colonne pour prédire (label)** dropdown.
1. Laissez les valeurs par défaut pour le dropdown **des colonnes d’entrée (Caractéristiques).**
1. Sélectionnez le lien **Train** pour passer à l’étape suivante de l’outil Model Builder.

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

La tâche d’apprentissage automatique utilisée pour former le modèle d’analyse de sentiment dans ce tutoriel est la classification binaire. Pendant le processus de formation du modèle, Model Builder forme des modèles distincts à l’aide de différents algorithmes et paramètres de classification binaire pour trouver le modèle le plus performant pour votre jeu de données.

Le temps nécessaire pour l’entraînement du modèle est proportionnel à la quantité de données. Model Builder sélectionne automatiquement une valeur par défaut pour **le temps de train (secondes)** en fonction de la taille de votre source de données.

1. Bien que Model Builder fixe la valeur du **temps de train (secondes)** à 10 secondes, l’augmenter à 30 secondes. La formation pour une plus longue période de temps permet à Model Builder d’explorer un plus grand nombre d’algorithmes et de combinaison de paramètres à la recherche du meilleur modèle.
1. Sélectionnez **Commencer l’entraînement**.

    Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.

    - Le champ État affiche l’état d’achèvement du processus d’entraînement.
    - Le champ Meilleure précision affiche la précision du modèle le plus performant trouvé jusqu’à présent par Model Builder. Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test.
    - Le champ Meilleur algorithme affiche le nom de l’algorithme le plus performant trouvé jusqu’à présent par Model Builder.
    - Le champ Dernier algorithme affiche le nom de l’algorithme le plus récemment utilisé par Model Builder pour entraîner le modèle.

1. Une fois la formation terminée, sélectionnez le lien **d’évaluation** pour passer à l’étape suivante.

## <a name="evaluate-the-model"></a>Évaluer le modèle

Le résultat de l’étape d’entraînement sera le modèle qui a eu les meilleures performances. Dans l’étape d’évaluation de l’outil Model Builder, la section de sortie, contiendra l’algorithme utilisé par le modèle le plus performant dans **l’entrée du meilleur modèle** avec des mesures dans **la meilleure précision du modèle**. Vous voyez aussi un tableau récapitulatif contenant les cinq meilleurs modèles et leurs métriques.

Si vous n’êtes pas satisfait de vos métriques de précision, un moyen facile pour améliorer la précision du modèle consiste à augmenter la quantité de temps pour entraîner le modèle ou à utiliser plus de données. Dans le cas contraire, sélectionnez le lien **de code** pour passer à l’étape finale de l’outil Model Builder.

## <a name="add-the-code-to-make-predictions"></a>Ajouter le code pour effectuer des prédictions

Deux projets sont créés à la suite du processus d’entraînement.

### <a name="reference-the-trained-model"></a>Référence au modèle formé

1. Dans l’étape *de code* de l’outil Model Builder, sélectionnez Ajouter **des projets** pour ajouter les projets autogénérés à la solution.

    Les projets suivants devraient apparaître dans la **Solution Explorer**:

    - *SentimentRazorML.ConsoleApp*: Une application .NET Core Console qui contient le modèle de formation et de code de prédiction.
    - *SentimentRazorML.Model*: Une bibliothèque de classe standard .NET contenant les modèles de données qui définissent le schéma des données des modèles d’entrée et de sortie ainsi que la version enregistrée du modèle le plus performant pendant la formation.

    Pour ce tutoriel, seul le projet *SentimentRazorML.Model* est utilisé parce que les prédictions seront faites dans *l’application Web SentimentRazor* plutôt que dans la console. Bien que le *SentimentRazorML.ConsoleApp* ne sera pas utilisé pour la notation, il peut être utilisé pour recycler le modèle à l’aide de nouvelles données à une date ultérieure. Le recyclage est en dehors de la portée de ce tutoriel si.

### <a name="configure-the-predictionengine-pool"></a>Configurer la piscine PredictionEngine

Pour faire une seule prédiction, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)vous devez créer un . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas sans fil. En outre, vous devez créer une instance de celui-ci partout où il est nécessaire dans votre application. Au fur et à mesure que votre application se développe, ce processus peut devenir ingérable. Pour améliorer les performances et la sécurité des `PredictionEnginePool` fils, utilisez [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) une combinaison d’injection de dépendance et le service, qui crée un des objets à utiliser tout au long de votre application.

1. Installer le *paquet nuGet Microsoft.Extensions.ML* :

    1. Dans **Solution Explorer**, cliquez à droite sur le projet et sélectionnez Manage **NuGet Packages**.
    1. Choisissez «nuget.org» comme source de paquet.
    1. Sélectionnez l’onglet **Parcourir** et recherchez **Microsoft.Extensions.ML**.
    1. Sélectionnez le paquet dans la liste et sélectionnez le bouton **Installer.**
    1. Sélectionnez le bouton **OK** sur le dialogue **de preview Changes**
    1. Sélectionnez le bouton **I Accept** sur le dialogue **d’acceptation de licence** si vous êtes d’accord avec les conditions de licence pour les paquets énumérés.

1. Ouvrez le fichier *Startup.cs* dans le projet *SentimentRazor.*
1. Ajoutez les instructions suivantes à l’aide des *instructions pour référencer* le Microsoft.Extensions.ML paquet NuGet et le projet *SentimentRazorML.Model* :

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. Créez une variable globale pour stocker l’emplacement du fichier modèle formé.

    ```csharp
    private readonly string _modelPath;
    ```

1. Le fichier modèle est stocké dans l’annuaire de construction aux côtés des fichiers d’assemblage de votre application. Pour faciliter l’accès, créez une `GetAbsolutePath` méthode `Configure` d’aide appelée après la méthode

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. Utilisez `GetAbsolutePath` la méthode `Startup` dans le constructeur `_modelPath`de classe pour définir le .

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. Configurez `PredictionEnginePool` le pour `ConfigureServices` votre application dans la méthode :

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a>Créer un gestionnaire d’analyse de sentiment

Les prédictions seront faites à l’intérieur de la page principale de l’application. Par conséquent, une méthode qui prend `PredictionEnginePool` l’entrée de l’utilisateur et utilise le pour retourner une prédiction doit être ajoutée.

1. Ouvrez le fichier *Index.cshtml.cs* situé dans l’annuaire *Pages* et ajoutez les instructions suivantes à l’aide de relevés :

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    Afin d’utiliser `PredictionEnginePool` le configuré dans la `Startup` classe, vous devez l’injecter dans le constructeur du modèle où vous souhaitez l’utiliser.

1. Ajoutez une variable `PredictionEnginePool` pour `IndexModel` référencer l’intérieur de la classe.

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. Créez un constructeur `IndexModel` dans la `PredictionEnginePool` classe et injectez le service en elle.

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. Créez un gestionnaire de `PredictionEnginePool` méthode qui utilise les prédictions à partir des entrées de l’utilisateur reçues de la page Web.

    1. Ci-dessous la `OnGet` méthode, créez une nouvelle méthode appelée`OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. À `OnGetAnalyzeSentiment` l’intérieur de la méthode, retourner *sentiment neutre* si l’entrée de l’utilisateur est vide ou nul.

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. Compte tenu d’une entrée `ModelInput`valide, créez une nouvelle instance de .

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. Utilisez `PredictionEnginePool` le pour prédire le sentiment.

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. Convertir la `bool` valeur prévue en toxique ou non toxique avec le code suivant.

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. Enfin, retournez le sentiment à la page web.

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a>Configurer la page Web

Les résultats retournés par le `OnGetAnalyzeSentiment` seront `Index` affichés dynamiquement sur la page web.

1. Ouvrez le fichier *Index.cshtml* dans l’annuaire *Pages* et remplacez son contenu par le code suivant :

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. Ensuite, ajoutez du code de style css à la fin de la page *site.css* dans le répertoire *wwwroot-css* :

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. Après cela, ajoutez du code pour envoyer `OnGetAnalyzeSentiment` des entrées de la page Web au gestionnaire.

    1. Dans le fichier *site.js* situé dans *l’annuaire wwwroot-js,* créez une fonction appelée `getSentiment` `OnGetAnalyzeSentiment` pour faire une demande GET HTTP avec l’entrée de l’utilisateur au gestionnaire.

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. Ci-dessous, ajouter `updateMarker` une autre fonction appelée à mettre à jour dynamiquement la position du marqueur sur la page Web que le sentiment est prédit.

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. Créez une fonction `updateSentiment` de gestionnaire d’événements appelée pour `OnGetAnalyzeSentiment` obtenir l’entrée de l’utilisateur, envoyez-la à la fonction en utilisant la `getSentiment` fonction et mettez à jour le marqueur avec la `updateMarker` fonction.

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. Enfin, enregistrez le gestionnaire d’événements et liez-le à l’élément `textarea` avec l’attribut. `id=Message`

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>Exécuter l’application

Maintenant que votre application est configuré, exécutez l’application qui doit être lancée dans votre navigateur.

Lorsque l’application est lancée, entrez *Model Builder est cool!* dans la zone de texte. Le sentiment prévu affiché ne doit pas être *toxique*.

![Fenêtre de course avec la fenêtre de sentiment prévue](./media/sentiment-analysis-model-builder/web-app.png)

Si vous avez besoin de référencer les projets générés par Le `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` constructeur modèle à une date ultérieure à l’intérieur d’une autre solution, vous pouvez les trouver à l’intérieur de l’annuaire.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Créez une application ASP.NET Core Razor Pages
> - Préparer et comprendre les données
> - Choisir un scénario
> - Chargement des données
> - Effectuer l’apprentissage du modèle
> - Évaluer le modèle
> - Utiliser le modèle pour les prévisions

### <a name="additional-resources"></a>Ressources supplémentaires

Pour en savoir plus sur les rubriques mentionnées dans ce tutoriel, consultez les ressources suivantes :

- [Scénarios du Générateur de modèles](../automate-training-with-model-builder.md#scenarios)
- [Classification binaire](../resources/glossary.md#binary-classification)
- [Mesures du modèle de classification binaire](../resources/metrics.md#evaluation-metrics-for-binary-classification)
