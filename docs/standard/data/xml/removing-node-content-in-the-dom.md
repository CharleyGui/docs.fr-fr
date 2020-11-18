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
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="83ece-102">Suppression du contenu d'un nœud dans le DOM</span><span class="sxs-lookup"><span data-stu-id="83ece-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="83ece-103">Pour les types de nœuds héritant de l'objet <xref:System.Xml.XmlCharacterData>, à savoir les types de nœuds <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace> et <xref:System.Xml.XmlSignificantWhitespace>, vous pouvez supprimer des caractères à l'aide de la méthode <xref:System.Xml.XmlCharacterData.DeleteData%2A>, qui supprime une série de caractères du nœud.</span><span class="sxs-lookup"><span data-stu-id="83ece-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="83ece-104">Pour supprimer intégralement le contenu, vous devez supprimer le nœud en question.</span><span class="sxs-lookup"><span data-stu-id="83ece-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="83ece-105">Pour conserver le nœud, alors que son contenu est incorrect, vous devez modifier le contenu.</span><span class="sxs-lookup"><span data-stu-id="83ece-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="83ece-106">Pour plus d'informations sur la modification du contenu d'un nœud, consultez [Modification de nœuds, de contenu et de valeurs dans un document XML](modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="83ece-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ece-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83ece-107">See also</span></span>

- [<span data-ttu-id="83ece-108">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="83ece-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
