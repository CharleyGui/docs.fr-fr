---
title: Suppression de nœuds du DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: 5df95700bb1e84aa5f3adcc752b2314dc964477b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288639"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="825f1-102">Suppression de nœuds du DOM</span><span class="sxs-lookup"><span data-stu-id="825f1-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="825f1-103">Pour supprimer un nœud du DOM (Document Object Model) XML, utilisez la méthode <xref:System.Xml.XmlNode.RemoveChild%2A>.</span><span class="sxs-lookup"><span data-stu-id="825f1-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="825f1-104">La méthode supprime le sous-arbre appartenant au nœud en cours de suppression, du moins s'il ne s'agit pas d'un nœud sans descendant.</span><span class="sxs-lookup"><span data-stu-id="825f1-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="825f1-105">Pour supprimer plusieurs nœuds du DOM, utilisez la méthode <xref:System.Xml.XmlNode.RemoveAll%2A>, qui permet de supprimer tous les enfants et attributs (le cas échéant) du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="825f1-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="825f1-106">Si vous travaillez avec un objet <xref:System.Xml.XmlNamedNodeMap>, vous pouvez supprimer un nœud à l'aide de la méthode <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="825f1-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="825f1-107">Pour plus d'informations sur la suppression d'attributs, consultez [Suppression d'attributs d'un nœud d'élément dans le DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="825f1-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825f1-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="825f1-108">See also</span></span>

- [<span data-ttu-id="825f1-109">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="825f1-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
