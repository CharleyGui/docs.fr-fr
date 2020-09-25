---
title: Génération de relations de DataSet à partir du schéma XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 2673280ebb94dcc10c130f3969f3e3250d3706a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198585"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Génération de relations de DataSet à partir du schéma XML (XSD)

Dans un objet <xref:System.Data.DataSet>, vous créez une association entre deux ou plusieurs colonnes en établissant une relation parent-enfant. Il existe trois façons de représenter une relation de **DataSet** dans un schéma en langage XSD (XML Schema Definition) :  
  
- spécifier des types complexes imbriqués ;  
  
- Utilisez l’annotation **msdata : Relationship** .  
  
- Spécifiez un **XS : keyref** sans l’annotation **msdata : ConstraintOnly** .  
  
## <a name="nested-complex-types"></a>Types complexes imbriqués  

 Les définitions de types complexes imbriqués dans un schéma indiquent les relations parent-enfant des éléments. Le fragment de schéma XML suivant montre que **OrderDetail** est un élément enfant de l’élément **Order** .  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>
       <xs:element name="OrderDetail" />  
           <xs:complexType>
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Le processus de mappage de schéma XML crée dans le **DataSet** des tables qui correspondent aux types complexes imbriqués dans le schéma. Il crée également des colonnes supplémentaires qui sont utilisées comme **-** colonnes enfants parentes pour les tables générées. Notez que ces **-** colonnes enfants parentes spécifient des relations, ce qui n’est pas le même que la spécification de contraintes de clé primaire/clé étrangère.  
  
## <a name="msdatarelationship-annotation"></a>Annotation msdata:Relationship  

 L’annotation **msdata : Relationship** vous permet de spécifier explicitement les relations parent-enfant entre les éléments du schéma qui ne sont pas imbriqués. L’exemple suivant illustre la structure de l’élément **Relationship** .  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 Les attributs de l’annotation **msdata : Relationship** identifient les éléments impliqués dans la relation parent-enfant, ainsi que les éléments et attributs **ParentKey** et **childkey** impliqués dans la relation. Le processus de mappage utilise ces informations pour générer des tables dans le **jeu de données** et pour créer la relation clé primaire/clé étrangère entre ces tables.  
  
 Par exemple, le fragment de schéma suivant spécifie les éléments **Order** et **OrderDetail** au même niveau (non imbriqué). Le schéma spécifie une annotation **msdata : Relationship** , qui spécifie la relation parent-enfant entre ces deux éléments. Dans ce cas, une relation explicite doit être spécifiée à l’aide de l’annotation **msdata : Relationship** .  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 Le processus de mappage utilise l’élément **Relationship** pour créer une relation parent-enfant entre la colonne **OrderNumber** de la table **Order** et la colonne **OrderNo** de la table **OrderDetail** du **DataSet**. Il ne spécifie que la relation ; il ne spécifie pas automatiquement de contraintes sur les valeurs de ces colonnes comme le font des contraintes de clé primaire/clé étrangère dans des bases de données relationnelles.  
  
### <a name="in-this-section"></a>Dans cette section  

 [Mapper les relations implicites entre éléments de schéma imbriqués](map-implicit-relations-between-nested-schema-elements.md)  
 Décrit les contraintes et les relations qui sont créées implicitement dans un **DataSet** lorsque des éléments imbriqués sont rencontrés dans le schéma XML.  
  
 [Mapper les relations spécifiées pour les éléments imbriqués](map-relations-specified-for-nested-elements.md)  
 Décrit comment définir explicitement des relations dans un **DataSet** pour les éléments imbriqués dans le schéma XML.  
  
 [Spécifier les relations entre éléments sans imbrication](specify-relations-between-elements-with-no-nesting.md)  
 Décrit comment créer des relations dans un **DataSet** entre des éléments de schéma XML qui ne sont pas imbriqués.  
  
### <a name="related-sections"></a>Sections connexes  

 [Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Décrit la structure relationnelle, ou schéma, d’un **DataSet** créé à partir du schéma en langage XSD (XML Schema Definition).  
  
 [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML utilisés pour créer des contraintes de clé étrangère et uniques dans un **DataSet**.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
