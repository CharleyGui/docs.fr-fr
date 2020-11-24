---
title: Traitement des données XML à l'aide du modèle de données XPath
ms.date: 03/30/2017
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
ms.openlocfilehash: 840fb40cc650d8f65af533d4102f18132bce3f53
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686954"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a>Traitement des données XML à l'aide du modèle de données XPath

L'espace de noms <xref:System.Xml?displayProperty=nameWithType> offre une représentation par programme de documents XML, de fragments, de nœuds ou de collections de nœuds en mémoire à l'aide des classes <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XPath.XPathDocument>.  
  
 La classe <xref:System.Xml.XPath.XPathDocument> fournit une représentation rapide, en lecture seule et en mémoire d'un document XML à l'aide du modèle de données XPath. La classe <xref:System.Xml.XmlDocument> offre une représentation en mémoire modifiable d'un document XML qui implémente les recommandations du W3C sur les modèles objet de document (DOM) niveaux 1 et 2 (noyau). Les deux classes implémentent l'interface <xref:System.Xml.XPath.IXPathNavigable> et retournent un objet <xref:System.Xml.XPath.XPathNavigator> utilisé pour sélectionner, évaluer, parcourir et, dans certains cas, modifier les données XML sous-jacentes.  
  
 Les sections suivantes décrivent les fonctionnalités de la classe <xref:System.Xml.XPath.XPathNavigator> en fonction de la classe qui la retourne.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Lecture de données XML à l’aide de XPathDocument et XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Décrit comment créer un objet de classe <xref:System.Xml.XPath.XPathDocument> en lecture seule pour lire un document XML et un objet de classe <xref:System.Xml.XmlDocument> modifiable pour lire et modifier un document XML. Cette rubrique décrit également comment retourner un objet <xref:System.Xml.XPath.XPathNavigator> de chaque classe pour parcourir et modifier un document XML.  
  
 [Sélection, évaluation et mise en correspondance de données XML à l’aide de XPathNavigator](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Décrit les méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> utilisées pour sélectionner des nœuds dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> à l’aide de la requête XPath, pour évaluer et examiner les résultats d’une expression XPath et pour déterminer si un nœud d’un document XML correspond à une expression XPath donnée.  
  
 [Accès à des données XML à l’aide de XPathNavigator](accessing-xml-data-using-xpathnavigator.md)  
 Décrit les méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> utilisées pour parcourir des nœuds, extraire des données XML et accéder à des données XML fortement typées dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>.  
  
 [Modification de données XML à l'aide de XPathNavigator](editing-xml-data-using-xpathnavigator.md)  
 Décrit les méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> utilisées pour insérer, modifier et supprimer des nœuds et des valeurs d'un document XML contenu dans un objet <xref:System.Xml.XmlDocument>.  
  
 [Validation de schéma à l'aide de XPathNavigator](schema-validation-using-xpathnavigator.md)  
 Décrit les méthodes de validation du contenu XML d'un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Traitement de données XML à l'aide du modèle DOM](process-xml-data-using-the-dom-model.md)
