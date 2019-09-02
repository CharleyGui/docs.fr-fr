---
title: Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 611322065a4df53d1a3149ef4e1ca5592f149081
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203439"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet
L’élément **keyref** vous permet d’établir des liens entre des éléments dans un document. Le résultat est similaire à une relation de clé étrangère dans une base de données relationnelle. Si un schéma spécifie l’élément **keyref** , l’élément est converti pendant le processus de mappage de schéma en une contrainte de clé étrangère correspondante sur les colonnes dans <xref:System.Data.DataSet>les tables de. Par défaut, l’élément **keyref** génère également une relation, avec les **Propriétés ParentTable**, **ChildTable**, **ParentColumn**et **ChildColumn** spécifiées sur la relation.  
  
 Le tableau suivant présente les attributs **msdata** que vous pouvez spécifier dans l’élément **keyref** .  
  
|Nom d'attribut|Description|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Si **ConstraintOnly = "true"** est spécifié sur l’élément **keyref** du schéma, une contrainte est créée, mais aucune relation n’est créée. Si cet attribut n’est pas spécifié (ou a lavaleur false), la contrainte et la relation sont créées dans le **DataSet**.|  
|**msdata:ConstraintName**|Si l’attribut **ConstraintName** est spécifié, sa valeur est utilisée comme nom de la contrainte. Dans le cas contraire, l’attribut **Name** de l’élément **keyref** dans le schéma fournit le nom de la contrainte dans le **DataSet**.|  
|**msdata:UpdateRule**|Si l’attribut **UpdateRule** est spécifié dans l’élément **keyref** du schéma, sa valeur est assignée à la propriété **UpdateRule** de la contrainte dans le **DataSet**. Sinon, la propriété **UpdateRule** a la valeur **cascade**.|  
|**msdata:DeleteRule**|Si l’attribut **DeleteRule** est spécifié dans l’élément **keyref** du schéma, sa valeur est assignée à la propriété de contrainte **DeleteRule** dans le **DataSet**. Sinon, la propriété **DeleteRule** a la valeur **cascade**.|  
|**msdata:AcceptRejectRule**|Si l’attribut **AcceptRejectRule** est spécifié dans l’élément **keyref** du schéma, sa valeur est assignée à la propriété **AcceptRejectRule** de la contrainte dans le **DataSet**. Sinon, la propriété **AcceptRejectRule** est définie sur **None**.|  
  
 L’exemple suivant contient un schéma qui spécifie les relations **Key** et **keyref** entre l’élément enfant **OrderNumber** de l’élément **Order** et l’élément enfant **OrderNo** de **OrderDetail** appartient.  
  
 Dans l’exemple, l’élément enfant **OrderNumber** de l’élément **OrderDetail** fait référence à l’élément enfant de la clé **OrderNo** de l’élément **Order** .  
  
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
  
 Le processus de mappage de schéma en langage XSD (XML Schema Definition) génère le **jeu de données** suivant avec deux tables:  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 En outre, le **jeu de données** définit les contraintes suivantes:  
  
- Contrainte unique sur la table **Order** .  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- Relation entre les tables **Order** et **OrderDetail** . La propriété Nested a la valeur **false** , car les deux éléments ne sont pas imbriqués dans le schéma.  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- Contrainte de clé étrangère sur la table **OrderDetail** .  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Génération de relations de DataSet à partir du schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
