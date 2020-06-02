---
title: Effet des espaces de noms sur le développement des références d'entité avec les nouveaux nœuds contenant des éléments et attributs
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 05ec622f09106978281cd3e6f0a82f13703c2097
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288808"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="822df-102">Effet des espaces de noms sur le développement des références d'entité avec les nouveaux nœuds contenant des éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="822df-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="822df-103">Le contenu d’une déclaration d’entité peut contenir pratiquement n’importe quel élément, c’est pourquoi il est possible qu’il comporte un élément tel que `<!ENTITY aname "<elem>test</elem>">`.</span><span class="sxs-lookup"><span data-stu-id="822df-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="822df-104">Lorsque le document XML est analysé, `&aname;` n’est pas développé avec son contenu de remplacement au moment de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="822df-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="822df-105">Le développement XML n’a pas lieu car la résolution de l’espace de noms pour l’élément ne peut se produire tant que le nœud n’est pas placé dans le document.</span><span class="sxs-lookup"><span data-stu-id="822df-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="822df-106">Jusqu'alors, l'espace de noms figurant dans la portée n'est pas détectable.</span><span class="sxs-lookup"><span data-stu-id="822df-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="822df-107">Lorsque le nœud est placé dans le document, la résolution de l’espace de noms se produit et le contenu d’entité résultant est analysé dans ses nœuds adéquats.</span><span class="sxs-lookup"><span data-stu-id="822df-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="822df-108">Après que le développement a eu lieu sur un nœud de référence d'entité à peine créé, il ne peut se produire à nouveau.</span><span class="sxs-lookup"><span data-stu-id="822df-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="822df-109">C'est pourquoi les espaces de noms utilisés dans le texte de remplacement de l'élément sont liés au moment de la définition du nœud parent.</span><span class="sxs-lookup"><span data-stu-id="822df-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="822df-110">Toutefois, l'espace de noms peut être modifié pour des nœuds de référence d'entité existants lorsque vous les supprimez ou les insérez ailleurs, ou bien pour des nœuds de référence d'entité clonés à l'aide de la méthode **CloneNode**.</span><span class="sxs-lookup"><span data-stu-id="822df-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="822df-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="822df-111">See also</span></span>

- [<span data-ttu-id="822df-112">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="822df-112">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
