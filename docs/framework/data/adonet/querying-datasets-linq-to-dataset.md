---
title: Interrogation de DataSets (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: bb64abcffdbbcd46dfb11b2564619c565e461436
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634779"
---
# <a name="querying-datasets-linq-to-dataset"></a>Interrogation de DataSets (LINQ to DataSet)
Une fois qu'un objet <xref:System.Data.DataSet> a été rempli avec des données, vous pouvez commencer de l'interroger. La formulation de requêtes avec LINQ to DataSet est semblable à l’utilisation de LINQ (Language-Integrated Query) sur d’autres sources de données compatibles LINQ. Toutefois, n’oubliez pas que lorsque vous utilisez des requêtes LINQ sur un objet <xref:System.Data.DataSet>, vous interrogez une énumération d’objets <xref:System.Data.DataRow> au lieu d’une énumération d’un type personnalisé. Cela signifie que vous pouvez utiliser n’importe quel membre de la classe <xref:System.Data.DataRow> dans vos requêtes LINQ. Cela vous permet de créer des requêtes riches et complexes.  
  
 Comme pour les autres implémentations de LINQ, vous pouvez créer des requêtes LINQ to DataSet dans deux formes différentes : la syntaxe d’expression de requête et la syntaxe de requête fondée sur une méthode. Vous pouvez utiliser une syntaxe d'expression de requête ou une syntaxe de requête fondée sur une méthode sur des tables uniques d'un <xref:System.Data.DataSet>, sur plusieurs tables sur un <xref:System.Data.DataSet>, ou sur les tables d'un <xref:System.Data.DataSet> typé.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Requêtes de table unique](single-table-queries-linq-to-dataset.md)  
 Explique comment exécuter des requêtes d'analyse unique.  
  
 [Requêtes de table croisée](cross-table-queries-linq-to-dataset.md)  
 Explique comment exécuter des requêtes d'analyse croisée.  
  
 [Interrogation de DataSets typés](querying-typed-datasets.md)  
 Explique comment interroger des objets <xref:System.Data.DataSet> typés.  
  
## <a name="see-also"></a>Voir aussi

- [Exemples LINQ to DataSet](linq-to-dataset-examples.md)
- [Chargement de données dans un DataSet](loading-data-into-a-dataset.md)
