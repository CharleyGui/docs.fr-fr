---
title: Mapper les relations spécifiées pour les éléments imbriqués
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: cd652f51f01dcfa16a8b707f35c658043c20670d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150894"
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapper les relations spécifiées pour les éléments imbriqués
Un schéma peut inclure une **msdata:Relationship** annotation pour spécifier explicitement la cartographie entre deux éléments du schéma. Les deux éléments spécifiés dans **msdata:Relation** peut être imbriqué dans le schéma, mais n’ont pas à être. Le processus de cartographie utilise **msdata:Relation** dans le schéma pour générer la clé principale / relation clé étrangère entre les deux colonnes.  
  
 L’exemple suivant montre un schéma XML dans lequel **l’élément OrderDetail** est un élément enfant de **l’Ordre**. La **msdata:Relation** identifie cette relation parent-enfant et précise que la colonne **OrderNumber** de la table de **l’Ordre** qui en résulte est liée à la colonne **OrderNo** de la table **OrderDetail** résultant.  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
 <xs:complexType>  
  <xs:choice maxOccurs="unbounded">  
   <xs:element name="Order">  
    <xs:complexType>  
     <xs:sequence>  
       <xs:element name="OrderNumber" type="xs:string" />  
       <xs:element name="EmpNumber" type="xs:string" />  
       <xs:element name="OrderDetail">  
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"
                                msdata:parent="Order"
                                msdata:child="OrderDetail"
                                msdata:parentkey="OrderNumber"
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
          <xs:complexType>  
            <xs:sequence>  
             <xs:element name="OrderNo" type="xs:string" />  
             <xs:element name="ItemNo" type="xs:string" />  
            </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:sequence>  
    </xs:complexType>  
   </xs:element>  
  </xs:choice>  
 </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
 Le processus de mappage du schéma XML crée les éléments suivants dans le <xref:System.Data.DataSet> :  
  
- Une **commande** et une table **OrderDetail.**  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- Une relation entre les tables **Order** et **OrderDetail.** La propriété **nichée** pour cette relation est définie à **Vrai** parce que les éléments **De l’Ordre** et **de l’Ordre** sont imbriqués dans le schéma.  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 Le processus de mappage ne crée aucune contrainte.  
  
## <a name="see-also"></a>Voir aussi

- [Génération de relations de DataSet à partir du schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
