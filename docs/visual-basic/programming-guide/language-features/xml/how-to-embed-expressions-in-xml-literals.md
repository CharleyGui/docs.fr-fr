---
title: 'Comment : incorporer des expressions dans des littéraux XML'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332939"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="e15aa-102">Comment : incorporer des expressions dans des littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e15aa-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="e15aa-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span><span class="sxs-lookup"><span data-stu-id="e15aa-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="e15aa-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span><span class="sxs-lookup"><span data-stu-id="e15aa-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="e15aa-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span><span class="sxs-lookup"><span data-stu-id="e15aa-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span></span> <span data-ttu-id="e15aa-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e15aa-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="e15aa-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span><span class="sxs-lookup"><span data-stu-id="e15aa-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="e15aa-108">Pour plus d'informations, consultez <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e15aa-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="e15aa-109">Procédures</span><span class="sxs-lookup"><span data-stu-id="e15aa-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="e15aa-110">To insert text as element content</span><span class="sxs-lookup"><span data-stu-id="e15aa-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="e15aa-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span><span class="sxs-lookup"><span data-stu-id="e15aa-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="e15aa-112">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e15aa-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="e15aa-113">To insert text as an attribute value</span><span class="sxs-lookup"><span data-stu-id="e15aa-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="e15aa-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span><span class="sxs-lookup"><span data-stu-id="e15aa-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="e15aa-115">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e15aa-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="e15aa-116">To insert text for an element name</span><span class="sxs-lookup"><span data-stu-id="e15aa-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="e15aa-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span><span class="sxs-lookup"><span data-stu-id="e15aa-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="e15aa-118">When creating elements by using this technique, you must close them with the \</> tag.</span><span class="sxs-lookup"><span data-stu-id="e15aa-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="e15aa-119">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e15aa-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e15aa-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e15aa-120">See also</span></span>

- [<span data-ttu-id="e15aa-121">Guide pratique : créer des littéraux XML</span><span class="sxs-lookup"><span data-stu-id="e15aa-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [<span data-ttu-id="e15aa-122">Expressions incorporées en XML</span><span class="sxs-lookup"><span data-stu-id="e15aa-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="e15aa-123">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e15aa-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="e15aa-124">XML</span><span class="sxs-lookup"><span data-stu-id="e15aa-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
