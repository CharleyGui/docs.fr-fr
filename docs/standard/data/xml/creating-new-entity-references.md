---
title: Création de nouvelles références d'entité
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8d4e9e1e2dfd9882504c935912bcf235608485
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965900"
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="3b669-102">Création de nouvelles références d'entité</span><span class="sxs-lookup"><span data-stu-id="3b669-102">Creating New Entity References</span></span>
<span data-ttu-id="3b669-103">La méthode **CreateEntityReference** crée un nouveau nœud **XmlEntityReference**.</span><span class="sxs-lookup"><span data-stu-id="3b669-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="3b669-104">Le DOM (Document Object Model) XML vérifie si le nom de l'entité référencée a déjà été déclaré.</span><span class="sxs-lookup"><span data-stu-id="3b669-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="3b669-105">Si tel est le cas, les nœuds enfants du nœud **XmlEntityReference** sont copiés à partir du nœud de la déclaration d'entité.</span><span class="sxs-lookup"><span data-stu-id="3b669-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="3b669-106">Si aucune déclaration d'entité ne correspond, un nœud de texte vide est joint en tant qu'unique enfant du nœud de référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="3b669-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="3b669-107">Les nœuds enfants du nœud **XmlEntityReference** étant des copies d'autres nœuds, ils sont en lecture seule et ne peuvent pas être modifiés.</span><span class="sxs-lookup"><span data-stu-id="3b669-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="3b669-108">Lorsque les nœuds sont copiés, il est possible qu'un espace de noms soit dans la portée à la position de la référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="3b669-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="3b669-109">Cet espace de noms a une incidence sur la configuration de tous les nœuds d'élément ou d'attribut générés.</span><span class="sxs-lookup"><span data-stu-id="3b669-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b669-110">Le DOM ajoute des nœuds enfants à **EntityReference** uniquement si vous insérez le nœud **EntityReference** dans le document.</span><span class="sxs-lookup"><span data-stu-id="3b669-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="3b669-111">Les nœuds **EntityReference** nouvellement créés ne possèdent pas de nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="3b669-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="3b669-112">Même si **XmlDataDocument** est une classe dérivée de **XmlDocument**, **XmlDataDocument** ne prend pas en charge la création de références d'entité.</span><span class="sxs-lookup"><span data-stu-id="3b669-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="3b669-113">Cela tient au fait que les enfants **EntityReference** sont en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="3b669-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="3b669-114">Les enfants d'un nœud **EntityReference** peuvent s'étendre sur plus d'une région.</span><span class="sxs-lookup"><span data-stu-id="3b669-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="3b669-115">Dans ce cas, une partie d'une ligne associée à la région qui contient une partie de **EntityReference** sera en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="3b669-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b669-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b669-116">See also</span></span>

- [<span data-ttu-id="3b669-117">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="3b669-117">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
