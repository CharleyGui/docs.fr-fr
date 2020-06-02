---
title: Lecture de déclarations d'entité et de références d'entité vers le DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
ms.openlocfilehash: 41d88de9ee988a29c54c6e2c6c437963b9f79cf8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289874"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="87c6e-102">Lecture de déclarations d'entité et de références d'entité vers le DOM</span><span class="sxs-lookup"><span data-stu-id="87c6e-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="87c6e-103">Une entité est une déclaration établissant qu'un certain nom doit être utilisé dans les données XML en lieu et place d'un contenu ou d'un balisage donné.</span><span class="sxs-lookup"><span data-stu-id="87c6e-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="87c6e-104">Une entité présente deux aspects.</span><span class="sxs-lookup"><span data-stu-id="87c6e-104">There are two parts to entities.</span></span> <span data-ttu-id="87c6e-105">D'une part, vous devez associer un nom au contenu de remplacement, au moyen d'une déclaration d'entité.</span><span class="sxs-lookup"><span data-stu-id="87c6e-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="87c6e-106">Une déclaration d'entité est créée au moyen de la syntaxe `<!ENTITY name "value">` dans une DTD ou un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="87c6e-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="87c6e-107">D'autre part, le nom défini dans la déclaration d'entité est utilisé par la suite dans les données XML.</span><span class="sxs-lookup"><span data-stu-id="87c6e-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="87c6e-108">Ce nom, une fois employé dans le code XML, est appelé référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="87c6e-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="87c6e-109">Par exemple, la déclaration d'entité suivante déclare une entité portant le nom `publisher` associé au contenu de « Microsoft Press ».</span><span class="sxs-lookup"><span data-stu-id="87c6e-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="87c6e-110">L'exemple suivant illustre l'utilisation de cette déclaration d'entité dans le code XML en tant que référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="87c6e-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="87c6e-111">Certains analyseurs développent automatiquement des entités lors du chargement d’un document en mémoire.</span><span class="sxs-lookup"><span data-stu-id="87c6e-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="87c6e-112">Dès lors, lorsque le code XML est lu et chargé en mémoire, les déclarations d'entité sont mémorisées et enregistrées.</span><span class="sxs-lookup"><span data-stu-id="87c6e-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="87c6e-113">Ensuite, quand l'analyseur rencontre des caractères `&;` qui identifient une référence d'entité générale, il recherche ce nom dans une table de déclaration d'entité.</span><span class="sxs-lookup"><span data-stu-id="87c6e-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="87c6e-114">La référence, `&publisher;`, est remplacée par le contenu qu'elle représente.</span><span class="sxs-lookup"><span data-stu-id="87c6e-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="87c6e-115">À l'aide du code XML suivant,</span><span class="sxs-lookup"><span data-stu-id="87c6e-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="87c6e-116">le développement de la référence d’entité et le remplacement de `&publisher;` par le contenu Microsoft Press produit les données XML développées suivantes :</span><span class="sxs-lookup"><span data-stu-id="87c6e-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="87c6e-117">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="87c6e-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="87c6e-118">Il existe diverses sortes d'entités.</span><span class="sxs-lookup"><span data-stu-id="87c6e-118">There are many kinds of entities.</span></span> <span data-ttu-id="87c6e-119">Le diagramme suivant montre la répartition des types d'entité et leur terminologie.</span><span class="sxs-lookup"><span data-stu-id="87c6e-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="87c6e-120">![organigramme de la hiérarchie des types d'entités](media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="87c6e-120">![flow chart of entity type hierarchy](media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="87c6e-121">Par défaut, l’implémentation par Microsoft .NET Framework de DOM (Document Object Model) XML préserve les références d’entités et ne développe pas les entités lors du chargement du XML.</span><span class="sxs-lookup"><span data-stu-id="87c6e-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="87c6e-122">Cela a pour effet de créer, lorsqu'un document est chargé dans le DOM, un nœud **XmlEntityReference** contenant la variable de référence `&publisher;`, avec des nœuds enfants représentant le contenu de l'entité déclarée dans la DTD.</span><span class="sxs-lookup"><span data-stu-id="87c6e-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="87c6e-123">En se basant sur la déclaration d'entité `<!ENTITY publisher "Microsoft Press">`, le diagramme suivant montre les nœuds **XmlEntity** et **XmlText** créés à partir de cette déclaration.</span><span class="sxs-lookup"><span data-stu-id="87c6e-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="87c6e-124">![nœuds créés à partir de la déclaration d'entité](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="87c6e-124">![nodes created from entity declaration](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="87c6e-125">Les différences qu'il existe entre les références d'entité développées et non développées concernent les nœuds qui sont générés dans l'arborescence DOM en mémoire.</span><span class="sxs-lookup"><span data-stu-id="87c6e-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="87c6e-126">La différence dans les nœuds générés est expliquée dans les rubriques [Conservation des références d’entité](entity-references-are-preserved.md) et [Développement sans conservation des références d’entité](entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="87c6e-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c6e-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87c6e-127">See also</span></span>

- [<span data-ttu-id="87c6e-128">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="87c6e-128">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
