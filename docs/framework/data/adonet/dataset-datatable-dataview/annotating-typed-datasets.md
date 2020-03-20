---
title: Annotation de DataSet typés
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 757a87f92d8dc6049de1844fed892d95dc57c990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151518"
---
# <a name="annotating-typed-datasets"></a>Annotation de DataSet typés
Les annotations vous permettent de modifier le nom des éléments de votre objet <xref:System.Data.DataSet> typé sans pour autant modifier le schéma sous-jacent. Modifier les noms des éléments de votre schéma sous-jacent ferait en sorte que le **DataSet** dactylographie se réfère à des objets qui n’existent pas dans la source de données, ainsi que de perdre une référence aux objets qui existent dans la source de données.  
  
 À l’aide d’annotations, vous pouvez personnaliser les noms d’objets de votre **DataSet** dactylographue avec des noms plus significatifs, ce qui rend le code plus lisible et votre **DataSet** dactylographier plus facile à utiliser pour les clients, tout en laissant intact le schéma sous-jacent. Par exemple, l’élément schéma suivant pour le tableau **des clients** de la base de données **Northwind** donnerait lieu à un nom d’objet **DataRow** de **CustomersRow** et à un <xref:System.Data.DataRowCollection> **client**nommé .  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Un nom **DataRowCollection** des **clients** est significatif dans le code client, mais un nom **DataRow** de **CustomersRow** est trompeur parce qu’il s’agit d’un seul objet. En outre, dans des scénarios courants, l’objet serait mentionné sans l’identifiant **Row** et serait plutôt simplement appelé un objet **client.** La solution consiste à annoter le schéma et à identifier de nouveaux noms pour les objets **DataRow** et **DataRowCollection.** Voici une version annotée du précédent schéma.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Spécifier une valeur **dactylographiée** du **Client** se traduira par un nom d’objet **DataRow** du **client**. Spécifier une valeur **dactylographie** des **clients** conserve le nom **DataRowCollection** des **clients**.  
  
 Le tableau suivant présente les différentes annotations disponibles.  
  
|Annotation|Description|  
|----------------|-----------------|  
|**typedName**|Nom de l'objet.|  
|**typedPlural**|Nom d’une collection d’objets.|  
|**typedParent**|Nom de l'objet lorsqu'il y est fait référence dans une relation parente.|  
|**typedChildren**|Nom de la méthode permettant de retourner des objets d'une relation enfant.|  
|**nullValue (en)**|Valeur si la valeur sous-jacente est **DBNull**. Voir le tableau suivant pour les annotations **nullValue.** La valeur par défaut est **_throw**.|  
  
 Le tableau suivant montre les valeurs qui peuvent être spécifiées pour l’annotation **nullValue.**  
  
|Valeur nullValue|Description|  
|---------------------|-----------------|  
|*Valeur de remplacement*|Spécifier une valeur à retourner. La valeur retournée doit correspondre au type de l'élément. Par exemple, utilisez `nullValue="0"` pour retourner 0 pour les champs de type null integer (entier nul).|  
|**_throw**|Levée d'une exception. Il s’agit de la valeur par défaut.|  
|**_null**|Retourner une référence null ou lever une exception si un type primitif est rencontré.|  
|**_empty**|Pour les cordes, retourner **String.Empty**, sinon retourner un objet créé à partir d’un constructeur vide. Si un type primitif est rencontré, lever une exception.|  
  
 Le tableau suivant affiche les valeurs par défaut pour les objets dans un **DataSet** dactylographe et les annotations disponibles.  
  
|Objet/méthode/événement|Default|Annotation|  
|---------------------------|-------------|----------------|  
|**Datatable**|TableNameDataTable|typedPlural|  
|**DataTable (en)** Méthodes|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**Datarow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**Propriété**|PropertyName|typedName|  
|**Enfant** Accesseur|GetChildTableNameRows|typedChildren|  
|**Parent** Accesseur|TableNameRow|typedParent|  
|**Ensemble de données** Événements|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 Pour utiliser les annotations **DataSet** typées, vous devez inclure la référence **xmlns** suivante dans votre langage de définition XML Schema (XSD). Pour créer un xsd à <xref:System.Data.DataSet.WriteXmlSchema%2A> partir de tables de base de données, voir ou [travailler avec des jeux de données dans Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Voici un exemple de schéma annoté qui expose la table **des clients** de la base de données **Northwind** avec une relation avec le tableau **des commandes** inclus.  
  
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
  
 L’exemple de code suivant utilise un **DataSet** fortement typé créé à partir du schéma de l’échantillon. Il utilise <xref:System.Data.SqlClient.SqlDataAdapter> l’un pour peupler la table **des clients** et un autre <xref:System.Data.SqlClient.SqlDataAdapter> pour remplir la table des **commandes.** Le **DataSet** fortement tapé définit les **DataRelations**.  
  
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
