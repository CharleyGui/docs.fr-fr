---
title: Espaces blancs dans les littéraux XML
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 56ededeb12d07e979bc86b03924e1ae0f0432822
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336005"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="ef2a1-102">Espaces blancs dans les littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef2a1-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="ef2a1-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="ef2a1-104">The insignificant white space characters are not incorporated.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="ef2a1-105">Significant and Insignificant White Space</span><span class="sxs-lookup"><span data-stu-id="ef2a1-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="ef2a1-106">White space characters in XML literals are significant in only three areas:</span><span class="sxs-lookup"><span data-stu-id="ef2a1-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
- <span data-ttu-id="ef2a1-107">When they are in an attribute value.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-107">When they are in an attribute value.</span></span>  
  
- <span data-ttu-id="ef2a1-108">When they are part of an element's text content and the text also contains other characters.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
- <span data-ttu-id="ef2a1-109">When they are in an embedded expression for an element's text content.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="ef2a1-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="ef2a1-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef2a1-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ef2a1-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="ef2a1-113">Examples</span></span>  
 <span data-ttu-id="ef2a1-114">The following example contains two XML elements, outer and inner.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="ef2a1-115">Both elements contain white space in their text content.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="ef2a1-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="ef2a1-117">The white space in the inner element is significant because it contains white space and text.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="ef2a1-118">When run, this code displays the following text.</span><span class="sxs-lookup"><span data-stu-id="ef2a1-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef2a1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef2a1-119">See also</span></span>

- [<span data-ttu-id="ef2a1-120">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ef2a1-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
