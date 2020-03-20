---
title: Spécifier les relations entre éléments sans imbrication
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: bee427c6cdf76792773ea827c8772b276ff29c31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150816"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="c989d-102">Spécifier les relations entre éléments sans imbrication</span><span class="sxs-lookup"><span data-stu-id="c989d-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="c989d-103">Lorsque des éléments ne sont pas imbriqués, aucune relation implicite n'est créée.</span><span class="sxs-lookup"><span data-stu-id="c989d-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="c989d-104">Vous pouvez cependant spécifier explicitement les relations entre les éléments qui ne sont pas imbriqués en utilisant **l’annotation msdata:Relation.**</span><span class="sxs-lookup"><span data-stu-id="c989d-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="c989d-105">L’exemple suivant montre un schéma XML dans lequel **l’annotation msdata:Relation** est spécifiée entre les éléments **Order** et **OrderDetail,** qui ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="c989d-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="c989d-106">**L’annotation msdata:Relation** est spécifiée comme l’élément enfant de l’élément **Schema.**</span><span class="sxs-lookup"><span data-stu-id="c989d-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="c989d-107">Le processus de cartographie des schémas de définition XML Schema (XSD) crée une <xref:System.Data.DataSet> relation avec les tables **Order** and **OrderDetail** et une relation spécifiée entre ces deux tableaux, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c989d-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="c989d-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c989d-108">See also</span></span>

- [<span data-ttu-id="c989d-109">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="c989d-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="c989d-110">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="c989d-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="c989d-111">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c989d-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
