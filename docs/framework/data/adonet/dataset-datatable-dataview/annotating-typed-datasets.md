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
# <a name="annotating-typed-datasets"></a><span data-ttu-id="8ff93-102">Annotation de DataSet typés</span><span class="sxs-lookup"><span data-stu-id="8ff93-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="8ff93-103">Les annotations vous permettent de modifier le nom des éléments de votre objet <xref:System.Data.DataSet> typé sans pour autant modifier le schéma sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="8ff93-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="8ff93-104">Modifier les noms des éléments de votre schéma sous-jacent ferait en sorte que le **DataSet** dactylographie se réfère à des objets qui n’existent pas dans la source de données, ainsi que de perdre une référence aux objets qui existent dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="8ff93-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="8ff93-105">À l’aide d’annotations, vous pouvez personnaliser les noms d’objets de votre **DataSet** dactylographue avec des noms plus significatifs, ce qui rend le code plus lisible et votre **DataSet** dactylographier plus facile à utiliser pour les clients, tout en laissant intact le schéma sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="8ff93-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="8ff93-106">Par exemple, l’élément schéma suivant pour le tableau **des clients** de la base de données **Northwind** donnerait lieu à un nom d’objet **DataRow** de **CustomersRow** et à un <xref:System.Data.DataRowCollection> **client**nommé .</span><span class="sxs-lookup"><span data-stu-id="8ff93-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="8ff93-107">Un nom **DataRowCollection** des **clients** est significatif dans le code client, mais un nom **DataRow** de **CustomersRow** est trompeur parce qu’il s’agit d’un seul objet.</span><span class="sxs-lookup"><span data-stu-id="8ff93-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="8ff93-108">En outre, dans des scénarios courants, l’objet serait mentionné sans l’identifiant **Row** et serait plutôt simplement appelé un objet **client.**</span><span class="sxs-lookup"><span data-stu-id="8ff93-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="8ff93-109">La solution consiste à annoter le schéma et à identifier de nouveaux noms pour les objets **DataRow** et **DataRowCollection.**</span><span class="sxs-lookup"><span data-stu-id="8ff93-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="8ff93-110">Voici une version annotée du précédent schéma.</span><span class="sxs-lookup"><span data-stu-id="8ff93-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="8ff93-111">Spécifier une valeur **dactylographiée** du **Client** se traduira par un nom d’objet **DataRow** du **client**.</span><span class="sxs-lookup"><span data-stu-id="8ff93-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="8ff93-112">Spécifier une valeur **dactylographie** des **clients** conserve le nom **DataRowCollection** des **clients**.</span><span class="sxs-lookup"><span data-stu-id="8ff93-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="8ff93-113">Le tableau suivant présente les différentes annotations disponibles.</span><span class="sxs-lookup"><span data-stu-id="8ff93-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="8ff93-114">Annotation</span><span class="sxs-lookup"><span data-stu-id="8ff93-114">Annotation</span></span>|<span data-ttu-id="8ff93-115">Description</span><span class="sxs-lookup"><span data-stu-id="8ff93-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="8ff93-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="8ff93-116">**typedName**</span></span>|<span data-ttu-id="8ff93-117">Nom de l'objet.</span><span class="sxs-lookup"><span data-stu-id="8ff93-117">Name of the object.</span></span>|  
|<span data-ttu-id="8ff93-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="8ff93-118">**typedPlural**</span></span>|<span data-ttu-id="8ff93-119">Nom d’une collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="8ff93-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="8ff93-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="8ff93-120">**typedParent**</span></span>|<span data-ttu-id="8ff93-121">Nom de l'objet lorsqu'il y est fait référence dans une relation parente.</span><span class="sxs-lookup"><span data-stu-id="8ff93-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="8ff93-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="8ff93-122">**typedChildren**</span></span>|<span data-ttu-id="8ff93-123">Nom de la méthode permettant de retourner des objets d'une relation enfant.</span><span class="sxs-lookup"><span data-stu-id="8ff93-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="8ff93-124">**nullValue (en)**</span><span class="sxs-lookup"><span data-stu-id="8ff93-124">**nullValue**</span></span>|<span data-ttu-id="8ff93-125">Valeur si la valeur sous-jacente est **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="8ff93-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="8ff93-126">Voir le tableau suivant pour les annotations **nullValue.**</span><span class="sxs-lookup"><span data-stu-id="8ff93-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="8ff93-127">La valeur par défaut est **_throw**.</span><span class="sxs-lookup"><span data-stu-id="8ff93-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="8ff93-128">Le tableau suivant montre les valeurs qui peuvent être spécifiées pour l’annotation **nullValue.**</span><span class="sxs-lookup"><span data-stu-id="8ff93-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="8ff93-129">Valeur nullValue</span><span class="sxs-lookup"><span data-stu-id="8ff93-129">nullValue Value</span></span>|<span data-ttu-id="8ff93-130">Description</span><span class="sxs-lookup"><span data-stu-id="8ff93-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="8ff93-131">*Valeur de remplacement*</span><span class="sxs-lookup"><span data-stu-id="8ff93-131">*Replacement Value*</span></span>|<span data-ttu-id="8ff93-132">Spécifier une valeur à retourner.</span><span class="sxs-lookup"><span data-stu-id="8ff93-132">Specify a value to be returned.</span></span> <span data-ttu-id="8ff93-133">La valeur retournée doit correspondre au type de l'élément.</span><span class="sxs-lookup"><span data-stu-id="8ff93-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="8ff93-134">Par exemple, utilisez `nullValue="0"` pour retourner 0 pour les champs de type null integer (entier nul).</span><span class="sxs-lookup"><span data-stu-id="8ff93-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="8ff93-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="8ff93-135">**_throw**</span></span>|<span data-ttu-id="8ff93-136">Levée d'une exception.</span><span class="sxs-lookup"><span data-stu-id="8ff93-136">Throw an exception.</span></span> <span data-ttu-id="8ff93-137">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8ff93-137">This is the default.</span></span>|  
|<span data-ttu-id="8ff93-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="8ff93-138">**_null**</span></span>|<span data-ttu-id="8ff93-139">Retourner une référence null ou lever une exception si un type primitif est rencontré.</span><span class="sxs-lookup"><span data-stu-id="8ff93-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="8ff93-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="8ff93-140">**_empty**</span></span>|<span data-ttu-id="8ff93-141">Pour les cordes, retourner **String.Empty**, sinon retourner un objet créé à partir d’un constructeur vide.</span><span class="sxs-lookup"><span data-stu-id="8ff93-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="8ff93-142">Si un type primitif est rencontré, lever une exception.</span><span class="sxs-lookup"><span data-stu-id="8ff93-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="8ff93-143">Le tableau suivant affiche les valeurs par défaut pour les objets dans un **DataSet** dactylographe et les annotations disponibles.</span><span class="sxs-lookup"><span data-stu-id="8ff93-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="8ff93-144">Objet/méthode/événement</span><span class="sxs-lookup"><span data-stu-id="8ff93-144">Object/Method/Event</span></span>|<span data-ttu-id="8ff93-145">Default</span><span class="sxs-lookup"><span data-stu-id="8ff93-145">Default</span></span>|<span data-ttu-id="8ff93-146">Annotation</span><span class="sxs-lookup"><span data-stu-id="8ff93-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="8ff93-147">**Datatable**</span><span class="sxs-lookup"><span data-stu-id="8ff93-147">**DataTable**</span></span>|<span data-ttu-id="8ff93-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="8ff93-148">TableNameDataTable</span></span>|<span data-ttu-id="8ff93-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="8ff93-149">typedPlural</span></span>|  
|<span data-ttu-id="8ff93-150">**DataTable (en)** Méthodes</span><span class="sxs-lookup"><span data-stu-id="8ff93-150">**DataTable** Methods</span></span>|<span data-ttu-id="8ff93-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="8ff93-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="8ff93-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="8ff93-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="8ff93-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="8ff93-153">DeleteTableNameRow</span></span>|<span data-ttu-id="8ff93-154">typedName</span><span class="sxs-lookup"><span data-stu-id="8ff93-154">typedName</span></span>|  
|<span data-ttu-id="8ff93-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="8ff93-155">**DataRowCollection**</span></span>|<span data-ttu-id="8ff93-156">TableName</span><span class="sxs-lookup"><span data-stu-id="8ff93-156">TableName</span></span>|<span data-ttu-id="8ff93-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="8ff93-157">typedPlural</span></span>|  
|<span data-ttu-id="8ff93-158">**Datarow**</span><span class="sxs-lookup"><span data-stu-id="8ff93-158">**DataRow**</span></span>|<span data-ttu-id="8ff93-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="8ff93-159">TableNameRow</span></span>|<span data-ttu-id="8ff93-160">typedName</span><span class="sxs-lookup"><span data-stu-id="8ff93-160">typedName</span></span>|  
|<span data-ttu-id="8ff93-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="8ff93-161">**DataColumn**</span></span>|<span data-ttu-id="8ff93-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="8ff93-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="8ff93-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="8ff93-163">DataRow.ColumnName</span></span>|<span data-ttu-id="8ff93-164">typedName</span><span class="sxs-lookup"><span data-stu-id="8ff93-164">typedName</span></span>|  
|<span data-ttu-id="8ff93-165">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="8ff93-165">**Property**</span></span>|<span data-ttu-id="8ff93-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="8ff93-166">PropertyName</span></span>|<span data-ttu-id="8ff93-167">typedName</span><span class="sxs-lookup"><span data-stu-id="8ff93-167">typedName</span></span>|  
|<span data-ttu-id="8ff93-168">**Enfant** Accesseur</span><span class="sxs-lookup"><span data-stu-id="8ff93-168">**Child** Accessor</span></span>|<span data-ttu-id="8ff93-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="8ff93-169">GetChildTableNameRows</span></span>|<span data-ttu-id="8ff93-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="8ff93-170">typedChildren</span></span>|  
|<span data-ttu-id="8ff93-171">**Parent** Accesseur</span><span class="sxs-lookup"><span data-stu-id="8ff93-171">**Parent** Accessor</span></span>|<span data-ttu-id="8ff93-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="8ff93-172">TableNameRow</span></span>|<span data-ttu-id="8ff93-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="8ff93-173">typedParent</span></span>|  
|<span data-ttu-id="8ff93-174">**Ensemble de données** Événements</span><span class="sxs-lookup"><span data-stu-id="8ff93-174">**DataSet** Events</span></span>|<span data-ttu-id="8ff93-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="8ff93-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="8ff93-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="8ff93-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="8ff93-177">typedName</span><span class="sxs-lookup"><span data-stu-id="8ff93-177">typedName</span></span>|  
  
 <span data-ttu-id="8ff93-178">Pour utiliser les annotations **DataSet** typées, vous devez inclure la référence **xmlns** suivante dans votre langage de définition XML Schema (XSD).</span><span class="sxs-lookup"><span data-stu-id="8ff93-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="8ff93-179">Pour créer un xsd à <xref:System.Data.DataSet.WriteXmlSchema%2A> partir de tables de base de données, voir ou [travailler avec des jeux de données dans Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="8ff93-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="8ff93-180">Voici un exemple de schéma annoté qui expose la table **des clients** de la base de données **Northwind** avec une relation avec le tableau **des commandes** inclus.</span><span class="sxs-lookup"><span data-stu-id="8ff93-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="8ff93-181">L’exemple de code suivant utilise un **DataSet** fortement typé créé à partir du schéma de l’échantillon.</span><span class="sxs-lookup"><span data-stu-id="8ff93-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="8ff93-182">Il utilise <xref:System.Data.SqlClient.SqlDataAdapter> l’un pour peupler la table **des clients** et un autre <xref:System.Data.SqlClient.SqlDataAdapter> pour remplir la table des **commandes.**</span><span class="sxs-lookup"><span data-stu-id="8ff93-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="8ff93-183">Le **DataSet** fortement tapé définit les **DataRelations**.</span><span class="sxs-lookup"><span data-stu-id="8ff93-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ff93-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ff93-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="8ff93-185">Datasets typés</span><span class="sxs-lookup"><span data-stu-id="8ff93-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="8ff93-186">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="8ff93-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="8ff93-187">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8ff93-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
