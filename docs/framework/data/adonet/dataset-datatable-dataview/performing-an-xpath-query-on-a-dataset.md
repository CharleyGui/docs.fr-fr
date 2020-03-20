---
title: Exécution d’une requête XPath sur un DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 5e9a00ab78a57c3c1686d7c87ed8b45d9b2649af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150829"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Exécution d’une requête XPath sur un DataSet
La relation entre un <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument> synchronisé et vous permet d’utiliser des services XML, tels que la requête XML Path Language (XPath), qui accèdent au **XmlDataDocument** et peut effectuer certaines fonctionnalités plus facilement que l’accès au **DataSet** directement. Par exemple, plutôt que d’utiliser la méthode **Select** d’un <xref:System.Data.DataTable> pour naviguer les relations vers d’autres tables dans un **DataSet**, vous pouvez effectuer une requête XPath sur <xref:System.Xml.XmlNodeList>un **XmlDataDocument** qui est synchronisé avec le **DataSet**, pour obtenir une liste d’éléments XML sous la forme d’un . Les nœuds dans le **XmlNodeList**, moulé <xref:System.Xml.XmlElement> comme nœuds, peuvent alors être passés à la méthode **GetRowDeEnement** de la **XmlDataDocument**, pour retourner des références correspondantes <xref:System.Data.DataRow> aux lignes de la table dans le **DataSet**synchronisé .  
  
 Ainsi, l'exemple de code suivant exécute une requête XPath « petit-enfant ». Le **DataSet** est rempli de trois tables: **Clients**, **Commandes**, et **OrderDetails**. Dans l’échantillon, une relation parent-enfant est créée d’abord entre les tableaux **Clients** et **Commandes,** et entre les tableaux **Ordres** et **OrderDetails.** Une requête XPath est ensuite effectuée pour retourner un **XmlNodeList** of **Customers** noeuds où un nœud **petit-enfant OrderDetails** a un nœud **ProductID** d’une valeur de 43. Essentiellement, l’échantillon utilise la requête XPath pour déterminer quels clients ont commandé le produit qui a le **ProductID** de 43.  
  
```vb  
' Assumes that connection is a valid SqlConnection.  
connection.Open()  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
Dim detailAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM [Order Details]", connection)  
detailAdapter.Fill(dataSet, "OrderDetails")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
dataSet.Relations.Add("OrderDetail", _  
  dataSet.Tables("Orders").Columns("OrderID"), _  
dataSet.Tables("OrderDetails").Columns("OrderID"), false).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)
  
Dim nodeList As XmlNodeList = xmlDoc.DocumentElement.SelectNodes( _  
  "descendant::Customers[*/OrderDetails/ProductID=43]")  
  
Dim dataRow As DataRow  
Dim xmlNode As XmlNode  
  
For Each xmlNode In nodeList  
  dataRow = xmlDoc.GetRowFromElement(CType(xmlNode, XmlElement))  
  
  If Not dataRow Is Nothing then Console.WriteLine(xmlRow(0).ToString())  
Next  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection.  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(dataSet, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(dataSet, "Orders");  
  
SqlDataAdapter detailAdapter = new SqlDataAdapter(  
  "SELECT * FROM [Order Details]", connection);  
detailAdapter.Fill(dataSet, "OrderDetails");  
  
connection.Close();  
  
dataSet.Relations.Add("CustOrders",  
  dataSet.Tables["Customers"].Columns["CustomerID"],  
 dataSet.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
dataSet.Relations.Add("OrderDetail",  
  dataSet.Tables["Orders"].Columns["OrderID"],  
  dataSet.Tables["OrderDetails"].Columns["OrderID"],
  false).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);
  
XmlNodeList nodeList = xmlDoc.DocumentElement.SelectNodes(  
  "descendant::Customers[*/OrderDetails/ProductID=43]");  
  
DataRow dataRow;  
foreach (XmlNode xmlNode in nodeList)  
{  
  dataRow = xmlDoc.GetRowFromElement((XmlElement)xmlNode);  
  if (dataRow != null)  
    Console.WriteLine(dataRow[0]);  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Synchronisation DataSet et XmlDataDocument](dataset-and-xmldatadocument-synchronization.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
