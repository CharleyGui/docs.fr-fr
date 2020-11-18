---
title: Utilisation de schémas XML
ms.date: 03/30/2017
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
ms.openlocfilehash: adad77eaefd85abf111a25180b7289af997a7222
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818412"
---
# <a name="working-with-xml-schemas"></a>Utilisation de schémas XML
Pour définir la structure d'un document XML, les relations entre ses éléments, les types de données et les limites de contenu, vous devez utiliser une définition de type de document (DTD) ou un schéma de langage XSD (XML Schema Definition). Bien qu'un document XML soit considéré comme correctement construit s'il répond à toutes les exigences syntaxiques définies par la recommandation du W3C (World Wide Web Consortium) sur le langage XML (Extensible Markup Language) 1.0, il est considéré comme non valide à moins d'être correctement construit et conforme aux limites définies par sa DTD ou son schéma. Par conséquent, même si tous les documents XML valides sont construits correctement, tous les documents XML construits correctement ne sont pas valides.  
  
 Pour plus d'informations sur XML, consultez [W3C XML 1.0 Recommendation](https://www.w3.org/TR/REC-xml/) (en anglais). Pour plus d'informations sur le schéma XML, consultez les recommandations intitulées [W3C XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/) et [W3C XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) (en anglais).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modèle Objet du schéma (SOM) XML](xml-schema-object-model-som.md)  
 Présente le modèle Objet du schéma (SOM) dans l'espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType>, qui fournit un ensemble de classes permettant de lire un schéma de langage XSD (XML Schema Definition) à partir d'un fichier ou de créer par programmation un cache de schéma en mémoire.  
  
 [XmlSchemaSet pour la compilation de schémas](xmlschemaset-for-schema-compilation.md)  
 Présente la classe <xref:System.Xml.Schema.XmlSchemaSet>, qui est un cache où les schémas XSD peuvent être stockés et validés.  
  
 [Validation XmlSchemaValidator de type push](xmlschemavalidator-push-based-validation.md)  
 Présente la classe <xref:System.Xml.Schema.XmlSchemaValidator>, qui fournit un mécanisme efficace et performant de validation des données XML par rapport aux schémas XSD selon le modèle push.  
  
 [Inférence d'un schéma XML](inferring-an-xml-schema.md)  
 Décrit comment utiliser la classe <xref:System.Xml.Schema.XmlSchemaInference> pour inférer un schéma XSD à partir de la structure d'un document XML.  
  
## <a name="reference"></a>Référence  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>Sections connexes  
 [Validation d'un document XML dans le DOM](validating-an-xml-document-in-the-dom.md)  
 Explique comment valider le XML dans le DOM (Document Object Model). Vous pouvez valider le XML lors de son chargement dans le DOM ou valider un document XML précédemment non validé dans le DOM.  
  
 [Validation de schéma à l'aide de XPathNavigator](schema-validation-using-xpathnavigator.md)  
 Explique comment valider le XML en cours de navigation et de modification à l'aide de la classe <xref:System.Xml.XPath.XPathNavigator>.
