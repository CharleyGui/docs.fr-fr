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
# <a name="inspect-intermediate-data-during-processing"></a>Inspecter les données intermédiaires pendant le traitement

Découvrez comment inspecter les données intermédiaires pendant les étapes de chargement, de traitement et d’entraînement du modèle dans ML.NET. Les données intermédiaires sont les résultats de chaque étape dans le pipeline Machine Learning.

Les données intermédiaires comme celle représentée [`IDataView`](xref:Microsoft.ML.IDataView) ci-dessous qui est chargée dans un peut être inspectée de diverses façons dans ML.NET.

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

Une des façons les plus [`IDataView`](xref:Microsoft.ML.IDataView) rapides d’inspecter un est de le convertir en un [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601). Pour convertir [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) un [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) pour utiliser la méthode.

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

Si vous n’avez besoin que d’accéder [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) à une `reuseRowObject` partie `false` des données ou des indices spécifiques, utilisez et définissez la valeur du paramètre pour créer un nouvel objet pour chacune des lignes demandées dans le jeu de données. Ensuite, convertissez le [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dans un tableau ou une liste.

> [!WARNING]
> La conversion du [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) résultat en un tableau ou [`IDataView`](xref:Microsoft.ML.IDataView) une liste chargera toutes les lignes demandées en mémoire, ce qui peut affecter les performances.

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

À tout moment du processus de construction du [`IDataView`](xref:Microsoft.ML.IDataView) modèle, les valeurs [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) d’une seule colonne d’un peut être consultée à l’aide de la méthode. La [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) méthode renvoie toutes les valeurs [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)dans une seule colonne comme un .

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Inspecter les valeurs d’IDataView une ligne à la fois

[`IDataView`](xref:Microsoft.ML.IDataView)est évaluée paresseusement. Pour itérer sur les lignes [`IDataView`](xref:Microsoft.ML.IDataView) d’un [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) sans convertir en un comme démontré [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) dans les [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) sections précédentes de ce [`IDataView`](xref:Microsoft.ML.IDataView) document, créer un en utilisant la méthode et en passant dans le [DataViewSchema](xref:Microsoft.ML.DataViewSchema) de votre comme un paramètre. Ensuite, pour itérer sur les [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) rangées, utilisez [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) la méthode du curseur avec les délégués pour extraire les valeurs respectives de chacune des colonnes.

> [!IMPORTANT]
> Pour des raisons de performance, [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) les vecteurs dans ML.NET `Vector`utilisent`float[]`au lieu des types de collecte natifs (c’est-à-dire, , ).

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

Le processus de génération de modèle est expérimental et itératif. Pour prévisualiser les données après le pré-traitement ou la formation d’un modèle d’apprentissage automatique sur un sous-ensemble des données, utilisez la [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) méthode qui renvoie un [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview). Le résultat est `ColumnView` un `RowView` objet avec [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) et des propriétés qui sont à la fois un et contiennent les valeurs dans une colonne ou une rangée particulière. Spécifiez le nombre de lignes auxquelles appliquer la transformation à l’aide du paramètre `maxRows`.

![Débogueur de données : aperçu de l’objet](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

Le résultat de [`IDataView`](xref:Microsoft.ML.IDataView) l’inspection d’un serait similaire à ce qui suit:

![Débogueur de données : aperçu de la vue de ligne](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
