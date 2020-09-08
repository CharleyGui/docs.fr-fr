---
title: Sérialiser vers des fichiers, TextWriters et XmlWriters-LINQ to XML
description: Vous pouvez sérialiser des arborescences XML dans un fichier, un TextWriter ou un XmlWriter, et vous pouvez sérialiser n’importe quel composant XML, y compris XDocument et XElement, en une chaîne à l’aide de la méthode ToString.
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20651c06a759d83934c4b035a42eac7c2700eb9f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553814"
---
# <a name="serialize-to-files-textwriters-and-xmlwriters-linq-to-xml"></a><span data-ttu-id="65b1d-103">Sérialiser vers des fichiers, TextWriters et XmlWriters (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="65b1d-103">Serialize to files, TextWriters, and XmlWriters (LINQ to XML)</span></span>

<span data-ttu-id="65b1d-104">Vous pouvez sérialiser des arborescences XML vers un objet <xref:System.IO.File>, <xref:System.IO.TextWriter> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="65b1d-104">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="65b1d-105">Vous pouvez sérialiser n'importe quel composant XML, y compris <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement>, vers une chaîne à l'aide de la méthode `ToString`.</span><span class="sxs-lookup"><span data-stu-id="65b1d-105">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="65b1d-106">Si vous souhaitez supprimer la mise en forme lors de la sérialisation vers une chaîne, vous pouvez utiliser la méthode <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65b1d-106">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="65b1d-107">Le comportement par défaut lors de la sérialisation vers un fichier consiste à mettre en forme (mettre en retrait) le document XML obtenu.</span><span class="sxs-lookup"><span data-stu-id="65b1d-107">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="65b1d-108">Lorsque vous mettez en retrait, les espaces blancs non significatifs dans l’arborescence XML ne sont pas conservés.</span><span class="sxs-lookup"><span data-stu-id="65b1d-108">When you indent, the insignificant white space in the XML tree isn't preserved.</span></span> <span data-ttu-id="65b1d-109">Pour sérialiser avec la mise en forme, utilisez l’une des surcharges des méthodes suivantes qui ne prennent pas <xref:System.Xml.Linq.SaveOptions> comme argument :</span><span class="sxs-lookup"><span data-stu-id="65b1d-109">To serialize with formatting, use one of the overloads of the following methods that don't take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="65b1d-110">Si vous souhaitez avoir l'option de ne pas mettre en retrait et de conserver les espaces blancs non significatifs dans l'arborescence XML, utilisez l'une des surcharges des méthodes suivantes qui prennent <xref:System.Xml.Linq.SaveOptions> comme argument :</span><span class="sxs-lookup"><span data-stu-id="65b1d-110">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="65b1d-111">Pour obtenir des exemples, consultez l’article de référence approprié.</span><span class="sxs-lookup"><span data-stu-id="65b1d-111">For examples, see the appropriate reference article.</span></span>
