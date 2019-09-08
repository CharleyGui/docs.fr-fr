---
title: Interrogation de DataSets (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 79a9b320fbdbfecc3f7d531d992b1529873871a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783050"
---
# <a name="querying-datasets-linq-to-dataset"></a>Interrogation de DataSets (LINQ to DataSet)
Une fois qu'un objet <xref:System.Data.DataSet> a été rempli avec des données, vous pouvez commencer de l'interroger. La formulation de requêtes avec LINQ to DataSet est semblable [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] à l' [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]utilisation de sur d’autres sources de données compatibles. Toutefois, n’oubliez pas que lorsque vous [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] utilisez des requêtes <xref:System.Data.DataSet> sur un objet, vous interrogez une <xref:System.Data.DataRow> énumération d’objets, au lieu d’une énumération d’un type personnalisé. Cela signifie que vous pouvez utiliser n’importe quel membre de la <xref:System.Data.DataRow> classe dans vos [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] requêtes. Vous pouvez ainsi créer des requêtes riches et complexes.  
  
 Comme pour les autres implémentations [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]de, vous pouvez créer des requêtes LINQ to DataSet dans deux formes différentes : la syntaxe d’expression de requête et la syntaxe de requête fondée sur une méthode. Vous pouvez utiliser une syntaxe d'expression de requête ou une syntaxe de requête fondée sur une méthode sur des tables uniques d'un <xref:System.Data.DataSet>, sur plusieurs tables sur un <xref:System.Data.DataSet>, ou sur les tables d'un <xref:System.Data.DataSet> typé.  
  
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
