---
title: Conserver les espaces blancs lors de la sérialisation de-LINQ to XML
description: Vous pouvez contrôler les espaces de différentes façons lors de la sérialisation d’une arborescence XML.
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d907e68a2df3905794b555954330f31b5e75655
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552488"
---
# <a name="preserve-white-space-while-serializing-linq-to-xml"></a><span data-ttu-id="bc24b-103">Conserver les espaces blancs lors de la sérialisation (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="bc24b-103">Preserve white space while serializing (LINQ to XML)</span></span>

<span data-ttu-id="bc24b-104">Cet article explique comment contrôler l’espace blanc lors de la sérialisation d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="bc24b-104">This article describes how to control white space when serializing an XML tree.</span></span>

<span data-ttu-id="bc24b-105">Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d’espace blanc (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="bc24b-105">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="bc24b-106">Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés.</span><span class="sxs-lookup"><span data-stu-id="bc24b-106">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="bc24b-107">Il s’agit du comportement par défaut pour LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="bc24b-107">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="bc24b-108">Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="bc24b-108">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="bc24b-109">Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière.</span><span class="sxs-lookup"><span data-stu-id="bc24b-109">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="bc24b-110">Pour effectuer cette opération dans LINQ to XML, vous conservez l’espace blanc lorsque vous chargez ou analysez le XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.</span><span class="sxs-lookup"><span data-stu-id="bc24b-110">To do this in LINQ to XML, you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>

## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="bc24b-111">Comportement d’espace blanc des méthodes qui sérialisent des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="bc24b-111">White-space behavior of methods that serialize XML trees</span></span>

<span data-ttu-id="bc24b-112">Les méthodes suivantes dans les classes <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XDocument> sérialisent une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="bc24b-112">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="bc24b-113">Vous pouvez sérialiser une arborescence XML vers un fichier, un objet <xref:System.IO.TextReader> ou un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="bc24b-113">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="bc24b-114">La méthode `ToString` sérialise vers une chaîne.</span><span class="sxs-lookup"><span data-stu-id="bc24b-114">The `ToString` method serializes to a string.</span></span>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bc24b-115">XElement.ToString()</span><span class="sxs-lookup"><span data-stu-id="bc24b-115">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
- [<span data-ttu-id="bc24b-116">XDocument.ToString()</span><span class="sxs-lookup"><span data-stu-id="bc24b-116">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)

<span data-ttu-id="bc24b-117">Si la méthode ne prend pas <xref:System.Xml.Linq.SaveOptions> comme argument, la méthode met en forme (en retrait) le code XML sérialisé.</span><span class="sxs-lookup"><span data-stu-id="bc24b-117">If the method doesn't take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="bc24b-118">Dans ce cas, tous les espaces blancs non significatifs dans l'arborescence XML seront ignorés.</span><span class="sxs-lookup"><span data-stu-id="bc24b-118">In this case, all insignificant white space in the XML tree is discarded.</span></span>

<span data-ttu-id="bc24b-119">Si la méthode prend l'objet <xref:System.Xml.Linq.SaveOptions> comme argument, vous pouvez spécifier qu'elle ne mettra pas en forme (en retrait) le code XML sérialisé.</span><span class="sxs-lookup"><span data-stu-id="bc24b-119">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="bc24b-120">Dans ce cas, tous les espaces blancs dans l’arborescence XML seront conservés.</span><span class="sxs-lookup"><span data-stu-id="bc24b-120">In this case, all white space in the XML tree is preserved.</span></span>
