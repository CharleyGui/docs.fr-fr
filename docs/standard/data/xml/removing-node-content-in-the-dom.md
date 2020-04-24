---
title: Suppression du contenu d'un nœud dans le DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: f5086bdea8ff1f0ee5329f347223ebb4a6bd71da
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710334"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="dbfb3-102">Suppression du contenu d'un nœud dans le DOM</span><span class="sxs-lookup"><span data-stu-id="dbfb3-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="dbfb3-103">Pour les types de nœuds héritant de l'objet <xref:System.Xml.XmlCharacterData>, à savoir les types de nœuds <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace> et <xref:System.Xml.XmlSignificantWhitespace>, vous pouvez supprimer des caractères à l'aide de la méthode <xref:System.Xml.XmlCharacterData.DeleteData%2A>, qui supprime une série de caractères du nœud.</span><span class="sxs-lookup"><span data-stu-id="dbfb3-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="dbfb3-104">Pour supprimer intégralement le contenu, vous devez supprimer le nœud en question.</span><span class="sxs-lookup"><span data-stu-id="dbfb3-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="dbfb3-105">Pour conserver le nœud, alors que son contenu est incorrect, vous devez modifier le contenu.</span><span class="sxs-lookup"><span data-stu-id="dbfb3-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="dbfb3-106">Pour plus d'informations sur la modification du contenu d'un nœud, consultez [Modification de nœuds, de contenu et de valeurs dans un document XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="dbfb3-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbfb3-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbfb3-107">See also</span></span>

- [<span data-ttu-id="dbfb3-108">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="dbfb3-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
