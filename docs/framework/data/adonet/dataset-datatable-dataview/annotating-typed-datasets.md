---
title: Annotation de DataSet typés
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 79d3913827d5df6f0ac4e77bfdb8f37b553a86d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203746"
---
# <a name="annotating-typed-datasets"></a>Annotation de DataSet typés

Les annotations vous permettent de modifier le nom des éléments de votre objet <xref:System.Data.DataSet> typé sans pour autant modifier le schéma sous-jacent. Si vous modifiez les noms des éléments dans votre schéma sous-jacent, le **DataSet** typé fait référence aux objets qui n’existent pas dans la source de données, ainsi qu’à la perte d’une référence aux objets qui existent dans la source de données.  
  
 À l’aide des annotations, vous pouvez personnaliser les noms des objets de votre **DataSet** typé avec des noms plus explicites, ce qui rend le code plus lisible et le **jeu de données** typé plus facile à utiliser par les clients, tout en laissant intact le schéma sous-jacent. Par exemple, l’élément de schéma suivant pour la table **Customers** de la base de données **Northwind** entraînerait un nom d’objet **DataRow** **CustomersRow** et un <xref:System.Data.DataRowCollection> nommé **Customers**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Le nom du **DataRowCollection** des **clients** est explicite dans le code client, mais un nom **DataRow** de **CustomersRow** est trompeur, car il s’agit d’un objet unique. En outre, dans les scénarios courants, l’objet est référencé sans l’identificateur de **ligne** et il est simplement désigné comme un objet **client** . La solution consiste à annoter le schéma et à identifier les nouveaux noms des objets **DataRow** et **DataRowCollection** . Voici une version annotée du précédent schéma.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Si vous spécifiez une valeur **typedName** de **client** , le nom d’objet **DataRow** est **Customer**. Si vous spécifiez une valeur **typedPlural** , les **clients** préservent le nom du **DataRowCollection** des **clients**.  
  
 Le tableau suivant présente les différentes annotations disponibles.  
  
|Annotation|Description|  
|----------------|-----------------|  
|**typedName**|Nom de l'objet.|  
|**typedPlural**|Nom d’une collection d’objets.|  
|**typedParent**|Nom de l'objet lorsqu'il y est fait référence dans une relation parente.|  
|**typedChildren**|Nom de la méthode permettant de retourner des objets d'une relation enfant.|  
|**nullValue**|Valeur si la valeur sous-jacente est **DBNull**. Consultez le tableau suivant pour les annotations **NullValue** . La valeur par défaut est **_throw**.|  
  
 Le tableau suivant indique les valeurs qui peuvent être spécifiées pour l’annotation **NullValue** .  
  
|Valeur nullValue|Description|  
|---------------------|-----------------|  
|*Valeur de remplacement*|Spécifier une valeur à retourner. La valeur retournée doit correspondre au type de l'élément. Par exemple, utilisez `nullValue="0"` pour retourner 0 pour les champs de type null integer (entier nul).|  
|**_throw**|Levée d'une exception. Il s’agit de la valeur par défaut.|  
|**_null**|Retourner une référence null ou lever une exception si un type primitif est rencontré.|  
|**_empty**|Pour les chaînes, retourne **String. Empty**, sinon retourne un objet créé à partir d’un constructeur vide. Si un type primitif est rencontré, lever une exception.|  
  
 Le tableau suivant présente les valeurs par défaut pour les objets d’un **DataSet** typé et les annotations disponibles.  
  
|Objet/méthode/événement|Default|Annotation|  
|---------------------------|-------------|----------------|  
|**Tables**|TableNameDataTable|typedPlural|  
|**DataTable** Leurs|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**DataRow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**Propriété**|PropertyName|typedName|  
|**Enfant** Accesseur|GetChildTableNameRows|typedChildren|  
|**Parent** Accesseur|TableNameRow|typedParent|  
|**Jeu de données** Événements|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 Pour utiliser des annotations de **DataSet** typé, vous devez inclure la référence **xmlns** suivante dans votre schéma en langage XSD (XML Schema Definition). Pour créer un XSD à partir de tables de base de données, consultez <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [utilisation de datasets dans Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Voici un exemple de schéma annoté qui expose la table **Customers** de la base de données **Northwind** avec une relation avec la table **Orders** incluse.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""
      xmlns:xs="http://www.w3.org/2001/XMLSchema"
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 L’exemple de code suivant utilise un **DataSet** fortement typé créé à partir de l’exemple de schéma. Elle en utilise une <xref:System.Data.SqlClient.SqlDataAdapter> pour remplir la table **Customers** et une autre <xref:System.Data.SqlClient.SqlDataAdapter> pour remplir la table **Orders** . Le **DataSet** fortement typé définit le **DataRelations**.  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [Datasets typés](typed-datasets.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
