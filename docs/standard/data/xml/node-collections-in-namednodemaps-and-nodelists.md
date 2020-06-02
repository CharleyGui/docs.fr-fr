---
title: Collections de nœuds dans NamedNodeMap et NodeList
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 025954b8-7aa8-47c5-a1c1-f81064fb4d65
ms.openlocfilehash: 3d721e9a6cff87adbf8896b1b37c0e2dfa55fa71
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288769"
---
# <a name="node-collections-in-namednodemaps-and-nodelists"></a><span data-ttu-id="2bbd1-102">Collections de nœuds dans NamedNodeMap et NodeList</span><span class="sxs-lookup"><span data-stu-id="2bbd1-102">Node Collections in NamedNodeMaps and NodeLists</span></span>
<span data-ttu-id="2bbd1-103">Il est possible d'extraire une collection de nœuds et de les placer dans une collection triée ou non.</span><span class="sxs-lookup"><span data-stu-id="2bbd1-103">You can retrieve a set of nodes and put it in an ordered or unordered collection.</span></span> <span data-ttu-id="2bbd1-104">Si vous regroupez une collection de nœuds dans une collection non triée, cet ensemble est appelé NamedNodeMap par le World Wide Web Consortium (W3C). Ce type de collection vous permet d’extraire des données au moyen de leur nom ou de l’index.</span><span class="sxs-lookup"><span data-stu-id="2bbd1-104">When putting a set of nodes into an unordered collection, the set is called a NamedNodeMap by the World Wide Web Consortium (W3C); you can retrieve the data by name or index in this type of collection.</span></span> <span data-ttu-id="2bbd1-105">En revanche, si vous placez une collection de nœuds dans une collection triée, celle-ci est appelée NodeList par le W3C, et ses données peuvent être extraites au moyen d’un index de base zéro.</span><span class="sxs-lookup"><span data-stu-id="2bbd1-105">Putting a set of nodes in an ordered collection is called a NodeList by the W3C, and the data can be retrieved by a zero-based index.</span></span> <span data-ttu-id="2bbd1-106">NamedNodeMap et NodeList sont décrits par le W3C.</span><span class="sxs-lookup"><span data-stu-id="2bbd1-106">NamedNodeMaps and NodeLists are described by the W3C.</span></span> <span data-ttu-id="2bbd1-107">Leurs implémentations dans Microsoft .NET Framework sont **XmlNamedNodeMap** pour NamedNodeMap et **XmlNodeList** pour NodeList.</span><span class="sxs-lookup"><span data-stu-id="2bbd1-107">The implementations in the Microsoft .NET Framework for the NamedNodeMap is the **XmlNamedNodeMap**, and the NodeList is implemented by the **XmlNodeList**.</span></span>  
  
 <span data-ttu-id="2bbd1-108">Pour obtenir des informations sur la collection non triée, consultez [Extraction de nœuds non triés par leur nom ou par l’index](unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="2bbd1-108">For information on the unordered collection, see [Unordered Node Retrieval by Name or Index](unordered-node-retrieval-by-name-or-index.md).</span></span> <span data-ttu-id="2bbd1-109">Pour obtenir des informations sur la collection triée, consultez [Extraction de nœuds triés par l’index](ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="2bbd1-109">For information on the ordered collection, see [Ordered Node Retrieval by Index](ordered-node-retrieval-by-index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bbd1-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bbd1-110">See also</span></span>

- [<span data-ttu-id="2bbd1-111">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="2bbd1-111">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
