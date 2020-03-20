---
title: Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 902b79b73f494ced0f54b29babff1b2e767bd47a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150881"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet
**L’élément keyref** vous permet d’établir des liens entre les éléments d’un document. Le résultat est similaire à une relation de clé étrangère dans une base de données relationnelle. Si un schéma spécifie **l’élément keyref,** l’élément est converti au cours du processus de <xref:System.Data.DataSet>cartographie du schéma en une contrainte clé étrangère correspondante sur les colonnes dans les tableaux de la . Par défaut, **l’élément keyref** génère également une relation, avec les propriétés **ParentTable**, **ChildTable**, **ParentColumn**et **ChildColumn** spécifiées sur la relation.  
  
 Le tableau suivant décrit les attributs **msdata** que vous pouvez spécifier dans l’élément **keyref.**  
  
|Nom de l’attribut|Description|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Si **ConstraintOnlyMD "vrai"** est spécifié sur **l’élément keyref** dans le schéma, une contrainte est créée, mais aucune relation n’est créée. Si cet attribut n’est pas spécifié (ou est réglé sur **Faux),** la contrainte et la relation sont créées dans le **DataSet**.|  
|**msdata:ConstraintName**|Si l’attribut **ConstraintName** est spécifié, sa valeur est utilisée comme nom de la contrainte. Dans **le** cas contraire, l’attribut nom de l’élément **keyref** dans le schéma fournit le nom de contrainte dans le **DataSet**.|  
|**msdata:UpdateRule**|Si l’attribut **UpdateRule** est spécifié dans **l’élément keyref** dans le schéma, sa valeur est attribuée à la propriété de contrainte **UpdateRule** dans le **DataSet**. Sinon, la propriété **UpdateRule** est réglée sur **Cascade**.|  
|**msdata:DeleteRule**|Si l’attribut **DeleteRule** est spécifié dans **l’élément keyref** dans le schéma, sa valeur est attribuée à la propriété de contrainte **DeleteRule** dans le **DataSet**. Sinon, la propriété **DeleteRule** est réglée sur **Cascade**.|  
|**msdata:AcceptRejectRule**|Si **l’attribut AcceptRejectRule** est spécifié dans **l’élément keyref** dans le schéma, sa valeur est attribuée à la propriété de contrainte **AcceptRejectRule** dans le **DataSet**. Sinon, la propriété **AcceptRejectRule** est réglée à **Aucun**.|  
  
 L’exemple suivant contient un schéma qui spécifie les relations **clés** et **Order** **clés** entre **l’élément enfant de l’Ordre** et **l’élément** enfant OrderNo de l’élément **OrderDetail.**  
  
 Dans l’exemple, **l’élément enfant de l’ordrenumber** de l’élément **OrderDetail** se réfère à **l’élément** clé de l’ordre n’a pas d’enfant clé de l’élément **de l’Ordre.**  
  
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
  
 Le processus de cartographie des schémas de définition XML Schema (XSD) produit le **DataSet** suivant avec deux tableaux :  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 En outre, le **DataSet** définit les contraintes suivantes :  
  
- Une contrainte unique sur la table de **l’Ordre.**  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- Une relation entre les tables **Order** et **OrderDetail.** La propriété **nichée** est réglée à **Faux** parce que les deux éléments ne sont pas imbriqués dans le schéma.  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- Une contrainte clé étrangère sur la table **OrderDetail.**  
  
    ```text  
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
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
