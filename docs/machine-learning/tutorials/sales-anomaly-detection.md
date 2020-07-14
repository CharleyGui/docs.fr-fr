---
title: 'Didacticiel : détecter les anomalies dans les ventes de produits'
description: Découvrez comment créer une application de détection des anomalies pour des données de ventes de produit. Ce didacticiel crée une application de console .NET Core à l’aide de C# dans Visual Studio 2019.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: cf61f197e4befebdbb1fbf2ca4cbcdc61c48780a
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281665"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a>Didacticiel : détecter les anomalies dans les ventes de produits avec ML.NET

Découvrez comment créer une application de détection des anomalies pour des données de ventes de produit. Ce didacticiel crée une application de console .NET Core à l’aide de C# dans Visual Studio.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> * Chargement des données
> * Créer une transformation pour la détection d’anomalie de pics
> * Détecter des anomalies de pics avec la transformation
> * Créer une transformation pour la détection d’anomalie de points de changement
> * Détecter des anomalies de points de changement avec la transformation

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).

## <a name="prerequisites"></a>Prérequis

* [Visual Studio 2017 version 15,6 ou ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail « développement multiplateforme .net Core » installée.

* [Jeu de données product-sales.csv](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Le format de données dans `product-sales.csv` est basé sur le jeu de données « Shampoo Sales Over a Three Year Period », disponible sur DataMarket et fourni dans la bibliothèque TSDL (Time Series Data Library) créée par Rob Hyndman.
> Ce jeu de données est concédé sous la licence Open par défaut de DataMarket.

## <a name="create-a-console-application"></a>Création d’une application console

1. Créez une **application console .NET Core** appelée « ProductSalesAnomalyDetection ».

2. Créez un répertoire nommé *Data* dans votre projet pour enregistrer les fichiers de votre jeu de données.

3. Installez le **package NuGet Microsoft.ML** :

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ml** , puis sélectionnez le bouton **installer** . Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés. Répétez ces étapes pour **Microsoft. ml. TimeSeries**.

4. Ajoutez les instructions `using` suivantes en tête de votre fichier *Program.cs* :

    [!code-csharp[AddUsings](./snippets/sales-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Télécharger vos données

1. Téléchargez le jeu de données et enregistrez-le dans le dossier *Data* précédemment créé :

   * Cliquez avec le bouton droit sur [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) et sélectionnez « Enregistrer le lien (ou la cible) sous... ».

     Veillez à enregistrer le fichier \*.csv dans le dossier *Data* ou, si vous l’avez enregistré ailleurs, à déplacer le fichier \*.csv dans le dossier *Data*.

2. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier \*.csv et sélectionnez **Propriétés**. Sous **avancé**, remplacez la valeur de **copier dans le répertoire de sortie** par **copier si plus récent**.

Le tableau suivant présente un aperçu des données de votre fichier \*.csv :

|Mois  |ProductSales |
|-------|-------------|
|1 jan  |    271      |
|2 jan  |    150,9    |
|.....  |    .....    |
|1 fév  |    199,3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Créer des classes et définir des chemins

Définissez à présent vos structures de données de classe d’entrée et de prédiction.

Ajoutez une nouvelle classe à votre projet :

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter > Nouvel élément**.

2. Dans la **boîte de dialogue Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez le champ **Nom** par *ProductSalesData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

   Le fichier *ProductSalesData.cs* s’ouvre dans l’éditeur de code.

3. Ajoutez l’instruction `using` suivante en haut de *ProductSalesData.cs* :

   ```csharp
   using Microsoft.ML.Data;
   ```

4. Supprimez la définition de classe existante et ajoutez le code suivant, lequel contient deux classes (`ProductSalesData` et `ProductSalesPrediction`), au fichier *ProductSalesData.cs* :

    [!code-csharp[DeclareTypes](./snippets/sales-anomaly-detection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    `ProductSalesData` spécifie une classe de données d’entrée. L’attribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) spécifie les colonnes (par index de colonne) du jeu de données qui doivent être chargées.

    `ProductSalesPrediction` spécifie la classe de données de prédiction. Pour la détection d’anomalies, la prédiction est constituée d’une alerte indiquant s’il existe une anomalie, un score brut et une p-value. Plus la p-value est proche de 0, plus il est probable qu’une anomalie existe.

5. Créez deux champs globaux pour le chemin du fichier de jeu de données téléchargé et celui du fichier de modèle enregistré :

    * `_dataPath` contient le chemin d’accès au jeu de données utilisé pour l’apprentissage du modèle.
    * `_docsize` contient le nombre d’enregistrements dans le fichier de jeu de données. Vous allez utiliser `_docSize` pour calculer `pvalueHistoryLength`.

6. Ajoutez le code suivant à la ligne juste au-dessus de la méthode `Main` pour spécifier ces chemins :

    [!code-csharp[Declare global variables](./snippets/sales-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a>Initialiser les variables dans Principal

1. Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable `mlContext` :

    [!code-csharp[CreateMLContext](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

### <a name="load-the-data"></a>Chargement des données

Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView). `IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte). Les données peuvent être chargées à partir d’un fichier texte ou d’autres sources (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.

1. Ajoutez le code suivant comme prochaine ligne de la méthode `Main()` :

    [!code-csharp[LoadData](./snippets/sales-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier. Elle prend les variables de chemin de données et retourne un `IDataView`.

## <a name="time-series-anomaly-detection"></a>Détection des anomalies de série chronologique

La détection d’anomalies signale des événements ou comportements inattendus ou inhabituels. Elle fournit des indices sur la localisation des problèmes potentiels et vous aide à déterminer si une situation est « étrange ».

![Exemple de détection d’anomalie « est-ce étrange ».](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

La détection d’anomalie est le processus d’identification des valeurs hors norme dans une série chronologique donnée, c’est-à-dire les points dont le comportement est inattendu ou « étrange ».

La détection d’anomalie peut se révéler utile dans de nombreux cas. Exemple :

Si vous disposez d’une voiture, vous souhaiterez peut-être en savoir : cette jauge d’huile est-elle normale ou est-ce que j’ai une fuite ?
Si vous surveillez la consommation d’énergie, voulez-vous en savoir : existe-t-il une panne ?

Vous pouvez détecter deux types d’anomalies dans les séries chronologiques :

* Un **pic** correspond à la poussée temporaire d’un comportement anormal dans le système.

* Un **point de changement** indique le début d’un changement persistant dans le système.

Dans ML.NET, les algorithmes de détection de pic ou de point de changement IID sont adaptés aux [jeux de données indépendants et identiquement distribués](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).

Contrairement aux modèles des autres tutoriels, les transformations du détecteur d’anomalies de série chronologique opèrent directement sur les données d’entrée. La méthode `IEstimator.Fit()` n’a pas besoin de données d’entraînement pour produire la transformation. Toutefois, elle a besoin du schéma de données, qui est fourni par une vue de données générée à partir d’une liste vide de `ProductSalesData`.

Vous allez analyser les mêmes données de ventes d’un produit pour détecter les pics et les points de changement. Le processus de génération et d’entraînement du modèle est le même pour la détection des pics et des points de changement ; la principale différence réside dans l’algorithme de détection utilisé.

## <a name="spike-detection"></a>Détection des pics

L’objectif est d’identifier les poussées d’activité, par définition soudaines et temporaires, qui diffèrent considérablement de la majorité des valeurs de données de la série chronologique. Il est important de détecter au plus vite ces éléments, événements ou constats suspects pour pouvoir les minimiser. Vous pouvez utiliser l’approche suivante pour détecter de nombreuses anomalies, notamment des pannes, des cyberattaques et du contenu web viral. L’image suivante illustre des pics dans le jeu de données d’une série chronologique :

![Capture d’écran montrant deux détections pic.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a>Ajouter la méthode CreateEmptyDataView()

Ajoutez la méthode suivante à `Program.cs` :

[!code-csharp[CreateEmptyDataView](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEmptyDataView)]

La méthode `CreateEmptyDataView()` produit un objet de vue de données vide avec le bon schéma à utiliser comme entrée à la méthode `IEstimator.Fit()`.

### <a name="create-the-detectspike-method"></a>Créer la méthode DetectSpike()

La méthode `DetectSpike()` :

* Crée la transformation à partir de l’estimateur.
* Détecte les pics par rapport aux données de ventes historiques.
* Affiche les résultats.

1. Créez la méthode `DetectSpike()` juste après la méthode `Main()`, en utilisant le code suivant :

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. Utilisez [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) pour entraîner le modèle à la détection de pics. Ajoutez-le à la méthode `DetectSpike()` avec le code suivant :

    [!code-csharp[AddSpikeTrainer](./snippets/sales-anomaly-detection/csharp/Program.cs#AddSpikeTrainer)]

1. Créez la transformation de détection de pics en ajoutant ce qui suit comme ligne de code suivante dans la méthode `DetectSpike()` :

    [!code-csharp[TrainModel1](./snippets/sales-anomaly-detection/csharp/Program.cs#TrainModel1)]

1. Ajoutez la ligne de code suivante pour transformer les données `productSales` comme prochaine ligne de la méthode `DetectSpike()` :

    [!code-csharp[TransformData1](./snippets/sales-anomaly-detection/csharp/Program.cs#TransformData1)]

    Le code précédent utilise la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) pour prédire plusieurs lignes d’entrée d’un jeu de données.

1. Convertissez votre `transformedData` en un type fortement typé `IEnumerable` pour un affichage plus facile à l’aide de la méthode [CreateEnumerable ()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) avec le code suivant :

    [!code-csharp[CreateEnumerable1](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEnumerable1)]

1. Créez une ligne d’en-tête d’affichage à l’aide du code <xref:System.Console.WriteLine?displayProperty=nameWithType> suivant :

    [!code-csharp[DisplayHeader1](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayHeader1)]

    Les informations suivantes apparaissent dans vos résultats de détection des pics :

    * `Alert` indique une alerte de pic pour un point de données spécifique.
    * `Score` est la valeur de `ProductSales` pour un point de données spécifique dans le jeu de données.
    * `P-Value` où « P » correspond à la probabilité. Plus la p-value est proche de 0, plus il est probable que le point de données soit une anomalie.

1. Utilisez le code suivant pour itérer au sein de `predictions` `IEnumerable` et afficher les résultats :

    [!code-csharp[DisplayResults1](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayResults1)]

1. Ajoutez l’appel à la méthode `DetectSpike()` dans la méthode `Main()` :

    [!code-csharp[CallDetectSpike](./snippets/sales-anomaly-detection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a>Résultats de la détection des pics

Vos résultats doivent être similaires à ce qui suit. Durant le processus, des messages sont affichés. Vous pouvez voir des avertissements ou des messages de traitement. Certains messages ont été supprimés des résultats suivants par souci de clarté.

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a>Détection des points de changement

Les points de changement (`Change points`) indiquent des changements persistants dans la distribution de valeurs d’un flux d’événements d’une série chronologique, comme des changements de niveau ou des tendances. Ces changements persistants durent beaucoup plus longtemps que les pics (`spikes`) et peuvent indiquer des événements catastrophiques. `Change points` ne sont généralement pas visibles à l’œil nu, mais vous pouvez les détecter dans vos données à l’aide d’approches comme celles décrites dans la méthode suivante.  L’image suivante illustre la détection des points de changement :

![Capture d’écran montrant une détection de point de modification.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a>Créer la méthode DetectChangepoint()

La méthode `DetectChangepoint()` exécute les tâches suivantes :

* Crée la transformation à partir de l’estimateur.
* Détecte les points de changement par rapport aux données de ventes historiques.
* Affiche les résultats.

1. Créez la méthode `DetectChangepoint()` juste après la méthode `Main()`, en utilisant le code suivant :

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. Créez [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) dans la méthode `DetectChangepoint()` avec le code suivant :

    [!code-csharp[AddChangepointTrainer](./snippets/sales-anomaly-detection/csharp/Program.cs#AddChangepointTrainer)]

1. Comme vous l’avez fait précédemment, créez la transformation à partir de l’estimateur en ajoutant la ligne de code suivante dans la méthode `DetectChangePoint()` :

    [!code-csharp[TrainModel2](./snippets/sales-anomaly-detection/csharp/Program.cs#TrainModel2)]

1. Utilisez la méthode `Transform()` pour transformer les données en ajoutant le code suivant à `DetectChangePoint()` :

    [!code-csharp[TransformData2](./snippets/sales-anomaly-detection/csharp/Program.cs#TransformData2)]

1. Comme vous l’avez fait précédemment, convertissez votre `transformedData` en un type fortement typé `IEnumerable` pour un affichage plus facile à l’aide de la `CreateEnumerable()` méthode avec le code suivant :

    [!code-csharp[CreateEnumerable2](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEnumerable2)]

1. Créez un en-tête d’affichage en ajoutant la ligne de code suivante comme prochaine ligne de la méthode `DetectChangePoint()` :

    [!code-csharp[DisplayHeader2](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayHeader2)]

    Les informations suivantes apparaissent dans vos résultats de détection des points de changement :

    * `Alert` indique une alerte de point de changement pour un point de données spécifique.
    * `Score` est la valeur de `ProductSales` pour un point de données spécifique dans le jeu de données.
    * `P-Value` où « P » correspond à la probabilité. Plus la P-value est proche de 0, plus il est probable que le point de données soit une anomalie.
    * `Martingale value` permet d’identifier le « degré d’étrangeté » d’un point de données en fonction de la séquence de valeurs P.

1. Itérez au sein de `predictions` `IEnumerable` et affichez les résultats avec le code suivant :

    [!code-csharp[DisplayResults2](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayResults2)]

1. Ajoutez l’appel suivant à la méthode `DetectChangepoint()` dans la méthode `Main()` :

    [!code-csharp[CallDetectChangepoint](./snippets/sales-anomaly-detection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a>Résultats de la détection des points de changement

Vos résultats doivent être similaires à ce qui suit. Durant le processus, des messages sont affichés. Vous pouvez voir des avertissements ou des messages de traitement. Certains messages ont été supprimés des résultats suivants par souci de clarté.

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

Félicitations ! Vous venez de générer des modèles de machine learning pour détecter des anomalies (pics et points de changement) dans des données de ventes.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Chargement des données
> * Entraîner le modèle pour détecter des pics
> * Détecter des pics avec le modèle entraîné
> * Entraîner le modèle pour détecter des points de changement
> * Détecter des points de changement avec le modèle entraîné

## <a name="next-steps"></a>Étapes suivantes

Consultez le dépôt GitHub d’exemples de machine learning pour explorer un exemple de détection d’anomalie dans le domaine de la consommation d’énergie.
> [!div class="nextstepaction"]
> [Référentiel GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
