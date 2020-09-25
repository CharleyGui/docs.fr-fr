---
title: Mapper les contraintes clés de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: b55b232faa01bf36788276caaf8bc2e97dddf697
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172786"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapper les contraintes clés de schéma XML (XSD) aux contraintes de DataSet

Dans un schéma, vous pouvez spécifier une contrainte de clé sur un élément ou un attribut à l’aide de l’élément **Key** . L'élément ou attribut sur lequel une contrainte de clé est spécifiée doit avoir des valeurs uniques dans toute instance du schéma et ne peut pas avoir de valeurs null.  
  
 La contrainte de clé est similaire à la contrainte unique, si ce n'est que la colonne sur laquelle une contrainte de clé est définie ne peut pas comporter de valeurs null.  
  
 Le tableau suivant présente les attributs **msdata** que vous pouvez spécifier dans l’élément **Key** .  
  
|Nom de l’attribut|Description|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte. Dans le cas contraire, l’attribut **Name** fournit la valeur du nom de la contrainte.|  
|**msdata:PrimaryKey**|Si `PrimaryKey="true"` est présent, la propriété de contrainte **IsPrimaryKey** a la valeur **true**, ce qui en fait une clé primaire. La propriété de la colonne **AllowDBNull** a la valeur **false**, car les clés primaires ne peuvent pas avoir de valeurs NULL.|  
  
 Lors de la conversion d’un schéma dans lequel une contrainte de clé est spécifiée, le processus de mappage crée une contrainte unique sur la table avec la propriété de colonne **AllowDBNull** définie sur **false** pour chaque colonne de la contrainte. La propriété **IsPrimaryKey** de la contrainte unique a également la valeur **false** , sauf si vous avez spécifié `msdata:PrimaryKey="true"` sur l’élément **Key** . Ce mode de fonctionnement est identique à celui d'une contrainte unique dans le schéma faisant apparaître `PrimaryKey="true"`.  
  
 Dans l’exemple de schéma suivant, l’élément **Key** spécifie la contrainte de clé sur l’élément **CustomerID** .  
  
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
  
 L’élément **Key** spécifie que les valeurs de l’élément enfant **CustomerID** de l’élément **Customers** doivent avoir des valeurs uniques et ne peuvent pas avoir de valeurs NULL. En convertissant le schéma en langage XSD (XML Schema Definition), le processus de mappage crée la table suivante :  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 Le mappage de schéma XML crée également un **UniqueConstraint** sur la colonne **CustomerID** , comme indiqué dans le code suivant <xref:System.Data.DataSet> . (Par souci de simplicité, seules les propriétés pertinentes sont représentées.)  
  
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
  
 Dans le **DataSet** généré, la propriété **IsPrimaryKey** de **UniqueConstraint** a la valeur **true** car le schéma spécifie `msdata:PrimaryKey="true"` dans l’élément **Key** .  
  
 La valeur de la propriété **ConstraintName** de **UniqueConstraint** dans le **DataSet** est la valeur de l’attribut **msdata : ConstraintName** spécifié dans l’élément **Key** du schéma.  
  
## <a name="see-also"></a>Voir aussi

- [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Génération de relations de DataSet à partir du schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
