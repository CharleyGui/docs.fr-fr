---
title: Recherche de lignes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: dc0661e29e6d3ee5aa3f54179e8abf265cd67d58
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186976"
---
# <a name="finding-rows"></a>Recherche de lignes

Vous pouvez rechercher des lignes en fonction des valeurs de leur clé de tri en utilisant les méthodes <xref:System.Data.DataView.Find%2A> et <xref:System.Data.DataView.FindRows%2A> de l'objet <xref:System.Data.DataView>. Le respect de la casse des valeurs de recherche dans les méthodes **Find** et **FindRows** est déterminé par la propriété **CaseSensitive** de l’objet sous-jacent <xref:System.Data.DataTable> . Pour qu'un résultat soit retourné, les valeurs de recherche doivent correspondre aux valeurs des clés de tri existantes dans leur intégralité.  
  
 La méthode **Find** retourne un entier avec l’index du <xref:System.Data.DataRowView> qui correspond aux critères de recherche. Si plusieurs lignes correspondent aux critères de recherche, seul l’index du premier **DataRowView** correspondant est retourné. Si aucune correspondance n’est trouvée, **Find** retourne-1.  
  
 Pour retourner des résultats de recherche qui correspondent à plusieurs lignes, utilisez la méthode **FindRows** . **FindRows** fonctionne comme la méthode **Find** , à la différence qu’elle retourne un tableau **DataRowView** qui fait référence à toutes les lignes correspondantes dans le **DataView**. Si aucune correspondance n’est trouvée, le tableau **DataRowView** sera vide.  
  
 Pour utiliser les méthodes **Find** ou **FindRows** , vous devez spécifier un ordre de tri en affectant à **ApplyDefaultSort** la **valeur true** ou en utilisant la propriété **sort** . Si aucun ordre de tri n'est spécifié, une exception est levée.  
  
 Les méthodes **Find** et **FindRows** prennent un tableau de valeurs comme entrée dont la longueur correspond au nombre de colonnes dans l’ordre de tri. Si un tri doit s'effectuer sur une seule colonne, vous pouvez passer une seule valeur. Pour les ordres de tri incluant plusieurs colonnes, vous passez un tableau d'objets. Notez que, pour un tri sur plusieurs colonnes, les valeurs du tableau d’objets doivent correspondre à l’ordre des colonnes spécifiées dans la propriété **sort** du **DataView**.  
  
 L’exemple de code suivant montre la méthode **Find** appelée sur un **DataView** avec un ordre de tri de colonne unique.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 Si votre propriété de **Tri** spécifie plusieurs colonnes, vous devez passer un tableau d’objets avec les valeurs de recherche de chaque colonne dans l’ordre spécifié par la propriété de **Tri** , comme dans l’exemple de code suivant.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](dataviews.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
