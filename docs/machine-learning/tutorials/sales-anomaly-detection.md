---
title: 'Didacticiel : Détecter les anomalies dans les ventes de produits'
description: Découvrez comment créer une application de détection des anomalies pour des données de ventes de produit. Ce didacticiel crée une application de console .NET Core à l’aide de C# dans Visual Studio 2019.
ms.date: 07/17/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: e87034733b048153202bc11ab94ed7605749f60c
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331697"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a>Didacticiel : Détecter les anomalies dans les ventes de produits avec ML.NET

Découvrez comment créer une application de détection des anomalies pour des données de ventes de produit. Ce didacticiel crée une application de console .NET Core à l’aide de C# dans Visual Studio.

Ce tutoriel vous montre comment effectuer les opérations suivantes :
> [!div class="checklist"]
> * Chargement des données
> * Entraîner le modèle pour détecter des pics
> * Détecter des pics avec le modèle entraîné
> * Entraîner le modèle pour détecter des points de changement
> * Détecter des points de changement avec le modèle entraîné

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).

## <a name="prerequisites"></a>Prérequis

* [Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), avec la charge de travail « Développement multiplateforme .Net Core » installée.

* [Jeu de données product-sales.csv](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Le format de données dans `product-sales.csv` est basé sur le jeu de données « Shampoo Sales Over a Three Year Period », disponible sur DataMarket et fourni dans la bibliothèque TSDL (Time Series Data Library) créée par Rob Hyndman. Ce jeu de données est concédé sous la licence Open par défaut de DataMarket.

## <a name="create-a-console-application"></a>Création d’une application console

1. Créez une **application console .NET Core** appelée « ProductSalesAnomalyDetection ».

2. Créez un répertoire nommé *Data* dans votre projet pour enregistrer les fichiers du jeu de données.

3. Installez le **package NuGet Microsoft.ML** :

    Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ML**, sélectionnez le package **v1.0.0** dans la liste, puis cliquez sur le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés. Répétez ces étapes pour **Microsoft.ML.TimeSeries v0.12.0**.

4. Ajoutez les instructions `using` suivantes en tête de votre fichier *Program.cs* :

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Télécharger vos données

1. Téléchargez le jeu de données et enregistrez-le dans le dossier *Data* précédemment créé :

   * Cliquez avec le bouton droit sur [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) et sélectionnez « Enregistrer le lien (ou la cible) sous... ».

     Veillez à enregistrer le fichier \*.csv dans le dossier *Data* ou, si vous l’avez enregistré ailleurs, à déplacer le fichier \*.csv dans le dossier *Data*.

2. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier \*.csv et sélectionnez **Propriétés**. Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.

Le tableau suivant présente un aperçu des données de votre fichier \*.csv :

|Mois  |ProductSales |
|-------|-------------|
|1 jan  |    271      |
|2 jan  |    150,9    |
|.....  |    .....    |
|1 fév  |    199,3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Créer des classes et définir des chemins

Définissez à présent la structure de données de votre classe d’entrée.

Ajoutez une nouvelle classe à votre projet :

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter > Nouvel élément**.

2. Dans la **boîte de dialogue Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez le champ **Nom** par *ProductSalesData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

Le fichier *ProductSalesData.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction `using` suivante en haut de *ProductSalesData.cs* :

```csharp
using Microsoft.ML.Data;
```

Supprimez la définition de classe existante et ajoutez le code suivant, lequel contient deux classes (`ProductSalesData` et `ProductSalesPrediction`), au fichier *ProductSalesData.cs* :

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

`ProductSalesData` spécifie une classe de données d’entrée. L’attribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) spécifie les colonnes (par index de colonne) du jeu de données qui doivent être chargées. 

Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

Il faut créer deux champs globaux pour le chemin d’accès du fichier de jeu de données téléchargé et celui du fichier de modèle enregistré :

* `_dataPath` contient le chemin d’accès au jeu de données utilisé pour l’apprentissage du modèle.
* `_docsize` contient le nombre d’enregistrements dans le fichier de jeu de données. Vous allez l’utiliser pour calculer `pvalueHistoryLength`.

Ajoutez le code suivant à la ligne juste au-dessus de la méthode `Main` pour spécifier ces chemins :

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

### <a name="initialize-variables-in-main"></a>Initialiser les variables dans Principal

Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable `mlContext` :

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a>Chargement des données

Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView). `IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte). Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`. Ajoutez le code suivant comme prochaine ligne de la méthode `Main()` :

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier. Elle prend les variables de chemin de données et retourne un `IDataView`.

## <a name="ml-task---time-series-anomaly-detection"></a>Tâche ML - Détection d’anomalie dans une série chronologique 

La détection d’anomalie signale des événements ou des comportements inattendus ou inhabituels. Elle fournit des indices sur la localisation des problèmes potentiels et vous aide à déterminer si une situation est « étrange ».

![Cette situation est-elle étrange ?](./media/sales-anomaly-detection/anomalydetection.png)

La détection d’anomalie est le processus d’identification des valeurs hors norme dans une série chronologique donnée, c’est-à-dire les points dont le comportement est inattendu ou « étrange ».

Cela peut être utile à bien des égards. Exemple :

Si vous avez une voiture, il est bon de savoir si l’indicateur de niveau d’huile est normal ou si vous avez une fuite.
Si vous analysez la consommation d’énergie, il est important de connaître l’existence d’une panne.

Vous pouvez détecter deux types d’anomalies dans les séries chronologiques : 

* Un **pic** correspond à la poussée temporaire d’un comportement anormal dans le système. 

* Un **point de changement** indique le début d’un changement persistant dans le système. 

Dans ML.NET, les algorithmes de détection de pic ou de point de changement IID sont adaptés aux [jeux de données indépendants et identiquement distribués](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables). 

Vous allez analyser les mêmes données de ventes d’un produit pour détecter les pics et les points de changement. Le processus de génération et d’entraînement du modèle est le même pour la détection des pics et des points de changement ; la principale différence réside dans l’algorithme de détection utilisé.

## <a name="spike-detection"></a>Détection des pics 

L’objectif est d’identifier les poussées d’activité, par définition soudaines et temporaires, qui diffèrent considérablement de la majorité des valeurs de données de la série chronologique. Il est important de détecter au plus vite ces éléments, événements ou constats suspects pour pouvoir les minimiser. Vous pouvez utiliser l’approche suivante pour détecter de nombreuses anomalies, notamment des pannes, des cyberattaques et du contenu web viral. L’image suivante illustre des pics dans le jeu de données d’une série chronologique :

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a>Créer la méthode DetectSpike()

Ajoutez l’appel suivant à la méthode `DetectSpike()` comme prochaine ligne de code dans la méthode `Main()` :

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

La méthode `DetectSpike()` exécute les tâches suivantes :

* Effectue l’apprentissage du modèle.
* Détecte les pics par rapport aux données de ventes historiques.
* Affiche les résultats.

Créez la méthode `DetectSpike()` juste après la méthode `Main()`, en utilisant le code suivant :

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

Utilisez [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) pour entraîner le modèle à la détection de pics. Ajoutez-le à la méthode `DetectSpike()` avec le code suivant :

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

Ajustez le modèle aux données `productSales` en ajoutant la ligne de code suivante dans la méthode `DetectSpike()` :

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

La méthode [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) entraîne votre modèle en transformant le jeu de données et en appliquant l’entraînement.

Ajoutez la ligne de code suivante pour transformer les données `productSales` comme prochaine ligne de la méthode `DetectSpike()` :

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

Le code précédent utilise la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) pour prédire plusieurs lignes d’entrée d’un jeu de données de test.

Convertissez vos données `transformedData` en `IEnumerable` fortement typé pour faciliter l’affichage. Utilisez pour cela la méthode [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) avec le code suivant :

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

Créez une ligne d’en-tête d’affichage à l’aide du code <xref:System.Console.WriteLine?displayProperty=nameWithType> suivant :

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

Les informations suivantes apparaissent dans vos résultats de détection des pics :

* `Alert` indique une alerte de pic pour un point de données spécifique.

* `Score` est la valeur de `ProductSales` pour un point de données spécifique dans le jeu de données.

* `P-Value` où « P » correspond à la probabilité. Il s’agit de la probabilité selon laquelle ce point de données constitue une anomalie. 

Utilisez le code suivant pour effectuer une itération dans le `IEnumerable` `predictions` et afficher les résultats :

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a>Résultats de la détection des pics

Vos résultats doivent être similaires à ce qui suit. Durant le processus, des messages sont affichés. Vous pouvez voir des avertissements ou des messages de traitement. Ils ont été supprimés des résultats ci-dessous par souci de clarté.

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

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a>Créer la méthode DetectChangepoint()

Ajoutez l’appel suivant à la méthode `DetectChangepoint()` comme prochaine ligne de code dans la méthode `Main()` :

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

La méthode `DetectChangepoint()` exécute les tâches suivantes :

* Effectue l’apprentissage du modèle.
* Détecte les points de changement par rapport aux données de ventes historiques.
* Affiche les résultats.

Créez la méthode `DetectChangepoint()` juste après la méthode `Main()`, en utilisant le code suivant :

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

Utilisez [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) pour entraîner le modèle à détecter les points de changement. Ajoutez-le à la méthode `DetectChangepoint()` avec le code suivant :

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

Comme vous l’avez fait précédemment, ajustez le modèle aux données `productSales` en ajoutant la ligne de code suivante dans la méthode `DetectChangePoint()` :

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

Utilisez la méthode `Transform()` pour transformer les données `Training` en ajoutant le code suivant à `DetectChangePoint()` :

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

Comme précédemment, convertissez vos données `transformedData` en `IEnumerable` fortement typé pour faciliter l’affichage. Utilisez pour cela la méthode `CreateEnumerable()` avec le code suivant :

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

Créez un en-tête d’affichage en ajoutant la ligne de code suivante comme prochaine ligne de la méthode `DetectChangePoint()` :

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

Les informations suivantes apparaissent dans vos résultats de détection des points de changement :

* `Alert` indique une alerte de point de changement pour un point de données spécifique.
* `Score` est la valeur de `ProductSales` pour un point de données spécifique dans le jeu de données.
* `P-Value` où « P » correspond à la probabilité. Il s’agit de la probabilité selon laquelle ce point de données constitue une anomalie. 
* `Martingale value` permet d’identifier le « degré d’étrangeté » d’un point de données en fonction de la séquence de valeurs P.  

Effectuez une itération dans le `IEnumerable` `predictions` et affichez les résultats avec le code suivant :

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a>Résultats de la détection des points de changement

Vos résultats doivent être similaires à ce qui suit. Durant le processus, des messages sont affichés. Vous pouvez voir des avertissements ou des messages de traitement. Ils ont été supprimés des résultats ci-dessous par souci de clarté.

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

Félicitations ! Vous venez de générer des modèles de machine learning pour détecter des anomalies (pics et points de changement) dans des données de ventes.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).

Dans ce tutoriel, vous avez appris à :
> [!div class="checklist"]
> * Chargement des données
> * Entraîner le modèle pour détecter des pics
> * Détecter des pics avec le modèle entraîné
> * Entraîner le modèle pour détecter des points de changement
> * Détecter des points de changement avec le modèle entraîné

## <a name="next-steps"></a>Étapes suivantes

Consultez le dépôt GitHub d’exemples de machine learning pour explorer un exemple de détection d’anomalie dans le domaine de la consommation d’énergie.
> [!div class="nextstepaction"]
> [Référentiel GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
