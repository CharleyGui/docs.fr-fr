---
title: Recherche de lignes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: cfd4587f0dde7687ecf88bf6b31c44b90a2287ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151141"
---
# <a name="finding-rows"></a>Recherche de lignes
Vous pouvez rechercher des lignes en fonction des valeurs de leur clé de tri en utilisant les méthodes <xref:System.Data.DataView.Find%2A> et <xref:System.Data.DataView.FindRows%2A> de l'objet <xref:System.Data.DataView>. La sensibilité de cas des valeurs de recherche dans les méthodes **Find** and <xref:System.Data.DataTable> **FindRows** est déterminée par la propriété **CaseSensitive** du sous-jacent . Pour qu'un résultat soit retourné, les valeurs de recherche doivent correspondre aux valeurs des clés de tri existantes dans leur intégralité.  
  
 La méthode **Trouver** renvoie un integer avec l’index de celui <xref:System.Data.DataRowView> qui correspond aux critères de recherche. Si plus d’une ligne correspond aux critères de recherche, seul l’index du premier **DataRowView** correspondant est retourné. Si aucune correspondance n’est trouvée, **Trouvez** les retours -1.  
  
 Pour retourner les résultats de recherche qui correspondent à plusieurs lignes, utilisez la méthode **FindRows.** **FindRows** fonctionne comme la méthode **Trouver,** sauf qu’elle renvoie un tableau **DataRowView** qui fait référence à toutes les lignes correspondantes dans le **DataView**. Si aucune correspondance n’est trouvée, le tableau **DataRowView** sera vide.  
  
 Pour utiliser les méthodes **Trouver** ou **FindRows,** vous devez spécifier une commande de tri soit en définissant **ApplyDefaultSort** à **vrai** ou en utilisant la propriété **Tri.** Si aucun ordre de tri n'est spécifié, une exception est levée.  
  
 Les méthodes **Find** and **FindRows** prennent un éventail de valeurs comme entrée dont la longueur correspond au nombre de colonnes dans l’ordre de tri. Si un tri doit s'effectuer sur une seule colonne, vous pouvez passer une seule valeur. Pour les ordres de tri incluant plusieurs colonnes, vous passez un tableau d'objets. Notez que pour une sorte sur plusieurs colonnes, les valeurs dans le tableau d’objet doivent correspondre à l’ordre des colonnes spécifiées dans la propriété **Tri** de la **DataView**.  
  
 L’exemple de code suivant montre la méthode **Trouver** appelée contre un **DataView** avec un seul ordre de tri de colonne.  
  
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
  
 Si votre propriété **Tri** spécifie plusieurs colonnes, vous devez passer un tableau d’objets avec les valeurs de recherche pour chaque colonne dans l’ordre spécifié par la propriété **Tri,** comme dans l’exemple de code suivant.  
  
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
