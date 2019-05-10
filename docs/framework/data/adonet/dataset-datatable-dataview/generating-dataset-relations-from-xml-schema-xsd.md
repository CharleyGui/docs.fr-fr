---
title: Génération de relations de DataSet à partir du schéma XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 2cf6d2ed949a3efa39c0f1c049bc03e7a5b0eb0b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621081"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Génération de relations de DataSet à partir du schéma XML (XSD)
Dans un objet <xref:System.Data.DataSet>, vous créez une association entre deux ou plusieurs colonnes en établissant une relation parent-enfant. Il existe trois façons pour représenter un **DataSet** relation au sein d’un schéma XML Schema definition language (XSD) :  
  
- spécifier des types complexes imbriqués ;  
  
- Utilisez le **msdata : Relationship** annotation.  
  
- Spécifiez un **xs : keyref** sans le **msdata : ConstraintOnly** annotation.  
  
## <a name="nested-complex-types"></a>Types complexes imbriqués  
 Les définitions de types complexes imbriqués dans un schéma indiquent les relations parent-enfant des éléments. Le fragment de schéma XML suivant montre que **OrderDetail** est un élément enfant de le **ordre** élément.  
  
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
  
 Le processus de mappage de schéma XML crée les tables dans le **DataSet** qui correspondent aux types complexes imbriqués dans le schéma. Il crée également des colonnes supplémentaires qui sont utilisés en tant que parent**-** colonnes enfants pour les tables générées. Notez que ces parent**-** colonnes enfant spécifient des relations, qui n’est pas identique à des contraintes de clé étrangère/clé primaire.  
  
## <a name="msdatarelationship-annotation"></a>Annotation msdata:Relationship  
 Le **msdata : Relationship** annotation vous permet de spécifier explicitement les relations parent-enfant entre les éléments qui ne sont pas imbriqués dans le schéma. L’exemple suivant montre la structure de la **relation** élément.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Les attributs de la **msdata : Relationship** annotation identifient les éléments impliqués dans la relation parent-enfant en tant que le **parentkey** et **childkey** éléments et attributs impliqués dans la relation. Le processus de mappage utilise ces informations pour générer des tables dans le **DataSet** et pour créer la relation clé primaire/étrangère clé entre ces tables.  
  
 Par exemple, le fragment de schéma suivant spécifie **ordre** et **OrderDetail** éléments au même niveau (non imbriqué). Le schéma spécifie un **msdata : Relationship** annotation, qui spécifie la relation parent-enfant entre ces deux éléments. Dans ce cas, une relation explicite doit être spécifiée à l’aide de la **msdata : Relationship** annotation.  
  
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
  
 Le processus de mappage utilise le **relation** élément pour créer une relation parent-enfant entre les **OrderNumber** colonne dans le **ordre** table et la **OrderNo** colonne dans le **OrderDetail** table dans le **DataSet**. Il ne spécifie que la relation ; il ne spécifie pas automatiquement de contraintes sur les valeurs de ces colonnes comme le font des contraintes de clé primaire/clé étrangère dans des bases de données relationnelles.  
  
### <a name="in-this-section"></a>Dans cette section  
 [Mapper les relations implicites entre éléments de schéma imbriqués](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 Décrit les contraintes et relations implicitement créées dans un **DataSet** lorsque surviennent des éléments imbriqués dans le schéma XML.  
  
 [Mapper les relations spécifiées pour les éléments imbriqués](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 Décrit comment définir explicitement des relations un **DataSet** pour les éléments imbriqués dans le schéma XML.  
  
 [Spécifier les relations entre éléments sans imbrication](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 Décrit comment créer des relations dans un **DataSet** entre les éléments de schéma XML qui ne sont pas imbriqués.  
  
### <a name="related-sections"></a>Rubriques connexes  
 [Dérivation de la structure relationnelle des DataSets à partir du schéma XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Décrit la structure relationnelle, ou schéma, d’un **DataSet** qui est créé à partir de schéma XML Schema definition language (XSD).  
  
 [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML utilisés pour créer des contraintes de clés étrangères et uniques dans un **DataSet**.  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
