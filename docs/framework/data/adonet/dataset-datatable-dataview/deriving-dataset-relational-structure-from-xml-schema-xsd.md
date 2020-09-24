---
title: Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 878e39af575328fb0abba096c327d36203a52231
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164803"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)

Cette section propose une vue d'ensemble de la façon dont le schéma relationnel d'un objet `DataSet` est construit à partir d'un document de schéma en langage XSD (XML Schema Definition). En général, pour chaque `complexType` élément enfant d’un élément de schéma, une table est générée dans le `DataSet` . La structure de cette table est déterminée par la définition du type complexe. Les tables sont créées dans le `DataSet` pour les éléments de niveau supérieur dans le schéma. Toutefois, une table est créée uniquement pour un élément de niveau supérieur `complexType` lorsque l' `complexType` élément est imbriqué à l’intérieur d’un autre `complexType` élément, auquel cas l' `complexType` élément imbriqué est mappé à un `DataTable` dans le `DataSet` .  
  
 Pour plus d’informations sur le langage XSD, consultez World Wide Web Consortium la recommandation XML Schema [part 0 : Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), [XML Schema Part 1 : structures Recommendation](https://www.w3.org/TR/xmlschema-1/)(en anglais) et [XML Schema Part 2 : Datatypes recommendation](https://www.w3.org/TR/xmlschema-2/)(en anglais).  
  
 L’exemple suivant illustre un schéma XML où `customers` est l’élément enfant de l' `MyDataSet` élément, qui est un élément de **DataSet** .  
  
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
> Si l’élément `customers` est d’un type de données de schéma XML simple, tel qu’un **entier**, aucune table n’est générée. Des tables sont créées uniquement pour les éléments de niveau supérieur de type complexe.  
  
 Dans le schéma XML suivant, l’élément de **schéma** a deux enfants d’élément, `InStateCustomers` et `OutOfStateCustomers` .  
  
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
  
 Les éléments enfants `InStateCustomers` et `OutOfStateCustomers` sont tous deux des éléments de type complexe (`customerType`). Par conséquent, le processus de mappage génère les deux tables identiques suivantes dans le `DataSet` .  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Dans cette section  

 [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML utilisés pour créer des contraintes de clé étrangère et uniques dans un `DataSet` .  
  
 [Génération de relations de DataSet à partir du schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Décrit les éléments de schéma XML utilisés pour créer des relations entre des colonnes de table dans un `DataSet` .  
  
 [Contraintes et relations du schéma XML](xml-schema-constraints-and-relationships.md)  
 Décrit comment les relations sont créées implicitement lors de l’utilisation d’éléments de schéma XML pour créer des contraintes dans un `DataSet` .  
  
## <a name="related-sections"></a>Sections connexes  

 [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)  
 Décrit comment charger et conserver la structure et les données relationnelles dans une `DataSet` sous forme de données XML.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
