---
title: 'Tutorial: ML.NET modèle de classification d’image de TensorFlow'
description: Apprenez à transférer les connaissances d’un modèle TensorFlow existant en un nouveau modèle de classification d’image ML.NET. Le modèle TensorFlow a été formé pour classer les images en mille catégories. Le modèle ML.NET utilise l’apprentissage de transfert pour classer les images en moins de catégories plus larges.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 1e5478f53c82f36ddafe19e3659e2234ff9687b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241024"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Tutorial: Générer un modèle de classification d’image ML.NET à partir d’un modèle TensorFlow pré-formé

Apprenez à transférer les connaissances d’un modèle TensorFlow existant en un nouveau modèle de classification d’image ML.NET.

Le modèle TensorFlow a été formé pour classer les images en mille catégories. Le modèle ML.NET utilise une partie du modèle TensorFlow dans son pipeline pour former un modèle pour classer les images en 3 catégories.

Pour entraîner un modèle de [Classification d’images](https://en.wikipedia.org/wiki/Outline_of_object_recognition) à partir de zéro, il faut définir des millions de paramètres, disposer d’une multitude de données d’apprentissage étiquetées et posséder une grande quantité de ressources de calcul (des centaines d’heures GPU). S’il n’est pas aussi efficace que l’apprentissage d’un modèle personnalisé à partir de zéro, l’apprentissage par transfert permet de raccourcir ce processus : il s’agit de travailler avec des milliers (et non des millions) d’images étiquetées et de créer assez vite un modèle personnalisé (en une heure sur un ordinateur sans GPU). Ce tutoriel échelles qui traitent encore plus loin, en utilisant seulement une douzaine d’images de formation.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> * Comprendre le problème
> * Intégrer le modèle TensorFlow pré-formé dans le pipeline ML.NET
> * Former et évaluer le modèle ML.NET
> * Classifier une image de test

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF). Notez que, par défaut, la configuration de projet .NET pour ce tutoriel cible .NET Core 2.2.

## <a name="what-is-transfer-learning"></a>Qu’est-ce que l’apprentissage par transfert ?

L’apprentissage de transfert est le processus d’utilisation des connaissances acquises tout en résolvant un problème et en l’appliquant à un problème différent mais connexe.

Pour ce tutoriel, vous utilisez une partie d’un modèle TensorFlow - formé pour classer les images en mille catégories - dans un modèle ML.NET qui classe les images en 3 catégories.

## <a name="prerequisites"></a>Conditions préalables requises

* [Visual Studio 2017 version 15.6 ou plus tard](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) avec le ".NET Core cross-platform development" charge de travail installé.
* [Le fichier .zip du répertoire de ressources du tutoriel](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [Le modèle Machine Learning InceptionV1](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Sélectionnez la bonne tâche d’apprentissage automatique

### <a name="deep-learning"></a>Apprentissage approfondi

Le [Deep Learning](https://en.wikipedia.org/wiki/Deep_learning) est un sous-ensemble du Machine Learning, qui révolutionne des domaines comme la Vision par ordinateur et la Reconnaissance vocale.

L’entraînement des modèles Deep Learning s’effectue à l’aide de grands ensembles de [données étiquetées](https://en.wikipedia.org/wiki/Labeled_data) et de [réseaux neuronaux](https://en.wikipedia.org/wiki/Artificial_neural_network) comportant plusieurs couches d’apprentissage. Le Deep Learning présente différentes caractéristiques :

* Il fonctionne mieux sur certaines tâches comme la Vision par ordinateur.
* Nécessite d’énormes quantités de données de formation.

La classification d’image est une tâche commune d’apprentissage automatique qui nous permet de classer automatiquement les images en catégories telles que :

* détecter ou non la présence d’un visage dans une image ;
* Détection des chats contre des chiens.

 Ou comme dans les images suivantes, déterminer si une image est un (n) nourriture, jouet ou appareil:

![image de pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![image de nounours](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![image de grille-pain](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Les images précédentes appartiennent à Wikimedia Commons et sont attribuées ainsi :
>
> * « 220px-Pepperoni_pizza.jpg », domaine public, https://commons.wikimedia.org/w/index.php?curid=79505 ;
> * « 119px-Nalle_-_a_small_brown_teddy_bear.jpg », de [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) (photographie personnelle), CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166 ;
> * « 193px Broodrooster.jpg », de [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) (travail personnel), CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403.

Le `Inception model` est formé pour classer les images en mille catégories, mais pour ce tutoriel, vous devez classer les images dans un ensemble de catégories plus petites, et seulement ces catégories. Entrez la partie `transfer` de `transfer learning`. Vous pouvez transposer la capacité de `Inception model` à identifier et à classer des images aux nouvelles catégories, en nombre limité, de votre classifieur d’images personnalisé.

* Aliment
* Jouet
* Appliance

Ce tutoriel utilise le modèle TensorFlow [Inception modèle](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) d’apprentissage `ImageNet` profond, un modèle populaire de reconnaissance d’image formés sur le jeu de données. Le modèle TensorFlow classe des images entières en mille classes, telles que "Umbrella", "Jersey" et "Dishwasher".

Parce `Inception model` que le a déjà été pré-formé sur des milliers d’images différentes, en interne, il contient les [caractéristiques d’image](https://en.wikipedia.org/wiki/Feature_(computer_vision)) nécessaires pour l’identification d’images. Nous pouvons utiliser ces caractéristiques d’image interne dans le modèle pour former un nouveau modèle avec beaucoup moins de classes.

Comme le montre le diagramme suivant, vous ajoutez une référence aux packages NuGet ML.NET dans vos applications .NET Core ou .NET Framework. Sous les couvertures, ML.NET inclut et `TensorFlow` fait référence à la bibliothèque indigène `TensorFlow` qui vous permet d’écrire du code qui charge un fichier modèle formé existant.

![Diagramme ML.NET de transformation TensorFlow](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Classification multiclasse

Après avoir utilisé le modèle de création TensorFlow pour extraire des fonctionnalités adaptées comme entrée pour un algorithme d’apprentissage automatique classique, nous ajoutons un classificateur ML.NET [multi-classes](../resources/tasks.md#multiclass-classification).

Le formateur spécifique utilisé dans ce cas est [l’algorithme de régression logistique multinomiale](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).

L’algorithme mis en œuvre par ce formateur fonctionne bien sur les problèmes avec un grand nombre de fonctionnalités, ce qui est le cas pour un modèle d’apprentissage profond fonctionnant sur les données d’image.

### <a name="data"></a>Données

Il y a deux sources de données : le fichier `.tsv` et les fichiers image.  Le fichier `tags.tsv` comporte deux colonnes : la première est définie comme `ImagePath` et la deuxième est le `Label` correspondant à l’image. L’exemple de fichier suivant ne possède pas de ligne d’en-tête :

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

Les images d’apprentissage et de test se trouvent dans les dossiers de ressources que vous allez télécharger dans un fichier zip. Elles appartiennent à Wikimedia Commons.
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), le dépôt de fichiers multimédias sous licence libre.* Extrait le 17 octobre 2018 à https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster 10:48https://commons.wikimedia.org/wiki/Teddy_bear

## <a name="setup"></a>Programme d’installation

### <a name="create-a-project"></a>Création d’un projet

1. Créer une **application console .NET Core** appelée « TransferLearningTF ».

1. Installez le **package NuGet Microsoft.ML** :

    * Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**.
    * Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir et recherchez **Microsoft.ML**.
    * Cliquez sur la **version** drop-down, sélectionnez le paquet **1.4.0** dans la liste, et sélectionnez le bouton **Installer.**
    * Sélectionnez le bouton **OK** sur le dialogue **Preview Changes.**
    * Sélectionnez le bouton **I Accept** sur le dialogue **d’acceptation de licence** si vous êtes d’accord avec les conditions de licence pour les paquets énumérés.
    * Répétez ces étapes pour **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** et **Microsoft.ML.TensorFlow v1.4.0**.

### <a name="download-assets"></a>Télécharger les éléments multimédias

1. Téléchargez le [fichier zip du répertoire de ressources du projet ](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip) et décompressez-le.

1. Copiez le répertoire `assets` dans votre répertoire de projet *TransferLearningTF*. Ce répertoire et ses sous-répertoires contiennent les fichiers de données et d’aide nécessaires à ce tutoriel (sauf pour le modèle Inception, que vous allez télécharger et ajouter à l’étape suivante).

1. Téléchargez le [modèle Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) et décompressez-le.

1. Copiez le contenu décompressé du répertoire `inception5h` dans le répertoire `assets/inception` de votre projet *TransferLearningTF*. Ce répertoire contient le modèle et les fichiers d’aide supplémentaires nécessaires à ce tutoriel, comme le montre l’image suivante :

   ![Contenu du répertoire Inception](./media/image-classification/inception-files.png)

1. Dans l’Explorateur de solutions, cliquez sur chacun des fichiers du répertoire et des sous-répertoires de ressources et sélectionnez **Propriétés**. Sous **Advanced**, changer la valeur de **la copie à l’annuaire de sortie** à copier si plus **récent**.

### <a name="create-classes-and-define-paths"></a>Créer des classes et définir des chemins

1. Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* : 

    [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddUsings)]

1. Ajoutez le code suivant à `Main` la ligne juste au-dessus de la méthode pour spécifier les trajectoires d’actifs :

    [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareGlobalVariables)]

1. Créez des classes pour vos données d’entrée et vos prédictions.

    [!code-csharp[DeclareImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImageData)]

    `ImageData` est la classe de données d’images d’entrée, qui comprend les champs <xref:System.String> suivants :

    * `ImagePath` contient le nom du fichier image.
    * `Label` contient la valeur de l’étiquette d’image.

1. Ajoutez une nouvelle classe à votre projet pour `ImagePrediction` :

    [!code-csharp[DeclareImagePrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImagePrediction)]

    `ImagePrediction` est la classe de prédiction des images, qui comprend les champs suivants :

    * `Score` contient le pourcentage de confiance d’une classification d’image donnée.
    * `PredictedLabelValue` contient la valeur de l’étiquette de classification d’image prédite.

    `ImagePrediction` représente la classe utilisée pour la prédiction, une fois le modèle formé. Elle comporte une `string` (`ImagePath`) correspondant au chemin de l’image. Le `Label` est utilisé pour réutiliser et former le modèle. L’attribut `PredictedLabelValue` est utilisé pendant la prédiction et l’évaluation. L’évaluation utilise une entrée avec les données d’apprentissage, les valeurs prédites et le modèle.

### <a name="initialize-variables-in-main"></a>Initialiser les variables dans Principal

1. Initialiser la variable `mlContext` avec une nouvelle instance de `MLContext`.  Remplacez la ligne `Console.WriteLine("Hello World!")` par le code suivant dans la méthode `Main` :

    [!code-csharp[CreateMLContext](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CreateMLContext)]

    La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

### <a name="create-a-struct-for-inception-model-parameters"></a>Créer une structure pour les paramètres du modèle Inception

1. Le modèle Inception a plusieurs paramètres que vous devez transmettre. Créez une struct pour cartographier les valeurs de paramètres `Main()` vers des noms amicaux avec le code suivant, juste après la méthode :

    [!code-csharp[InceptionSettings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Créer une méthode d’utilitaire d’affichage

Étant donné que vous allez afficher les données d’image et les prédictions associées plusieurs fois, créez une méthode d’utilitaire d’affichage qui gère l’affichage des données d’image et des résultats de prédiction.

1. Créez la méthode `DisplayResults()` juste après le struct `InceptionSettings` avec le code suivant :

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. Remplir le corps `DisplayResults` de la méthode:

    [!code-csharp[DisplayPredictions](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>Créez une méthode d’utilitaire de fichier .tsv

1. Créez la méthode `ReadFromTsv()` juste après la méthode `DisplayResults()`, en utilisant le code suivant :

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. Remplir le corps `ReadFromTsv` de la méthode:

    [!code-csharp[ReadFromTsv](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReadFromTsv)]

    Le code analyse le `tags.tsv` fichier pour ajouter le chemin de `ImagePath` fichier au nom `Label` du `ImageData` fichier d’image pour la propriété et le charger et le dans un objet.

### <a name="create-a-method-to-make-a-prediction"></a>Créer une méthode pour faire une prédiction

1. Créez la méthode `ClassifySingleImage()` juste avant la méthode `DisplayResults()`, en utilisant le code suivant :

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Créez `ImageData` un objet qui contient le chemin entièrement `ImagePath`qualifié et le nom de fichier d’image pour le single . Ajoutez le code suivant à la fin de la méthode `ClassifySingleImage()` :

    [!code-csharp[LoadImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadImageData)]

1. Faites une seule prédiction, en ajoutant le code `ClassifySingleImage` suivant comme ligne suivante dans la méthode:

    [!code-csharp[PredictSingle](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#PredictSingle)]

    Pour obtenir la prédiction, utilisez la méthode [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) . Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas sans fil. Il est acceptable d’utiliser dans des environnements à thread unique ou prototype. Pour améliorer les performances et la `PredictionEnginePool` sécurité des fils [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dans les environnements de production, utilisez le service, qui crée un des objets à utiliser dans toute votre application. Voir ce guide sur la façon [d’utiliser `PredictionEnginePool` dans un ASP.NET’API Web de base](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > L’extension de service `PredictionEnginePool` est disponible en préversion.

1. Affichez le résultat de la prédiction à la fin de la méthode `ClassifySingleImage()` :

   [!code-csharp[DisplayPrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>Construire le pipeline modèle ML.NET

Un pipeline modèle ML.NET est une chaîne d’estimateurs. Notez qu’aucune exécution n’a lieu pendant la construction du pipeline. Les objets de l’estimateur sont créés mais non exécutés.

1. Ajouter une méthode pour générer le modèle

    Cette méthode est le cœur du tutoriel. Il crée un pipeline pour le modèle, et forme le pipeline pour produire le modèle ML.NET. Il évalue également le modèle par rapport à certaines données de test inédites.

    Créez la méthode `GenerateModel()`, juste après le struct `InceptionSettings` et juste avant la méthode `DisplayResults()`, avec le code suivant :

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Ajouter les estimateurs pour charger, resize et extraire les pixels des données d’image :

    [!code-csharp[ImageTransforms](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ImageTransforms)]

    Les données d’image doivent être traitées dans le format que le modèle TensorFlow attend. Dans ce cas, les images sont chargées dans la mémoire, resized à une taille cohérente, et les pixels sont extraits dans un vecteur numérique.

1. Ajouter l’estimateur pour charger le modèle TensorFlow, et le marquer:

    [!code-csharp[ScoreTensorFlowModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ScoreTensorFlowModel)]

    Cette étape du pipeline charge le modèle TensorFlow en mémoire, puis traite le vecteur des valeurs de pixels à travers le réseau modèle TensorFlow. L’application d’entrées à un modèle d’apprentissage profond, et la génération d’une sortie à l’aide du modèle, est appelée **notation**. Lors de l’utilisation du modèle dans son intégralité, la notation fait une inférence, ou une prédiction.

    Dans ce cas, vous utilisez tout le modèle TensorFlow, sauf la dernière couche, qui est la couche qui fait l’inférence. La sortie de l’avant-dernière `softmax_2_preactivation`couche est étiquetée. La sortie de cette couche est en fait un vecteur de fonctionnalités qui caractérisent les images d’entrée originales.

    Ce vecteur de fonctionnalité généré par le modèle TensorFlow sera utilisé comme entrée à un algorithme de formation ML.NET.

1. Ajoutez l’estimateur pour cartographier les étiquettes de chaîne dans les données de formation pour integer les valeurs clés :

    [!code-csharp[MapValueToKey](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapValueToKey)]

    Le formateur ML.NET qui est annexé ensuite exige que `key` ses étiquettes soient en format plutôt que des cordes arbitraires. Une clé est un nombre qui a une cartographie d’un à un à une valeur de chaîne.

1. Ajoutez l’algorithme de formation ML.NET :

    [!code-csharp[AddTrainer](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddTrainer)]

1. Ajoutez l’estimateur pour cartographier la valeur clé prévue en une chaîne :

    [!code-csharp[MapKeyToValue](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

1. Chargez les données de formation à l’aide de l’emballage [LoadFromTextFile.](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) Ajoutez le code suivant comme première ligne de la méthode `GenerateModel()` :

    [!code-csharp[LoadData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadData "Load the data")]

    Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView). `IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte). Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.

1. Entraînez le modèle avec les données chargées ci-dessus :

    [!code-csharp[TrainModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#TrainModel)]

    La `Fit()` méthode forme votre modèle en appliquant l’ensemble de données de formation au pipeline.

## <a name="evaluate-the-accuracy-of-the-model"></a>Évaluer l’exactitude du modèle

1. Chargez et transformez les données de test, en `GenerateModel` ajoutant le code suivant à la ligne suivante de la méthode :

    [!code-csharp[LoadAndTransformTestData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Il ya quelques images d’échantillons que vous pouvez utiliser pour évaluer le modèle. Comme les données de formation, ceux-ci doivent être chargés dans un `IDataView`, afin qu’ils puissent être transformés par le modèle.

1. Ajoutez le code `GenerateModel()` suivant à la méthode pour évaluer le modèle :

    [!code-csharp[Evaluate](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#Evaluate)]

    Une fois la prédiction définie, la méthode [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :

    * Évalue le modèle (compare les valeurs prévues `labels`avec le jeu de données de test ).
    * Retourne les indicateurs de performances du modèle.

1. Afficher les mesures de précision du modèle

    Utilisez le code suivant pour afficher les métriques, partager les résultats et agir dessus :

    [!code-csharp[DisplayMetrics](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayMetrics)]

    Les indicateurs suivants sont évalués pour la classification d’images :

    * `Log-loss` (voir [Perte logarithmique](../resources/glossary.md#log-loss)). Vous voulez que la perte logarithmique soit aussi proche de zéro que possible.
    * `Per class Log-loss`. La perte logarithmique doit être aussi proche de zéro que possible.

1. Ajoutez le code suivant pour retourner le modèle entraîné à la ligne suivante :

    [!code-csharp[SaveModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Exécutez l’application !

1. Ajoutez l’appel `GenerateModel` `Main` à la méthode après la création de la classe MLContexte :

    [!code-csharp[CallGenerateModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallGenerateModel)]

1. Ajoutez l’appel `ClassifySingleImage()` à la méthode comme `Main` ligne suivante de code dans la méthode:

    [!code-csharp[CallClassifySingleImage](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallClassifySingleImage)]

1. Exécutez votre application console (Ctrl et F5). Vous devriez obtenir les résultats suivants.  Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

Félicitations ! Vous avez maintenant réussi à construire un modèle d’apprentissage `TensorFlow` automatique pour la classification d’images en appliquant l’apprentissage de transfert à un modèle en ML.NET.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Comprendre le problème
> * Intégrer le modèle TensorFlow pré-formé dans le pipeline ML.NET
> * Former et évaluer le modèle ML.NET
> * Classifier une image de test

Consultez le référentiel GitHub d’exemples Machine Learning pour voir un exemple développé de classification d’images.
> [!div class="nextstepaction"]
> [Référentiel GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/)
