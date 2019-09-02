---
title: Générer automatiquement un classifieur binaire à l’aide de la CLI ML.NET
description: Générer automatiquement un modèle ML et le code C# associé à partir d’un exemple de jeu de données
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: c0e188286821f0e3822fde4af74a1561edfbb868
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107272"
---
# <a name="auto-generate-a-binary-classifier-using-the-cli"></a>Générer automatiquement un classifieur binaire à l’aide de la CLI

Découvrez comment utiliser la CLI ML.NET pour générer automatiquement un modèle ML.NET et le code C# sous-jacent. Vous fournissez simplement votre jeu de données et la tâche de machine learning que vous souhaitez implémenter, et la CLI utilise le moteur AutoML pour créer le code source nécessaire à la génération et au déploiement du modèle, ainsi que le modèle binaire.

Dans ce tutoriel, vous allez effectuer les étapes suivantes :
> [!div class="checklist"]
> - Préparer vos données pour la tâche de machine learning sélectionnée
> - Exécuter la commande « mlnet auto-train » à partir de la CLI
> - Examiner les résultats des métriques de la qualité
> - Comprendre le code C# généré nécessaire pour utiliser le modèle dans votre application
> - Explorer le code C# généré ayant servi à entraîner le modèle

> [!NOTE]
> Cette rubrique fait référence à l’outil CLI ML.NET, actuellement en préversion. Les ressources sont donc susceptibles d’être modifiées. Pour plus d’informations, consultez [l’introduction à ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Intégrée à ML.NET, l’interface CLI ML.NET a pour objectif principal de « démocratiser » ML.NET auprès des développeurs .NET qui débutent avec ML.NET afin de leur éviter d’écrire le code de zéro quand ils commencent.

Vous pouvez exécuter l’interface CLI ML.NET à partir de n’importe quelle invite de commandes (Windows, Mac ou Linux) et générer ensuite des modèles ML.NET et du code source de qualité sur la base des jeux de données d’entraînement que vous fournissez.

## <a name="pre-requisites"></a>Conditions préalables

- [SDK .NET Core 2.2 ](https://dotnet.microsoft.com/download/dotnet-core/2.2) ou version ultérieure
- (Facultatif) [Visual Studio 2017 ou 2019](https://visualstudio.microsoft.com/vs/)
- [CLI ML.NET](../how-to-guides/install-ml-net-cli.md)

Une fois que les projets en C# ont été générés, vous pouvez les exécuter à partir de Visual Studio ou à l’aide de la commande `dotnet run` (CLI .NET Core).

## <a name="prepare-your-data"></a>Préparer vos données

Nous allons utiliser un jeu de données existant issu d’un scénario « Analyse des sentiments », qui est une tâche de machine learning de classification binaire. Vous pouvez utiliser votre propre jeu de données de la même façon, et le modèle et le code seront générés automatiquement.

1. Téléchargez le [fichier zip du jeu de données UCI Sentiment Labeled Sentences (voir les citations dans la remarque ci-dessous)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) et décompressez-le dans un dossier de votre choix.

    > [!NOTE]
    > Les jeux de données utilisés dans ce tutoriel incluent un jeu de données provenant de « From Group to Individual Labels using Deep Features » (Kotzias et al,. KDD 2015), hébergé dans le référentiel UCI Machine Learning (Dua, D. et Karra Taniskidou, E., 2017). Référentiel UCI Machine Learning [http://archive.ics.uci.edu/ml ]. Irvine (Californie) : Université de Californie, School of Information and Computer Science.

2. Copiez le fichier `yelp_labelled.txt` dans un dossier que vous avez créé précédemment (par exemple, `/cli-test`).

3. Ouvrez votre invite de commandes standard et accédez au dossier où vous avez copié le fichier de jeu de données. Par exemple :

    ```console
    > cd /cli-test
    ```

    Utilisez un éditeur de texte comme Visual Studio Code pour ouvrir et explorer le fichier de jeu de données `yelp_labelled.txt`. Vous voyez que le fichier a cette structure :

    - Le fichier n’a pas d’en-tête. Vous utiliserez l’index de colonne.

    - Il y a seulement deux colonnes :

        | Texte (index de colonne 0) | Étiquette (index de colonne 1)|
        |--------------------------|-------|
        | Super ! J’ai adoré cet endroit. | 1 |
        | La pâte n’est pas bonne. | 0 |
        | Elle n’avait aucun goût et sa texture n’était vraiment pas agréable. | 0 |
        | ...BEAUCOUP D’AUTRES LIGNES DE TEXTE... | ...(1 ou 0)... |

    N’oubliez pas de fermer le fichier de jeu dans l’éditeur.

    Maintenant, vous êtes prêt à commencer à utiliser la CLI pour ce scénario « Analyse des sentiments ».

    > [!NOTE]
    > Quand vous aurez terminé ce tutoriel, vous pourrez également essayer avec vos propres jeux de données, si ceux-ci ont été préparés en vue d’être utilisés pour les tâches ML prises en charge dans la préversion de la CLI ML.NET, à savoir les tâches *« Classification binaire », « Classification multiclasse » et « Régression »* ).

## <a name="run-the-mlnet-auto-train-command"></a>Exécuter la commande « mlnet auto-train »

1. Exécutez la commande CLI ML.NET suivante :

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    Cette commande exécute la **commande `mlnet auto-train`**  :
    - pour une **tâche ML** de type **`binary-classification`**
    - en utilisant le **fichier de jeu de données `yelp_labelled.txt`** comme jeu de données d’entraînement et de test (en interne, la CLI utilise la validation croisée ou divise le jeu de données initial en deux jeux de données distincts pour l’entraînement et le test)
    - où la **colonne objectif/cible** que vous voulez prédire (généralement appelée **« étiquette »** ) est la **colonne d’index 1** (soit la deuxième colonne puisqu’il s’agit ici d’un index de base zéro)
    - qui **n’utilise pas d’en-tête de fichier** avec les noms de colonnes étant donné que ce fichier de jeu de données particulier n’a pas d’en-tête
    - où la **durée d’exploration ciblée** pour l’essai est de **10 secondes**

    La CLI affiche une sortie de ce type :

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[Fenêtres](#tab/windows)

    ![Commande auto-train de l’interface CLI ML.NET dans PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    ![Commande auto-train de l’interface CLI ML.NET dans PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    Dans ce cas particulier, en seulement 10 secondes et avec le petit jeu de données fourni, l’outil CLI a eu le temps d’exécuter plusieurs itérations, ce qui signifie qu’il a effectué plusieurs opérations d’entraînement en essayant diverses combinaisons d’algorithmes/configuration, avec différentes transformations de données internes et différents hyperparamètres d’algorithme. 

    Au final, le modèle de « meilleure qualité » trouvé dans le délai de 10 secondes est un modèle qui utilise un entraîneur/algorithme particulier avec une configuration spécifique. La commande peut produire des résultats variables selon la durée de l’exploration. La sélection est basée sur toutes les métriques indiquées, comme `Accuracy`.

    **Comprendre les métriques de qualité du modèle**

    La première métrique, et la plus simple, permettant d’évaluer un modèle de classification binaire est la précision, car elle est facile à comprendre. La précision peut se définir comme la proportion de prédictions correctes avec un jeu de données de test. Plus la précision est proche de 100 % (1.00), meilleure est la qualité.

    Toutefois, dans certains cas, faire une évaluation seulement avec la métrique de précision ne suffit pas, en particulier quand l’étiquette (0 et 1 dans ce cas) n’est pas équilibrée dans le jeu de données de test.

    Pour connaître les autres métriques et avoir **plus d’informations détaillées sur les métriques** telles que la précision (Accuracy), l’aire sous la courbe (AUC), l’aire sous la courbe précision/rappel (AUCPR), le score F1 utilisées pour évaluer les différents modèles, consultez [Présentation des métriques ML.NET](../resources/metrics.md)

    > [!NOTE]
    > Vous pouvez essayer ce jeu de données très semblable et définir une durée de quelques minutes pour `--max-exploration-time` (par exemple, spécifiez 180 secondes pour une durée de trois minutes). Cela permet de vous trouver un modèle encore « meilleur », avec une configuration de pipeline d’entraînement différente pour ce jeu de données (qui est très petit, avec 1 000 lignes). 
        
    Si vous souhaitez trouver un modèle de « meilleure/bonne qualité » qui soit un « modèle prêt pour la production » et ciblant des jeux de données plus volumineux, vous devez faire des essais avec la CLI, généralement en spécifiant une durée d’exploration beaucoup plus longue selon la taille du jeu de données. En fait, dans de nombreux cas, vous aurez besoin de spécifier une durée d’exploration de plusieurs heures, d’autant plus si le jeu de données contient beaucoup de lignes et de colonnes. 

1. L’exécution de la commande précédente a généré les ressources suivantes :

    - Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé. 
    - Le code C# nécessaire pour exécuter/évaluer ce modèle généré (et pour effectuer des prédictions dans vos applications utilisateur avec ce modèle).
    - Le code C# d’entraînement utilisé pour générer ce modèle (à des fins d’apprentissage).
    - Un fichier journal présentant toutes les itérations explorées, avec les détails de chaque algorithme essayé avec sa combinaison d’hyperparamètres et de transformations des données. 

    Les deux premières ressources (fichier .zip du modèle et code C# pour exécuter ce modèle) peuvent être utilisées directement dans vos applications utilisateur (application web ASP.NET Core, services, application de bureau, etc.) pour effectuer des prédictions à l’aide de ce modèle ML généré.

    La troisième ressource, le code d’entraînement, montre quel code de l’API ML.NET a été utilisé par la CLI pour entraîner le modèle généré. Vous pouvez ainsi savoir quels entraîneur/algorithme et hyperparamètres spécifiques ont été sélectionnés par la CLI.

Toutes les ressources listées ci-dessus seront décrites dans les étapes suivantes du tutoriel.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Explorer le code C# généré à utiliser pour exécuter le modèle et effectuer des prédictions

1. Dans Visual Studio (2017 ou 2019), ouvrez la solution générée dans le dossier nommé `SampleBinaryClassification`, situé dans votre dossier de destination d’origine (dans le tutoriel qui s’appelait `/cli-test`). Vous devez voir une solution similaire à celle-ci :

    > [!NOTE]
    > Dans le tutoriel, nous vous suggérons d’utiliser Visual Studio, mais vous pouvez aussi explorer le code C# généré (deux projets) dans n’importe quel éditeur de texte et exécuter ensuite l’application console générée avec `dotnet CLI` sur une machine macOS, Linux ou Windows.

    ![Solution Visual Studio générée par la CLI](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - Vous pouvez utiliser la **bibliothèque de classes** générée, qui contient le modèle ML sérialisé (fichier .zip) et les classes de données (modèles de données), directement dans votre application utilisateur final, éventuellement en référençant directement cette bibliothèque de classes (ou en déplaçant le code, selon votre préférence).
    - L’**application console** générée contient le code d’exécution que vous devez revoir. Ensuite, vous réutilisez généralement le « score d’évaluation » (code qui exécute le modèle ML pour effectuer des prédictions) en déplaçant ce code simple (de quelques lignes) vers l’application utilisateur où vous souhaitez effectuer les prédictions. 

1. Ouvrez les fichiers de classes **ModelInput.cs** et **ModelOutput.cs** dans le projet de bibliothèque de classes. Vous voyez que ces classes sont les « classes de données » ou les classes POCO où sont stockées les données. Il s’agit de « code réutilisable », qui peut être utile de générer si votre jeu de données contient des dizaines ou des centaines de colonnes. 
    - La classe `ModelInput` est utilisée pour lire les données du jeu de données. 
    - La classe `ModelOutput` est utilisée pour obtenir le résultat de prédiction (données de prédiction).

1. Ouvrez le fichier Program.cs et explorez le code. Quelques lignes suffisent pour exécuter le modèle et effectuer un exemple de prédiction.

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // Create sample data to do a single prediction with it 
        ModelInput sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        ModelOutput predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

- La première ligne de code crée simplement un objet `MLContext`, qui est nécessaire pour exécuter le code ML.NET. 

- La deuxième ligne de code est commentée, car vous n’avez pas besoin d’entraîner le modèle dans la mesure où celui-ci a déjà été entraîné automatiquement par l’outil CLI et enregistré dans le fichier .zip sérialisé du modèle. Toutefois, si vous souhaitez afficher les commentaires pour savoir *comment le modèle a été entraîné* par la CLI, vous pouvez décommenter cette ligne et exécuter/déboguer le code d’entraînement utilisé pour ce modèle ML spécifique.

- Dans la troisième ligne de code, vous chargez le modèle du fichier .zip de modèle sérialisé à l’aide de l’API `mlContext.Model.Load()`, en fournissant le chemin de ce fichier.

- Dans la quatrième ligne de code, vous chargez le code pour créer l’objet `PredictionEngine` avec l’API `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)`. Vous avez besoin de l’objet `PredictionEngine` chaque fois que vous souhaitez effectuer une prédiction ciblant un exemple de données unique (dans ce cas, un seul élément de texte pour prédire le sentiment).

- La cinquième ligne de code spécifie où vous créez cet *exemple de données unique* à utiliser pour la prédiction, en appelant la fonction `CreateSingleDataSample()`. Étant donné que l’outil CLI ne sait pas quel type d’exemple de données utiliser, au sein de cette fonction, il charge la première ligne du jeu de données. Toutefois, dans ce cas, vous pouvez également créer vos propres données « codées en dur » au lieu de l’implémentation actuelle de la fonction `CreateSingleDataSample()`, en mettant à jour ce code plus simple pour implémenter cette fonction :

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. Exécutez le projet, soit en utilisant l’exemple de données initialement chargé de la première ligne du jeu de données, soit en fournissant votre propre exemple de données personnalisées codées en dur. Vous devez obtenir une prédiction comparable à ceci :

    # <a name="windowstabwindows"></a>[Fenêtres](#tab/windows)

    Exécutez l’application console à partir de Visual Studio en appuyant sur F5 (bouton de lecture) :

    ![Commande auto-train de l’interface CLI ML.NET dans PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    Exécutez l’application console à partir de l’invite de commandes en tapant les commandes suivantes :

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![Commande auto-train de l’interface CLI ML.NET dans PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. Essayez de remplacer l’exemple de données codées en dur par d’autres phrases avec un sentiment différent afin de voir comment le modèle prédit un sentiment positif ou négatif. 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>Intégrer les prédictions de modèle ML à vos applications utilisateur

Vous pouvez utiliser du « code d’évaluation de modèle ML » similaire pour exécuter le modèle dans votre application utilisateur et effectuer des prédictions. 

Par exemple, déplacez ce code directement vers une application de bureau Windows, comme **WPP** et **WinForms**, puis exécutez le modèle de la même façon que dans l’application console.

Toutefois, la méthode d’implémentation de ces lignes de code pour exécuter un modèle ML doit être optimisée (notamment en mettant en cache le fichier .zip du modèle et en le chargeant une seule fois) et utiliser des objets singleton au lieu de les créer à chaque requête, en particulier si votre application doit être scalable, à l’image des applications web ou des services distribués, comme nous allons le voir dans la section suivante.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Exécuter des modèles ML.NET dans des applications ou services web ASP.NET Core scalables (applications multithread)

La création de l’objet modèle (`ITransformer` chargé d’un fichier .zip de modèle) et de l’objet `PredictionEngine` doit être optimisée, surtout en vue d’une exécution sur des applications web ou des services distribués scalables. Pour le premier cas, l’objet modèle (`ITransformer`), l’optimisation est simple. Dans la mesure où l’objet `ITransformer` est thread-safe, vous pouvez le mettre en cache en tant qu’objet singleton ou statique, afin de charger le modèle une seule fois.

Pour le deuxième objet, l’objet `PredictionEngine`, l’optimisation n’est pas si facile, car l’objet `PredictionEngine` n’est pas thread-safe. Vous ne pouvez donc pas instancier cet objet en tant qu’objet singleton ou statique dans une application ASP.NET Core. Ce problème est traité en détail dans ce [billet de blog](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/). 

Toutefois, les choses sont heureusement beaucoup plus simples pour vous que ce qui est expliqué dans ce billet de blog. Dans un souci de vous proposer une approche plus simple, nous avons créé un **« package d’intégration .NET Core »** très utile. Vous pouvez facilement vous en servir dans vos applications et services ASP.NET Core en l’inscrivant auprès des services DI, puis en l’utilisant directement à partir de votre code. Consultez le tutoriel et l’exemple ci-dessous pour savoir comment faire :

- [Tutoriel : Exécuter des modèles ML.NET sur des applications web et API web ASP.NET Core scalables](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Exemple : Modèle ML.NET scalable sur une API web ASP.NET Core](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>Explorer le code C# généré ayant servi à entraîner le modèle de « meilleure qualité » 

Pour approfondir l’apprentissage, vous pouvez également explorer le code C# généré qui a été utilisé par l’outil CLI pour entraîner le modèle généré.

Ce « code de modèle d’entraînement » est actuellement généré dans la classe personnalisée générée, nommée `ModelBuilder`. Vous pouvez y examiner ce code d’entraînement.

Plus important encore, pour ce scénario particulier (modèle « Analyse des sentiments »), vous pouvez également comparer ce code d’entraînement généré avec le code décrit dans le tutoriel suivant :

- Comparaison : [Tutoriel : Utiliser ML.NET dans un scénario de classification binaire d’une analyse de sentiments](sentiment-analysis.md).

Il est intéressant de comparer la configuration d’algorithme et de pipeline choisie dans le tutoriel avec le code généré par l’outil CLI. Selon la durée d’itération et de recherche de meilleurs modèles, l’algorithme choisi peut être différent, tout comme sa configuration d’hyperparamètres et de pipeline.

## <a name="see-also"></a>Voir aussi

- [Automatiser l’entraînement du modèle avec la CLI ML.NET](../automate-training-with-cli.md)
- [Tutoriel : Exécuter des modèles ML.NET sur des applications web et API web ASP.NET Core scalables](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Exemple : Modèle ML.NET scalable sur une API web ASP.NET Core](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [Informations de référence sur la commande auto-train de la CLI ML.NET](../reference/ml-net-cli-reference.md) 
- [Guide pratique pour installer l’outil CLI ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Télémétrie dans la CLI ML.NET](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> - Préparer vos données pour la tâche ML sélectionnée (problème à résoudre)
> - Exécuter la commande « mlnet auto-train » dans l’outil CLI
> - Examiner les résultats des métriques de la qualité
> - Comprendre le code C# généré nécessaire pour exécuter le modèle (code à utiliser dans votre application utilisateur)
> - Explorer le code C# généré ayant servi à entraîner le modèle de « meilleure qualité » (à des fins d’apprentissage)

> [!div class="nextstepaction"]
> [Automatiser l’entraînement du modèle avec la CLI ML.NET](../automate-training-with-cli.md)
