---
title: Ajout de données à un DataTable
description: Reportez-vous à cet exemple de code pour ajouter de nouvelles lignes de données à une table dans ADO.NET, après avoir créé un DataTable et défini sa structure à l’aide de colonnes et de contraintes.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: aac2d90cc57a4af823c42f8c7eb2adcd43c63caf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164816"
---
# <a name="adding-data-to-a-datatable"></a>Ajout de données à un DataTable

Après avoir créé un objet <xref:System.Data.DataTable> et défini sa structure à l'aide de colonnes et de contraintes, vous pouvez ajouter de nouvelles lignes de données à la table. Pour ajouter une nouvelle ligne, déclarez une nouvelle variable comme type <xref:System.Data.DataRow>. Un nouvel objet **DataRow** est retourné lorsque vous appelez la <xref:System.Data.DataTable.NewRow%2A> méthode. Le **DataTable** crée ensuite l’objet **DataRow** en fonction de la structure de la table, comme défini par <xref:System.Data.DataColumnCollection> .  
  
 L’exemple suivant montre comment créer une nouvelle ligne en appelant la méthode **NewRow** .  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Vous pouvez ensuite manipuler la ligne ajoutée en utilisant un index ou le nom de colonne, comme le montre l'exemple suivant.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Une fois que les données sont insérées dans la nouvelle ligne, la méthode **Add** est utilisée pour ajouter la ligne à <xref:System.Data.DataRowCollection> , comme indiqué dans le code suivant.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Vous pouvez également appeler la méthode **Add** pour ajouter une nouvelle ligne en passant un tableau de valeurs, de type <xref:System.Object> , comme indiqué dans l’exemple suivant.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Le passage d’un tableau de valeurs, typé en tant qu' **objet**, à la méthode **Add** crée une nouvelle ligne à l’intérieur de la table et définit ses valeurs de colonne avec les valeurs du tableau d’objets. Notez que les valeurs du tableau correspondent de façon séquentielle aux colonnes, en fonction de leur ordre d'apparition dans la table.  
  
 L’exemple suivant ajoute 10 lignes à la table **Customers** nouvellement créée.  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [Manipulation des données dans un DataTable](manipulating-data-in-a-datatable.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
