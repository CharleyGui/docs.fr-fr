---
title: Contraintes et relations du schéma XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 2388d7c277ba1f01bea8d419e5aedf487b843ed7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150712"
---
# <a name="xml-schema-constraints-and-relationships"></a>Contraintes et relations du schéma XML
Dans un schéma de définition XML Schema (XSD), vous pouvez spécifier les contraintes (contraintes uniques, clés et keyref) et les relations (à l’aide de **l’annotation msdata:Relation).** Cette rubrique explique comment les contraintes et relations spécifiées dans un schéma XML sont interprétées pour générer l'objet <xref:System.Data.DataSet>.  
  
 En général, dans un schéma XML, vous spécifiez **l’annotation msdata:Relation** si vous voulez générer uniquement des relations dans le **DataSet**. Pour plus d’informations, voir [Generating DataSet Relations de XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md). Vous spécifiez des contraintes (uniques, clés et keyref) si vous souhaitez générer des contraintes dans le **DataSet**. Notez que les contraintes key et keyref peuvent aussi servir à générer des relations, comme expliqué plus loin dans cette rubrique.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Génération d'une relation à partir des contraintes key et keyref  
 Au lieu de spécifier **l’annotation msdata:Relation,** vous pouvez spécifier les contraintes clés et keyref, qui sont utilisés pendant le processus de cartographie XML Schema pour générer non seulement les contraintes, mais aussi la relation dans le **DataSet**. Toutefois, si `msdata:ConstraintOnly="true"` vous spécifiez dans **l’élément keyref,** le **DataSet** n’inclura que les contraintes et n’inclura pas la relation.  
  
 L’exemple suivant montre un schéma XML qui comprend des éléments **Order** et **OrderDetail,** qui ne sont pas imbriqués. Le schéma spécifie également des contraintes key et keyref.  
  
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
  
 Le **DataSet** généré au cours du processus de cartographie XML Schema comprend les tables **Order** et **OrderDetail.** En outre, le **DataSet** inclut les relations et les contraintes. L'exemple suivant illustre ces relations et contraintes. Notez que le schéma ne précise pas la **msdata:Annotation relationnelle;** au lieu de cela, les contraintes clés et keyref sont utilisées pour générer la relation.  
  
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
  
 Dans l’exemple précédent du schéma, les éléments **Order** and **OrderDetail** ne sont pas imbriqués. Ils le sont dans l'exemple qui suit. Cependant, aucune **msdata:** L’annotation relationnelle est spécifiée; par conséquent, une relation implicite est supposée. Pour plus d’informations, voir [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md). Le schéma spécifie également des contraintes key et keyref.  
  
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
  
 Le **DataSet** résultant du processus de cartographie XML Schema comprend deux tableaux :  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 Le **DataSet** comprend également les deux relations (l’une basée sur la **msdata:annotation relationnelle** et l’autre basée sur les contraintes clés et clés) et diverses contraintes. L'exemple suivant illustre ces relations et contraintes.  
  
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
  
 Si une contrainte de clé se référant à une table imbriquée contient **l’annotation msdata:IsNestedMD "vrai",** le **DataSet** créera une seule relation imbriquée qui est basée sur la contrainte keyref et la contrainte unique/clé connexe.  
  
## <a name="see-also"></a>Voir aussi

- [Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
