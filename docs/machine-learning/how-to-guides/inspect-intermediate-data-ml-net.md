---
title: Inspecter les données intermédiaires pendant le traitement dans ML.NET
description: Découvrez comment inspecter les données intermédiaires pendant les étapes de chargement, de traitement et d’entraînement du modèle du pipeline Machine Learning de ML.NET.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 11df1d5caaa7b7974360d863f85afbff18985e47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977091"
---
# <a name="inspect-intermediate-data-during-processing"></a><span data-ttu-id="7c975-103">Inspecter les données intermédiaires pendant le traitement</span><span class="sxs-lookup"><span data-stu-id="7c975-103">Inspect intermediate data during processing</span></span>

<span data-ttu-id="7c975-104">Découvrez comment inspecter les données intermédiaires pendant les étapes de chargement, de traitement et d’entraînement du modèle dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="7c975-104">Learn how to inspect intermediate data during loading, processing, and model training steps in ML.NET.</span></span> <span data-ttu-id="7c975-105">Les données intermédiaires sont les résultats de chaque étape dans le pipeline Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="7c975-105">Intermediate data is the output of each stage in the machine learning pipeline.</span></span>

<span data-ttu-id="7c975-106">Les données intermédiaires comme celle représentée [`IDataView`](xref:Microsoft.ML.IDataView) ci-dessous qui est chargée dans un peut être inspectée de diverses façons dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="7c975-106">Intermediate data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="7c975-107">Convertir IDataView en IEnumerable</span><span class="sxs-lookup"><span data-stu-id="7c975-107">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="7c975-108">Une des façons les plus [`IDataView`](xref:Microsoft.ML.IDataView) rapides d’inspecter un est de le convertir en un [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="7c975-108">One of the quickest ways to inspect an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="7c975-109">Pour convertir [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) un [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) pour utiliser la méthode.</span><span class="sxs-lookup"><span data-stu-id="7c975-109">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

<span data-ttu-id="7c975-110">Pour optimiser les performances, définissez `reuseRowObject` sur `true`.</span><span class="sxs-lookup"><span data-stu-id="7c975-110">To optimize performance, set `reuseRowObject` to `true`.</span></span> <span data-ttu-id="7c975-111">Cette opération remplit tardivement le même objet avec les données de la ligne actuelle au moment de son évaluation, par opposition à la création d’un objet pour chaque ligne dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="7c975-111">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

```csharp
// Create an IEnumerable of HousingData objects from IDataView
IEnumerable<HousingData> housingDataEnumerable =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: true);

// Iterate over each row
foreach (HousingData row in housingDataEnumerable)
{
    // Do something (print out Size property) with current Housing Data object being evaluated
    Console.WriteLine(row.Size);
}
```

## <a name="accessing-specific-indices-with-ienumerable"></a><span data-ttu-id="7c975-112">Accès à des index spécifiques avec IEnumerable</span><span class="sxs-lookup"><span data-stu-id="7c975-112">Accessing specific indices with IEnumerable</span></span>

<span data-ttu-id="7c975-113">Si vous n’avez besoin que d’accéder [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) à une `reuseRowObject` partie `false` des données ou des indices spécifiques, utilisez et définissez la valeur du paramètre pour créer un nouvel objet pour chacune des lignes demandées dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="7c975-113">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="7c975-114">Ensuite, convertissez le [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dans un tableau ou une liste.</span><span class="sxs-lookup"><span data-stu-id="7c975-114">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="7c975-115">La conversion du [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) résultat en un tableau ou [`IDataView`](xref:Microsoft.ML.IDataView) une liste chargera toutes les lignes demandées en mémoire, ce qui peut affecter les performances.</span><span class="sxs-lookup"><span data-stu-id="7c975-115">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="7c975-116">Une fois la collection créée, vous pouvez effectuer des opérations sur les données.</span><span class="sxs-lookup"><span data-stu-id="7c975-116">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="7c975-117">L’extrait de code ci-dessous prend les trois premières lignes du jeu de données et calcule le prix moyen actuel.</span><span class="sxs-lookup"><span data-stu-id="7c975-117">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

```csharp
// Create an Array of HousingData objects from IDataView
HousingData[] housingDataArray =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: false)
        .Take(3)
        .ToArray();

// Calculate Average CurrentPrice of First Three Elements
HousingData firstRow = housingDataArray[0];
HousingData secondRow = housingDataArray[1];
HousingData thirdRow = housingDataArray[2];
float averageCurrentPrice = (firstRow.CurrentPrice + secondRow.CurrentPrice + thirdRow.CurrentPrice) / 3;
```

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="7c975-118">Inspecter les valeurs d’une colonne spécifique</span><span class="sxs-lookup"><span data-stu-id="7c975-118">Inspect values in a single column</span></span>

<span data-ttu-id="7c975-119">À tout moment du processus de construction du [`IDataView`](xref:Microsoft.ML.IDataView) modèle, les valeurs [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) d’une seule colonne d’un peut être consultée à l’aide de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7c975-119">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span> <span data-ttu-id="7c975-120">La [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) méthode renvoie toutes les valeurs [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)dans une seule colonne comme un .</span><span class="sxs-lookup"><span data-stu-id="7c975-120">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="7c975-121">Inspecter les valeurs d’IDataView une ligne à la fois</span><span class="sxs-lookup"><span data-stu-id="7c975-121">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="7c975-122">[`IDataView`](xref:Microsoft.ML.IDataView)est évaluée paresseusement.</span><span class="sxs-lookup"><span data-stu-id="7c975-122">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="7c975-123">Pour itérer sur les lignes [`IDataView`](xref:Microsoft.ML.IDataView) d’un [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) sans convertir en un comme démontré [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) dans les [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) sections précédentes de ce [`IDataView`](xref:Microsoft.ML.IDataView) document, créer un en utilisant la méthode et en passant dans le [DataViewSchema](xref:Microsoft.ML.DataViewSchema) de votre comme un paramètre.</span><span class="sxs-lookup"><span data-stu-id="7c975-123">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="7c975-124">Ensuite, pour itérer sur les [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) rangées, utilisez [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) la méthode du curseur avec les délégués pour extraire les valeurs respectives de chacune des colonnes.</span><span class="sxs-lookup"><span data-stu-id="7c975-124">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c975-125">Pour des raisons de performance, [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) les vecteurs dans ML.NET `Vector`utilisent`float[]`au lieu des types de collecte natifs (c’est-à-dire, , ).</span><span class="sxs-lookup"><span data-stu-id="7c975-125">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span>

```csharp
// Get DataViewSchema of IDataView
DataViewSchema columns = data.Schema;

// Create DataViewCursor
using (DataViewRowCursor cursor = data.GetRowCursor(columns))
{
    // Define variables where extracted values will be stored to
    float size = default;
    VBuffer<float> historicalPrices = default;
    float currentPrice = default;

    // Define delegates for extracting values from columns
    ValueGetter<float> sizeDelegate = cursor.GetGetter<float>(columns[0]);
    ValueGetter<VBuffer<float>> historicalPriceDelegate = cursor.GetGetter<VBuffer<float>>(columns[1]);
    ValueGetter<float> currentPriceDelegate = cursor.GetGetter<float>(columns[2]);

    // Iterate over each row
    while (cursor.MoveNext())
    {
        //Get values from respective columns
        sizeDelegate.Invoke(ref size);
        historicalPriceDelegate.Invoke(ref historicalPrices);
        currentPriceDelegate.Invoke(ref currentPrice);
    }
}
```

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="7c975-126">Obtenir un aperçu du résultat du prétraitement ou de l’entraînement sur un sous-ensemble des données</span><span class="sxs-lookup"><span data-stu-id="7c975-126">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="7c975-127">N’utilisez pas `Preview` dans le code de production, car celui-ci est destiné au débogage et peut réduire les performances.</span><span class="sxs-lookup"><span data-stu-id="7c975-127">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="7c975-128">Le processus de génération de modèle est expérimental et itératif.</span><span class="sxs-lookup"><span data-stu-id="7c975-128">The model building process is experimental and iterative.</span></span> <span data-ttu-id="7c975-129">Pour prévisualiser les données après le pré-traitement ou la formation d’un modèle d’apprentissage automatique sur un sous-ensemble des données, utilisez la [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) méthode qui renvoie un [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span><span class="sxs-lookup"><span data-stu-id="7c975-129">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="7c975-130">Le résultat est `ColumnView` un `RowView` objet avec [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) et des propriétés qui sont à la fois un et contiennent les valeurs dans une colonne ou une rangée particulière.</span><span class="sxs-lookup"><span data-stu-id="7c975-130">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="7c975-131">Spécifiez le nombre de lignes auxquelles appliquer la transformation à l’aide du paramètre `maxRows`.</span><span class="sxs-lookup"><span data-stu-id="7c975-131">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![Débogueur de données : aperçu de l’objet](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="7c975-133">Le résultat de [`IDataView`](xref:Microsoft.ML.IDataView) l’inspection d’un serait similaire à ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="7c975-133">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![Débogueur de données : aperçu de la vue de ligne](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
