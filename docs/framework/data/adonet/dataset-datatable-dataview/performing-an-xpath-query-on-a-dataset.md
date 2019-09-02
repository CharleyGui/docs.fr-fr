---
title: Exécution d’une requête XPath sur un DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 56d1d11240934036994a14e454cf1a1d8b95226a
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204539"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Exécution d’une requête XPath sur un DataSet
La relation entre une synchronisée <xref:System.Data.DataSet> et <xref:System.Xml.XmlDataDocument> vous permet d’utiliser des services XML, tels que la requête XPath (XML Path Language), qui accèdent au **XmlDataDocument** et peuvent exécuter certaines fonctionnalités plus facilement que accès direct au **jeu de données** . Par exemple, au lieu d’utiliser la méthode **Select** d' <xref:System.Data.DataTable> un objet pour parcourir les relations vers d’autres tables dans un **DataSet**, vous pouvez exécuter une requête XPath sur un **XmlDataDocument** synchronisé avec le **DataSet**, pour obtenir un liste d’éléments XML sous la forme d’un <xref:System.Xml.XmlNodeList>. Les nœuds de **XmlNodeList**, castés <xref:System.Xml.XmlElement> en tant que nœuds, peuvent ensuite être passés à la méthode **GetRowFromElement** de **XmlDataDocument**pour <xref:System.Data.DataRow> retourner des références correspondantes aux lignes de la table dans le  **Jeu de données**.  
  
 Ainsi, l'exemple de code suivant exécute une requête XPath « petit-enfant ». Le **jeu de données** est rempli avec trois tables: **Customers**, **Orders**et **OrderDetails**. Dans l’exemple, une relation parent-enfant est d’abord créée entre les tables Customers et **Orders** , et entre les tables **Orders** et **OrderDetails** . Une requête XPath est ensuite exécutée pour retourner un **XmlNodeList** de nœuds **Customers** où un nœud petit-enfant **OrderDetails** a un nœud **ProductID** avec la valeur 43. Fondamentalement, l’exemple utilise la requête XPath pour déterminer quels sont les clients qui ont commandé le produit dont le **ProductID** est 43.  
  
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
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
