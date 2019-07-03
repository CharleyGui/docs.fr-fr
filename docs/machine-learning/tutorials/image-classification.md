---
title: 'Tutoriel : Reformer le classifieur d’images TensorFlow - Apprentissage par transfert'
description: Apprenez à reformer un modèle de classification des images TensorFlow avec apprentissage par transfert et ML.NET. Le modèle d’origine a été formé pour classer des images individuelles. Après reformation, le nouveau modèle organise les images en grandes catégories.
ms.date: 06/12/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 2ad9e71f572cb694897fd12ecbb15da069afe338
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67026086"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a>Tutoriel : Reformer un classifieur d’images TensorFlow avec apprentissage par transfert et ML.NET

Apprenez à reformer un modèle de classification des images TensorFlow avec apprentissage par transfert et ML.NET. Le modèle d’origine a été formé pour classer des images individuelles. Après reformation, le nouveau modèle organise les images en grandes catégories. 

Pour entraîner un modèle de [Classification d’images](https://en.wikipedia.org/wiki/Outline_of_object_recognition) à partir de zéro, il faut définir des millions de paramètres, disposer d’une multitude de données d’apprentissage étiquetées et posséder une grande quantité de ressources de calcul (des centaines d’heures GPU). S’il n’est pas aussi efficace que l’apprentissage d’un modèle personnalisé à partir de zéro, l’apprentissage par transfert permet de raccourcir ce processus : il s’agit de travailler avec des milliers (et non des millions) d’images étiquetées et de créer assez vite un modèle personnalisé (en une heure sur un ordinateur sans GPU).

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> * Comprendre le problème
> * Réutiliser et paramétrer le modèle préentraîné
> * Classer des images

## <a name="what-is-transfer-learning"></a>Qu’est-ce que l’apprentissage par transfert ?

Et si vous pouviez réutiliser un modèle déjà entraîné pour résoudre un problème et réentraîner une partie ou la totalité de ses couches de sorte qu’il résolve un problème similaire ? Cette technique se nomme [apprentissage par transfert](https://en.wikipedia.org/wiki/Transfer_learning).

## <a name="image-classification-sample-overview"></a>Vue d’ensemble de l’exemple de classification d’images

L’exemple est une application console qui s’appuie sur ML.NET pour créer un classifieur d’images en réutilisant un modèle préentraîné avec un petit volume de données d’apprentissage.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).

## <a name="prerequisites"></a>Prérequis

* [Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .Net Core » installée.

* Package NuGet Microsoft.ML 1.0.0
* Package NuGet Microsoft.ML.ImageAnalytics 1.0.0
* Package NuGet Microsoft.ML.TensorFlow 0.12.0

* [Le fichier .zip du répertoire de ressources du tutoriel](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [Le modèle Machine Learning InceptionV3](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a>Sélectionner la tâche d’apprentissage automatique appropriée

Le [Deep Learning](https://en.wikipedia.org/wiki/Deep_learning) est un sous-ensemble du Machine Learning, qui révolutionne des domaines comme la Vision par ordinateur et la Reconnaissance vocale.

L’entraînement des modèles Deep Learning s’effectue à l’aide de grands ensembles de [données étiquetées](https://en.wikipedia.org/wiki/Labeled_data) et de [réseaux neuronaux](https://en.wikipedia.org/wiki/Artificial_neural_network) comportant plusieurs couches d’apprentissage. Le Deep Learning présente différentes caractéristiques :

* Il fonctionne mieux sur certaines tâches comme la Vision par ordinateur.

* Il marche bien avec d’énormes volumes de données.

La classification d’images est une tâche courante de Machine Learning qui permet de classer automatiquement des images dans plusieurs catégories, par exemple :

* détecter ou non la présence d’un visage dans une image ;
* détecter des chats ou des chiens.

 On peut également, comme dans les images suivantes, déterminer si une image représente un aliment, un jouet ou un appareil :

![image de pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![image de nounours](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![image de grille-pain](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Les images précédentes appartiennent à Wikimedia Commons et sont attribuées ainsi :
>
> * « 220px-Pepperoni_pizza.jpg », domaine public, https://commons.wikimedia.org/w/index.php?curid=79505 ;
> * « 119px-Nalle_-_a_small_brown_teddy_bear.jpg », de [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) (photographie personnelle), CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166 ;
> * « 193px Broodrooster.jpg », de [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) (travail personnel), CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403.

L’apprentissage par transfert comporte quelques stratégies, comme *réentraîner toutes les couches* et *avant-dernière couche*. Ce tutoriel explique et montre comment utiliser la *stratégie de l’avant-dernière couche*. Cette *stratégie* réutilise un modèle déjà entraîné pour résoudre un problème spécifique. Elle réentraîne la couche finale de ce modèle de sorte qu’il résolve un nouveau problème. Le fait de réutiliser le modèle préentraîné dans le nouveau modèle permet de gagner beaucoup de temps et d’économiser de nombreuses ressources.

Le modèle de classification d’images réutilise le [modèle Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), un modèle TensorFlow classique de reconnaissance d’images, entraîné sur le jeu de données `ImageNet`, qui tente de classer des images entières en un millier de classes, comme « Parapluie », « Pull » et « Lave-vaisselle ».

`Inception v3 model`, que l’on peut considérer comme un [réseau neuronal convolutif profond](https://en.wikipedia.org/wiki/Convolutional_neural_network), peut atteindre sur des tâches de reconnaissance visuelle dure des performances raisonnables, au moins égales à l’efficacité humaine dans certains domaines. Le modèle/algorithme, développé par de nombreux chercheurs, s’appuie sur le document d’origine [« Rethinking the Inception Architecture for Computer Vision », Szegedy et al.](https://arxiv.org/abs/1512.00567)

Étant donné que `Inception model` a déjà été préentraîné sur des milliers d’images différentes, il contient les [caractéristiques des images](https://en.wikipedia.org/wiki/Feature_(computer_vision)) nécessaires à leur identification. Les couches inférieures reconnaissent des caractéristiques simples (comme les bords) et les couches supérieures des caractéristiques plus complexes (comme les formes). La dernière couche est entraînée sur un ensemble de données beaucoup plus petit, car elle part d’un modèle préentraîné qui sait déjà classer des images. Comme le modèle permet de classer les images dans plus de deux catégories, il s’agit d’un exemple de [classifieur en classes multiples](../resources/tasks.md#multiclass-classification). 

`TensorFlow` est un kit de ressources de Deep Learning et de Machine Learning très répandu qui permet d’entraîner des réseaux neuronaux profonds (et des calculs numériques généraux) et est implémenté comme un `transformer` dans ML.NET. Dans ce tutoriel, il sert à réutiliser `Inception model`.

Comme le montre le diagramme suivant, vous ajoutez une référence aux packages NuGet ML.NET dans vos applications .NET Core ou .NET Framework. En coulisses, ML.NET inclut la bibliothèque native `TensorFlow` qui permet d’écrire du code afin de charger un fichier de modèle `TensorFlow` existant pour le scoring.  

![Diagramme ML.NET de transformation TensorFlow](./media/image-classification/tensorflow-mlnet.png)

`Inception model` est entraîné pour classer des images dans un millier de catégories, mais nous devons les classer exclusivement dans un plus petit jeu de catégories. Entrez la partie `transfer` de `transfer learning`. Vous pouvez transposer la capacité de `Inception model` à identifier et à classer des images aux nouvelles catégories, en nombre limité, de votre classifieur d’images personnalisé.  

 Il s’agit de réentraîner la couche finale de ce modèle selon trois catégories :

* Aliment
* Jouet
* Appareil

La couche utilise un [algorithme de régression logistique multinomiale](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) afin de trouver la bonne catégorie aussi vite que possible. Cet algorithme se sert des probabilités pour déterminer la réponse, donnant la valeur un à la bonne catégorie et la valeur zéro aux autres.  

### <a name="dataset"></a>DataSet

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
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), le dépôt de fichiers multimédias sous licence libre.* Récupéré le 17 octobre 2018 à 10 h 48 aux adresses :  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a>Créer une application console

### <a name="create-a-project"></a>Créer un projet

1. Créer une **application console .NET Core** appelée « TransferLearningTF ».

2. Installez le **package NuGet Microsoft.ML** :

    Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir et recherchez **Microsoft.ML**. Cliquez sur la liste déroulante **Version** et sélectionnez le package **1.0.0** dans la liste, puis sélectionnez le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés. Répétez ces étapes pour **Microsoft.ML.ImageAnalytics v1.0.0** et **Microsoft.ML.TensorFlow v0.12.0**.

### <a name="prepare-your-data"></a>Préparer vos données

1. Téléchargez le [fichier zip du répertoire de ressources du projet ](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip) et décompressez-le.

2. Copiez le répertoire `assets` dans votre répertoire de projet *TransferLearningTF*. Ce répertoire et ses sous-répertoires contiennent les fichiers de données et d’aide nécessaires à ce tutoriel (sauf pour le modèle Inception, que vous allez télécharger et ajouter à l’étape suivante).

3. Téléchargez le [modèle Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) et décompressez-le.

4. Copiez le contenu décompressé du répertoire `inception5h` dans le répertoire `assets\inputs-train\inception` de votre projet *TransferLearningTF*. Ce répertoire contient le modèle et les fichiers d’aide supplémentaires nécessaires à ce tutoriel, comme le montre l’image suivante :

   ![Contenu du répertoire Inception](./media/image-classification/inception-files.png)

5. Dans l’Explorateur de solutions, cliquez sur chacun des fichiers du répertoire et des sous-répertoires de ressources et sélectionnez **Propriétés**. Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.

### <a name="create-classes-and-define-paths"></a>Créer des classes et définir des chemins

Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

Créez des champs globaux qui représenteront les chemins des différentes ressources, puis des variables globales pour `LabelTokey`, `ImageReal` et `PredictedLabelValue` :

* `_assetsPath` comporte le chemin des ressources.
* `_trainTagsTsv` comporte le chemin du fichier .tsv des balises des données d’images d’apprentissage.
* `_predictTagsTsv` comporte le chemin du fichier .tsv des balises des données d’images de prédiction.
* `_trainImagesFolder` comporte le chemin des images servant à l’apprentissage du modèle.
* `_predictImagesFolder` comporte le chemin des images que le modèle entraîné devra classer.
* `_inceptionPb` comporte le chemin du modèle Inception préentraîné à réutiliser pour réentraîner le modèle.
* `_inputImageClassifierZip` comporte le chemin où sera chargé le modèle entraîné.
* `_outputImageClassifierZip` contient le chemin d’accès où le modèle formé est enregistré.
* `LabelTokey` est la valeur `Label` mappée à une clé.
* `ImageReal` est la colonne contenant la valeur d’image prédite.
* `PredictedLabelValue` est la colonne contenant la valeur d’étiquette prédite.

Ajoutez le code suivant à la ligne juste au-dessus de la méthode `Main` pour spécifier ces chemins et les autres variables :

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

Créez des classes pour vos données d’entrée et vos prédictions. Ajoutez une nouvelle classe à votre projet :

1. Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *ImageData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

    Le fichier *ImageData.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction `using` suivante en haut de *ImageData.cs* :

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

Supprimez la définition de classe existante et ajoutez le code suivant pour la classe `ImageData` au fichier *ImageData.cs* :

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

`ImageData` est la classe de données d’images d’entrée, qui comprend les champs <xref:System.String> suivants :

* `ImagePath` contient le nom du fichier image.
* `Label` contient la valeur de l’étiquette d’image.

Ajoutez une nouvelle classe à votre projet pour `ImagePrediction` :

1. Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *ImagePrediction.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

    Le fichier *ImagePrediction.cs* s’ouvre dans l’éditeur de code. Supprimez les instructions `System.Collections.Generic` et `System.Text` `using` en haut de *ImagePrediction.cs* :

Supprimez la définition de classe existante et ajoutez le code suivant, qui contient la classe `ImagePrediction`, au fichier *ImagePrediction.cs* :

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

`ImagePrediction` est la classe de prédiction des images, qui comprend les champs suivants :

* `Score` contient le pourcentage de confiance d’une classification d’image donnée.
* `PredictedLabelValue` contient la valeur de l’étiquette de classification d’image prédite.

`ImagePrediction` représente la classe utilisée pour la prédiction, une fois le modèle formé. Elle comporte une `string` (`ImagePath`) correspondant au chemin de l’image. `Label` sert à réutiliser et à réentraîner le modèle. L’attribut `PredictedLabelValue` est utilisé pendant la prédiction et l’évaluation. L’évaluation utilise une entrée avec les données d’apprentissage, les valeurs prédites et le modèle.

La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

### <a name="initialize-variables-in-main"></a>Initialiser les variables dans Principal

Initialiser la variable `mlContext` avec une nouvelle instance de `MLContext`.  Remplacez la ligne `Console.WriteLine("Hello World!")` par le code suivant dans la méthode `Main` :

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a>Créer un struct pour les paramètres par défaut

Le modèle Inception comporte plusieurs paramètres par défaut qu’il faut passer. Créez un struct permettant de mapper les valeurs de paramètre par défaut sur les noms conviviaux avec le code suivant, juste après la méthode `Main()` :

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Créer une méthode d’utilitaire d’affichage

Étant donné que vous allez afficher les données d’image et les prédictions associées plusieurs fois, créez une méthode d’utilitaire d’affichage qui gère l’affichage des données d’image et des résultats de prédiction.

La méthode `DisplayResults()` exécute les tâches suivantes :

* Affiche les résultats prédits.

Créez la méthode `DisplayResults()` juste après le struct `InceptionSettings` avec le code suivant :

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

La méthode `Transform()` a rempli `ImagePath` dans `ImagePrediction` avec les champs prédits. À mesure que le processus ML.NET progresse, chaque composant ajoute des colonnes, ce qui rend l’affichage des résultats plus facile :

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

Vous devez appeler la méthode `DisplayResults()` dans les deux méthodes de classification des images.

### <a name="create-a-tsv-file-utility-method"></a>Créez une méthode d’utilitaire de fichier .tsv

La méthode `ReadFromTsv()` exécute les tâches suivantes :

* Lit le fichier `tags.tsv` de données d’images.
* Ajoute le chemin de fichier au nom de fichier image.
* Charge les données du fichier dans un objet `ImageData` IEnumerable.

Créez la méthode `ReadFromTsv()` juste après la méthode `PairAndDisplayResults()`, en utilisant le code suivant :

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

Le code suivant analyse le fichier `tags.tsv` afin d’ajouter le chemin de fichier au nom de fichier image pour la propriété `ImagePath` et de le charger ainsi que le `Label` dans un objet `ImageData`. Ajoutez-le en première ligne de la méthode `ReadFromTsv()`.  Le chemin de fichier complet est nécessaire pour afficher les résultats de prédiction.

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
Il existe trois principaux concepts dans ML.NET : les [données](../resources/glossary.md#data), les [transformateurs](../resources/glossary.md#transformer) et les [estimateurs](../resources/glossary.md#estimator).

## <a name="reuse-and-tune-pre-trained-model"></a>Réutiliser et paramétrer le modèle préentraîné

Ajoutez l’appel suivant à la méthode `ReuseAndTuneInceptionModel()` comme prochaine ligne de code dans la méthode `Main()` :

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

La méthode `ReuseAndTuneInceptionModel()` exécute les tâches suivantes :

* Charge les données.
* Extrait et transforme les données.
* Évalue le modèle TensorFlow.
* Paramètre (réentraîne) le modèle.
* Affiche les résultats du modèle.
* Évalue le modèle.
* Retourne le modèle.

Créez la méthode `ReuseAndTuneInceptionModel()`, juste après le struct `InceptionSettings` et juste avant la méthode `DisplayResults()`, avec le code suivant :

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a>Charger les données

Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView). `IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte). Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.

Chargez les données avec le wrapper `MLContext.Data.LoadFromTextFile`. Ajoutez le code suivant comme première ligne de la méthode `ReuseAndTuneInceptionModel()` :

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a>Extraire des caractéristiques et transformer les données

Le prétraitement et le nettoyage des données constituent des tâches importantes qui se produisent avant qu’un jeu de données puisse être utilisé efficacement pour l’apprentissage.  L’utilisation de données sans effectuer ces tâches de modélisation peut produire des résultats trompeurs.

Les algorithmes de Machine Learning prennent des données [caractérisées](../resources/glossary.md#feature) ; pour utiliser un réseau neuronal profond, il faut adapter les images au format qu’il attend. Ce format est un [vecteur numérique](../resources/glossary.md#numerical-feature-vector).

Après l’apprentissage et l’évaluation, passez à la prédiction avec les valeurs de la colonne **Label**. Comme vous utilisez un modèle préentraîné, mappez les champs sur le nouveau modèle avec la méthode [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A). Elle transforme le `Label` en une colonne de type de clé numérique (`LabelTokey`) qu’elle ajoute aux colonnes du jeu de données :  Nommez cela `estimator`, car vous y ajouterez également le processus d’apprentissage. Ajoutez la ligne de code suivante :

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

L’estimateur de traitement d’images utilise des extracteurs de caractéristiques de type [réseau neuronal profond](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) préentraînés. Il faut adapter les images au format attendu par des réseaux neuronaux profonds. C’est la raison pour laquelle on utilise plusieurs transformations d’images afin d’obtenir les données d’images au format nécessaire au modèle :

1. La transformation `LoadImages` charge les images en mémoire au type bitmap.
2. La transformation `ResizeImages` redimensionne les images, car le modèle préentraîné définit une largeur et une hauteur d’image d’entrée.
3. La transformation `ExtractPixels` extrait les pixels des images d’entrée et les convertit en un vecteur numérique.

Ajoutez ces transformations d’images à la suite du code :

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

`LoadTensorFlowModel` est une méthode pratique qui permet de charger le modèle `TensorFlow` une seule fois, puis de créer `TensorFlowEstimator` à l’aide de `ScoreTensorFlowModel`. `ScoreTensorFlowModel` extrait des sorties spécifiées (les caractéristiques des images de `Inception model` `softmax2_pre_activation`) et évalue un jeu de données avec le modèle `TensorFlow` préentraîné.

`softmax2_pre_activation` aide à le modèle à déterminer à quelle classe appartiennent les images. `softmax2_pre_activation` retourne la probabilité de chacune des catégories pour une image donnée ; la somme de toutes ces probabilités doit être égale à 1. Il suppose qu’une image appartient à une seule catégorie, comme le montre l’exemple suivant :

| Classe         | Probabilité   |
| ------------- | ------------- |
| `Food`        |  0,001        |
| `Toy`         |  0,95         |
| `Appliance`   |  0,06         |

Ajoutez `TensorFlowTransform` à `estimator` avec la ligne de code suivante :

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a>Choisir un algorithme d’apprentissage

Pour ajouter l’algorithme d’apprentissage, appelez la méthode de wrapper `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()`.  [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) est ajouté à `estimator` et accepte les caractéristiques d’images Inception (`softmax2_pre_activation`) et les paramètres d’entrée `Label` pour apprendre à partir des données d’historique.  Ajoutez le processus d’apprentissage avec le code suivant :

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

Il faut également mapper `predictedlabel` sur `predictedlabelvalue` :

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

La méthode `Fit()` entraîne votre modèle en transformant le jeu de données et en appliquant l’entraînement. Ajustez le modèle au jeu de données d’entraînement et retournez le modèle entraîné en ajoutant la ligne de code suivante dans la méthode `ReuseAndTuneInceptionModel()` :

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

La méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) établit des prédictions pour plusieurs lignes d’entrée fournies d’un jeu de données de test.  Transformez les données `Training` en ajoutant le code suivant à `ReuseAndTuneInceptionModel()` :

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

Convertissez vos données d’images et `DataViews` de prédiction en `IEnumerables` fortement typés à associer pour faciliter l’affichage. Utilisez pour cela la méthode `MLContext.CreateEnumerable()` avec le code suivant :

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

Appelez la méthode `DisplayResults()` pour afficher vos données et prédictions à la fin de la méthode `ReuseAndTuneInceptionModel()` :

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

Une fois la prédiction définie, la méthode [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :

* Évalue le modèle (compare les valeurs prédites avec le jeu de données réel `Labels`).

* Retourne les indicateurs de performances du modèle.

Ajoutez comme nouvelle ligne le code suivant à la méthode `ReuseAndTuneInceptionModel()` :

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

Les indicateurs suivants sont évalués pour la classification d’images :

* `Log-loss` (voir [Perte logarithmique](../resources/glossary.md#log-loss)). Vous voulez que la perte logarithmique soit aussi proche de zéro que possible.

* `Per class Log-loss`. La perte logarithmique doit être aussi proche de zéro que possible.

Utilisez le code suivant pour afficher les métriques, partager les résultats et agir dessus :

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 Ajoutez le code suivant pour retourner le modèle entraîné à la ligne suivante :

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a>Classer des images avec un modèle chargé

Ajoutez l’appel suivant à la méthode `ClassifyImages()` à la fin de la méthode `Main` :

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

La méthode `ClassifyImages()` exécute les tâches suivantes :

* Lit le fichier .tsv en `IEnumerable`.
* Prédit les classifications d’images en fonction des données de test.

Créez la méthode `ClassifyImages()`, juste après la méthode `ReuseAndTuneInceptionModel()` et juste avant la méthode `PairAndDisplayResults()`, avec le code suivant :

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

Appelez d’abord la méthode `ReadFromTsv()` pour créer une classe `IEnumerable<ImageData>` contenant le chemin complet de chaque `ImagePath`. Il faut que ce chemin de fichier soit associé à vos données et résultats de prédiction. Vous devez également convertir la classe `IEnumerable<ImageData>` en une `IDataView` servant aux prédictions. Ajoutez le code suivant à la fin de la méthode `ClassifyImages()` :

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

Comme vous l’avez fait avec les données d’images d’entraînement, prédisez la catégorie des données d’images de test en utilisant la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) du modèle passé. Ajoutez le code suivant à la méthode `ClassifyImages()` pour les prédictions et la conversion de la `IDataView` `predictions` en `IEnumerable` à des fins d’association et d’affichage :

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

Pour associer et afficher vos données d’images de test et vos prédictions, ajoutez le code suivant, qui appelle la méthode `DisplayResults()` déjà créée, à la fin de la méthode `ClassifyImages()` :

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a>Classer une seule image avec un modèle chargé

Ajoutez l’appel suivant à la méthode `ClassifySingleImage()` à la fin de la méthode `Main` :

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

La méthode `ClassifySingleImage()` exécute les tâches suivantes :

* Charge une instance `ImageData`.
* Prédit la classification d’image en fonction des données de test.

Créez la méthode `ClassifySingleImage()`, juste après la méthode `ClassifyImages()` et juste avant la méthode `PairAndDisplayResults()`, avec le code suivant :

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

Créez d’abord une classe `ImageData` contenant le chemin complet et le nom de fichier d’image de l’unique `ImagePath`. Ajoutez le code suivant à la fin de la méthode `ClassifySingleImage()` :

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

La [classe PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API utile qui effectue une prévision sur une seule instance de données. La fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) établit une prédiction sur une seule colonne de données. Passez `imageData` à `PredictionEngine` pour prédire la catégorie d’image en ajoutant le code suivant à `ClassifySingleImage()` :

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

Affichez le résultat de la prédiction à la fin de la méthode `ClassifySingleImage()` :

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a>Résultats

Après avoir suivi les étapes précédentes, exécutez votre application console (Ctrl + F5). Vous devriez obtenir les résultats suivants.  Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.

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
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379

C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
Press any key to close this window . . .
```

Félicitations ! Vous avez créé un modèle Machine Learning de classification d’images en réutilisant un modèle `TensorFlow` préentraîné dans ML.NET.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> * Comprendre le problème
> * Réutiliser et paramétrer le modèle préentraîné
> * Classer des images avec un modèle chargé

Consultez le référentiel GitHub d’exemples Machine Learning pour voir un exemple développé de classification d’images.
> [!div class="nextstepaction"]
> [Référentiel GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/)
