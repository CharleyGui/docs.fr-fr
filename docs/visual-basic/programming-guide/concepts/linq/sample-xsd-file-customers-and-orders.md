---
title: 'Exemple de fichier XSD : clients et Consolidées2'
ms.date: 07/20/2015
ms.assetid: a0c0b414-c8e1-45e4-bb67-b5e650c97130
ms.openlocfilehash: b1b1d9f1702f9ba9946d9bd7f678440558ef0a75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360694"
---
# <a name="sample-xsd-file-customers-and-orders"></a><span data-ttu-id="96f50-102">Exemple de fichier XSD : Clients et commandes</span><span class="sxs-lookup"><span data-stu-id="96f50-102">Sample XSD File: Customers and Orders</span></span>
<span data-ttu-id="96f50-103">Le fichier XSD suivant est utilisé dans différents exemples dans la documentation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="96f50-103">The following XSD file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="96f50-104">Ce fichier contient une définition de schéma pour l’[exemple de fichier XML : Clients et commandes (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="96f50-104">This file contains a schema definition for the [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span> <span data-ttu-id="96f50-105">Le schéma utilise les fonctionnalités `xs:key` et `xs:keyref` de XSD pour déterminer que l'attribut `CustomerID` de l'élément `Customer` est une clé et pour établir une relation entre l'élément `CustomerID` dans chaque élément `Order` et l'attribut `CustomerID` dans chaque élément `Customer`.</span><span class="sxs-lookup"><span data-stu-id="96f50-105">The schema uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="96f50-106">Pour obtenir un exemple d’écriture de requêtes LINQ qui tirent parti de cette relation à l’aide de la `Join` clause, consultez Guide pratique [pour joindre deux Collections (LINQ to XML) (Visual Basic)](how-to-join-two-collections-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="96f50-106">For an example of writing LINQ queries that take advantage of this relationship using the `Join` clause, see [How to: Join Two Collections (LINQ to XML) (Visual Basic)](how-to-join-two-collections-linq-to-xml.md).</span></span>  
  
## <a name="customersordersxsd"></a><span data-ttu-id="96f50-107">CustomersOrders.xsd</span><span class="sxs-lookup"><span data-stu-id="96f50-107">CustomersOrders.xsd</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name='Root'>  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name='Customers'>  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name='Customer' type='CustomerType' minOccurs='0' maxOccurs='unbounded' />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name='Orders'>  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name='Order' type='OrderType' minOccurs='0' maxOccurs='unbounded' />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
    <xs:key name='CustomerIDKey'>  
      <xs:selector xpath='Customers/Customer'/>  
      <xs:field xpath='@CustomerID'/>  
    </xs:key>  
    <xs:keyref name='CustomerIDKeyRef' refer='CustomerIDKey'>  
      <xs:selector xpath='Orders/Order'/>  
      <xs:field xpath='CustomerID'/>  
    </xs:keyref>  
  </xs:element>  
  <xs:complexType name='CustomerType'>  
    <xs:sequence>  
      <xs:element name='CompanyName' type='xs:string'/>  
      <xs:element name='ContactName' type='xs:string'/>  
      <xs:element name='ContactTitle' type='xs:string'/>  
      <xs:element name='Phone' type='xs:string'/>  
      <xs:element name='Fax' minOccurs='0' type='xs:string'/>  
      <xs:element name='FullAddress' type='AddressType'/>  
    </xs:sequence>  
    <xs:attribute name='CustomerID' type='xs:token'/>  
  </xs:complexType>  
  <xs:complexType name='AddressType'>  
    <xs:sequence>  
      <xs:element name='Address' type='xs:string'/>  
      <xs:element name='City' type='xs:string'/>  
      <xs:element name='Region' type='xs:string'/>  
      <xs:element name='PostalCode' type='xs:string' />  
      <xs:element name='Country' type='xs:string'/>  
    </xs:sequence>  
    <xs:attribute name='CustomerID' type='xs:token'/>  
  </xs:complexType>  
  <xs:complexType name='OrderType'>  
    <xs:sequence>  
      <xs:element name='CustomerID' type='xs:token'/>  
      <xs:element name='EmployeeID' type='xs:token'/>  
      <xs:element name='OrderDate' type='xs:dateTime'/>  
      <xs:element name='RequiredDate' type='xs:dateTime'/>  
      <xs:element name='ShipInfo' type='ShipInfoType'/>  
    </xs:sequence>  
  </xs:complexType>  
  <xs:complexType name='ShipInfoType'>  
    <xs:sequence>  
      <xs:element name='ShipVia' type='xs:integer'/>  
      <xs:element name='Freight' type='xs:decimal'/>  
      <xs:element name='ShipName' type='xs:string'/>  
      <xs:element name='ShipAddress' type='xs:string'/>  
      <xs:element name='ShipCity' type='xs:string'/>  
      <xs:element name='ShipRegion' type='xs:string'/>  
      <xs:element name='ShipPostalCode' type='xs:string'/>  
      <xs:element name='ShipCountry' type='xs:string'/>  
    </xs:sequence>  
    <xs:attribute name='ShippedDate' type='xs:dateTime'/>  
  </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96f50-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96f50-108">See also</span></span>

- [<span data-ttu-id="96f50-109">Exemples de documents XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="96f50-109">Sample XML Documents (LINQ to XML)</span></span>](sample-xml-documents-linq-to-xml.md)
