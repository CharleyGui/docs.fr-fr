---
title: Spécifier les relations entre éléments sans imbrication
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 83dce7173c016a7d7d2d626bb7a3606de29d54ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204463"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="2654c-102">Spécifier les relations entre éléments sans imbrication</span><span class="sxs-lookup"><span data-stu-id="2654c-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="2654c-103">Lorsque des éléments ne sont pas imbriqués, aucune relation implicite n'est créée.</span><span class="sxs-lookup"><span data-stu-id="2654c-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="2654c-104">Toutefois, vous pouvez spécifier explicitement des relations entre des éléments qui ne sont pas imbriqués à l’aide de l’annotation **msdata: Relationship** .</span><span class="sxs-lookup"><span data-stu-id="2654c-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="2654c-105">L’exemple suivant illustre un schéma XML dans lequel l’annotation **msdata: Relationship** est spécifiée entre les éléments **Order** et **OrderDetail** , qui ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="2654c-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="2654c-106">L’annotation **msdata: Relationship** est spécifiée en tant qu’élément enfant de l’élément **Schema** .</span><span class="sxs-lookup"><span data-stu-id="2654c-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="2654c-107">Le processus de mappage de schéma en langage XSD (XML Schema Definition <xref:System.Data.DataSet> ) crée un avec les tables **Order** et **OrderDetail** , ainsi qu’une relation entre ces deux tables, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="2654c-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="2654c-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2654c-108">See also</span></span>

- [<span data-ttu-id="2654c-109">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="2654c-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="2654c-110">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="2654c-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="2654c-111">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="2654c-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
