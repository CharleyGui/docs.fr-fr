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
# <a name="specify-relations-between-elements-with-no-nesting"></a>Spécifier les relations entre éléments sans imbrication

Lorsque des éléments ne sont pas imbriqués, aucune relation implicite n'est créée. Toutefois, vous pouvez spécifier explicitement des relations entre des éléments qui ne sont pas imbriqués à l’aide de l’annotation **msdata : Relationship** .  
  
 L’exemple suivant illustre un schéma XML dans lequel l’annotation **msdata : Relationship** est spécifiée entre les éléments **Order** et **OrderDetail** , qui ne sont pas imbriqués. L’annotation **msdata : Relationship** est spécifiée en tant qu’élément enfant de l’élément **Schema** .  
  
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
  
 Le processus de mappage de schéma en langage XSD (XML Schema Definition) crée un <xref:System.Data.DataSet> avec les tables **Order** et **OrderDetail** , ainsi qu’une relation entre ces deux tables, comme indiqué ci-dessous.  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a>Voir aussi

- [Génération de relations de DataSet à partir du schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
