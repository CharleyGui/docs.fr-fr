---
title: Inspecter les données intermédiaires pendant le traitement dans ML.NET
description: Découvrez comment inspecter les données intermédiaires pendant les étapes de chargement, de traitement et d’entraînement du modèle du pipeline Machine Learning de ML.NET.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: d6ddeb523fb229eb0ebc9c2f22809312060e4266
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402392"
---
# <a name="inspect-intermediate-data-during-processing"></a>Inspecter les données intermédiaires pendant le traitement

Découvrez comment inspecter les données intermédiaires pendant les étapes de chargement, de traitement et d’entraînement du modèle dans ML.NET. Les données intermédiaires sont les résultats de chaque étape dans le pipeline Machine Learning.

Les données intermédiaires comme celles représentées ci-dessous, qui sont chargées dans un [`IDataView`](xref:Microsoft.ML.IDataView), peuvent être inspectées de plusieurs façons dans ML.NET.
 
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

## <a name="convert-idataview-to-ienumerable"></a>Convertir IDataView en IEnumerable

Un des moyens les plus rapides pour inspecter un [`IDataView`](xref:Microsoft.ML.IDataView) consiste à le convertir en un [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601). Pour convertir un [`IDataView`](xref:Microsoft.ML.IDataView) en [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601), utilisez la méthode [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*). 

Pour optimiser les performances, définissez `reuseRowObject` sur `true`. Cette opération remplit tardivement le même objet avec les données de la ligne actuelle au moment de son évaluation, par opposition à la création d’un objet pour chaque ligne dans le jeu de données.

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

## <a name="accessing-specific-indices-with-ienumerable"></a>Accès à des index spécifiques avec IEnumerable

Si vous devez uniquement accéder à une partie des données ou à des index spécifiques, utilisez [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) et définissez la valeur du paramètre `reuseRowObject` sur `false` afin qu’un objet soit créé pour chaque ligne demandée dans le jeu de données. Convertissez ensuite le [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) en tableau ou liste.

> [!WARNING]
> La conversion du résultat de [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) en tableau ou liste charge en mémoire toutes les lignes [`IDataView`](xref:Microsoft.ML.IDataView) demandées, ce qui peut affecter les performances.

Une fois la collection créée, vous pouvez effectuer des opérations sur les données. L’extrait de code ci-dessous prend les trois premières lignes du jeu de données et calcule le prix moyen actuel.

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

## <a name="inspect-values-in-a-single-column"></a>Inspecter les valeurs d’une colonne spécifique

À n’importe quel point du processus de génération de modèle, les valeurs d’une colonne spécifique d’un [`IDataView`](xref:Microsoft.ML.IDataView) sont accessibles à l’aide de la méthode [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*). La méthode [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) retourne toutes les valeurs d’une colonne spécifique sous la forme d’un [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Inspecter les valeurs d’IDataView une ligne à la fois

[`IDataView`](xref:Microsoft.ML.IDataView) est évalué tardivement. Pour effectuer une itération sur les lignes d’un [`IDataView`](xref:Microsoft.ML.IDataView) sans opérer de conversion en [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) comme illustré dans les sections précédentes de ce document, créez un [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) en utilisant la méthode [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) et en passant le [DataViewSchema](xref:Microsoft.ML.DataViewSchema) de votre [`IDataView`](xref:Microsoft.ML.IDataView) comme paramètre. Ensuite, pour effectuer une itération sur les lignes, utilisez la méthode de curseur [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) avec des délégués [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) pour extraire les valeurs respectives de chacune des colonnes.

> [!IMPORTANT]
> Pour des raisons de performances, les vecteurs dans ML.NET utilisent [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) au lieu de types de collection native (autrement dit, `Vector`,`float[]`). 

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a>Obtenir un aperçu du résultat du prétraitement ou de l’entraînement sur un sous-ensemble des données

> [!WARNING]
> N’utilisez pas `Preview` dans le code de production, car celui-ci est destiné au débogage et peut réduire les performances.

Le processus de génération de modèle est expérimental et itératif. Pour obtenir un aperçu de ce à quoi ressembleraient les données après le prétraitement ou l’entraînement d’un modèle Machine Learning sur un sous-ensemble des données, utilisez la méthode [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*), qui retourne un [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview). Le résultat est un objet avec des propriétés `ColumnView` et `RowView` qui sont toutes deux un [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) et contiennent les valeurs dans une ligne ou une colonne particulière. Spécifiez le nombre de lignes auxquelles appliquer la transformation à l’aide du paramètre `maxRows`.

![Débogueur de données : aperçu de l’objet](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

Le résultat de l’inspection d’un [`IDataView`](xref:Microsoft.ML.IDataView) devrait être semblable à ce qui suit :

![Débogueur de données : aperçu de la vue de ligne](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
