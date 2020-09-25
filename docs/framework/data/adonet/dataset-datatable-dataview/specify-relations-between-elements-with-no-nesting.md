---
title: Spécifier les relations entre éléments sans imbrication
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 6684e992242d5c695f3c237f70de61b4dae1c48f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183401"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="4ed74-102">Spécifier les relations entre éléments sans imbrication</span><span class="sxs-lookup"><span data-stu-id="4ed74-102">Specify Relations Between Elements with No Nesting</span></span>

<span data-ttu-id="4ed74-103">Lorsque des éléments ne sont pas imbriqués, aucune relation implicite n'est créée.</span><span class="sxs-lookup"><span data-stu-id="4ed74-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="4ed74-104">Toutefois, vous pouvez spécifier explicitement des relations entre des éléments qui ne sont pas imbriqués à l’aide de l’annotation **msdata : Relationship** .</span><span class="sxs-lookup"><span data-stu-id="4ed74-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="4ed74-105">L’exemple suivant illustre un schéma XML dans lequel l’annotation **msdata : Relationship** est spécifiée entre les éléments **Order** et **OrderDetail** , qui ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="4ed74-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="4ed74-106">L’annotation **msdata : Relationship** est spécifiée en tant qu’élément enfant de l’élément **Schema** .</span><span class="sxs-lookup"><span data-stu-id="4ed74-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
             xmlns:xs="http://www.w3.org/2001/XMLSchema"
             xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:string" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNumber" type="xs:string" />  
           <xs:element name="EmpNumber" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  </xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrderDetailRelation"  
                            msdata:parent="Order"
                            msdata:child="OrderDetail"
                            msdata:parentkey="OrderNumber"
                            msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
</xs:schema>  
```  
  
 <span data-ttu-id="4ed74-107">Le processus de mappage de schéma en langage XSD (XML Schema Definition) crée un <xref:System.Data.DataSet> avec les tables **Order** et **OrderDetail** , ainsi qu’une relation entre ces deux tables, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="4ed74-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ed74-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ed74-108">See also</span></span>

- [<span data-ttu-id="4ed74-109">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="4ed74-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="4ed74-110">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="4ed74-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="4ed74-111">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4ed74-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
