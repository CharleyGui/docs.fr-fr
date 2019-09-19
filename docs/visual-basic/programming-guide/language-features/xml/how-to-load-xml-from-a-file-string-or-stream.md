---
title: 'Procédure : Charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: ba88ae19abc216a318d6c2069ab0846d5db8a346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054169"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="36a1f-102">Procédure : Charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36a1f-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>

<span data-ttu-id="36a1f-103">Vous pouvez créer des [littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md) et les remplir avec le contenu d’une source externe, telle qu’un fichier, une chaîne ou un flux à l’aide de plusieurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="36a1f-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="36a1f-104">Ces méthodes sont illustrées dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="36a1f-104">These methods are shown in the following examples.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a><span data-ttu-id="36a1f-105">Pour charger du code XML à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="36a1f-105">To load XML from a file</span></span>

<span data-ttu-id="36a1f-106">Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement> objet <xref:System.Xml.Linq.XDocument> ou à partir d’un fichier, `Load` utilisez la méthode.</span><span class="sxs-lookup"><span data-stu-id="36a1f-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="36a1f-107">Cette méthode peut accepter un chemin d’accès de fichier, un flux de texte ou un flux XML comme entrée.</span><span class="sxs-lookup"><span data-stu-id="36a1f-107">This method can take a file path, text stream, or XML stream as input.</span></span>

<span data-ttu-id="36a1f-108">L’exemple de code suivant illustre l’utilisation de <xref:System.Xml.Linq.XDocument.Load%28System.String%29> la méthode pour remplir <xref:System.Xml.Linq.XDocument> un objet avec du code XML à partir d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="36a1f-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a><span data-ttu-id="36a1f-109">Pour charger du code XML à partir d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="36a1f-109">To load XML from a string</span></span>

<span data-ttu-id="36a1f-110">Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement> objet <xref:System.Xml.Linq.XDocument> ou à partir d’une chaîne, vous pouvez `Parse` utiliser la méthode.</span><span class="sxs-lookup"><span data-stu-id="36a1f-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>

<span data-ttu-id="36a1f-111">L’exemple de code suivant illustre l’utilisation de <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> la méthode pour remplir <xref:System.Xml.Linq.XDocument> un objet avec du code XML à partir d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="36a1f-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="36a1f-112">Pour charger du code XML à partir d’un flux</span><span class="sxs-lookup"><span data-stu-id="36a1f-112">To load XML from a stream</span></span>

<span data-ttu-id="36a1f-113">Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement> objet <xref:System.Xml.Linq.XDocument> ou à partir d’un flux, vous pouvez `Load` utiliser la méthode <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> ou la méthode.</span><span class="sxs-lookup"><span data-stu-id="36a1f-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="36a1f-114">L’exemple de code suivant illustre l’utilisation de <xref:System.Xml.Linq.XNode.ReadFrom%2A> la méthode pour remplir <xref:System.Xml.Linq.XDocument> un objet avec du code XML à partir d’un flux XML.</span><span class="sxs-lookup"><span data-stu-id="36a1f-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a><span data-ttu-id="36a1f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36a1f-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="36a1f-116">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="36a1f-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="36a1f-117">XML</span><span class="sxs-lookup"><span data-stu-id="36a1f-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="36a1f-118">Manipulation de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36a1f-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
