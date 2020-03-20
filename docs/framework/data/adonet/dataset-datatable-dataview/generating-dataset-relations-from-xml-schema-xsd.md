---
title: Génération de relations de DataSet à partir du schéma XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151128"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Génération de relations de DataSet à partir du schéma XML (XSD)
Dans un objet <xref:System.Data.DataSet>, vous créez une association entre deux ou plusieurs colonnes en établissant une relation parent-enfant. Il existe trois façons de représenter une relation **DataSet** dans un schéma de définition XML Schema (XSD) :  
  
- spécifier des types complexes imbriqués ;  
  
- Utilisez l’annotation **msdata:Relation.**  
  
- Spécifier un **xs:keyref** sans la **msdata:ConstraintOnly** annotation.  
  
## <a name="nested-complex-types"></a>Types complexes imbriqués  
 Les définitions de types complexes imbriqués dans un schéma indiquent les relations parent-enfant des éléments. Le fragment XML Schema suivant montre que **OrderDetail** est un élément enfant de l’élément **De l’Ordre.**  
  
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
  
 Le processus de cartographie XML Schema crée des tables dans le **DataSet** qui correspondent aux types complexes imbriqués dans le schéma. Il crée également des colonnes**-** supplémentaires qui sont utilisées comme colonnes d’enfant parent pour les tables générées. Notez que**-** ces colonnes d’enfants parents spécifient les relations, ce qui n’est pas la même chose que de spécifier les contraintes clés principales primaires/étrangères.  
  
## <a name="msdatarelationship-annotation"></a>Annotation msdata:Relationship  
 L’annotation **msdata:Relation** vous permet de spécifier explicitement les relations parent-enfant entre les éléments du schéma qui ne sont pas imbriqués. L’exemple suivant montre la structure de l’élément **relationnel.**  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 Les attributs de l’annotation **msdata:Relation** identifient les éléments impliqués dans la relation parent-enfant, ainsi que les éléments **parentkey** et **childkey** et les attributs impliqués dans la relation. Le processus de cartographie utilise ces informations pour générer des tableaux dans le **DataSet** et pour créer la principale relation clé clé/étrangère entre ces tables.  
  
 Par exemple, le fragment de schéma suivant spécifie les éléments **de l’Ordre** et **de l’Ordre à** la même échelle (non imbriqués). Le schéma spécifie une **msdata:Relationship** annotation, qui spécifie la relation parent-enfant entre ces deux éléments. Dans ce cas, une relation explicite doit être spécifiée à l’aide de **l’annotation msdata:Relation.**  
  
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
  
 Le processus de cartographie utilise **l’élément relationnel** pour créer une relation parent-enfant entre la colonne **OrderNumber** dans le tableau **de l’Ordre** et la colonne **OrderNo** dans le tableau **OrderDetail** dans le **DataSet**. Il ne spécifie que la relation ; il ne spécifie pas automatiquement de contraintes sur les valeurs de ces colonnes comme le font des contraintes de clé primaire/clé étrangère dans des bases de données relationnelles.  
  
### <a name="in-this-section"></a>Dans cette section  
 [Mapper les relations implicites entre éléments de schéma imbriqués](map-implicit-relations-between-nested-schema-elements.md)  
 Décrit les contraintes et les relations qui sont implicitement créées dans un **ensemble de données** lorsque des éléments imbriqués sont rencontrés dans XML Schema.  
  
 [Mapper les relations spécifiées pour les éléments imbriqués](map-relations-specified-for-nested-elements.md)  
 Décrit comment définir explicitement les relations dans un **DataSet** pour les éléments imbriqués dans XML Schema.  
  
 [Spécifier les relations entre éléments sans imbrication](specify-relations-between-elements-with-no-nesting.md)  
 Décrit comment créer des relations dans un **ensemble de données** entre les éléments XML Schema qui ne sont pas imbriqués.  
  
### <a name="related-sections"></a>Sections connexes  
 [Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Décrit la structure relationnelle, ou schéma, d’un **DataSet** qui est créé à partir de XML Schema langage de définition (XSD) schéma.  
  
 [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments XML Schema utilisés pour créer des contraintes clés uniques et étrangères dans un **DataSet**.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
