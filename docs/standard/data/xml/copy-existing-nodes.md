---
title: Copie de nœuds existants
ms.date: 03/30/2017
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 651e9fc9dc0d1a50a2d15d382b3ca65f7fd4b7fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701430"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="a4bae-102">Copie de nœuds existants</span><span class="sxs-lookup"><span data-stu-id="a4bae-102">Copy Existing Nodes</span></span>

<span data-ttu-id="a4bae-103">Le DOM (Document Object Model) XML comporte de nombreuses méthodes et propriétés que vous pouvez utiliser pour sélectionner un nœud, par exemple **SelectSingleNode**, **ChildNodes[int i]** ou **Attributes[int i]**.</span><span class="sxs-lookup"><span data-stu-id="a4bae-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="a4bae-104">Une fois le nœud sélectionné, vous pouvez l’insérer dans l’arborescence à l’aide de l’une des méthodes d’insertion adaptées à ce type de nœud particulier.</span><span class="sxs-lookup"><span data-stu-id="a4bae-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="a4bae-105">La seule restriction à l’insertion d’un nœud dans l’arborescence est que cette opération ne doit pas compromettre la validité du format du document.</span><span class="sxs-lookup"><span data-stu-id="a4bae-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="a4bae-106">Quand un nœud existant est inséré dans l’arborescence DOM, il est supprimé de sa position d’origine et ajouté à sa position de destination.</span><span class="sxs-lookup"><span data-stu-id="a4bae-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4bae-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4bae-107">See also</span></span>

- [<span data-ttu-id="a4bae-108">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="a4bae-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
