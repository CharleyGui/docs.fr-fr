---
title: Suppression d'attributs d'un nœud d'élément dans le DOM
ms.date: 03/30/2017
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
ms.openlocfilehash: 53922c55295e852a1aa62d847313fbd657a42541
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686759"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>Suppression d'attributs d'un nœud d'élément dans le DOM

Il existe plusieurs manières de supprimer des attributs. L’une des techniques consiste à les supprimer de la collection d’attributs. Pour ce faire, procédez comme suit :  
  
1. Obtenez la collection d’attributs à partir de l’élément à l’aide de `XmlAttributeCollection attrs = elem.Attributes;`.  
  
2. Supprimez l'attribut de la collection d'attributs à l'aide d'une des trois méthodes suivantes :  
  
    - Utilisez la méthode <xref:System.Xml.XmlAttributeCollection.Remove%2A> pour supprimer un attribut spécifique.  
  
    - Utilisez la méthode <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> pour supprimer tous les attributs de la collection et conserver l'élément sans attribut.  
  
    - Utilisez la méthode <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> pour supprimer un attribut d’une collection d’attributs à l’aide de son numéro d’index.  
  
 Les méthodes suivantes suppriment des attributs du nœud d'élément.  
  
- Utilisez la méthode <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> pour supprimer la collection d’attributs.  
  
- Utilisez la méthode <xref:System.Xml.XmlElement.RemoveAttribute%2A> pour supprimer de la collection un attribut spécifique par son nom.  
  
- Utilisez la méthode <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> pour supprimer de la collection un attribut spécifique par son numéro d'index.  
  
 Une autre solution consiste à obtenir l'élément, puis l'attribut à partir de la collection d'attributs et de supprimer directement le nœud d'attribut. Pour obtenir l’attribut à partir de la collection d’attributs, vous pouvez utiliser un nom, `XmlAttribute attr = attrs["attr_name"];`, un index `XmlAttribute attr = attrs[0];` ou donner un nom qualifié à l’espace de noms `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.  
  
 Quelle que soit la méthode utilisée pour la suppression des attributs, la suppression d'attributs définis comme des attributs par défaut dans la DTD (définition de type de document) est sujette à des restrictions spéciales. Les attributs par défaut ne peuvent pas être supprimés, à moins que l'élément auquel ils appartiennent ne le soit également. Les attributs par défaut sont toujours présents pour les éléments possédant des attributs par défaut déclarés. La suppression d'un attribut par défaut d'un objet <xref:System.Xml.XmlAttributeCollection> ou de l'objet <xref:System.Xml.XmlElement> provoque l'insertion d'un attribut de substitution dans l'objet <xref:System.Xml.XmlAttributeCollection> de l'élément, initialisé à la valeur par défaut qui a été déclarée. Si un élément est défini comme `<book att1="1" att2="2" att3="3"></book>`, un élément `book` possède trois attributs par défaut déclarés. L'implémentation du modèle DOM (Document Object Model) XML assure que tant que cet élément `book` existe, il possède ces trois attributs par défaut `att1`, `att2` et `att3`.  
  
 Appelée avec un objet <xref:System.Xml.XmlAttribute>, la méthode <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> définit la valeur de l'attribut sur String.Empty, étant donné qu'un attribut ne peut pas exister sans valeur.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
