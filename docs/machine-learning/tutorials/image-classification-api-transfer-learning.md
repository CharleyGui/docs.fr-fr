---
title: 'Didacticiel : inspection visuelle automatisée à l’aide de l’apprentissage de transfert'
description: Ce didacticiel explique comment utiliser l’apprentissage de transfert pour former un modèle d’apprentissage profond TensorFlow dans ML.NET à l’aide de l’API de détection d’images pour classer les images de surfaces concrètes comme fissurées ou non fissurées.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: eb61ad85580310c7becc2a1a2237efe188fbecf0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794587"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Didacticiel : inspection visuelle automatisée à l’aide de l’apprentissage de transfert avec l’API de classification d’image ML.NET

Apprenez à former un modèle d’apprentissage approfondi personnalisé à l’aide de l’apprentissage de transfert, un modèle TensorFlow préformé et l’API de classification d’image ML.NET pour classer les images de surfaces concrètes comme fissurées ou non.

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
>
> - Comprendre le problème
> - En savoir plus sur l’API de classification d’image ML.NET
> - Comprendre le modèle préformé
> - Utilisation de l’apprentissage de transfert pour l’apprentissage d’un modèle de classification d’image TensorFlow personnalisé
> - Classer les images avec le modèle personnalisé

## <a name="prerequisites"></a>Prerequisites

- [Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .Net Core » installée.

## <a name="image-classification-transfer-learning-sample-overview"></a>Vue d’ensemble de l’exemple d’apprentissage de transfert de classification d’image

Cet exemple est une C# application console .net core qui classe les images à l’aide d’un modèle TensorFlow d’apprentissage profond préformé. Vous trouverez le code de cet exemple dans le [dépôt dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) sur GitHub.

## <a name="understand-the-problem"></a>Comprendre le problème

La classification d’images est un problème de vision par ordinateur. La classification d’image prend une image en tant qu’entrée et la classe dans une classe prescrite. Voici quelques scénarios où la classification d’images est utile :

- Reconnaissance faciale
- Détection d’émotion
- Diagnostic médical
- Détection du repère géographique

Ce didacticiel forme un modèle de classification d’image personnalisé pour effectuer une inspection visuelle automatisée des ponts de pont afin d’identifier les structures qui sont endommagées par des fissures.

## <a name="mlnet-image-classification-api"></a>API de classification d’image ML.NET

ML.NET fournit différentes façons d’effectuer la classification des images. Ce didacticiel applique l’apprentissage de transfert à l’aide de l’API de classification d’image. L’API de classification d’image utilise [TensorFlow.net](https://github.com/SciSharp/TensorFlow.NET), une bibliothèque de bas niveau qui fournit C# des liaisons pour l’API C++ TensorFlow.

## <a name="what-is-transfer-learning"></a>Qu’est-ce que l’apprentissage par transfert ?

Le transfert d’apprentissage applique les connaissances acquises en résolvant un problème à un autre problème.

La formation d’un modèle d’apprentissage profond à partir de zéro requiert la définition de plusieurs paramètres, une grande quantité de données d’apprentissage étiquetées et une grande quantité de ressources de calcul (des centaines d’heures GPU). L’utilisation d’un modèle préformé et de l’apprentissage de transfert vous permet de raccourcir le processus de formation.

## <a name="training-process"></a>Processus d’apprentissage

L’API de classification d’image démarre le processus d’apprentissage en chargeant un modèle TensorFlow préformé. Le processus d’apprentissage se compose de deux étapes :

1. Phase de goulot d’étranglement
2. Phase de formation

![Étapes de formation](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>Phase de goulot d’étranglement

Pendant la phase de goulot d’étranglement, l’ensemble des images de formation est chargé et les valeurs de pixel sont utilisées comme entrées ou caractéristiques pour les couches figées du modèle préformé. Les couches figées incluent toutes les couches du réseau neuronal jusqu’à l’avant-dernière couche, de manière informellement connue sous le nom de couche de goulot d’étranglement. Ces couches sont désignées comme étant figées, car aucune formation ne se produit sur ces couches et les opérations sont directes. C’est à ces couches figées où les modèles de niveau inférieur qui aident un modèle à différencier entre les différentes classes sont calculés. Plus le nombre de couches est élevé, plus cette étape est gourmande en calculs. Heureusement, étant donné qu’il s’agit d’un calcul unique, les résultats peuvent être mis en cache et utilisés ultérieurement lors de l’expérimentation avec des paramètres différents.

### <a name="training-phase"></a>Phase de formation

Une fois les valeurs de sortie de la phase de goulot d’étranglement calculées, elles sont utilisées comme entrée pour reformer la couche finale du modèle. Ce processus est itératif et s’exécute pendant le nombre de fois spécifié par les paramètres de modèle. Lors de chaque exécution, la perte et la précision sont évaluées. Ensuite, les ajustements appropriés sont effectués pour améliorer le modèle avec l’objectif de réduire la perte et d’optimiser la précision. Une fois l’apprentissage terminé, deux formats de modèle sont générés. L’une d’entre elles est la version `.pb` du modèle et l’autre est la version sérialisée `.zip` ML.NET du modèle. Quand vous travaillez dans des environnements pris en charge par ML.NET, il est recommandé d’utiliser la version `.zip` du modèle. Toutefois, dans les environnements où ML.NET n’est pas pris en charge, vous avez la possibilité d’utiliser la version `.pb`.

## <a name="understand-the-pretrained-model"></a>Comprendre le modèle préformé

Le modèle préformé utilisé dans ce didacticiel est la variante de couche 101 du modèle de réseau résiduel (ResNet) v2. Le modèle d’origine est formé pour classer les images en milliers de catégories. Le modèle prend comme entrée une image de taille 224 x 224 et génère les probabilités de la classe pour chacune des classes sur lesquelles il est formé. Une partie de ce modèle est utilisée pour l’apprentissage d’un nouveau modèle à l’aide d’images personnalisées pour effectuer des prédictions entre deux classes.

## <a name="create-console-application"></a>Créer une application console

Maintenant que vous avez une compréhension générale de la formation de transfert et de l’API de classification d’image, il est temps de générer l’application.

1. Créez une  **C# application console .net Core** appelée « DeepLearning_ImageClassification_Binary ».
1. Installez le package NuGet **1.4.0** version **Microsoft.ml** :
    1. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.
    1. Choisissez « nuget.org » comme source du package.
    1. Sélectionnez l’onglet **Parcourir**.
    1. Cochez la case **inclure la version préliminaire** .
    1. Recherchez **Microsoft.ml**.
    1. Sélectionnez le bouton **Installer**.
    1. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.
    1. Répétez ces étapes pour les packages NuGet **Microsoft. ml. vision** version **1.4.0**, **SciSharp. TensorFlow. Redist** version **1.15.0**et **Microsoft. ml. ImageAnalytics** version **1.4.0** .

### <a name="prepare-and-understand-the-data"></a>Préparer et comprendre les données

> [!NOTE]
> Les jeux de données de ce didacticiel proviennent de Maguire, Marc ; Dorafshan, Sattar; et Thomas, Robert J., « SDNET2018 : jeu de données d’image de piratage concret pour les applications de Machine Learning » (2018). Parcourez tous les jeux de données. Papier 48. https://digitalcommons.usu.edu/all_datasets/48

SDNET2018 est un jeu de données d’image qui contient des annotations pour les structures concrètes fissurées et non fissurées (ponts, murs et chaussées de pont).

![Exemples de jeux de données de pont SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

Les données sont organisées en trois sous-répertoires :

- D contient des images de pont de pont
- P contient des images de chaussée
- W contient des images de mur

Chacun de ces sous-répertoires contient deux sous-répertoires préfixés supplémentaires :

- C est le préfixe utilisé pour les surfaces fissurées
- U est le préfixe utilisé pour les surfaces non craquées

Dans ce didacticiel, seules les images de pont de pont sont utilisées.

1. Téléchargez le [jeu de données](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) et décompressez.
1. Créez un répertoire nommé « ressources » dans votre projet pour enregistrer les fichiers de votre jeu de données.
1. Copiez les sous-répertoires *CD* et *ud* à partir du répertoire décompressé récemment vers le répertoire *Assets* .

### <a name="create-input-and-output-classes"></a>Créer des classes d’entrée et de sortie

1. Ouvrez le fichier *Program.cs* et remplacez les instructions `using` existantes en haut du fichier par les éléments suivants :

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. Sous la classe `Program` dans *Program.cs*, créez une classe appelée `ImageData`. Cette classe est utilisée pour représenter les données initialement chargées.

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData` contient les propriétés suivantes :

    - `ImagePath` est le chemin d’accès complet où l’image est stockée.
    - `Label` est la catégorie à laquelle l’image appartient. Il s’agit de la valeur à prédire.

1. Créer des classes pour vos données d’entrée et de sortie

    1. Sous la classe `ImageData`, définissez le schéma de vos données d’entrée dans une nouvelle classe appelée `ModelInput`.

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput` contient les propriétés suivantes :

        - `Image` est la représentation `byte[]` de l’image. Le modèle s’attend à ce que les données de l’image soient de ce type pour l’apprentissage.
        - `LabelAsKey` est la représentation numérique du `Label`.
        - `ImagePath` est le chemin d’accès complet où l’image est stockée.
        - `Label` est la catégorie à laquelle l’image appartient. Il s’agit de la valeur à prédire.

        Seuls les `Image` et les `LabelAsKey` sont utilisés pour l’apprentissage du modèle et la création de prédictions. Les propriétés `ImagePath` et `Label` sont conservées pour plus de commodité afin d’accéder au nom et à la catégorie du fichier image d’origine.

    1. Ensuite, sous la classe `ModelInput`, définissez le schéma de vos données de sortie dans une nouvelle classe appelée `ModelOutput`.

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput` contient les propriétés suivantes :

        - `ImagePath` est le chemin d’accès complet où l’image est stockée.
        - `Label` est la catégorie d’origine à laquelle l’image appartient. Il s’agit de la valeur à prédire.
        - `PredictedLabel` est la valeur prédite par le modèle.

        Comme pour `ModelInput`, seul le `PredictedLabel` est requis pour effectuer des prédictions, car il contient la prédiction effectuée par le modèle. Les propriétés `ImagePath` et `Label` sont conservées pour plus de commodité afin d’accéder au nom et à la catégorie du fichier image d’origine.

### <a name="create-workspace-directory"></a>Créer le répertoire de l’espace de travail

Lorsque les données d’apprentissage et de validation ne changent pas souvent, il est recommandé de mettre en cache les valeurs de goulot d’étranglement calculées pour d’autres exécutions.

1. Dans votre projet, créez un répertoire appelé *espace de travail* pour stocker les valeurs de goulot d’étranglement calculées et la version `.pb` du modèle.

### <a name="define-paths-and-initialize-variables"></a>Définir des chemins d’accès et initialiser des variables

1. À l’intérieur de la méthode `Main`, définissez l’emplacement de vos ressources, les valeurs de goulot d’étranglement calculées et la version `.pb` du modèle.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. Initialisez la variable `mlContext` avec une nouvelle instance de [MLContext](xref:Microsoft.ML.MLContext).

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    La classe [MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ml.net, et l’initialisation de MLContext crée un nouvel environnement ml.net qui peut être partagé entre les objets de flux de travail de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

## <a name="load-the-data"></a>Charger les données

### <a name="create-data-loading-utility-method"></a>Créer une méthode utilitaire de chargement de données

Les images sont stockées dans deux sous-répertoires. Avant de charger les données, celles-ci doivent être mises en forme dans une liste d’objets `ImageData`. Pour ce faire, créez la méthode `LoadImagesFromDirectory` sous la méthode `Main`.

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. Dans le `LoadImagesDirectory` ajoutez le code suivant pour récupérer tous les chemins d’accès aux fichiers à partir des sous-répertoires :

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. Ensuite, itérez au sein de chacun des fichiers à l’aide d’une instruction `foreach`.

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. À l’intérieur de l’instruction `foreach`, vérifiez que les extensions de fichier sont prises en charge. L’API de classification d’image prend en charge les formats JPEG et PNG.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. Ensuite, récupérez le nom du fichier. Si le paramètre `useFolderNameAsLabel` est défini sur `true`, le répertoire parent où le fichier est enregistré est utilisé comme étiquette. Dans le cas contraire, il s’attend à ce que l’étiquette soit un préfixe du nom de fichier ou du nom de fichier lui-même.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. Enfin, créez une nouvelle instance de `ModelInput`.

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>Préparer les données

1. De retour dans la méthode `Main`, utilisez la méthode de l’utilitaire `LoadFromDirectory` pour obtenir la liste des images utilisées pour l’apprentissage.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. Ensuite, chargez les images dans un [`IDataView`](xref:Microsoft.ML.IDataView) à l’aide de la méthode [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) .

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. Les données sont chargées dans l’ordre dans lequel elles ont été lues à partir des répertoires. Pour équilibrer les données, utilisez la méthode [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) .

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. Les modèles d’apprentissage automatique s’attendent à ce que l’entrée soit au format numérique. Par conséquent, un prétraitement doit être effectué sur les données avant l’apprentissage. Créez un [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) constitué du [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) et des transformations de `LoadRawImageBytes`. La transformation `MapValueToKey` prend la valeur catégorique dans la colonne `Label`, la convertit en valeur de `KeyType` numérique et la stocke dans une nouvelle colonne appelée `LabelAsKey`. Le `LoadImages` prend les valeurs de la colonne `ImagePath` avec le paramètre `imageFolder` pour charger des images pour l’apprentissage.

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. Utilisez la méthode [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) pour appliquer les données au `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) suivi de la méthode [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) , qui retourne un [`IDataView`](xref:Microsoft.ML.IDataView) contenant les données prétraitées.

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Pour effectuer l’apprentissage d’un modèle, il est important de disposer d’un jeu de données d’apprentissage, ainsi que d’un jeu de données de validation. Le modèle est formé dans le jeu d’apprentissage. La façon dont il effectue des prédictions sur les données invisibles est mesurée en fonction des performances par rapport au jeu de validation. En fonction des résultats de ces performances, le modèle apporte des ajustements à ce qu’il a appris dans un effort d’amélioration. Le jeu de validation peut provenir soit du fractionnement de votre jeu de données d’origine, soit d’une autre source qui a déjà été réservée à cet effet. Dans ce cas, le jeu de données préalablement traité est divisé en jeux d’apprentissage, de validation et de test.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    L’exemple de code ci-dessus effectue deux fractionnements. Tout d’abord, les données prétraitées sont fractionnées et 70% est utilisé pour l’apprentissage, tandis que les 30% restants sont utilisés pour la validation. Le jeu de validation de 30% est ensuite divisé en jeux de validation et de test où 90% est utilisé pour la validation et 10% sont utilisés pour le test.

    Un moyen de réfléchir à l’objectif de ces partitions de données consiste à effectuer un examen. Lorsque vous étudiez un examen, vous examinez vos notes, livres ou autres ressources pour comprendre les concepts qui sont à l’examen. Il s’agit de ce à quoi sert l’ensemble de rames. Ensuite, vous pouvez effectuer un examen fictif pour valider vos connaissances. C’est là que le jeu de validation est utile. Vous souhaitez vérifier si vous avez une bonne compréhension des concepts avant d’effectuer l’examen réel. En fonction de ces résultats, vous prenez note de ce que vous avez trouvé ou que vous n’avez pas bien compris et incorporez vos modifications à mesure que vous l’examinez pour l’examen réel. Enfin, vous prenez l’examen. C’est pour cela que le jeu de test est utilisé. Vous n’avez jamais vu les questions qui sont à l’examen et utilisez maintenant ce que vous avez appris de la formation et de la validation pour appliquer vos connaissances à la tâche en cours.

1. Affectez les partitions à leurs valeurs respectives pour les données d’apprentissage, de validation et de test.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Définir le pipeline d’apprentissage

L’apprentissage du modèle se compose de deux étapes. Tout d’abord, l’API de classification d’image est utilisée pour l’apprentissage du modèle. Ensuite, les étiquettes encodées dans la colonne `PredictedLabel` sont reconverties en leur valeur catégorique d’origine à l’aide de la transformation `MapKeyToValue`.

1. Créez une variable pour stocker un ensemble de paramètres obligatoires et facultatifs pour un `ImageClassificationTrainer`. 

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    Un `ImageClassificationTrainer` prend plusieurs paramètres facultatifs :

    - `FeatureColumnName` est la colonne utilisée comme entrée pour le modèle.
    - `LabelColumnName` est la colonne de la valeur à prédire.
    - `ValidationSet` est le [`IDataView`](xref:Microsoft.ML.IDataView) contenant les données de validation.
    - `Arch` définit les architectures de modèle préformées à utiliser. Ce didacticiel utilise la variante de couche 101 du modèle ResNetv2.
    - `MetricsCallback` lie une fonction pour suivre la progression au cours de l’apprentissage.
    - `TestOnTrainSet` indique au modèle de mesurer les performances par rapport au jeu d’apprentissage quand aucun jeu de validation n’est présent.
    - `ReuseTrainSetBottleneckCachedValues` indique au modèle s’il faut utiliser les valeurs mises en cache à partir de la phase de goulot d’étranglement lors des exécutions suivantes. La phase de goulot d’étranglement est un calcul direct unique qui exige beaucoup de ressources de calcul la première fois qu’il est exécuté. Si les données d’apprentissage ne changent pas et que vous souhaitez expérimenter à l’aide d’un nombre d’époques ou d’une taille de lot différent, l’utilisation de valeurs mises en cache réduit considérablement le temps nécessaire pour l’apprentissage d’un modèle.
    - `ReuseValidationSetBottleneckCachedValues` est semblable à `ReuseTrainSetBottleneckCachedValues` uniquement dans ce cas, il s’agit du jeu de données de validation.
    - `WorkspacePath` définit le répertoire dans lequel stocker les valeurs de goulot d’étranglement calculées et la version de `.pb` du modèle.

1. Définissez le pipeline d’apprentissage [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) qui se compose des `mapLabelEstimator` et des `ImageClassificationTrainer`.

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. Utilisez la méthode [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) pour effectuer l’apprentissage de votre modèle.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>Utiliser le modèle

Maintenant que vous avez formé votre modèle, il est temps de l’utiliser pour classifier les images.

Sous la méthode `Main`, créez une nouvelle méthode utilitaire appelée `OutputPrediction` pour afficher les informations de prédiction dans la console.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>Classer une seule image

1. Ajoutez une nouvelle méthode appelée `ClassifySingleImage` sous la méthode `Main` pour créer et générer une prédiction d’image unique.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Créez un [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) à l’intérieur de la méthode `ClassifySingleImage`. L' [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet de transmettre, puis d’effectuer une prédiction sur une seule instance de données.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. Pour accéder à une instance de `ModelInput` unique, convertissez le `data` [`IDataView`](xref:Microsoft.ML.IDataView) en [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) à l’aide de la méthode [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) , puis récupérez la première observation.

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. Utilisez la méthode [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) pour classifier l’image.

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. Sortie de la prédiction vers la console avec la méthode `OutputPrediction`.

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. À l’intérieur de la méthode `Main`, appelez `ClassifySingleImage` à l’aide du jeu de test d’images.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>Classer plusieurs images

1. Ajoutez une nouvelle méthode appelée `ClassifyImages` sous la méthode `ClassifySingleImage` pour créer et générer plusieurs prédictions d’image.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Créez un [`IDataView`](xref:Microsoft.ML.IDataView) contenant les prédictions à l’aide de la méthode [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) . Ajoutez le code suivant dans la méthode `ClassifyImages`.

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. Pour itérer au sein des prédictions, convertissez le `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) en [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) à l’aide de la méthode [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) , puis récupérez les 10 premières observations.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. Itère et génère les étiquettes d’origine et prédites pour les prédictions.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. Enfin, à l’intérieur de la méthode `Main`, appelez `ClassifyImages` à l’aide du jeu de test d’images.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>Exécuter l'application

Exécutez votre application console. La sortie doit ressembler à ce qui suit. Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté. Par souci de concision, la sortie a été condensée.

**Phase de goulot d’étranglement**

Aucune valeur n’est imprimée pour le nom de l’image car les images sont chargées en tant que `byte[]` il n’y a donc aucun nom d’image à afficher.

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

**Phase de formation**

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

**Résultat de la classification des images**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

Lors de l’inspection de l’image *7001 -220. jpg* , vous pouvez constater qu’elle n’est pas piratée.

![Image du jeu de données SDNET2018 utilisée pour la prédiction](./media/image-classification-api-transfer-learning/predictedimage.jpg)

Félicitations ! Vous avez maintenant créé avec succès un modèle d’apprentissage profond pour la classification des images.

### <a name="improve-the-model"></a>Améliorer le modèle

Si vous n’êtes pas satisfait des résultats de votre modèle, vous pouvez essayer d’améliorer ses performances en essayant certaines des approches suivantes :

- **Plus de données**: plus d’exemples d’apprentissage d’un modèle, mieux c’est. Téléchargez le [jeu de données SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) complet et utilisez-le pour effectuer l’apprentissage.
- **Augmenter les données**: une technique courante pour ajouter de la diversité aux données consiste à augmenter les données en acceptant une image et en appliquant des transformations différentes (rotation, retournement, déplacement, rognage). Cela permet d’obtenir des exemples variés pour le modèle.
- **Formation pour une durée plus longue**: plus vous exercez de temps, plus le modèle est ajusté. L’augmentation du nombre d’époques peut améliorer les performances de votre modèle.
- **Expérimentez avec les hyperparamètres**: en plus des paramètres utilisés dans ce didacticiel, d’autres paramètres peuvent être réglés pour améliorer les performances. La modification du taux d’apprentissage, qui détermine l’amplitude des mises à jour apportées au modèle après chaque époque peut améliorer les performances.
- **Utilisez une architecture de modèle différente**: selon l’aspect de vos données, le modèle qui peut mieux apprendre ses fonctionnalités peut être différent. Si vous n’êtes pas satisfait des performances de votre modèle, essayez de modifier l’architecture.

### <a name="additional-resources"></a>Ressources supplémentaires

- [Apprentissage profond et machine learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).

## <a name="next-steps"></a>Étapes suivantes :

Dans ce didacticiel, vous avez appris à créer un modèle d’apprentissage profond personnalisé à l’aide de l’apprentissage de transfert, d’un modèle TensorFlow de classification d’image préformée et de l’API de classification d’image ML.NET pour classer les images de surfaces concrètes comme fissurées ou non.

Passez au tutoriel suivant pour en savoir plus.

> [!div class="nextstepaction"]
> [Détection d’objet](object-detection-onnx.md)
