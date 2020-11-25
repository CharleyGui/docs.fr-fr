---
title: Inférence de schémas à partir de documents XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
ms.openlocfilehash: 4540e1706cbd3dad9490f100d7e8fa58e80a9206
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733436"
---
# <a name="inferring-schemas-from-xml-documents"></a>Inférence de schémas à partir de documents XML

Cette rubrique décrit comment utiliser la classe <xref:System.Xml.Schema.XmlSchemaInference> pour déduire un schéma en langage XSD (XML Schema Definition) à partir de la structure d'un document XML.  
  
## <a name="the-schema-inference-process"></a>Processus d'inférence du schéma  

 La classe <xref:System.Xml.Schema.XmlSchemaInference> de l'espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType> est utilisée pour générer un ou plusieurs schémas en langage XSD à partir de la structure d'un document XML. Les schémas générés peuvent être utilisés pour valider le document XML original.  
  
 Lorsqu'un document XML est traité par la classe <xref:System.Xml.Schema.XmlSchemaInference>, la classe <xref:System.Xml.Schema.XmlSchemaInference> fait des hypothèses sur les composants du schéma qui décrivent les éléments et les attributs du document XML. La classe <xref:System.Xml.Schema.XmlSchemaInference> déduit également des composants de schéma de façon contrainte en déduisant le type le plus restrictif d'un élément ou d'un attribut particulier. À mesure que des informations supplémentaires sur le document XML sont collectées, ces contraintes sont assouplies par l'inférence de types moins restrictifs. Le type le moins restrictif qui puisse être déduit est `xs:string`.  
  
 Prenez, par exemple, l'élément suivant d'un document XML.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A" />
```  
  
 Dans l'exemple ci-avant, quand l'attribut `attribute1` est rencontré avec une valeur `6` par le processus <xref:System.Xml.Schema.XmlSchemaInference>, il est supposé être du type `xs:unsignedByte`. Lorsque le second élément `parent` est rencontré par le processus <xref:System.Xml.Schema.XmlSchemaInference>, la contrainte est assouplie en modifiant le type en `xs:string` parce que la valeur de l'attribut `attribute1` est à présent `A`. De même, l'attribut `minOccurs` pour tous les éléments `child` déduits dans le schéma sont assouplis en `minOccurs="0"` parce que le second élément parent n'a pas d'élément enfant.  
  
## <a name="inferring-schemas-from-xml-documents"></a>Inférence de schémas à partir de documents XML  

 La classe <xref:System.Xml.Schema.XmlSchemaInference> utilise deux méthodes <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> surchargées pour déduire un schéma à partir d'un document XML.  
  
 La première méthode <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> est utilisée pour créer un schéma basé sur un document XML. La seconde méthode <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> est utilisée pour déduire un schéma décrivant plusieurs documents XML. Par exemple, vous pouvez transmettre plusieurs documents XML à la méthode <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> l'un après l'autre afin de produire un schéma décrivant l'ensemble des documents XML.  
  
 La première méthode <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> déduit un schéma à partir d'un document XML contenu dans un objet <xref:System.Xml.XmlReader> et retourne un objet <xref:System.Xml.Schema.XmlSchemaSet> contenant le schéma déduit. La seconde méthode <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> recherche un objet <xref:System.Xml.Schema.XmlSchemaSet> pour un schéma ayant le même nom d'espaces cible que le document XML contenu dans l'objet <xref:System.Xml.XmlReader>, affine le schéma existant et retourne un objet <xref:System.Xml.Schema.XmlSchemaSet> contenant le schéma déduit.  
  
 Les modifications apportées au schéma affiné sont basées sur la nouvelle structure trouvée dans le document XML. Par exemple, lors du parcours d'un document XML, des hypothèses sont faites concernant les types de données rencontrés et le schéma est créé sur la base de ces hypothèses. Toutefois, si des données sont rencontrées lors d'un second cycle d'inférence, qui diffèrent de l'hypothèse initiale, le schéma est affiné. L'exemple suivant illustre le processus d'affinement.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 L'exemple prend le fichier `item1.xml` comme première entrée.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 L'exemple prend ensuite le fichier `item2.xml` comme seconde entrée :  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 Si l'attribut `productID` est détecté dans le premier document XML, la valeur `123456789` est supposée être un type `xs:unsignedInt`. Toutefois, lors de la lecture du second document XML, si la valeur de `A53-246` est détectée, l'hypothèse du type `xs:unsignedInt` n'est plus valable. Le schéma est affiné et le type de `productID` est changé en `xs:string`. En outre, l'attribut `minOccurs` pour l'élément `supplierID` a la valeur `0` parce que le second document XML ne contient pas d'élément `supplierID`.  
  
 Voici le schéma déduit à partir du premier document XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 Voici le schéma déduit à partir du premier document XML, affiné par le second document XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Schémas inline  

 Si un schéma en langage XSD (XML Schema Definition) est détecté durant le processus <xref:System.Xml.Schema.XmlSchemaInference>, une exception <xref:System.Xml.Schema.XmlSchemaInferenceException> est levée. Par exemple, le schéma inline suivant lève une exception <xref:System.Xml.Schema.XmlSchemaInferenceException> :  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Schémas qui ne peuvent pas être affinés  

 Il y a trois constructions de schéma XML conformes aux spécifications du W3C que le processus <xref:System.Xml.Schema.XmlSchemaInference> de schéma en langage XSD ne peut pas gérer s'il reçoit un type particulier à affiner, et qui entraînent la levée d'une exception. Il peut s'agir, par exemple, d'un type complexe dont le constructeur de niveau supérieur n'est pas une séquence. Dans le Modèle Objet du schéma (SOM), cela correspond à un objet <xref:System.Xml.Schema.XmlSchemaComplexType> dont la propriété <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> n'est pas une instance de l'objet <xref:System.Xml.Schema.XmlSchemaSequence>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Schema.XmlSchemaInference>
- [Modèle Objet du schéma (SOM) XML](xml-schema-object-model-som.md)
- [Inférence d'un schéma XML](inferring-an-xml-schema.md)
- [Règles pour l'inférence de types et de structure de nœud de schéma](rules-for-inferring-schema-node-types-and-structure.md)
- [Règles relatives à l'inférence de types simples](rules-for-inferring-simple-types.md)
