---
title: Attributs qui contrôlent la sérialisation XML
description: Cet article contient des attributs que vous pouvez appliquer aux classes et aux membres de classe pour contrôler la façon dont le XmlSerializer sérialise ou désérialise une instance d’une classe.
ms.date: 03/30/2017
helpviewer_keywords:
- classes, serializing
- XmlSerializer class, serializing
- XML serialization, attributes
- attributes [.NET], XML serialization
- serialization, attributes
- XML Schema, serializing
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
ms.openlocfilehash: 032843728c74799d7ee78257b21243b31cb4f99c
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281984"
---
# <a name="attributes-that-control-xml-serialization"></a>Attributs qui contrôlent la sérialisation XML
Vous pouvez appliquer les attributs du tableau suivant à des classes et des membres de classe pour contrôler la manière dont <xref:System.Xml.Serialization.XmlSerializer> sérialise ou désérialise une instance de la classe. Pour comprendre comment ces attributs contrôlent la sérialisation XML, consultez [Contrôle de la sérialisation XML à l’aide d’attributs](controlling-xml-serialization-using-attributes.md).  
  
 Ces attributs peuvent également être utilisés pour contrôler les messages SOAP de style littéral générés par un service Web XML. Pour plus d’informations sur l’application de ces attributs à une méthode de services web XML, consultez [Sérialisation XML avec les services Web XML](xml-serialization-with-xml-web-services.md).  
  
 Pour plus d’informations sur les attributs, consultez [Attributs](../attributes/index.md).  
  
|Attribut|S’applique à|Spécifie|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.XmlAnyAttributeAttribute>|Champ public, propriété, paramètre ou valeur de retour qui retourne un tableau d'objets <xref:System.Xml.XmlAttribute>.|Lors de la désérialisation, le tableau est rempli avec les objets <xref:System.Xml.XmlAttribute> qui représentent tous les attributs XML inconnus du schéma.|  
|<xref:System.Xml.Serialization.XmlAnyElementAttribute>|Champ public, propriété, paramètre ou valeur de retour qui retourne un tableau d'objets <xref:System.Xml.XmlElement>.|Lors de la désérialisation, le tableau est rempli avec les objets <xref:System.Xml.XmlElement> qui représentent tous les éléments XML inconnus du schéma.|  
|<xref:System.Xml.Serialization.XmlArrayAttribute>|Champ public, propriété, paramètre ou valeur de retour qui retourne un tableau d'objets complexes.|Les membres du tableau sont générés en tant que membres d'un tableau XML.|  
|<xref:System.Xml.Serialization.XmlArrayItemAttribute>|Champ public, propriété, paramètre ou valeur de retour qui retourne un tableau d'objets complexes.|Types dérivés qui peuvent être insérés dans un tableau. S'applique habituellement avec <xref:System.Xml.Serialization.XmlArrayAttribute>.|  
|<xref:System.Xml.Serialization.XmlAttributeAttribute>|Champ public, propriété, paramètre ou valeur de retour.|Le membre est sérialisé en tant qu'attribut XML.|  
|<xref:System.Xml.Serialization.XmlChoiceIdentifierAttribute>|Champ public, propriété, paramètre ou valeur de retour.|L'ambiguïté du membre peut être levée à l'aide d'une énumération.|  
|<xref:System.Xml.Serialization.XmlElementAttribute>|Champ public, propriété, paramètre ou valeur de retour.|Le champ ou la propriété est sérialisé en tant qu'élément XML.|  
|<xref:System.Xml.Serialization.XmlEnumAttribute>|Champ public qui est un identificateur d'énumération.|Nom d'élément d'un membre d'énumération.|  
|<xref:System.Xml.Serialization.XmlIgnoreAttribute>|Champs et propriétés publics.|La propriété ou le champ doit être ignoré lorsque la classe conteneur est sérialisée.|  
|<xref:System.Xml.Serialization.XmlIncludeAttribute>|Déclarations de classe dérivée publiques et valeurs de retour de méthodes publiques pour les documents WSDL (Web Services Description Language).|La classe doit être incluse lors de la génération de schémas (afin d'être reconnue en cas de sérialisation).|  
|<xref:System.Xml.Serialization.XmlRootAttribute>|Déclarations de classe publiques.|Contrôle la sérialisation XML de l'attribut cible en tant qu'élément racine XML. Utilisez l'attribut pour préciser l'espace de noms et le nom d'élément.|  
|<xref:System.Xml.Serialization.XmlTextAttribute>|Champs et propriétés publics.|La propriété ou le champ doit être sérialisé en tant que texte XML.|  
|<xref:System.Xml.Serialization.XmlTypeAttribute>|Déclarations de classe publiques.|Nom et espace de noms du type XML.|  
  
 En plus de ces attributs, qui se trouvent tous dans l'espace de noms <xref:System.Xml.Serialization>, vous pouvez également appliquer l'attribut <xref:System.ComponentModel.DefaultValueAttribute> à un champ. **DefaultValueAttribute** définit la valeur qui sera assignée automatiquement au membre si aucune valeur n’est spécifiée.  
  
 Pour contrôler la sérialisation XML encodée selon le protocole SOAP, consultez [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](attributes-that-control-encoded-soap-serialization.md).  
  
## <a name="see-also"></a>Voir aussi

- [Sérialisation XML et SOAP](xml-and-soap-serialization.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Contrôle de la sérialisation XML à l'aide d'attributs](controlling-xml-serialization-using-attributes.md)
- [Comment : spécifier un nom d'élément différent pour un flux XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [Guide pratique pour sérialiser un objet](how-to-serialize-an-object.md)
- [Comment : désérialiser un objet](how-to-deserialize-an-object.md)
