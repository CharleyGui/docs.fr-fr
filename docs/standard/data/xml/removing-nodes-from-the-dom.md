---
title: Suppression de nœuds du DOM
ms.date: 03/30/2017
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: ecda49960f51d807730cb44b966aa2dfcada22d7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823704"
---
# <a name="removing-nodes-from-the-dom"></a>Suppression de nœuds du DOM
Pour supprimer un nœud du DOM (Document Object Model) XML, utilisez la méthode <xref:System.Xml.XmlNode.RemoveChild%2A>. La méthode supprime le sous-arbre appartenant au nœud en cours de suppression, du moins s'il ne s'agit pas d'un nœud sans descendant.  
  
 Pour supprimer plusieurs nœuds du DOM, utilisez la méthode <xref:System.Xml.XmlNode.RemoveAll%2A>, qui permet de supprimer tous les enfants et attributs (le cas échéant) du nœud actuel.  
  
 Si vous travaillez avec un objet <xref:System.Xml.XmlNamedNodeMap>, vous pouvez supprimer un nœud à l'aide de la méthode <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A>.  
  
 Pour plus d'informations sur la suppression d'attributs, consultez [Suppression d'attributs d'un nœud d'élément dans le DOM](removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
