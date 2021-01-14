---
title: 'Didacticiel : détecter les anomalies dans les appels téléphoniques'
description: Découvrez comment créer une application de détection des anomalies pour les données de séries chronologiques. Ce didacticiel crée une application de console .NET Core à l’aide de C# dans Visual Studio 2019.
ms.date: 12/04/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: f001cb912bb695a7edb0917f3306ca9bfbe311ac
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187780"
---
# <a name="tutorial-detect-anomalies-in-time-series-with-mlnet"></a>Didacticiel : détecter les anomalies dans les séries chronologiques avec ML.NET

Découvrez comment créer une application de détection des anomalies pour les données de séries chronologiques. Ce didacticiel crée une application de console .NET Core à l’aide de C# dans Visual Studio 2019.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> * Chargement des données
> * Détecter une période pour une série chronologique
> * Détectez les anomalies pour une série chronologique périodique

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection).

## <a name="prerequisites"></a>Prérequis

* [Visual Studio 2019 version 16.7.8 ou ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail « développement multiplateforme .net Core » installée.

* [Jeu de données phone-calls.csv](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv).

## <a name="create-a-console-application"></a>Création d’une application console

1. Créez une **application console C# .net Core** appelée « ProductSalesAnomalyDetection ».

2. Créez un répertoire nommé *Data* dans votre projet pour enregistrer les fichiers de votre jeu de données.

3. Installez le **package NuGet Microsoft.ML** :

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ml** , puis sélectionnez le bouton **installer** . Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés. Répétez ces étapes pour **Microsoft. ml. TimeSeries**.

4. Ajoutez les instructions `using` suivantes en tête de votre fichier *Program.cs* :

    [!code-csharp[AddUsings](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Télécharger vos données

1. Téléchargez le jeu de données et enregistrez-le dans le dossier *Data* précédemment créé :

    Cliquez avec le bouton droit sur [*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv) , puis sélectionnez « Enregistrer le lien (ou la cible) en tant que... »

     Veillez à enregistrer le fichier \*.csv dans le dossier *Data* ou, si vous l’avez enregistré ailleurs, à déplacer le fichier \*.csv dans le dossier *Data*.

2. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier \*.csv et sélectionnez **Propriétés**. Sous **avancé**, remplacez la valeur de **copier dans le répertoire de sortie** par **copier si plus récent**.

Le tableau suivant présente un aperçu des données de votre fichier \*.csv :

| timestamp  | value |
|--------|--------------|
| 2018/9/3  | 36,69670857  |
| 2018/9/4  | 35,74160571  |
| .....  | .....  |
| 2018/10/3  | 34,49893429  |
| ...    | ....   |

Ce fichier représente une série chronologique. Chaque ligne du fichier est un point de données. Chaque point de données a deux attributs, à savoir, `timestamp` et `value` , pour représenter le nombre d’appels téléphoniques à chaque jour. Le nombre d’appels téléphoniques est transformé en désensitivation.

### <a name="create-classes-and-define-paths"></a>Créer des classes et définir des chemins

Définissez à présent vos structures de données de classe d’entrée et de prédiction.

Ajoutez une nouvelle classe à votre projet :

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter > Nouvel élément**.

2. Dans la **boîte de dialogue Ajouter un nouvel élément**, sélectionnez **classe** et modifiez le champ **nom** en *PhoneCallsData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

   Le fichier *PhoneCallsData.cs* s’ouvre dans l’éditeur de code.

3. Ajoutez l' `using` instruction suivante en haut de *PhoneCallsData.cs*:

   ```csharp
   using Microsoft.ML.Data;
   ```

4. Supprimez la définition de classe existante et ajoutez le code suivant, qui a deux classes `PhoneCallsData` et `PhoneCallsPrediction` , au fichier *PhoneCallsData.cs* :

    [!code-csharp[DeclareTypes](./snippets/phone-calls-anomaly-detection/csharp/PhoneCallsData.cs#DeclareTypes "Declare data record types")]

    `PhoneCallsData` spécifie une classe de données d’entrée. L’attribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) spécifie les colonnes (par index de colonne) du jeu de données qui doivent être chargées. Il a deux attributs `timestamp` et `value` qui correspondent aux mêmes attributs dans le fichier de données.

    `PhoneCallsPrediction` spécifie la classe de données de prédiction. Pour le détecteur SR-CNN, la prédiction dépend du [mode de détection](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode) spécifié. Dans cet exemple, nous sélectionnons le `AnomalyAndMargin` mode. La sortie contient sept colonnes. Dans la plupart des cas,,,, `IsAnomaly` `ExpectedValue` `UpperBoundary` et `LowerBoundary` sont suffisamment informatifs. Ils vous indiquent si un point est une anomalie, la valeur attendue du point et la région de limite inférieure/supérieure du point.

5. Ajoutez le code suivant à la ligne située juste au-dessus de la `Main` méthode pour spécifier le chemin d’accès à votre fichier de données :

    [!code-csharp[Declare global variables](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a>Initialiser les variables dans Principal

1. Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable `mlContext` :

    [!code-csharp[CreateMLContext](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

### <a name="load-the-data"></a>Chargement des données

Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView). `IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte). Les données peuvent être chargées à partir d’un fichier texte ou d’autres sources (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.

1. Ajoutez le code suivant comme prochaine ligne de la méthode `Main` :

    [!code-csharp[LoadData](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier. Elle prend les variables de chemin de données et retourne un `IDataView`.

## <a name="time-series-anomaly-detection"></a>Détection des anomalies de série chronologique

La détection des anomalies de série chronologique est le processus de détection des valeurs hors norme des données de série chronologique ; pointe sur une série chronologique d’entrée donnée où le comportement n’est pas celui attendu, ou « bizarre ». Ces anomalies sont généralement indicatives de certains événements intéressants dans le domaine du problème : une attaque contre les attaques contre les comptes d’utilisateur, une panne de courant, une augmentation de RPS sur un serveur, une fuite de mémoire, etc.

Pour rechercher des anomalies sur les séries chronologiques, vous devez d’abord déterminer la période de la série. Ensuite, la série chronologique peut être décomposée en plusieurs composants en tant que `Y = T + S + R` , où `Y` est la série d’origine, `T` est le composant de tendance, `S` est le composant saisonnier et `R` est la composante résiduelle de la série. Cette étape est appelée [décomposition](https://en.wikipedia.org/wiki/Decomposition_of_time_series). Enfin, la détection est effectuée sur le composant résiduel pour rechercher les anomalies. Dans ML.NET, l’algorithme SR-CNN est un algorithme avancé et un nouvel algorithme basé sur les réseaux de neurones spectraux et de convolution (CNN) pour détecter les anomalies dans les séries chronologiques. Pour plus d’informations sur cet algorithme, consultez [service de détection des anomalies de série chronologique chez Microsoft](https://arxiv.org/pdf/1906.03821.pdf).

Dans ce didacticiel, vous verrez que ces procédures peuvent être effectuées à l’aide de deux fonctions.

## <a name="detect-period"></a>Période de détection

Dans la première étape, nous invoquons la `DetectSeasonality` fonction pour déterminer la période de la série.

### <a name="create-the-detectperiod-method"></a>Créer la méthode DetectPeriod

1. Créez la `DetectPeriod` méthode, juste en dessous de la `Main` méthode, à l’aide du code suivant :

    ```csharp
    static void DetectPeriod(MLContext mlContext, IDataView phoneCalls)
    {

    }
    ```

2. Utilisez la <xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A> fonction pour détecter une période. Ajoutez-le à la méthode `DetectPeriod` avec le code suivant :

    [!code-csharp[DetectSeasonality](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectSeasonality)]

3. Affichez la valeur de période en ajoutant le code suivant à la ligne de code suivante dans la `DetectPeriod` méthode :

    [!code-csharp[DisplayPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayPeriod)]

4. Ajoutez l’appel suivant à la `DetectPeriod` méthode dans la `Main` méthode :

    [!code-csharp[CallDetectPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectPeriod)]

### <a name="period-detection-results"></a>Résultats de la détection de période

Exécutez l'application. Vos résultats doivent être similaires à ce qui suit.

```console
Period of the series is: 7.
```

## <a name="detect-anomaly"></a>Détecter les anomalies

Dans cette étape, vous utilisez la <xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> méthode pour rechercher des anomalies.

### <a name="create-the-detectanomaly-method"></a>Créer la méthode DetectAnomaly

1. Créez la `DetectAnomaly` méthode, juste en dessous de la `DetectPeriod` méthode, à l’aide du code suivant :

    ```csharp
    static void DetectAnomaly(MLContext mlContext, IDataView phoneCalls, int period)
    {

    }
    ```

2. Configurez <xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> dans la `DetectAnomaly` méthode avec le code suivant :

    [!code-csharp[SetupSrCnnParameters](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#SetupSrCnnParameters)]

3. Pour détecter les anomalies par algorithme SR-CNN, ajoutez la ligne de code suivante dans la `DetectAnomaly` méthode :

    [!code-csharp[DetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectAnomaly)]

4. Convertissez la vue des données de sortie en un type fortement typé `IEnumerable` pour faciliter l’affichage à l’aide de la [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) méthode avec le code suivant :

    [!code-csharp[CreateEnumerableForResult](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateEnumerableForResult)]

5. Créez un en-tête d’affichage en ajoutant la ligne de code suivante comme prochaine ligne de la méthode `DetectAnomaly` :

    [!code-csharp[DisplayHeader](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayHeader)]

    Les informations suivantes apparaissent dans vos résultats de détection des points de changement :

    * `Index` est l’index de chaque point.
    * `Anomaly` indique si chaque point est détecté comme une anomalie.
    * `ExpectedValue` valeur estimée de chaque point.
    * `LowerBoundary` est la valeur la plus faible que chaque point peut être de ne pas être une anomalie.
    * `UpperBoundary` est la valeur la plus élevée que chaque point peut être de ne pas être une anomalie.

6. Itérez au sein de `predictions` `IEnumerable` et affichez les résultats avec le code suivant :

    [!code-csharp[DisplayAnomalyDetectionResults](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayAnomalyDetectionResults)]

7. Ajoutez l’appel suivant à la `DetectAnomaly` méthode dans la `Main` méthode :

    [!code-csharp[CallDetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectAnomaly)]

## <a name="anomaly-detection-results"></a>Résultats de la détection d’anomalies

Exécutez l'application. Vos résultats doivent être similaires à ce qui suit. Durant le processus, des messages sont affichés. Vous pouvez voir des avertissements ou des messages de traitement. Certains messages ont été supprimés des résultats suivants par souci de clarté.

```console
Detect period of the series
Period of the series is: 7.
Detect anomaly points in the series
Index   Data    Anomaly AnomalyScore    Mag     ExpectedValue   BoundaryUnit    UpperBoundary   LowerBoundary
0,0,36.841787256739266,41.14206982401966,32.541504689458876
1,0,35.67303618137362,39.97331874865401,31.372753614093227
2,0,34.710132999891826,39.029491313022824,30.390774686760828
3,0,33.44765248883495,37.786086547816545,29.10921842985335
4,0,28.937110922276364,33.25646923540736,24.61775260914537
5,0,5.143895892785781,9.444178460066171,0.843613325505391
6,0,5.163325228419392,9.463607795699783,0.8630426611390014
7,0,36.76414836240396,41.06443092968435,32.46386579512357
8,0,35.77908590657007,40.07936847385046,31.478803339289676
9,0,34.547259536635245,38.847542103915636,30.246976969354854
10,0,33.55193524820608,37.871293561337076,29.23257693507508
11,0,29.091800129624648,33.392082696905035,24.79151756234426
12,0,5.154836630338823,9.455119197619213,0.8545540630584334
13,0,5.234332502492464,9.534615069772855,0.934049935212073
14,0,36.54992549471526,40.85020806199565,32.24964292743487
15,0,35.79526470980883,40.095547277089224,31.494982142528443
16,0,34.34099013096804,38.64127269824843,30.040707563687647
17,0,33.61201516582131,37.9122977331017,29.31173259854092
18,0,29.223563320561812,33.5238458878422,24.923280753281425
19,0,5.170512168851533,9.470794736131923,0.8702296015711433
20,0,5.2614938889462834,9.561776456226674,0.9612113216658926
21,0,36.37103858487317,40.67132115215356,32.07075601759278
22,0,35.813544599026855,40.113827166307246,31.513262031746464
23,0,34.05600492733225,38.356287494612644,29.755722360051863
24,0,33.65828319077884,37.95856575805923,29.358000623498448
25,0,29.381125690882463,33.681408258162854,25.080843123602072
26,0,5.261543539820418,9.561826107100808,0.9612609725400283
27,0,5.4873712582971805,9.787653825577571,1.1870886910167897
28,1,36.504694001629254,40.804976568909645,32.20441143434886  <-- alert is on, detected anomaly
...
```

Félicitations ! Vous avez maintenant réussi à créer des modèles de Machine Learning pour détecter les périodes et les anomalies sur une série périodique.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection).

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Chargement des données
> * Détecter la période sur les données de la série chronologique
> * Détecter les anomalies sur les données de série chronologique

## <a name="next-steps"></a>Étapes suivantes

Consultez le dépôt GitHub d’exemples de machine learning pour explorer un exemple de détection d’anomalie dans le domaine de la consommation d’énergie.
> [!div class="nextstepaction"]
> [Référentiel GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
