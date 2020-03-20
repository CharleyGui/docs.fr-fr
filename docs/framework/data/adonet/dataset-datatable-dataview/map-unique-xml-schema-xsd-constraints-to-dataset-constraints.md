---
title: Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150842"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet
Dans un schéma de définition XML Schema (XSD), l’élément **unique** spécifie la contrainte d’unicité sur un élément ou un attribut. Dans le processus de conversion d'un schéma XML en schéma relationnel, la contrainte unique spécifiée sur un élément ou un attribut du schéma XML est mappée à une contrainte unique dans l'objet <xref:System.Data.DataTable> de l'objet <xref:System.Data.DataSet> correspondant qui est généré.  
  
 Le tableau suivant décrit les attributs **msdata** que vous pouvez spécifier dans **l’élément unique.**  
  
|Nom de l’attribut|Description|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte. Dans le cas contraire, l’attribut de **nom** fournit la valeur du nom de contrainte.|  
|**msdata:PrimaryKey**|Si `PrimaryKey="true"` elle est présente dans **l’élément unique,** une contrainte unique est créée avec la propriété **IsPrimaryKey** définie pour **vrai**.|  
  
 L’exemple suivant montre un schéma XML qui utilise **l’élément unique** pour spécifier une contrainte d’unicité.  
  
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
  
 **L’élément unique** dans le schéma précise que pour tous les éléments **clients** dans une instance de document, la valeur de **l’élément** enfant CustomerID doit être unique. Lors de la construction du **DataSet**, le processus de cartographie lit ce schéma et génère le tableau suivant :  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Le processus de cartographie crée également une contrainte unique sur la colonne **CustomerID,** comme le montre le **DataSet**suivant . (Par souci de simplicité, seules les propriétés pertinentes sont représentées.)  
  
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
  
 Dans le **DataSet** qui est généré, la propriété **IsPrimaryKey** est définie à **False** pour la contrainte unique. La propriété **unique** sur la colonne indique que les valeurs de colonne **CustomerID** doivent être uniques (mais elles peuvent être une référence nulle, comme le précise la propriété **AllowDBNull** de la colonne).  
  
 Si vous modifiez le schéma et définissez la valeur d’attribut **msdata:PrimaryKey** optionnelle à **True**, la contrainte unique est créée sur la table. La propriété de colonne **AllowDBNull** est réglée à **False**, et la propriété **IsPrimaryKey** de la contrainte définie à **True**, faisant ainsi de la colonne **CustomerID** une colonne principale.  
  
 Vous pouvez spécifier une contrainte unique sur une combinaison d'éléments ou d'attributs dans le schéma XML. L’exemple suivant montre comment spécifier qu’une combinaison de valeurs **CustomerID** et **CompanyName** doit être unique pour tous les **clients** dans n’importe quel cas, en ajoutant un autre élément **xs:field** dans le schéma.  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 C’est la contrainte qui est créée dans le **DataSet**résultant .  
  
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
