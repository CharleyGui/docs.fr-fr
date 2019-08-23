---
title: Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 98c43b6af2913b9737085d2d983b37c6da4c1724
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934462"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)
Cette section propose une vue d'ensemble de la façon dont le schéma relationnel d'un objet `DataSet` est construit à partir d'un document de schéma en langage XSD (XML Schema Definition). En général, pour chaque `complexType` élément enfant d’un élément de schéma, une table est générée dans `DataSet`le. La structure de cette table est déterminée par la définition du type complexe. Les tables sont créées dans `DataSet` le pour les éléments de niveau supérieur dans le schéma. Toutefois, une table est créée uniquement pour un élément de niveau `complexType` supérieur lorsque l' `complexType` élément est imbriqué à l’intérieur `complexType` d’un autre `complexType` élément, auquel cas l’élément imbriqué est mappé à un `DataTable` dans le `DataSet`.  
  
 Pour plus d’informations sur le langage XSD, consultez le World Wide Web Consortium ( [W3C) XML Schema Part 0: Première recommandation](https://www.w3.org/TR/xmlschema-0/), le [schéma XML, partie 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/)et le [schéma XML, partie 2: Recommandation](https://www.w3.org/TR/xmlschema-2/)de type de données.  
  
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
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Le type de données de chaque colonne de la table est dérivé du type de schéma XML de l'élément ou de l'attribut spécifié correspondant.  
  
> [!NOTE]
> Si l’élément `customers` est d’un type de données de schéma XML simple, tel qu’un **entier**, aucune table n’est générée. Des tables sont créées uniquement pour les éléments de niveau supérieur de type complexe.  
  
 Dans le schéma XML suivant, l’élément de **schéma** a deux enfants d' `InStateCustomers` élément `OutOfStateCustomers`, et.  
  
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
  
 Les éléments enfants `InStateCustomers` et `OutOfStateCustomers` sont tous deux des éléments de type complexe (`customerType`). Par conséquent, le processus de mappage génère les deux tables identiques suivantes `DataSet`dans le.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML utilisés pour créer des contraintes de clé étrangère et `DataSet`uniques dans un.  
  
 [Génération de relations de DataSet à partir du schéma XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Décrit les éléments de schéma XML utilisés pour créer des relations entre des colonnes `DataSet`de table dans un.  
  
 [Contraintes et relations du schéma XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 Décrit comment les relations sont créées implicitement lors de l’utilisation d’éléments de schéma XML `DataSet`pour créer des contraintes dans un.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Décrit comment charger et conserver la structure et les données relationnelles dans une `DataSet` sous forme de données XML.  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
