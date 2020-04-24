---
title: Hiérarchie du DOM XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 1193d7631816fe9fbf7aa1984d79ef8e61d5da80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709970"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hiérarchie du DOM XML
L’illustration suivante montre la hiérarchie de classes du DOM (Document Object Model) XML et fournit le nom World Wide Web Consortium (W3C) entre parenthèses en même temps que le nom de la classe lorsque cela est pertinent.  
  
 ![Hiérarchie&#41; XML Document Object Model &#40;DOM](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
Hiérarchie du modèle DOM (Document Object Model) XML  
  
 Les classes suivantes n'héritent pas de **XmlNode** :  
  
- **XmlImplementation**  
  
- **XmlNamedNodeMap**  
  
- **XmlNodeList**  
  
- **XmlNodeChangedEventArgs**  
  
 La classe **XmlImplementation** est utilisée pour créer un document XML. Pour plus d'informations, consultez [Création d'un document XML](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 La classe **XmlNamedNodeMap** gère une collection de nœuds non triée. Pour plus d'informations, consultez [Extraction de nœuds non triés par leur nom ou par l'index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 La classe **XmlNodeList** gère une liste triée de nœuds. Pour plus d'informations, consultez [Extraction de nœuds triés par l'index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 La classe **XmlNodeChangedEventArgs** gère des gestionnaires d'événements inscrits dans **XmlDocument**. Pour plus d'informations, consultez [Gestion d'événements dans un document XML à l'aide de XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 La classe **XmlLinkedNode** hérite de **XmlNode**. Sa fonction consiste à substituer deux méthodes de **XmlNode** : les méthodes **PreviousSibling** et **NextSibling**. Les méthodes substituées sont ensuite héritées et utilisées par **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference** et **XmlProcessingInstruction**, qui sont des classes dotées de frères précédents et suivants.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
