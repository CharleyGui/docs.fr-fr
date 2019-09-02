---
title: Mapper les relations spécifiées pour les éléments imbriqués
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 510a5e676df7bac274c6086b94e9a23e7540da20
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204637"
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapper les relations spécifiées pour les éléments imbriqués
Un schéma peut inclure une annotation **msdata: Relationship** pour spécifier explicitement le mappage entre deux éléments quelconques dans le schéma. Les deux éléments spécifiés dans **msdata: Relationship** peuvent être imbriqués dans le schéma, mais n’ont pas besoin d’être. Le processus de mappage utilise l' **Annotation msdata: Relationship** dans le schéma pour générer la relation clé primaire/clé étrangère entre les deux colonnes.  
  
 L’exemple suivant illustre un schéma XML dans lequel l’élément **OrderDetail** est un élément enfant de **Order**. L' **Annotation msdata: Relationship** identifie cette relation parent-enfant et spécifie que la colonne **OrderNumber** de la table **Order** obtenue est associée à la colonne **OrderNo** de la table **OrderDetail** résultante.  
  
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
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- Relation entre les tables **Order** et **OrderDetail** . La propriété Nested de cette relation a la valeur **true** , car les éléments **Order** et **OrderDetail** sont imbriqués dans le schéma.  
  
    ```  
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
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
