---
title: Création de colonnes d'expressions
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: ad14e4d3d6a1107f994d9536485257f9dc1851f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166844"
---
# <a name="creating-expression-columns"></a>Création de colonnes d'expressions

Vous pouvez définir une expression pour une colonne lui permettant de contenir une valeur calculée à partir d'autres valeurs de colonne de la même ligne ou de valeurs de colonne de plusieurs lignes de la table. Pour définir l'expression à évaluer, utilisez la propriété <xref:System.Data.DataColumn.Expression%2A> de la colonne cible. Utilisez la propriété <xref:System.Data.DataColumn.ColumnName%2A> pour faire référence à d'autres colonnes dans l'expression. La propriété <xref:System.Data.DataColumn.DataType%2A> de la colonne d'expression doit être appropriée pour la valeur que l'expression retournera.  
  
 Le tableau suivant énumère différentes utilisations possibles des colonnes d'expression dans une table.  
  
|Type d'expression|Exemple|  
|---------------------|-------------|  
|Comparaison|« Total >= 500 »|  
|Calcul|"UnitPrice * Quantity"|  
|Agrégation|Sum(Price)|  
  
 Vous pouvez définir la propriété **expression** sur un objet **DataColumn** existant, ou vous pouvez inclure la propriété comme troisième argument passé au <xref:System.Data.DataColumn> constructeur, comme indiqué dans l’exemple suivant.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 Les expressions peuvent faire référence à d'autres colonnes d'expression ; cependant, une référence circulaire, dans laquelle deux expressions se référencent mutuellement, générera une exception. Pour plus d’informations sur les règles d’écriture d’expressions, consultez la <xref:System.Data.DataColumn.Expression%2A> propriété de la classe **DataColumn** .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Définition de schéma de DataTable](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
