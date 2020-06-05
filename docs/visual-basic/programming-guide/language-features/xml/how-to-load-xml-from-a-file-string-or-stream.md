---
title: "Comment : charger du code XML à partir d'un fichier, d'une chaîne ou d'un flux"
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7f2a961ebb7ecd4fc0512e141b4a437be87bec0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392286"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="92ead-102">Comment : charger du code XML à partir d'un fichier, d'une chaîne ou d'un flux (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92ead-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>

<span data-ttu-id="92ead-103">Vous pouvez créer des [littéraux XML](../../../language-reference/xml-literals/index.md) et les remplir avec le contenu d’une source externe, telle qu’un fichier, une chaîne ou un flux à l’aide de plusieurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="92ead-103">You can create [XML Literals](../../../language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="92ead-104">Ces méthodes sont illustrées dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="92ead-104">These methods are shown in the following examples.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a><span data-ttu-id="92ead-105">Pour charger du code XML à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="92ead-105">To load XML from a file</span></span>

<span data-ttu-id="92ead-106">Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objet ou à partir d’un fichier, utilisez la `Load` méthode.</span><span class="sxs-lookup"><span data-stu-id="92ead-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="92ead-107">Cette méthode peut accepter un chemin d’accès de fichier, un flux de texte ou un flux XML comme entrée.</span><span class="sxs-lookup"><span data-stu-id="92ead-107">This method can take a file path, text stream, or XML stream as input.</span></span>

<span data-ttu-id="92ead-108">L’exemple de code suivant illustre l’utilisation de la <xref:System.Xml.Linq.XDocument.Load%28System.String%29> méthode pour remplir un <xref:System.Xml.Linq.XDocument> objet avec du code XML à partir d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="92ead-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a><span data-ttu-id="92ead-109">Pour charger du code XML à partir d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="92ead-109">To load XML from a string</span></span>

<span data-ttu-id="92ead-110">Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objet ou à partir d’une chaîne, vous pouvez utiliser la `Parse` méthode.</span><span class="sxs-lookup"><span data-stu-id="92ead-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>

<span data-ttu-id="92ead-111">L’exemple de code suivant illustre l’utilisation de la <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> méthode pour remplir un <xref:System.Xml.Linq.XDocument> objet avec du code XML à partir d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="92ead-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="92ead-112">Pour charger du code XML à partir d’un flux</span><span class="sxs-lookup"><span data-stu-id="92ead-112">To load XML from a stream</span></span>

<span data-ttu-id="92ead-113">Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objet ou à partir d’un flux, vous pouvez utiliser la `Load` méthode ou la <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="92ead-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="92ead-114">L’exemple de code suivant illustre l’utilisation de la <xref:System.Xml.Linq.XNode.ReadFrom%2A> méthode pour remplir un <xref:System.Xml.Linq.XDocument> objet avec du code XML à partir d’un flux XML.</span><span class="sxs-lookup"><span data-stu-id="92ead-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a><span data-ttu-id="92ead-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92ead-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="92ead-116">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="92ead-116">XML Literals</span></span>](../../../language-reference/xml-literals/index.md)
- [<span data-ttu-id="92ead-117">XML</span><span class="sxs-lookup"><span data-stu-id="92ead-117">XML</span></span>](index.md)
- [<span data-ttu-id="92ead-118">Manipulation de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92ead-118">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
