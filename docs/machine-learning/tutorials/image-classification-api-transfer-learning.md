---
title: 'Tutorial: Inspection visuelle automatisée à l’aide de l’apprentissage de transfert'
description: Ce tutoriel illustre comment utiliser l’apprentissage de transfert pour former un modèle d’apprentissage profond TensorFlow dans ML.NET en utilisant l’API de détection d’image pour classer les images de surfaces en béton comme fissurés ou non fissurés.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a050d7673f7ef00cf11d959d04e709222cb2be8f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607556"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Tutorial: Inspection visuelle automatisée à l’aide de l’apprentissage de transfert avec l’API de classification des images ML.NET

Apprenez à former un modèle d’apprentissage profond personnalisé à l’aide de l’apprentissage de transfert, un modèle TensorFlow préentraîné et l’API de classification d’image ML.NET pour classer les images de surfaces en béton comme fissurées ou non.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Comprendre le problème
> - En savoir plus sur ML.NET’API de classification d’image
> - Comprendre le modèle préentraîné
> - Utiliser l’apprentissage de transfert pour former un modèle personnalisé de classification d’image TensorFlow
> - Classer les images avec le modèle personnalisé

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou plus tard ou Visual Studio 2017 version 15.6 ou plus tard avec le ".NET Core cross-platform development" charge de travail installée.

## <a name="image-classification-transfer-learning-sample-overview"></a>Aperçu de l’échantillon d’apprentissage de transfert de classification d’image

Cet exemple est une application de console C .NET Core qui classe les images à l’aide d’un modèle TensorFlow d’apprentissage profond préentraîné. Vous trouverez le code de cet exemple dans le [dépôt dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) sur GitHub.

## <a name="understand-the-problem"></a>Comprendre le problème

La classification d’image est un problème de vision par ordinateur. La classification des images prend une image comme entrée et la classe dans une classe prescrite. Voici quelques scénarios où la classification des images est utile :

- Reconnaissance faciale
- Détection d’émotions
- Diagnostic médical
- Détection historique

Ce tutoriel forme un modèle personnalisé de classification d’image pour effectuer l’inspection visuelle automatisée des ponts pour identifier les structures qui sont endommagées par les fissures.

## <a name="mlnet-image-classification-api"></a>ML.NET Image Classification API

ML.NET fournit différentes façons d’effectuer la classification des images. Ce tutoriel applique l’apprentissage de transfert à l’aide de l’API de classification d’image. L’API de classification d’image utilise [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), une bibliothèque de bas niveau qui fournit des liaisons CMD pour l’API TensorFlow CMD.

## <a name="what-is-transfer-learning"></a>Qu’est-ce que l’apprentissage par transfert ?

L’apprentissage de transfert applique les connaissances acquises en résolvant un problème à un autre problème connexe.

La formation d’un modèle d’apprentissage profond à partir de zéro nécessite de définir plusieurs paramètres, une grande quantité de données de formation étiquetées, et une grande quantité de ressources de calcul (des centaines d’heures GPU). L’utilisation d’un modèle préentraîné avec l’apprentissage de transfert vous permet de raccourcir le processus de formation.

## <a name="training-process"></a>Processus de formation

L’API de classification d’image commence le processus de formation en chargeant un modèle tensorFlow préentraîné. Le processus de formation se compose de deux étapes :

1. Phase de goulot d’étranglement
2. Phase de formation

![Étapes de formation](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>Phase de goulot d’étranglement

Pendant la phase de goulot d’étranglement, l’ensemble des images de formation est chargé et les valeurs de pixels sont utilisées comme entrée, ou caractéristiques, pour les couches congelées du modèle préentraîné. Les couches gelées comprennent toutes les couches du réseau neuronal jusqu’à l’avant-dernière couche, connue officieusement sous le nom de couche de goulot d’étranglement. Ces couches sont appelées congelées parce qu’aucune formation ne se produira sur ces couches et que les opérations sont transmises. C’est à ces couches gelées que les modèles de niveau inférieur qui aident un modèle à différencier les différentes classes sont calculés. Plus le nombre de couches est élevé, plus cette étape est intensive sur le plan du calcul. Heureusement, puisqu’il s’agit d’un calcul ponctuen, les résultats peuvent être mis en cache et utilisés dans des exécutions ultérieures lors de l’expérimentation de différents paramètres.

### <a name="training-phase"></a>Phase de formation

Une fois que les valeurs de sortie de la phase de goulot d’étranglement sont calculées, elles sont utilisées comme entrée pour recycler la couche finale du modèle. Ce processus est itératif et s’exécute pour le nombre de fois spécifié par les paramètres du modèle. Au cours de chaque course, la perte et la précision sont évaluées. Ensuite, les ajustements appropriés sont effectués pour améliorer le modèle dans le but de minimiser la perte et de maximiser la précision. Une fois la formation terminée, deux formats de modèles sont en sortie. L’un d’eux est la `.pb` version `.zip` du modèle et l’autre est la ML.NET version sérialisée du modèle. Lorsque vous travaillez dans des environnements pris en `.zip` charge par ML.NET, il est recommandé d’utiliser la version du modèle. Toutefois, dans des environnements où ML.NET n’est pas `.pb` pris en charge, vous avez la possibilité d’utiliser la version.

## <a name="understand-the-pretrained-model"></a>Comprendre le modèle préentraîné

Le modèle préentraîné utilisé dans ce tutoriel est la variante de 101 couches du modèle V2 du réseau résiduel (ResNet). Le modèle original est formé pour classer les images en mille catégories. Le modèle prend comme entrée une image de taille 224 x 224 et produit les probabilités de classe pour chacune des classes sur qui il est formé. Une partie de ce modèle est utilisée pour former un nouveau modèle à l’aide d’images personnalisées pour faire des prédictions entre deux classes.

## <a name="create-console-application"></a>Création d’une application de console

Maintenant que vous avez une compréhension générale de l’apprentissage des transferts et de l’API de classification d’image, il est temps de construire l’application.

1. Créez une **application de console de base CMD .NET** appelée « DeepLearning_ImageClassification_Binary ».
1. Installer la version **Microsoft.ML** **1.4.0** NuGet Forfait:
    1. Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**.
    1. Choisissez «nuget.org» comme source de paquet.
    1. Sélectionnez l’onglet **Parcourir**.
    1. Vérifiez la case à cocher **prérelease Inclure.**
    1. Recherche de **Microsoft.ML**.
    1. Sélectionnez le bouton **Installer**.
    1. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.
    1. Répétez ces étapes pour la version **Microsoft.ML.Vision** **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, et **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.

### <a name="prepare-and-understand-the-data"></a>Préparer et comprendre les données

> [!NOTE]
> Les jeux de données pour ce tutoriel sont de Maguire, Marc; Dorafshan, Sattar; et Thomas, le juge Robert, "SDNET2018: A concrete crack image dataset for machine learning applications" (2018). Parcourez tous les Jeux de Données. Papier 48. https://digitalcommons.usu.edu/all_datasets/48

SDNET2018 est un ensemble de données d’images qui contient des annotations pour les structures en béton fissurées et non fissurées (ponts, murs et chaussée).

![Échantillons de ponts de dataset SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

Les données sont organisées en trois sous-directions :

- D contient des images de pont
- P contient des images de chaussée
- W contient des images murales

Chacune de ces sous-directions contient deux sous-directions préfixés supplémentaires :

- C est le préfixe utilisé pour les surfaces fissurées
- U est le préfixe utilisé pour les surfaces non encées

Dans ce tutoriel, seules les images de plate-forme de pont sont utilisées.

1. Téléchargez le [jeu de données](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) et unzip.
1. Créez un répertoire nommé « actifs » dans votre projet pour enregistrer vos fichiers de jeu de données.
1. Copiez les sous-directeurs *CD* et *UD* de l’annuaire récemment décompressé à l’annuaire *des actifs.*

### <a name="create-input-and-output-classes"></a>Créer des classes d’entrée et de sortie

1. Ouvrez le *fichier Program.cs* et `using` remplacez les relevés existants en haut du fichier par les éléments suivants :

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. Ci-dessous la `Program` classe en *Program.cs*, `ImageData`créer une classe appelée . Cette classe est utilisée pour représenter les données initialement chargées.

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData`contient les propriétés suivantes :

    - `ImagePath`est le chemin entièrement qualifié où l’image est stockée.
    - `Label`est la catégorie à laquelle appartient l’image. C’est la valeur à prévoir.

1. Créez des classes pour vos données d’entrée et de sortie

    1. Au-dessous de la `ImageData` classe, définissez le schéma `ModelInput`de vos données d’entrée dans une nouvelle classe appelée .

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput`contient les propriétés suivantes :

        - `Image`est `byte[]` la représentation de l’image. Le modèle s’attend à ce que les données d’image soient de ce type pour la formation.
        - `LabelAsKey`est la représentation `Label`numérique de la .
        - `ImagePath`est le chemin entièrement qualifié où l’image est stockée.
        - `Label`est la catégorie à laquelle appartient l’image. C’est la valeur à prévoir.

        Seulement `Image` `LabelAsKey` et sont utilisés pour former le modèle et faire des prédictions. Les `ImagePath` `Label` propriétés et les propriétés sont conservées pour plus de commodité pour accéder au nom et à la catégorie de fichier d’image d’origine.

    1. Ensuite, en `ModelInput` dessous de la classe, définissez le `ModelOutput`schéma de vos données de sortie dans une nouvelle classe appelée .

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput`contient les propriétés suivantes :

        - `ImagePath`est le chemin entièrement qualifié où l’image est stockée.
        - `Label`est la catégorie originale à laquelle appartient l’image. C’est la valeur à prévoir.
        - `PredictedLabel`est la valeur prédite par le modèle.

        Semblable `ModelInput`à , `PredictedLabel` seul le est nécessaire pour faire des prédictions car il contient la prédiction faite par le modèle. Les `ImagePath` `Label` propriétés et les propriétés sont conservées pour plus de commodité pour accéder au nom et à la catégorie de fichier d’image d’origine.

### <a name="create-workspace-directory"></a>Créer un répertoire d’espace de travail

Lorsque les données de formation et de validation ne changent pas souvent, il est recommandé de mettre en cache les valeurs de goulot d’étranglement calculées pour d’autres exécutions.

1. Dans votre projet, créez un nouvel annuaire appelé *espace de* travail `.pb` pour stocker les valeurs de goulot d’étranglement calculées et la version du modèle.

### <a name="define-paths-and-initialize-variables"></a>Définir les chemins et les variables d’initialisation

1. À `Main` l’intérieur de la méthode, définissez l’emplacement de vos actifs, les valeurs de goulot d’étranglement calculées et `.pb` la version du modèle.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. Initialiser `mlContext` la variable avec une nouvelle instance de [MLContext](xref:Microsoft.ML.MLContext).

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    La classe [MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation du mlContext crée un nouvel environnement ML.NET qui peut être partagé entre les objets de flux de travail de création de modèles. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

## <a name="load-the-data"></a>Chargement des données

### <a name="create-data-loading-utility-method"></a>Créer une méthode d’utilité de chargement de données

Les images sont stockées dans deux sous-directions. Avant de charger les données, elles doivent `ImageData` être formatées en une liste d’objets. Pour ce faire, `LoadImagesFromDirectory` créez `Main` la méthode ci-dessous la méthode.

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. À `LoadImagesDirectory` l’intérieur de l’ajouter le code suivant pour obtenir tous les chemins de fichier à partir des sous-directions:

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. Ensuite, itérer à travers chacun `foreach` des fichiers à l’aide d’une déclaration.

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. À `foreach` l’intérieur de la déclaration, vérifiez que les extensions de fichiers sont prises en charge. L’API de classification d’image prend en charge les formats JPEG et PNG.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. Ensuite, obtenir l’étiquette pour le fichier. Si `useFolderNameAsLabel` le paramètre `true`est défini, alors le répertoire parent où le fichier est enregistré est utilisé comme étiquette. Dans le cas contraire, il s’attend à ce que l’étiquette soit un préfixe du nom du fichier ou du nom du fichier lui-même.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. Enfin, créer une `ModelInput`nouvelle instance de .

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>Préparer les données

1. De retour `Main` dans la `LoadFromDirectory` méthode, utilisez la méthode d’utilité pour obtenir la liste des images utilisées pour la formation.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. Ensuite, chargez les [`IDataView`](xref:Microsoft.ML.IDataView) images [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) dans une méthode utilisant.

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. Les données sont chargées dans l’ordre où elles ont été lues dans les répertoires. Pour équilibrer les données, [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) mélangez-les en utilisant la méthode.

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. Les modèles d’apprentissage automatique s’attendent à ce que les données soient en format numérique. Par conséquent, certains prétraitement doivent être effectués sur les données avant la formation. Créez [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) un composé [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) de `LoadRawImageBytes` la et transforme. La `MapValueToKey` transformation prend la valeur `Label` catégorique dans la colonne, la convertit en valeur numérique `KeyType` et la stocke dans une nouvelle colonne appelée `LabelAsKey`. Le `LoadImages` prend les `ImagePath` valeurs de `imageFolder` la colonne avec le paramètre pour charger des images pour la formation.

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. Utilisez [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) la méthode pour appliquer `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) les [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) données sur les [`IDataView`](xref:Microsoft.ML.IDataView) données suivies de la méthode, qui renvoie une contenant les données pré-traitées.

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Pour former un modèle, il est important d’avoir un jeu de données de formation ainsi qu’un jeu de données de validation. Le modèle est formé sur l’ensemble de formation. La façon dont il fait des prédictions sur des données invisibles est mesurée par les performances par rapport à l’ensemble de validation. Sur la base des résultats de cette performance, le modèle apporte des ajustements à ce qu’il a appris dans un effort pour s’améliorer. L’ensemble de validation peut provenir soit du fractionnement de votre jeu de données d’origine, soit d’une autre source qui a déjà été mise de côté à cette fin. Dans ce cas, le jeu de données prétrafé par traité est divisé en ensembles de formation, de validation et de test.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    L’échantillon de code ci-dessus effectue deux fractionnements. Tout d’abord, les données pré-traitées sont divisées et 70% sont utilisées pour la formation tandis que les 30% restants sont utilisés pour validation. Ensuite, l’ensemble de validation de 30% est encore divisé en jeux de validation et de test où 90% est utilisé pour la validation et 10% est utilisé pour les tests.

    Une façon de penser à l’objectif de ces partitions de données est de passer un examen. Lorsque vous étudiez pour un examen, vous passez en revue vos notes, livres ou autres ressources pour obtenir une compréhension sur les concepts qui sont à l’examen. C’est à ça que s’adresse le train. Ensuite, vous pourriez passer un faux examen pour valider vos connaissances. C’est là que l’ensemble de validation est utile. Vous voulez vérifier si vous avez une bonne compréhension des concepts avant de passer l’examen réel. Sur la base de ces résultats, vous prenez note de ce que vous vous êtes trompé ou ne comprenait pas bien et d’intégrer vos changements que vous examinez pour l’examen réel. Enfin, vous passerez l’examen. C’est pour cela que sert l’ensemble de test. Vous n’avez jamais vu les questions qui sont à l’examen et utilisez maintenant ce que vous avez appris de la formation et de la validation pour appliquer vos connaissances à la tâche à accomplir.

1. Attribuez les partitions à leurs valeurs respectives pour les données de train, de validation et de test.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Définir le pipeline de formation

La formation modèle se compose d’un couple d’étapes. Tout d’abord, l’API de classification d’image est utilisé pour former le modèle. Ensuite, les étiquettes codées dans la `PredictedLabel` colonne sont converties `MapKeyToValue` à leur valeur catégorique d’origine à l’aide de la transformation.

1. Créez une nouvelle variable pour stocker un ensemble `ImageClassificationTrainer`de paramètres requis et facultatifs pour un .

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    Un `ImageClassificationTrainer` prend plusieurs paramètres facultatifs :

    - `FeatureColumnName`est la colonne qui est utilisée comme entrée pour le modèle.
    - `LabelColumnName`est la colonne pour la valeur à prévoir.
    - `ValidationSet`est [`IDataView`](xref:Microsoft.ML.IDataView) la contenant des données de validation.
    - `Arch`définit laquelle des architectures modèles préentraînées à utiliser. Ce tutoriel utilise la variante 101 couches du modèle ResNetv2.
    - `MetricsCallback`lie une fonction pour suivre les progrès pendant l’entraînement.
    - `TestOnTrainSet`indique au modèle de mesurer les performances par rapport à l’ensemble de formation lorsqu’aucun ensemble de validation n’est présent.
    - `ReuseTrainSetBottleneckCachedValues`indique au modèle s’il faut utiliser les valeurs mises en cache de la phase de goulot d’étranglement dans les exécutions suivantes. La phase de goulot d’étranglement est un calcul unique qui est d’une intensité de calcul la première fois qu’il est effectué. Si les données de formation ne changent pas et que vous souhaitez expérimenter à l’aide d’un nombre différent d’époques ou de la taille du lot, l’utilisation des valeurs mises en cache réduit considérablement le temps nécessaire pour former un modèle.
    - `ReuseValidationSetBottleneckCachedValues`est similaire `ReuseTrainSetBottleneckCachedValues` à celle que dans ce cas, c’est pour le jeu de données de validation.
    - `WorkspacePath`définit l’annuaire où stocker les valeurs de `.pb` goulot d’étranglement calculées et la version du modèle.

1. Définir [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) le pipeline de formation `mapLabelEstimator` qui `ImageClassificationTrainer`se compose à la fois de la et le .

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. Utilisez [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) la méthode pour former votre modèle.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>Utiliser le modèle

Maintenant que vous avez formé votre modèle, il est temps de l’utiliser pour classer les images.

Ci-dessous la `Main` méthode, créez `OutputPrediction` une nouvelle méthode utilitaire appelée pour afficher les informations de prédiction dans la console.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>Classer une seule image

1. Ajoutez une nouvelle `ClassifySingleImage` méthode `Main` appelée ci-dessous la méthode pour faire et sortir une seule prédiction d’image.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Créez [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) une `ClassifySingleImage` méthode à l’intérieur de la méthode. Il [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) s’agit d’une API pratique, qui vous permet de passer dedans et d’effectuer une prédiction sur une seule instance de données.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. Pour accéder `ModelInput` à une `data` [`IDataView`](xref:Microsoft.ML.IDataView) seule [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) instance, [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) convertir le en une utilisation de la méthode, puis obtenir la première observation.

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. Utilisez [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) la méthode pour classer l’image.

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. Sortie de la prédiction `OutputPrediction` à la console avec la méthode.

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. À `Main` l’intérieur `ClassifySingleImage` de la méthode, appelez en utilisant l’ensemble de test d’images.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>Classer plusieurs images

1. Ajoutez une nouvelle `ClassifyImages` méthode `ClassifySingleImage` appelée ci-dessous la méthode pour faire et sortir plusieurs prédictions d’image.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Créez [`IDataView`](xref:Microsoft.ML.IDataView) un contenant les [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) prédictions en utilisant la méthode. Ajoutez le code suivant dans la méthode `ClassifyImages`.

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. Afin d’itérer sur les prédictions, [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) convertir [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) le `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) en une utilisation de la méthode, puis obtenir les 10 premières observations.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. Itérer et produire les étiquettes originales et prévues pour les prédictions.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. Enfin, à `Main` l’intérieur de la méthode, appelez `ClassifyImages` en utilisant l’ensemble de test d’images.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>Exécution de l'application

Exécutez votre application console. La sortie devrait être similaire à celle ci-dessous. Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté. Pour la brièveté, la sortie a été condensée.

**Phase de goulot d’étranglement**

Aucune valeur n’est imprimée pour le nom `byte[]` de l’image parce que les images sont chargées car il n’y a donc pas de nom d’image à afficher.

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

**Classer la sortie d’images**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

Lors de l’inspection de l’image *7001-220.jpg,* vous pouvez voir qu’il n’est en fait pas fissuré.

![Image de jeu de données SDNET2018 utilisée pour la prédiction](./media/image-classification-api-transfer-learning/predictedimage.jpg)

Félicitations ! Vous avez maintenant construit avec succès un modèle d’apprentissage profond pour classer les images.

### <a name="improve-the-model"></a>Améliorer le modèle

Si vous n’êtes pas satisfait des résultats de votre modèle, vous pouvez essayer d’améliorer ses performances en essayant certaines des approches suivantes :

- **Plus de données**: Plus un modèle apprend d’exemples, mieux il fonctionne. Téléchargez le [jeu de données SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) complet et utilisez-le pour vous entraîner.
- **Augmenter les données**: Une technique courante pour ajouter de la variété aux données est d’augmenter les données en prenant une image et en appliquant différentes transformations (rotation, flip, shift, crop). Cela ajoute des exemples plus variés pour le modèle à apprendre.
- **Entraînez-vous plus longtemps**: Plus vous vous entraînez, plus le modèle sera à l’écoute. L’augmentation du nombre d’époques peut améliorer les performances de votre modèle.
- **Expérimentez avec les hyper-paramètres**: En plus des paramètres utilisés dans ce tutoriel, d’autres paramètres peuvent être réglés pour améliorer potentiellement les performances. Changer le taux d’apprentissage, qui détermine l’ampleur des mises à jour apportées au modèle après chaque époque peut améliorer les performances.
- **Utilisez une architecture de modèle différente**: Selon vos données, le modèle qui peut le mieux apprendre ses fonctionnalités peut différer. Si vous n’êtes pas satisfait des performances de votre modèle, essayez de changer l’architecture.

### <a name="additional-resources"></a>Ressources supplémentaires

- [Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez appris à construire un modèle d’apprentissage profond personnalisé en utilisant l’apprentissage de transfert, un modèle de classification d’image pré-formé TensorFlow et l’API de classification d’image ML.NET pour classer des images de surfaces en béton comme fissurées ou non.

Passez au tutoriel suivant pour en savoir plus.

> [!div class="nextstepaction"]
> [Détection d’objets](object-detection-onnx.md)
