---
title: Mapper les contraintes clés de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 5ebf333b065157fa9497cc1471a45698663638e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150933"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapper les contraintes clés de schéma XML (XSD) aux contraintes de DataSet
Dans un schéma, vous pouvez spécifier une contrainte clé sur un élément ou un attribut à l’aide de **l’élément clé.** L'élément ou attribut sur lequel une contrainte de clé est spécifiée doit avoir des valeurs uniques dans toute instance du schéma et ne peut pas avoir de valeurs null.  
  
 La contrainte de clé est similaire à la contrainte unique, si ce n'est que la colonne sur laquelle une contrainte de clé est définie ne peut pas comporter de valeurs null.  
  
 Le tableau suivant décrit les attributs **msdata** que vous pouvez spécifier dans l’élément **clé.**  
  
|Nom de l’attribut|Description|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte. Dans le cas contraire, l’attribut de **nom** fournit la valeur du nom de contrainte.|  
|**msdata:PrimaryKey**|Si `PrimaryKey="true"` elle est présente, la propriété de contrainte **IsPrimaryKey** est définie pour **vrai,** ce qui en fait une clé principale. La propriété de colonne **AllowDBNull** est réglée à **faux,** parce que les clés primaires ne peuvent pas avoir des valeurs nulles.|  
  
 En convertissant le schéma dans lequel une contrainte clé est spécifiée, le processus de cartographie crée une contrainte unique sur la table avec la propriété de colonne **AllowDBNull** réglée à **faux** pour chaque colonne dans la contrainte. La propriété **IsPrimaryKey** de la contrainte **false** unique est également `msdata:PrimaryKey="true"` définie à faux à moins que vous avez spécifié sur l’élément **clé.** Ce mode de fonctionnement est identique à celui d'une contrainte unique dans le schéma faisant apparaître `PrimaryKey="true"`.  
  
 Dans l’exemple de schéma suivant, l’élément **clé** spécifie la contrainte clé sur l’élément **CustomerID.**  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 **L’élément clé** précise que les valeurs de **l’élément enfant ClientID** de **l’élément Clients** doivent avoir des valeurs uniques et ne peuvent pas avoir de valeurs nulles. En convertissant le schéma en langage XSD (XML Schema Definition), le processus de mappage crée la table suivante :  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 La cartographie XML Schema crée également un **UniqueConstraint** sur la <xref:System.Data.DataSet>colonne **CustomerID,** comme le montre ce qui suit . (Par souci de simplicité, seules les propriétés pertinentes sont représentées.)  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 Dans le **DataSet** qui est généré, la propriété **IsPrimaryKey** de **l’UniqueConstraint** est définie pour **vrai** parce que le schéma spécifie `msdata:PrimaryKey="true"` dans **l’élément clé.**  
  
 La valeur de la propriété **ConstraintName** de **l’UniqueConstraint** dans le **DataSet** est la valeur de **l’attribut msdata:ConstraintName** spécifié dans **l’élément clé** du schéma.  
  
## <a name="see-also"></a>Voir aussi

- [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Génération de relations de DataSet à partir du schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
