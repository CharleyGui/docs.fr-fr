---
title: Suppression du contenu d'un nœud dans le DOM
ms.date: 03/30/2017
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: 7b33ebfea244dbe81879c61be3809adcb2a1f5d3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828866"
---
# <a name="removing-node-content-in-the-dom"></a>Suppression du contenu d'un nœud dans le DOM
Pour les types de nœuds héritant de l'objet <xref:System.Xml.XmlCharacterData>, à savoir les types de nœuds <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace> et <xref:System.Xml.XmlSignificantWhitespace>, vous pouvez supprimer des caractères à l'aide de la méthode <xref:System.Xml.XmlCharacterData.DeleteData%2A>, qui supprime une série de caractères du nœud. Pour supprimer intégralement le contenu, vous devez supprimer le nœud en question. Pour conserver le nœud, alors que son contenu est incorrect, vous devez modifier le contenu. Pour plus d'informations sur la modification du contenu d'un nœud, consultez [Modification de nœuds, de contenu et de valeurs dans un document XML](modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
