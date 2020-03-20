---
title: Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d32b5cb86bc5a138f9a5f438629d8e231be4ba94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151167"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)
Cette section propose une vue d'ensemble de la façon dont le schéma relationnel d'un objet `DataSet` est construit à partir d'un document de schéma en langage XSD (XML Schema Definition). En général, `complexType` pour chaque élément enfant d’un élément `DataSet`schéma, un tableau est généré dans le . La structure de cette table est déterminée par la définition du type complexe. Les tables sont `DataSet` créées dans le pour les éléments de haut niveau dans le schéma. Cependant, une table n’est créée `complexType` que `complexType` pour un élément `complexType` de haut niveau lorsque `complexType` l’élément est `DataTable` imbriqué à l’intérieur d’un autre élément, auquel cas l’élément imbriqué est cartographié à un intérieur de la `DataSet`.  
  
 Pour plus d’informations sur le XSD, voir le World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), le [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), et le [XML Schema Partie 2: Datatypes Recommandation](https://www.w3.org/TR/xmlschema-2/).  
  
 L’exemple suivant montre un schéma `customers` XML où `MyDataSet` est l’élément enfant de l’élément, qui est un élément **DataSet.**  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 Dans l'exemple précédent, l'élément `customers` est un élément de type complexe. Par conséquent, la définition du type complexe est analysée et le processus de mappage crée la table suivante.  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Le type de données de chaque colonne de la table est dérivé du type de schéma XML de l'élément ou de l'attribut spécifié correspondant.  
  
> [!NOTE]
> Si l’élément `customers` est d’un simple type de données XML Schema comme **l’intégrant,** aucun tableau n’est généré. Des tables sont créées uniquement pour les éléments de niveau supérieur de type complexe.  
  
 Dans le schéma XML suivant, l’élément **Schema** a deux enfants élément, `InStateCustomers` et `OutOfStateCustomers`.  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 Les éléments enfants `InStateCustomers` et `OutOfStateCustomers` sont tous deux des éléments de type complexe (`customerType`). Par conséquent, le processus de cartographie génère `DataSet`les deux tableaux identiques suivants dans le .  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments XML Schema utilisés pour créer `DataSet`des contraintes clés uniques et étrangères dans un .  
  
 [Génération de relations de DataSet à partir du schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Décrit les éléments XML Schema utilisés pour créer `DataSet`des relations entre les colonnes de table dans un .  
  
 [Contraintes et relations du schéma XML](xml-schema-constraints-and-relationships.md)  
 Décrit comment les relations sont créées implicitement lors de l’utilisation des éléments XML Schema pour créer des contraintes dans un `DataSet`.  
  
## <a name="related-sections"></a>Sections connexes  
 [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)  
 Décrit comment charger et persister la structure `DataSet` relationnelle et les données dans un comme données XML.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
