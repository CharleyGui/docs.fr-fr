---
title: Exécution d’une requête XPath sur un DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 6082a171d24c55ea52c153bbd920bb7486be78a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784372"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="5cd59-102">Exécution d’une requête XPath sur un DataSet</span><span class="sxs-lookup"><span data-stu-id="5cd59-102">Performing an XPath Query on a DataSet</span></span>
<span data-ttu-id="5cd59-103">La relation entre une synchronisée <xref:System.Data.DataSet> et <xref:System.Xml.XmlDataDocument> vous permet d’utiliser des services XML, tels que la requête XPath (XML Path Language), qui accèdent au **XmlDataDocument** et peuvent exécuter certaines fonctionnalités plus facilement que accès direct au **jeu de données** .</span><span class="sxs-lookup"><span data-stu-id="5cd59-103">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="5cd59-104">Par exemple, au lieu d’utiliser la méthode **Select** d' <xref:System.Data.DataTable> un objet pour parcourir les relations vers d’autres tables dans un **DataSet**, vous pouvez exécuter une requête XPath sur un **XmlDataDocument** synchronisé avec le **DataSet**, pour obtenir un liste d’éléments XML sous la forme d’un <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="5cd59-104">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="5cd59-105">Les nœuds de **XmlNodeList**, castés <xref:System.Xml.XmlElement> en tant que nœuds, peuvent ensuite être passés à la méthode **GetRowFromElement** de **XmlDataDocument**pour <xref:System.Data.DataRow> retourner des références correspondantes aux lignes de la table dans le  **Jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="5cd59-105">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="5cd59-106">Ainsi, l'exemple de code suivant exécute une requête XPath « petit-enfant ».</span><span class="sxs-lookup"><span data-stu-id="5cd59-106">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="5cd59-107">Le **jeu de données** est rempli avec trois tables : **Customers**, **Orders**et **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="5cd59-107">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="5cd59-108">Dans l’exemple, une relation parent-enfant est d’abord créée entre les tables **Customers** et **Orders** , et entre les tables **Orders** et **OrderDetails** .</span><span class="sxs-lookup"><span data-stu-id="5cd59-108">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="5cd59-109">Une requête XPath est ensuite exécutée pour retourner un **XmlNodeList** de nœuds **Customers** où un nœud petit-enfant **OrderDetails** a un nœud **ProductID** avec la valeur 43.</span><span class="sxs-lookup"><span data-stu-id="5cd59-109">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="5cd59-110">Fondamentalement, l’exemple utilise la requête XPath pour déterminer quels sont les clients qui ont commandé le produit dont le **ProductID** est 43.</span><span class="sxs-lookup"><span data-stu-id="5cd59-110">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5cd59-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cd59-111">See also</span></span>

- [<span data-ttu-id="5cd59-112">Synchronisation DataSet et XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="5cd59-112">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="5cd59-113">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5cd59-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
