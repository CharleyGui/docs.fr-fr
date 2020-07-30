---
title: Sérialisation vers des fichiers, TextWriters et XmlWriters
description: Découvrez les options permettant de sérialiser des arborescences XML dans un fichier, un TextWriter ou un XmlWriter en C# à l’aide des méthodes ToString ou Save.
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 43c51ae7e9bf1a7848d45fd900424d6186671e53
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302384"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="dbfca-103">Sérialisation vers des fichiers, TextWriters et XmlWriters</span><span class="sxs-lookup"><span data-stu-id="dbfca-103">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="dbfca-104">Vous pouvez sérialiser des arborescences XML vers un objet <xref:System.IO.File>, <xref:System.IO.TextWriter> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="dbfca-104">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="dbfca-105">Vous pouvez sérialiser n'importe quel composant XML, y compris <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement>, vers une chaîne à l'aide de la méthode `ToString`.</span><span class="sxs-lookup"><span data-stu-id="dbfca-105">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="dbfca-106">Si vous souhaitez supprimer la mise en forme lors de la sérialisation vers une chaîne, vous pouvez utiliser la méthode <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbfca-106">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="dbfca-107">Le comportement par défaut lors de la sérialisation vers un fichier consiste à mettre en forme (mettre en retrait) le document XML obtenu.</span><span class="sxs-lookup"><span data-stu-id="dbfca-107">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="dbfca-108">Lorsque vous mettez en retrait, les espaces blancs non significatifs dans l’arborescence XML ne sont pas conservés.</span><span class="sxs-lookup"><span data-stu-id="dbfca-108">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="dbfca-109">Pour sérialiser avec la mise en forme, utilisez l'une des surcharges des méthodes suivantes qui ne prennent pas <xref:System.Xml.Linq.SaveOptions> comme argument :</span><span class="sxs-lookup"><span data-stu-id="dbfca-109">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="dbfca-110">Si vous souhaitez avoir l'option de ne pas mettre en retrait et de conserver les espaces blancs non significatifs dans l'arborescence XML, utilisez l'une des surcharges des méthodes suivantes qui prennent <xref:System.Xml.Linq.SaveOptions> comme argument :</span><span class="sxs-lookup"><span data-stu-id="dbfca-110">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="dbfca-111">Pour obtenir des exemples, consultez la rubrique de référence appropriée.</span><span class="sxs-lookup"><span data-stu-id="dbfca-111">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbfca-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbfca-112">See also</span></span>

- [<span data-ttu-id="dbfca-113">Sérialisation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="dbfca-113">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
