---
title: Conservation des références d'entité
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: e4c902df1b0cd2bd9e97b49c0ec1d10df91ef1c7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290342"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="f5947-102">Conservation des références d'entité</span><span class="sxs-lookup"><span data-stu-id="f5947-102">Entity References are Preserved</span></span>
<span data-ttu-id="f5947-103">Si une référence d’entité n’est pas développée, mais préservée, le DOM (Document Object Model) XML crée un nœud **XmlEntityReference** quand il rencontre une référence d’entité.</span><span class="sxs-lookup"><span data-stu-id="f5947-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="f5947-104">À l'aide du code XML suivant,</span><span class="sxs-lookup"><span data-stu-id="f5947-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="f5947-105">le DOM crée un nœud **XmlEntityReference** quand il rencontre la référence `&publisher;`.</span><span class="sxs-lookup"><span data-stu-id="f5947-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="f5947-106">**XmlEntityReference** contient des nœuds enfants copiés à partir du contenu dans la déclaration d'entité.</span><span class="sxs-lookup"><span data-stu-id="f5947-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="f5947-107">L'exemple de code précédent contient du texte dans la déclaration d'entité, c'est pourquoi un nœud **XmlText** est créé en tant que nœud enfant du nœud de référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="f5947-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="f5947-108">![arborescence pour références d'entité préservées](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="f5947-108">![Tree structure for preserved entity references](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="f5947-109">Structure d’arborescence avec références d’entité préservées</span><span class="sxs-lookup"><span data-stu-id="f5947-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="f5947-110">Les nœuds enfants de **XmlEntityReference** sont des copies de tous les nœuds enfants créés à partir du nœud **XmlEntity** quand la déclaration d'entité a été rencontrée.</span><span class="sxs-lookup"><span data-stu-id="f5947-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5947-111">Les nœuds copiés à partir de **XmlEntity** ne constituent pas toujours des copies exactes une fois placés sous le nœud de référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="f5947-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="f5947-112">Il peut y avoir des espaces de noms qui sont dans la portée au niveau du nœud de référence d'entité et qui ont une incidence sur la configuration finale des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="f5947-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="f5947-113">Par défaut, des entités générales telles que `&abc;` sont préservées et les nœuds **XmlEntityReference** sont toujours créés.</span><span class="sxs-lookup"><span data-stu-id="f5947-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5947-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5947-114">See also</span></span>

- [<span data-ttu-id="f5947-115">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="f5947-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
