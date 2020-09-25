---
title: Contraintes et relations du schéma XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 5861386e42defa189aaa50a3af0bd95d7e9257fd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173703"
---
# <a name="xml-schema-constraints-and-relationships"></a>Contraintes et relations du schéma XML

Dans un schéma en langage XSD (XML Schema Definition), vous pouvez spécifier des contraintes (unique, Key et keyref) et des relations (à l’aide de l’annotation **msdata : Relationship** ). Cette rubrique explique comment les contraintes et relations spécifiées dans un schéma XML sont interprétées pour générer l'objet <xref:System.Data.DataSet>.  
  
 En général, dans un schéma XML, vous spécifiez l’annotation **msdata : Relationship** si vous souhaitez générer uniquement des relations dans le **DataSet**. Pour plus d’informations, consultez [génération de relations de DataSet à partir d’un schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md). Vous spécifiez des contraintes (unique, Key et keyref) si vous souhaitez générer des contraintes dans le **DataSet**. Notez que les contraintes key et keyref peuvent aussi servir à générer des relations, comme expliqué plus loin dans cette rubrique.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Génération d'une relation à partir des contraintes key et keyref  

 Au lieu de spécifier l’annotation **msdata : Relationship** , vous pouvez spécifier des contraintes Key et keyref, qui sont utilisées pendant le processus de mappage du schéma XML pour générer non seulement les contraintes, mais également la relation dans le **DataSet**. Toutefois, si vous spécifiez `msdata:ConstraintOnly="true"` dans l’élément **keyref** , le **DataSet** inclut uniquement les contraintes et n’inclut pas la relation.  
  
 L’exemple suivant illustre un schéma XML qui comprend des éléments **Order** et **OrderDetail** , qui ne sont pas imbriqués. Le schéma spécifie également des contraintes key et keyref.  
  
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
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 Le **DataSet** généré pendant le processus de mappage du schéma XML comprend les tables **Order** et **OrderDetail** . En outre, le **DataSet** comprend des relations et des contraintes. L'exemple suivant illustre ces relations et contraintes. Notez que le schéma ne spécifie pas l’annotation **msdata : Relationship** ; au lieu de cela, les contraintes Key et keyref sont utilisées pour générer la relation.  
  
```text
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 Dans l’exemple de schéma précédent, les éléments **Order** et **OrderDetail** ne sont pas imbriqués. Ils le sont dans l'exemple qui suit. Toutefois, aucune annotation **msdata : Relationship** n’est spécifiée ; par conséquent, une relation implicite est supposée. Pour plus d’informations, consultez [mapper les relations implicites entre les éléments de schéma imbriqués](map-implicit-relations-between-nested-schema-elements.md). Le schéma spécifie également des contraintes key et keyref.  
  
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
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 Le **jeu de données** résultant du processus de mappage du schéma XML comprend deux tables :  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 Le **DataSet** comprend également les deux relations (une basée sur l’annotation **msdata : Relationship** et l’autre basée sur les contraintes Key et keyref) et diverses contraintes. L'exemple suivant illustre ces relations et contraintes.  
  
```text
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 Si une contrainte keyref faisant référence à une table imbriquée contient l’annotation **msdata : IsNested = "true"** , le **DataSet** crée une seule relation imbriquée basée sur la contrainte keyref et la contrainte unique/Key associée.  
  
## <a name="see-also"></a>Voir aussi

- [Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
