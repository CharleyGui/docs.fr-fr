---
title: Prise en charge du type dans les classes System.Xml
ms.date: 03/30/2017
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: 6fe55c64bc9bd17d5416eebf77060f2be27b81bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675657"
---
# <a name="type-support-in-the-systemxml-classes"></a>Prise en charge du type dans les classes System.Xml

Dans .NET Framework version 2.0, les classes XML noyau ont été améliorées pour inclure des fonctions de prise en charge du type. Les classes <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.XPath.XPathNavigator> comprennent des fonctionnalités de prise en charge du type, notamment la possibilité de conversion entre des types de schémas XML et des types CLR (Common Language Runtime).  
  
 Dans .NET Framework version 2.0, les classes <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.XPath.XPathNavigator> ont été améliorées pour inclure des fonctionnalités de prise en charge du type.  
  
- Les classes <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator> contiennent chacune une propriété **SchemaInfo** qui retourne les informations de schéma à un nœud.  
  
- Les méthodes **ReadContentAs** et **ReadElementContentAs** de la classe <xref:System.Xml.XmlReader> lisent une valeur texte et la convertissent en valeur CLR en un seul appel de méthode.  
  
- La méthode <xref:System.Xml.XmlWriter.WriteValue%2A> de la classe <xref:System.Xml.XmlWriter> convertit un type CLR en type de schéma XML lors de l'écriture de XML.  
  
- Les propriétés **ValueAs** et <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> retournent une valeur de nœud et la convertissent en valeur CLR en un seul appel de méthode.  
  
> [!NOTE]
> Dans .NET Framework version 1.0, la classe <xref:System.Xml.XmlConvert> était nécessaire pour la conversion entre les types CLR et de schéma XML.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Mappage entre types de données XML et types CLR](mapping-xml-data-types-to-clr-types.md)  
 Décrit les mappages par défaut des types de données XML en types CLR.  
  
 [Remarques pour l'implémentation de la prise en charge du type XML](xml-type-support-implementation-notes.md)  
 Explique certains détails de l'implémentation de la prise en charge du type.  
  
 [Conversion des types de données XML](conversion-of-xml-data-types.md)  
 Décrit l'utilisation de la classe <xref:System.Xml.XmlConvert> pour la conversion entre des types CLR et de schéma XML.  
  
## <a name="related-sections"></a>Sections connexes  

 [Accès à des données XML fortement typées à l'aide de XPathNavigator](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
