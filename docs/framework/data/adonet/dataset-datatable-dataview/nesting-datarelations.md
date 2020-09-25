---
title: Imbrication de DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 8db75f486c7c08b6a02401af35c9edf9969f9063
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201276"
---
# <a name="nesting-datarelations"></a>Imbrication de DataRelations

Dans une représentation relationnelle des données, chaque table contient des lignes reliées aux lignes d'autres tables par une colonne ou un ensemble de colonnes. Dans l'objet <xref:System.Data.DataSet> ADO.NET, la relation entre les tables est implémentée à l'aide d'un objet <xref:System.Data.DataRelation>. Lorsque vous créez un **DataRelation**, les relations parent-enfant des colonnes sont gérées uniquement par le biais de la relation. Les tables et les colonnes constituent des entités distinctes. Dans la représentation hiérarchique des données proposée par XML, les relations parent-enfant sont représentés sous forme d'éléments parents contenant des éléments enfants imbriqués.  
  
 Pour faciliter l’imbrication des objets enfants lorsqu’un **DataSet** est synchronisé avec un objet <xref:System.Xml.XmlDataDocument> ou écrit sous forme de données XML à l’aide de **WriteXml**, le **DataRelation** expose une propriété **imbriquée** . L’affectation de la **valeur true** à la propriété **Nested** d’un **DataRelation** entraîne l’imbrication des lignes enfants de la relation dans la colonne parente lors de l’écriture sous forme de données XML ou de la synchronisation avec un **XmlDataDocument**. La propriété **Nested** du **DataRelation** a la **valeur false**par défaut.  
  
 Par exemple, considérez le **jeu de données**suivant.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 Étant donné que la propriété **Nested** de l’objet **DataRelation** n’a pas la valeur **true** pour ce **DataSet**, les objets enfants ne sont pas imbriqués dans les éléments parents lorsque ce **DataSet** est représenté sous forme de données XML. La transformation de la représentation XML d’un **DataSet** qui contient des **DataSets**associés avec des relations de données non imbriquées peut entraîner un ralentissement des performances. Il est recommandé d'imbriquer les relations de données. Pour ce faire, affectez à la propriété **Nested** la **valeur true**. Puis, écrivez le code dans la feuille de style XSLT qui utilise des expressions de requête XPath hiérarchisées de haut en bas pour rechercher et transformer les données.  
  
 L’exemple de code suivant montre le résultat de l’appel de **WriteXml** sur le **DataSet**.  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 Notez que l’élément **Customers** et les éléments **Orders** sont affichés en tant qu’éléments frères. Si vous souhaitez que les éléments **Orders** s’affichent en tant qu’enfants de leurs éléments parents respectifs, la propriété **Nested** du **DataRelation** doit avoir la valeur **true** et vous devez ajouter ce qui suit :  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 Le code suivant montre à quoi ressemblerait la sortie obtenue, avec les éléments **Orders** imbriqués dans leurs éléments parents respectifs.  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [Ajout de DataRelations](adding-datarelations.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
