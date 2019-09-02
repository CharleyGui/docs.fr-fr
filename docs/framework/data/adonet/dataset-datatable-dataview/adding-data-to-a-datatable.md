---
title: Ajout de données à un DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 91c635e2bc2ed617e8c45171d9ec7d7359b9ca88
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205481"
---
# <a name="adding-data-to-a-datatable"></a>Ajout de données à un DataTable
Après avoir créé un objet <xref:System.Data.DataTable> et défini sa structure à l'aide de colonnes et de contraintes, vous pouvez ajouter de nouvelles lignes de données à la table. Pour ajouter une nouvelle ligne, déclarez une nouvelle variable comme type <xref:System.Data.DataRow>. Un nouvel objet **DataRow** est retourné lorsque vous appelez la <xref:System.Data.DataTable.NewRow%2A> méthode. Le **DataTable** crée ensuite l’objet **DataRow** en fonction de la structure de la table, comme <xref:System.Data.DataColumnCollection>défini par.  
  
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
  
 Une fois que les données sont insérées dans la nouvelle ligne, la méthode **Add** est utilisée pour ajouter <xref:System.Data.DataRowCollection>la ligne à, comme indiqué dans le code suivant.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Vous pouvez également appeler la méthode **Add** pour ajouter une nouvelle ligne en passant un tableau de valeurs, de type <xref:System.Object>, comme indiqué dans l’exemple suivant.  
  
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
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
