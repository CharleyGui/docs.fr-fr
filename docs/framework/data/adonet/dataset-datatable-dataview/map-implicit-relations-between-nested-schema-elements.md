---
title: Mapper les relations implicites entre éléments de schéma imbriqués
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: e9ea85db98a577991e06e0239a0738a2ca5bada6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203481"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapper les relations implicites entre éléments de schéma imbriqués
Un schéma en langage XSD (XML Schema Definition) peut présenter des types complexes imbriqués les uns dans les autres. Dans ce cas, le processus de mappage applique le mappage par défaut et crée les différents éléments suivants dans l'objet <xref:System.Data.DataSet> :  
  
- Une table pour chacun des types complexes (parent et enfant).  
  
- S’il n’existe aucune contrainte unique sur le parent, une colonne de clé primaire supplémentaire par définition de table nommée *TableName*_ ID où *TableName* est le nom de la table parente.  
  
- Contrainte de clé primaire sur la table parente identifiant la colonne supplémentaire en tant que clé primaire (en affectant à la propriété **IsPrimaryKey** la **valeur true**). La contrainte est nommée selon le modèle Constraint\#, où \# est 1, 2, 3, etc. Par exemple, le nom par défaut de la première contrainte est Constraint1.  
  
- Une contrainte de clé étrangère sur la table enfant, qui identifie la colonne supplémentaire en tant que clé étrangère faisant référence à la clé primaire de la table parente. La contrainte est nommée *ParentTable_ChildTable* où *ParentTable* est le nom de la table parente et *ChildTable* est le nom de la table enfant.  
  
- Une relation de données entre les tables parente et enfant.  
  
 L’exemple suivant illustre un schéma où **OrderDetail** est un élément enfant de **Order**.  
  
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
  
 Le processus de mappage de schéma XML crée les éléments suivants dans le **jeu de données**:  
  
- Une **commande Order** et une table **OrderDetail** .  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- Contrainte unique sur la table **Order** . Notez que la propriété **IsPrimaryKey** a la valeur **true**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- Contrainte de clé étrangère sur la table **OrderDetail** .  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- Relation entre les tables **Order** et **OrderDetail** . La propriété Nested de cette relation a la valeur **true** , car les éléments **Order** et **OrderDetail** sont imbriqués dans le schéma.  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Génération de relations de DataSet à partir du schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
