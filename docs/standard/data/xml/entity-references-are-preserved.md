---
title: Conservation des références d'entité
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e512f2077c2e6b9feba5024c4eabc2568357ecab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965913"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="1b3f5-102">Conservation des références d'entité</span><span class="sxs-lookup"><span data-stu-id="1b3f5-102">Entity References are Preserved</span></span>
<span data-ttu-id="1b3f5-103">Si une référence d’entité n’est pas développée, mais préservée, le DOM (Document Object Model) XML crée un nœud **XmlEntityReference** quand il rencontre une référence d’entité.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="1b3f5-104">À l'aide du code XML suivant,</span><span class="sxs-lookup"><span data-stu-id="1b3f5-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="1b3f5-105">le DOM crée un nœud **XmlEntityReference** quand il rencontre la référence `&publisher;`.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="1b3f5-106">**XmlEntityReference** contient des nœuds enfants copiés à partir du contenu dans la déclaration d'entité.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="1b3f5-107">L'exemple de code précédent contient du texte dans la déclaration d'entité, c'est pourquoi un nœud **XmlText** est créé en tant que nœud enfant du nœud de référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="1b3f5-108">![Arborescence pour références d’entité préservées](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="1b3f5-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="1b3f5-109">Structure d’arborescence avec références d’entité préservées</span><span class="sxs-lookup"><span data-stu-id="1b3f5-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="1b3f5-110">Les nœuds enfants de **XmlEntityReference** sont des copies de tous les nœuds enfants créés à partir du nœud **XmlEntity** quand la déclaration d'entité a été rencontrée.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b3f5-111">Les nœuds copiés à partir de **XmlEntity** ne constituent pas toujours des copies exactes une fois placés sous le nœud de référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="1b3f5-112">Il peut y avoir des espaces de noms qui sont dans la portée au niveau du nœud de référence d'entité et qui ont une incidence sur la configuration finale des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="1b3f5-113">Par défaut, des entités générales telles que `&abc;` sont préservées et les nœuds **XmlEntityReference** sont toujours créés.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b3f5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b3f5-114">See also</span></span>

- [<span data-ttu-id="1b3f5-115">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="1b3f5-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
