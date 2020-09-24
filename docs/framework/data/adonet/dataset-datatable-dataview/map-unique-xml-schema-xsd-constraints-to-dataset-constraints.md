---
title: Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 3b2dad44176e52adcf32e2e3ccff3d82ba23f6ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153233"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet

Dans un schéma en langage XSD (XML Schema Definition), l’élément **unique** spécifie la contrainte d’unicité sur un élément ou un attribut. Dans le processus de conversion d'un schéma XML en schéma relationnel, la contrainte unique spécifiée sur un élément ou un attribut du schéma XML est mappée à une contrainte unique dans l'objet <xref:System.Data.DataTable> de l'objet <xref:System.Data.DataSet> correspondant qui est généré.  
  
 Le tableau suivant présente les attributs **msdata** que vous pouvez spécifier dans l’élément **unique** .  
  
|Nom de l’attribut|Description|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte. Dans le cas contraire, l’attribut **Name** fournit la valeur du nom de la contrainte.|  
|**msdata:PrimaryKey**|Si `PrimaryKey="true"` est présent dans l’élément **unique** , une contrainte unique est créée avec la valeur **true**affectée à la propriété **IsPrimaryKey** .|  
  
 L’exemple suivant illustre un schéma XML qui utilise l’élément **unique** pour spécifier une contrainte d’unicité.  
  
```xml  
<xs:schema id="SampleDataSet"
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 L’élément **unique** dans le schéma spécifie que pour tous les éléments **Customers** dans une instance de document, la valeur de l’élément enfant **CustomerID** doit être unique. Lors de la génération du **jeu de données**, le processus de mappage lit ce schéma et génère la table suivante :  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Le processus de mappage crée également une contrainte unique sur la colonne **CustomerID** , comme indiqué dans le **jeu de données**suivant. (Par souci de simplicité, seules les propriétés pertinentes sont représentées.)  
  
```text  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID
      IsPrimaryKey: False  
```  
  
 Dans le **DataSet** généré, la propriété **IsPrimaryKey** a la valeur **false** pour la contrainte unique. La propriété **unique** sur la colonne indique que les valeurs de la colonne **CustomerID** doivent être uniques (mais elles peuvent être une référence null, comme spécifié par la propriété **AllowDBNull** de la colonne).  
  
 Si vous modifiez le schéma et définissez la valeur d’attribut **msdata : PrimaryKey** facultative sur **true**, la contrainte unique est créée sur la table. La propriété de la colonne **AllowDBNull** a la valeur **false**et la propriété **IsPrimaryKey** de la contrainte a la valeur **true**, ce qui fait de la colonne **CustomerID** une colonne de clé primaire.  
  
 Vous pouvez spécifier une contrainte unique sur une combinaison d'éléments ou d'attributs dans le schéma XML. L’exemple suivant montre comment spécifier qu’une combinaison de valeurs **CustomerID** et **CompanyName** doit être unique pour tous les **clients** d’une instance, en ajoutant un autre élément **XS : Field** dans le schéma.  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 Il s’agit de la contrainte créée dans le **jeu de données**résultant.  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Voir aussi

- [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Génération de relations de DataSet à partir du schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
