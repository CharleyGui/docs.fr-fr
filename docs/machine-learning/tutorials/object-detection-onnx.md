---
title: 'Didacticiel : détecter des objets à l’aide d’un modèle d’apprentissage profond ONNX'
description: Ce tutoriel montre comment utiliser un modèle de deep learning ONNX préentraîné dans ML.NET pour détecter des objets dans des images.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ff9986c09e39f5c4d24f52c351db6455ff63e77
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092718"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a>Didacticiel : détecter des objets à l’aide de ONNX dans ML.NET

Découvrez comment utiliser un modèle ONNX préentraîné dans ML.NET pour détecter des objets dans des images.

L’entraînement d’un modèle de détection d’objets à partir de zéro nécessite de définir des millions de paramètres et d’avoir un grand nombre de données d’entraînement étiquetées et de ressources de calcul (des centaines d’heures GPU). L’utilisation d’un modèle préentraîné vous permet de raccourcir le processus d’entraînement.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Comprendre le problème
> - Découvrir ce qu’est ONNX et comment il fonctionne avec ML.NET
> - Comprendre le modèle
> - Réutiliser le modèle préentraîné
> - Détecter les objets avec un modèle chargé

## <a name="pre-requisites"></a>Conditions préalables

- [Visual Studio 2017 version 15,6 ou ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) avec la charge de travail « développement multiplateforme .net Core » installée.
- [Package NuGet Microsoft.ML](https://www.nuget.org/packages/Microsoft.ML/)
- [Package NuGet Microsoft.ML.ImageAnalytics](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [Package NuGet Microsoft.ML.OnnxTransformer](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [Modèle préentraîné Tiny YOLOv2](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)
- [Netron](https://github.com/lutzroeder/netron) (facultatif)

## <a name="onnx-object-detection-sample-overview"></a>Vue d’ensemble de l’exemple de détection d’objets ONNX

Cet exemple crée une application console .NET Core qui détecte les objets dans une image à l’aide d’un modèle ONNX de deep learning préentraîné. Vous trouverez le code de cet exemple dans le [dépôt dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) sur GitHub.

## <a name="what-is-object-detection"></a>Qu’est-ce que la détection d’objets ?

La détection d’objets est un problème de vision par ordinateur. Même si elle est étroitement liée à la classification d’images, la détection d’objets effectue une classification d’images à une échelle plus précise. La détection d’objets localise _et_ catégorise les entités dans les images. Utilisez la détection d’objets quand les images contiennent plusieurs objets de différents types.

![Captures d’écran montrant la classification des images par rapport à la classification des objets.](./media/object-detection-onnx/img-classification-obj-detection.png)

Voici quelques cas d’utilisation de la détection d’objets :

- Voitures autonomes
- Robotique
- Détection de visage
- Sécurité des espaces de travail
- Dénombrement des objets
- Reconnaissance des activités

## <a name="select-a-deep-learning-model"></a>Sélectionner un modèle de deep learning

Le deep learning fait partie du machine learning. Pour entraîner des modèles de deep learning, de grandes quantités de données sont nécessaires. Les différents motifs (patterns) de données sont représentés par une série de couches. Les relations dans les données sont encodées en tant que connexions entre les couches contenant des poids. Plus le poids est élevé, plus la relation est forte. Collectivement, cette série de couches et de connexions est connue sous le nom de réseaux neuronaux artificiels. Plus le nombre de couches d’un réseau est élevé, plus il est profond, ce qui en fait un réseau neuronal profond.

Il existe différents types de réseaux neuronaux, les plus courants étant les perceptrons multicouches (MLP), les réseaux de neurones convolutifs (CNN) et les réseaux de neurones récurrents (RNN). Le plus simple est le MLP, qui mappe un ensemble d’entrées à un ensemble de sorties. Ce réseau neuronal est parfait quand les données n’ont pas de composant spatial ou temporel. Le réseau CNN utilise des couches convolutives pour traiter les informations spatiales contenues dans les données. Un bon cas d’utilisation des réseaux CNN est le traitement d’images pour détecter la présence d’une caractéristique dans une zone d’une image (par exemple, y a-t-il un nez au centre d’une image ?). Enfin, les réseaux RNN autorisent la persistance de l’état ou de la mémoire à utiliser comme entrée. Ils sont utilisés pour l’analyse des séries chronologiques, où le tri séquentiel et le contexte des événements sont importants.

### <a name="understand-the-model"></a>Comprendre le modèle

La détection d’objets est une tâche de traitement d’image. C’est pourquoi la plupart des modèles de deep learning préentraînés pour résoudre ce problème sont des réseaux CNN. Le modèle utilisé dans ce didacticiel est le petit modèle YOLOv2, une version plus compacte du modèle YOLOv2 décrit dans le document : [« YOLO9000 : meilleur, plus rapide et plus puissant » par RedMon et Fadhari](https://arxiv.org/pdf/1612.08242.pdf). Tiny YOLOv2 est entraîné sur le jeu de données Pascal COV et est constitué de 15 couches qui peuvent prédire 20 classes différentes d’objets. Étant donné que Tiny YOLOv2 est une version condensée du modèle YOLOv2 d’origine, un compromis est établi entre la vitesse et la précision. Les différentes couches qui composent le modèle peuvent être visualisées à l’aide d’outils comme Netron. L’inspection du modèle produit un mappage des connexions entre toutes les couches qui composent le réseau neuronal, où chaque couche contient le nom de la couche ainsi que les dimensions des entrée/sortie respectives. Les structures de données utilisées pour décrire les entrées et les sorties du modèle sont appelées des tenseurs. Les tenseurs peuvent être considérés comme des conteneurs qui stockent des données dans N dimensions. Dans le cas de Tiny YOLOv2, le nom de la couche d’entrée est `image` et il attend un tenseur de dimensions `3 x 416 x 416`. Le nom de la couche de sortie est `grid` et génère un tenseur de sortie de dimensions `125 x 13 x 13`.

![Couche d’entrée fractionnée en couches masquées, puis couche de sortie](./media/object-detection-onnx/netron-model-map-layers.png)

Le modèle YOLO prend une image `3(RGB) x 416px x 416px`. Le modèle prend cette entrée et la passe à travers les différentes couches pour produire une sortie. La sortie divise l’image d’entrée en une grille `13 x 13`, chaque cellule de la grille contenant les valeurs `125`.

### <a name="what-is-an-onnx-model"></a>Qu’est-ce qu’un modèle ONNX ?

ONNX (Open Neural Network Exchange) est un format open source pour les modèles IA. ONNX prend en charge l’interopérabilité entre les frameworks. Cela signifie que vous pouvez entraîner un modèle dans l’un des nombreux frameworks de machine learning connus tels que PyTorch, le convertir au format ONNX et consommer le modèle ONNX dans un autre framework comme ML.NET. Pour en savoir plus, consultez le [site web ONNX](https://onnx.ai/).

![Diagramme des formats pris en charge par ONNX.](./media/object-detection-onnx/onnx-supported-formats.png)

Le modèle Tiny YOLOv2 préentraîné est stocké au format ONNX, représentation sérialisée des couches et des motifs appris de ces couches. Dans ML.NET, l’interopérabilité avec ONNX s’obtient avec les packages NuGet [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) et [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer). Le package[`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) contient une série de transformations qui prennent une image et l’encodent en valeurs numériques pouvant être utilisées comme entrée dans un pipeline de prédiction ou d’entraînement. Le package [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) tire profit du runtime ONNX afin de charger un modèle ONNX et de l’utiliser pour faire des prédictions en fonction de l’entrée fournie.

![Le workflow de données du fichier ONNX dans le runtime ONNX.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a>Configurer le projet .NET Core

Maintenant que vous avez une compréhension générale de ce qu’est ONNX et de la façon dont Tiny YOLOv2 fonctionne, il est temps de générer l’application.

### <a name="create-a-console-application"></a>Création d’une application console

1. Créez une **application console .NET Core** appelée « ObjectDetection ».

1. Installez le **package NuGet Microsoft.ML** :

    - Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.
    - Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir et recherchez **Microsoft.ML**.
    - Sélectionnez le bouton **Installer**.
    - Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.
    - Répétez ces étapes pour **Microsoft.ML.ImageAnalytics** et **Microsoft.ML.OnnxTransformer**.

### <a name="prepare-your-data-and-pre-trained-model"></a>Préparer vos données et votre modèle préentraîné

1. Téléchargez le [fichier zip du répertoire de ressources du projet ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) et décompressez-le.

1. Copiez le répertoire `assets` dans votre répertoire de projet *ObjectDetection*. Ce répertoire et ses sous-répertoires contiennent les fichiers image nécessaires à ce tutoriel (sauf pour le modèle Tiny YOLOv2, que vous allez télécharger et ajouter à l’étape suivante).

1. Téléchargez le [modèle Tiny YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) depuis [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2) et décompressez-le.

    Ouvrez l’invite de commande et entrez la commande suivante :

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. Copiez le fichier `model.onnx` extrait du répertoire que vous venez de décompresser dans le répertoire *de votre projet*ObjectDetection`assets\Model` et renommez-le `TinyYolo2_model.onnx`. Ce répertoire contient le modèle nécessaire pour ce tutoriel.

1. Dans l’Explorateur de solutions, cliquez sur chacun des fichiers du répertoire et des sous-répertoires de ressources et sélectionnez **Propriétés**. Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.

### <a name="create-classes-and-define-paths"></a>Créer des classes et définir des chemins

Ouvrez le fichier *Program.cs* et ajoutez les instructions `using` supplémentaires suivantes en haut du fichier :

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

Ensuite, définissez les chemins des différentes ressources.

1. Tout d’abord, ajoutez la méthode `GetAbsolutePath` sous la méthode `Main` dans la classe `Program`.

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. Ensuite, dans la méthode `Main`, créez des champs pour stocker l’emplacement de vos ressources.

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

Ajoutez un nouveau répertoire à votre projet pour stocker vos données d’entrée et vos classes de prédiction.

Dans l’**Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouveau dossier**. Lorsque le nouveau dossier s’affiche dans l’Explorateur de solutions, nommez-le « DataStructures ».

Créez votre classe de données d’entrée dans le répertoire *DataStructures* qui vient d’être créé.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *DataStructures*, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *ImageNetData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

    Le fichier *ImageNetData.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction `using` suivante en haut de *ImageNetData.cs* :

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    Supprimez la définition de classe existante et ajoutez le code suivant pour la classe `ImageNetData` au fichier *ImageNetData.cs* :

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    `ImageNetData` est la classe de données d’images d’entrée, qui comprend les champs <xref:System.String> suivants :

    - `ImagePath` contient le chemin où l’image est stockée.
    - `Label` contient le nom du fichier.

    En outre, `ImageNetData` contient une méthode `ReadFromFile` qui charge plusieurs fichiers image stockés dans le chemin d’accès `imageFolder` spécifié et les retourne sous la forme d’une collection d’objets `ImageNetData`.

Créez votre classe de prédiction dans le répertoire *DataStructures*.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *DataStructures*, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *ImageNetPrediction.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

    Le fichier *ImageNetPrediction.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction `using` suivante en haut de *ImageNetPrediction.cs* :

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    Supprimez la définition de classe existante et ajoutez le code suivant pour la classe `ImageNetPrediction` au fichier *ImageNetPrediction.cs* :

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    `ImageNetPrediction` est la classe de données de prédiction et présente le champ `float[]` suivant :

    - `PredictedLabel` contient les dimensions, le score d’objet et les probabilités de classe pour chacune des zones englobantes détectées dans une image.

### <a name="initialize-variables-in-main"></a>Initialiser les variables dans Principal

La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

Initialisez la variable `mlContext` avec une nouvelle instance de `MLContext` en ajoutant la ligne suivante à la méthode `Main` de *Program.cs* sous le champ `outputFolder`.

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a>Créer un analyseur pour le post-traitement des sorties du modèle

Le modèle segmente une image dans une grille `13 x 13`, où chaque cellule de grille est `32px x 32px`. Chaque cellule de grille contient 5 rectangles englobants d’objet potentiels. Un rectangle englobant a 25 éléments :

![Exemple de grille à gauche, et exemple de cadre englobant à droite](./media/object-detection-onnx/model-output-description.png)

- `x` position x du centre du rectangle englobant par rapport à la cellule de grille à laquelle il est associé.
- `y` position y du centre du rectangle englobant par rapport à la cellule de grille à laquelle il est associé.
- `w` largeur du rectangle englobant.
- `h` hauteur du rectangle englobant.
- `o` valeur de confiance qu’un objet existe dans le rectangle englobant, également connue sous le nom de score d’objet.
- `p1-p20` probabilités de classe pour chacune des 20 classes prédites par le modèle.

Au total, les 25 éléments décrivant chacun des 5 rectangles englobants composent les 125 éléments contenus dans chaque cellule de grille.

La sortie générée par le modèle ONNX préentraîné est un tableau de type float de longueur `21125`, représentant les éléments d’un tenseur avec les dimensions `125 x 13 x 13`. Pour transformer les prédictions générées par le modèle en tenseur, un travail de post-traitement est nécessaire. Pour ce faire, créez un ensemble de classes pour permettre l’analyse de la sortie.

Ajoutez un nouveau répertoire à votre projet pour organiser l’ensemble des classes d’analyseur.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouveau dossier**. Lorsque le nouveau dossier s’affiche dans l’Explorateur de solutions, nommez-le « YoloParser ».

### <a name="create-bounding-boxes-and-dimensions"></a>Créer des rectangles englobants et des dimensions

Les données générées par le modèle contiennent les coordonnées et les dimensions des rectangles englobants des objets dans l’image. Créez une classe de base pour les dimensions.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *YoloParser*, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *DimensionsBase.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

    Le fichier *DimensionsBase.cs* s’ouvre dans l’éditeur de code. Supprimez toutes les instructions `using` et la définition de classe existante.

    Ajoutez le code suivant pour la classe `DimensionsBase` au fichier *DimensionsBase.cs* :

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    `DimensionsBase` présente les propriétés de `float` suivantes :

    - `X` contient la position de l’objet sur l’axe x.
    - `Y` contient la position de l’objet sur l’axe y.
    - `Height` contient la hauteur de l’objet.
    - `Width` contient la largeur de l’objet.

Ensuite, créez une classe pour vos rectangles englobants.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *YoloParser*, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *YoloBoundingBox.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

    Le fichier *YoloBoundingBox.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction `using` suivante en haut de *YoloBoundingBox.cs* :

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    Juste au-dessus de la définition de classe existante, ajoutez une nouvelle définition de classe appelée `BoundingBoxDimensions` qui hérite de la classe `DimensionsBase` pour contenir les dimensions de la zone englobante respective.

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    Supprimez la définition de classe `YoloBoundingBox` existante et ajoutez le code suivant pour la classe `YoloBoundingBox` au fichier *YoloBoundingBox.cs* :

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    `YoloBoundingBox` a les propriétés suivantes :

    - `Dimensions` contient les dimensions du rectangle englobant.
    - `Label` contient la classe de l’objet détecté dans le rectangle englobant.
    - `Confidence` contient la valeur de confiance de la classe.
    - `Rect` contient la représentation rectangle des dimensions du rectangle englobant.
    - `BoxColor` contient la couleur associée à la classe respective utilisée pour dessiner sur l’image.

### <a name="create-the-parser"></a>Créer l’analyseur

Maintenant que les classes pour les dimensions et les rectangles englobants sont créées, il est temps de créer l’analyseur.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *YoloParser*, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez le champ **Nom** par *YoloOutputParser.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

    Le fichier *YoloOutputParser.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction `using` suivante en haut du fichier *YoloOutputParser.cs* :

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    Dans la définition de la classe `YoloOutputParser` existante, ajoutez une classe imbriquée qui contient les dimensions de chacune des cellules de l’image. Ajoutez le code suivant pour la classe `CellDimensions` qui hérite de la classe `DimensionsBase` en haut de la définition de classe `YoloOutputParser`.

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. À l’intérieur de la définition de classe `YoloOutputParser`, ajoutez les constantes et les champs suivants.

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - `ROW_COUNT` est le nombre de lignes dans la grille dans laquelle l’image est divisée.
    - `COL_COUNT` est le nombre de colonnes dans la grille dans laquelle l’image est divisée.
    - `CHANNEL_COUNT` est le nombre total de valeurs contenues dans une cellule de la grille.
    - `BOXES_PER_CELL` est le nombre de rectangles englobants dans une cellule.
    - `BOX_INFO_FEATURE_COUNT` est le nombre de caractéristiques contenues dans un rectangle (x, y, hauteur, largeur, confiance).
    - `CLASS_COUNT` est le nombre de prédictions de classe contenues dans chaque rectangle englobant.
    - `CELL_WIDTH` est la largeur d’une cellule dans la grille de l’image.
    - `CELL_HEIGHT` est la hauteur d’une cellule dans la grille de l’image.
    - `channelStride` est la position de départ de la cellule active dans la grille.

    Quand le modèle fait une prédiction (ou « scoring »), il divise l’image d’entrée `416px x 416px` sous forme de grille de cellules d’une taille de `13 x 13`. Chaque cellule contient `32px x 32px`. Dans chaque cellule, il y a 5 rectangles englobants contenant chacun 5 caractéristiques (x, y, largeur, hauteur, confiance). En outre, chaque cadre englobant contient la probabilité de chacune des classes, soit 20 dans le cas présent. Par conséquent, chaque cellule contient 125 informations différentes (5 caractéristiques + 20 probabilités de classe).

Créez une liste d’ancres sous `channelStride` pour les 5 rectangles englobants :

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

Les ancres sont des ratios de hauteur et de largeur prédéfinis pour les rectangles englobants. La plupart des objets ou classes détectés par un modèle ont des ratios similaires. C’est utile lorsqu’il s’agit de créer des rectangles englobants. Au lieu de prédire les rectangles englobants, le décalage par rapport aux dimensions prédéfinies est calculé, réduisant ainsi le calcul nécessaire pour prédire le rectangle englobant. En général, ces ratios d’ancre sont calculés en fonction du jeu de données utilisé. Dans ce cas, étant donné que le jeu de données est connu et que les valeurs ont été précalculées, les ancres peuvent être codées en dur.

Ensuite, définissez les étiquettes ou les classes que le modèle va prédire. Ce modèle prédit 20 classes, qui est un sous-ensemble du nombre total de classes prédites par le modèle YOLOv2 d’origine.

Ajoutez votre liste d’étiquettes sous les `anchors`.

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

Des couleurs sont associées à chacune des classes. Attribuez vos couleurs de classe sous vos `labels` :

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a>Créer des fonctions d’assistance

Il faut suivre une série d’étapes dans la phase de post-traitement. Pour vous aider, vous pouvez faire appel à plusieurs méthodes d’assistance.

Les méthodes d’assistance utilisées par l’analyseur sont :

- `Sigmoid` applique la fonction sigmoïde qui génère un nombre entre 0 et 1.
- `Softmax` normalise un vecteur d’entrée dans une distribution de probabilité.
- `GetOffset` mappe les éléments de la sortie du modèle unidimensionnelle à la position correspondante dans un tenseur `125 x 13 x 13`.
- `ExtractBoundingBoxes` extrait les dimensions du rectangle englobant en utilisant la méthode `GetOffset` de la sortie du modèle.
- `GetConfidence` extrait la valeur de confiance qui indique comment s’assurer que le modèle a détecté un objet et utilise la fonction `Sigmoid` pour le convertir en pourcentage.
- `MapBoundingBoxToCell` utilise les dimensions du rectangle englobant et les mappe à sa cellule respective dans l’image.
- `ExtractClasses` extrait les prédictions de classe pour le rectangle englobant de la sortie du modèle en utilisant la méthode `GetOffset` et les transforme en distribution de probabilité en utilisant la méthode `Softmax`.
- `GetTopResult` sélectionne la classe dans la liste des classes prédites avec la probabilité la plus forte.
- `IntersectionOverUnion` filtre les rectangles englobants qui se chevauchent avec des probabilités moins fortes.

Ajoutez le code pour toutes les méthodes d’assistance sous votre liste de `classColors`.

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

Une fois que vous avez défini toutes les méthodes d’assistance, il est temps de les utiliser pour traiter la sortie du modèle.

Sous la méthode `IntersectionOverUnion`, créez la méthode `ParseOutputs` pour traiter la sortie générée par le modèle.

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

Créez une liste pour stocker vos rectangles englobants et définir des variables dans la méthode `ParseOutputs`.

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

Chaque image est divisée en grille de cellules `13 x 13`. Chaque cellule contient cinq rectangles englobants. Sous la variable `boxes`, ajoutez le code pour traiter tous les rectangles de chacune des cellules.

```csharp
for (int row = 0; row < ROW_COUNT; row++)
{
    for (int column = 0; column < COL_COUNT; column++)
    {
        for (int box = 0; box < BOXES_PER_CELL; box++)
        {

        }
    }
}
```

Dans la boucle la plus interne, calculez la position de départ du rectangle actuel au sein de la sortie du modèle unidimensionnelle.

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

Directement en dessous, utilisez la méthode `ExtractBoundingBoxDimensions` pour obtenir les dimensions du rectangle englobant actuel.

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

Utilisez ensuite la méthode `GetConfidence` pour obtenir la confiance du rectangle englobant actuel.

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

Après, utilisez la méthode `MapBoundingBoxToCell` pour mapper le rectangle englobant actuel à la cellule active en cours de traitement.

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

Avant d’aller plus loin dans le traitement, vérifiez si votre valeur de confiance est supérieure au seuil fourni. Si elle ne l’est pas, traitez le rectangle englobant suivant.

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

Sinon, continuez à traiter la sortie. L’étape suivante consiste à obtenir la distribution de probabilité des classes prédites pour le rectangle englobant actuel en utilisant la méthode `ExtractClasses`.

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

Utilisez ensuite la méthode `GetTopResult` pour obtenir la valeur et l’index de la classe avec la probabilité la plus forte pour le rectangle actuel et calculer son score.

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

Utilisez `topScore` pour une fois de plus conserver uniquement les rectangles englobants qui se trouvent au-dessus du seuil spécifié.

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

Enfin, si le rectangle englobant actuel dépasse le seuil, créez un objet `BoundingBox` et ajoutez-le à la liste des `boxes`.

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

Une fois que toutes les cellules de l’image ont été traitées, retournez la liste des `boxes`. Ajoutez l’instruction return suivante sous la boucle for la plus externe dans la méthode `ParseOutputs`.

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a>Filtrer les rectangles qui se chevauchent

Maintenant que tous les rectangles englobants à confiance élevée ont été extraits de la sortie du modèle, il faut procéder à un autre filtrage pour supprimer les images qui se chevauchent. Ajoutez une méthode appelée `FilterBoundingBoxes` sous la méthode `ParseOutputs` :

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

Dans la méthode `FilterBoundingBoxes`, commencez par créer un tableau égal à la taille des rectangles détectés et par marquer tous les emplacements comme actifs ou prêts pour le traitement.

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

Triez ensuite la liste contenant vos rectangles englobants dans l’ordre décroissant en fonction de la confiance.

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

Ensuite, créez une liste pour contenir les résultats filtrés.

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

Commencez à traiter chaque rectangle englobant en effectuant une itération sur chacun d’eux.

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

Dans cette boucle for, vérifiez si le rectangle englobant actuel peut être traité.

```csharp
if (isActiveBoxes[i])
{

}
```

Dans ce cas, ajoutez le rectangle englobant à la liste des résultats. Si les résultats dépassent la limite de cases spécifiée à extraire, arrêtez la boucle. Ajoutez le code suivant dans l’instruction if.

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

Sinon, regardez les rectangles englobants adjacents. Ajoutez le code suivant sous le contrôle de la limite de rectangle.

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

Comme pour le premier rectangle, si le rectangle adjacent est actif ou prêt à être traité, utilisez la méthode `IntersectionOverUnion` pour vérifier si le premier rectangle et le deuxième rectangle dépassent le seuil spécifié. Ajoutez le code suivant à votre boucle for la plus profonde.

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

En dehors de la boucle for la plus interne qui vérifie les rectangles englobants adjacents, regardez s’il reste d’éventuels rectangles englobants à traiter. Si ce n’est pas le cas, rompez la boucle for externe.

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

Enfin, en dehors de la boucle for initiale de la méthode `FilterBoundingBoxes`, retournez les résultats :

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

Parfait ! Il est maintenant temps d’utiliser ce code avec le modèle de scoring.

## <a name="use-the-model-for-scoring"></a>Utiliser le modèle pour le scoring

Tout comme le post-traitement, il faut suivre quelques étapes pour le scoring. Pour vous y aider, ajoutez une classe qui contiendra la logique de scoring à votre projet.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *OnnxModelScorer.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

    Le fichier *OnnxModelScorer.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction `using` suivante en haut de *OnnxModelScorer.cs* :

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    Dans la définition de la classe `OnnxModelScorer`, ajoutez les variables suivantes.

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    Juste en dessous, créez un constructeur pour la classe `OnnxModelScorer` qui initialisera les variables déjà définies.

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    Une fois que vous avez créé le constructeur, définissez quelques structs qui contiennent les variables relatives aux paramètres de l’image et du modèle. Créez un struct appelé `ImageNetSettings` pour contenir la hauteur et la largeur attendues comme entrée pour le modèle.

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    Ensuite, créez un autre struct appelé `TinyYoloModelSettings` qui contient les noms des couches d’entrée et de sortie du modèle. Pour visualiser le nom des couches d’entrée et de sortie du modèle, vous pouvez utiliser un outil comme [Netron](https://github.com/lutzroeder/netron).

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    Après, créez le premier ensemble de méthodes à utiliser pour le scoring. Créez la méthode `LoadModel` dans votre classe `OnnxModelScorer`.

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    Dans la méthode `LoadModel`, ajoutez le code suivant pour la journalisation.

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    Les pipelines ML.NET doivent connaître le schéma de données sur lequel opérer quand la méthode [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) est appelée. Dans ce cas, un processus similaire à l’entraînement sera utilisé. Toutefois, étant donné qu’aucun véritable entraînement ne se produit, il est acceptable d’utiliser une [`IDataView`](xref:Microsoft.ML.IDataView) vide. Créez une [`IDataView`](xref:Microsoft.ML.IDataView) pour le pipeline à partir d’une liste vide.

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    En dessous, définissez le pipeline. Le pipeline se compose de quatre transformations.

    - [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) charge l’image en tant que bitmap.
    - [`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) redimensionne l’image à la taille spécifiée (dans le cas présent, `416 x 416`).
    - [`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) change la représentation en pixels de l’image en passant d’une bitmap à un vecteur numérique.
    - [`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) charge le modèle ONNX et l’utilise pour effectuer un scoring sur les données fournies.

    Définissez votre pipeline dans la méthode `LoadModel` sous la variable `data`.

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    Il est maintenant temps d’instancier le modèle pour le scoring. Appelez la méthode [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) sur le pipeline et retournez-la pour poursuivre le traitement.

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

Une fois que le modèle est chargé, il peut être utilisé pour faire des prédictions. Pour faciliter ce processus, créez une méthode appelée `PredictDataUsingModel` sous la méthode `LoadModel`.

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

Dans `PredictDataUsingModel`, ajoutez le code suivant pour la journalisation.

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

Ensuite, utilisez la méthode [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) pour le scoring des données.

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

Extrayez les probabilités prédites et retournez-les pour un traitement supplémentaire.

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

Maintenant que les deux étapes sont configurées, fusionnez-les en une seule méthode. Sous la méthode `PredictDataUsingModel`, ajoutez une nouvelle méthode appelée `Score`.

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

Vous avez presque fini ! À présent, passons à la pratique.

## <a name="detect-objects"></a>Détecter des objets

Maintenant que la configuration est terminée, il est temps de détecter des objets. Commencez par ajouter des références au scoreur et à l’analyseur dans votre classe *Program.cs*.

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a>Scorer et analyser les sorties du modèle

Dans la méthode `Main` de votre classe *Program.cs*, ajoutez une instruction try-catch.

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

Dans le bloc `try`, commencez à implémenter la logique de détection d’objet. Chargez d’abord les données dans une [`IDataView`](xref:Microsoft.ML.IDataView).

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

Créez ensuite une instance de `OnnxModelScorer` et utilisez-la pour le scoring des données chargées.

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

À présent, passons à l’étape de post-traitement. Créez une instance de `YoloOutputParser` et utilisez-la pour traiter la sortie du modèle.

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

Une fois que la sortie du modèle a été traitée, il est temps de tracer les rectangles englobants sur les images.

### <a name="visualize-predictions"></a>Visualiser des prédictions

Une fois que le modèle a scoré les images et que les sorties ont été traitées, les rectangles englobants doivent être tracés sur l’image. Pour ce faire, ajoutez une méthode appelée `DrawBoundingBox` en dessous de la méthode `GetAbsolutePath` dans *Program.cs*.

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

Tout d’abord, chargez l’image et récupérez les dimensions de hauteur et de largeur dans la méthode `DrawBoundingBox`.

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

Ensuite, créez une boucle for-each pour itérer sur chaque rectangle englobant détecté par le modèle.

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

À l’intérieur de la boucle for-each, récupérez les dimensions du rectangle englobant.

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

Étant donné que les dimensions du rectangle englobant correspondent à l’entrée de modèle de `416 x 416`, adaptez les dimensions du rectangle englobant pour qu’elles correspondent à la taille réelle de l’image.

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

Ensuite, définissez un modèle pour le texte qui s’affichera au-dessus de chaque cadre englobant. Le texte contient la classe de l’objet qui se trouve dans le rectangle englobant respectif, ainsi que l’indice de confiance.

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

Pour tracer sur l’image, convertissez-la en objet [`Graphics`](xref:System.Drawing.Graphics).

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

Dans le bloc de code `using`, réglez les paramètres d’objet [`Graphics`](xref:System.Drawing.Graphics) du graphique.

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

En dessous, définissez les options de police et de couleur du texte et du rectangle englobant.

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

Créez et renseignez un rectangle au-dessus du rectangle englobant pour contenir le texte à l’aide de la méthode [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*). Cela permettra de distinguer le texte et d’améliorer la lisibilité.

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

Écrivez ensuite le texte et tracez le rectangle englobant sur l’image en utilisant les méthodes [`DrawString`](xref:System.Drawing.Graphics.DrawString*) et [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*).

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

En dehors de la boucle for-each, ajoutez du code pour enregistrer les images dans `outputDirectory`.

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

Pour obtenir des commentaires supplémentaires indiquant que l’application fait des prédictions comme prévu au moment de l’exécution, ajoutez une méthode appelée `LogDetectedObjects` en dessous de la méthode `DrawBoundingBox` dans le fichier *Program.cs* pour générer les objets détectés dans la console.

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

Maintenant que vous disposez de méthodes d’assistance pour créer des commentaires visuels à partir des prédictions, ajoutez une boucle For pour itérer sur chacune des images scorées.

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

Dans la boucle for, récupérez le nom du fichier image et les rectangles englobants associés.

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

Dessous, utilisez la méthode `DrawBoundingBox` pour tracer les rectangles englobants sur l’image.

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

Enfin, utilisez la méthode `LogDetectedObjects` pour sortir des prédictions dans la console.

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

Après l’instruction try-catch, ajoutez une logique supplémentaire pour indiquer que le processus a fini l’exécution.

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

Et voilà !

## <a name="results"></a>Résultats

Après avoir suivi les étapes précédentes, exécutez votre application console (Ctrl + F5). Vous devriez obtenir les résultats suivants. Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.

```console
=====Identify the objects in the images=====

.....The objects in the image image1.jpg are detected as below....
car and its Confidence score: 0.9697262
car and its Confidence score: 0.6674225
person and its Confidence score: 0.5226039
car and its Confidence score: 0.5224892
car and its Confidence score: 0.4675332

.....The objects in the image image2.jpg are detected as below....
cat and its Confidence score: 0.6461141
cat and its Confidence score: 0.6400049

.....The objects in the image image3.jpg are detected as below....
chair and its Confidence score: 0.840578
chair and its Confidence score: 0.796363
diningtable and its Confidence score: 0.6056048
diningtable and its Confidence score: 0.3737402

.....The objects in the image image4.jpg are detected as below....
dog and its Confidence score: 0.7608147
person and its Confidence score: 0.6321323
dog and its Confidence score: 0.5967442
person and its Confidence score: 0.5730394
person and its Confidence score: 0.5551759

========= End of Process..Hit any Key ========
```

Pour voir les images avec les rectangles englobants, accédez au répertoire `assets/images/output/`. Voici un exemple de l’une des images traitées.

![Exemple d’image traitée d’une salle de repas](./media/object-detection-onnx/dinning-room-table-chairs.png)

Félicitations ! Vous avez créé un modèle Machine Learning pour la détection d’objets en réutilisant un modèle `ONNX` préentraîné dans ML.NET.

Vous pouvez trouver le code source de ce didacticiel dans le référentiel [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) .

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Comprendre le problème
> - Découvrir ce qu’est ONNX et comment il fonctionne avec ML.NET
> - Comprendre le modèle
> - Réutiliser le modèle préentraîné
> - Détecter les objets avec un modèle chargé

Consultez le dépôt d’exemples Machine Learning GitHub pour voir un exemple détaillé de détection d’objets.
> [!div class="nextstepaction"]
> [Référentiel GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
