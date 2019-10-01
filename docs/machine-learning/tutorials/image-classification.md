---
title: 'Tutoriel : Générer un modèle de classification d’image ML.NET à partir d’un modèle TensorFlow pré-formé'
description: Découvrez comment transférer les connaissances d’un modèle TensorFlow existant dans un nouveau modèle de classification d’image ML.NET. Le modèle TensorFlow a été formé pour classifier les images en milliers de catégories. Le modèle ML.NET utilise l’apprentissage de transfert pour classer les images en moins de catégories plus larges.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: 8ae966330ca85722c72c92e26363d99c7d9de3e7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698651"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Tutoriel : Générer un modèle de classification d’image ML.NET à partir d’un modèle TensorFlow pré-formé

Découvrez comment transférer les connaissances d’un modèle TensorFlow existant dans un nouveau modèle de classification d’image ML.NET.

Le modèle TensorFlow a été formé pour classifier les images en milliers de catégories. Le modèle ML.NET utilise une partie du modèle TensorFlow dans son pipeline pour former un modèle afin de classer les images en 3 catégories.

Pour entraîner un modèle de [Classification d’images](https://en.wikipedia.org/wiki/Outline_of_object_recognition) à partir de zéro, il faut définir des millions de paramètres, disposer d’une multitude de données d’apprentissage étiquetées et posséder une grande quantité de ressources de calcul (des centaines d’heures GPU). S’il n’est pas aussi efficace que l’apprentissage d’un modèle personnalisé à partir de zéro, l’apprentissage par transfert permet de raccourcir ce processus : il s’agit de travailler avec des milliers (et non des millions) d’images étiquetées et de créer assez vite un modèle personnalisé (en une heure sur un ordinateur sans GPU). Ce didacticiel met à l’échelle ce processus plus en détail, en utilisant seulement une douzaine d’images de formation.

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
>
> * Comprendre le problème
> * Incorporer le modèle TensorFlow pré-formé dans le pipeline ML.NET
> * Former et évaluer le modèle ML.NET
> * Classer une image de test

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF). Notez que, par défaut, la configuration de projet .NET pour ce tutoriel cible .NET Core 2.2.

## <a name="what-is-transfer-learning"></a>Qu’est-ce que l’apprentissage par transfert ?

Le transfert d’apprentissage est le processus qui consiste à utiliser les connaissances acquises tout en résolvant un problème et en l’appliquant à un problème différent mais lié.

Pour ce didacticiel, vous utilisez une partie d’un modèle TensorFlow, formé pour classifier les images en mille catégories, dans un modèle ML.NET qui classe les images en trois catégories.

## <a name="prerequisites"></a>Prérequis

* [Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .Net Core » installée.

* Package NuGet Microsoft.ML 1.3.1
* Package NuGet Microsoft. ML. ImageAnalytics 1.3.1
* Package NuGet Microsoft. ML. TensorFlow 1.3.1

* [Le fichier .zip du répertoire de ressources du tutoriel](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [Le modèle Machine Learning InceptionV1](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Sélectionner la tâche de Machine Learning appropriée

### <a name="deep-learning"></a>Deep Learning

Le [Deep Learning](https://en.wikipedia.org/wiki/Deep_learning) est un sous-ensemble du Machine Learning, qui révolutionne des domaines comme la Vision par ordinateur et la Reconnaissance vocale.

L’entraînement des modèles Deep Learning s’effectue à l’aide de grands ensembles de [données étiquetées](https://en.wikipedia.org/wiki/Labeled_data) et de [réseaux neuronaux](https://en.wikipedia.org/wiki/Artificial_neural_network) comportant plusieurs couches d’apprentissage. Le Deep Learning présente différentes caractéristiques :

* Il fonctionne mieux sur certaines tâches comme la Vision par ordinateur.
* Nécessite d’énormes quantités de données d’apprentissage.

La classification d’images est une tâche Machine Learning commune qui nous permet de classer automatiquement les images en catégories telles que :

* détecter ou non la présence d’un visage dans une image ;
* Détection des chats et des chiens.

 Ou comme dans les images suivantes, en déterminant si une image est un (n) aliment, jouet ou appareil :

![image de pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![image de nounours](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![image de grille-pain](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Les images précédentes appartiennent à Wikimedia Commons et sont attribuées ainsi :
>
> * « 220px-Pepperoni_pizza.jpg », domaine public, https://commons.wikimedia.org/w/index.php?curid=79505 ;
> * « 119px-Nalle_-_a_small_brown_teddy_bear.jpg », de [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) (photographie personnelle), CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166 ;
> * « 193px Broodrooster.jpg », de [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) (travail personnel), CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403.

Le `Inception model` est formé pour classer les images en milliers de catégories, mais pour ce didacticiel, vous devez classer les images dans un ensemble de catégories plus petit, et uniquement ces catégories. Entrez la partie `transfer` de `transfer learning`. Vous pouvez transposer la capacité de `Inception model` à identifier et à classer des images aux nouvelles catégories, en nombre limité, de votre classifieur d’images personnalisé.

* Aliment
* Jouet
* Appareil

Ce didacticiel utilise [le modèle d’apprentissage profond TensorFlow](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) , un modèle de reconnaissance d’image populaire formé sur le jeu de données `ImageNet`. Le modèle TensorFlow classifie les images entières en mille classes, telles que « parapluie », « Jersey » et « lave-vaisselle ».

Étant donné que le `Inception model` a déjà été formé sur des milliers d’images différentes, en interne, il contient les [fonctionnalités d’image](https://en.wikipedia.org/wiki/Feature_(computer_vision)) nécessaires à l’identification de l’image. Nous pouvons utiliser ces fonctionnalités d’image interne dans le modèle pour effectuer l’apprentissage d’un nouveau modèle avec beaucoup moins de classes.

Comme le montre le diagramme suivant, vous ajoutez une référence aux packages NuGet ML.NET dans vos applications .NET Core ou .NET Framework. En coulisses, ML.NET inclut et référence la bibliothèque `TensorFlow` native qui vous permet d’écrire du code qui charge un fichier de modèle `TensorFlow` formé existant.

![Diagramme ML.NET de transformation TensorFlow](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Classification multiclasse

Après avoir utilisé le modèle d’Inception TensorFlow pour extraire les fonctionnalités qui conviennent comme entrée pour un algorithme de Machine Learning classique, nous ajoutons un [classifieur multiclasse](../resources/tasks.md#multiclass-classification)ml.net.

Le formateur spécifique utilisé dans ce cas est l' [algorithme de régression logistique multimultinomiale](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).

L’algorithme implémenté par ce formateur fonctionne bien sur les problèmes liés à un grand nombre de fonctionnalités, ce qui est le cas pour un modèle d’apprentissage profond fonctionnant sur des données d’image.

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
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), le dépôt de fichiers multimédias sous licence libre.* Extrait 10:48, 17 octobre 2018 à partir de : https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear

## <a name="setup"></a>Installation

### <a name="create-a-project"></a>Créer un projet

1. Créer une **application console .NET Core** appelée « TransferLearningTF ».

1. Installez le **package NuGet Microsoft.ML** :

    * Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.
    * Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir et recherchez **Microsoft.ML**.
    * Cliquez sur la liste déroulante **version** , sélectionnez le package **1.3.1** dans la liste, puis cliquez sur le bouton **installer** .
    * Sélectionnez le bouton **OK** dans la boîte de dialogue **aperçu des modifications** .
    * Sélectionnez le bouton **J’accepte** dans la boîte de dialogue acceptation de la **licence** si vous acceptez les termes du contrat de licence pour les packages listés.
    * Répétez ces étapes pour **Microsoft. ml. ImageAnalytics v 1.3.1** et **Microsoft. ml. TensorFlow v 1.3.1**.

### <a name="download-assets"></a>Télécharger les ressources

1. Téléchargez le [fichier zip du répertoire de ressources du projet ](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip) et décompressez-le.

1. Copiez le répertoire `assets` dans votre répertoire de projet *TransferLearningTF*. Ce répertoire et ses sous-répertoires contiennent les fichiers de données et d’aide nécessaires à ce tutoriel (sauf pour le modèle Inception, que vous allez télécharger et ajouter à l’étape suivante).

1. Téléchargez le [modèle Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) et décompressez-le.

1. Copiez le contenu décompressé du répertoire `inception5h` dans le répertoire `assets/inputs-train/inception` de votre projet *TransferLearningTF*. Ce répertoire contient le modèle et les fichiers d’aide supplémentaires nécessaires à ce tutoriel, comme le montre l’image suivante :

   ![Contenu du répertoire Inception](./media/image-classification/inception-files.png)

1. Dans l’Explorateur de solutions, cliquez sur chacun des fichiers du répertoire et des sous-répertoires de ressources et sélectionnez **Propriétés**. Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.

### <a name="create-classes-and-define-paths"></a>Créer des classes et définir des chemins

1. Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. Ajoutez le code suivant à la ligne située juste au-dessus de la méthode `Main` pour spécifier les chemins d’accès aux éléments multimédias :

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. Créez des classes pour vos données d’entrée et prédictions.

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    `ImageData` est la classe de données d’images d’entrée, qui comprend les champs <xref:System.String> suivants :

    * `ImagePath` contient le nom du fichier image.
    * `Label` contient la valeur de l’étiquette d’image.

1. Ajoutez une nouvelle classe à votre projet pour `ImagePrediction` :

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    `ImagePrediction` est la classe de prédiction des images, qui comprend les champs suivants :

    * `Score` contient le pourcentage de confiance d’une classification d’image donnée.
    * `PredictedLabelValue` contient la valeur de l’étiquette de classification d’image prédite.

    `ImagePrediction` représente la classe utilisée pour la prédiction, une fois le modèle formé. Elle comporte une `string` (`ImagePath`) correspondant au chemin de l’image. Le `Label` est utilisé pour la réutilisation et l’apprentissage du modèle. L’attribut `PredictedLabelValue` est utilisé pendant la prédiction et l’évaluation. L’évaluation utilise une entrée avec les données d’apprentissage, les valeurs prédites et le modèle.

### <a name="initialize-variables-in-main"></a>Initialiser les variables dans Principal

1. Initialiser la variable `mlContext` avec une nouvelle instance de `MLContext`.  Remplacez la ligne `Console.WriteLine("Hello World!")` par le code suivant dans la méthode `Main` :

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

### <a name="create-a-struct-for-inception-model-parameters"></a>Créer un struct pour les paramètres de modèle d’Inception

1. Le modèle d’Inception a plusieurs paramètres que vous devez passer. Créez un struct pour mapper les valeurs de paramètre à des noms conviviaux avec le code suivant, juste après la méthode `Main()` :

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Créer une méthode d’utilitaire d’affichage

Étant donné que vous allez afficher les données d’image et les prédictions associées plusieurs fois, créez une méthode d’utilitaire d’affichage qui gère l’affichage des données d’image et des résultats de prédiction.

1. Créez la méthode `DisplayResults()` juste après le struct `InceptionSettings` avec le code suivant :

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. Renseignez le corps de la méthode `DisplayResults` :

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>Créez une méthode d’utilitaire de fichier .tsv

1. Créez la méthode `ReadFromTsv()` juste après la méthode `DisplayResults()`, en utilisant le code suivant :

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. Renseignez le corps de la méthode `ReadFromTsv` :

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    Le code analyse le fichier `tags.tsv` pour ajouter le chemin d’accès au fichier image pour la propriété `ImagePath` et le charger, ainsi que le `Label` dans un objet `ImageData`.

### <a name="create-a-method-to-make-a-prediction"></a>Créer une méthode pour effectuer une prédiction

1. Créez la méthode `ClassifySingleImage()` juste avant la méthode `DisplayResults()`, en utilisant le code suivant :

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Créez un objet `ImageData` qui contient le chemin d’accès qualifié complet et le nom du fichier image pour la seule `ImagePath`. Ajoutez le code suivant à la fin de la méthode `ClassifySingleImage()` :

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. Effectuez une seule prédiction en ajoutant le code suivant comme ligne suivante dans la méthode `ClassifySingleImage` :

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    Pour récupérer la prédiction, utilisez la méthode [Predict ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) . Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe. Il est acceptable d’utiliser dans des environnements à thread unique ou prototype. Pour améliorer les performances et la sécurité des threads dans les environnements de production, utilisez le service `PredictionEnginePool`, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d’objets [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pour une utilisation dans votre application. Consultez ce guide sur l' [utilisation de `PredictionEnginePool` dans une API Web ASP.net Core](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)

    > [!NOTE]
    > L’extension de service `PredictionEnginePool` est disponible en préversion.

1. Affichez le résultat de la prédiction à la fin de la méthode `ClassifySingleImage()` :

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>Construire le pipeline de modèle ML.NET

Un pipeline de modèle ML.NET est une chaîne d’estimateurs. Notez qu’aucune exécution ne se produit pendant la construction du pipeline. Les objets estimateur sont créés, mais ils ne sont pas exécutés.

1. Ajouter une méthode pour générer le modèle

    Cette méthode est le cœur du didacticiel. Il crée un pipeline pour le modèle et forme le pipeline pour produire le modèle ML.NET. Il évalue également le modèle par rapport à certaines données de test précédemment invisibles.

    Créez la méthode `GenerateModel()`, juste après le struct `InceptionSettings` et juste avant la méthode `DisplayResults()`, avec le code suivant :

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Ajoutez les estimateurs pour charger, redimensionner et extraire les pixels à partir des données de l’image :

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    Les données de l’image doivent être traitées dans le format attendu par le modèle TensorFlow. Dans ce cas, les images sont chargées en mémoire, redimensionnées à une taille cohérente et les pixels sont extraits dans un vecteur numérique.

1. Ajoutez l’estimateur pour charger le modèle TensorFlow et le noter :

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    Cette étape du pipeline charge le modèle TensorFlow en mémoire, puis traite le vecteur de valeurs de pixel via le réseau de modèles TensorFlow. L’application d’entrées à un modèle d’apprentissage profond et la génération d’une sortie à l’aide du modèle sont appelées **notation**. Lorsque vous utilisez le modèle dans son intégralité, la notation effectue une inférence ou une prédiction. 

    Dans ce cas, vous utilisez tout le modèle TensorFlow, à l’exception de la dernière couche, qui est la couche qui effectue l’inférence. La sortie de la couche avant est étiquetée `softmax_2_preactivation`. La sortie de cette couche est effectivement un vecteur de fonctionnalités qui caractérisent les images d’entrée d’origine.

    Ce vecteur de fonctionnalité généré par le modèle TensorFlow sera utilisé comme entrée pour un algorithme d’apprentissage ML.NET.

1. Ajoutez l’estimateur pour mapper les étiquettes de chaîne dans les données d’apprentissage aux valeurs de clés entières :

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    Le formateur ML.NET qui est ajouté ensuite requiert que ses étiquettes soient au format `key` plutôt qu’à des chaînes arbitraires. Une clé est un nombre qui a un mappage un-à-un à une valeur de chaîne.

1. Ajoutez l’algorithme d’apprentissage ML.NET :

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. Ajoutez l’estimateur pour mapper la valeur de clé prédite dans une chaîne :

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

1. Charger les données d’apprentissage à l’aide du wrapper [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) . Ajoutez le code suivant comme première ligne de la méthode `GenerateModel()` :

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView). `IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte). Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.

1. Effectuer l’apprentissage du modèle avec les données chargées ci-dessus :

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    La méthode `Fit()` forme votre modèle en appliquant le jeu de données d’apprentissage au pipeline.

## <a name="evaluate-the-accuracy-of-the-model"></a>Évaluer la précision du modèle

1. Chargez et transformez les données de test en ajoutant le code suivant à la ligne suivante de la méthode `GenerateModel` :

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Voici quelques exemples d’images que vous pouvez utiliser pour évaluer le modèle. Comme les données d’apprentissage, celles-ci doivent être chargées dans un `IDataView`, afin qu’elles puissent être transformées par le modèle.
   
1. Ajoutez le code suivant à la méthode `GenerateModel()` pour évaluer le modèle :

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    Une fois la prédiction définie, la méthode [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :

    * Évalue le modèle (compare les valeurs prédites avec le jeu de données de test `labels`).
    * Retourne les indicateurs de performances du modèle.

1. Afficher les métriques de précision du modèle

    Utilisez le code suivant pour afficher les métriques, partager les résultats et agir dessus :

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    Les indicateurs suivants sont évalués pour la classification d’images :

    * `Log-loss` (voir [Perte logarithmique](../resources/glossary.md#log-loss)). Vous voulez que la perte logarithmique soit aussi proche de zéro que possible.
    * `Per class Log-loss` . La perte logarithmique doit être aussi proche de zéro que possible.

1. Ajoutez le code suivant pour retourner le modèle entraîné à la ligne suivante :

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Exécutez l’application !

1. Ajoutez l’appel à `GenerateModel` dans la méthode `Main` après la création de la classe MLContext :

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. Ajoutez l’appel à la méthode `ClassifySingleImage()` comme ligne de code suivante dans la méthode `Main` :

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. Exécutez votre application console (Ctrl + F5). Vous devriez obtenir les résultats suivants.  Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.

    ```console
    =============== Training classification model ===============
    Image: broccoli.jpg predicted as: food with score: 0.976743
    Image: pizza.jpg predicted as: food with score: 0.9751652
    Image: pizza2.jpg predicted as: food with score: 0.9660203
    Image: teddy2.jpg predicted as: toy with score: 0.9748783
    Image: teddy3.jpg predicted as: toy with score: 0.9829691
    Image: teddy4.jpg predicted as: toy with score: 0.9868168
    Image: toaster.jpg predicted as: appliance with score: 0.9769174
    Image: toaster2.png predicted as: appliance with score: 0.9800823
    =============== Classification metrics ===============
    LogLoss is: 0.0228266745633507
    PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9625379

    C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
    Press any key to close this window . . .
    ```

Félicitations ! Vous avez maintenant correctement créé un modèle de Machine Learning pour la classification d’images en appliquant l’apprentissage de transfert à un modèle `TensorFlow` dans ML.NET.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Comprendre le problème
> * Incorporer le modèle TensorFlow pré-formé dans le pipeline ML.NET
> * Former et évaluer le modèle ML.NET
> * Classer une image de test

Consultez le référentiel GitHub d’exemples Machine Learning pour voir un exemple développé de classification d’images.
> [!div class="nextstepaction"]
> [Référentiel GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/)
