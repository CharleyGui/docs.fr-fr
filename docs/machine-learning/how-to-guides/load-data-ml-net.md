---
title: Charger des données depuis des fichiers et d’autres sources
description: Ce guide pratique vous montre comment charger des données à des fins de traitement et d’entraînement dans ML.NET. Les données sont stockées à l’origine dans des fichiers ou d’autres sources de données, comme des bases de données, du JSON, du XML ou des collections en mémoire.
ms.date: 06/25/2019
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: fafbe3fed9e3f0b509eda4f9d8967965bde19767
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397742"
---
# <a name="load-data-from-files-and-other-sources"></a>Charger des données depuis des fichiers et d’autres sources

Ce guide pratique vous montre comment charger des données à des fins de traitement et d’entraînement dans ML.NET. Les données sont stockées à l’origine dans des fichiers ou d’autres sources de données, comme des bases de données, du JSON, du XML ou des collections en mémoire.

## <a name="create-the-data-model"></a>Créer le modèle de données

ML.NET permet de définir des modèles de données par le biais de classes. Soit les données d’entrée suivantes :

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Créez un modèle de données qui représente l’extrait de code ci-dessous :

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }
 
    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a>Annotation du modèle de données avec des attributs de colonne

Les attributs donnent à ML.NET plus d’informations sur le modèle de données et la source de données.

L’attribut [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) spécifie les index de colonne de vos propriétés.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) est nécessaire uniquement lors du chargement de données à partir d’un fichier.

Chargez les colonnes en tant que : 
- Colonnes individuelles comme `Size` et `CurrentPrices` dans la classe `HousingData`.
- Plusieurs colonnes à la fois sous la forme d’un vecteur comme `HistoricalPrices` dans la classe `HousingData`.

Si vous avez une propriété de vecteur, appliquez-lui l’attribut [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) dans votre modèle de données. Il est important de noter que tous les éléments du vecteur doivent être du même type.

ML.NET fonctionne par le biais des noms de colonne. Si vous souhaitez nommer une colonne en autre chose que le nom de propriété, utilisez l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute). Quand vous créez des objets en mémoire, vous le faites toujours en utilisant le nom de propriété. Toutefois, pour le traitement des données et la génération des modèles Machine Learning, ML.NET remplace la propriété et la référence avec la valeur fournie dans l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute).

## <a name="load-data-from-a-single-file"></a>Charger des données à partir d’un fichier spécifique

Pour charger des données à partir d’un fichier, utilisez la méthode [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) ainsi que le modèle de données pour les données à charger. Le paramètre `separatorChar` étant par défaut défini sur le caractère de tabulation, changez-le pour votre fichier de données si cela est nécessaire. Si votre fichier a un en-tête, définissez le paramètre `hasHeader` sur `true` pour ignorer la première ligne du fichier et commencer à charger les données à partir de la deuxième ligne.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Charger des données à partir de plusieurs fichiers

Si vos données sont stockées dans plusieurs fichiers, tant que le schéma de données est le même, ML.NET vous permet de charger les données, que les différents fichiers se trouvent dans le même répertoire ou dans plusieurs répertoires.

### <a name="load-from-files-in-a-single-directory"></a>Effectuer le chargement à partir de fichiers situés dans le même répertoire

Si tous vos fichiers de données se trouvent dans le même répertoire, utilisez des caractères génériques dans la méthode [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Effectuer le chargement à partir de fichiers situés dans plusieurs répertoires

Pour charger des données à partir de plusieurs répertoires, utilisez la méthode [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) pour créer un [`TextLoader`](xref:Microsoft.ML.Data.TextLoader). Ensuite, utilisez la méthode [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) et spécifiez les différents chemins de fichiers (vous ne pouvez pas utiliser de caractères génériques).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-other-sources"></a>Charger des données depuis d’autres sources

En plus du chargement de données stockées dans des fichiers, ML.NET prend en charge le chargement de données depuis des sources incluant notamment celles-ci :

- Collections en mémoire
- JSON/XML
- Bases de données

Notez que quand vous utilisez des sources de streaming, ML.NET s’attend à ce que l’entrée se présente sous la forme d’une collection en mémoire. Ainsi, quand vous utilisez des sources telles que JSON/XML, veillez à convertir les données en une collection en mémoire.

Soit la collection en mémoire suivante :

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

Chargez la collection en mémoire dans un [`IDataView`](xref:Microsoft.ML.IDataView) avec la méthode [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) :

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
