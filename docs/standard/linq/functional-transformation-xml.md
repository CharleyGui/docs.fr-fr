---
title: Transformation fonctionnelle des LINQ to XML XML
description: Découvrez l’approche de transformation fonctionnelle pure permettant de modifier des documents XML et leurs différences par rapport à une approche procédurale.
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: b23288e013a4104b21523e17e1f266a9f712c451
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552449"
---
# <a name="functional-transformation-of-xml-linq-to-xml"></a><span data-ttu-id="8ebc6-103">Transformation fonctionnelle de XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8ebc6-103">Functional transformation of XML (LINQ to XML)</span></span>

<span data-ttu-id="8ebc6-104">Cet article décrit l’approche de transformation fonctionnelle pure permettant de modifier des documents XML et les compare à une approche procédurale.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-104">This article discusses the pure functional transformation approach to modifying XML documents, and contrasts it with a procedural approach.</span></span>

## <a name="modifying-an-xml-document"></a><span data-ttu-id="8ebc6-105">Modification d’un document XML</span><span class="sxs-lookup"><span data-stu-id="8ebc6-105">Modifying an XML document</span></span>

<span data-ttu-id="8ebc6-106">L'une des tâches les plus courantes pour un programmeur XML consiste à transformer du code XML d'une forme en une autre.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-106">One of the most common tasks for an XML programmer is transforming XML from one shape to another.</span></span> <span data-ttu-id="8ebc6-107">La forme d'un document XML est la structure du document, qui inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="8ebc6-107">The shape of an XML document is the structure of the document, which includes the following:</span></span>

- <span data-ttu-id="8ebc6-108">la hiérarchie exprimée par le document ;</span><span class="sxs-lookup"><span data-stu-id="8ebc6-108">The hierarchy expressed by the document.</span></span>
- <span data-ttu-id="8ebc6-109">les noms des éléments et des attributs ;</span><span class="sxs-lookup"><span data-stu-id="8ebc6-109">The element and attribute names.</span></span>
- <span data-ttu-id="8ebc6-110">les types de données des éléments et attributs.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-110">The data types of the elements and attributes.</span></span>

<span data-ttu-id="8ebc6-111">En général, l'approche la plus efficace pour transformer du code XML d'une forme en une autre consiste à utiliser la transformation fonctionnelle pure.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-111">In general, the most effective approach to transforming XML from one shape to another is that of pure functional transformation.</span></span> <span data-ttu-id="8ebc6-112">Avec cette approche, la principale tâche du programmeur est de créer une transformation qui est appliquée à l'ensemble du document XML (ou à un ou plusieurs nœuds strictement définis).</span><span class="sxs-lookup"><span data-stu-id="8ebc6-112">In this approach, the primary programmer task is to create a transformation which is applied to the entire XML document (or to one or more strictly defined nodes).</span></span> <span data-ttu-id="8ebc6-113">La transformation fonctionnelle offre sans aucun doute la plus grande facilité de codage (une fois que le programmeur s'est familiarisé avec cette approche) et la plus grande facilité de maintenance du code, et elle est souvent plus compacte que les autres approches.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-113">Functional transformation is arguably the easiest to code (after a programmer is familiar with the approach), yields the most maintainable code, and is often more compact than alternative approaches.</span></span>

### <a name="xml-functional-transformational-technologies"></a><span data-ttu-id="8ebc6-114">Technologies de transformation fonctionnelle XML</span><span class="sxs-lookup"><span data-stu-id="8ebc6-114">XML functional transformational technologies</span></span>

<span data-ttu-id="8ebc6-115">Microsoft propose deux technologies de transformation fonctionnelle pour une utilisation sur des documents XML : XSLT et LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-115">Microsoft offers two functional transformation technologies for use on XML documents: XSLT and LINQ to XML.</span></span> <span data-ttu-id="8ebc6-116">XSLT est pris en charge dans l'espace de noms managé <xref:System.Xml.Xsl> et dans l'implémentation COM native de MSXML.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-116">XSLT is supported in the <xref:System.Xml.Xsl> managed namespace and in the native COM implementation of MSXML.</span></span> <span data-ttu-id="8ebc6-117">Bien que XSLT soit une technologie robuste pour la manipulation de documents XML, elle requiert un savoir-faire dans un domaine spécialisé, à savoir le langage XSLT et ses API de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-117">Although XSLT is a robust technology for manipulating XML documents, it requires expertise in a specialized domain, namely the XSLT language and its supporting APIs.</span></span>

<span data-ttu-id="8ebc6-118">LINQ to XML procure les outils nécessaires pour coder des transformations fonctionnelles pures de manière expressive et puissante, dans du code C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-118">LINQ to XML provides the tools necessary to code pure functional transformations in an expressive and powerful way, within C# or Visual Basic code.</span></span> <span data-ttu-id="8ebc6-119">Par exemple, bon nombre des exemples dans la documentation LINQ to XML utilisent une approche fonctionnelle pure.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-119">For example, many of the examples in the LINQ to XML documentation use a pure functional approach.</span></span> <span data-ttu-id="8ebc6-120">En outre, dans le didacticiel [: manipulation de contenu dans un document WordprocessingML](xml-shape-wordprocessingml-documents.md) , nous utilisons LINQ to XML dans une approche fonctionnelle pour manipuler des informations dans un document Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-120">Also, in the [Tutorial: Manipulating Content in a WordprocessingML Document](xml-shape-wordprocessingml-documents.md) tutorial, we use LINQ to XML in a functional approach to manipulate information in a Microsoft Word document.</span></span>

<span data-ttu-id="8ebc6-121">Pour une comparaison plus complète des LINQ to XML avec d’autres technologies XML Microsoft, consultez [LINQ to XML différences par rapport à d’autres technologies XML](linq-xml-vs-xml-technologies.md).</span><span class="sxs-lookup"><span data-stu-id="8ebc6-121">For a more complete comparison of LINQ to XML with other Microsoft XML technologies, see [LINQ to XML vs. other XML technologies](linq-xml-vs-xml-technologies.md).</span></span>

<span data-ttu-id="8ebc6-122">XSLT est l'outil recommandé pour les transformations centrées sur les documents lorsque le document source a une structure irrégulière.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-122">XSLT is the recommended tool for  document-centric transformations when the source document has an irregular structure.</span></span> <span data-ttu-id="8ebc6-123">Toutefois, LINQ to XML peut également effectuer des transformations centrées sur les documents.</span><span class="sxs-lookup"><span data-stu-id="8ebc6-123">However, LINQ to XML can also perform document-centric transforms.</span></span> <span data-ttu-id="8ebc6-124">Pour plus d’informations, consultez [comment utiliser des annotations pour transformer des arbres LINQ to XML dans un style XSLT](use-annotations-transform-linq-xml-trees-xslt-style.md).</span><span class="sxs-lookup"><span data-stu-id="8ebc6-124">For more information, see [How to use annotations to transform LINQ to XML trees in an XSLT style](use-annotations-transform-linq-xml-trees-xslt-style.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ebc6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ebc6-125">See also</span></span>

- [<span data-ttu-id="8ebc6-126">Présentation des transformations fonctionnelles pures</span><span class="sxs-lookup"><span data-stu-id="8ebc6-126">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)
- [<span data-ttu-id="8ebc6-127">Didacticiel : manipuler du contenu dans un document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="8ebc6-127">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
- [<span data-ttu-id="8ebc6-128">LINQ to XML différences par rapport à d’autres technologies XML</span><span class="sxs-lookup"><span data-stu-id="8ebc6-128">LINQ to XML vs. other XML technologies</span></span>](linq-xml-vs-xml-technologies.md)