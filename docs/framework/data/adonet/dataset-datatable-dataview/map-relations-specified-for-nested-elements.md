---
title: Mapper les relations spécifiées pour les éléments imbriqués
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: f758e1ef2c3786a102dc6bb5f6dd217b20dc5b55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198546"
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapper les relations spécifiées pour les éléments imbriqués

Un schéma peut inclure une annotation **msdata : Relationship** pour spécifier explicitement le mappage entre deux éléments quelconques dans le schéma. Les deux éléments spécifiés dans **msdata : Relationship** peuvent être imbriqués dans le schéma, mais n’ont pas besoin d’être. Le processus de mappage utilise l' **Annotation msdata : Relationship** dans le schéma pour générer la relation clé primaire/clé étrangère entre les deux colonnes.  
  
 L’exemple suivant illustre un schéma XML dans lequel l’élément **OrderDetail** est un élément enfant de **Order**. L' **Annotation msdata : Relationship** identifie cette relation parent-enfant et spécifie que la colonne **OrderNumber** de la table **Order** obtenue est associée à la colonne **OrderNo** de la table **OrderDetail** résultante.  
  
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
  
- Une **commande Order** et une table **OrderDetail** .  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- Relation entre les tables **Order** et **OrderDetail** . La propriété **Nested** de cette relation a la valeur **true** , car les éléments **Order** et **OrderDetail** sont imbriqués dans le schéma.  
  
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
