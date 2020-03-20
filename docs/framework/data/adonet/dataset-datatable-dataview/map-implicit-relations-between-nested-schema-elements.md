---
title: Mapper les relations implicites entre éléments de schéma imbriqués
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150961"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapper les relations implicites entre éléments de schéma imbriqués
Un schéma en langage XSD (XML Schema Definition) peut présenter des types complexes imbriqués les uns dans les autres. Dans ce cas, le processus de mappage applique le mappage par défaut et crée les différents éléments suivants dans l'objet <xref:System.Data.DataSet> :  
  
- Une table pour chacun des types complexes (parent et enfant).  
  
- S’il n’existe aucune contrainte unique sur le parent, une colonne clé primaire supplémentaire par définition de tableau nommée *TableName*_Id où *TableName* est le nom de la table mère.  
  
- Une contrainte clé primaire sur le tableau parent identifiant la colonne supplémentaire comme la clé principale (en fixant la propriété **IsPrimaryKey** à **True**). La contrainte est nommée selon le modèle Constraint\#, où \# est 1, 2, 3, etc. Par exemple, le nom par défaut de la première contrainte est Constraint1.  
  
- Une contrainte de clé étrangère sur la table enfant, qui identifie la colonne supplémentaire en tant que clé étrangère faisant référence à la clé primaire de la table parente. La contrainte est nommée *ParentTable_ChildTable* où *ParentTable* est le nom de la table mère et *ChildTable* est le nom de la table de l’enfant.  
  
- Une relation de données entre les tables parente et enfant.  
  
 L’exemple suivant montre un schéma où **OrderDetail** est un élément enfant de **l’Ordre**.  
  
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
  
 Le processus de cartographie XML Schema crée ce qui suit dans le **DataSet**:  
  
- Une **commande** et une table **OrderDetail.**  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- Une contrainte unique sur la table de **l’Ordre.** Notez que la propriété **IsPrimaryKey** est définie à **True**.  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- Une contrainte clé étrangère sur la table **OrderDetail.**  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- Une relation entre les tables **Order** et **OrderDetail.** La propriété **nichée** pour cette relation est définie à **Vrai** parce que les éléments **De l’Ordre** et **de l’Ordre** sont imbriqués dans le schéma.  
  
    ```text  
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
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
