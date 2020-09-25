---
title: Pagination à travers un résultat de requête
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 065b509d8385ee37b2a86587f520b5fd3207ceff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186950"
---
# <a name="paging-through-a-query-result"></a>Pagination à travers un résultat de requête

Ce mode d'affichage consiste à retourner les résultats d'une requête sous forme de sous-ensembles, plus petits, de données, aussi appelés pages. Cette façon de procéder est courante lorsqu'il s'agit de présenter à l'utilisateur un affichage des résultats par petits segments, plus faciles à gérer.  
  
 Le **DataAdapter** fournit une fonctionnalité permettant de retourner uniquement une page de données, par le biais de surcharges de la méthode **Fill** . Toutefois, ce n’est peut-être pas le meilleur choix pour la pagination via des résultats de requête volumineux, car même si le **DataAdapter** remplit la cible <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> avec uniquement les enregistrements demandés, les ressources pour retourner l’intégralité de la requête sont toujours utilisées. Pour retourner une page de données provenant d'une source de donnée sans solliciter les ressources requises pour retourner l'intégralité de la requête, spécifiez des critères supplémentaires pour votre requête afin de limiter le nombre de lignes retournées à celles qui sont requises.  
  
 Pour utiliser la méthode **Fill** pour retourner une page de données, spécifiez un paramètre **startRecord** , pour le premier enregistrement de la page de données, et un paramètre **maxRecords** , pour le nombre d’enregistrements dans la page de données.  
  
 L’exemple de code suivant montre comment utiliser la méthode **Fill** pour retourner la première page d’un résultat de requête où la taille de la page est de cinq enregistrements.  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 Dans l’exemple précédent, le **jeu de données** ne contient que cinq enregistrements, mais l’intégralité de la table **Orders** est retournée. Pour remplir le **DataSet** avec ces cinq mêmes enregistrements, mais ne retournent que cinq enregistrements, utilisez les clauses Top et Where dans votre instruction SQL, comme dans l’exemple de code suivant.  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 Notez que, lorsque vous choisissez ce mode d'affichage par pages des résultats d'une requête, vous devez conserver l'identificateur unique en fonction duquel les lignes sont organisées, afin de passer cet identificateur unique à la commande pour retourner la page d'enregistrements suivante, comme le montre l'exemple de code ci-après.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Pour retourner la page d’enregistrements suivante à l’aide de la surcharge de la méthode **Fill** qui accepte les paramètres **startRecord** et **maxRecords** , incrémentez l’index actuel de l’enregistrement en utilisant la taille de la page et remplissez la table. N’oubliez pas que le serveur de base de données renvoie l’intégralité des résultats de la requête, même si une seule page d’enregistrements est ajoutée au **jeu**de données. Dans l'exemple de code suivant, les lignes de la table sont vidées de leur contenu avant de recevoir la page de données suivante. Vous avez la possibilité de conserver dans un cache local un certain nombre de lignes retournées afin de limiter les sollicitations du serveur de base de données.  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 Pour retourner la page d'enregistrements suivante sans que le serveur de base de données ne retourne l'intégralité de la requête, spécifiez des critères restrictifs pour l'instruction SELECT. Parce que l'exemple précédent conservait le dernier enregistrement retourné, vous pouvez l'utiliser dans la clause WHERE afin de spécifier le point de départ de la requête, comme le montre l'exemple de code suivant.  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
